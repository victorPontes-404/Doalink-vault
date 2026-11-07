---
tags: [doalink, rf, catálogos, padronização, importante]
id: RF-014
prioridade: Importante
origem: Expansão (relacionada a PD-006)
---

# RF-014 — Catálogos e padronização

**Prioridade:** Importante (sugestão)

## Descrição
O sistema deve utilizar catálogos padronizados para categorias de itens, unidades de medida e tipos de veículo, garantindo comparabilidade no matching e consistência de dados.

## Catálogos sugeridos
- **Categorias de itens:** alimentos perecíveis/não perecíveis, higiene, roupas, medicamentos, móveis/eletrodomésticos, materiais de limpeza, etc. (validar com negócio e restrições legais — ex.: medicamentos).
- **Unidades:** unidade, kg, g, litro, ml, caixa, pacote, pallet; definir conversões permitidas.
- **Tipos de veículo:** moto, carro, utilitário, van, caminhão pequeno/médio/grande, etc.
- **Estados/situações:** enums controlados para ofertas, necessidades, propostas, campanhas e doações.

## Regras
- Valores governados por tabela/domínio quando houver necessidade de evolução sem deploy (conforme observação técnica do documento base).
- Conversões de unidade só podem ser aplicadas quando houver regra explícita e segura.
- Mudanças em catálogos devem considerar impacto em registros históricos.