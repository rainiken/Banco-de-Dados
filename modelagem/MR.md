# Modelo Entidade-Relacionamento (MER) - Pousada do Seu Zeca

## 1. Entidades

* **Cliente**: Representa os hóspedes cadastrados no sistema que realizam reservas na pousada.
* **Quarto**: Representa as acomodações físicas disponíveis para hospedagem na pousada.
* **Reserva**: Representa o agendamento de uma estadia realizado por um cliente para um quarto específico em um determinado período.
* **Pagamento**: Representa a transação financeira referente à quitação do valor total de uma reserva.

---

## 2. Relacionamentos e Cardinalidades

* **[CLIENTE] (1,N) <Realiza> (1,1) [RESERVA]**
  * **Explicação:** Um cliente pode realizar uma ou várias reservas ao longo do tempo (1,N). No entanto, uma reserva específica pertence obrigatoriamente a apenas um cliente (1,1).

* **[QUARTO] (0,N) <Alocado em> (1,1) [RESERVA]**
  * **Explicação:** Um quarto pode estar associado a nenhuma ou a várias reservas em períodos distintos (0,N). Porém, cada reserva aloca exatamente um quarto por período (1,1).

* **[RESERVA] (1,1) <Gera> (0,1) [PAGAMENTO]**
  * **Explicação:** Uma reserva pode não ter pagamento registrado no momento do agendamento, mas gera no máximo um pagamento final (0,1). Cada pagamento é exclusivo de apenas uma reserva (1,1).

---

## 3. Sugestão de Atributos

### Cliente
* **id_cliente** (Chave Primária / PK)
* **nome** (Simples)
* **cpf** (Simples, Único)
* **telefone** (Simples)
* **email** (Simples)

### Quarto
* **id_quarto** (Chave Primária / PK)
* **numero** (Simples, Único)
* **tipo** (Simples)
* **valor_diaria** (Simples)
* **status** (Simples)

### Reserva
* **id_reserva** (Chave Primária / PK)
* **data_checkin** (Simples)
* **data_checkout** (Simples)
* **valor_total** (Simples)
* **status_reserva** (Simples)
* **fk_cliente** (Chave Estrangeira / FK)
* **fk_quarto** (Chave Estrangeira / FK)

### Pagamento
* **id_pagamento** (Chave Primária / PK)
* **data_pagamento** (Simples)
* **valor_pago** (Simples)
* **forma_pagamento** (Simples)
* **fk_reserva** (Chave Estrangeira / FK)

---

## 4. Diagrama Entidade e Relacionamento (DER)

![Diagrama ER - Pousada do Seu Zeca](MER.png)

> **Nota:** O diagrama conceitual foi construído no Draw.io. O arquivo editável `MER.drawio` encontra-se salvo na pasta `modelagem/` deste repositório.
