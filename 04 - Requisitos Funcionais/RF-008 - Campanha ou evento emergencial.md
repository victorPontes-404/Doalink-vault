---
tags: [doalink, rf, campanha, emergência, essencial]
id: RF-008
prioridade: Essencial
origem: implementacao-doalink.md
---

# RF-008 — Campanha ou evento emergencial

**Prioridade:** Essencial  
**Origem:** Documento base (§4 RF-008)  
Relacionado: [[RF-006 - Necessidade de doação]] | [[RF-007 - Sugestão e resposta a combinações]] | [[03 - Perfis e Permissões]]

## Descrição
O sistema deve permitir o cadastro de campanhas/desastres com região afetada e necessidades emergenciais. Necessidades devem poder ser relacionadas a itens e quantidades, e receptores podem associar necessidades à campanha.

## Atores
- Usuário autorizado para criar campanha (perfil/papel **A definir** — PD-011).
- Receptores (associam necessidades, se permitido).
- Doadores/transportadores (consultam e participam via ofertas/disponibilidades).

## Campos mínimos

| Campo | Obrigatório | Observações |
|---|:---:|---|
| Nome/título da campanha | Sim | Identificação clara. |
| Descrição/contexto | Recomendado | Tipo de evento, orientações. **Sugestão**. |
| Região afetada | Sim | Formato (UF, cidade, polígono, raio, lista de CEPs): **A definir**. |
| Data de início | Sim/**A definir** | — |
| Data de término/encerramento | **A definir** | Encerramento/arquivamento: PD-011. |
| Estado | Sim | Ex.: ativa, encerrada, arquivada. |
| Necessidades emergenciais | Sim | Relacionadas a itens e quantidades. |

## Critérios de aceite
- **CA-008-1:** Dado usuário autorizado, quando cadastra campanha com região e necessidades, então o sistema registra a campanha.
- **CA-008-2:** Dada campanha registrada, quando participantes consultam necessidades ou o sistema gera sugestões, então a campanha participa conforme regras de visibilidade e compatibilidade.

## Estado atual
- Não implementado.