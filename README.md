# PARALLAX

**An Open Intelligence Infrastructure**

PARALLAX is an open-source AI infrastructure platform designed to bring together intelligent retrieval, LLM routing, agent orchestration, workflow automation, observability, evaluation, and model optimization in one modular system.

## Vision

Build a production-oriented platform that makes it possible to develop, operate, observe, evaluate, and continuously improve intelligent AI applications.

## Core Capabilities

- **Retrieval:** Document ingestion, BM25, vector search, hybrid retrieval, and reranking.
- **Context Engineering:** Token-aware context assembly, memory, and prompt management.
- **LLM Gateway:** Model routing, semantic caching, fallbacks, and streaming.
- **Agent Runtime:** Deterministic orchestration, tool execution, and multi-agent coordination.
- **MCP Integration:** Model Context Protocol server and client implementations.
- **Reliability:** Guardrails, sandboxed execution, and durable workflows.
- **Observability:** Tracing, metrics, latency, token usage, and error analysis.
- **Evaluation:** Retrieval quality, answer quality, agent trajectories, and regression testing.
- **Model Improvement:** Feedback collection, synthetic data generation, and fine-tuning experiments.

## Architecture

PARALLAX starts as a modular monolith managed through a pnpm workspace.

- `apps/` contains executable applications.
- `packages/` contains reusable TypeScript modules.
- `ml/` contains Python-based machine learning components.
- `infrastructure/` contains local and deployment infrastructure.
- `evaluation/` contains evaluation datasets, tooling, and reports.
- `docs/` contains architecture documentation and engineering decisions.

## Technology Stack

| Area | Technology |
|---|---|
| Backend | Node.js, TypeScript, Fastify |
| Package management | pnpm workspaces |
| Database | PostgreSQL, pgvector |
| Cache | Redis |
| Local inference | Ollama |
| Machine learning | Python, Sentence Transformers |
| Frontend | Next.js |
| Containers | Docker |
| Testing | Vitest, Pytest |
| Observability | OpenTelemetry, Jaeger |

## Development Philosophy

- Prefer simple, explicit architecture over unnecessary abstraction.
- Implement educationally valuable algorithms ourselves.
- Use established libraries for infrastructure and operational concerns.
- Keep modules independently testable.
- Measure performance and quality rather than relying on assumptions.
- Introduce distributed services only when justified by real requirements.

## Project Status

Currently in the foundation phase. The monorepo structure and architectural boundaries are being established.
