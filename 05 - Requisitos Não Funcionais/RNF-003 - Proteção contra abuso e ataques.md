---
tags: [doalink, rnf, segurança, abuso, rate-limit]
id: RNF-003
prioridade: Essencial
---

# RNF-003 — Proteção contra abuso e ataques comuns

**Categoria:** Segurança  
**Prioridade:** Essencial

## Declaração
O sistema deve reduzir risco de ataques e abuso automatizado, aplicando validações, limites e controles defensivos.

## Controles sugeridos
| Risco | Controle | Verificação |
|---|---|---|
| Força bruta / credential stuffing | Rate limit em login, recuperação de senha e confirmação; bloqueio temporário/captcha conforme política. | Testes controlados e configuração. |
| Enumeração de contas | Respostas neutras em recuperação/login quando aplicável. | Testes. |
| Injeção (SQL, NoSQL, comandos) | Uso de ORM parametrizado/prepared statements; validação de entrada. | Revisão e testes. |
| XSS/CSRF (conforme arquitetura) | Escape/sanitização em saída; proteção CSRF quando houver cookies de sessão; cabeçalhos de segurança. | Revisão e testes. |
| Uploads (futuro) | Se houver anexos/imagens: validação de tipo/tamanho, armazenamento seguro, antivírus/scan conforme risco. | A definir. |
| Exposição de dados | Princípio do menor dado; DTOs de resposta sem campos sensíveis. | Revisão de API. |
| Dependências vulneráveis | Monitorar CVEs e atualizar dependências. | Processo de manutenção. |

## Métricas (A definir)
- Limite de tentativas de login por IP/conta/janela.
- Limite de solicitações de recuperação por e-mail/janela.
- Tempo de bloqueio temporário.

## Critérios de aceite
- **CA-RNF-003-1:** Dada sequência excessiva de tentativas de login/recovery, quando ultrapassa o limite definido, então o sistema aplica controle (atraso, bloqueio temporário ou captcha).