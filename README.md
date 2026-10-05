Distributed Currency Exchange & Conversion Microservices
A scalable, distributed microservices platform designed for dynamic currency conversion across multiple exchange pairs, backed by service discovery, central API routing, distributed tracing, and Docker containerization.

Microservices Breakdown
Netflix Eureka Naming Server (Port 8761): Central service discovery registry where all services register and resolve addresses dynamically.

Spring Cloud API Gateway (Port 8765): Single entry point handling routing, path rewriting, and global request filtering.

Currency Exchange Service (Port 8000): Data persistence layer exposing exchange rate pairs with Spring Data JPA.

Currency Conversion Service (Port 8100): Calculation service consuming the exchange service via declarative Spring Cloud OpenFeign clients.

Distributed Tracing with Zipkin (Port 9411): Centralized request tracing across microservice hops using correlated Trace IDs.

Architecture Flow
Client / Browser -> API Gateway (:8765) -> Currency Conversion Service (:8100) -> OpenFeign Call -> Currency Exchange Service (:8000) -> Database

All services register automatically with Eureka Naming Server (:8761)

Requests are traced across all hops using Zipkin (:9411)

How to Run with Docker
Spin up all services and Zipkin with one command:

Bash
docker-compose up --build
Access URLs
Eureka Dashboard: http://localhost:8761

Zipkin Tracing UI: http://localhost:9411

API Gateway: http://localhost:8765