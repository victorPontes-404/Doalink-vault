---
tags: [doalink, rf, endereço, cep, geocodificação, importante]
id: RF-025
prioridade: Importante
origem: Expansão
---

# RF-025 — Validação e geocodificação de endereço

**Prioridade:** Importante (sugestão)

## Descrição
O sistema deve validar endereços informados e, quando adotado, enriquecer dados com consulta de CEP/geocodificação para melhorar qualidade de localização e matching.

## Capacidades sugeridas
- Consulta por CEP para preencher logradouro/bairro/cidade/UF (com possibilidade de ajuste manual).
- Validação de UF/cidade coerentes.
- Normalização de CEP.
- Geocodificação (latitude/longitude) opcional para cálculo de distância/rota (PD-008).
- Cache de consultas externas para reduzir custo e latência.

## Regras
- Falha no serviço externo de CEP não deve impedir cadastro se os dados mínimos forem informados manualmente (política A definir).
- Dados geográficos aproximados podem ser sensíveis; tratar conforme LGPD/RNF-004.
- Fonte de dados de endereço/geocodificação deve ser definida (PD e RNF-012).