# Sistema de Gestão de Pousada (Pousada do Seu Zeca)

Este repositório contém a modelagem conceitual de banco de dados para o sistema de gestão da Pousada Vila do Sol, desenvolvido para a disciplina de Banco de Dados.

---

## Mini-Mundo

A **Pousada do Seu Zeca** necessita de um sistema para informatizar o controle de suas acomodações e hospedagens. Atualmente, o controle é manual, o que gera conflitos de datas e atrasos no atendimento.

O sistema deve cadastrar os **Clientes**, armazenando informações como nome, CPF, telefone e e-mail. A pousada possui vários **Quartos**, sendo que cada quarto é identificado por um número, tipo (Solteiro, Casal, Suíte Master), valor da diária e status atual (Disponível, Ocupado, Manutenção).

Os clientes realizam **Reservas** informando a data prevista de entrada (*check-in*) e a data prevista de saída (*check-out*). Cada reserva está vinculada a um único cliente e a um único quarto. 

Ao final da estadia, é gerado um **Pagamento** associado à reserva, contendo a data do pagamento, o valor total calculado e a forma de pagamento (Cartão, PIX, Dinheiro).

---

## Regras de Negócio

* **RN01 - Unicidade de Cliente:** Não é permitido cadastrar dois clientes com o mesmo CPF.
* **RN02 - Vínculo de Reserva:** Toda reserva deve obrigatoriamente estar associada a um único cliente e a um único quarto.
* **RN03 - Histórico de Reservas:** Um cliente pode realizar várias reservas ao longo do tempo, mas uma reserva pertence a apenas um cliente.
* **RN04 - Reuso de Quarto:** Um quarto pode estar presente em diversas reservas em períodos de tempo diferentes.
* **RN05 - Integridade de Pagamento:** Cada pagamento deve estar vinculado a exatamente uma reserva. Uma reserva só possui um pagamento final registrado.# Banco-de-Dados
