---
tags: [doalink, rf, senha, recuperação, essencial]
id: RF-003
prioridade: Essencial
origem: implementacao-doalink.md
---

# RF-003 — Recuperação de senha

**Prioridade:** Essencial  
**Origem:** Documento base (§4 RF-003)  
Relacionado: [[RF-002 - Autenticação e sessão]] | [[10 - Decisões Pendentes|PD-003, PD-004]]

## Descrição
O sistema deve permitir que o participante inicie a recuperação de senha informando o e-mail associado à conta. O sistema deve conduzir um fluxo seguro por **link ou código de uso único** (decisão pendente), validar a nova senha e atualizar a credencial.

## Decisões pendentes que afetam este RF
- Canal de envio (e-mail, SMS, ambos): PD-003.
- Formato do token/código, tamanho, validade, limite de tentativas e reuso: PD-003.
- Mensagem para e-mail inexistente (segurança vs. UX): PD-004.
- Política de senha: PD-004.

## Fluxo principal
1. Participante informa e-mail.
2. Sistema verifica se existe conta elegível.
3. Se elegível, sistema gera token/código protegido, com expiração e controle de uso, e envia pelo canal definido.
4. Participante acessa o fluxo com token/código válido e informa nova senha.
5. Sistema valida token/código e política de senha.
6. Sistema atualiza hash da senha, invalida token/código usado e (recomendado) invalida sessões/refresh tokens ativos conforme política.
7. Sistema confirma conclusão.

## Regras de segurança esperadas
- Token/código não deve ser previsível; armazenar apenas forma protegida (hash) quando aplicável.
- Expiração curta e uso único.
- Limitar tentativas e solicitações por conta/IP/canal (rate limit).
- Resposta inicial não deve facilitar enumeração de contas (definir mensagem neutra).

## Critérios de aceite
- **CA-003-01:** Dado e-mail cadastrado elegível, quando solicita recuperação, então o sistema inicia o fluxo vinculado à conta correspondente.
- **CA-003-02:** Dado e-mail não cadastrado, quando solicita recuperação, então o sistema não permite alterar outra conta (e adota resposta conforme política de segurança definida).
- **CA-003-03:** Dado fluxo válido e nova senha válida, quando conclui a redefinição, então o sistema atualiza a senha.
- **CA-003-04:** Dado fluxo inválido, expirado ou já usado, quando tenta redefinir, então o sistema rejeita e mantém a senha atual.
- **CA-003-05:** Após conclusão válida, a nova senha autentica.
- **CA-003-06:** Após conclusão válida, a senha anterior não autentica.