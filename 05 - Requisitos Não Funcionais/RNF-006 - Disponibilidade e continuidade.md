---
tags: [doalink, rnf, disponibilidade]
id: RNF-006
prioridade: Importante
---

# RNF-006 — Disponibilidade e continuidade do serviço

**Categoria:** Disponibilidade  
**Prioridade:** Importante

## Declaração
O sistema deve estar disponível para uso dentro de metas acordadas, com degradação controlada em falhas parciais e capacidade de recuperação.

## Métricas sugeridas (A definir)
| Métrica | Sugestão inicial | Observação |
|---|---|---|
| Disponibilidade mensal | 99% a 99,5% (MVP) | Calibrar conforme criticidade e custo. |
| Janela de manutenção | Comunicada previamente | Preferir janelas de baixo uso. |
| RTO (Recovery Time Objective) | A definir | Tempo alvo para restaurar serviço. |
| RPO (Recovery Point Objective) | A definir | Perda máxima aceitável de dados. |

## Critérios
- Falhas em integrações externas (ex.: validação CNPJ, envio de e-mail) não devem corromper dados locais; usar timeout, fila/retry e fallback quando aplicável.
- Health checks para aplicação e dependências críticas (banco).
- Em campanhas emergenciais, avaliar meta de disponibilidade maior (A definir).