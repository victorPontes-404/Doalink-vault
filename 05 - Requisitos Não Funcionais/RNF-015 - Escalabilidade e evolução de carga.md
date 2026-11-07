---
tags: [doalink, rnf, escalabilidade]
id: RNF-015
prioridade: Importante
---

# RNF-015 — Escalabilidade e evolução de carga

**Categoria:** Desempenho / Arquitetura operacional  
**Prioridade:** Importante

## Declaração
O sistema deve suportar crescimento de usuários, registros e picos de acesso (ex.: campanhas emergenciais) sem redesign completo.

## Critérios
- Arquitetura stateless para componentes de aplicação quando viável (facilita escala horizontal).
- Consultas paginadas e indexadas; matching pesado pode ser assíncrono.
- Capacidade alvo (usuários simultâneos, registros/dia, picos): **A definir**.
- Testes de carga antes de eventos/campanhas de grande porte (recomendado).