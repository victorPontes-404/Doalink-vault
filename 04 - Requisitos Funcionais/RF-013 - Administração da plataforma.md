---
tags: [doalink, rf, administração, governança, importante]
id: RF-013
prioridade: Importante
origem: Expansão
---

# RF-013 — Administração da plataforma

**Prioridade:** Importante (sugestão)

## Descrição
O sistema deve fornecer capacidades administrativas para operação, suporte, moderação e governança da plataforma.

## Capacidades sugeridas
- Gestão de usuários (consulta, bloqueio/desbloqueio, redefinição assistida — com auditoria).
- Gestão de campanhas (criação, edição, encerramento, arquivamento) se não delegada.
- Gestão de catálogos (itens, unidades, tipos de veículo).
- Visualização de auditoria e trilhas de eventos críticos.
- Tratamento de denúncias/suporte (RF-016).
- Configurações operacionais (limites, feature flags, mensagens institucionais) — com controle de acesso.

## Regras
- Acesso restrito a perfil administrativo.
- Ações administrativas devem ser auditáveis (quem, quando, o quê, antes/depois quando aplicável).
- Princípio do menor privilégio entre operadores (se houver múltiplos papéis admin).