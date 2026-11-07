---
tags: [doalink, rnf, interoperabilidade, api]
id: RNF-012
prioridade: Desejável
---

# RNF-012 — Interoperabilidade e integrações

**Categoria:** Interoperabilidade  
**Prioridade:** Desejável

## Declaração
O sistema deve expor contratos de API claros e integrar-se de forma resiliente a serviços externos necessários.

## Critérios
| Item | Requisito |
|---|---|
| Contrato de API | Endpoints com verbos, status HTTP, payloads e erros consistentes; documentação OpenAPI recomendada. |
| Versionamento de API | Estratégia de versionamento (path/header) — A definir antes de clientes externos. |
| Integrações externas | CEP, validação CNPJ, e-mail/SMS: encapsular em clientes com timeout, retry controlado e tratamento de falha. |
| Idempotência | Considerar idempotência em operações sensíveis sujeitas a reenvio (A definir). |