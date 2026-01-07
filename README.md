# Plan Core

**PlanCore** is the unified platform that transforms findings, risks, and objectives into structured action plans. It centralizes the management of **Correction**, **Corrective Action**, **Risk Treatment**, and **Improvement Plans** in a single hub. The system is triggered by both reactive sources, like nonconformities, and proactive change initiatives. It ensures the tracking, closure, and verification of every commitment, closing the improvement cycle. The solution provides the evidence and operational discipline required for an effective management system. **PlanCore** turns intention into traceable results, tangibly driving continuous improvement.

## Core Domain Concepts

The system is centered around the **Plan** aggregate, which coordinates several core entities:
- **Action**: Concrete tasks or steps defined within a plan.
- **Evidence**: Documentation, files, or data that verify the completion and effectiveness of actions.
- **Rules & Invariants**: Centralized business logic that ensures data consistency and state validity (e.g., a plan cannot be closed without verified evidence for all actions).

Key domain enumerations (`enums.py`) define states, types, and origins, such as:
- **Plan Status**: `DRAFT`, `ACTIVE`, `ON_HOLD`, `CLOSED`
- **Plan Type**: `CORRECTION`, `CORRECTIVE_ACTION`, `RISK_TREATMENT`, `IMPROVEMENT`
- **Origin**: `EXTERNAL_AUDIT`, `INTERNAL_AUDIT`, `CUSTOMER_COMPLAINT`, `RISK_ASSESSMENT`, `MANAGEMENT_REVIEW`

## Tech Stack & Architecture

- **Framework**: FastAPI (with Pydantic for data validation)
- **Database**: PostgreSQL
- **Containerization & Orchestration**: Docker & Docker Compose
- **Operations**: CI/CD pipeline, structured logging, explicit environment-based configuration
- **Architectural Style**: Domain-Driven Design (DDD) applied pragmatically ("without ceremony"), focusing on a rich domain model isolated in the `domain/` layer.

## Getting Started

### Prerequisites
- Docker and Docker Compose
- Git

### Installation & Running

1.  Clone the repository:
    ```bash
    git clone <repository-url>
    cd plancore
    ```

2.  Configure environment:
    ```bash
    cp .env.example .env
    # Edit the .env file with your specific configuration (database credentials, etc.)
    ```

3.  Build and start the services:
    ```bash
    docker-compose up --build
    ```

4.  The API will be available at `http://localhost:8000`.
    - Interactive API documentation (Swagger UI): `http://localhost:8000/docs`
    - Alternative API docs (ReDoc): `http://localhost:8000/redoc`

## Project Structure

```
plancore/
├── domain/ # Core business models, enums, and rules
├── services/ # Domain service layer containing business logic
├── tests/ # Test suites, focusing on domain logic
└── README.md # This file
```


## Testing

Run the test suite to verify domain invariants and business rules:
```bash
# Run tests from the project root
pytest
```

Tests are primarily located in tests/domain/ and focus on the behavior of domain entities and the integrity of business rules.

## Configuration
All runtime configuration is managed through explicit environment variables for security and flexibility. Key configurations include database connection strings, log levels, and external service URLs.
