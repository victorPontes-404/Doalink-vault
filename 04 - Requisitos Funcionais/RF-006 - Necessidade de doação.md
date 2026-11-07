---
tags: [doalink, rf, necessidade, receptor, essencial]
id: RF-006
prioridade: Essencial
origem: implementacao-doalink.md
---

# RF-006 — Necessidade de doação

**Prioridade:** Essencial  
**Origem:** Documento base (§4 RF-006)  
Relacionado: [[RF-004 - Oferta de doação]] | [[RF-008 - Campanha ou evento emergencial]] | [[RF-007 - Sugestão e resposta a combinações]]

## Descrição
O sistema deve permitir que receptores autenticados cadastrem necessidades de doação com item/categoria, quantidade/unidade e local de entrega. Necessidades podem ser associadas a campanhas emergenciais.

## Atores
- Receptor.

## Campos mínimos

| Campo | Obrigatório | Validação e observações |
|---|:---:|---|
| Item/categoria | Sim | Categorias compatíveis com ofertas (PD-006). |
| Quantidade | Sim | Positiva. |
| Unidade | Sim | Compatível/conversível. |
| Local de entrega | **A definir** | Documento questiona se endereço completo é obrigatório; receptor já possui endereço cadastral. |
| Campanha associada | Não | Quando a necessidade fizer parte de campanha (RF-008). |
| Urgência/prioridade | Não | **Sugestão** para emergências. |
| Estado | **A definir** | Aberta, parcialmente atendida, atendida, cancelada, expirada. |

## Critérios de aceite
- **CA-006-1:** Dado receptor autenticado, quando informa necessidade completa e válida, então o sistema registra a necessidade.
- **CA-006-2:** Dada necessidade registrada e elegível, quando há consulta ou análise de compatibilidade, então fica disponível conforme regras de visibilidade.

## Estado atual
- Não há entidade/fluxo de necessidade implementado no estado analisado.