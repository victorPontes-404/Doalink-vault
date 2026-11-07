---
tags: [doalink, rnf, segurança, autenticação, autorização]
id: RNF-002
prioridade: Essencial
---

# RNF-002 — Autenticação, sessão e controle de acesso

**Categoria:** Segurança  
**Prioridade:** Essencial

## Declaração
O sistema deve garantir que apenas usuários autenticados e autorizados acessem funcionalidades e dados protegidos, com sessões/tokens controlados por expiração, revogação e escopo.

## Critérios e métricas
| Item | Requisito | Verificação |
|---|---|---|
| Autorização por perfil | Endpoints protegidos validam identidade e papel/perfil no servidor. | Testes de autorização (401/403). |
| Propriedade de recurso | Usuário só altera/consulta recursos próprios quando aplicável (oferta, necessidade, disponibilidade). | Testes de acesso indevido. |
| Expiração | Tokens de acesso com TTL curto (sugestão: 5–15 min, A definir); refresh com TTL maior e revogável. | Configuração e testes. |
| Revogação | Logout invalida refresh token/sessão aplicável; redefinição de senha pode revogar sessões ativas (política A definir). | Testes. |
| Cookies (se usados) | `HttpOnly`, `Secure` (produção), `SameSite` adequado; escopo mínimo. | Inspeção de resposta/configuração. |
| Falhas de autenticação | Mensagem genérica; sem diferenciar "e-mail inexistente" vs "senha incorreta" por padrão. | Testes de API. |

## Critérios de aceite
- **CA-RNF-002-1:** Dado visitante sem credenciais válidas, quando acessa endpoint protegido, então recebe 401 (ou equivalente).
- **CA-RNF-002-2:** Dado usuário autenticado com perfil sem permissão, quando acessa ação restrita, então recebe 403.
- **CA-RNF-002-3:** Dado participante A, quando tenta responder/alterar recurso do participante B sem autorização, então o sistema nega.