---
tags: [doalink, rf, matching, proposta, combinação, desejável, detalhado]
id: RF-007
prioridade: Desejável (base) / Importante (recomendação de roadmap)
origem: implementacao-doalink.md (expandido)
---

# RF-007 — Sugestão e resposta a combinações (detalhado)

**Prioridade:** Desejável no documento base; **recomenda-se tratar como Importante** por ser o núcleo da proposta de valor.  
Relacionado: [[RF-004 - Oferta de doação]] | [[RF-005 - Disponibilidade de transporte]] | [[RF-006 - Necessidade de doação]] | [[RF-009 - Acompanhamento da doação]] | [[RF-012 - Notificações]] | [[RF-014 - Catálogos e padronização]] | [[RF-021 - Expiração, renovação e arquivamento]] | [[07 - Modelo de Dados e Domínio]] | [[10 - Decisões Pendentes|PD-006–PD-010, PD-014]]

## 1. Descrição
O sistema deve identificar oportunidades de combinação entre **oferta(s)**, **necessidade(s)** e, quando necessário, **disponibilidade(s) de transporte**, gerando **propostas** rastreáveis. Os participantes envolvidos devem poder analisar, aceitar ou recusar propostas, com registro completo de respostas, prazos e mudanças de estado.

## 2. Objetivos do requisito
- Reduzir esforço manual para encontrar doador/receptor/transporte compatíveis.
- Tornar explícitas as condições da combinação (o quê, quanto, onde, quando).
- Garantir que somente envolvidos respondam e que decisões fiquem auditáveis.
- Suportar cenários com e sem transporte.

## 3. Conceitos operacionais

### 3.1 Proposta
Entidade que representa uma sugestão/negociação estruturada. Composição mínima:
- 1 oferta (ou item de oferta) + 1 necessidade (ou item de necessidade);
- 0 ou 1 disponibilidade de transporte (obrigatória apenas quando a regra indicar necessidade logística);
- quantidade/capacidade comprometida na proposta;
- local/rota e janela temporal considerados;
- estado da proposta e respostas por participante.

### 3.2 Participantes envolvidos
- **Doador:** dono da oferta.
- **Receptor:** dono da necessidade.
- **Transportador:** dono da disponibilidade de transporte, quando incluído.

### 3.3 Tipos de combinação (sugestão)
| Tipo | Quando ocorre | Exemplo |
|---|---|---|
| Direta (sem transporte) | Coleta/entrega resolvida entre doador e receptor | Receptor retira no local do doador. |
| Com transporte | Há necessidade logística explícita ou distância/regra exige | Transportador coleta na origem e entrega no destino. |
| Parcial *(A definir)* | Proposta atende parte da necessidade/oferta | Oferta de 100 atende necessidade de 40. |
| Multi-origem/multi-destino *(futuro)* | Combinações complexas | Fora do MVP, salvo decisão. |

## 4. Critérios de compatibilidade (motor de matching)

> Cada dimensão abaixo precisa de regra objetiva. Dimensões sem regra definida devem ir para PD e não bloquear o desenho do fluxo.

| Dimensão | Critério base | Detalhamento / pendências |
|---|---|---|
| Item/categoria | Categoria/tipo compatível | Usar catálogo padronizado (PD-006, RF-014). Definir equivalências (ex.: “cesta básica” vs itens). |
| Quantidade | Necessidade <= oferta disponível (ou parcialização) | Considerar saldo livre, reservas e propostas pendentes (PD-007). |
| Unidade | Mesma unidade ou conversão permitida | Conversões explícitas e seguras (PD-006). |
| Capacidade de transporte | Capacidade >= quantidade/volume/peso comprometido | Unidade de capacidade deve ser comparável (PD-006). |
| Localização/rota | Origem, coleta, entrega e destino compatíveis | Modelo geográfico (CEP/cidade/raio/coordenadas) e limite de distância/rota (PD-008). |
| Tempo | Janelas de oferta, necessidade e transporte se interceptam | Precisão (dia/hora), fuso, tolerância e expiração (PD-009). |
| Estado/elegibilidade | Registros ativos e não expirados | RF-021. |
| Restrições do item | Item permitido, condições especiais atendidas | RF-032, PD-016. |
| Visibilidade | Proposta só usa dados/registros visíveis ao contexto autorizado | PD-014, RN-010. |

## 5. Estados sugeridos da proposta (A definir — PD-010)

