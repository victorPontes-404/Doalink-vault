---
tags: [doalink, rnf, manutenibilidade, qualidade]
id: RNF-010
prioridade: Importante
---

# RNF-010 — Manutenibilidade e qualidade técnica

**Categoria:** Manutenibilidade  
**Prioridade:** Importante

## Declaração
O sistema deve ser evolutivo, testável e compreensível, com padrões consistentes de código e arquitetura.

## Critérios
| Item | Requisito |
|---|---|
| Arquitetura | Separar responsabilidades (controller/service/repository/DTO), conforme convenções do projeto. |
| Testes | Cobrir regras de negócio críticas e caminhos de erro; testes automatizados para autenticação, autorização e validações principais. Meta de cobertura: A definir (evitar meta numérica sem qualidade). |
| Migrations | Mudanças de schema versionadas (Flyway). |
| Documentação técnica | APIs documentadas (OpenAPI/Swagger, A definir); decisões arquiteturais registradas quando relevante. |
| Padrões | Convenções de nomenclatura, tratamento de erros e validação consistentes. |
| Revisão | Mudanças relevantes passam por revisão (PR) — processo de equipe. |