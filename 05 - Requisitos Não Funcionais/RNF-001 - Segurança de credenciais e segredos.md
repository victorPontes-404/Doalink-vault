---
tags: [doalink, rnf, segurança, credenciais]
id: RNF-001
prioridade: Essencial
---

# RNF-001 — Segurança de credenciais e segredos

**Categoria:** Segurança  
**Prioridade:** Essencial

## Declaração
O sistema deve proteger credenciais e segredos de forma que senhas, tokens e chaves não sejam expostos em texto puro, logs, respostas de API, mensagens de erro ou repositórios.

## Critérios e métricas
| Item | Requisito | Medição/Verificação |
|---|---|---|
| Senhas | Armazenar apenas hash com algoritmo apropriado para senhas (ex.: bcrypt/Argon2) e parâmetros revisados. | Inspeção de código/configuração; verificação em banco (nunca texto puro). |
| Tokens de recuperação/refresh | Gerar com alta entropia; preferir armazenar apenas hash quando comparável; expiração e uso único para recuperação. | Revisão de implementação e testes. |
| Segredos de aplicação | Chaves JWT, credenciais de banco, chaves de integração não devem estar hardcoded no código-fonte. Usar variáveis de ambiente/secret manager. | Revisão de repositório e pipeline. |
| Respostas/logs | Campos `senha`, `password`, hash, token completo e segredos não devem ser serializados em respostas normais nem logados. | Testes de API e revisão de logs. |
| Transporte | Credenciais e tokens transmitidos apenas por canal protegido (HTTPS em produção). | Teste de ambiente/configuração. |

## Critérios de aceite (verificáveis)
- **CA-RNF-001-1:** Dado um cadastro ou redefinição de senha, quando o dado é persistido, então não há senha em texto puro no banco.
- **CA-RNF-001-2:** Dada uma resposta de API de cadastro/login/perfil, quando inspecionada, então não contém senha, hash ou segredo.
- **CA-RNF-001-3:** Dada execução em ambiente produtivo, quando credenciais são transmitidas, então o canal usa HTTPS/TLS.

## Fonte/decisão
Boas práticas de segurança de aplicações; política de segredos a formalizar (A definir).