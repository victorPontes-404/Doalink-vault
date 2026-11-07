---
tags: [doalink, rnf, privacidade, ambientes]
id: RNF-019
prioridade: Importante
---

# RNF-019 — Proteção de dados em ambientes não produtivos

**Categoria:** Privacidade / Operação  
**Prioridade:** Importante

## Declaração
Dados pessoais de produção não devem ser expostos indevidamente em ambientes de desenvolvimento, teste ou homologação.

## Critérios
- Uso de dados sintéticos/anonimizados/mascarados em ambientes não produtivos quando possível.
- Controle de acesso a cópias de banco e backups.
- Logs de não produção também devem evitar dados sensíveis desnecessários.
- Procedimento de sanitização para dumps: **A definir**.