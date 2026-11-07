---
tags: [doalink, rf, requisitos-funcionais, índice]
---

# Requisitos Funcionais — Índice

Relacionado: [[00 - Início]] | [[06 - Regras de Negócio]] | [[09 - Matriz de Rastreabilidade]] | [[10 - Decisões Pendentes]]

## Visão geral
Este índice cataloga os requisitos funcionais (RF) do DoaLink. Os RFs **RF-001 a RF-009** derivam do documento base `implementacao-doalink.md`. Os demais (**RF-010+**) são **sugestões de expansão** identificadas a partir do domínio, lacunas comuns de produto e necessidades de operação/conformidade — devem ser validadas com stakeholders.

## Catálogo

| ID | Título | Prioridade sugerida | Origem | Documento |
|---|---|---|---|---|
| RF-001 | Cadastro de participante | Essencial | Base | [[RF-001 - Cadastro de participante]] |
| RF-002 | Autenticação e sessão | Essencial | Base | [[RF-002 - Autenticação e sessão]] |
| RF-003 | Recuperação de senha | Essencial | Base | [[RF-003 - Recuperação de senha]] |
| RF-004 | Oferta de doação | Essencial | Base | [[RF-004 - Oferta de doação]] |
| RF-005 | Disponibilidade de transporte | Essencial | Base | [[RF-005 - Disponibilidade de transporte]] |
| RF-006 | Necessidade de doação | Essencial | Base | [[RF-006 - Necessidade de doação]] |
| RF-007 | Sugestão e resposta a combinações | Desejável (base) / Importante* | Base | [[RF-007 - Sugestão e resposta a combinações]] |
| RF-008 | Campanha ou evento emergencial | Essencial | Base | [[RF-008 - Campanha ou evento emergencial]] |
| RF-009 | Acompanhamento da doação | Desejável | Base | [[RF-009 - Acompanhamento da doação]] |
| RF-010 | Gestão do perfil do participante | Importante | Expansão | [[RF-010 - Gestão do perfil do participante]] |
| RF-011 | Consulta e busca de ofertas, necessidades e transportes | Importante | Expansão | [[RF-011 - Consulta e busca]] |
| RF-012 | Notificações e comunicações do sistema | Importante | Expansão | [[RF-012 - Notificações]] |
| RF-013 | Administração da plataforma | Importante | Expansão | [[RF-013 - Administração da plataforma]] |
| RF-014 | Catálogos e padronização (itens, unidades, veículos) | Importante | Expansão | [[RF-014 - Catálogos e padronização]] |
| RF-015 | Relatórios e indicadores operacionais | Desejável | Expansão | [[RF-015 - Relatórios e indicadores]] |
| RF-016 | Moderação, denúncias e segurança operacional | Desejável | Expansão | [[RF-016 - Moderação e denúncias]] |
| RF-017 | Privacidade, consentimento e direitos do titular (LGPD) | Essencial (conformidade)* | Expansão | [[RF-017 - Privacidade e LGPD]] |
| RF-018 | Confirmação e gestão de conta/e-mail | Importante | Expansão | [[RF-018 - Confirmação de conta e e-mail]] |
| RF-019 | Anexos e evidências de itens | Desejável | Expansão | [[RF-019 - Anexos e evidências de itens]] |
| RF-020 | Agendamento de coleta e entrega | Desejável | Expansão | [[RF-020 - Agendamento de coleta e entrega]] |
| RF-021 | Expiração, renovação e arquivamento | Importante | Expansão | [[RF-021 - Expiração, renovação e arquivamento]] |
| RF-022 | Favoritos, interesse e acompanhamento de itens | Desejável | Expansão | [[RF-022 - Favoritos, interesse e acompanhamento de itens]] |
| RF-023 | Histórico de atividades do participante | Importante | Expansão | [[RF-023 - Histórico de atividades do participante]] |
| RF-024 | Termos de uso, políticas e aceite | Importante | Expansão | [[RF-024 - Termos de uso, políticas e aceite]] |
| RF-025 | Validação e geocodificação de endereço | Importante | Expansão | [[RF-025 - Validação e geocodificação de endereço]] |
| RF-026 | Gestão de veículos do transportador | Desejável | Expansão | [[RF-026 - Gestão de veículos do transportador]] |
| RF-027 | Duplicação e rascunho de registros | Desejável | Expansão | [[RF-027 - Duplicação e rascunho de registros]] |
| RF-028 | Mensagens operacionais e motivos | Desejável | Expansão | [[RF-028 - Mensagens operacionais e motivos]] |
| RF-029 | Avaliação e reputação (futuro controlado) | Futuro | Expansão | [[RF-029 - Avaliação e reputação (futuro controlado)]] |
| RF-030 | Suporte operacional e atendimento | Desejável | Expansão | [[RF-030 - Acessibilidade operacional para suporte]] |
| RF-031 | Gestão de múltiplos itens e kits | Importante | Expansão | [[RF-031 - Gestão de múltiplos itens e kits]] |
| RF-032 | Elegibilidade e restrições de itens | Importante (se aplicável) | Expansão | [[RF-032 - Elegibilidade e restrições de itens]] |
| RF-033 | Painéis por perfil ("Minha área") | Importante | Expansão | [[RF-033 - Painéis por perfil (minha área)]] |
| RF-034 | Bloqueio, suspensão e reativação de conta | Importante | Expansão | [[RF-034 - Bloqueio, suspensão e reativação de conta]] |
| RF-035 | Cancelamento e desistência com impacto controlado | Importante | Expansão | [[RF-035 - Cancelamento e desistência com impacto controlado]] |
| RF-036 | Busca geográfica e proximidade | Desejável | Expansão | [[RF-036 - Busca geográfica e proximidade]] |

\* Classificação sugerida; validar com negócio/jurídico/produto.

## Observações de cobertura
- O documento base já sinaliza lacunas críticas em autenticação, visibilidade, estados de proposta, localização e catálogos. Esses pontos afetam múltiplos RFs e estão consolidados em [[10 - Decisões Pendentes]].
- RF-007 é marcado como desejável no documento base, mas é central para a proposta de valor ("conectar" e "formar combinações"). Recomenda-se tratar como **Importante/estratégico** no roadmap, mesmo que implementado em fases.
- RNFs ausentes no documento base foram criados em [[05 - Requisitos Não Funcionais/RNF - Índice]].