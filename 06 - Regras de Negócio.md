---
tags: [doalink, regras-de-negócio, rn]
---

# Regras de Negócio (RN)

Relacionado: [[04 - Requisitos Funcionais/RF - Índice]] | [[05 - Requisitos Não Funcionais/RNF - Índice]] | [[07 - Modelo de Dados e Domínio]]

## Catálogo

| ID | Nome | Descrição | RFs relacionados |
|---|---|---|---|
| RN-001 | Documento por perfil | Doador/transportador informam CPF **ou** CNPJ (excludentes). Receptor informa CNPJ. | RF-001 |
| RN-002 | Unicidade de identificação | CPF/CNPJ e e-mail devem ser únicos conforme política de contas ativas/inativas. | RF-001, RF-010 |
| RN-003 | Normalização e máscara | CPF/CNPJ/CEP/telefone armazenados normalizados; máscara é só apresentação. | RF-001, RF-010 |
| RN-004 | Identificador automático | Identificador do participante é gerado pelo sistema e não editável. Visibilidade ao usuário: PD-013. | RF-001 |
| RN-005 | Quantidade positiva e compatibilidade de unidade | Quantidades/capacidades > 0. Matching exige unidade compatível ou conversão definida. | RF-004, RF-005, RF-006, RF-007 |
| RN-006 | Saldo e parcialização *(A definir)* | Definir se oferta pode atender múltiplas necessidades e como reservar/baixar saldo sem exceder. | RF-004, RF-007 |
| RN-007 | Resposta apenas por envolvido | Só participante envolvido na proposta pode aceitar/recusar. | RF-007 |
| RN-008 | Registro de resposta | Toda resposta deve registrar ator, decisão, data/hora e efeito no estado. | RF-007, RF-009 |
| RN-009 | Compatibilidade limitada por disponibilidade | Matching/proposta não pode comprometer quantidade/capacidade além do disponível. | RF-007 |
| RN-010 | Visibilidade de dados pessoais | E-mail/telefone/endereço/documentos expostos apenas quando houver permissão/finalidade legítima. | RF-001, RF-007, RF-011, RF-017 |
| RN-011 | Autorização de campanha | Criação/encerramento de campanha exige perfil autorizado. | RF-008, RF-013 |
| RN-012 | Estados controlados | Propostas, doações, ofertas, necessidades e campanhas seguem estados e transições válidas. | RF-004, RF-006, RF-007, RF-008, RF-009 |
| RN-013 | Endereço obrigatório do receptor | Receptor deve possuir CNPJ e endereço no cadastro. | RF-001 |
| RN-014 | Credencial protegida | Senha nunca em texto puro; recuperação por token/código seguro, temporário e de uso único. | RF-001, RF-003 |
| RN-015 | Catálogos padronizados | Itens, unidades e veículos usados em matching devem seguir catálogo/regras comuns. | RF-004–RF-008, RF-014 |
| RN-016 | Auditoria de ações críticas | Ações sensíveis devem ser rastreáveis para suporte, segurança e conformidade. | RF-002, RF-003, RF-007, RF-013, RF-016 |

## Observações
- Regras com *A definir* dependem de decisões em [[10 - Decisões Pendentes]].
- Regras legais (LGPD, restrições para medicamentos/alimentos etc.) devem ser validadas com especialistas quando o escopo incluir itens regulados.