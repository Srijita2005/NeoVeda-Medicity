# NeoVeda Medicity — Hospital Management System

A web-hosted, interactive Hospital Management System modeled on an **Indian superspeciality medical institution** with 21 clinical departments. It features a 3NF-normalized PostgreSQL persistence layer, strict Employee Code authentication, and a scalable architecture.

## 🌟 Key Features

- **Comprehensive Department Management**: Operating across 21 clinical departments (Cardiology, Neurology, Oncology, etc.).
- **Role-Based Access Control (RBAC)**: Strict authentication using Employee Code + Password mapping to specific roles (`Super Admin`, `Hospital Admin`, `Department Admin`, `Doctor`, `Nurse`, `Receptionist`, `Staff`).
- **Patient Management**: Complete end-to-end tracking of patients via Unique Hospital ID (UHID), containing demographics and previous medical records.
- **Appointment & Admission Modules**: Real-time management of doctor schedules, OPD booking, and ward/bed admissions.
- **Billing & Invoicing**: Structured billing pipeline covering consultations, procedures, lab tests, and room charges.
- **Audit Logging**: Immutable audit trails tracking every action performed by employees for compliance.

## 🏗 System Architecture

The project splits into three primary layers:
- **Client (Frontend)**: React Single-Page Application (SPA) built with Vite and React Router.
- **Server (Backend)**: Node.js + Express API Layer with robust JWT & bcrypt-based authentication.
- **Database**: Fully normalized 3NF PostgreSQL database (hosted on Neon), scaling transparently. 

## 🛠 Tech Stack

- **Frontend**: React (v18), Vite, React Router DOM
- **Backend**: Node.js, Express, jsonwebtoken, bcryptjs, morgan
- **Database**: PostgreSQL (pg), Neon Serverless Postgres
- **Security**: express-rate-limit, helmet, cors

## 📁 Repository Structure

```text
├── client/                 # React SPA frontend
│   ├── src/
│   ├── package.json
│   └── vite.config.js
├── server/                 # Node.js backend
│   ├── src/
│   │   ├── config/         # DB and Env config
│   │   ├── controllers/    # API controllers
│   │   ├── middleware/     # Auth, RBAC, Rate-Limiting
│   │   ├── routes/         # API Endpoint Definitions
│   │   ├── models/         # Database models/queries
│   │   └── server.js       # Entry point
│   └── package.json
├── database/               # SQL Scripts & Migrations
│   ├── migrations/         # DDL execution files
│   └── seed/               # Data seeding scripts
└── docs/                   # Architectural & technical documentation
```

## 🚀 Getting Started

### Prerequisites
- [Node.js](https://nodejs.org/) (v18+)
- [PostgreSQL](https://postgresql.org/) database / [Neon](https://neon.tech/) DB connection string

### 1. Database Setup
Ensure you have a running PostgreSQL database instance. You can run migrations via the utility scripts provided in the server, or run the SQL files from the `database/migrations` directory sequentially to set up the normalized schema. 
```bash
cd server
npm run migrate
npm run seed
```

### 2. Backend Server

Navigate to the `server` directory and install dependencies:
```bash
cd server
npm install
```

Configure your environment variables (create a `.env` file referencing database connection details and your JWT secret).

Start the server:
```bash
# Development mode
npm run dev

# Production
npm start
```

### 3. Frontend Client

Navigate to the `client` directory and install dependencies:
```bash
cd client
npm install
```

Start the Vite development server:
```bash
npm run dev
```
The application will be accessible at `http://localhost:3001`.

## 🔒 Authentication

Authentication relies strictly on the **Employee Code** model. No standard username/email combinations are permitted.
Format: `EMP-{DEPT_CODE}-{SEQUENCE}` (e.g., `EMP-CARD-00001` for Cardiology).

The initial state requires setting up Super Admin credentials, which subsequently can provision further administrative or clinical staff depending on clearance levels.

## 📝 Documentation
For deeper architectural insight, please refer to the detailed artifacts in the `docs` directory:
- [Architecture & Execution Plan](docs/implementation_plan.md)
- [Architecture Reference](docs/architecture.md)

## 📄 License
See the [LICENSE](LICENSE) file for more information.
