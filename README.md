# 🎬 OTT Billing Microservices Platform

![CI](https://github.com/L-O-K-E-S-H-P/CapstoneProject-Backened/actions/workflows/ci.yml/badge.svg)
![Java](https://img.shields.io/badge/Java-17-orange)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.1.4-green)
![Spring Cloud](https://img.shields.io/badge/Spring%20Cloud-2022.0.4-blue)
![Architecture](https://img.shields.io/badge/Architecture-Microservices-purple)

A production-ready **OTT Billing & Invoice Management Platform** built with **Spring Boot 3**, **Spring Cloud**, and **Microservices Architecture**. Handles family account hierarchy, subscription billing, and automated invoice generation.

---

## 🏗️ Microservices Architecture

```
                        Client Request
                              │
                              ▼
                   ┌─────────────────────┐
                   │   API Gateway (8080) │  ← Single entry point
                   │  Spring Cloud Gateway│     Route & Load Balance
                   └──────────┬──────────┘
                              │
              ┌───────────────┼───────────────┐
              │               │               │
              ▼               ▼               ▼
   ┌──────────────┐  ┌───────────────┐  ┌──────────────────┐
   │Billing-System│  │Invoice-Genera-│  │  Discovery       │
   │   (8081)     │  │  tion (8082)  │  │  Client (8761)   │
   │              │  │               │  │  Eureka Server   │
   │ • Family     │  │ • PDF Invoice │  │  Service Registry│
   │   Accounts   │  │ • Billing     │  └──────────────────┘
   │ • Subscript- │  │   History     │
   │   ions       │  │ • Email Notif │
   │ • Plans      │  └───────────────┘
   └──────────────┘
```

---

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Java 17 | Core Language |
| Spring Boot 3.1.4 | Microservice Framework |
| Spring Cloud Gateway | API Gateway & Routing |
| Spring Cloud Netflix Eureka | Service Discovery & Registry |
| Spring Cloud 2022.0.4 | Cloud Native Features |
| Maven Multi-Module | Build Management |
| Lombok | Boilerplate Reduction |

---

## 📦 Microservices Breakdown

### 1. 🔀 API-Gateway-OTT (Port: 8080)
- Single entry point for all client requests
- Routes requests to appropriate microservices
- Load balancing across service instances
- Built with Spring Cloud Gateway

### 2. 💰 Billing-System (Port: 8081)
- Manages family account hierarchy
- Handles OTT subscription plans (Basic/Standard/Premium)
- Tracks billing cycles and payment status
- REST APIs for account and subscription management

### 3. 🧾 Invoice-Generation (Port: 8082)
- Auto-generates invoices for billing cycles
- Maintains billing history per account
- Sends invoice notifications
- Supports multiple invoice formats

### 4. 🔍 Discovery-Client (Port: 8761)
- Eureka Service Registry
- All microservices register here on startup
- Enables dynamic service discovery
- Health monitoring for all services

---

## 🚀 Quick Start

### Prerequisites
```bash
Java 17+
Maven 3.8+
```

### Run All Services

```bash
# 1. Clone the repo
git clone https://github.com/L-O-K-E-S-H-P/CapstoneProject-Backened.git
cd CapstoneProject-Backened

# 2. Start Eureka Discovery Server FIRST
cd Discovery-client
mvn spring-boot:run

# 3. Start Billing System
cd ../Billing-System
mvn spring-boot:run

# 4. Start Invoice Generation
cd ../Invoice-Generation
mvn spring-boot:run

# 5. Start API Gateway LAST
cd ../API-Gateway-OTT
mvn spring-boot:run
```

### Access Points
```
Eureka Dashboard  → http://localhost:8761
API Gateway       → http://localhost:8080
Billing APIs      → http://localhost:8080/billing/**
Invoice APIs      → http://localhost:8080/invoice/**
```

---

## 📌 Key API Endpoints

### Billing Service (via Gateway)
```
GET    /billing/accounts          → Get all family accounts
POST   /billing/accounts          → Create new account
GET    /billing/accounts/{id}     → Get account by ID
POST   /billing/subscriptions     → Subscribe to OTT plan
PUT    /billing/subscriptions/{id}→ Update subscription
```

### Invoice Service (via Gateway)
```
GET    /invoice/generate/{id}     → Generate invoice for account
GET    /invoice/history/{id}      → Get billing history
GET    /invoice/download/{id}     → Download invoice PDF
```

---

## 🎯 Key Features

- ✅ **Microservices Architecture** — 4 independent services
- ✅ **API Gateway** — Single entry point with routing
- ✅ **Service Discovery** — Eureka-based dynamic registration
- ✅ **Maven Multi-Module** — Unified build management
- ✅ **Family Account Hierarchy** — Parent/child account support
- ✅ **Automated Invoice Generation** — Per billing cycle
- ✅ **Spring Cloud Integration** — Production-grade cloud features

---

## 🗂️ Project Structure

```
CapstoneProject-Backened/
├── API-Gateway-OTT/          ← Spring Cloud Gateway
│   ├── src/
│   └── pom.xml
├── Billing-System/           ← Core billing microservice
│   ├── src/
│   └── pom.xml
├── Discovery-client/         ← Eureka Service Registry
│   ├── src/
│   └── pom.xml
├── Invoice-Generation/       ← Invoice microservice
│   ├── src/
│   └── pom.xml
└── pom.xml                   ← Parent Maven multi-module POM
```

---

## 👤 Author

**Lokesh P** — Java Full Stack Developer
AWS Certified Solutions Architect | NPTEL Gold Medalist (Java - IIT Kharagpur)

---

*Built with ❤️ using Spring Boot & Spring Cloud Microservices*
