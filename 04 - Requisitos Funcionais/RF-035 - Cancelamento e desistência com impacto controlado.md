---
tags: [doalink, rf, cancelamento, estados, importante]
id: RF-035
prioridade: Importante
origem: Expansão
---

# RF-035 — Cancelamento e desistência com impacto controlado

**Prioridade:** Importante (sugestão)

## Descrição
O sistema deve tratar cancelamentos e desistências (oferta, necessidade, transporte, participação em proposta) com regras claras de impacto, notificação e liberação de reservas.

## Cenários
| Cenário | Impacto esperado |
|---|---|
| Doador cancela oferta com proposta pendente | Propostas dependentes reavaliadas/canceladas; notificar envolvidos. |
| Receptor cancela necessidade | Idem. |
| Transportador fica indisponível | Proposta busca substituto ou é invalidada (A definir). |
| Participante desiste após confirmação | Fluxo excepcional; exige política, registro e possível intervenção administrativa. |

## Regras
- Exigir motivo (RF-028) em cancelamentos críticos.
- Preservar histórico e auditoria.