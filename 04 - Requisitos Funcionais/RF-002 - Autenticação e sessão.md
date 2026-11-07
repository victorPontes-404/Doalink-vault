---
tags: [doalink, rf, autenticação, login, sessão, essencial]
id: RF-002
prioridade: Essencial
origem: implementacao-doalink.md
---

# RF-002 — Autenticação e sessão

**Prioridade:** Essencial  
**Origem:** Documento base (§4 RF-002)  
Relacionado: [[RF-001 - Cadastro de participante]] | [[RF-003 - Recuperação de senha]] | [[05 - Requisitos Não Funcionais/RNF - Índice|RNF-002, RNF-003]]

## Descrição
O sistema deve permitir que participantes autenticados acessem as funções autorizadas aos seus perfis por meio de credenciais (e-mail e senha), encerrar sessão e iniciar a recuperação de senha.

## Atores
- Participante (doador, receptor, transportador).
- Sistema de autenticação/autorização.

## Pré-condições
- Conta previamente cadastrada (e elegível para autenticação, conforme confirmação de e-mail — PD-003).
- Credenciais informadas.

## Entradas
| Campo | Obrigatório | Validação |
|---|:---:|---|
| E-mail | Sim | Formato válido; comparação normalizada (case-insensitive) conforme regra de cadastro. |
| Senha | Sim | Comparada ao hash armazenado; nunca logada/exposta. |

## Fluxo principal — login
1. Participante informa e-mail e senha.
2. Sistema valida credenciais.
3. Sistema cria sessão/token de acesso conforme mecanismo definido (JWT/cookie/sessão — decisão técnica).
4. Sistema autoriza acesso às funcionalidades do perfil.
5. Sistema registra evento de autenticação bem-sucedida (auditoria).

## Fluxo principal — logout
1. Participante autenticado solicita encerramento.
2. Sistema invalida sessão/token aplicável (ex.: revoga refresh token).
3. Sistema confirma encerramento.

## Fluxos alternativos e exceções
| Condição | Comportamento | Observação |
|---|---|---|
| Credenciais inválidas | Não conceder acesso; retornar falha genérica de autenticação. | Evitar indicar se e-mail existe (RNF segurança). |
| Conta bloqueada/inativa (se aplicável) | Rejeitar acesso com mensagem adequada. | Política a definir. |
| Muitas tentativas falhas | Aplicar proteção (rate limit/captcha/bloqueio temporário). | Ver RNF-003. |
| Token/sessão expirada | Exigir nova autenticação. | — |

## Critérios de aceite
- **CA-002-1:** Dado participante com credenciais válidas, quando autentica, então o sistema concede acesso às funções autorizadas ao seu perfil.
- **CA-002-2:** Dadas credenciais inválidas, quando tenta autenticar, então o sistema não concede acesso e retorna mensagem de falha de autenticação.
- **CA-002-3:** Dado participante autenticado, quando solicita logout, então o sistema encerra a sessão/contexto de autenticação.
- **CA-002-4:** Dado participante que esqueceu a senha, quando solicita recuperação, então o sistema inicia o fluxo de recuperação (RF-003).

## Observações
- O código atual inclui dependências/configurações relacionadas a JWT/refresh token/security (conforme histórico do `origin/main` integrado ao branch), mas a validação ponta a ponta depende de controllers, filtros e política de cookies/tokens.
- O modelo de autorização deve refletir [[03 - Perfis e Permissões]].