# Plan of Action & Milestone
1. What a POA&M is (short + practical)
2. A clean reusable **POA&M template**
3. A filled-in **example using the earlier architecture risk**

---

# **What is a POA&M?**

A **Plan of Action & Milestones** documents:

* What risk or gap exists
* What actions will remediate it
* Who owns each action
* When each milestone is due
* When the risk will be considered resolved

📍 **Required in NIST RMF**, FedRAMP, DoD, and generally good architecture hygiene.

---

# **POA&M Template**

*(Copy/Paste into Word, Excel, or Confluence)*

```
POA&M ID:
Related Risk ID:
System / Project:
POA&M Owner:
Date Opened:
Status: Open | In-Progress | Deferred | Resolved | Closed

1. Weakness / Gap Description
   - Summary of the risk or issue found
   - What system, process, or control is impacted

2. Root Cause
   - What caused this weakness?

3. Required Actions (high level)
   1)
   2)
   3)

4. Milestones & Schedule
   +----+----------------------------+--------------+-----------+------------------+
   | #  | Milestone                  | Date Due     | Owner     | Completion Date  |
   +----+----------------------------+--------------+-----------+------------------+
   | 1  |                            |              |           |                  |
   | 2  |                            |              |           |                  |
   | 3  |                            |              |           |                  |
   +----+----------------------------+--------------+-----------+------------------+

5. Resources or Budget Required

6. Dependencies / Constraints

7. Expected Residual Risk
   - Risk score after mitigation (Low/Medium/High)

8. Closure Criteria
   - Acceptance test or metric that proves mitigation is successful
```

---

# **Filled Example POA&M**

*(Tied to Risk R1 — DB scalability failure)*

```
POA&M ID: POAM-001
Related Risk: R1 – Database may not scale with user growth
System: Customer Platform API
Owner: Lead Architect
Date Opened: Jan 08 2026
Status: In-Progress

1. Weakness / Gap
Current PostgreSQL instance has no clear scaling strategy; projected write volume
will exceed capacity under 10x expected user growth.

2. Root Cause
No performance testing plan; architecture decision deferred; no read replica plan.

3. Required Actions
1) Model peak reads/writes and required capacity
2) Establish high-availability plan
3) Perform load test and document thresholds
4) Enable read replicas and auto-scaling policy

4. Milestones
+----+---------------------------------------------+------------+----------------------+
| #  | Milestone                                   | Date Due   | Owner                |
+----+---------------------------------------------+------------+----------------------+
| 1  | Baseline performance benchmark created      | Feb 15     | Data Engineer        |
| 2  | Load test executed with 10x transaction load| Mar 01     | Platform SRE         |
| 3  | Read replica deployment & tuning complete   | Mar 15     | DBA                  |
| 4  | Scaling playbook validated in staging       | Apr 01     | Architecture Council |
+----+---------------------------------------------+------------+----------------------+

5. Resources Required
AWS RDS test cluster; Grafana Metering; SRE/DPA time

6. Dependencies
ADR on DB strategy; Budget approval for extra RDS instance

7. Expected Residual Risk
Medium → Low once replicas + threshold monitoring deployed

8. Closure Criteria
Platform maintains < 80% CPU and < 60% disk I/O under 10x load for 1 hour
```

---

# Where POA&Ms Fit in Risk Governance

**Risk → POA&M → Tracking → Closure**

* Identified in **risk assessment**
* Captured in **POA&M register**
* Tied to **NIST controls**
* Closed when demonstrably mitigated

