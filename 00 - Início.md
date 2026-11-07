---
tags: [doalink, requisitos, vault, índice]
projeto: DoaLink
tipo: documentação de requisitos
versão: 0.1 (rascunho para revisão)
data: 2026-05-09
---

# DoaLink — Vault de Requisitos

Bem-vindo ao cofre (vault) do Obsidian com a documentação de levantamento de requisitos do projeto **DoaLink**.

Este vault reúne, organiza e expande os requisitos do produto a partir do documento base `implementacao-doalink.md`, com o objetivo de servir como referência para:
- **Negócio/stakeholders:** entender o que o sistema faz, para quem e com quais limites.
- **Desenvolvimento:** ter requisitos claros, campos, regras e critérios de aceite verificáveis.
- **QA/testes:** derivar casos de teste a partir de critérios de aceite e regras de negócio.
- **Produto/gestão:** acompanhar escopo, decisões pendentes e rastreabilidade.

> **Status:** rascunho para revisão. Este documento não substitui validação com stakeholders. Itens incertos estão marcados como *A definir* ou registrados em [[10 - Decisões Pendentes]].

---

## Como navegar neste vault

| Documento | O que você encontra |
|---|---|
| [[00 - Início]] | Índice, objetivo do vault e convenções. |
| [[01 - Visão Geral do Produto]] | Contexto, problema, proposta de valor, escopo e fora do escopo. |
| [[02 - Glossário e Conceitos]] | Definições de termos, siglas e entidades do domínio. |
| [[03 - Perfis e Permissões]] | Atores, perfis, permissões e pré-condições de acesso. |
| [[04 - Requisitos Funcionais/RF - Índice]] | Catálogo completo de requisitos funcionais (RF) com critérios de aceite. |
| [[05 - Requisitos Não Funcionais/RNF - Índice]] | Catálogo de requisitos não funcionais (RNF): segurança, desempenho, LGPD, etc. |
| [[06 - Regras de Negócio]] | Políticas e restrições do domínio (RN) referenciadas pelos RF/RNF. |
| [[07 - Modelo de Dados e Domínio]] | Modelo lógico inicial, entidades, relacionamentos e estados. |
| [[08 - Fluxos Principais]] | Fluxos ponta a ponta: cadastro, doação, combinação, emergência, acompanhamento. |
| [[09 - Matriz de Rastreabilidade]] | Ligação entre necessidades, RF/RNF, RN, critérios de aceite e evidências. |
| [[10 - Decisões Pendentes]] | Perguntas em aberto, impactos e responsáveis sugeridos. |
| [[11 - Fora do Escopo]] | O que o produto não faz nesta versão (para evitar suposições). |

---

## Convenções usadas

### Identificadores estáveis
- **RF-001, RF-002...** — Requisitos funcionais (comportamento observável do sistema).
- **RNF-001, RNF-002...** — Requisitos não funcionais (qualidades e restrições).
- **RN-001, RN-002...** — Regras de negócio.
- **CA-001-1...** — Critérios de aceite (vinculados ao RF correspondente).
- **PD-001...** — Decisões/pendências.

Os IDs **não devem ser renumerados** após publicação/referência em specs ou testes. Requisitos retirados devem ser marcados como *(retirado)*.

### Leitura de prioridade (quando informada)
- **Essencial:** necessário para a proposta central do produto.
- **Importante:** agrega valor significativo; pode ser faseado com decisão explícita.
- **Desejável:** melhora experiência ou operação; não bloqueia o núcleo.

> Prioridade é sugestão de negócio/produto quando não houver decisão formal. Sempre confirmar com stakeholders.

### Campos e máscaras
- Máscaras (CPF, CNPJ, CEP, telefone) são **apenas de apresentação** na interface.
- O armazenamento deve usar valores **normalizados** (ex.: somente dígitos) quando aplicável.
- Validação semântica (dígitos verificadores, formato, unicidade) é obrigatória no back-end.

### Critérios de aceite
Escritos no formato: **Dado** [contexto], **quando** [ação], **então** [resultado verificável]. Cada critério deve ser testável de forma independente sempre que possível.

---

## Origem e referências

- Documento base: `implementacao-doalink.md` (raiz do repositório `doalink-api`).
- Código atual do back-end: `doalink-api/` (Spring Boot, Java 21, JPA, PostgreSQL, Flyway, Security).
- Este vault **expande** o documento base: adiciona RFs complementares, RNFs ausentes, regras, fluxos, glossário e rastreabilidade. Onde houver divergência com o documento base, registrar em [[10 - Decisões Pendentes]] ou como nota de revisão.

---

## Próximos passos sugeridos
1. Revisar visão geral, perfis e escopo com stakeholders ([[01 - Visão Geral do Produto]], [[03 - Perfis e Permissões]]).
2. Priorizar RFs essenciais vs. desejáveis ([[04 - Requisitos Funcionais/RF - Índice]]).
3. Resolver decisões pendentes críticas ([[10 - Decisões Pendentes]]) — especialmente perfis múltiplos, visibilidade, estados de proposta e localização.
4. Validar RNFs de segurança/privacidade antes de exposição de dados pessoais ([[05 - Requisitos Não Funcionais/RNF - Índice]]).
5. Derivar specs técnicas e casos de teste a partir de RF/RN/CA.