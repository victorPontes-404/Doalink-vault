---
tags: [doalink, rf, perfil, conta, importante]
id: RF-010
prioridade: Importante
origem: Expansão (sugerido)
---

# RF-010 — Gestão do perfil do participante

**Prioridade:** Importante (sugestão)  
**Origem:** Expansão — lacuna comum após cadastro.

## Descrição
O sistema deve permitir que participantes autenticados consultem e atualizem dados do próprio perfil, respeitando campos imutáveis, validações e regras de segurança.

## Capacidades sugeridas
- Visualizar dados cadastrais (com mascaramento adequado).
- Atualizar nome, telefone e, quando aplicável, endereço.
- Solicitar alteração de e-mail com confirmação no novo endereço (ver RF-018).
- Alterar senha informando senha atual (ou fluxo equivalente seguro).
- Visualizar perfil/tipo de conta e status.
- Desativar/encerrar conta (com tratamento LGPD e impacto em registros ativos) — **A definir**.

## Regras
- Documento/CPF/CNPJ: alteração deve ser excepcional, auditada e sujeita a política (geralmente imutável ou mediante suporte).
- Identificador interno: não editável.
- Alterações sensíveis devem gerar registro de auditoria.

## Critérios de aceite (sugestão)
- **CA-010-1:** Dado participante autenticado, quando acessa seu perfil, então visualiza seus dados conforme permissões.
- **CA-010-2:** Dado participante autenticado, quando atualiza campo permitido com valor válido, então o sistema persiste a alteração.
- **CA-010-3:** Dado participante, quando tenta alterar campo não permitido ou de outro participante, então o sistema rejeita.