---
tags: [doalink, rf, expiração, ciclo-de-vida, importante]
id: RF-021
prioridade: Importante
origem: Expansão
---

# RF-021 — Expiração, renovação e arquivamento

**Prioridade:** Importante (sugestão)

## Descrição
O sistema deve controlar o ciclo de vida temporal de ofertas, necessidades, disponibilidades e propostas, expirando registros vencidos e permitindo renovação/arquivamento conforme regras.

## Regras sugeridas
| Entidade | Comportamento |
|---|---|
| Oferta | Expira ao fim da janela de disponibilidade; pode ser renovada/republicada pelo doador (A definir). |
| Necessidade | Expira ou é encerrada quando atendida/cancelada; campanha pode influenciar. |
| Disponibilidade de transporte | Expira após data/horário final. |
| Proposta | Expira se não houver resposta no prazo definido (PD-010). |
| Campanha | Encerrada/arquivada por usuário autorizado. |

## Critérios de aceite (sugestão)
- **CA-021-1:** Dado registro com data/validade expirada, quando o sistema avalia elegibilidade, então o registro não participa de novos matchings ativos.
- **CA-021-2:** Dado participante autorizado e registro elegível para renovação, quando renova com dados válidos, então o sistema atualiza a vigência conforme política.