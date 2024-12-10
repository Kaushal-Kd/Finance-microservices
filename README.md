# Distributed Banking System

This project demonstrates a microservices architecture implemented using .NET 8.

Below is the visual representation of the overall architecture:

![Sample Bank - Dotnet Microservice Architecture](https://imesh.ai/blog/wp-content/uploads/2023/05/Traffic-flow-of-an-incoming-gRPC-request-through-the-API-gateway.png)

## Components Overview

### Customer Microservice

- **ASP.NET Core Web API** and **gRPC Server** applications
- Adheres to **REST API** principles and performs basic **CRUD** operations
- Follows **DDD**, **CQRS**, and **Clean Architecture** methodologies using industry best practices
- Implements high-performance inter-service communication via **gRPC**
- **CQRS** architecture with **MediatR**, **FluentValidation**, and **AutoMapper**
- Connects to a **PostgreSQL** database, containerized for portability
- Uses **Entity Framework Core ORM** with automatic database migration to SQL Server at runtime
- Includes **Swagger/OpenAPI** for API documentation

### Account Microservice

- **ASP.NET Core Web API** application
- Follows **REST API** standards with **CRUD** operations
- Implements **DDD**, **CQRS**, and **Clean Architecture** based on best practices
- Publishes transaction data via **MassTransit** and **RabbitMQ**
- Consumes **gRPC Customer Service** for communication between microservices
- Implements **CQRS** with **MediatR**, **FluentValidation**, and **AutoMapper**
- Utilizes a **PostgreSQL** database with containerization
- Automatic SQL Server migration via **Entity Framework Core ORM**
- **Swagger/OpenAPI** documentation integration

### Transaction Microservice

- **ASP.NET Core Web API** application
- Provides **REST API** endpoints with **CRUD** functionalities
- Uses **Repository Pattern** for clean data access
- Consumes transaction data through **MassTransit** and **RabbitMQ**
- Connects to **MongoDB** for data storage, containerized for ease of deployment
- Includes **Swagger/OpenAPI** for API documentation

### API Gateway (Ocelot)

- Implements an **API Gateway** using **Ocelot**
- Demonstrates routing across various microservices/containers via the API Gateway
- Supports multiple **API Gateway** and **BFF** container types

### Cross-Cutting Microservice Features

- **Centralized Distributed Logging** using the **Elastic Stack (ELK)**: Elasticsearch, Logstash, Kibana, and **Serilog**
- Implements **Health Checks** in backend ASP.NET microservices for service monitoring

### Resilience Features for Microservices

- Enhances service resilience using **IHttpClientFactory** to make robust HTTP requests
- Implements **Retry** and **Circuit Breaker** patterns with exponential backoff, using **IHttpClientFactory** and **Polly**

### Supporting Containers

- **Portainer** provides an intuitive web-based UI for managing Docker containers
- **pgAdmin** offers a comprehensive open-source platform for managing and developing PostgreSQL databases

### Docker Compose Setup

- Microservices and databases are containerized for easy deployment
- Environment variables are configured to enable flexible runtime configurations
