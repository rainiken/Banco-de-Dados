# Modelo de Entidade e Relacionamento (MER) - Sistema Pousada

## 1. Entidades

* **Cliente:** Representa a pessoa física responsável pela reserva e pela hospedagem.
* **Funcionário:** Representa o colaborador da pousada responsável por efetuar o atendimento e registar a reserva.
* **Reserva:** Representa o agendamento prévio da intenção de hospedagem efetuado pelo cliente.
* **Hospedagem:** Representa a estadia presencial e ativa do cliente na pousada após o check-in.
* **Quarto:** Representa a unidade física de acomodação da pousada.
* **Categoria:** Representa a classificação e a faixa de preço aplicada aos quartos.
* **Acompanhante:** Representa as pessoas adicionais que ocupam o mesmo quarto juntamente com o cliente principal.
* **Consumo:** Representa cada lançamento individual de despesa efetuado durante a estadia.
* **Produto_Serviço:** Representa os itens do catálogo (frigobar, refeições, serviços) disponíveis para consumo.
* **Pagamento:** Representa cada transação financeira realizada para quitar os custos da hospedagem.

[Cliente] (1,1)  (0,N) [Reserva]
Explicação: Um Cliente pode realizar nenhuma ou várias Reservas ao longo do tempo, mas cada Reserva é realizada obrigatoriamente por 1 único Cliente.

[Funcionário] (1,1)  (0,N) [Reserva]
Explicação: Um Funcionário pode atender nenhuma ou várias Reservas, mas cada Reserva é atendida por 1 único Funcionário.

[Reserva] (1,1)  (0,1) [Hospedagem]
Explicação: Uma Reserva origina 1 Hospedagem caso o cliente realize o check-in, ou 0 Hospedagens caso a reserva seja cancelada. Cada Hospedagem deriva de exatamente 1 Reserva.

[Hospedagem] (0,N)  (1,1) [Quarto]
Explicação: Uma Hospedagem ocupa 1 Quarto específico. O mesmo Quarto pode ser ocupado por N Hospedagens ao longo do tempo (em datas diferentes).

[Quarto] (0,N)  (1,1) [Categoria]
Explicação: Cada Quarto pertence a 1 Categoria. Uma Categoria pode classificar N Quartos.

[Hospedagem] (1,1)  (0,N) [Acompanhante]
Explicação: Uma Hospedagem pode incluir 0 ou N Acompanhantes registados. Cada Acompanhante está vinculado a apenas 1 Hospedagem.

[Hospedagem] (1,1)  (0,N) [Consumo]
Explicação: Uma Hospedagem pode gerar 0 ou N lançamentos de Consumo. Cada lançamento de Consumo é atribuído a 1 única Hospedagem.

[Consumo] (0,N)  (1,1) [Produto_Serviço]
Explicação: Cada registo de Consumo refere-se a 1 único Produto_Serviço do catálogo. Um Produto_Serviço pode ser referido em N lançamentos de Consumo.

[Hospedagem] (1,1)  (1,N) [Pagamento]
Explicação: Uma Hospedagem pode receber 1 ou N Pagamentos (ex.: sinal na entrada e quitação no check-out). Cada Pagamento é efetuado para 1 única Hospedagem.

erDiagram
    CLIENTE {
        string cpf PK
        string nome
        string_array telefones
        string_array emails
    }
    FUNCIONARIO {
        string cpf_funcionario PK
        string nome
        string cargo
    }
    RESERVA {
        int cod_reserva PK
        date data_reserva
        date data_prevista_em
        date data_prevista_out
        string status
    }
    HOSPEDAGEM {
        int cod_hospedagem PK
        datetime checkin
        datetime checkout
        decimal valor_diarias
        decimal valor_total
    }
    QUARTO {
        int num_quarto PK
        int andar
        string status_limpeza
    }
    CATEGORIA {
        int cod_categoria PK
        string nome_categoria
        decimal preco_diaria
    }
    ACOMPANHANTE {
        int cod_acompanhante PK
        string nome
        string documento
    }
    CONSUMO {
        int cod_consumo PK
        datetime data_hora
        int quantidade
        decimal valor_subtotal
    }
    PRODUTO_SERVICO {
        int cod_item PK
        string nome_item
        string tipo
        decimal preco_unitario
    }
    PAGAMENTO {
        int cod_pagamento PK
        datetime datahora
        decimal valor
        string forma_pagamento
    }

    CLIENTE ||--o{ RESERVA : "realiza (1:N)"
    FUNCIONARIO ||--o{ RESERVA : "atende (1:N)"
    RESERVA ||--o| HOSPEDAGEM : "origina (1:0..1)"
    HOSPEDAGEM }|--|| QUARTO : "ocupa (N:1)"
    QUARTO }|--|| CATEGORIA : "pertence (N:1)"
    HOSPEDAGEM ||--o{ ACOMPANHANTE : "inclui (1:N)"
    HOSPEDAGEM ||--o{ CONSUMO : "gera (1:N)"
    CONSUMO }|--|| PRODUTO_SERVICO : "refere (N:1)"
    HOSPEDAGEM ||--|{ PAGAMENTO : "recebe (1:N)"
