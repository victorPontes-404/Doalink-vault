---
tags: [doalink, rf, agendamento, logística, desejável]
id: RF-020
prioridade: Desejável
origem: Expansão
---

# RF-020 — Agendamento de coleta e entrega

**Prioridade:** Desejável (sugestão)

## Descrição
O sistema deve apoiar o agendamento de janelas de coleta/entrega entre participantes envolvidos em uma proposta confirmada.

## Capacidades sugeridas
- Definir janela sugerida (data/horário início-fim) na proposta ou após confirmação.
- Participantes envolvidos podem propor/confirmar horários (fluxo A definir).
- Registrar endereço/ponto de coleta e entrega confirmado.
- Registrar observações logísticas (portaria, contato no local, restrições).
- Integrar com notificações (RF-012) e acompanhamento (RF-009).

## Regras
- Apenas envolvidos podem alterar agendamento.
- Mudanças relevantes devem atualizar histórico/notificação.
- Agendamento não substitui execução logística real; é coordenação de informação.

## Critérios de aceite (sugestão)
- **CA-020-1:** Dada proposta confirmada e participante envolvido, quando registra janela de coleta/entrega válida, então o sistema persiste o agendamento.
- **CA-020-2:** Dado conflito de permissão, quando usuário não envolvido tenta alterar agendamento, então o sistema nega.