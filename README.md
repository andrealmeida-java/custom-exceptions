# Hotel Reservation System (Java)

Projeto simples em Java desenvolvido com foco em **Programação Orientada a Objetos**, **tratamento de exceções** e **uso da API moderna de datas (`java.time`)**.

O sistema simula o cadastro e a atualização de uma reserva de hotel via terminal, aplicando regras de negócio e validações por meio de exceções personalizadas.

---

## 📌 Funcionalidades

- Criar uma reserva informando:
  - Número do quarto
  - Data de check-in
  - Data de check-out
- Exibir os dados da reserva
- Atualizar as datas da reserva
- Aplicar regras de negócio diretamente no domínio
- Tratar erros por meio de exceções personalizadas

---

## 🛠️ Tecnologias utilizadas

- Java 21+
- Programação Orientada a Objetos (POO)
- API `java.time`
  - `LocalDate`
  - `DateTimeFormatter`
  - `ChronoUnit`
- Exceções personalizadas
- Entrada de dados via `Scanner`

---

## 📂 Estrutura do projeto

```
src/
├── application
│ └── Program.java
├── model
│ ├── entities
│ │ └── Reservation.java
│ └── exceptions
│ └── DomainException.java
```

---

## 🔧 Regras de negócio

A classe `Reservation` é responsável por garantir a integridade das reservas, aplicando as seguintes regras:

- A data de **check-out deve ser posterior** à data de check-in
- As datas informadas para **atualização da reserva devem ser futuras**
- A duração da reserva é calculada com base no número exato de dias entre as datas

Qualquer violação dessas regras resulta no lançamento de uma **exceção de domínio (`DomainException`)**.

---

## ⏱️ Cálculo da duração da reserva

A duração da reserva é calculada utilizando a API moderna de datas do Java:

- `ChronoUnit.DAYS.between(checkIn, checkOut)`

Essa abordagem garante precisão no cálculo do número total de noites da reserva.

---

## ⚠️ Tratamento de exceções

O projeto utiliza uma exceção personalizada chamada `DomainException`, que estende `RuntimeException`.

Ela é usada para representar erros de regra de negócio, como:

- Datas inválidas
- Tentativa de atualizar a reserva com datas passadas
- Check-out anterior ou igual ao check-in

Essas exceções são tratadas na camada de aplicação (`Program`).

---

## ▶️ Como executar o projeto

### Pré-requisitos

- Java JDK 21 ou superior
- Terminal (Linux, Windows ou macOS)

---

### Compilação

No diretório `src` do projeto:

```bash
javac application/Program.java
