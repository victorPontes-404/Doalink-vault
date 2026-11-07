---
tags: [doalink, modelo-de-dados, domínio, entidades]
---

# Modelo de Dados e Domínio (lógico inicial)

Relacionado: [[02 - Glossário e Conceitos]] | [[04 - Requisitos Funcionais/RF - Índice]] | [[10 - Decisões Pendentes]]

> Modelo **lógico** para orientar requisitos e implementação. Nomes físicos, tipos SQL exatos e estratégia de ORM podem variar por decisão técnica, desde que preservem as regras.

## 1. Entidades principais

### Participante / Usuário
Representa a identidade cadastrada na plataforma.

| Atributo | Observação |
|---|---|
| id | Identificador interno gerado automaticamente. |
| nome / nomeOrganizacao | Obrigatório. |
| cpf | Opcional/condicional; normalizado; único quando presente. |
| cnpj | Opcional/condicional; normalizado; único quando presente. |
| email | Obrigatório, único, normalizado para comparação. |
| senhaHash | Obrigatório; nunca senha em texto puro. |
| telefone | Contato; obrigatoriedade/normalização A definir. |
| tipoPerfil | Doador, Receptor, Transportador (ou modelo multi-perfil). |
| tipoPessoa | Física/Jurídica, conforme documento. |
| statusConta | Sugestão: pendente confirmação, ativa, bloqueada, desativada. |
| datas | createdAt, updatedAt, lastLoginAt (sugestão). |

**Implementação atual:** `Usuario` abstrata com herança `JOINED` para `Doador`, `Receptor`, `Transportador`. Assume 1 perfil por conta.

### Endereço
Pode ser embutido no participante (receptor) e/ou associado a oferta/local de retirada/entrega.

| Atributo | Observação |
|---|---|
| cep | Normalizado. |
| uf | — |
| cidade | — |
| bairro | — |
| logradouro | — |
| numero | — |
| complemento | Opcional. |
| latitude/longitude | Sugestão futura, se matching geográfico exigir. |

### OfertaDoacao
| Atributo | Observação |
|---|---|
| id | — |
| doadorId | FK para participante doador. |
| estado | A definir (rascunho/publicada/reservada/concluída/expirada/cancelada). |
| localRetirada | Endereço ou referência. |
| disponibilidadeInicio/Fim | A definir. |
| observacoes | Sugestão. |

**Implementação atual:** existe `ItemDoacao` (item individual) ligado a `Doador` e `Endereco`; o conceito de "oferta agregadora" ainda pode evoluir.

### ItemDoacao / Item de Oferta
| Atributo | Observação |
|---|---|
| id | — |
| ofertaId ou doadorId | Conforme modelagem. |
| categoria/tipoItem | Catálogo padronizado. |
| quantidade | Positiva; tipo com precisão adequada. |
| unidade | — |
| endereco/local | No modelo atual, embutido por item — revisar se local é da oferta ou do item. |

### Necessidade
| Atributo | Observação |
|---|---|
| id | — |
| receptorId | — |
| campanhaId | Opcional. |
| categoria | — |
| quantidade | — |
| unidade | — |
| localEntrega | — |
| estado | A definir. |
| urgencia | Sugestão. |

### DisponibilidadeTransporte
| Atributo | Observação |
|---|---|
| id | — |
| transportadorId | — |
| tipoVeiculo | Catálogo. |
| capacidade | — |
| unidadeCapacidade | — |
| origem | — |
| destino/regiao | — |
| dataInicio/Fim | — |
| estado | A definir. |

### Proposta / Match
| Atributo | Observação |
|---|---|
| id | — |
| ofertaId | — |
| necessidadeId | — |
| transporteId | Opcional. |
| estado | A definir (sugerida, aguardando, confirmada, recusada, expirada...). |
| createdAt/updatedAt | — |

### RespostaProposta (por participante)
| Atributo | Observação |
|---|---|
| propostaId | — |
| participanteId | — |
| papel | Doador/Receptor/Transportador no contexto. |
| resposta | PENDENTE, ACEITA, RECUSADA. |
| respondidoEm | — |
| observacao | Opcional. |

### Campanha
| Atributo | Observação |
|---|---|
| id | — |
| nome | — |
| descricao | — |
| regiaoAfetada | Formato A definir. |
| estado | ativa, encerrada, arquivada. |
| inicio/fim | — |
| criadoPor | — |

### HistoricoSituacaoDoacao
| Atributo | Observação |
|---|---|
| id | — |
| propostaId/doacaoId | — |
| situacao | OFERTADA, COMBINADA, EM_TRANSPORTE, ENTREGUE (base). |
| dataHora | — |
| responsavelId | Recomendado. |
| origem | manual/sistema. |

### TokenRecuperacao / Confirmacao (conceitual)
| Atributo | Observação |
|---|---|
| id | — |
| contaId | — |
| tipo | recuperação senha / confirmação e-mail. |
| tokenHash | Nunca armazenar token puro quando evitável. |
| expiraEm | — |
| usadoEm | — |
| canal | e-mail/SMS. |

**Estado atual:** existem conceitos de refresh token/JWT no histórico integrado; token de recuperação/confirmação ainda a implementar.

## 2. Estados sugeridos (a consolidar)

### Oferta
`RASCUNHO` → `PUBLICADA` → `RESERVADA`/`PARCIAL` → `CONCLUIDA` | `EXPIRADA` | `CANCELADA` *(sugestão)*.

### Necessidade
`ABERTA` → `PARCIALMENTE_ATENDIDA` → `ATENDIDA` | `CANCELADA` | `EXPIRADA` *(sugestão)*.

### Proposta
`SUGERIDA` → `AGUARDANDO_RESPOSTAS` → `CONFIRMADA` | `RECUSADA` | `EXPIRADA` | `CANCELADA` *(sugestão; regra de confirmação PD-010)*.

### Campanha
`ATIVA` → `ENCERRADA` → `ARQUIVADA`.

### Doação/acompanhamento
`OFERTADA` → `COMBINADA` → `EM_TRANSPORTE` → `ENTREGUE` (base), com possíveis estados excepcionais (`CANCELADA`, `DEVOLVIDA`, `FALHA_ENTREGA`) — **A definir**.

## 3. Relacionamentos (resumo)
- Doador 1—N Ofertas/Itens.
- Receptor 1—N Necessidades.
- Transportador 1—N Disponibilidades.
- Campanha 1—N Necessidades.
- Proposta N—1 Oferta, N—1 Necessidade, N—0..1 Transporte.
- Proposta 1—N Respostas; Proposta 1—N Histórico de situação.