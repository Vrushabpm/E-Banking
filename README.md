# 🏦 E-Banking System — Full Stack Web Application

![Java](https://img.shields.io/badge/Java-21-orange?style=for-the-badge&logo=java)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.5-brightgreen?style=for-the-badge&logo=springboot)
![React](https://img.shields.io/badge/React-19-blue?style=for-the-badge&logo=react)
![MySQL](https://img.shields.io/badge/MySQL-8.0-blue?style=for-the-badge&logo=mysql)
![Redis](https://img.shields.io/badge/Redis-7.0-red?style=for-the-badge&logo=redis)
![JWT](https://img.shields.io/badge/JWT-Auth-black?style=for-the-badge&logo=jsonwebtokens)

A secure, full-stack online banking application where users can register, verify OTP, manage bank accounts, deposit money via Razorpay, transfer funds, and view transaction history. Admins can manage users and approve accounts through a dedicated dashboard.

---

## 🚀 Live Demo

> Frontend: `http://localhost:5173`
> Backend API: `http://localhost:8055`

---

## 📸 Screenshots

> _Add screenshots of your Login, Dashboard, and Admin pages here_

---

## 🛠️ Tech Stack

### Frontend
| Technology | Purpose |
|---|---|
| React 19 + Vite | UI Framework |
| Bootstrap 5 (Dark) | Styling & Responsive Design |
| React Router DOM v7 | Client-side Routing |
| Axios | HTTP Client with JWT Interceptor |
| React Toastify | Toast Notifications |

### Backend
| Technology | Purpose |
|---|---|
| Spring Boot 3.5 | Backend Framework |
| Spring Security + JWT | Authentication & Authorization |
| Spring Data JPA + Hibernate | ORM & Database Access |
| MySQL | Primary Database |
| Redis | OTP Temporary Storage |
| JavaMailSender | OTP Email Sending |
| Razorpay SDK | Payment Gateway |
| MapStruct | DTO Mapping |
| SpringDoc OpenAPI | API Documentation (Swagger) |

---

## ✨ Features

### 👤 User Module
- ✅ User Registration with OTP Email Verification
- ✅ Secure Login with JWT Authentication
- ✅ Forgot Password & Reset Password via OTP
- ✅ Create Savings Bank Account
- ✅ Check Account Balance
- ✅ Deposit Money via Razorpay Payment Gateway
- ✅ Fund Transfer between Accounts
- ✅ View Transaction History

### 🔐 Admin Module
- ✅ Admin Dashboard
- ✅ View All Registered Users
- ✅ Approve / Reject Pending Accounts
- ✅ Block / Unblock User Accounts
- ✅ View All Bank Transactions
- ✅ View Bank Account Details

---

## 🏗️ Project Architecture

```
ebanking/
├── bank-frontend-main/          # React Frontend
│   ├── src/
│   │   ├── components/          # Reusable UI Components
│   │   ├── pages/               # Page Components
│   │   ├── services/            # Axios API Services
│   │   └── App.jsx              # Main App with Routing
│   └── package.json
│
└── ebanking-SpringBoot-RestApi-main/   # Spring Boot Backend
    └── src/main/java/org/jsp/ebanking/
        ├── controller/          # REST API Controllers
        ├── service/             # Business Logic Layer
        ├── repository/          # JPA Repositories
        ├── entity/              # Database Entities
        ├── dto/                 # Data Transfer Objects
        ├── config/              # Security & JWT Config
        ├── mapper/              # MapStruct Mappers
        ├── exception/           # Global Exception Handling
        └── util/                # JWT & Payment Utilities
```

---

## 🔄 Application Flow

```
User Registers → OTP sent to Email (via Redis temp storage)
     ↓
User verifies OTP → Account Created in MySQL
     ↓
User Logs In → JWT Token generated & returned
     ↓
JWT Token stored in frontend → sent in every API request
     ↓
User performs Banking Operations → Data saved in MySQL
```

---

## ⚙️ Setup & Installation

### Prerequisites
- Java JDK 21+
- Node.js v20+
- MySQL 8.0+
- Redis
- Maven 3.9+

---

### 1️⃣ Clone the Repository
```bash
git clone https://github.com/Vrushabpm/E-Banking.git
cd E-Banking
```

---

### 2️⃣ Setup MySQL Database
```sql
CREATE DATABASE ebankingdb;
```

---

### 3️⃣ Configure Backend

Open `ebanking-SpringBoot-RestApi-main/src/main/resources/application-dev.yml` and update:

```yaml
spring:
  datasource:
    url: jdbc:mysql://localhost:3306/ebankingdb
    username: root
    password: YOUR_MYSQL_PASSWORD
  data:
    redis:
      host: localhost
      port: 6379
  mail:
    username: YOUR_GMAIL@gmail.com
    password: YOUR_GMAIL_APP_PASSWORD
server:
  port: 8055
jwt:
  secret: YOUR_JWT_SECRET_KEY_MIN_32_CHARACTERS
razorpay:
  key: YOUR_RAZORPAY_KEY
  secret: YOUR_RAZORPAY_SECRET
```

---

### 4️⃣ Run Backend
```bash
cd ebanking-SpringBoot-RestApi-main
mvn spring-boot:run
```
Backend starts at `http://localhost:8055` ✅

---

### 5️⃣ Configure Frontend

Create `.env` file inside `bank-frontend-main/`:
```
VITE_API_BASE=http://localhost:8055
```

---

### 6️⃣ Run Frontend
```bash
cd bank-frontend-main
npm install
npm run dev
```
Frontend starts at `http://localhost:5173` ✅

---

## 📡 API Endpoints

### Auth APIs
| Method | Endpoint | Description |
|---|---|---|
| POST | `/auth/register` | Register new user |
| POST | `/auth/verify-otp` | Verify OTP |
| POST | `/auth/login` | User login |
| POST | `/auth/forgot-password` | Forgot password |
| POST | `/auth/reset-password` | Reset password |

### User APIs
| Method | Endpoint | Description |
|---|---|---|
| POST | `/user/create-account` | Create bank account |
| GET | `/user/balance` | Check balance |
| POST | `/user/deposit` | Deposit money |
| POST | `/user/transfer` | Fund transfer |
| GET | `/user/transactions` | View transactions |

### Admin APIs
| Method | Endpoint | Description |
|---|---|---|
| GET | `/admin/users` | Get all users |
| GET | `/admin/pending-accounts` | Get pending accounts |
| PUT | `/admin/approve/:id` | Approve account |
| PUT | `/admin/block/:id` | Block/Unblock user |

---

## 🔒 Security

- Passwords are **BCrypt hashed** before storing
- All APIs (except auth) are protected with **JWT Bearer Token**
- OTPs are stored in **Redis** with expiry time
- Role-based access control for **Admin** and **User** roles
- Spring Security filters validate JWT on every request

---

## 👨‍💻 Developer

**Vrushabh PM**
- 📧 vrushab932@gmail.com
- 🐙 GitHub: [Vrushabpm](https://github.com/Vrushabpm)

---

## 🎓 Project Info

- **Type:** Java Full Stack Internship Project
- **Institute:** JSpiders
- **Tech Stack:** Spring Boot + React + MySQL + Redis + JWT

---

## 📄 License

This project is for educational purposes only.
