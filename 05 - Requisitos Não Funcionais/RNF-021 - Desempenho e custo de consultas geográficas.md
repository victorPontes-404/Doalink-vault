---
tags: [doalink, rnf, desempenho, geo]
id: RNF-021
prioridade: Desejável
---

# RNF-021 — Desempenho e custo de consultas geográficas

**Categoria:** Desempenho  
**Prioridade:** Desejável (se RF-036/RF-025 adotados)

## Declaração
Consultas por proximidade/rota devem ter desempenho aceitável e custo controlado.

## Critérios
- Uso de índices geoespaciais ou estratégia equivalente quando aplicável.
- Limites de raio/página para evitar consultas abusivas.
- Cache para geocodificação e resultados estáveis quando possível.
- Metas de latência: A definir.