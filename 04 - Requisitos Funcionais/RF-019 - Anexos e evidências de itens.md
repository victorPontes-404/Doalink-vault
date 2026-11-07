---
tags: [doalink, rf, anexos, mídia, desejável]
id: RF-019
prioridade: Desejável
origem: Expansão
---

# RF-019 — Anexos e evidências de itens

**Prioridade:** Desejável (sugestão)

## Descrição
O sistema deve permitir anexar fotos ou documentos a ofertas e, quando aplicável, a necessidades/propostas, para aumentar confiança e clareza sobre os itens.

## Campos/capacidades sugeridas
| Campo | Observação |
|---|---|
| Imagens do item | Formatos aceitos (JPEG/PNG/WebP), tamanho máximo, quantidade máxima — A definir. |
| Documento de apoio | Opcional; uso restrito (ex.: nota, laudo) — avaliar privacidade. |
| Legenda/descrição | Texto curto por anexo. |
| Ordem de exibição | Opcional. |

## Regras
- Validar tipo MIME real, tamanho e dimensões no servidor.
- Armazenar em storage seguro; não expor caminhos internos sensíveis.
- Verificar autorização para visualizar anexos vinculados a registros com visibilidade restrita.
- Definir retenção e exclusão de anexos ao cancelar/excluir registro (LGPD/armazenamento).
- Considerar moderação para conteúdo impróprio (RF-016).

## Critérios de aceite (sugestão)
- **CA-019-1:** Dado participante autorizado, quando anexa arquivo válido ao próprio registro, então o sistema armazena e associa o anexo.
- **CA-019-2:** Dado arquivo inválido (tipo/tamanho), quando tenta anexar, então o sistema rejeita com erro claro.
- **CA-019-3:** Dado usuário sem permissão sobre o registro, quando tenta acessar anexo, então o sistema nega acesso.