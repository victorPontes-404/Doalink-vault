---
tags: [doalink, rf, termos, aceite, legal, importante]
id: RF-018
prioridade: Importante
origem: Expansão
---

# RF-018 — Termos de uso, políticas e aceite

**Prioridade:** Importante (sugestão; validar com jurídico)

## Descrição
O sistema deve apresentar Termos de Uso e Política de Privacidade, coletando ciência/aceite quando necessário antes de habilitar o cadastro ou funcionalidades sensíveis.

## Capacidades sugeridas
- Exibir versão vigente dos documentos.
- Registrar data/hora, versão aceita e contexto do aceite.
- Solicitar novo aceite quando houver mudança material relevante (política A definir).
- Disponibilizar acesso permanente aos documentos.

## Critérios de aceite (sugestão)
- **CA-018-1:** Dado cadastro com aceite obrigatório, quando o usuário não aceita os termos exigidos, então o sistema não conclui o cadastro.
- **CA-018-2:** Dado aceite registrado, quando consultado para auditoria legal/operacional autorizada, então o sistema apresenta evidência da versão e momento do aceite.