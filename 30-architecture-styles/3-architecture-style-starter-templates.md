# Architecture Templates

## 1) Layered Architecture

**Folder Structure**

```
project/
  src/
    presentation/
    application/
    domain/
    infrastructure/
  tests/
  docs/
    architecture.md
    decisions.md
```

**README Purpose**
A traditional layered system separating UI, application logic, domain logic, and infrastructure concerns.
Single deployable unit.
Ideal for well-understood business systems with modest complexity.

---

## 2) Dataflow / Pipeline Architecture

**Folder Structure**

```
pipeline/
  stages/
    ingest/
    validate/
    transform/
    aggregate/
    publish/
  shared/
  tests/
docs/
  architecture.md
  pipeline-steps.md
```

**README Purpose**
A linear processing model where data flows through staged transformations.
Each step performs a single responsibility.
Useful for ETL, batch analytics, or streaming flows.

---

## 3) Microkernel Architecture

**Folder Structure**

```
core/
  api/
  service/
plugins/
  plugin-a/
  plugin-b/
tests/
docs/
  plugin-contracts.md
```

**README Purpose**
Core system provides base capabilities while plugins extend behavior.
Good for tools, rule engines, and systems needing controlled extensibility.

---

## 4) Service-Based Architecture

**Folder Structure**

```
services/
  customer/
  billing/
  catalog/
shared/
  data/
  messaging/
ui/
tests/
docs/
  service-boundaries.md
```

**README Purpose**
Multiple deployable services grouped by business capability but still sharing infrastructure or a database.
Good transition step between monolith and microservices.

---

## 5) Event-Driven Architecture

**Folder Structure**

```
producers/
  order-service/
  customer-service/
consumers/
  analytics/
  reporting/
events/
  schemas/
shared/
  messaging/
docs/
  event-contracts.md
```

**README Purpose**
Services communicate through events rather than direct calls.
Highly decoupled system behavior emerges from published messages and subscribed processors.

---

## 6) Space-Based / In-Memory Grid

**Folder Structure**

```
processing-units/
  service-a/
  service-b/
data-grid/
  replication/
  partitioning/
clients/
tests/
docs/
  scaling-strategy.md
```

**README Purpose**
State and processing are distributed across a grid of nodes.
Designed for high throughput and elastic scaling with minimal database contention.

---

## 7) Orchestrated SOA

**Folder Structure**

```
orchestrator/
  workflows/
services/
  service-a/
  service-b/
shared/
  schema/
docs/
  workflow-definitions.md
```

**README Purpose**
Central workflow component coordinates distributed services to complete business processes.
Suited for enterprises integrating many legacy systems.

---

## 8) Microservices Architecture

**Folder Structure**

```
services/
  auth/
  inventory/
  orders/
  payments/
gateway/
  api-gateway/
observability/
  logging/
  tracing/
tests/
docs/
  domain-map.md
```

**README Purpose**
Independent, domain-aligned services owned, deployed, and scaled separately.
Requires strong automation, DevOps maturity, and clear domain boundaries.

---

## Optional Shared Conventions Across All Templates

Add these to every repo or a root template:

```
docs/
  adr/                 Architecture Decision Records
  readme-context.md
  tradeoffs.md
scripts/
  run-local.sh
  deploy.sh
infra/
  docker-compose.yml or terraform/
```
