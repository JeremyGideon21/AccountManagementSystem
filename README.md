Below is your **updated and expanded README.md** — combining your existing content **PLUS all new tasks (6–10)** in a clean, professional **Markdown format** ready for GitHub.

---

# 🏦 AccountManagementSystem

# Banking System API

A **Spring Boot** project that simulates a simple **banking platform** supporting account management, fund transfers, transaction history, interest calculation, and additional banking/financial service APIs.
This project is designed to strengthen skills in **RESTful API development**, **transaction handling**, **backend business logic**, **Spring Boot**, and **MySQL**.

---

## ✨ Features

### 💰 Account Management

* Create new bank accounts
* Deposit and withdraw funds
* View account details and balance

### 🔁 Fund Transfers

* Transfer money between accounts
* Prevent self-transfer and insufficient balance
* Fully transaction-safe using `@Transactional`

### 📜 Transaction History

* Logs deposits, withdrawals, and transfers
* Retrieve recent *N* transactions per account

### 📈 Interest Calculator

* Calculates simple interest
* Formula: `(Principal × Rate × Time) / 100`
* Validates positive input

---

## 🧠 Tech Stack

| Component      | Technology              |
| -------------- | ----------------------- |
| **Backend**    | Spring Boot 3.x         |
| **Language**   | Java 17                 |
| **Database**   | MySQL / H2 (testing)    |
| **ORM**        | Spring Data JPA         |
| **Validation** | Jakarta Bean Validation |
| **Testing**    | JUnit 5                 |
| **Build Tool** | Maven                   |

---

# 🧾 API Endpoints

## 1️⃣ Account Management

| Method   | Endpoint                  | Description          |
| -------- | ------------------------- | -------------------- |
| **POST** | `/accounts`               | Create a new account |
| **GET**  | `/accounts/{id}`          | Get account details  |
| **POST** | `/accounts/{id}/deposit`  | Deposit funds        |
| **POST** | `/accounts/{id}/withdraw` | Withdraw funds       |

### Example Request

```json
{
  "name": "Simon",
  "initialDeposit": 10000
}
```

### Example Response

```json
{
  "accountID": 101,
  "balance": 10000
}
```

---

## 2️⃣ Fund Transfer

| Method   | Endpoint             | Description                     |
| -------- | -------------------- | ------------------------------- |
| **POST** | `/accounts/transfer` | Transfer funds between accounts |

---

## 3️⃣ Transaction History

| Method  | Endpoint                      | Description               |
| ------- | ----------------------------- | ------------------------- |
| **GET** | `/accounts/{id}/transactions` | Fetch last N transactions |

### Example Response

```json
[
  { "type": "DEPOSIT", "amount": 1000, "date": "2025-10-24" },
  { "type": "WITHDRAW", "amount": 100, "date": "2025-10-25" },
  { "type": "TRANSFER_OUT", "amount": 1500, "date": "2025-10-25" }
]
```

---

## 4️⃣ Interest Calculator

| Method   | Endpoint                     | Description               |
| -------- | ---------------------------- | ------------------------- |
| **POST** | `/api/v1/interest/calculate` | Calculate simple interest |

### Example Request

```json
{
  "principal": 10000,
  "rate": 6.5,
  "time": 2
}
```

### Example Response

```json
{
  "Interest": 1300,
  "TotalAmount": 11300,
  "Message": "Calculation successful"
}
```

---

---

## 🧮 **Task  – Interest Calculator API (Basic Version)**

### Endpoint:

`POST /calculateInterest`

### Inputs:

* principal
* annual rate
* time (years)

### Output:

* interest
* totalAmount

### Example

```json
{
  "principal": 10000,
  "rate": 6.5,
  "time": 2
}
```

```json
{
  "interest": 1300,
  "totalAmount": 11300
}
```

---

## 🏦 **Task 5 – Loan Eligibility Checker**

### Endpoint:

`POST /loanEligibility`

