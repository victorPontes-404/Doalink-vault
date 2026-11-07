---
tags: [doalink, rf, email, confirmação, conta, importante]
id: RF-018
prioridade: Importante
origem: Expansão (relacionada a PD-003)
---

# RF-018 — Confirmação e gestão de conta/e-mail

**Prioridade:** Importante (sugestão)

## Descrição
O sistema deve suportar confirmação de e-mail e fluxos seguros de alteração de e-mail, quando essa estratégia for adotada.

## Capacidades sugeridas
- Enviar link/código de confirmação após cadastro.
- Marcar conta como confirmada/pendente.
- Restringir ações sensíveis enquanto pendente (política a definir).
- Reenviar confirmação com rate limit.
- Ao alterar e-mail, confirmar posse do novo endereço antes de efetivar troca.

## Critérios de aceite (sugestão)
- **CA-018-1:** Dado cadastro com confirmação habilitada, quando o usuário confirma o e-mail por meio válido, então a conta passa ao estado confirmado.
- **CA-018-2:** Dado token de confirmação inválido/expirado, quando usado, então o sistema rejeita e mantém o estado anterior.