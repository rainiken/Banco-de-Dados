# Modelo Entidade-Relacionamento (MER) — Sistema de Pousada

## 1. Entidades

As entidades identificadas no minimundo da pousada são:

| Entidade | Definição |
|---|---|
| **Cliente** | Pessoa que realiza reservas na pousada; possui identificação e dados de contato. |
| **Funcionário** | Colaborador responsável por atender as reservas, identificado também pelo cargo. |
| **Reserva** | Registro da solicitação de hospedagem, com data de criação, período previsto e status. |
| **Hospedagem** | Registro da estadia que se concretizou, incluindo check-in, check-out e valores. |
| **Quarto** | Unidade de acomodação da pousada, identificada pelo número, andar e situação de limpeza. |
| **Categoria** | Classificação dos quartos, com nome e preço da diária. |
| **Acompanhante** | Pessoa registrada como acompanhante de uma hospedagem. |
| **Consumo** | Registro de quantidade, data/hora e valor referente ao uso de um produto ou serviço durante a hospedagem. |
| **Produto_Servico** | Item do catálogo de produtos ou serviços oferecidos pela pousada, com tipo e preço unitário. |
| **Pagamento** | Registro do valor, data/hora e forma de pagamento de uma hospedagem. |

## 2. Relacionamentos e Cardinalidades

A seguir estão as **nove associações do diagrama**, mantendo seus nomes e cardinalidades. Os símbolos `1`, `N` e `0..1` seguem a notação do desenho; salvo quando indicado, ele não define todas as participações mínimas.

1. **[Cliente] (1) — realiza — (N) [Reserva]**  
   Um cliente pode realizar diversas reservas. Cada reserva está associada a um único cliente.

2. **[Funcionário] (1) — atende — (N) [Reserva]**  
   Um funcionário pode atender diversas reservas. Cada reserva fica associada a um único funcionário responsável pelo atendimento.

3. **[Reserva] (1) — origina — (0..1) [Hospedagem]**  
   Uma reserva pode ainda não ter resultado em hospedagem ou originar uma única hospedagem. Cada hospedagem decorre de uma reserva no modelo proposto.

4. **[Hospedagem] (N) — ocupa — (1) [Quarto]**  
   Cada hospedagem está vinculada a um quarto. Um mesmo quarto pode ser ocupado por várias hospedagens em momentos diferentes.

5. **[Quarto] (N) — pertence — (1) [Categoria]**  
   Cada quarto pertence a uma categoria. Uma categoria pode classificar diversos quartos.

6. **[Hospedagem] (1) — inclui — (N) [Acompanhante]**  
   Uma hospedagem pode reunir registros de vários acompanhantes; cada acompanhante registrado está ligado a uma hospedagem. O mínimo de acompanhantes não está especificado no desenho além da indicação geral 1:N.

7. **[Hospedagem] (1) — gera — (N) [Consumo]**  
   Uma hospedagem pode gerar diversos registros de consumo. Cada registro de consumo pertence a uma hospedagem.

8. **[Consumo] (N) — contém — (1) [Produto_Servico]**  
   Cada registro de consumo corresponde a um produto ou serviço. Um mesmo item do catálogo pode aparecer em diversos registros de consumo.

9. **[Hospedagem] (1) — recebe — (N) [Pagamento]**  
   Uma hospedagem pode receber diversos pagamentos. Cada registro de pagamento está associado a uma hospedagem.

## 3. Sugestão de Atributos

Os atributos abaixo reproduzem os nomes e tipos apresentados no diagrama do draw.io. A coluna **Classificação** identifica as chaves primárias (PK) e os atributos multivalorados. Os demais são atributos simples, conforme representados no desenho.

### Cliente

| Atributo | Tipo | Classificação |
|---|---|---|
| `cpf` | `string` | **PK** |
| `nome` | `string` | Simples |
| `telefones` | `string_array` | **Multivalorado** |
| `emails` | `string_array` | **Multivalorado** |

