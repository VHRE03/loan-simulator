<div align="center">

<img src="assets/logo.svg" width="118" alt="Fintech Loan Simulator logo" />

# Fintech Loan Simulator

**Institutional-grade loan simulation for banking & fintech.**

Calculate your loan schedule: transparent rates, instant estimates and a
real-time amortization breakdown — every number computed by a real REST API.
No mock data, no smoke and mirrors.

<p>
  <img src="https://img.shields.io/badge/Java-21-00236F?style=for-the-badge&logo=openjdk&logoColor=white" alt="Java 21" />
  &nbsp;
  <img src="https://img.shields.io/badge/Spring_Boot-4.1.1-006591?style=for-the-badge&logo=springboot&logoColor=white" alt="Spring Boot 4.1.1" />
  &nbsp;
  <img src="https://img.shields.io/badge/Angular-22-1E3A8A?style=for-the-badge&logo=angular&logoColor=white" alt="Angular 22" />
</p>
<p>
  <img src="https://img.shields.io/badge/TypeScript-6-004666?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript 6" />
  &nbsp;
  <img src="https://img.shields.io/badge/Tailwind_CSS-4.3-004C6E?style=for-the-badge&logo=tailwindcss&logoColor=white" alt="Tailwind CSS 4.3" />
  &nbsp;
  <img src="https://img.shields.io/badge/PostgreSQL-14%2B-003211?style=for-the-badge&logo=postgresql&logoColor=white" alt="PostgreSQL 14+" />
</p>

<p>
  <a href="#-about">About</a> &nbsp;•&nbsp;
  <a href="#-features">Features</a> &nbsp;•&nbsp;
  <a href="#-tech-stack">Tech Stack</a> &nbsp;•&nbsp;
  <a href="#-repository-structure">Structure</a> &nbsp;•&nbsp;
  <a href="#-getting-started">Getting Started</a>
</p>

</div>

---

## 📖 About

**Fintech Loan Simulator** is a full-stack web application that lets users
simulate credit and loan scenarios the way a bank or fintech would: enter the
loan amount, term and annual rate, and the platform computes the **monthly
installment** using the classic *French amortization* method — with all the
math done on the server, so the numbers you see are the numbers the bank
would charge.

But it goes beyond a simple calculator. It also includes a **client
directory** to register and manage borrowers, link simulations to real
customers, and turn a draft simulation into a **completed loan application**
(`DRAFT → COMPLETED` / `EXPIRED`).

The project is organized as a monorepo with two git submodules:

| Submodule | Repository | What it does |
| :--- | :--- | :--- |
| `backend/` | [loan-simulator-api][api-repo] | Spring Boot REST API: simulations, amortization logic and data persistence |
| `frontend/` | [loan-simulator-web][web-repo] | Angular SPA: interactive simulator and client management dashboard |

[api-repo]: https://github.com/VHRE03/loan-simulator-api
[web-repo]: https://github.com/VHRE03/loan-simulator-front

---

## ✨ Features

### 🧮 Loan Simulator (`/simulator`)

- Enter amount, term and rate → get the **server-computed monthly payment**
- Amortization breakdown with key milestones: total interest, total cost, remaining balances and final maturity
- **Complete Loan Application** action that moves a simulation from `DRAFT`
  to a real application and reflects its live status
- Deep links: preselect a borrower straight from the clients view

### 👥 Client Directory (`/clients`)

- Live, paginated registry of borrowers with instant search
- Client registration with bank-grade validation (email format, CURP, age ≥ 18, no duplicates)
- **CSV export** of the client list
- KPI cards computed from real API data: total clients, total simulations, average requested amount

### 🔌 Under the hood

- **No mock data anywhere** — every figure comes from the API
- Interactive **Swagger UI** to explore and test every endpoint
- Versioned database migrations, so the schema evolves safely
- The same validation rules on both sides: the frontend mirrors the backend constraints

---

## 🛠️ Tech Stack

### Backend — [`loan-simulator-api`][api-repo]

| Technology | Version |
| :--- | :--- |
| Java | 21 |
| Spring Boot | 4.1.1 |
| Spring Data JPA (Hibernate) | managed by Boot |
| PostgreSQL | 14+ |
| Flyway (DB migrations) | managed by Boot |
| springdoc-openapi (Swagger UI) | 3.1.0 |
| MapStruct | 1.5.5 |
| Lombok | 1.18.48 |
| Build: Maven (wrapper included) | — |
| Testing: JUnit 5 · Mockito · AssertJ · MockMvc | — |

### Frontend — [`loan-simulator-web`][web-repo]

| Technology | Version |
| :--- | :--- |
| Angular (standalone, signals, zoneless) | 22.2 |
| TypeScript (strict) | 6.0 |
| Tailwind CSS (institutional design tokens) | 4.3 |
| RxJS | 7.8 |
| Icons / typography: Material Symbols Outlined · Inter | — |
| Node.js / npm | 24.x / 11.19 |
| Testing: Vitest · Prettier | 5.x · 3.8 |

---

## 📂 Repository Structure

```
loan-simulator/
├── assets/       # 🖼️ brand assets (logo)
├── backend/      # 🔧 loan-simulator-api  → Spring Boot REST API
└── frontend/     # 🎨 loan-simulator-web  → Angular web app
```

> 💡 Each submodule has its **own README** with detailed setup and run
> instructions for that project.

---

## 🚀 Getting Started

Clone the repository **with its submodules**:

```bash
git clone --recurse-submodules git@github.com:VHRE03/loan-simulator.git
cd loan-simulator
```

Then start each project:

1. **Backend** → follow [`backend/README.md`](backend/README.md)
   *(needs JDK 21+ and a local PostgreSQL)*

   ```bash
   cd backend
   ./mvnw spring-boot:run     # API + Swagger UI on http://localhost:8080
   ```

2. **Frontend** → follow [`frontend/README.md`](frontend/README.md)
   *(needs Node.js 24.x)*

   ```bash
   cd frontend
   npm install
   npm start                 # app on http://localhost:4200
   ```

Open **http://localhost:4200** and start simulating! 🎉

---

<div align="center">

<img src="assets/logo.svg" width="40" alt="Fintech Loan Simulator logo" />

<sub><b>Fintech Loan Simulator</b> — institutional-grade loan simulation</sub>

<sub>Built with ☕ + ❤️ by <a href="https://github.com/VHRE03">VHRE03</a></sub>

</div>
