---
tags: [doalink, rnf, backup, recuperação]
id: RNF-014
prioridade: Importante
---

# RNF-014 — Backup e recuperação de desastres

**Categoria:** Backup / Recuperação  
**Prioridade:** Importante

## Declaração
O sistema deve possuir estratégia de backup e restauração de dados compatível com os objetivos de RPO/RTO definidos.

## Critérios (A definir)
| Item | Requisito |
|---|---|
| Backup do banco | Frequência, retenção, criptografia e armazenamento separado. |
| Restauração | Procedimento testado periodicamente. |
| Segredos/config | Backup seguro de configurações críticas (sem expor segredos em repositório). |
| Integridade | Verificar possibilidade de restauração consistente. |