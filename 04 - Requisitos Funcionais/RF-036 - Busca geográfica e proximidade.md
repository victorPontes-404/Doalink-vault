---
tags: [doalink, rf, localização, mapa, desejável]
id: RF-036
prioridade: Desejável
origem: Expansão (relacionada a PD-008)
---

# RF-036 — Busca geográfica e proximidade

**Prioridade:** Desejável (sugestão)

## Descrição
O sistema deve apoiar busca por proximidade geográfica entre origem, coleta e entrega, quando o modelo de localização for definido.

## Capacidades sugeridas
- Filtrar por cidade/UF/região/raio.
- Ordenar por proximidade estimada.
- Exibir mapa (se houver componente de UI) — cuidado com custo e privacidade.
- Considerar rota de transporte (origem-destino) além de distância linear (A definir).

## Regras
- Não expor endereço exato de terceiros sem autorização; pode usar granularidade reduzida (cidade/bairro/região) em listagens públicas.
- Depende de PD-008 e eventual geocodificação (RF-025).