### Funcionário

| Atributo | Tipo | Classificação |
|---|---|---|
| `cpf_funcionario` | `string` | **PK** |
| `nome` | `string` | Simples |
| `cargo` | `string` | Simples |

### Reserva

| Atributo | Tipo | Classificação |
|---|---|---|
| `cod_reserva` | `int` | **PK** |
| `data_reserva` | `date` | Simples |
| `data_prevista_in` | `date` | Simples |
| `data_prevista_out` | `date` | Simples |
| `status` | `string` | Simples |

### Hospedagem

| Atributo | Tipo | Classificação |
|---|---|---|
| `cod_hospedagem` | `int` | **PK** |
| `checkin` | `datetime` | Simples |
| `checkout` | `datetime` | Simples |
| `valor_diarias` | `decimal` | Simples no diagrama |
| `valor_total` | `decimal` | Simples no diagrama |

### Quarto

| Atributo | Tipo | Classificação |
|---|---|---|
| `num_quarto` | `int` | **PK** |
| `andar` | `int` | Simples |
| `status_limpeza` | `string` | Simples |

### Categoria

| Atributo | Tipo | Classificação |
|---|---|---|
| `cod_categoria` | `int` | **PK** |
| `nome_categoria` | `string` | Simples |
| `preco_diaria` | `decimal` | Simples |

### Acompanhante

| Atributo | Tipo | Classificação |
|---|---|---|
| `cod_acompanhante` | `int` | **PK** |
| `nome` | `string` | Simples |
| `documento` | `string` | Simples |

### Consumo

| Atributo | Tipo | Classificação |
|---|---|---|
| `cod_consumo` | `int` | **PK** |
| `data_hora` | `datetime` | Simples |
| `quantidade` | `int` | Simples |
| `valor_subtotal` | `decimal` | Simples no diagrama |

### Produto_Servico

| Atributo | Tipo | Classificação |
|---|---|---|
| `cod_item` | `int` | **PK** |
| `nome_item` | `string` | Simples |
| `tipo` | `string` | Simples |
| `preco_unitario` | `decimal` | Simples |

### Pagamento

| Atributo | Tipo | Classificação |
|---|---|---|
| `cod_pagamento` | `int` | **PK** |
| `datahora` | `datetime` | Simples |
| `valor` | `decimal` | Simples |
| `forma_pagamento` | `string` | Simples |

### Atributos multivalorados, compostos e derivados

- **Multivalorados:** `Cliente.telefones` e `Cliente.emails`, ambos representados como `string_array`. Isso indica que um cliente pode ter mais de um telefone e de um e-mail.
- **Compostos:** o desenho não identifica nenhum atributo como composto.
- **Derivados:** o desenho não marca explicitamente nenhum atributo como derivado. Em uma evolução do projeto, `Consumo.valor_subtotal` **poderia** ser calculado a partir da quantidade e do preço unitário; `Hospedagem.valor_total` **poderia** depender das diárias e de outras cobranças. Esses cálculos são **sugestões**, ainda não regras definidas no diagrama.

> **Para uma futura implementação no MySQL:** os relacionamentos poderão ser representados por chaves estrangeiras, e os dados multivalorados de telefone e e-mail poderão exigir tabelas próprias. Essas decisões pertencem à etapa de modelagem lógica e não foram adicionadas ao desenho original.

## 4. Diagrama Entidade e Relacionamento (DER)

O DER foi construído no **draw.io (diagrams.net)** e contém as 10 entidades descritas, suas chaves primárias e os 9 relacionamentos listados.

![DER da Pousada](pousada.png)

- [Visualizar a imagem em tamanho original](pousada.png)
- [Abrir o arquivo editável no draw.io](Pousada.drawio)

> A imagem tem fundo branco apenas para facilitar a visualização das linhas no GitHub. O arquivo `Pousada.drawio` foi preservado sem alterações.
