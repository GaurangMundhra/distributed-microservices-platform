# Distributed Event-Driven Microservices Platform

A modular backend system designed using microservice architecture where services communicate asynchronously through event streaming.

This project focuses on service isolation, scalability, and reducing synchronous dependencies between components.

---

## Architecture Overview

The system is divided into independent services:

- Auth Service → handles authentication & token validation
- User Service → manages user data & profile operations
- Event Broker → Kafka message streaming between services

Services do not directly depend on each other’s database.  
Communication happens using events to avoid tight coupling.

---

## Why Event-Driven?

Instead of blocking API calls between services:

Request → Event → Consumer → Update

This improves responsiveness and prevents cascading failures when one service becomes slow or unavailable.

---

## Key Design Decisions

**Service Ownership**
Each service manages its own data to maintain boundaries and prevent cross-service data corruption.

**Asynchronous Communication**
Kafka is used so requests don’t wait for other services to complete processing.

**Stateless APIs**
Services validate requests using tokens instead of storing session state locally.

**Failure Handling**
Consumers safely retry event processing without breaking upstream services.

---

## Technology Stack

- Java
- Spring Boot
- Apache Kafka
- REST APIs
- Docker

---

## Repositories

Auth Service  
👉 https://github.com/GaurangMundhra/auth-service

User Service  
👉 https://github.com/GaurangMundhra/user-service

---

## How the System Works

1. Client sends request to Auth Service
2. Auth validates credentials and produces an event
3. User Service consumes the event and updates state
4. Services remain independent but eventually consistent

---

## Learning Focus

This project explores:

- Microservice boundaries
- Eventual consistency
- Asynchronous processing
- Stateless authentication
- Failure isolation
