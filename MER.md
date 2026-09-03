Este documento descreve as entidades, atributos e relacionamentos do banco de dados da Pousada do Seu Zeca.

---

## Entidades e Atributos

### 1. CLIENTE
Representa os hóspedes cadastrados no sistema.
* **id_cliente** (Inteiro, Chave Primária, Auto-incremento)
* **nome** (Texto, Obrigatório)
* **cpf** (Texto, Único, Obrigatório)
* **telefone** (Texto, Obrigatório)
* **email** (Texto, Opcional)

### 2. QUARTO
Representa as acomodações disponíveis na pousada.
* **id_quarto** (Inteiro, Chave Primária, Auto-incremento)
* **numero** (Inteiro, Único, Obrigatório)
* **tipo** (Texto, Obrigatório) — *Ex: Solteiro, Casal, Suíte*
* **valor_diaria** (Decimal, Obrigatório)
* **status** (Texto, Obrigatório) — *Ex: Disponível, Ocupado, Manutenção*

### 3. RESERVA
Representa a solicitação de hospedagem feita por um cliente.
* **id_reserva** (Inteiro, Chave Primária, Auto-incremento)
* **data_checkin** (Data, Obrigatório)
* **data_checkout** (Data, Obrigatório)
* **valor_total** (Decimal, Obrigatório)
* **status_reserva** (Texto, Obrigatório) — *Ex: Confirmada, Cancelada, Finalizada*
* **fk_cliente** (Inteiro, Chave Estrangeira -> CLIENTE)
* **fk_quarto** (Inteiro, Chave Estrangeira -> QUARTO)

### 4. PAGAMENTO
Representa a quitação financeira de uma reserva.
* **id_pagamento** (Inteiro, Chave Primária, Auto-incremento)
* **data_pagamento** (Data, Obrigatório)
* **valor_pago** (Decimal, Obrigatório)
* **forma_pagamento** (Texto, Obrigatório) — *Ex: Cartão, PIX, Dinheiro*
* **fk_reserva** (Inteiro, Chave Estrangeira -> RESERVA)

---

## Relacionamentos e Cardinalidades

### CLIENTE — (1,N) ------- (1,1) — RESERVA
* Um **Cliente** pode fazer **uma ou várias (1,N)** reservas.
* Uma **Reserva** pertence a **um e somente um (1,1)** cliente.

### QUARTO — (0,N) ------- (1,1) — RESERVA
* Um **Quarto** pode estar associado a **zero ou várias (0,N)** reservas ao longo do tempo.
