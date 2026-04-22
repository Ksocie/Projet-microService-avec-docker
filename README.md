 # 🏗️ Microservices Architecture with Docker

> A production-ready microservices infrastructure built with Java Spring Boot, Docker Compose, PostgreSQL, MongoDB, and Spring Cloud Config Server.

![Java](https://img.shields.io/badge/Java-17-orange?style=flat-square&logo=java)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.x-brightgreen?style=flat-square&logo=springboot)
![Docker](https://img.shields.io/badge/Docker-Compose-blue?style=flat-square&logo=docker)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15-blue?style=flat-square&logo=postgresql)
![MongoDB](https://img.shields.io/badge/MongoDB-6.0-green?style=flat-square&logo=mongodb)

---

## 📐 Architecture Overview

```
┌─────────────────────────────────────────────────────────┐
│                    Docker Network                        │
│                                                         │
│  ┌─────────────────┐      ┌──────────────────────────┐  │
│  │  Config Server  │◄─────│     Microservices        │  │
│  │  (Spring Cloud) │      │  (Service A, B, C...)    │  │
│  └─────────────────┘      └──────────┬───────────────┘  │
│                                      │                  │
│              ┌───────────────────────┼──────────┐       │
│              ▼                       ▼          ▼       │
│       ┌────────────┐        ┌──────────────┐  ┌──────┐  │
│       │ PostgreSQL │        │   MongoDB    │  │ Mail │  │
│       │ + pgAdmin  │        │ + Mongo Exp. │  │ Dev  │  │
│       └────────────┘        └──────────────┘  └──────┘  │
└─────────────────────────────────────────────────────────┘
```

---

## 🧩 Services

| Service | Role | Port | UI |
|---|---|---|---|
| **Config Server** | Centralized configuration management (Spring Cloud) | `8888` | - |
| **PostgreSQL** | Relational database for structured data | `5432` | pgAdmin → `5050` |
| **MongoDB** | NoSQL database for flexible/document data | `27017` | Mongo Express → `8081` |
| **MailDev** | Local SMTP server for email testing in dev | `1025` | `1080` |

---

## 🛠️ Tech Stack

- **Java 17** + **Spring Boot 3.x**
- **Spring Cloud Config** — centralized config server for all microservices
- **Docker & Docker Compose** — containerized, reproducible environments
- **PostgreSQL** — relational data storage
- **MongoDB** — document-oriented storage
- **MailDev** — development SMTP server (no real emails sent)

---

## 🚀 Getting Started

### Prerequisites

- [Docker](https://docs.docker.com/get-docker/) >= 24.x
- [Docker Compose](https://docs.docker.com/compose/) >= 2.x
- Java 17+

### Run the stack

```bash
# Clone the repository
git clone https://github.com/Ksocie/Projet-microService-avec-docker.git
cd Projet-microService-avec-docker

# Start all services
docker-compose up -d

# Check running containers
docker ps
```

### Access the services

| Interface | URL | Credentials |
|---|---|---|
| pgAdmin | http://localhost:5050 | See `docker-compose.yml` |
| Mongo Express | http://localhost:8081 | See `docker-compose.yml` |
| MailDev UI | http://localhost:1080 | No auth required |
| Config Server | http://localhost:8888 | No auth required |

### Stop the stack

```bash
docker-compose down

# Stop and remove volumes (full reset)
docker-compose down -v
```

---

## ⚙️ Configuration

All configurations are managed centrally by the **Spring Cloud Config Server**.

Each microservice fetches its configuration from the config server at startup, which allows:
- Environment-specific configs (`dev`, `staging`, `prod`)
- No hardcoded credentials in the codebase
- Hot reload of configs without restarting services

> ⚠️ **Security Note:** Default credentials are defined in `docker-compose.yml` for local development only. In production, always use environment variables or a secrets manager (AWS Secrets Manager, HashiCorp Vault, etc.)

---

## 📁 Project Structure

```
.
├── services/
│   └── config-server/          # Spring Cloud Config Server
│       ├── src/
│       └── pom.xml
├── docker-compose.yml          # Full infrastructure definition
├── .gitignore
└── README.md
```

---

## 🔭 Roadmap

- [ ] Add API Gateway (Spring Cloud Gateway)
- [ ] Add service discovery (Eureka / Consul)
- [ ] Add distributed tracing (Zipkin)
- [ ] Add CI/CD pipeline with GitHub Actions
- [ ] Add Kubernetes manifests (Helm charts)

---

## 🤝 Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

---
