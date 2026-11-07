---
tags: [doalink, rf, acompanhamento, status, desejável]
id: RF-009
prioridade: Desejável
origem: implementacao-doalink.md
---

# RF-009 — Acompanhamento da doação

**Prioridade:** Desejável  
**Origem:** Documento base (§4 RF-009)  
Relacionado: [[RF-007 - Sugestão e resposta a combinações]] | [[07 - Modelo de Dados e Domínio]]

## Descrição
O sistema deve permitir que participantes autorizados consultem a situação atual da doação. Estados informados no documento base: `OFERTADA`, `COMBINADA`, `EM_TRANSPORTE`, `ENTREGUE`. Cada atualização deve registrar data/hora.

## Decisões pendentes
- Atualização manual ou automática (eventos do sistema)? PD-012.
- Quais papéis podem atualizar cada estado? PD-012.
- Registrar participante responsável pela atualização? Documento base sugere confirmar — recomendado.
- Relação com estados da proposta (RF-007): unificar ou separar modelos?

## Campos do histórico (sugestão)
| Campo | Observação |
|---|---|
| Doação/proposta relacionada | Identificador. |
| Situação | Enum controlado. |
| Data/hora | Timestamp da atualização. |
| Responsável | Usuário/sistema que realizou a mudança. |
| Observação | Opcional. |

## Critérios de aceite
- **CA-009-1:** Dado participante autorizado, quando consulta a doação, então visualiza a situação atual.
- **CA-009-2:** Dada atualização de situação, quando exibida, então corresponde à atualização mais recente registrada.

## Estado atual
- Não implementado.