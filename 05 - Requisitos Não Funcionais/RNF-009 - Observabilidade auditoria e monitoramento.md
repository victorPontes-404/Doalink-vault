---
tags: [doalink, rnf, observabilidade, auditoria, logs]
id: RNF-009
prioridade: Importante
---

# RNF-009 — Observabilidade, auditoria e monitoramento

**Categoria:** Observabilidade  
**Prioridade:** Importante

## Declaração
O sistema deve produzir informações suficientes para diagnóstico operacional, segurança e auditoria, sem expor dados sensíveis.

## Critérios
| Item | Requisito |
|---|---|
| Logs de aplicação | Eventos relevantes (erros, integrações, autenticação, mudanças críticas) com timestamp, correlação/request ID e nível adequado. |
| Sem dados sensíveis | Não logar senhas, tokens completos, documentos completos sem mascaramento quando desnecessário. |
| Auditoria de negócio | Registrar ações críticas: cadastro, login relevante, recuperação de senha, criação/edição/cancelamento de oferta/necessidade/transporte, respostas de proposta, mudanças de estado, ações administrativas. |
| Métricas | Expor métricas técnicas/operacionais (latência, erros, taxa de requisições) — ferramenta A definir. |
| Alertas | Alertas para erros elevados, indisponibilidade de dependências e comportamento anômalo (A definir). |