### Inputs:

* age
* annualIncome
* creditScore
* existingLoanAmount

### Eligibility Rules:

* Minimum age: **21**
* Income must be **> ₹3,00,000 / year**
* Credit score must be **≥ 700**
* Loan-to-Income ratio **< 40%**

### Output:

* `"Eligible"` or `"Not Eligible"`
* Reason message

### Example

```json
{
  "age": 25,
  "annualIncome": 500000,
  "creditScore": 720,
  "existingLoanAmount": 100000
}
```

---

## 🏛️ **Task 6 – Fixed Deposit & Maturity Calculator**

### Endpoint:

`POST /fixedDeposit`

### Inputs:

* deposit amount
* rate of interest
* tenure (years)

### Logic:

* Uses **compound interest**
* Optional: Premature withdrawal → 1% penalty

### Example

```json
{
  "amount": 50000,
  "rate": 7,
  "tenure": 3
}
```

```json
{
  "maturityAmount": 61252,
  "interestEarned": 11252
}
```

---

## 🧾 **Task 7 – Monthly Statement Generator**

### Endpoint:

`GET /statement/{accountId}?month=09&year=2025`

### Output Includes:

* Opening balance
* Total deposits
* Total withdrawals
* Closing balance
* Month-wise summary
* Optional: CSV/PDF export

### Example

```json
{
  "month": "September",
  "openingBalance": 15000,
  "totalDeposits": 3000,
  "totalWithdrawals": 2000,
  "closingBalance": 16000
}
```

---

## 🛡️ **Task 8 – Simple Admin Dashboard API**

### Endpoints:

| Endpoint                | Purpose                           |
| ----------------------- | --------------------------------- |
| `/admin/totalCustomers` | Count all customers               |
| `/admin/totalDeposits`  | Sum of all deposits               |
| `/admin/topAccounts`    | Accounts with balance > ₹1,00,000 |
| `/admin/loanSummary`    | Loan distribution report          |

Focus: Aggregation queries, optimized SQL, clean JSON.

---

## 💳 **Task 9 – Credit Card Bill Calculator**

### Endpoint:

`POST /creditCardBill`

### Inputs:

* totalSpending
* paymentsMade
* dueDate
* currentDate

### Output:

* pendingAmount
* late interest (if overdue)
* status: `"On Time"` or `"Late Payment"`

---

## 🏧 **Task 10 – Mini ATM Simulator**

### Endpoints:

* `POST /atm/validateCard`
* `POST /atm/verifyPin`
* `POST /atm/withdraw` (daily limit)
* `GET /atm/balance`

Can use dummy JSON data or database tables.

---

# ⚙️ Setup Instructions

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/<your-username>/banking-system-api.git
cd banking-system-api
```

### 2️⃣ Configure Database (MySQL)

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/bankdb
spring.datasource.username=root
spring.datasource.password=yourpassword
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

### 3️⃣ Run the Application

```bash
mvn clean install
mvn spring-boot:run
```

App runs at: **[http://localhost:8080](http://localhost:8080)**

---

## 🧪 Testing

```bash
mvn test
```

Tests include:

* Interest calculator
* Fund transfers
* Loan eligibility
* Fixed deposit
* Transaction history
* Admin dashboard metrics

---

## 📂 Project Structure

```
src/
 ├── main/java/com/example/bankingsystem/
 │   ├── controller/       # REST Controllers
 │   ├── service/          # Business Logic
 │   ├── dto/              # DTOs
 │   ├── model/            # Entities
 │   ├── repository/       # JPA Repositories
 │   └── exception/        # Global Error Handling
 └── test/java/...         # JUnit Tests
```

---

## 💡 Highlights

* Clean layered architecture
* Strong validation and exception handling
* Transaction-safe money operations
* Advanced banking simulation tasks
* Ideal for backend learning & portfolio projects

---

## 👨‍💻 Author

**JEREMY GIDEON**

---

## 🪪 License

