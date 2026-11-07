---
tags: [doalink, fluxos, jornada]
---

# Fluxos Principais

Relacionado: [[04 - Requisitos Funcionais/RF - Índice]] | [[07 - Modelo de Dados e Domínio]]

## 1. Cadastro e acesso
```text
Visitante escolhe perfil
  -> preenche dados comuns (+ CNPJ/endereço se Receptor)
  -> sistema valida/normaliza/verifica unicidade
  -> cria participante + identificador
  -> (opcional) confirmação de e-mail
  -> login com e-mail/senha
  -> sessão/token emitido
  -> acesso às funções do perfil
  -> logout / recuperação de senha quando necessário
```
**RFs:** RF-001, RF-002, RF-003, RF-018.

## 2. Oferta, necessidade e transporte
```text
Doador cadastra oferta
Receptor cadastra necessidade (opcionalmente vinculada a campanha)
Transportador cadastra disponibilidade
  -> registros ficam elegíveis conforme estado/visibilidade
  -> sistema/usuários consultam (RF-011)
```
**RFs:** RF-004, RF-005, RF-006, RF-008, RF-011, RF-014.

## 3. Matching e proposta
```text
Sistema avalia compatibilidade (item, quantidade/unidade, local/rota, data)
  -> encontra combinação viável
  -> cria proposta (oferta + necessidade [+ transporte])
  -> notifica envolvidos (RF-012)
  -> participantes respondem: aceitar/recusar
  -> sistema consolida respostas
  -> proposta confirmada, recusada ou expirada
```
**RFs:** RF-007, RF-012.

## 4. Emergência
```text
Usuário autorizado cria campanha + região + necessidades
  -> receptores associam necessidades
  -> doadores/transportadores consultam campanhas
  -> matching prioriza/considera contexto emergencial (regra a definir)
  -> acompanhamento operacional
```
**RFs:** RF-008, RF-006, RF-007, RF-011, RF-015.

## 5. Acompanhamento da doação
```text
Proposta confirmada
  -> situação OFERTADA/COMBINADA
  -> coleta/transporte iniciado -> EM_TRANSPORTE
  -> entrega concluída -> ENTREGUE
  -> histórico registra data/hora/responsável
  -> participantes autorizados consultam
```
**RFs:** RF-009, RF-007, RF-012. Transições e responsáveis: **A definir**.

## 6. Privacidade e suporte (transversal)
```text
Titular solicita acesso/correção/exclusão
  -> sistema autentica titular
  -> registra solicitação
  -> avalia elegibilidade legal/operacional
  -> executa ou responde conforme política
```
**RFs:** RF-017, RF-013. Requer política jurídica/procedimento definido.