# **Architecture Risk Matrix Template**

*(Probability × Impact with example entries)*

```
ARCHITECTURE RISK MATRIX
System / Project:
Date:
Owner / Author:

PROBABILITY SCALE
1 – Rare
2 – Unlikely
3 – Possible
4 – Likely
5 – Almost Certain

IMPACT SCALE
1 – Negligible
2 – Minor
3 – Moderate
4 – Major
5 – Critical

RISK SCORE = Probability × Impact
Low (1–6), Medium (7–14), High (15–25)
```

### Risk Register Table

```
+----+-----------------------------+-------------+---------+---------+-----------+----------------------------------------------+
| ID | Risk Description            | Category    | Prob.   | Impact  | Score     | Mitigation / Controls                        |
+----+-----------------------------+-------------+---------+---------+-----------+----------------------------------------------+
| R1 | New DB may not scale        | Technical   |    4    |    5    |   20 H    | Load testing, sharding roadmap, read replicas|
| R2 | Vendor lock-in              | Strategic   |    3    |    4    |   12 M    | Multi-cloud abstractions, contract clauses   |
| R3 | API gateway outage          | Operational |    3    |    5    |   15 H    | HA cluster, health checks, blue/green deploy |
| R4 | Security breach             | Security    |    2    |    5    |   10 M    | IAM, MFA, pen testing, encryption everywhere |
| R5 | Data quality degradation    | Data        |    4    |    3    |   12 M    | Validation rules, pipelines, observability   |
| R6 | Cost overruns               | Financial   |    3    |    3    |    9 M    | FinOps monitoring, budget threshold alarms   |
| R7 | Skills gap on new tech      | People      |    4    |    2    |    8 L    | Training, mentoring, rollback capability     |
| R8 | Regulatory change           | Compliance  |    2    |    4    |    8 L    | Policy review cadence, DPIAs, legal partner  |
+----+-----------------------------+-------------+---------+---------+-----------+----------------------------------------------+
```

---

# Visual 5×5 Heat Map (text-based)

*(Score = Prob × Impact)*

```
Impact →
 5 |      H     H     H     H     H
 4 |      M     M     H     H     H
 3 |      L     M     M     H     H
 2 |      L     L     M     M     H
 1 |      L     L     L     M     M
          1     2     3     4     5  → Probability
Legend: L = Low, M = Medium, H = High
```

---

# Categories You Can Use (Pick What Fits)

* **Technical** – scalability, latency, failure domains
* **Operational** – deployments, monitoring, maintainability
* **Security** – access control, threat exposure
* **Data** – quality, lineage, privacy, retention
* **Compliance** – GDPR/CCPA/HIPAA/NIST obligations
* **Strategic** – vendor lock-in, architectural direction
* **Financial** – unexpected cloud usage or licensing
* **People** – skills, staffing, onboarding risk

---

# Optional Add-ons

You can add columns if needed:

* **Trigger Condition / Early Warning**
* **Residual Risk after Mitigation**
* **Owner per Risk**
* **Target Resolution Date**

Example:

```
Owner: Data Platform Lead
Early Warning: ETL latency > 2 hr SLA 2 weeks in a row
Residual Risk: 12 → 6
```

--- 
# ️ **Architecture Risks → NIST 800-53 Control Mapping**

*(Using the same example risks from the matrix)*

