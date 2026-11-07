---
tags: [doalink, produto, visão-geral, escopo]
---

# Visão Geral do Produto

Relacionado: [[00 - Início]] | [[03 - Perfis e Permissões]] | [[11 - Fora do Escopo]]

## 1. Nome e propósito
**DoaLink** é uma plataforma digital que conecta **doadores**, **receptores** (ONGs e outras organizações) e **transportadores** para facilitar o ciclo de doações: oferta de itens, registro de necessidades e disponibilidade de transporte, com apoio à descoberta e formação de combinações — inclusive em **campanhas de emergência**.

## 2. Problema que o produto busca resolver
Doações muitas vezes falham não por falta de intenção, mas por falta de coordenação:
- Doadores têm itens disponíveis, mas não sabem quem precisa e como entregar.
- Receptores têm necessidades urgentes, mas não têm visibilidade de ofertas compatíveis.
- Transporte é um gargalo frequente (capacidade, rota, data, custo/logística).
- Em emergências, a necessidade de matching rápido aumenta e a informação fica dispersa.

O DoaLink busca reduzir esse atrito organizando informações e sugerindo combinações compatíveis entre oferta, necessidade e transporte.

## 3. Proposta de valor
- **Para doadores:** publicar ofertas com clareza (item, quantidade, local) e acompanhar propostas.
- **Para receptores:** registrar necessidades e participar de campanhas/emergências com dados estruturados.
- **Para transportadores:** ofertar capacidade logística com origem/destino/data e ser incluído em combinações viáveis.
- **Para a rede:** aumentar a chance de doações efetivas ao considerar compatibilidade de item, quantidade/unidade, localização/rota e data.

## 4. O que o sistema é (e o que não é)
O DoaLink é, no escopo atual, uma **plataforma de conexão e coordenação de informações**.

- O sistema **guarda e exibe** dados de contato (e-mail e telefone) dos participantes, conforme regras de visibilidade/autorização a definir.
- O sistema **apoia** a formação de combinações/propostas.
- O sistema **pode** acompanhar digitalmente a situação da doação (requisito desejável).

O sistema **não garante**:
- comunicação direta embutida (chat/mensageria) entre participantes, no escopo original;
- rastreamento físico/GPS da carga;
- pagamento, intermediação financeira ou gestão fiscal da doação;
- verificação presencial da qualidade/quantidade dos itens.

Ver detalhes em [[11 - Fora do Escopo]].

## 5. Objetivos do produto
1. Permitir cadastro e acesso seguro de participantes por perfil.
2. Permitir registro estruturado de ofertas, necessidades e disponibilidades de transporte.
3. Apoiar a compatibilização entre oferta, necessidade e transporte.
4. Permitir que participantes envolvidos respondam a propostas (aceitar/recusar).
5. Apoiar campanhas emergenciais com necessidades regionalizadas.
6. Fornecer visibilidade do estado da doação para participantes autorizados (desejável).

## 6. Stakeholders e usuários
| Stakeholder | Interesse principal |
|---|---|
| Doador (pessoa física ou jurídica) | Ofertar itens e concluir doações com menos esforço de coordenação. |
| Receptor (ONG/organização) | Registrar necessidades, receber propostas compatíveis e atender beneficiários. |
| Transportador (PF/PJ) | Disponibilizar capacidade logística e participar de rotas viáveis. |
| Administrador/operador da plataforma *(a definir)* | Governança, moderação, suporte, gestão de campanhas e conformidade. |
| Beneficiário final (indireto) | Receber doações com maior agilidade e previsibilidade. |

## 7. Escopo funcional (resumo)
- Cadastro, autenticação e recuperação de credenciais.
- Gestão de ofertas de doação.
- Gestão de necessidades de doação.
- Gestão de disponibilidades de transporte.
- Sugestão e resposta a propostas/combinações.
- Campanhas/emergências.
- Acompanhamento da situação da doação (desejável).
- Funcionalidades de apoio sugeridas neste vault: notificações, busca/filtros, auditoria, administração, relatórios e conformidade LGPD (detalhadas em RFs complementares).

## 8. Premissas iniciais
- O back-end é uma API (Spring Boot) consumida por cliente(s) a definir (web/mobile).
- Dados pessoais (CPF, CNPJ, e-mail, telefone, endereço) exigem tratamento conforme LGPD.
- A compatibilidade entre itens depende de catálogos/unidades padronizadas ou regras de conversão (decisão pendente).
- A confirmação de combinações depende de regras de estado e aceite dos participantes (decisão pendente).

## 9. Restrições conhecidas / contexto técnico atual
- Stack atual observada: Java 21, Spring Boot, Spring Data JPA/Hibernate, PostgreSQL, Flyway, Spring Security, Validation.
- Modelo atual implementa perfis por herança (`Usuario` → `Doador`, `Receptor`, `Transportador`), assumindo **um perfil por conta** — decisão que deve ser validada ([[10 - Decisões Pendentes|PD-001]]).
- O domínio de propostas, campanhas, acompanhamento, notificações e administração ainda não está implementado no código no momento da análise.

## 10. Indicadores de sucesso (sugestão — a validar)
> Métricas de produto/negócio a confirmar com stakeholders; não são RNFs técnicos.

- Tempo médio entre criação de oferta/necessidade e primeira proposta compatível.
- Taxa de propostas aceitas por todos os participantes envolvidos.
- Taxa de doações que chegam ao estado `ENTREGUE`.
- Tempo de resposta em campanhas emergenciais.
- Taxa de cadastros concluídos com sucesso (sem abandono por erro/atrito).
- Número de combinações realizadas sem necessidade de transporte (quando aplicável).