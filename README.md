# Midas Core - Transaction Processing System

A robust transaction processing system built with Spring Boot that handles financial transactions with incentive calculations. This project is part of the JPMC Advanced Software Engineering Forage program.

## Attribution

This project is based on the JPMC Advanced Software Engineering Forage program. All rights reserved by JPMorgan Chase & Co.

## Features

- Transaction processing with Kafka integration
- Incentive calculation API integration
- User balance management
- RESTful API for balance queries
- Real-time transaction processing
- Data persistence with JPA/Hibernate

## Technical stack

- Java 17
- Spring Boot 3.2.5
- Spring Kafka
- Spring Data JPA
- H2 Database
- Maven
- JUnit 5

## Project Structure

```
src/
├── main/
│   ├── java/
│   │   └── com/jpmc/midascore/
│   │       ├── controller/    # REST controllers
│   │       │   ├── BalanceController.java
│   │       │   ├── IncentiveController.java
│   │       │   └── TransactionController.java
│   │       ├── foundation/    # Core domain models
│   │       │   ├── Balance.java
│   │       │   ├── Incentive.java
│   │       │   ├── Transaction.java
│   │       │   └── TransactionKafkaListener.java
│   │       ├── service/       # Business logic
│   │       │   ├── IncentiveService.java
│   │       │   └── TransactionService.java
│   │       └── MidasCoreApplication.java
│   └── resources/
│       └── application.yml    # Application configuration
└── test/
    └── java/
        └── com/jpmc/midascore/
            └── TaskFiveTests.java  # Integration tests
```

## Getting Started

### Prerequisites

- Java 17 or higher
- Maven 3.8.4 or higher

### Running the Application

1. Clone the repository
2. Build the project:
   ```bash
   ./mvnw clean install
   ```
3. Run the application:
   ```bash
   ./mvnw spring-boot:run
   ```

### Running Tests

```bash
./mvnw test
```

## API Endpoints

### Balance Query
- **GET** `/balance?userId={id}`
- Returns the balance for a given user
- Returns 0.0 if user doesn't exist

### Transaction Processing
- Transactions are processed through Kafka
- Each transaction can include an incentive amount
- Balances are updated in real-time

## Architecture

The system follows a microservices architecture:
1. Main application processes transactions via Kafka
2. Separate Incentive API calculates transaction incentives
3. REST API provides balance queries
4. Data is persisted in H2 database

## Development

### Code Style
- Follows Java code conventions
- Uses Spring Boot best practices
- Includes comprehensive logging
- Proper error handling

### Testing
- Unit tests for core functionality
- Integration tests for API endpoints
- Kafka integration tests
