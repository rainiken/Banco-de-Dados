# Sistema de Gestão de Pousada — Modelagem de Dados

## 1. Descrição do minimundo

Este projeto apresenta a modelagem de dados de um **sistema de gestão de pousada**. Seu objetivo é organizar informações sobre clientes, funcionários, reservas, hospedagens, quartos, categorias de quartos, acompanhantes, produtos e serviços consumidos e pagamentos.

No funcionamento de uma pousada, é necessário registrar quem fez uma reserva, qual funcionário a atendeu e, quando a reserva se concretiza, acompanhar a hospedagem e o quarto ocupado. Durante a estadia, também podem ser registrados acompanhantes, consumos e pagamentos.

**Problema do mundo real:** quando esses dados são controlados de forma dispersa, a pousada pode ter dificuldades para consultar o histórico de reservas e hospedagens, identificar o quarto associado a uma estadia, acompanhar consumos e verificar os pagamentos. O banco de dados proposto procura reunir essas informações de forma organizada e relacionada.

## 2. Contexto de aplicação

O sistema é voltado à organização das rotinas de atendimento e hospedagem de uma pousada. Os funcionários registram e atendem reservas, enquanto o cadastro de clientes mantém os dados de contato. As hospedagens registram as datas e os valores da estadia; os quartos pertencem a categorias que possuem preços de diária. Os consumos de produtos ou serviços e os pagamentos são vinculados às hospedagens.

## 3. Regras de negócio representadas no modelo

1. Um **cliente** pode realizar várias **reservas**, e cada reserva está associada a um cliente.
2. Um **funcionário** pode atender várias **reservas**, e cada reserva é atendida por um funcionário.
3. Uma **reserva** pode originar **zero ou uma hospedagem**. Cada hospedagem está ligada a uma reserva.
4. Cada **hospedagem** ocupa um **quarto**, e um quarto pode aparecer em diferentes hospedagens ao longo do tempo.
5. Cada **quarto** pertence a uma **categoria**, e uma categoria pode agrupar vários quartos.
6. Uma **hospedagem** pode estar associada a **acompanhantes**, conforme o relacionamento 1:N desenhado.
7. Uma **hospedagem** pode gerar vários registros de **consumo**; cada consumo se refere a um **produto ou serviço**.
8. Uma **hospedagem** pode receber vários registros de **pagamento**.
9. O cadastro de **cliente** admite múltiplos telefones e e-mails, conforme indicado no diagrama.

> **Observação de modelagem:** as cardinalidades acima seguem o diagrama original. Fora da relação Reserva–Hospedagem, o desenho informa principalmente relações 1:N ou N:1, sem detalhar todas as participações mínimas. Portanto, regras como a obrigatoriedade de acompanhantes, consumos e pagamentos ainda precisam ser validadas no levantamento de requisitos.

## 4. Principais processos atendidos

- **Cadastrar clientes** e manter seus dados de contato.
- **Cadastrar funcionários** e identificar quem atendeu cada reserva.
- **Registrar reservas**, suas datas previstas e o status.
- **Acompanhar hospedagens**, com check-in, check-out, quarto e valores.
- **Organizar quartos e categorias**, incluindo andar, situação da limpeza e preço da diária por categoria.
- **Registrar acompanhantes, consumos e pagamentos** ligados a cada hospedagem.
