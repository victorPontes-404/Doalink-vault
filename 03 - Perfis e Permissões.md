---
tags: [doalink, perfis, permissões, acesso]
---

# Perfis e Permissões

Relacionado: [[01 - Visão Geral do Produto]] | [[04 - Requisitos Funcionais/RF - Índice]] | [[10 - Decisões Pendentes|PD-001]]

## 1. Princípios
- **Autorização no servidor:** toda ação sensível deve ser validada no back-end, independentemente de a interface ocultar botões/opções.
- **Menor privilégio:** cada perfil acessa apenas o necessário para suas responsabilidades.
- **Contexto de envolvimento:** em propostas/doações, apenas participantes envolvidos podem responder ou visualizar dados sensíveis, conforme regras de visibilidade.
- **Auditoria:** ações críticas (cadastro, login, alteração de credenciais, criação/edição de campanha, mudança de estado, aceite/recusa) devem ser rastreáveis (ver RNF/RF de auditoria).

## 2. Perfis previstos

| Perfil | Descrição | Pré-condições típicas |
|---|---|---|
| **Visitante** | Usuário não autenticado. | Nenhuma. Pode acessar páginas públicas (a definir) e fluxos de cadastro/login/recuperação. |
| **Doador** | Participante que oferta doações. | Conta criada, autenticada; perfil doador ativo. |
| **Receptor** | Organização/ONG que registra necessidades. | Conta criada com CNPJ e endereço; autenticada; perfil receptor ativo. |
| **Transportador** | Participante que oferta transporte. | Conta criada, autenticada; perfil transportador ativo. |
| **Administrador** *(sugerido, a definir)* | Operador da plataforma. | Conta administrativa autorizada; permissões elevadas. |

> **PD-001:** o documento base não define se uma conta pode acumular múltiplos perfis. A implementação atual assume um perfil por conta. A matriz abaixo deve ser revisada se multi-perfil for adotado.

## 3. Matriz de permissões (visão inicial)

Legenda: ✅ permitido | ❌ não permitido | ⚠️ condicionado | — não aplicável/a definir

| Capacidade | Visitante | Doador | Receptor | Transportador | Admin* |
|---|:---:|:---:|:---:|:---:|:---:|
| Cadastrar conta | ✅ | — | — | — | ⚠️ |
| Autenticar (login) | ✅ | ✅ | ✅ | ✅ | ✅ |
| Recuperar senha | ✅ | ✅ | ✅ | ✅ | ✅ |
| Ver/editar próprio perfil | ❌ | ✅ | ✅ | ✅ | ✅ |
| Cadastrar oferta de doação | ❌ | ✅ | ❌ | ❌ | ⚠️ |
| Editar/cancelar própria oferta | ❌ | ✅ | ❌ | ❌ | ⚠️ |
| Cadastrar necessidade | ❌ | ❌ | ✅ | ❌ | ⚠️ |
| Editar/cancelar própria necessidade | ❌ | ❌ | ✅ | ❌ | ⚠️ |
| Cadastrar disponibilidade de transporte | ❌ | ❌ | ❌ | ✅ | ⚠️ |
| Editar/cancelar própria disponibilidade | ❌ | ❌ | ❌ | ✅ | ⚠️ |
| Consultar ofertas/necessidades/disponibilidades | ⚠️ | ⚠️ | ⚠️ | ⚠️ | ✅ |
| Visualizar propostas em que está envolvido | ❌ | ✅ | ✅ | ✅ | ✅ |
| Aceitar/recusar proposta em que está envolvido | ❌ | ✅ | ✅ | ✅ | ❌* |
| Criar/gerenciar campanha emergencial | ❌ | ❌ | ⚠️ | ❌ | ✅ |
| Consultar campanhas | ⚠️ | ✅ | ✅ | ✅ | ✅ |
| Atualizar situação da doação | ❌ | ⚠️ | ⚠️ | ⚠️ | ✅ |
| Acessar dados de contato de outro participante | ❌ | ⚠️ | ⚠️ | ⚠️ | ✅ |
| Administrar usuários/catálogos/moderação | ❌ | ❌ | ❌ | ❌ | ✅ |
| Visualizar auditoria/relatórios operacionais | ❌ | ❌ | ❌ | ❌ | ✅ |

\* Permissões de administrador são sugestões e dependem de definição de governança.

## 4. Regras de autorização (resumo)
- **RN-AUT-01:** ações de escrita exigem autenticação, exceto cadastro e recuperação de senha.
- **RN-AUT-02:** um participante só pode alterar/cancelar registros próprios (oferta, necessidade, disponibilidade), salvo administração autorizada.
- **RN-AUT-03:** resposta a proposta só é aceita se o usuário autenticado for participante envolvido na proposta.
- **RN-AUT-04:** dados de contato de terceiros só são expostos quando houver finalidade legítima no fluxo (ex.: proposta confirmada/envolvimento) e conforme política de privacidade — **A definir**.
- **RN-AUT-05:** criação e encerramento de campanha exigem perfil autorizado (admin ou papel delegado) — **A definir**.

## 5. Implicações para o design
- O modelo atual usa `TipoUsuario` (DOADOR, RECEPTOR, TRANSPORTADOR) no usuário. Se houver multi-perfil, será necessário separar identidade de papéis/perfis.
- Endpoints devem usar controle por papel/perfil (ex.: Spring Security authorities/roles) e validações de propriedade no service.
- A interface deve ocultar ações não permitidas, mas isso **não substitui** validação no servidor.