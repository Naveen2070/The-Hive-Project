<p align="center">
<img src="assets/the-hive-project-logo.png" alt="The Hive Project Logo" width="150"/>
</p>

<h1 align="center">The Hive Project 🐝</h1>

<p align="center"><em>A Polyglot Microservices Ecosystem for Events, Movies, and Streaming.</em></p>

<p align="center">
<img src="https://img.shields.io/badge/Architecture-Polyglot_Microservices-1f6feb" alt="Architecture"/>
<img src="https://img.shields.io/badge/Gateway-Nginx-009639" alt="Gateway"/>
<img src="https://img.shields.io/badge/Messaging-RabbitMQ-FF6600" alt="Messaging"/>
<img src="https://img.shields.io/badge/Containerization-Docker-2496ED" alt="Containerization"/>
</p>

<p align="center">
<img src="https://img.shields.io/badge/Frontend-React_+_Angular-61DAFB" alt="Frontend"/>
<img src="https://img.shields.io/badge/Backend-SpringBoot_+_.NET_10_+_NestJS-6DB33F" alt="Backend"/>
</p>

<p align="center">
<img src="https://img.shields.io/badge/Kotlin-7F52FF?logo=kotlin&logoColor=white" alt="Kotlin"/>
<img src="https://img.shields.io/badge/C%23-239120?logo=csharp&logoColor=white" alt="C#"/>
<img src="https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white" alt="TypeScript"/>
<img src="https://img.shields.io/badge/Node.js-339933?logo=node.js&logoColor=white" alt="Node.js"/>
</p>

<p align="center">
<img src="https://img.shields.io/badge/Database-PostgreSQL-336791?logo=postgresql&logoColor=white" alt="PostgreSQL"/>
<img src="https://img.shields.io/badge/Database-SQL_Server-CC2927?logo=microsoftsqlserver&logoColor=white" alt="SQL Server"/>
<img src="https://img.shields.io/badge/Database-MongoDB-47A248?logo=mongodb&logoColor=white" alt="MongoDB"/>
</p>

<p align="center">
<img src="https://img.shields.io/badge/Security-JWT_+_HMAC_SHA256-red" alt="Security"/>
<img src="https://img.shields.io/badge/Status-Actively_Evolving-blueviolet" alt="Status"/>
</p>

<p align="center">
<img src="https://img.shields.io/github/stars/Naveen2070/The-Hive-Project?style=social" />
<img src="https://img.shields.io/github/forks/Naveen2070/The-Hive-Project?style=social" />
<img src="https://img.shields.io/github/last-commit/Naveen2070/The-Hive-Project" />
<img src="https://img.shields.io/github/license/Naveen2070/The-Hive-Project" />
</p>

---

> **The Hive Project** is my personal engineering sandbox and ambitious playground. It’s a complete entertainment platform built using a **Polyglot Microservices Architecture**. Instead of relying on a single language, "The Hive" utilizes the best tool for each domain—combining the transactional safety of **Spring Boot**, the high-concurrency performance of **.NET 10**, the dynamic consumer interfaces of **React**, the complex data-handling of **Angular**, and the event-driven nature of **Node.js**.

## 📚 Table of Contents

