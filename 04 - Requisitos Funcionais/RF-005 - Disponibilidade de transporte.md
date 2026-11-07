---
tags: [doalink, rf, transporte, essencial]
id: RF-005
prioridade: Essencial
origem: implementacao-doalink.md
---

# RF-005 — Disponibilidade de transporte

**Prioridade:** Essencial  
**Origem:** Documento base (§4 RF-005)  
Relacionado: [[RF-007 - Sugestão e resposta a combinações]] | [[RF-014 - Catálogos e padronização]]

## Descrição
O sistema deve permitir que transportadores autenticados cadastrem disponibilidades de transporte com tipo de veículo, capacidade/unidade, origem, destino e data (com horário quando necessário).

## Atores
- Transportador.

## Campos mínimos

| Campo | Obrigatório | Validação e observações |
|---|:---:|---|
| Tipo de veículo | Sim | Categorias: **A definir** (PD-006). |
| Capacidade | Sim | Positiva. Significado/unidade: **A definir** (kg, m³, pallets, itens). |
| Unidade de capacidade | Sim/**A definir** | Necessária para comparação com ofertas/necessidades. |
| Origem | Sim | Formato (CEP, cidade/UF, coordenadas): **A definir** (PD-008). |
| Destino/região | Sim | Granularidade (ponto, cidade, raio, região): **A definir**. |
| Data | Sim | Precisão temporal e janela: **A definir** (PD-009). Horário opcional conforme necessidade. |
| Observações/restrições | Não | Ex.: tipos de item aceitos, necessidade de agendamento. **Sugestão**. |

## Critérios de aceite
- **CA-005-1:** Dado transportador autenticado, quando informa disponibilidade completa e válida, então o sistema registra a disponibilidade.
- **CA-005-2:** Dada disponibilidade registrada, quando o sistema sugere combinações, então considera capacidade, origem, destino e data conforme regras de compatibilidade.

## Estado atual
- Existe a entidade/perfil `Transportador`, mas **não há entidade de disponibilidade de transporte** nem fluxo de cadastro implementado.