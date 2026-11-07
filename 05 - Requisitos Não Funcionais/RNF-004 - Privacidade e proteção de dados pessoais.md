---
tags: [doalink, rnf, lgpd, privacidade]
id: RNF-004
prioridade: Essencial
---

# RNF-004 — Privacidade e proteção de dados pessoais

**Categoria:** Privacidade / LGPD  
**Prioridade:** Essencial (validação jurídica recomendada)

## Declaração
O sistema deve coletar, usar, armazenar e compartilhar dados pessoais apenas para finalidades legítimas e proporcionais, com transparência, segurança e respeito aos direitos do titular.

## Critérios
| Item | Requisito |
|---|---|
| Minimização | Coletar apenas dados necessários para o fluxo (ex.: evitar pedir dados sem finalidade). |
| Finalidade | Documentar finalidade de CPF/CNPJ, e-mail, telefone, endereço e localização. |
| Acesso | Expor dados de contato/pessoais de terceiros somente quando necessário ao fluxo autorizado (ex.: participantes envolvidos em proposta confirmada) — política A definir. |
| Retenção | Definir prazos de guarda, anonimização/exclusão e tratamento de contas inativas — A definir. |
| Transparência | Disponibilizar política de privacidade e informações de contato do controlador/DPO quando aplicável. |
| Direitos do titular | Suportar fluxos funcionais de acesso, correção e exclusão/anonimização conforme aplicável (RF-017). |
| Registros | Consentimentos/preferências rastreáveis quando base legal exigir. |

## Verificação
- Revisão de campos coletados por tela/endpoint.
- Revisão de visibilidade de dados em listagens, propostas e relatórios.
- Testes de autorização para acesso a dados pessoais.