- [🏗️ System Architecture](#-system-architecture)
- [📦 Service Ecosystem](#-service-ecosystem)
- [🚀 Quick Start](#-quick-start-local-development)
- [🗺️ Project Roadmap](#-project-roadmap)
- [💡 Why This Project Exists](#-why-this-project-exists)
- [👨‍💻 Developer Workflow](#-developer-workflow)
- [📜 License](#-license)

## 🏗️ System Architecture

The ecosystem is orchestrated via **Docker Compose**, with an **Nginx API Gateway** handling routing and **RabbitMQ** powering asynchronous, event-driven communication (utilizing the Transactional Outbox Pattern).

- **Gateway:** Nginx (Reverse Proxy)
- **Identity Provider:** Spring Boot 3 / Kotlin (Standalone IAM & S2S Auth)
- **Events Engine:** Spring Boot 3 / Kotlin (Core API)
- **Movies Engine:** .NET 10 / C# (High-Concurrency Seat Locking & Ticketing)
- **Consumer Portal:** React (Vite + TypeScript)
- **Admin Control Center (Planned):** Angular (TypeScript)
- **Notification Engine (Planned):** NestJS (Node.js)
- **Unified Dashboard Service (Planned):** Tech Stack TBD
- **Digital Wallet Service (Planned):** Tech Stack TBD
- **Streaming (Planned):** NestJS (Node.js)

---

## 📦 Service Ecosystem

This repository acts as the **Central Hub**, orchestrating the following independent microservices via Git Submodules:

| Service Domain           | Tech Stack                                      | Repository & Docs                                                    |
| ------------------------ | ----------------------------------------------- | -------------------------------------------------------------------- |
| **Consumer Portal**      | **React**, TypeScript, Tailwind, TanStack Query | **[Hive-Forager-UI](https://github.com/Naveen2070/Hive-Forager-UI)** |
| **Admin Control Center** | **Angular**, TypeScript, RxJS, Material         | _Coming Soon_                                                        |
| **Core API** (Events)    | **Kotlin**, Spring Boot 3, PostgreSQL           | **[Hive-Event](https://github.com/Naveen2070/Hive-Event)**           |
| **Identity Service**     | **Kotlin**, Spring Boot 3, PostgreSQL           | **[Hive-Identity](https://github.com/Naveen2070/Hive-Identity)**     |
| **Movies API**           | **C#**, .NET 10, SQL Server                     | **[Hive-Movie](https://github.com/Naveen2070/Hive-Movie)**           |
| **Notification Engine**  | **Node.js**, NestJS, RabbitMQ                   | _Coming Soon_                                                        |
| **Unified Dashboard**    | **TBD**                                         | _Coming Soon_                                                        |
| **Digital Wallet**       | **TBD**                                         | _Coming Soon_                                                        |
| **Streaming Engine**     | **Node.js**, NestJS, MongoDB                    | _Coming Soon_                                                        |

> **Security Note:** The backend microservices form a Zero-Trust network. They communicate via an industrial-grade **HMAC-SHA256** signature verification process for secure Service-to-Service (S2S) API calls, bypassing the need for JWTs internally.

---

## 🚀 Quick Start (Local Development)

Since this project uses **Git Submodules**, a standard clone will not work. Follow these steps to spin up the entire ecosystem.

### Prerequisites

- **Docker & Docker Compose** (Running)
- **Git**

### 1. Clone with Submodules

```bash
git clone --recurse-submodules https://github.com/Naveen2070/The-Hive-Project.git
cd The-Hive-Project
```

_Already cloned without the flag? Run `git submodule update --init --recursive` to fix it._

### 2. Configure Environment

```ini
# Database (Shared credentials for independent DBs: Postgres & SQL Server)
DB_USERNAME=admin
DB_PASSWORD=SuperSecretPassword123!

# JWT Security
JWT_SECRET=replace_this_with_a_very_long_secure_secret_key
JWT_EXPIRATION_MS=86400000

# Zero-Trust S2S Security
INTERNAL_SHARED_SECRET=replace_this_with_a_secure_s2s_key

# RabbitMQ Broker
RABBITMQ_USERNAME=publisher
RABBITMQ_PASSWORD=pub@2020
```

### 3. Ignite the Hive 🚀

```bash
docker-compose up --build -d
```

Access the services:

- **Frontend UI:** `http://localhost`
- **Core API (Events):** `http://localhost/api/events`
- **Identity API (Auth):** `http://localhost/api/auth`
- **Movies API:** `http://localhost/api/movies`
- **RabbitMQ Dashboard:** `http://localhost:15672` (Login: publisher/pub@2020)

---

## 🗺️ Project Roadmap

The Hive Project isn't just a static codebase; it's a living experiment in system design. I am actively evolving this from a Monolith into a Distributed System using the **Strangler Fig Pattern**. Here is the journey so far and where we are heading next:

### ✅ Phase 1: The Core Foundation (Completed)

- [x] **Event Management:** CRUD operations for Events and Ticket Tiers.
- [x] **Monolithic Auth:** JWT Authentication and RBAC implementation.
- [x] **Frontend:** Responsive React UI with Dashboard and Wallet.
- [x] **Infrastructure:** Nginx Gateway and Docker Compose orchestration.

### ✅ Phase 2: Identity Crisis (Completed)

- [x] **Decomposition:** Extract Authentication & User Management from `Hive-Event`.
- [x] **Standalone IAM:** Build a dedicated Spring Boot Identity Service (`Hive-Identity`).
- [x] **Zero-Trust Networking:** Implement timestamped HMAC-SHA256 signatures for S2S communication.

### ✅ Phase 3: The .NET Expansion (Completed)

- [x] **Microservice Setup:** .NET 10 Web API with SQL Server and Testcontainers.
- [x] **Seat Engine:** High-performance seat locking via Optimistic Concurrency (RowVersion).
- [x] **Reliability:** Implemented Transactional Outbox Pattern to guarantee RabbitMQ delivery.
- [x] **Webhooks:** Idempotent Stripe/Razorpay payment confirmation endpoints.
- [x] **Frontend Integration:** Full React UI integration for movie catalog and seating topologies.

### 🚧 Phase 4: Stabilization & Polish (Current Focus)

- [ ] **System Hardening:** Cleaning up the codebase and ensuring all glued-together microservices communicate flawlessly in the Docker environment.
- [ ] **Cross-Service Consistency:** Refining Nginx routing, standardizing polyglot pagination wrappers, and handling edge-case errors across the network boundary.

### 🔌 Phase 5: Angular Admin Portal (Next)

- [ ] **Admin UI:** Initialize an Angular + RxJS dashboard for super-admins to monitor the Hive ecosystem, approve venues, and manage users.

### 🔔 Phase 6: Notification Engine (Future)

- [ ] **Notification Service:** Spin up a worker (NestJS/Node) to consume RabbitMQ queues and dispatch real-time emails and WebSockets to users.

### 📊 Phase 7: Aggregation Services (Future)

- [ ] **Digital Wallet Service:** A dedicated microservice to aggregate and serve ticket/booking data from both the Event and Movie engines.
- [ ] **Unified Dashboard Service:** A central analytics engine to provide organizers with a holistic view of their sales across all domains.

### 🕸️ Phase 8: Service Mesh & Discovery (Future)

- [ ] **Service Registry & Tracing:** Implement Service Discovery (e.g., Consul or K8s DNS) and Distributed Tracing (Zipkin/Jaeger/OpenTelemetry) for better observability.

### 📺 Phase 9: Streaming (Future)

- [ ] **Streaming Service:** Video delivery wrapper to complete the entertainment ecosystem.

---

## 💡 Why This Project Exists

The Hive Project exists as a playground for experimenting with modern distributed system design.

It explores:

- Polyglot microservices
- Event-driven architecture
- Zero-trust service communication
- Containerized local environments
- Scalable ticketing and booking systems

---

## 👨‍💻 Developer Workflow

Hey there! 👋 Thanks for checking out the code.

I’m a developer who just really loves experimenting with polyglot architectures, messaging queues, and system design. This repository is my personal sandbox, which means things might occasionally break—and that's part of the fun! 🧪

While I am not officially managing this as a massive open-source organization with strict PR reviews, **I absolutely encourage you to fork it, tinker with it, and use it to learn.** **For my future self (and curious minds), here is the "Submodule Dance" to update the code:**

1. **📍 Navigate:** Go into the specific service folder first (e.g., `cd services/hive-movie`).
2. **🌿 Checkout:** Make sure you're on the main branch (`git checkout main`).
3. **💾 Code & Push:** Commit changes _inside_ that folder and push to its specific repository.
4. **🔗 Sync the Hub:** Come back to this root folder, run `git add services/...` and `git commit` to update the submodule pointer.

That's it! You're all set to experiment with the code.

---

## 📜 License

This project is licensed under the **[MIT License](https://github.com/Naveen2070/The-Hive-Project/blob/main/LICENSE)**.
Feel free to fork, experiment, and learn from it.

---

<p align="center">
Built with ❤️, ☕, curiosity, and a lot of debugging.<br>
Occasionally powered by existential debugging and distributed system experiments. 🧪<br><br>
⭐ If you enjoy this project, consider starring the repo.<br>
<b>Architected and maintained with ❤️ by
<a href="https://github.com/Naveen2070">Naveen</a></b>

</p>

---
