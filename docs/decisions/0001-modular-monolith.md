# ADR-0001: Adopt a Modular Monolith

- Status: Accepted
- Date: 2026-11-06

## Context

PARALLAX will contain multiple AI infrastructure capabilities, including retrieval, model routing, agent orchestration, caching, evaluation, and observability.

These capabilities have different responsibilities but are closely related during initial development.

Starting with independently deployed microservices would introduce additional operational complexity, network boundaries, deployment pipelines, and debugging overhead before those boundaries are justified.

## Decision

We will implement PARALLAX initially as a modular monolith within a pnpm-managed monorepo.

Each major capability will have a clear package boundary, public interface, and independent tests.

Applications will consume reusable packages through explicit interfaces.

## Consequences

### Positive

- Simpler local development.
- Easier debugging and integration.
- Reduced infrastructure overhead.
- Clear separation of responsibilities.
- Components remain independently testable.
- Future extraction into services remains possible.

### Negative

- Requires discipline to prevent package coupling.
- Components share an application deployment lifecycle initially.
- Independent scaling of individual components is not available by default.

## Future Considerations

A component may be extracted into an independent service when justified by operational isolation, independent scaling, deployment requirements, or resource constraints.

Extraction must preserve its existing public interface wherever practical.
