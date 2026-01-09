# Architecture Characteristics Rating Matrices


Scale:
★ = weak support
★★ = moderate
★★★ = strong
★★★★ = excellent
★★★★★ = dominant strength

A quantum is the smallest deployable unit of functionality in an architecture —
a piece you can build, test, deploy, scale, and replace independently.
---
## 1) LAYERED ARCHITECTURE

```
Partitioning type: Technical
Number of quanta: 1

Deployability:    ★
Elasticity:       ★
Evolutionary:     ★
Fault tolerance:  ★
Modularity:       ★
Overall cost:     ★★★★★
Performance:      ★★
Reliability:      ★★★
Scalability:      ★
Simplicity:       ★★★★★
Testability:      ★★
```

---
## 2) PIPELINE (OR DATAFLOW) ARCHITECTURE

```
Partitioning type: Technical 
Number of quanta: 1

Deployability:    ★★
Elasticity:       ★
Evolutionary:     ★★★
Fault tolerance:  ★
Modularity:       ★★★
Overall cost:     ★★★★★
Performance:      ★★
Reliability:      ★★★
Scalability:      ★
Simplicity:       ★★★★★
Testability:      ★★★
```

---
## 3) MICROKERNEL ARCHITECTURE

```
Partitioning type: Technical & Domain 
Number of quanta: 1

Deployability:    ★★★
Elasticity:       ★
Evolutionary:     ★★★
Fault tolerance:  ★
Modularity:       ★★★
Overall cost:     ★★★★★
Performance:      ★★★
Reliability:      ★★★
Scalability:      ★
Simplicity:       ★★★★
Testability:      ★★★
```

---

## 4) SERVICE-BASED ARCHITECTURE

```
Partitioning type: Domain
Number of quanta: 1 to Many

Deployability:    ★★★★
Elasticity:       ★★
Evolutionary:     ★★★
Fault tolerance:  ★★★★
Modularity:       ★★★★
Overall cost:     ★★★★
Performance:      ★★★
Reliability:      ★★★★
Scalability:      ★★★
Simplicity:       ★★★
Testability:      ★★★★
```
---

## 5) EVENT-DRIVEN ARCHITECTURE

```
Partitioning type: Technical
Number of quanta: 1 to Many

Deployability:    ★★★
Elasticity:       ★★★
Evolutionary:     ★★★★★
Fault tolerance:  ★★★★★
Modularity:       ★★★★
Overall cost:     ★★★
Performance:      ★★★★★
Reliability:      ★★★
Scalability:      ★★★★★
Simplicity:       ★
Testability:      ★★
```

---

## 6) SPACE-BASED ARCHITECTURE

```
Partitioning type: Domain & Technical
Number of quanta: 1 to Many

Deployability:    ★★★
Elasticity:       ★★★★★
Evolutionary:     ★★★
Fault tolerance:  ★★★
Modularity:       ★★★
Overall cost:     ★★
Performance:      ★★★★★
Reliability:      ★★★★
Scalability:      ★★★★★
Simplicity:       ★
Testability:      ★
```

---
## 7) ORCHESTRATION-DRIVEN SERVICE-ORIENTED ARCHITECTURE

```
Partitioning type: Technical
Number of quanta: 1

Deployability:    ★
Elasticity:       ★★★
Evolutionary:     ★
Fault tolerance:  ★★★
Modularity:       ★★★
Overall cost:     ★
Performance:      ★★
Reliability:      ★★
Scalability:      ★★★★
Simplicity:       ★
Testability:      ★
```

---

## 8) MICROSERVICES ARCHITECTURE

```
Partitioning type: Domain
Number of quanta: 1 to Many

Deployability:    ★★★★
Elasticity:       ★★★★★
Evolutionary:     ★★★★★
Fault tolerance:  ★★★★
Modularity:       ★★★★★
Overall cost:     ★
Performance:      ★★
Reliability:      ★★★★
Scalability:      ★★★★★
Simplicity:       ★
Testability:      ★★★★
```

---








