---
tags: [doalink, anexo, código, análise]
---

# Anexo — Análise do Estado Atual do Código

> Snapshot de análise realizado em 2026-05-09 sobre o repositório `doalink-api`. Serve como contexto para revisão de requisitos; o código pode evoluir.

## Stack observada
- Java 21, Spring Boot 4.1.2 (Maven).
- Spring Data JPA/Hibernate, PostgreSQL, Flyway, Spring Security, Validation, WebMVC.
- Lombok.

## Implementado (parcialmente ou como fundação)
- Entidades: `Usuario` (abstrata, herança `JOINED`), `Doador`, `Receptor`, `Transportador`, `ItemDoacao`, `Endereco`; enums de tipo usuário/pessoa/item.
- DTOs de cadastro e oferta (request/response) e mapper de endereço.
- `AuthService` com cadastro de doador/transportador/receptor, normalização básica, unicidade e hash de senha (`PasswordEncoder`).
- `UsuarioRepository` com verificações de existência por e-mail/documento.
- Configuração de datasource/Flyway (pasta `db/migration` ausente no estado analisado).
- Histórico integrado inclui componentes de autenticação/JWT/refresh token (config, filtro, serviços), mas a exposição ponta a ponta depende de controllers/endpoints.

## Não observado / lacunas
- Controllers REST para cadastro, login, ofertas, necessidades, transportes, propostas, campanhas, acompanhamento.
- Telefone no modelo de usuário (documento exige contato).
- Política/configuração explícita de BCrypt/Argon2 e `SecurityFilterChain` completa conforme produto.
- Migrations Flyway.
- Domínio de proposta/matching, campanha, necessidade, disponibilidade de transporte, acompanhamento.

## Implicações para requisitos
- O código atual cobre parte do **RF-001** (fundação de cadastro), mas não entrega os fluxos completos de RF-001 a RF-009.
- A decisão de **um perfil por conta** está embutida na modelagem atual (PD-001 precisa ser validada antes de expandir).
- Há risco de dívida se ofertas/propostas forem implementadas antes de consolidar catálogos, unidades, localização e estados (PD-006, PD-008, PD-010).