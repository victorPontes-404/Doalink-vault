---
tags: [doalink, rnf, requisitos-não-funcionais, índice]
---

# Requisitos Não Funcionais — Índice

Relacionado: [[00 - Início]] | [[09 - Matriz de Rastreabilidade]]

## Contexto
O documento base `implementacao-doalink.md` **não define requisitos não funcionais (RNFs)**. Este conjunto foi elaborado para cobrir qualidades e restrições esperadas para uma plataforma que trata dados pessoais, autenticação, coordenação de doações e possíveis cenários de emergência.

> **Importante:** valores numéricos (tempos, percentuais, capacidade) abaixo são **sugestões iniciais** e devem ser calibrados com stakeholders, infraestrutura alvo, orçamento e perfil de uso. Onde não houver decisão, manter como *A definir* com critério de medição.

## Catálogo

| ID | Categoria | Título | Prioridade sugerida | Documento |
|---|---|---|---|---|
| RNF-001 | Segurança | Proteção de credenciais e segredos | Essencial | [[RNF-001 - Segurança de credenciais e segredos]] |
| RNF-002 | Segurança | Autenticação, sessão e controle de acesso | Essencial | [[RNF-002 - Autenticação sessão e controle de acesso]] |
| RNF-003 | Segurança | Proteção contra abuso e ataques comuns | Essencial | [[RNF-003 - Proteção contra abuso e ataques]] |
| RNF-004 | Privacidade/LGPD | Proteção de dados pessoais | Essencial | [[RNF-004 - Privacidade e proteção de dados pessoais]] |
| RNF-005 | Confiabilidade | Integridade e consistência de dados | Essencial | [[RNF-005 - Integridade e consistência de dados]] |
| RNF-006 | Disponibilidade | Disponibilidade e continuidade do serviço | Importante | [[RNF-006 - Disponibilidade e continuidade]] |
| RNF-007 | Desempenho | Tempo de resposta e capacidade | Importante | [[RNF-007 - Desempenho e capacidade]] |
| RNF-008 | Usabilidade/Acessibilidade | Experiência de uso e acessibilidade | Importante | [[RNF-008 - Usabilidade e acessibilidade]] |
| RNF-009 | Observabilidade | Logs, auditoria e monitoramento | Importante | [[RNF-009 - Observabilidade auditoria e monitoramento]] |
| RNF-010 | Manutenibilidade | Qualidade técnica e evolutividade | Importante | [[RNF-010 - Manutenibilidade e qualidade técnica]] |
| RNF-011 | Portabilidade/Operação | Implantação, configuração e ambientes | Importante | [[RNF-011 - Implantação configuração e operação]] |
| RNF-012 | Interoperabilidade | APIs e integrações externas | Desejável | [[RNF-012 - Interoperabilidade e integrações]] |
| RNF-013 | Compatibilidade | Navegadores, dispositivos e clientes | Importante | [[RNF-013 - Compatibilidade de clientes]] |
| RNF-014 | Backup/Recuperação | Backup e recuperação de desastres | Importante | [[RNF-014 - Backup e recuperação de desastres]] |
| RNF-015 | Escalabilidade | Escalabilidade e evolução de carga | Importante | [[RNF-015 - Escalabilidade e evolução de carga]] |
| RNF-016 | Resiliência | Resiliência de integrações externas | Importante | [[RNF-016 - Resiliência de integrações externas]] |
| RNF-017 | Acessibilidade | Acessibilidade detalhada (WCAG) | Importante | [[RNF-017 - Acessibilidade detalhada (WCAG)]] |
| RNF-018 | Processo | Rastreabilidade e governança de requisitos | Desejável | [[RNF-018 - Rastreabilidade e governança de requisitos]] |
| RNF-019 | Privacidade/Operação | Proteção de dados em ambientes não produtivos | Importante | [[RNF-019 - Proteção de dados em ambientes não produtivos]] |
| RNF-020 | Privacidade/Comunicação | Gestão de consentimento e preferências de comunicação | Importante | [[RNF-020 - Gestão de consentimento e preferências de comunicação]] |
| RNF-021 | Desempenho | Desempenho e custo de consultas geográficas | Desejável | [[RNF-021 - Desempenho e custo de consultas geográficas]] |
| RNF-022 | Compliance | Legalidade e conformidade operacional de itens | Importante (se aplicável) | [[RNF-022 - Legalidade e conformidade operacional de itens]] |

## Convenções
- Cada RNF deve ter: **declaração**, **métrica/critério** (ou *A definir*), **condição de medição**, **método de verificação** e **fonte/decisão**.
- RNFs não descrevem telas ou classes; descrevem propriedades que o sistema deve satisfazer.