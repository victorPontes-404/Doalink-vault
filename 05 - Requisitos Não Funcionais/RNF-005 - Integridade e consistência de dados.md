---
tags: [doalink, rnf, integridade, dados]
id: RNF-005
prioridade: Essencial
---

# RNF-005 — Integridade e consistência de dados

**Categoria:** Confiabilidade  
**Prioridade:** Essencial

## Declaração
O sistema deve preservar a integridade e consistência dos dados, evitando cadastros duplicados indevidos, transições de estado inválidas e registros órfãos/parciais.

## Critérios
| Item | Requisito | Verificação |
|---|---|---|
| Unicidade | CPF/CNPJ e e-mail únicos conforme regra definida; enforced por validação + constraint de banco. | Testes e schema. |
| Transações | Operações compostas (cadastro + endereço, criação de proposta + respostas, atualização de estado + histórico) devem ser atômicas quando aplicável. | Testes de falha/rollback. |
| Validação server-side | Toda validação crítica ocorre no servidor, mesmo com validação no cliente. | Testes de API. |
| Estados | Transições de proposta/doação seguem máquina de estados definida; rejeitar transições inválidas. | Testes de domínio. |
| Concorrência | Definir estratégia para respostas simultâneas, reserva de saldo e expiração (otimista/pessimista/constraints). | Testes de concorrência. |
| Normalização | Dados persistidos em formato canônico (documentos, e-mail, CEP/telefone). | Testes. |
| Precisão numérica | Quantidades/capacidades com tipo adequado (evitar erros de ponto flutuante em comparações críticas). | Revisão de modelo. |