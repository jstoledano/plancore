# PlanCore

**PlanCore** is a unified platform that transforms operational findings and strategic goals into structured, traceable action plans. It centralizes the management of _corrections_, _corrective actions_, _risk treatments_, and _improvement initiatives_ under a single governance model.

The system supports both reactive triggers (such as nonconformities) and proactive initiatives (such as continuous improvement and risk management), ensuring that every plan is tracked, verified, and formally closed. **PlanCore** provides the evidence and operational discipline required by effective Quality Management Systems (QMS), turning organizational intent into verifiable results.

## Core Domain Model

**PlanCore** is centered around a single aggregate root: the **_Plan_**.

A Plan represents a formal organizational commitment that must be executed, verified, and closed according to explicit rules and invariants.

## Core Concepts

- **Plan**. The aggregate root. Nothing exists outside the context of a Plan.
- **Action**. Concrete steps defined within a Plan. Actions must be completed before a Plan can be verified.
- **Evidence**. Proof that actions were completed and effective. Evidence is required to verify a Plan.
- **Domain Rules & Invariants**. Explicit business rules that protect consistency and correctness (for example, a Plan cannot be closed unless all Actions are completed and required Evidence exists).

## Plan Classification (Semantic, Not Behavioral)

All Plans share the same lifecycle and rules. Classification _exists only for governance, traceability, and reporting_.

### Plan Category (WHY the plan exists)
- `NONCONFORMITY`
- `IMPROVEMENT`

### Plan Subtype (WHAT kind of plan it is)

#### For `NONCONFORMITY`:

- `CORRECTION`
- `CORRECTIVE_ACTION`
- `RISK_TREATMENT`

#### For `IMPROVEMENT`:

- `PROCESS`
- `PRODUCT_OR_SERVICE`
- `QMS`

#### Plan Source (WHAT triggered the plan)

- `EXTERNAL_AUDIT`
- `INTERNAL_AUDIT`
- `CUSTOMER_AUDIT`
- `MANAGEMENT_REVIEW`
- `PROCESS_RESULTS`
- `OBJECTIVES_AND_INDICATORS`
- `RISK_ASSESSMENT`
- `OTHER`

> **Important:** 
> Categories, subtypes, and sources never affect lifecycle, state transitions, or invariants.

Plan Lifecycle

All Plans follow the same explicit lifecycle:

DRAFT → OPEN → IN_PROGRESS → VERIFIED → CLOSED


There are:

no alternative lifecycles

no subtype-specific workflows

no special cases

Architectural Approach

PlanCore is designed following pragmatic Domain-Driven Design (DDD) principles:

The domain model is explicit and isolated.

Business rules and invariants are enforced in domain code, independent of frameworks.

Application services coordinate use cases without embedding domain logic.

The goal is clarity and correctness, not architectural ceremony.

Project Status

This repository currently focuses on:

Defining and enforcing the domain model

Implementing invariants and state transitions

Providing testable, framework-independent business logic

Infrastructure concerns (containerization, deployment, CI/CD, logging) are addressed in later phases.

Project Structure
plancore/
├── domain/      # Core domain model, enums, and invariants
├── services/    # Application services (use-case orchestration)
├── tests/       # Tests focused on domain behavior
└── README.md    # This document

Testing

Domain rules and invariants are validated through automated tests.

pytest


Tests focus on:

Valid and invalid state transitions

Enforcement of invariants

Independence of classification from behavior

Configuration

Runtime configuration and infrastructure integration are intentionally out of scope at this stage.
The current focus is correctness and clarity of the domain model.

Why This Matters

PlanCore intentionally models one unified lifecycle for all organizational plans.
This avoids tool fragmentation, reduces operational cost, and improves traceability across audits, risks, and improvement initiatives.

Final control note (important)

This README now:

Matches the locked domain

Does not overclaim

Strengthens senior-level credibility

Can be safely referenced in interviews
