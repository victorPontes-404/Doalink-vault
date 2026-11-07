---
tags: [doalink, rf, lgpd, privacidade, dados-pessoais, essencial]
id: RF-017
prioridade: Essencial (conformidade) — validação jurídica recomendada
origem: Expansão
---

# RF-017 — Privacidade, consentimento e direitos do titular (LGPD)

**Prioridade:** Essencial para conformidade (sugestão; validar com jurídico/DPO)

## Descrição
O sistema deve tratar dados pessoais com finalidade legítima, minimização, segurança e transparência, e oferecer mecanismos para atendimento de direitos do titular, conforme aplicável à LGPD.

> **Nota:** este RF descreve capacidades funcionais esperadas; a base legal, textos de consentimento, política de privacidade e prazos devem ser definidos com assessoria jurídica.

## Capacidades sugeridas
- Apresentar política de privacidade e, quando aplicável, coletar consentimento/ciência no cadastro.
- Permitir consulta/exportação de dados do próprio titular (portabilidade/acesso, conforme aplicável).
- Permitir solicitação de correção de dados.
- Permitir solicitação de exclusão/anonimização, observadas obrigações legais, guarda de registros e impacto em integridade operacional.
- Registrar consentimentos e preferências de comunicação.
- Minimizar exposição de dados pessoais a outros participantes (ex.: exibir contato apenas quando houver envolvimento/proposta confirmada).

## Critérios de aceite (sugestão)
- **CA-017-1:** Dado titular autenticado, quando solicita acesso aos seus dados, então o sistema fornece os dados previstos pela política aplicável.
- **CA-017-2:** Dado titular, quando solicita correção/exclusão elegível, então o sistema registra e processa a solicitação conforme fluxo definido.
- **CA-017-3:** Dados pessoais sensíveis/contato não são expostos a usuários sem finalidade/permissão.