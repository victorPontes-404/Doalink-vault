---
tags: [doalink, produto, visão-geral, escopo]
---

# Visão Geral do Produto

Relacionado: [[00 - Início]] | [[03 - Perfis e Permissões]] | [[11 - Fora do Escopo]]

## 1. Nome e propósito
**DoaLink** é uma plataforma digital cuja única responsabilidade é **interligar** doadores, receptores (ONGs e outras organizações) e transportadores — fazendo com que essas partes se encontrem e possam se combinar para que uma doação aconteça.

A plataforma organiza e exibe informações, sugere combinações compatíveis e permite que os participantes respondam a essas propostas. O que acontece depois disso — comunicação, logística, entrega — é responsabilidade exclusiva dos próprios participantes.

## 2. Problema que o produto busca resolver
Doações muitas vezes falham não por falta de intenção, mas por falta de visibilidade e coordenação:
- Doadores têm itens disponíveis, mas não sabem quem precisa nem como encontrar um transportador.
- Receptores têm necessidades urgentes, mas não têm como encontrar ofertas compatíveis.
- Transportadores têm disponibilidade, mas não encontram rotas com demanda real.
- Em emergências, a necessidade de conectar essas partes rapidamente é ainda mais crítica.

O DoaLink resolve isso sendo o ponto central onde as três partes se cadastram, publicam seus dados e se encontram.

## 3. Proposta de valor
- **Para doadores:** publicar ofertas com item, quantidade e local de retirada, e receber propostas de combinação.
- **Para receptores:** registrar necessidades e participar de campanhas emergenciais com dados estruturados.
- **Para transportadores:** publicar disponibilidade de capacidade, origem, destino e data, e ser incluído em combinações viáveis.
- **Para a rede:** aumentar a chance de doações acontecerem ao conectar as partes certas com informações compatíveis.

## 4. O que o sistema é — e o que não é

### O sistema É:
- Uma plataforma de **cadastro e publicação** de ofertas, necessidades e disponibilidades de transporte.
- Um **motor de combinação (matching)** que identifica compatibilidades entre as partes e gera propostas.
- Um **canal de resposta** onde os participantes aceitam ou recusam propostas.
- Um **ponto de contato**: cada participante pode incluir seu número de telefone no cadastro para que os outros envolvidos numa proposta possam entrar em contato por fora da plataforma.

### O sistema NÃO É:
- Um canal de comunicação em tempo real (sem chat, sem mensageria interna).
- Um sistema de rastreamento ou acompanhamento logístico (sem GPS, sem status de entrega).
- Um intermediário responsável pela execução da doação — o que acontece após a combinação confirmada é de responsabilidade exclusiva dos participantes.
- Um sistema de pagamento ou intermediação financeira.

## 5. Objetivos do produto
1. Permitir cadastro e acesso seguro de participantes por perfil (doador, receptor, transportador).
2. Permitir registro estruturado de ofertas, necessidades e disponibilidades de transporte.
3. Sugerir combinações compatíveis entre oferta, necessidade e transporte.
4. Permitir que participantes envolvidos aceitem ou recusem propostas.
5. Apoiar campanhas emergenciais com necessidades regionalizadas.
6. Exibir dados de contato (telefone) dos envolvidos em uma proposta para viabilizar comunicação externa.

## 6. Stakeholders e usuários
| Stakeholder | Interesse principal |
|---|---|
| Doador (pessoa física ou jurídica) | Publicar itens disponíveis e ser conectado a receptores e transportadores compatíveis. |
| Receptor (ONG/organização) | Registrar necessidades e receber propostas com oferta e transporte compatíveis. |
| Transportador (PF/PJ) | Publicar disponibilidade logística e ser conectado a rotas com demanda real. |
| Administrador/operador da plataforma | Governança, gestão de campanhas, catálogos e conformidade. |
| Beneficiário final (indireto) | Receber doações com maior agilidade graças à melhor coordenação entre as partes. |

## 7. Escopo funcional (resumo)
- Cadastro, autenticação e recuperação de credenciais.
- Gestão de ofertas de doação.
- Gestão de necessidades de doação.
- Gestão de disponibilidades de transporte.
- Sugestão e resposta a propostas/combinações (matching).
- Campanhas e eventos emergenciais.
- Notificações de eventos da plataforma (nova proposta, resposta, expiração).
- Busca e filtros de ofertas, necessidades e transportes.
- Administração da plataforma (usuários, catálogos, campanhas).
- Conformidade LGPD.

## 8. Premissas iniciais
- O back-end é uma API (Spring Boot) consumida por cliente(s) a definir (web/mobile).
- Dados pessoais (CPF, CNPJ, e-mail, telefone, endereço) exigem tratamento conforme LGPD.
- O telefone do participante pode ser incluído no cadastro e exibido aos envolvidos em uma proposta confirmada, como único canal de contato externo suportado pela plataforma.
- A compatibilidade entre itens depende de catálogos/unidades padronizadas (decisão pendente).
- A confirmação de combinações depende de regras de aceite dos participantes (decisão pendente).

## 9. Restrições conhecidas / contexto técnico atual
- Stack atual observada: Java 21, Spring Boot, Spring Data JPA/Hibernate, PostgreSQL, Flyway, Spring Security, Validation.
- Modelo atual implementa perfis por herança (`Usuario` → `Doador`, `Receptor`, `Transportador`), assumindo **um perfil por conta** — decisão que deve ser validada ([[10 - Decisões Pendentes|PD-001]]).
- O domínio de propostas, campanhas, notificações e administração ainda não está implementado no código no momento da análise.

## 10. Indicadores de sucesso (sugestão — a validar)
> Métricas de produto/negócio a confirmar com stakeholders.

- Número de combinações geradas e confirmadas por período.
- Taxa de propostas aceitas por todos os participantes envolvidos.
- Tempo médio entre publicação de oferta/necessidade e primeira proposta gerada.
- Taxa de cadastros concluídos com sucesso.
- Tempo de resposta em campanhas emergenciais.
