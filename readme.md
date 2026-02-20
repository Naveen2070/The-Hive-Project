# The Hive Project 🐝

> **A Polyglot Microservices Ecosystem for Events, Movies, and Streaming.**

![Polyglot Architecture](https://img.shields.io/badge/Architecture-Microservices-blue)
![Tech Stack](https://img.shields.io/badge/Tech-Kotlin_%7C_React_%7C_.NET_%7C_Node-orange)
![Status](https://img.shields.io/badge/Status-Pet_Project-purple)

**The Hive Project** is an ambitious engineering initiative to build a complete entertainment platform using a **Polyglot Microservices Architecture**. Instead of relying on a single language, "The Hive" utilizes the best tool for each domain—combining the transactional safety of **Spring Boot**, the performance of **.NET 8**, and the event-driven nature of **Node.js**.

---

## 🏗️ System Architecture

The ecosystem is currently orchestrated via **Docker Compose**, with an **Nginx API Gateway** handling routing and **RabbitMQ** handling asynchronous event-driven communication between microservices.

- **Gateway:** Nginx (Reverse Proxy)
- **Identity Provider:** Spring Boot 3 / Kotlin (Standalone IAM Service)
- **Events Engine:** Spring Boot 3 / Kotlin (Core API)
- **Message Broker:** RabbitMQ (Async Notifications)
- **Frontend:** React (Vite + TypeScript)
- **Movies (Planned):** .NET 8 (C#)
- **Streaming (Planned):** NestJS (Node.js)
- **Service Discovery (Planned):** Evaluating Netflix Eureka, Consul, or Kubernetes DNS.

---

## 📦 Service Ecosystem

This repository acts as the **Central Hub**, orchestrating the following independent microservices:

| Service Domain        | Tech Stack                                      | Repository & Docs                                                    |
| :-------------------- | :---------------------------------------------- | :------------------------------------------------------------------- |
| **User Interface**    | **React**, TypeScript, Tailwind, TanStack Query | [**EventHive-UI**](https://github.com/Naveen2070/EventHive-UI)       |
| **Core API** (Events) | **Kotlin**, Spring Boot 3, PostgreSQL, RabbitMQ | [**Hive-Event**](https://github.com/Naveen2070/EventHive)            |
| **Identity Service**  | **Kotlin**, Spring Boot 3, PostgreSQL, RabbitMQ | [**Hive-Identity**](https://github.com/Naveen2070/Hive-Identity.git) |
| **Movies API**        | **C#**, .NET 8, SQL Server                      | _Coming Soon_                                                        |
| **Streaming Engine**  | **Node.js**, NestJS, MongoDB                    | _Coming Soon_                                                        |

> **Note:** The **Core API** and **Identity Service** are the foundation of the **EventHive** ecosystem. They use an industrial-grade **HMAC-SHA256** signature verification process for secure Machine-to-Machine (S2S) communication.

---

## 🚀 Quick Start (Local Development)

Since this project uses **Git Submodules**, a standard clone will not work. Follow these steps to spin up the entire ecosystem.

### Prerequisites

- **Docker & Docker Compose** (Running)
- **Git**

### 1. Clone with Submodules

You must use the `--recurse-submodules` flag to pull the code for the backend and frontend simultaneously.

```bash
git clone --recurse-submodules [https://github.com/Naveen2070/The-Hive-Project.git](https://github.com/Naveen2070/The-Hive-Project.git)
cd The-Hive-Project
```

_Already cloned without the flag? Run `git submodule update --init --recursive` to fix it._

### 2. Configure Environment

Create a `.env` file in the root directory. This configures the databases, security layers, and message brokers across all containers:

```ini
# Database (Shared credentials for independent DBs)
DB_USERNAME=admin
DB_PASSWORD=password

# JWT Security
JWT_SECRET=replace_this_with_a_very_long_secure_secret_key
JWT_EXPIRATION_MS=86400000

# Zero-Trust S2S Security
INTERNAL_SHARED_SECRET=replace_this_with_a_secure_s2s_key

# RabbitMQ Broker
RABBITMQ_HOST=hive-rabbitmq
RABBITMQ_PORT=5672
RABBITMQ_USERNAME=guest
RABBITMQ_PASSWORD=guest
RABBITMQ_VHOST=/

# Email (Optional for Local - Used by Identity Service)
MAIL_HOST=smtp.mailtrap.io
MAIL_PORT=587
MAIL_USERNAME=guest
MAIL_PASSWORD=guest
```

### 3. Ignite the Hive 🚀

Run the orchestration script:

```bash
docker-compose up --build -d
```

Access the services:

- **Frontend UI:** `http://localhost` (Proxied via Nginx on Port 80)
- **Core API (Events):** `http://localhost/api/events`
- **Identity API (Auth):** `http://localhost/api/auth`
- **RabbitMQ Dashboard:** `http://localhost:15672` (Login: guest/guest)

---

## 🗺️ Project Roadmap

This project is evolving from a Monolith into a Distributed System using the **Strangler Fig Pattern**.

### ✅ Phase 1: The Core Foundation (Completed)

- [x] **Event Management:** CRUD operations for Events and Ticket Tiers.
- [x] **Monolithic Auth:** JWT Authentication and RBAC implementation.
- [x] **Booking Engine:** Concurrency-safe inventory management (Optimistic Locking).
- [x] **Frontend:** Responsive React UI with Dashboard and Wallet.
- [x] **Infrastructure:** Nginx Gateway and Docker Compose orchestration.

### ✅ Phase 2: Identity Crisis (Completed)

- [x] **Decomposition:** Extract Authentication & User Management from `Hive-Event`.
- [x] **Standalone IAM:** Build a dedicated Spring Boot Identity Service (`Hive-Identity`).
- [x] **Zero-Trust Networking:** Implement timestamped HMAC-SHA256 signatures for S2S communication.
- [x] **Event-Driven Upgrades:** Offload email notifications to RabbitMQ.

### 🚧 Phase 3: The .NET Expansion (Current Focus)

- [ ] **Microservice Setup:** Initialize .NET 8 Web API project.
- [ ] **Movie Domain:** Schema design for Movies, Cinemas, and Showtimes.
- [ ] **Seat Selection:** High-performance seat mapping engine using C# structs.
- [ ] **Integration:** Connect .NET service to the Identity ecosystem.

### 🔌 Phase 4: Service Mesh & Discovery

- [ ] **Service Registry:** Implement Service Discovery (e.g., Consul or K8s DNS).
- [ ] **Resilience:** Add Circuit Breakers and Retry policies across services.
- [ ] **Tracing:** Implement Distributed Tracing (Zipkin/Jaeger).

### 📺 Phase 5: Streaming & Real-Time

- [ ] **Streaming Service:** NestJS wrapper for video delivery.
- [ ] **Live Analytics:** Real-time dashboard for organizers using WebSockets.

---

## 👨‍💻 Developer Workflow

Thanks for checking out the code! 👋

This is a personal playground for experimenting (and breaking things!). 🧪
**I am not accepting contributions**, but please feel free to fork the repo and explore the architecture.

**For my future self (and curious minds), here is the "Submodule Dance" to update the code:**

1. **📍 Navigate:** Go into the specific service folder first (e.g., `cd services/core-api`).
2. **🌿 Checkout:** Make sure I'm on the main branch (`git checkout main`).
3. **💾 Code & Push:** Commit changes _inside_ that folder and push to its specific repository.
4. **🔗 Sync the Hub:** Come back to this root folder, run `git add services/...` and `git commit` to update the submodule pointer.

---

**Architected with ❤️ by [Naveen**](https://github.com/Naveen2070)
