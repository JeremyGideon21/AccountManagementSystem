# AccountManagementSystem

# 🏦 Banking System API

A **Spring Boot** project that simulates a simple **banking platform** featuring account management, fund transfers, transaction tracking, and interest calculation.
This project is designed to practice **RESTful API development**, **transaction handling**, and **data consistency** using **Spring Boot** and **MySQL**.

---

## ✨ Features

### 💰 Account Management

* Create new bank accounts
* Deposit and withdraw money
* View account details and balance

### 🔁 Fund Transfers

* Transfer money between two accounts
* Ensures sufficient balance and prevents self-transfer
* Uses `@Transactional` for atomic and consistent updates

### 📜 Transaction History

* Logs all deposits, withdrawals, and transfers
* Retrieve the last *N* transactions for an account

### 📈 Interest Calculator

* Calculates simple interest and total payable amount
* Formula: `(Principal × Rate × Time) / 100`
* Validates for positive input values

---

## 🧠 Tech Stack

| Component      | Technology               |
| -------------- | ------------------------ |
| **Backend**    | Spring Boot 3.x          |
| **Language**   | Java 17                  |
| **Database**   | MySQL / H2 (for testing) |
| **ORM**        | Spring Data JPA          |
| **Validation** | Jakarta Bean Validation  |
| **Testing**    | JUnit 5                  |
| **Build Tool** | Maven                    |

---

## 🧾 API Endpoints

### 1️⃣ Account Management

| Method   | Endpoint                  | Description          |
| -------- | ------------------------- | -------------------- |
| **POST** | `/accounts`               | Create a new account |
| **GET**  | `/accounts/{id}`          | Get account details  |
| **POST** | `/accounts/{id}/deposit`  | Deposit funds        |
| **POST** | `/accounts/{id}/withdraw` | Withdraw funds       |

**Example Request**

```json
{
  "name": "Simon",
  "initialDeposit": 10000
}
```

**Example Response**

```json
{
  "accountID": 101,
  "balance": 10000
}
```

---

### 2️⃣ Fund Transfer

| Method   | Endpoint             | Description                     |
| -------- | -------------------- | ------------------------------- |
| **POST** | `/accounts/transfer` | Transfer funds between accounts |




---

### 3️⃣ Transaction History

| Method  | Endpoint                      | Description                                 |
| ------- | ----------------------------- | ------------------------------------------- |
| **GET** | `/accounts/{id}/transactions` | Retrieve last N transactions for an account |

**Example Response**

```json
[
  { "type": "DEPOSIT", "amount": 1000, "date": "2025-10-24" },
  { "type": "WITHDRAW", "amount": 100, "date": "2025-10-25" },
  { "type": "TRANSFER_OUT", "amount": 1500, "date": "2025-10-25" }
]
```

---

### 4️⃣ Interest Calculator

| Method   | Endpoint                     | Description                                        |
| -------- | ---------------------------- | -------------------------------------------------- |
| **POST** | `/api/v1/interest/calculate` | Calculate simple interest and total payable amount |

**Example Request**

```json
{
  "principal": 10000,
  "rate": 6.5,
  "time": 2
}
```

**Example Response**

```json
{
  "Interest": 1300,
  "TotalAmount": 11300,
  "Message": "Calculation successful"
}
```

---

## ⚙️ Setup Instructions

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/<your-username>/banking-system-api.git
cd banking-system-api
```

### 2️⃣ Configure Database (MySQL)

Edit the file `src/main/resources/application.properties`:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/bankdb
spring.datasource.username=root
spring.datasource.password=yourpassword
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

> 💡 For quick testing, you can switch to the H2 in-memory database.

### 3️⃣ Build & Run the Application

```bash
mvn clean install
mvn spring-boot:run
```

App runs at:
👉 **[http://localhost:8080](http://localhost:8080)**

---

## 🧪 Testing

Run unit tests using:

```bash
mvn test
```

Includes:

* Interest calculation tests
* Fund transfer validations
* Deposit and withdrawal operations
* Transaction history consistency checks

---

## 📂 Project Structure

```
src/
 ├── main/java/com/example/bankingsystem/
 │   ├── controller/       # REST Controllers
 │   ├── service/          # Business Logic
 │   ├── dto/              # Data Transfer Objects
 │   ├── model/            # Entity Models
 │   ├── repository/       # JPA Repositories
 │   └── exception/        # Exception Handling
 └── test/java/...         # JUnit Test Cases
```

---

## 💡 Highlights

* Layered architecture for clean design
* DTOs ensure smooth API data exchange
* Robust validation and exception handling
* Transaction-safe money transfers
* Modular and reusable service layer

---

## 👨‍💻 Author

**JEREMY GIDEON**
---

## 🪪 License

This project is licensed under the **MIT License** — feel free to use and modify it.

---
