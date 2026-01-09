# Architecture Characteristics Rating Matrices

Rating Scale:
- weak support        = ★ 
- moderate            = ★★  
- strong              = ★★★ 
- excellent           = ★★★★  
- dominant strength   = ★★★★★ 

Footprint Position Bar Normalization: 
- Narrow [==========================] Broad
  - min = 15
  - max = 40
---
# Most Common Architectural Styles

## 1) Layered Architecture
```
Partitioning approach: Technical
Typical deployable units: 1

Operational Independence: 1
Elastic Capacity:         1
Adaptability Over Time:   1
Failure Containment:      1
Structural Modularity:    1
Total Lifecycle Cost:     5
Execution Efficiency:     2
Execution Reliability:    3
Growth Potential:         1
Conceptual Clarity:       5
Validation Support:       2
```

Summary Metrics
Total Score: 23
Footprint Category: Narrow Scope
Expertise Required: Low

Footprint Position
Narrow [====◆=====================] Broad

---

## 2) Dataflow (Pipeline) Architecture

```
Partitioning approach: Technical
Typical deployable units: 1

Operational Independence: 2
Elastic Capacity:         1
Adaptability Over Time:   3
Failure Containment:      1
Structural Modularity:    3
Total Lifecycle Cost:     5
Execution Efficiency:     2
Execution Reliability:    3
Growth Potential:         2
Conceptual Clarity:       4
Validation Support:       3
```

Summary Metrics
Total Score: 30
Footprint Category: Balanced Scope
Expertise Required: Medium

Footprint Position
Narrow [========◆=================] Broad

---

## 3) Microkernel Architecture

```
Partitioning approach: Mixed (Core + Plugins)
Typical deployable units: 1

Operational Independence: 3
Elastic Capacity:         1
Adaptability Over Time:   3
Failure Containment:      1
Structural Modularity:    3
Total Lifecycle Cost:     4
Execution Efficiency:     3
Execution Reliability:    3
Growth Potential:         2
Conceptual Clarity:       4
Validation Support:       3
```

Summary Metrics
Total Score: 30
Footprint Category: Balanced Scope
Expertise Required: Medium

Footprint Position
Narrow [========◆=================] Broad

---

## 4) Service-Based Architecture

```
Partitioning approach: Domain-oriented components
Typical deployable units: Few to many

Operational Independence: 4
Elastic Capacity:         2
Adaptability Over Time:   3
Failure Containment:      3
Structural Modularity:    4
Total Lifecycle Cost:     3
Execution Efficiency:     3
Execution Reliability:    4
Growth Potential:         3
Conceptual Clarity:       3
Validation Support:       4
```

Summary Metrics
Total Score: 36
Footprint Category: Broad Scope
Expertise Required: Medium

Footprint Position
Narrow [=============◆=============] Broad

---

## 5) Event-Driven Architecture

```
Partitioning approach: Decentralized
Typical deployable units: Few to many

Operational Independence: 3
Elastic Capacity:         4
Adaptability Over Time:   5
Failure Containment:      5
Structural Modularity:    4
Total Lifecycle Cost:     3
Execution Efficiency:     5
Execution Reliability:    3
Growth Potential:         5
Conceptual Clarity:       2
Validation Support:       2
```

Summary Metrics
Total Score: 41
Footprint Category: Distributed Scope
Expertise Required: High

Footprint Position
Narrow [==================◆========] Broad

---

## 6) Space-Based (In-Memory Grid) Architecture

```
Partitioning approach: Distributed state and processing
Typical deployable units: Few to many

Operational Independence: 3
Elastic Capacity:         5
Adaptability Over Time:   3
Failure Containment:      3
Structural Modularity:    3
Total Lifecycle Cost:     2
Execution Efficiency:     5
Execution Reliability:    4
Growth Potential:         5
Conceptual Clarity:       2
Validation Support:       2
```

Summary Metrics
Total Score: 37
Footprint Category: Broad Scope
Expertise Required: High

Footprint Position
Narrow [=============◆=============] Broad

---

## 7) Orchestrated SOA

```
Partitioning approach: Centralized control with distributed execution
Typical deployable units: 1 to few

Operational Independence: 1
Elastic Capacity:         3
Adaptability Over Time:   1
Failure Containment:      3
Structural Modularity:    3
Total Lifecycle Cost:     2
Execution Efficiency:     2
Execution Reliability:    2
Growth Potential:         4
Conceptual Clarity:       2
Validation Support:       2
```

Summary Metrics
Total Score: 24
Footprint Category: Narrow Scope
Expertise Required: Low

Footprint Position
Narrow [=====◆====================] Broad

---

## 8) Microservices Architecture

```
Partitioning approach: Domain
Typical deployable units: Many

Operational Independence: 4
Elastic Capacity:         5
Adaptability Over Time:   5
Failure Containment:      4
Structural Modularity:    5
Total Lifecycle Cost:     2
Execution Efficiency:     2
Execution Reliability:    4
Growth Potential:         5
Conceptual Clarity:       2
Validation Support:       4
```

Summary Metrics
Total Score: 42
Footprint Category: Distributed Scope
Expertise Required: High

Footprint Position
Narrow [====================◆======] Broad

