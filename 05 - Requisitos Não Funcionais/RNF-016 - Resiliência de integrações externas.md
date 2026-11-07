---
tags: [doalink, rnf, resiliência, integrações]
id: RNF-016
prioridade: Importante
---

# RNF-016 — Resiliência de integrações externas

**Categoria:** Confiabilidade / Interoperabilidade  
**Prioridade:** Importante

## Declaração
Integrações externas (CEP, CNPJ, e-mail, SMS, geocodificação) devem falhar de forma controlada, sem comprometer a integridade do fluxo local.

## Critérios
- Timeout configurado para chamadas externas.
- Retry com backoff apenas quando seguro/idempotente.
- Circuit breaker/fallback quando aplicável (A definir).
- Degradação graciosa: ex., permitir preenchimento manual de endereço se consulta CEP falhar (política definida).
- Observabilidade de erros externos (métricas/logs).