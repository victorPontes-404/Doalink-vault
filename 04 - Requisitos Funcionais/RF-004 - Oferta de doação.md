---
tags: [doalink, rf, oferta, doação, essencial, detalhado]
id: RF-004
prioridade: Essencial
origem: implementacao-doalink.md (expandido)
---

# RF-004 — Oferta de doação (detalhado)

**Prioridade:** Essencial  
Relacionado: [[RF-006 - Necessidade de doação]] | [[RF-007 - Sugestão e resposta a combinações]] | [[RF-011 - Consulta e busca]] | [[RF-014 - Catálogos e padronização]] | [[RF-019 - Anexos e evidências de itens]] | [[RF-021 - Expiração, renovação e arquivamento]] | [[RF-031 - Gestão de múltiplos itens e kits]] | [[RF-032 - Elegibilidade e restrições de itens]]

## 1. Descrição
O sistema deve permitir que doadores autenticados cadastrem, consultem, atualizem e gerenciem ofertas de doação. Uma oferta representa a disponibilização de um ou mais itens, com quantidade, unidade, local, janela de disponibilidade e estado de ciclo de vida.

## 2. Estrutura da oferta

### 2.1 Cabeçalho da oferta
| Campo | Obrigatório | Observação |
|---|:---:|---|
| Doador | Sim (implícito) | Obtido do usuário autenticado. |
| Título/resumo | Sugerido | Facilita busca (ex.: "Cestas básicas", "Roupas infantis"). |
| Descrição geral | Não | Contexto adicional. |
| Local de retirada/coleta | Sim | Pode ser endereço do doador ou local alternativo (PD-007). |
| Janela de disponibilidade | A definir | Data/hora início-fim ou datas válidas (PD-009). |
| Estado | Sim | Controlado por RN-012. |
| Visibilidade | A definir | Pública/autenticada/restrita (PD-014). |
| Canal/observações de coleta | Não | Ex.: portaria, horário comercial, agendamento prévio. |

### 2.2 Itens da oferta
| Campo | Obrigatório | Observação |
|---|:---:|---|
| Categoria/tipo | Sim | Catálogo padronizado (RF-014). |
| Subcategoria/descrição | Não | Detalhe livre controlado. |
| Quantidade | Sim | > 0. |
| Unidade | Sim | Compatível com categoria. |
| Quantidade disponível/reservada *(se parcialização)* | A definir | Necessário se PD-007 permitir atendimento parcial. |
| Condição | Sugerido | Novo, usado bom estado, etc., quando aplicável. |
| Validade do item | Condicional | Especialmente para alimentos/medicamentos — cuidado com RF-032. |

## 3. Estados sugeridos (A definir)
| Estado | Descrição |
|---|---|
| `RASCUNHO` | Criada, não visível para matching público. |
| `PUBLICADA` | Elegível para consulta/matching conforme visibilidade. |
| `PARCIALMENTE_RESERVADA` | Parte da quantidade comprometida (se parcialização). |
| `RESERVADA` | Totalmente comprometida em proposta confirmada/processo. |
| `CONCLUIDA` | Doação efetivada/encerrada com sucesso. |
| `EXPIRADA` | Janela de disponibilidade vencida. |
| `CANCELADA` | Cancelada pelo doador ou administrador autorizado. |

## 4. Regras de negócio
- Apenas doador autenticado cria oferta em seu nome.
- Doador só edita/cancela ofertas próprias, respeitando estado (ex.: oferta concluída não volta a publicada sem regra explícita).
- Quantidade comprometida não pode exceder quantidade disponível.
- Alterações relevantes após proposta criada devem seguir política de reavaliação/notificação (RF-007, RF-012).
- Itens regulados exigem validação adicional ou podem ser bloqueados (RF-032).

## 5. Fluxos
### 5.1 Criar oferta
1. Doador acessa "Nova oferta".
2. Informa dados gerais, local e itens.
3. Opcionalmente anexa fotos (RF-019) e salva rascunho (RF-027).
4. Publica oferta.
5. Sistema valida, persiste e torna elegível conforme regras.

### 5.2 Editar/cancelar
- Edição permitida em campos/estados definidos.
- Cancelamento exige confirmação; pode impactar propostas abertas.

### 5.3 Expiração
- Job/processo ou verificação sob demanda marca oferta expirada ao fim da janela (RF-021).

## 6. Critérios de aceite
- **CA-004-1:** Dado doador autenticado, quando informa dados obrigatórios válidos, então o sistema registra a oferta.
- **CA-004-2:** Dada oferta publicada e elegível, quando há consulta/matching, então participa conforme visibilidade e compatibilidade.
- **CA-004-3 (sugestão):** Dado doador, quando tenta editar/cancelar oferta de outro usuário, então o sistema nega.
- **CA-004-4 (sugestão):** Dada quantidade inválida (<= 0) ou item sem categoria, quando envia, então o sistema rejeita.
- **CA-004-5 (sugestão):** Dada oferta com múltiplos itens, quando registrada, então todos os itens válidos ficam associados à oferta.

## 7. Estado atual (código)
- Existem DTOs e `ItemDoacao` com `Doador` e `Endereco`. Falta modelar oferta agregadora (cabeçalho), persistência/serviço/controller, estados, janela temporal e saldo. Quantidade usa `Double`; avaliar precisão decimal.