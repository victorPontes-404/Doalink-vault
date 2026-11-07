---
tags: [doalink, rf, notificações, comunicação, importante]
id: RF-012
prioridade: Importante
origem: Expansão
---

# RF-012 — Notificações e comunicações do sistema

**Prioridade:** Importante (sugestão)

## Descrição
O sistema deve notificar participantes sobre eventos relevantes (nova proposta, resposta recebida, mudança de estado, campanha urgente, expiração, recuperação de senha), por canais definidos.

## Canais possíveis (A definir)
- E-mail (provável para eventos críticos).
- Notificação in-app.
- Push (se houver app mobile).

## Eventos candidatos
- Proposta criada/enviada para o participante.
- Proposta aceita/recusada por outro envolvido.
- Proposta confirmada/expirada/cancelada.
- Situação da doação atualizada (RF-009).
- Campanha emergencial relevante na região/interesse.
- Recuperação de senha / confirmação de conta.

## Regras
- Respeitar preferências de notificação do usuário (opt-in/opt-out onde legalmente aplicável).
- Não expor dados sensíveis desnecessários no conteúdo da notificação.
- Registrar envio/falha para suporte e auditoria operacional.

## Critérios de aceite (sugestão)
- **CA-012-1:** Dado evento notificável e participante elegível, quando o evento ocorre, então o sistema gera notificação pelo canal configurado.
- **CA-012-2:** Dado participante com preferência de canal definida, quando aplicável, então o sistema respeita a preferência.