---
tags: [doalink, rnf, desempenho, capacidade]
id: RNF-007
prioridade: Importante
---

# RNF-007 — Desempenho e capacidade

**Categoria:** Desempenho  
**Prioridade:** Importante

## Declaração
O sistema deve responder em tempo adequado para operações comuns e suportar crescimento esperado de usuários e registros.

## Métricas sugeridas (A definir)
| Cenário | Métrica sugerida | Condição |
|---|---|---|
| Login/cadastro | P95 < 2s (excluindo latência externa extrema) | Carga nominal. |
| Listagens paginadas | P95 < 2s | Página padrão, filtros comuns, índices adequados. |
| Criação de oferta/necessidade | P95 < 2s | Carga nominal. |
| Geração de sugestões (matching) | A definir | Pode ser assíncrona/batch dependendo da complexidade. |

## Critérios
- Paginação em todas as listagens.
- Índices para consultas frequentes (e-mail, documento, estado, datas, chaves de matching).
- Operações pesadas de matching podem ser assíncronas, com estado de processamento visível (A definir).
- Definir limites de payload e tamanho de página.