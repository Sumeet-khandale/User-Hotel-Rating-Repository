🏨 User Hotel Rating Microservices

A microservices-based Spring Boot application that manages Users, Hotels, and Ratings with full support for Eureka Service Discovery, API Gateway, and Centralized Configuration.
This project demonstrates inter-service communication, API orchestration, and modular design for scalable distributed systems.

---

Architecture Overview

Client
↓
API Gateway → User Service
↓
Service Registry (Eureka) → Hotel Service
↓
Config Server → Rating Service

Each service is independent, runs on its own port, and communicates via REST using Spring Cloud.

---

Features

* Microservices architecture
* Centralized configuration using Spring Cloud Config
* Service discovery using Eureka
* API Gateway routing
* RESTful CRUD APIs
* Inter-service communication using RestTemplate or WebClient
* Modular and scalable design
* MySQL or H2 database support
* Easy deployment using Docker

---

Microservices Included

User Service - Manages user data such as create, update, and fetch users.
Hotel Service - Handles hotel information and listings.
Rating Service - Manages user ratings for hotels.
API Gateway - Central entry point that routes requests to the correct service.
Service Registry - Eureka server for dynamic service discovery.
Config Server - Centralized configuration management for all microservices.

---

Tech Stack

Backend - Java 17, Spring Boot
Cloud - Spring Cloud (Eureka, Gateway, Config)
Database - MySQL or H2
Build Tool - Maven
Testing - JUnit, Mockito
Communication - REST APIs
Other Tools - Lombok, ModelMapper, Actuator

---

Prerequisites

* Java 17 or higher
* Maven 3.8 or higher
* MySQL database (or H2 for testing)
* Docker (optional)

---

How to Run the Project

1. Clone the Repository
   git clone [https://github.com/Sumeet-khandale/User-Hotel-Rating-Repository.git](https://github.com/Sumeet-khandale/User-Hotel-Rating-Repository.git)
   cd User-Hotel-Rating-Repository

2. Start Services in the following order

   cd ServiceRegistry
   mvn spring-boot:run

   cd ../ConfigServer
   mvn spring-boot:run

   cd ../UserService
   mvn spring-boot:run

   cd ../HotelService
   mvn spring-boot:run

   cd ../RatingService
   mvn spring-boot:run

   cd ../ApiGateway
   mvn spring-boot:run

3. Access Services

Eureka Dashboard - [http://localhost:8761](http://localhost:8761)
Config Server - [http://localhost:8888](http://localhost:8888)
API Gateway - [http://localhost:8084](http://localhost:8084)
User Service - [http://localhost:8081](http://localhost:8081)
Hotel Service - [http://localhost:8082](http://localhost:8082)
Rating Service - [http://localhost:8083](http://localhost:8083)

---

Example API Endpoints

User Service
POST /users
GET /users
GET /users/{userId}

Hotel Service
POST /hotels
GET /hotels
GET /hotels/{hotelId}

Rating Service
POST /ratings
GET /ratings
GET /ratings/users/{userId}
GET /ratings/hotels/{hotelId}

You can test all APIs using Postman or cURL.

---

Project Structure

User-Hotel-Rating-Repository/
│
├── ApiGateway/
├── ConfigServer/
├── ServiceRegistry/
├── UserService/
├── HotelService/
├── RatingService/
└── README.md

---

API Gateway Routing

/users/** → User Service
/hotels/** → Hotel Service
/ratings/** → Rating Service

---

Key Learnings

* How to build and deploy microservices independently
* Using Eureka for dynamic service registration
* Setting up a Config Server for environment management
* Exposing multiple APIs under one gateway
* Handling inter-service communication using RestTemplate or WebClient

---

Contributing

1. Fork the repository
2. Create your branch
   git checkout -b feature/your-feature
3. Commit and push
   git commit -m "Added new feature"
   git push origin feature/your-feature
4. Create a Pull Request

---

License

This project is open-source and available under the MIT License.

---

Author

Sumeet Khandale
GitHub: [https://github.com/Sumeet-khandale](https://github.com/Sumeet-khandale)
