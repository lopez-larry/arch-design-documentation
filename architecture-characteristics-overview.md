# **Architecture Characteristics Matrix**
---

## 1. Single-System Architecture Characteristic Matrix (Template)

Use this when you’re analyzing **one system** (or one slice of your platform) and want to decide which characteristics really matter.

```text
SYSTEM / CONTEXT: ______________________________
DATE: ______________      OWNER: _______________

+----+-------------------+---------------+-------------+-------------------------------------------------+
| ID | Characteristic    | Category      | Criticality | Notes / How It Affects the Architecture        |
+----+-------------------+---------------+-------------+-------------------------------------------------+
| C1 | Availability      | Operational   | H / M / L   | e.g., 99.9% uptime -> clustering, failover     |
| C2 | Performance       | Operational   | H / M / L   | e.g., p95 < 200ms -> caching, async I/O        |
| C3 | Scalability       | Operational   | H / M / L   | e.g., 10x load growth -> horizontal scaling    |
| C4 | Reliability       | Operational   | H / M / L   | e.g., error budgets, retries, idempotency      |
| C5 | Security          | Cross-cutting | H / M / L   | e.g., authZ, encryption, zero-trust boundaries |
| C6 | Observability     | Cross-cutting | H / M / L   | e.g., logs, metrics, traces, health checks     |
| C7 | Modularity        | Structural    | H / M / L   | e.g., service boundaries, low coupling         |
| C8 | Maintainability   | Structural    | H / M / L   | e.g., layering, clear modules, clean APIs      |
| C9 | Deployability     | Operational   | H / M / L   | e.g., blue/green, canary, small blast radius   |
| C10| Testability       | Structural    | H / M / L   | e.g., ports/adapters, seams, contract tests    |
| C11| Elasticity        | Operational   | H / M / L   | e.g., auto-scaling rules, stateless services   |
| C12| Auditability      | Cross-cutting | H / M / L   | e.g., audit logs for sensitive operations      |
+----+-------------------+---------------+-------------+-------------------------------------------------+
```

### How to use (aligned with the book’s guidance)

For each row:

1. **Decide if it’s really an architecture characteristic for *this* system.**

   * Non-domain.
   * Changes structure, not just code details.
   * Critical for success. ([blog.nimblepros.com][1])
2. Set **Criticality = H / M / L**:

   * **H** → drives major architectural decisions (style, patterns, infrastructure).
   * **M** → influences design, but not the primary driver.
   * **L** → acknowledged, but don’t design around it.
3. In **Notes**, write *what that means concretely* (SLO, numbers, or constraints).

---

## 2. Multi-System Architecture Characteristic Matrix (Portfolio View)

This is the “grid” a lot of people build after reading the book: **systems vs. characteristics**, with H/M/L ratings so you can see what drives each architecture.

```text
ARCHITECTURE CHARACTERISTICS PORTFOLIO

Legend: H = High, M = Medium, L = Low, – = Not relevant

+-------------------+------------+------------+------------+------------+
| Characteristic    | System A   | System B   | System C   | System D   |
+-------------------+------------+------------+------------+------------+
| Availability      | H          | M          | H          | L          |
| Performance       | M          | H          | H          | M          |
| Scalability       | H          | H          | M          | L          |
| Reliability       | H          | M          | H          | M          |
| Security          | H          | H          | M          | M          |
| Observability     | H          | M          | H          | L          |
| Modularity        | M          | H          | M          | H          |
| Maintainability   | H          | H          | M          | H          |
| Deployability     | H          | M          | H          | M          |
| Testability       | H          | M          | M          | H          |
| Elasticity        | H          | M          | L          | –          |
| Auditability      | M          | H          | L          | –          |
+-------------------+------------+------------+------------+------------+
```

Use this to:

* Explain **why** different systems in the same org have different architectures.
* Justify choices like microservices vs. modular monolith, event-driven vs. layered, etc.
* Tie back to governance: high-security/high-auditability systems get different controls.

---

## 3. Quick “Recipe” 

1. Start from **business/domain concerns** (SLAs, compliance, user expectations).   

2. Translate them into 5–9 **architecture characteristics** (keep the list short).   

3. Build:

   * A **single-system matrix** (template #1) for each major system.
   * An **org-wide matrix** (template #2) to compare systems.

4. Use those matrices to:

   * Drive **ADR**s and **RFC**s.
   * Choose **architecture patterns** (e.g., microservices, event-driven, layered). 

