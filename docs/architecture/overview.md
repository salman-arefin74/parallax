# PARALLAX Architecture Overview

## 1. Architectural Style

PARALLAX begins as a modular monolith inside a pnpm-managed monorepo.

A modular monolith provides clear internal boundaries without requiring independently deployed services or network communication between every component.

Individual components may be extracted into services later if scalability, isolation, deployment, or operational requirements justify it.

## 2. High-Level Structure

### Applications

Location: `apps/`

Applications are executable entry points into the platform.

- `apps/api`: Backend HTTP API and primary integration layer.
- `apps/web`: Web interface and operational dashboard.

Applications coordinate functionality exposed by reusable packages. They should not contain the internal implementation of reusable infrastructure components.

### Reusable Packages

Location: `packages/`

Packages contain independently organized TypeScript capabilities.

Planned components include:

- Core interfaces and shared types
- Document ingestion
- Lexical, vector, and hybrid retrieval
- Context assembly
- Prompt registry
- LLM provider abstraction
- Model routing
- Semantic caching
- Agent runtime
- MCP integration
- Guardrails
- Workflow engine
- Observability

Packages should expose explicit public interfaces and avoid depending on application-specific implementation details.

### Machine Learning Components

Location: `ml/`

Python is used where its machine learning ecosystem provides a practical advantage.

The initial component will be a reranking service using Sentence Transformers.

ML components communicate with the TypeScript platform through explicit service interfaces, initially HTTP where appropriate.

### Infrastructure

Location: `infrastructure/`

Contains local development and deployment infrastructure, including database, cache, model-serving, and observability configuration.

Infrastructure configuration must remain separate from application business logic.

### Evaluation

Location: `evaluation/`

Contains evaluation datasets, metrics, execution tooling, and benchmark reports.

Evaluation should measure component quality and detect regressions as the platform evolves.

### Documentation

Location: `docs/`

Contains system architecture, implementation notes, and Architecture Decision Records.

## 3. Dependency Rules

1. Applications may depend on reusable packages.
2. Reusable packages must not depend on applications.
3. Core must remain independent of application-specific and infrastructure-specific modules.
4. Packages should depend only on explicitly required public interfaces.
5. Circular package dependencies are prohibited.
6. Python components must communicate with TypeScript through explicit interfaces rather than direct runtime coupling.
7. Infrastructure configuration must not become a dependency of domain logic.

## 4. Communication Strategy

Inside the initial modular monolith, TypeScript packages communicate through direct function calls and typed interfaces.

External infrastructure is accessed through explicit adapters:

- PostgreSQL through database adapters.
- Redis through cache adapters.
- Local LLMs through provider interfaces.
- Python ML components through service interfaces.

Network boundaries are introduced only where technically justified.

## 5. Quality Attributes

PARALLAX prioritizes:

- Modularity and maintainability
- Testability
- Security and isolation
- Observability
- Performance and predictable resource usage
- Reproducible development environments
- Measurable AI quality

## 6. Evolution

The architecture will evolve incrementally.

Each major capability will be introduced with its own interfaces, implementation, tests, and documentation.

The initial priority is correctness and clarity, followed by performance optimization and production hardening.
