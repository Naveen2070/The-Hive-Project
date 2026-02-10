# The Hive Project 🐝

> **A Polyglot Microservices Ecosystem for Events, Movies, and Streaming.**

![Polyglot Architecture](https://img.shields.io/badge/Architecture-Microservices-blue)
![Tech Stack](https://img.shields.io/badge/Tech-Kotlin_%7C_React_%7C_.NET_%7C_Node-orange)
![Status](https://img.shields.io/badge/Status-Pet_Project-purple)

**The Hive Project** is an ambitious engineering initiative to build a complete entertainment platform using a **Polyglot Microservices Architecture**. Instead of relying on a single language, "The Hive" utilizes the best tool for each domain—combining the transactional safety of **Spring Boot**, the performance of **.NET 8**, and the event-driven nature of **Node.js**.

---

## 🏗️ System Architecture

The ecosystem is currently orchestrated via **Docker Compose**, with an **Nginx API Gateway** handling routing. As the system scales, a dedicated Service Registry will be introduced to handle dynamic service discovery.

- **Gateway:** Nginx (Reverse Proxy)
- **Identity Provider:** Spring Boot 3 (Standalone IAM Service)
- **Events Engine:** Spring Boot 3 (Kotlin)
- **Frontend:** React (Vite + TypeScript)
- **Movies (Planned):** .NET 8 (C#)
- **Streaming (Planned):** NestJS (Node.js)

* **Service Discovery (Planned):** Evaluating Netflix Eureka, Consul, or Kubernetes DNS.

---

## 📦 Service Ecosystem

This repository acts as the **Central Hub**, orchestrating the following independent microservices:

| Service Domain        | Tech Stack                                      | Repository & Docs                                              |
| :-------------------- | :---------------------------------------------- | :------------------------------------------------------------- |
| **User Interface**    | **React**, TypeScript, Tailwind, TanStack Query | [**EventHive-UI**](https://github.com/Naveen2070/EventHive-UI) |
| **Core API** (Events) | **Kotlin**, Spring Boot 3, PostgreSQL           | [**EventHive-Core**](https://github.com/Naveen2070/EventHive)  |
| **Identity Service**  | **Kotlin**, Spring Boot 3, Redis                | _Coming Soon_                                                  |
| **Movies API**        | **C#**, .NET 8, SQL Server                      | _Coming Soon_                                                  |
| **Streaming Engine**  | **Node.js**, NestJS, MongoDB                    | _Coming Soon_                                                  |

> **Note:** The **Core API** and **Identity Service** are the core components of the **EventHive** ecosystem. They serve as the foundation for the entire platform.

---

## 🚀 Quick Start (Local Development)

Since this project uses **Git Submodules**, a standard clone will not work. Follow these steps to spin up the entire ecosystem.

### Prerequisites

- **Docker Desktop** (Running)
- **Git**

### 1. Clone with Submodules

You must use the `--recurse-submodules` flag to pull the code for the backend and frontend.

```bash
git clone --recurse-submodules https://github.com/Naveen2070/The-Hive-Project.git
cd The-Hive-Project
```

_Already cloned without the flag? Run `git submodule update --init --recursive` to fix it._

### 2. Configure Environment

Create a `.env` file in the root directory:

```ini
# Database
DB_USERNAME=admin
DB_PASSWORD=password

# Security
JWT_SECRET=replace_this_with_a_very_long_secure_secret_key
JWT_EXPIRATION_MS=86400000

# Email (Optional for Local)
MAIL_HOST=smtp.mailtrap.io
MAIL_PORT=587
MAIL_USERNAME=guest
MAIL_PASSWORD=guest
```

### 3. Ignite the Hive 🚀

Run the orchestration script:

```bash
docker-compose up --build
```

Access the services:

- **Frontend UI:** [http://localhost](https://www.google.com/search?q=http://localhost) (Proxied via Port 80)
- **Core API:** [http://localhost/api](https://www.google.com/search?q=http://localhost/api)
- **API Docs (Swagger):** [http://localhost/api/swagger-ui.html](https://www.google.com/search?q=http://localhost/api/swagger-ui.html)

---

## 🗺️ Project Roadmap

This project is evolving from a Monolith into a Distributed System using the **Strangler Fig Pattern**.

### ✅ Phase 1: The Core Foundation (Completed)

- [x] **Event Management:** CRUD operations for Events and Ticket Tiers.
- [x] **Monolithic Auth:** JWT Authentication and RBAC implementation.
- [x] **Booking Engine:** Concurrency-safe inventory management (Optimistic Locking).
- [x] **Frontend:** Responsive React UI with Dashboard and Wallet.
- [x] **Infrastructure:** Nginx Gateway and Docker Compose orchestration.

### 🚧 Phase 2: Identity Crisis (Current Focus)

- [ ] **Decomposition:** Extract Authentication & User Management from `EventHive-Core`.
- [ ] **Standalone IAM:** Build a dedicated Spring Boot Identity Service.
- [ ] **Gateway Auth:** Implement centralized JWT validation at the Gateway level.
- [ ] **Session Sync:** Ensure seamless session sharing across potential future apps.

### 🔮 Phase 3: The .NET Expansion

- [ ] **Microservice Setup:** Initialize .NET 8 Web API project.
- [ ] **Movie Domain:** Schema design for Movies, Cinemas, and Showtimes.
- [ ] **Seat Selection:** High-performance seat mapping engine using C# structs.
- [ ] **Integration:** Connect .NET service to the ecosystem.

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

1.  **📍 Navigate:** Go into the specific service folder first (e.g., `cd services/core-api`).
2.  **🌿 Checkout:** Make sure I'm on the main branch (`git checkout main`).
3.  **💾 Code & Push:** Commit changes _inside_ that folder and push to its specific repository.
4.  **🔗 Sync the Hub:** Come back to this root folder, run `git add services/...` and `git commit` to update the submodule pointer.

---

**Architected with ❤️ by [Naveen](https://github.com/Naveen2070)**
