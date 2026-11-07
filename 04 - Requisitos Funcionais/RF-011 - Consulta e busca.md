---
tags: [doalink, rf, consulta, busca, filtros, importante]
id: RF-011
prioridade: Importante
origem: Expansão
---

# RF-011 — Consulta e busca de ofertas, necessidades e transportes

**Prioridade:** Importante (sugestão)

## Descrição
O sistema deve permitir consultar e filtrar ofertas, necessidades e disponibilidades de transporte de forma eficiente, respeitando regras de visibilidade por perfil e estado.

## Filtros sugeridos
- Categoria/item, quantidade/unidade.
- Localização (cidade/UF/região/raio — conforme PD-008).
- Data/janela de disponibilidade.
- Estado (aberta, ativa, expirada, etc.).
- Campanha associada.
- Ordenação (mais recente, mais próxima, maior urgência — a definir).

## Regras
- Visitantes podem ter acesso limitado (dados públicos) — **A definir**.
- Dados de contato pessoais só aparecem conforme autorização/envolvimento.
- Paginação obrigatória para listas.

## Critérios de aceite (sugestão)
- **CA-011-1:** Dado usuário autorizado, quando aplica filtros válidos, então o sistema retorna resultados compatíveis com a visibilidade permitida.
- **CA-011-2:** Dado grande volume de registros, quando consulta, então o sistema retorna resultados paginados.