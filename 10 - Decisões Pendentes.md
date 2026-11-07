---
tags: [doalink, pendências, decisões]
---

# Decisões Pendentes (PD)

Relacionado: [[00 - Início]] | [[04 - Requisitos Funcionais/RF - Índice]] | [[06 - Regras de Negócio]]

| ID | Decisão | Impacto | RF/RN relacionados | Prioridade sugerida |
|---|---|---|---|---|
| PD-001 | Conta pode ter múltiplos perfis? Como trocar perfil? | Modelo de identidade, autorização, cadastro e UX. | RF-001, RF-002, RNF-002 | Alta |
| PD-002 | Telefone obrigatório? Formato, DDI, validação e unicidade? | Cadastro, contato, LGPD, matching. | RF-001, RN-003 | Alta |
| PD-003 | Confirmação de e-mail? Canal/formato/validade/limite de token de recuperação? | Segurança de conta e recuperação. | RF-001, RF-003, RF-018 | Alta |
| PD-004 | Política de senha e mensagem para e-mail inexistente na recuperação. | Segurança e UX. | RF-001, RF-003, RNF-001 | Alta |
| PD-005 | Regras de tamanho/formato de nome e dados textuais. | Validação e consistência. | RF-001 | Média |
| PD-006 | Catálogos de itens, unidades e veículos; conversões aceitas. | Qualidade do matching. | RF-004–RF-007, RF-014, RN-005 | Alta |
| PD-007 | Oferta parcializável? Reserva de saldo? Local da doação é endereço do doador ou outro? | Modelo de oferta, concorrência, logística. | RF-004, RF-007, RN-006 | Alta |
| PD-008 | Modelo de localização (CEP/endereço, coordenadas, cidade/UF, raio) e regra de compatibilidade geográfica. | Matching, privacidade, UX. | RF-004–RF-007, RF-011 | Alta |
| PD-009 | Precisão de data/horário e janela de validade de ofertas/disponibilidades. | Matching e expiração. | RF-004, RF-005, RF-007 | Média |
| PD-010 | Máquina de estados da proposta: estados, transições e regra de confirmação (todos aceitam? timeout?). | Núcleo do RF-007. | RF-007, RF-009, RN-012 | Alta |
| PD-011 | Quem pode criar/encerrar/arquivar campanha? Formato da região? Necessidade tem local próprio? | Governança e operação emergencial. | RF-008, RF-013 | Alta |
| PD-012 | Acompanhamento manual ou automático? Quem pode atualizar cada estado? Registra responsável? | Confiabilidade do status. | RF-009 | Média |
| PD-013 | Identificador do participante é visível ao usuário? Documento base tem conflito. | UX, suporte e privacidade. | RF-001, RN-004 | Média |
| PD-014 | Regras de visibilidade para ofertas/necessidades/disponibilidades (público, autenticado, por perfil, por envolvimento). | Privacidade e produto. | RF-004–RF-007, RF-011, RN-010 | Alta |
| PD-015 | Cadastro de Receptor: endereço completo sempre obrigatório? Local de entrega da necessidade pode diferir do endereço cadastral? | Modelo e UX. | RF-001, RF-006 | Média |
| PD-016 | Itens regulados (medicamentos, alimentos perecíveis) têm restrições legais/operacionais? | Escopo, compliance e risco. | RF-004, RF-006, RF-014 | Alta (se aplicável) |
| PD-017 | Canal de notificações (e-mail, in-app, push) e preferências do usuário. | RF-012 e custo operacional. | RF-012 | Média |
| PD-018 | Existe perfil Administrador? Quais papéis administrativos? | Governança. | RF-008, RF-013, RF-016 | Alta |
| PD-019 | Estratégia de exclusão/anonimização de conta (LGPD) com histórico operacional. | Conformidade e integridade. | RF-010, RF-017 | Média |
| PD-020 | Definição de ambientes, SLOs, backup e RPO/RTO. | Operação e RNFs. | RNF-006, RNF-011, RNF-014 | Média |