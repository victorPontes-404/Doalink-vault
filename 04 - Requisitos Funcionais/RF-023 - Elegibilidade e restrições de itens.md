---
tags: [doalink, rf, compliance, itens-regulados, importante]
id: RF-023
prioridade: Importante (se aplicável)
origem: Expansão
---

# RF-023 — Elegibilidade e restrições de itens

**Prioridade:** Importante quando o catálogo incluir itens regulados (sugestão)

## Descrição
O sistema deve aplicar restrições para categorias de itens que exigem tratamento especial (ex.: medicamentos, alimentos perecíveis, itens perigosos), conforme política legal/operacional definida.

## Exemplos de restrições possíveis (validar)
| Categoria | Possível restrição |
|---|---|
| Medicamentos | Exigir informações específicas, restringir perfis, impedir publicação aberta ou exigir validação — **alto risco/compliance**. |
| Alimentos perecíveis | Exigir validade, condições de armazenamento/transporte e janela curta. |
| Itens usados | Exigir condição/estado e fotos. |
| Itens perigosos | Proibir ou tratar por fluxo especial. |

## Regra
- **CA-023-1:** Dado participante autorizado, quando consulta elegibilidade de item regulado, então o sistema aplica as restrições definidas na política.