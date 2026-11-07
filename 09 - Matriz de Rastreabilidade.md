---
tags: [doalink, rastreabilidade, matriz]
---

# Matriz de Rastreabilidade

Relacionado: [[04 - Requisitos Funcionais/RF - Índice]] | [[05 - Requisitos Não Funcionais/RNF - Índice]] | [[06 - Regras de Negócio]]

> Matriz inicial para revisão. IDs de testes/evidências devem ser preenchidos quando casos de teste forem criados. Status inicial: **Rascunho**.

## Requisitos funcionais

| Necessidade/Origem | RF | RNs relacionadas | Critérios de aceite | Evidência/Teste | Status |
|---|---|---|---|---|---|
| Base: cadastro de perfis | RF-001 | RN-001, RN-002, RN-003, RN-004, RN-013, RN-014 | CA-001-1..5 | Pendente | Rascunho |
| Base: acesso seguro | RF-002 | RN-014, RN-016 | CA-002-1..4 | Pendente | Rascunho |
| Base: redefinição de senha | RF-003 | RN-014 | CA-003-01..06 | Pendente | Rascunho |
| Base: doador oferta itens | RF-004 | RN-005, RN-006, RN-015 | CA-004-1..2 | Pendente | Rascunho |
| Base: transportador oferta capacidade | RF-005 | RN-005, RN-015 | CA-005-1..2 | Pendente | Rascunho |
| Base: receptor registra necessidade | RF-006 | RN-005, RN-015 | CA-006-1..2 | Pendente | Rascunho |
| Base: matching e resposta | RF-007 | RN-005–RN-010, RN-012, RN-016 | CA-007-1..6 | Pendente | Rascunho |
| Base: emergência/campanha | RF-008 | RN-011, RN-012, RN-015 | CA-008-1..2 | Pendente | Rascunho |
| Base: acompanhamento | RF-009 | RN-008, RN-012, RN-016 | CA-009-1..2 | Pendente | Rascunho |
| Expansão: autogestão de conta | RF-010 | RN-002, RN-003, RN-010, RN-016 | CA-010-1..3 | Pendente | Rascunho |
| Expansão: descoberta | RF-011 | RN-010 | CA-011-1..2 | Pendente | Rascunho |
| Expansão: engajamento operacional | RF-012 | RN-010, RN-016 | CA-012-1..2 | Pendente | Rascunho |
| Expansão: governança | RF-013 | RN-011, RN-016 | A definir | Pendente | Rascunho |
| Expansão: qualidade de matching | RF-014 | RN-015 | A definir | Pendente | Rascunho |
| Expansão: gestão/indicadores | RF-015 | RN-010 | A definir | Pendente | Rascunho |
| Expansão: confiança/segurança operacional | RF-016 | RN-016 | A definir | Pendente | Rascunho |
| Expansão: conformidade LGPD | RF-017 | RN-010, RN-016 | CA-017-1..3 | Pendente | Rascunho |
| Expansão: confirmação de conta | RF-018 | RN-014 | CA-018-1..2 | Pendente | Rascunho |

## Requisitos não funcionais

| Necessidade/Origem | RNF | RFs impactados | Verificação sugerida | Status |
|---|---|---|---|---|
| Segurança de credenciais | RNF-001 | RF-001–003 | Inspeção, testes de API/banco | Rascunho |
| Controle de acesso | RNF-002 | RF-002, RF-004–RF-009, RF-010–RF-013 | Testes 401/403/propriedade | Rascunho |
| Resiliência a abuso | RNF-003 | RF-001–003, RF-018 | Testes de rate limit/enumeração | Rascunho |
| LGPD/privacidade | RNF-004 | RF-001, RF-010, RF-011, RF-017 | Revisão de dados e visibilidade | Rascunho |
| Consistência | RNF-005 | RF-001, RF-004–RF-009 | Testes de transação/concorrência | Rascunho |
| Disponibilidade | RNF-006 | Todos (serviço) | Monitoramento/SLO | Rascunho |
| Desempenho | RNF-007 | RF-002, RF-004–RF-007, RF-011 | Testes de carga/latência | Rascunho |
| Usabilidade/acessibilidade | RNF-008 | Fluxos de UI (cliente) | Testes de usabilidade/WCAG | Rascunho |
| Observabilidade | RNF-009 | Todos | Revisão de logs/métricas/auditoria | Rascunho |
| Manutenibilidade | RNF-010 | Todos | Revisão técnica/testes/CI | Rascunho |
| Implantação/operação | RNF-011 | Todos | Revisão de ambiente/pipeline | Rascunho |
| Interoperabilidade | RNF-012 | RF-001 (CNPJ/CEP), RF-012 | Testes de integração/contrato | Rascunho |
| Compatibilidade | RNF-013 | Cliente | Matriz de navegadores/dispositivos | Rascunho |
| Backup/DR | RNF-014 | Todos | Teste de restauração | Rascunho |

## Lacunas conhecidas
- Critérios de aceite dos RFs 013–016 precisam ser detalhados após validação de escopo.
- Métricas numéricas de RNF-006/007/014 dependem de decisões operacionais (PD-020).
- Casos de teste ainda não existem; coluna "Evidência/Teste" deve ser preenchida na fase de QA/spec.