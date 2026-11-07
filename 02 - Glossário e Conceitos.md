---
tags: [doalink, glossário, domínio]
---

# Glossário e Conceitos

Relacionado: [[01 - Visão Geral do Produto]] | [[07 - Modelo de Dados e Domínio]]

## Siglas
| Sigla | Significado | Observação |
|---|---|---|
| **RF** | Requisito Funcional | Comportamento/serviço observável do sistema. |
| **RNF** | Requisito Não Funcional | Qualidade, restrição ou propriedade do sistema. |
| **RN** | Regra de Negócio | Política/condição do domínio. |
| **CA** | Critério de Aceite | Condição verificável para confirmar atendimento. |
| **PD** | Ponto/Decisão Pendente | Item que exige definição antes ou durante a implementação. |
| **LGPD** | Lei Geral de Proteção de Dados (Lei nº 13.709/2018) | Aplica-se ao tratamento de dados pessoais. |
| **PF** | Pessoa Física | Identificada por CPF. |
| **PJ** | Pessoa Jurídica | Identificada por CNPJ. |
| **ONG** | Organização Não Governamental | Exemplo de receptor; no sistema, tratada como organização/receptor conforme perfil. |
| **API** | Interface de Programação de Aplicações | Contrato de comunicação do back-end com clientes. |

## Termos do domínio

### Participante
Pessoa física ou jurídica cadastrada na plataforma. Possui dados de identificação/contato e um perfil (doador, receptor ou transportador), conforme decisão de modelagem de perfis. Ver [[03 - Perfis e Permissões]].

### Doador
Perfil de participante que registra **ofertas de doação** e responde a propostas em que está envolvido.

### Receptor
Perfil de participante que representa uma ONG ou organização. Registra **necessidades de doação**, responde a propostas e, no escopo base, deve informar **CNPJ e endereço**.

### Transportador
Perfil de participante que registra **disponibilidades de transporte** (capacidade, rota, data) e responde a propostas.

### Oferta de doação
Registro de item(s) que um doador disponibiliza, com quantidade/unidade e local de retirada/disponibilização. Pode ter visibilidade, estado e validade a definir.

### Necessidade de doação
Registro de item(s) que um receptor precisa, com quantidade/unidade e local de entrega. Pode estar associada a uma campanha emergencial.

### Disponibilidade de transporte
Registro de capacidade logística de um transportador: tipo de veículo, capacidade/unidade, origem, destino/região e data/horário.

### Item / Categoria de item
Tipo de bem doado/solicitado (ex.: alimentos não perecíveis, higiene, roupas). O catálogo e a compatibilidade entre oferta e necessidade dependem de padronização (PD pendente).

### Unidade de medida
Grandeza usada para quantidade/capacidade (ex.: unidade, kg, litro, caixa, pallet). Comparações exigem mesma unidade ou regra de conversão definida.

### Proposta / Combinação
Sugestão gerada pelo sistema (ou fluxo assistido) que relaciona oferta, necessidade e, quando necessário, transporte compatível. Possui participantes envolvidos, respostas e situação.

### Campanha / Evento emergencial
Contexto criado para concentrar necessidades de uma região afetada (ex.: desastre, enchente). Possui região, estado e necessidades relacionadas.

### Situação da doação
Estado do ciclo de vida da doação/proposta no acompanhamento digital. Estados iniciais previstos no documento base: `OFERTADA`, `COMBINADA`, `EM_TRANSPORTE`, `ENTREGUE` (a validar e detalhar).

### Resposta à proposta
Manifestação de um participante envolvido: aceitar ou recusar. Estados sugeridos: `PENDENTE`, `ACEITA`, `RECUSADA`.

### Token de recuperação
Credencial temporária (link/código de uso único, conforme decisão) usada para redefinir senha com segurança.

### Normalização
Transformação de dados para formato canônico de armazenamento/validação (ex.: remover pontuação de CPF/CNPJ/CEP/telefone, padronizar e-mail em minúsculas para comparação).

### Máscara de apresentação
Formatação visual de campos (ex.: `000.000.000-00`) aplicada na interface; não substitui validação nem define o formato persistido.

### Dado pessoal
Informação relacionada a pessoa natural identificada ou identificável (LGPD). No DoaLink: nome, CPF, e-mail, telefone, endereço e, indiretamente, padrões de participação — exigem base legal, finalidade, minimização e controles de acesso.