| Estado | Significado sugerido | Entrada típica | Saídas típicas |
|---|---|---|---|
| `RASCUNHO` | Criada mas não enviada (se houver fluxo manual) | Criação interna | Enviada, cancelada |
| `SUGERIDA` | Gerada pelo sistema | Matching | Aguardando respostas, expirada |
| `AGUARDANDO_RESPOSTAS` | Enviada aos envolvidos | Sugestão enviada | Parcialmente respondida, confirmada, recusada, expirada |
| `PARCIALMENTE_ACEITA` | Alguns aceitaram, faltam outros | Resposta parcial | Confirmada, recusada, expirada |
| `CONFIRMADA` | Regra de confirmação atendida | Aceites necessários | Em execução/acompanhamento, cancelada (excepcional) |
| `RECUSADA` | Recusada por participante/regra | Recusa | Encerrada |
| `EXPIRADA` | Prazo de resposta/validade esgotado | Tempo | Encerrada |
| `CANCELADA` | Cancelada por ator autorizado | Ação autorizada | Encerrada |

> **Regra crítica a definir:** confirmação exige aceite de todos os envolvidos? Existe timeout por participante? Recusa de um cancela toda a proposta?

## 6. Respostas dos participantes
Estados base do documento: `PENDENTE`, `ACEITA`, `RECUSADA`.

Campos mínimos por resposta:
- proposta;
- participante;
- papel no contexto;
- decisão;
- data/hora;
- motivo/observação (opcional, RF-028).

Regras:
- Usuário não envolvido não pode responder (CA-007-6).
- Resposta duplicada: definir se pode alterar antes do prazo/estado final (A definir).
- Toda resposta gera trilha auditável (RN-008, RNF-009).

## 7. Fluxo principal detalhado
1. **Gatilho:** criação/atualização de oferta, necessidade ou disponibilidade; ou execução agendada/manual de matching.
2. **Seleção de candidatos:** sistema busca registros elegíveis por categoria e região/janela inicial.
3. **Avaliação:** aplica critérios de compatibilidade.
4. **Formação da proposta:** calcula quantidade comprometida, inclui transporte se necessário.
5. **Reserva lógica (se adotada):** marca saldo como reservado para evitar sobrecomprometimento (PD-007).
6. **Publicação da proposta:** muda estado e notifica envolvidos (RF-012).
7. **Coleta de respostas:** cada envolvido aceita/recusa.
8. **Consolidação:** aplica regra de confirmação.
9. **Desfecho:** confirma, recusa, cancela ou expira; libera/baixa reservas conforme regra.
10. **Acompanhamento:** proposta confirmada pode gerar/iniciar acompanhamento (RF-009).

## 8. Fluxos alternativos e exceções
| Cenário | Comportamento esperado |
|---|---|
| Nenhuma combinação encontrada | Informar ausência de sugestões; manter registros elegíveis. |
| Oferta sem saldo suficiente | Não propor acima do saldo; sugerir parcial se permitido. |
| Transporte incompatível | Propor combinação direta ou buscar outro transporte. |
| Participante recusa | Registrar motivo (se houver); recusar/encerrar proposta conforme regra. |
| Proposta expira | Alterar estado; liberar reserva; notificar. |
| Registro origem é cancelado/expirado | Invalidar propostas dependentes conforme política. |
| Resposta concorrente | Garantir consistência transacional/otimista (RNF-005). |

## 9. Dados mínimos exibidos aos envolvidos (respeitar privacidade)
- Resumo do item/categoria, quantidade/unidade.
- Locais e janela temporal relevantes ao papel do participante.
- Estado da proposta e respostas já registradas (visibilidade a definir).
- Dados de contato: somente conforme política (PD-014, RN-010) — geralmente após confirmação ou quando necessário ao fluxo.

## 10. Critérios de aceite
- **CA-007-1:** Dadas oferta e necessidade compatíveis em item, quantidade, localização e data, quando avaliadas, então o sistema pode gerar proposta.
- **CA-007-2:** Quando houver necessidade de transporte, o sistema inclui disponibilidade compatível em capacidade, rota e data.
- **CA-007-3:** Quando não houver combinação compatível, o sistema informa ausência de resultado.
- **CA-007-4:** Dado participante envolvido, quando aceita ou recusa, então a resposta é registrada com data/hora e decisão.
- **CA-007-5:** Após resposta, o estado da proposta é atualizado conforme regra definida e exibido aos autorizados.
- **CA-007-6:** Dado usuário não envolvido, quando tenta responder/alterar, então o sistema nega.
- **CA-007-7 (sugestão):** Dada proposta expirada, quando o prazo termina, então o sistema muda o estado para expirada e libera reservas associadas.
- **CA-007-8 (sugestão):** Dada alteração/cancelamento de oferta, necessidade ou transporte vinculado, quando a proposta ainda depende dele, então o sistema reavalia ou invalida a proposta conforme política.

## 11. Pontos em aberto
PD-006, PD-007, PD-008, PD-009, PD-010, PD-014. Sem essas decisões, a implementação do matching pode ficar inconsistente ou exigir retrabalho.