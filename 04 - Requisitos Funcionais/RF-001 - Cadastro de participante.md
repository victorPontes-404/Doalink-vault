---
tags: [doalink, rf, cadastro, essencial]
id: RF-001
prioridade: Essencial
origem: implementacao-doalink.md
---

# RF-001 — Cadastro de participante

**Prioridade:** Essencial  
**Origem:** Documento base (§4 RF-001)  
Relacionado: [[RF-002 - Autenticação e sessão]] | [[RF-010 - Gestão do perfil do participante]] | [[RF-017 - Privacidade e LGPD]] | [[RF-018 - Confirmação de conta e e-mail]] | [[06 - Regras de Negócio|RN-001, RN-002, RN-003]]

## Descrição
O sistema deve permitir o cadastro de participantes nos perfis **Doador**, **Transportador** e **Receptor**. Ao concluir um cadastro válido, o sistema deve criar o participante, normalizar os dados conforme regras, armazenar a senha apenas como hash seguro e gerar um identificador automático.

## Atores
- Visitante (inicia cadastro).
- Sistema (valida, normaliza, persiste, gera identificador).

## Pré-condições
- Usuário não autenticado ou em fluxo público de cadastro.
- Dados informados pelo usuário.

## Dados comuns (todos os perfis)

| Campo | Tipo lógico | Obrigatório | Máscara/apresentação | Validação e observações |
|---|---|:---:|---|---|
| Nome ou nome da organização | Texto | Sim | — | Mínimo/máximo de caracteres: **A definir** (PD-005). Remover espaços extras nas bordas. |
| CPF | Texto numérico (11) | Condicional | `000.000.000-00` | Para doador/transportador: informar CPF **ou** CNPJ (excludentes). Validar dígitos verificadores e unicidade. Armazenar normalizado (só dígitos). Preservar zeros à esquerda. |
| CNPJ | Texto numérico (14) | Condicional | `00.000.000/0000-00` | Receptor: **sempre** CNPJ. Doador/transportador: alternativa ao CPF. Validar dígitos verificadores e unicidade. Armazenar normalizado. |
| E-mail | Texto (até 254, sugestão) | Sim | — | Validar formato. Comparação sem diferenciar maiúsculas/minúsculas. Unicidade. Confirmação por link/código: **A definir** (PD-003, RF-018). |
| Senha | Segredo (entrada) / hash (persistência) | Sim | — | Nunca armazenar ou exibir em texto puro. Política mínima (tamanho, complexidade, vazamentos conhecidos): **A definir** (PD-004). |
| Tipo de usuário/perfil | Enum/seleção | Sim | — | `DOADOR`, `RECEPTOR`, `TRANSPORTADOR` (base). Multi-perfil: **A definir** (PD-001). |
| Telefone de contato | Texto numérico | **A definir** | `(00) 00000-0000` | Documento base indica que o sistema deve guardar/exibir e-mail e telefone; obrigatoriedade, validação, DDI e unicidade: **A definir** (PD-002). Armazenar normalizado. |

## Dados adicionais — Receptor

| Campo | Tipo lógico | Obrigatório | Máscara/apresentação | Validação e observações |
|---|---|:---:|---|---|
| CEP | Texto numérico (8) | Sim | `00000-000` | Validar formato. Consulta automática por CEP: **A definir** (PD-008). |
| UF | Texto (2) | Sim | — | Sigla válida (catálogo de UFs). |
| Cidade | Texto | Sim | — | Fonte/lista de cidades: **A definir**. |
| Bairro | Texto | Sim | — | — |
| Logradouro | Texto | Sim | — | — |
| Número | Texto | Sim | — | Aceitar "S/N" se regra de negócio permitir (**A definir**). |
| Complemento | Texto | Não | — | Opcional. |

## Regras específicas
- **RN-001:** CPF e CNPJ são excludentes para doador/transportador (informar exatamente um). Receptor informa CNPJ.
- **RN-002:** CPF/CNPJ e e-mail devem ser únicos entre contas ativas (definir comportamento para contas inativas/excluídas — PD/LGPD).
- **RN-003:** dados normalizados são persistidos; máscaras são apenas de apresentação.
- **RN-004:** identificador do participante é gerado automaticamente e não editável. Visibilidade do identificador ao usuário: conflito no documento base (**A definir**, PD-013).

## Fluxo principal
1. Visitante seleciona o perfil (doador, receptor ou transportador).
2. Sistema apresenta campos comuns e, se receptor, campos de endereço/CNPJ.
3. Visitante preenche dados e envia.
4. Sistema valida formato, obrigatoriedade condicional, dígitos verificadores, unicidade e política de senha.
5. Sistema normaliza dados, gera hash da senha e cria o participante com identificador automático.
6. Sistema retorna confirmação de cadastro (sem expor senha/hash; expor identificador conforme PD-013).

## Fluxos alternativos e exceções
| Condição | Comportamento | Estado final |
|---|---|---|
| CPF/CNPJ inválido | Rejeitar; informar erro de validação no campo. | Cadastro não criado. |
| CPF/CNPJ ou e-mail já cadastrado | Rejeitar; mensagem segura (evitar enumeração indevida, conforme política — ver RNF segurança). | Cadastro não criado. |
| Senha fora da política | Rejeitar com critérios aplicáveis (sem revelar regras internas sensíveis desnecessárias). | Cadastro não criado. |
| Receptor sem CNPJ ou sem endereço completo | Rejeitar. | Cadastro não criado. |
| Falha de persistência/infra | Rejeitar com erro genérico; registrar log técnico; não criar cadastro parcial. | Cadastro não criado. |

## Critérios de aceite
- **CA-001-1:** Dado um visitante com dados obrigatórios válidos e não utilizados, quando conclui o cadastro, então o sistema cria o participante e gera o identificador automaticamente.
- **CA-001-2:** Dado CPF/CNPJ ou e-mail inválido ou já associado a outra conta, quando o visitante tenta cadastrar, então o sistema rejeita o cadastro e não cria novo participante.
- **CA-001-3:** Dada uma senha fora dos critérios mínimos definidos, quando o visitante tenta cadastrar, então o sistema rejeita o cadastro.
- **CA-001-4:** Dado perfil Receptor, quando CNPJ ou endereço obrigatório estiver ausente/inválido, então o sistema rejeita o cadastro.
- **CA-001-5:** Dado cadastro concluído, quando os dados são persistidos, então CPF/CNPJ/CEP/telefone (se aplicável) ficam normalizados e a senha fica armazenada apenas como hash.

## Observações de implementação (estado atual)
- Existe `AuthService` com cadastro de doador/transportador/receptor, validação de unicidade e hash de senha.
- Há validações por anotações (`@CPF`, `@CNPJ`, Bean Validation) nos DTOs.
- **Lacunas observadas:** telefone ausente no modelo; API de validação CNPJ externa marcada como TODO; sem controllers/endpoints expostos no trecho analisado; fluxo de confirmação de e-mail inexistente.