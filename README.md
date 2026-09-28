# Sistema de Gestão de Pousada

## 1. Descrição do Minimundo
Uma pousada necessita de um sistema centralizado para automatizar a gestão de hospedagens, reservas, controlo de acomodações e faturação de consumos extras. 

Atualmente, o controlo manual dificulta a verificação da disponibilidade de quartos, a gestão de acompanhantes e a rastreabilidade dos itens consumidos pelos hóspedes durante a estadia. O sistema visa resolver o problema de sobreposição de reservas, perda de registos de consumos e falta de histórico financeiro por hospedagem.

## 2. Processos Principais
* **Gestão de Clientes e Funcionários:** Registo dos hóspedes responsáveis e dos colaboradores que realizam os atendimentos.
* **Gestão de Reservas:** Registo prévio da intenção de estadia, especificando datas previstas de entrada e saída.
* **Check-in e Hospedagem:** Abertura da estadia efetiva no momento da chegada do cliente e alocação do quarto.
* **Registo de Acompanhantes:** Registo dos membros adicionais vinculados à mesma hospedagem.
* **Controlo de Consumo Extra:** Lançamento de produtos (frigobar, restaurante) e serviços (lavandaria, passeios) consumidos durante a estadia.
* **Check-out e Pagamento:** Fechamento da conta com cálculo das diárias e consumos, permitindo pagamentos fracionados ou integrais.

## 3. Regras de Negócio
1. Um **Cliente** pode realizar várias reservas ao longo do tempo, mas cada **Reserva** pertence obrigatoriamente a apenas um cliente.
2. Cada **Reserva** é registada por um **Funcionário**.
3. Uma **Reserva** pode originar no máximo uma **Hospedagem** (no check-in) ou nenhuma (em caso de cancelamento).
4. Várias **Hospedagens** em datas distintas ocupam o mesmo **Quarto**.
5. Cada **Quarto** pertence a uma **Categoria** que determina o valor base da sua diária.
6. Uma **Hospedagem** pode incluir múltiplos **Acompanhantes**, gerar múltiplos lançamentos de **Consumo** e receber múltiplos **Pagamentos**.