```
+----+--------------------------+-------------+---------+---------+-------+----------------------------+-----------------------------+
| ID | Risk Description         | Category    | Prob.   | Impact  | Score | Key NIST Controls          | Relevant Control Families   |
+----+--------------------------+-------------+---------+---------+-------+----------------------------+-----------------------------+
| R1 | DB may not scale         | Technical   |   4     |   5     |  20 H | CP-10, CP-2, SC-5          | CP (Contingency), SC (Sys)  |
|    |                          |             |         |         |       | CP-10: Recovery Strategy   |                             |
|    |                          |             |         |         |       | SC-5: System Utilization   |                             |
+----+--------------------------+-------------+---------+---------+-------+----------------------------+-----------------------------+
| R2 | Vendor lock-in           | Strategic   |   3     |   4     |  12 M | SA-2, SA-3, SA-4, PM-30    | SA (Acquisition), PM (Plan) |
|    |                          |             |         |         |       | SA-3: System Dev Lifecycle |                             |
|    |                          |             |         |         |       | SA-4: Acquisition          |                             |
+----+--------------------------+-------------+---------+---------+-------+----------------------------+-----------------------------+
| R3 | API gateway outage       | Operational |   3     |   5     |  15 H | CP-10, CP-8, SC-24, AU-6   | CP, SC, AU                  |
|    |                          |             |         |         |       | CP-8: Telecommunications   |                             |
|    |                          |             |         |         |       | SC-24: Failover            |                             |
+----+--------------------------+-------------+---------+---------+-------+----------------------------+-----------------------------+
| R4 | Security breach          | Security    |   2     |   5     |  10 M | AC-2, AC-3, SC-13, IR-4    | AC, SC, IR                  |
|    |                          |             |         |         |       | AC-2: Account Management   |                             |
|    |                          |             |         |         |       | SC-13: Cryptographic Prot. |                             |
|    |                          |             |         |         |       | IR-4: Incident Handling    |                             |
+----+--------------------------+-------------+---------+---------+-------+----------------------------+-----------------------------+
| R5 | Data quality failures    | Data        |   4     |   3     |  12 M | RA-2, RA-3, SI-7, AU-12    | RA (Risk), SI (System), AU  |
|    |                          |             |         |         |       | RA-3: Risk Assessment      |                             |
|    |                          |             |         |         |       | SI-7: Data Integrity       |                             |
+----+--------------------------+-------------+---------+---------+-------+----------------------------+-----------------------------+
| R6 | Cloud cost blow-up       | Financial   |   3     |   3     |   9 M | PM-3, PM-11, SA-2          | PM (Program), SA (Acq.)     |
|    |                          |             |         |         |       | PM-3: Resource Allocation  |                             |
|    |                          |             |         |         |       | PM-11: Tech Refresh        |                             |
+----+--------------------------+-------------+---------+---------+-------+----------------------------+-----------------------------+
| R7 | Skills gap               | People      |   4     |   2     |   8 L | AT-2, AT-3, PM-2           | AT (Training), PM           |
|    |                          |             |         |         |       | AT-2: Awareness Training   |                             |
|    |                          |             |         |         |       | PM-2: Governance Structure |                             |
+----+--------------------------+-------------+---------+---------+-------+----------------------------+-----------------------------+
| R8 | Regulatory change        | Compliance  |   2     |   4     |   8 L | PA-1, RA-3, PM-1, PL-2     | PA (Privacy), PM, PL, RA    |
|    |                          |             |         |         |       | PA-1: Governance + Privacy |                             |
|    |                          |             |         |         |       | PL-2: System Security Plan |                             |
+----+--------------------------+-------------+---------+---------+-------+----------------------------+-----------------------------+
```

---

# **Control Family Legend**

To support architecture governance at scale:

* **AC – Access Control**
* **AT – Awareness & Training**
* **AU – Audit & Accountability**
* **CP – Contingency Planning**
* **IR – Incident Response**
* **PA – Privacy**
* **PM – Program Management**
* **PL – Planning**
* **RA – Risk Assessment**
* **SA – System & Services Acquisition**
* **SC – System & Communications Protection**
* **SI – System & Information Integrity**

---

# Takeaways

### Architecture risks map directly to NIST via:

**Risk category → Risk controls → Compliance artifacts**

Example:

* If the risk is **Scalability** → CP + SC
* If it is **Security** → AC + SC + IR
* If **Privacy** → PA + RA + PL + PM
* If **Vendor lock-in** → SA + PM

