# Standard Roles Used
(Consistent Across All Styles)

| Role                             | Meaning                                        |
| -------------------------------- | ---------------------------------------------- |
| **Sponsor / Product Owner (PO)** | Business goals, funding, acceptance            |
| **Architect**                    | Architecture decisions, tradeoffs, constraints |
| **Tech Lead**                    | Implementation leadership, code quality        |
| **Development Team (Dev)**       | Build and integrate components                 |
| **Ops / Platform**               | Deployment, runtime, reliability               |
| **QA / Validation**              | Testing, verification, quality gates           |

---

# 1) Layered Architecture — RACI

| Activity                    | PO    | Architect | Tech Lead | Dev   | Ops     | QA    |
| --------------------------- | ----- | --------- | --------- | ----- | ------- | ----- |
| Requirements & Scope        | **A** | C         | I         | I     | I       | I     |
| Layered Architecture Design | I     | **R/A**   | C         | I     | I       | I     |
| Core Implementation         | I     | C         | **R**     | **R** | I       | I     |
| Integration                 | I     | C         | **R**     | **R** | I       | C     |
| Testing                     | I     | I         | C         | R     | I       | **A** |
| Deployment                  | I     | I         | C         | I     | **R/A** | C     |

**Pattern:** Architect-led design, Dev-heavy execution, Ops minimal.

---

# 2) Dataflow (Pipeline) Architecture — RACI

| Activity               | PO | Architect | Tech Lead | Dev   | Ops     | QA    |
| ---------------------- | -- | --------- | --------- | ----- | ------- | ----- |
| Pipeline Definition    | A  | **R**     | C         | I     | I       | I     |
| Stage Design           | I  | **R**     | C         | I     | I       | C     |
| Stage Implementation   | I  | C         | **R**     | **R** | I       | I     |
| Pipeline Orchestration | I  | C         | **R**     | R     | I       | I     |
| End-to-End Testing     | I  | I         | C         | R     | I       | **A** |
| Deployment             | I  | I         | C         | I     | **R/A** | C     |

**Pattern:** Tech Lead gains importance due to sequencing and flow control.

---

# 3) Microkernel Architecture — RACI

| Activity                   | PO | Architect | Tech Lead | Dev   | Ops     | QA    |
| -------------------------- | -- | --------- | --------- | ----- | ------- | ----- |
| Core System Design         | I  | **R/A**   | C         | I     | I       | I     |
| Plugin Contract Definition | I  | **R**     | C         | I     | I       | C     |
| Core Implementation        | I  | C         | **R**     | R     | I       | I     |
| Plugin Development         | I  | I         | C         | **R** | I       | C     |
| Compatibility Testing      | I  | I         | C         | R     | I       | **A** |
| Deployment                 | I  | I         | C         | I     | **R/A** | C     |

**Pattern:** Architect remains dominant to protect kernel stability.

---

# 4) Service-Based Architecture — RACI

| Activity                    | PO | Architect | Tech Lead | Dev   | Ops     | QA    |
| --------------------------- | -- | --------- | --------- | ----- | ------- | ----- |
| Domain Decomposition        | A  | **R**     | C         | I     | I       | I     |
| Service Contract Design     | I  | **R**     | C         | I     | I       | C     |
| Service Implementation      | I  | C         | **R**     | **R** | I       | I     |
| Inter-Service Communication | I  | C         | **R**     | R     | I       | I     |
| Contract Testing            | I  | I         | C         | R     | I       | **A** |
| Deployment                  | I  | I         | C         | I     | **R/A** | C     |

**Pattern:** Balanced responsibility; Ops influence increases.

---

# 5) Event-Driven Architecture — RACI

| Activity                | PO | Architect | Tech Lead | Dev   | Ops     | QA    |
| ----------------------- | -- | --------- | --------- | ----- | ------- | ----- |
| Event Model Design      | I  | **R/A**   | C         | I     | I       | I     |
| Broker Infrastructure   | I  | C         | C         | I     | **R/A** | I     |
| Producer Development    | I  | I         | **R**     | **R** | I       | I     |
| Consumer Development    | I  | I         | **R**     | **R** | I       | I     |
| Observability & Tracing | I  | I         | C         | I     | **R**   | **A** |
| Deployment              | I  | I         | C         | I     | **R/A** | C     |

**Pattern:** Ops becomes architecturally significant; QA weakens due to async complexity.

---

# 6) Space-Based Architecture — RACI

| Activity                  | PO | Architect | Tech Lead | Dev   | Ops     | QA      |
| ------------------------- | -- | --------- | --------- | ----- | ------- | ------- |
| Data Grid Design          | I  | **R/A**   | C         | I     | C       | I       |
| Grid Infrastructure Setup | I  | C         | C         | I     | **R/A** | I       |
| Processing Components     | I  | I         | **R**     | **R** | I       | I       |
| State Management          | I  | C         | **R**     | R     | I       | I       |
| Load & Failure Testing    | I  | I         | C         | I     | C       | **R/A** |
| Deployment                | I  | I         | C         | I     | **R/A** | C       |

**Pattern:** Ops and Architect jointly dominate early phases.

---

# 7) Orchestrated SOA — RACI

| Activity               | PO    | Architect | Tech Lead | Dev   | Ops     | QA      |
| ---------------------- | ----- | --------- | --------- | ----- | ------- | ------- |
| Process Definition     | **A** | **R**     | C         | I     | I       | I       |
| Orchestrator Design    | I     | **R/A**   | C         | I     | I       | I       |
| Service Implementation | I     | I         | **R**     | **R** | I       | I       |
| Integration Logic      | I     | C         | **R**     | R     | I       | I       |
| Workflow Testing       | I     | I         | C         | I     | I       | **R/A** |
| Deployment             | I     | I         | C         | I     | **R/A** | C       |

**Pattern:** Central control increases architectural rigidity.

---

# 8) Microservices Architecture — RACI

| Activity               | PO | Architect | Tech Lead | Dev   | Ops     | QA |
| ---------------------- | -- | --------- | --------- | ----- | ------- | -- |
| Domain Decomposition   | A  | **R**     | C         | I     | I       | I  |
| Service Foundations    | I  | C         | C         | I     | **R/A** | I  |
| Service Implementation | I  | I         | **R**     | **R** | I       | I  |
| Platform Capabilities  | I  | I         | C         | I     | **R/A** | I  |
| Resilience Engineering | I  | C         | **R**     | I     | **R**   | I  |
| Deployment & Scaling   | I  | I         | C         | I     | **R/A** | C  |

**Pattern:** Ops and Tech Lead become first-class architects.
