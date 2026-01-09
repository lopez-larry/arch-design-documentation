# Modular Equations Reference

---

## Abstractness

`A = Σ mᵃ / Σ mᶜ`

### What Abstractness Measures

Abstractness measures how abstract a code component (module or package) is, based on the types it contains.

A component is more abstract if it:

* Defines interfaces
* Contains abstract classes
* Uses base classes or abstract types

A component is more concrete if it:

* Mostly contains executable implementation classes
* Focuses on behavior rather than contracts

---

### Understanding the Formula

Symbols

* Σ mᵃ = total count of abstract types
  (interfaces, abstract classes, language-specific abstractions)
* Σ mᶜ = total count of concrete types
  (regular classes, structs, concrete implementations)

Meaning

```
A = (number of abstract types) / (total number of types)
```

Equivalent form:

```
A = Na / (Na + Nc)
```

---

### Result Range

| A value | Interpretation                          |
| ------- | --------------------------------------- |
| 0.0     | Purely concrete component               |
| 0.5     | Balanced mix of abstract and concrete   |
| 1.0     | Fully abstract; provides contracts only |

---

### Why the Metric Matters

Architecturally:

* Stable modules should be abstract (so dependents can extend without breaking).
* Volatile modules can afford to be concrete.

Imbalances lead to:

* Stable + concrete → Zone of Pain
* Abstract + unstable → Zone of Uselessness

This value feeds directly into Distance from Main Sequence.

---

### Example

A package contains:

* 2 interfaces
* 1 abstract base class
* 7 concrete classes

Then:

```
Σ mᵃ = 3
Total = 7 + 3 = 10
A = 3 / 10 = 0.3
```

Result: Mildly abstract, primarily concrete.

---

### Practical Takeaways

* Higher A: easier to extend safely
* Lower A: easier to execute but harder to evolve
* Abstractness is most informative when paired with Instability

One-sentence summary
Abstractness indicates how much a component defines contracts rather than implementing behavior.

---

## Instability

`I = Cᵉ / (Cᵉ + Cᵃ)`

Where:

* Cᵉ (efferent coupling) = outgoing dependencies
  Components this one relies on
* Cᵃ (afferent coupling) = incoming dependencies
  Components that rely on this one

---

### What Instability Measures

Instability estimates how likely a component is to change based on dependency direction.

Intuition:

* High outgoing dependencies → vulnerable to change → unstable
* High incoming dependencies → widely used → must remain stable

---

### Output Range Interpretation

| I value | Meaning        | Interpretation                            |
| ------- | -------------- | ----------------------------------------- |
| 0.0     | Fully stable   | Relied on heavily; changes are costly     |
| 0.5     | Balanced       | Depends on others and others depend on it |
| 1.0     | Fully unstable | Depends on many; nothing depends on it    |

---

### Examples

1. Depends on many, relied on little

```
Cᵉ = 12, Cᵃ = 3
I = 12 / (12 + 3) = 0.8
```

Highly unstable.

2. Relied on heavily, depends on little

```
Cᵃ = 25, Cᵉ = 2
I = 2 / (2 + 25) = 0.074
```

Highly stable.

---

### Where Instability Fits

Instability is paired with:

```
Abstractness:   A = Na / (Na + Nc)
Distance:       D = |A + I – 1|
```

Together they classify components into:

* Zone of Pain (stable + concrete)
* Zone of Uselessness (abstract + unstable)
* Main Sequence (balanced)

---

### Why Architects Care

Instability helps identify:

* Stable, reusable frameworks (low I, high A)
* Fast-changing application logic (high I, low A)
* Components under strain (low A, low I)

One-sentence summary
Instability measures how much a component depends on others versus how many depend on it, predicting how painful change will be.

---

## Distance from Main Sequence

`D = |A + I – 1|`

Where:

* A = Abstractness
* I = Instability

---

### What the Metric Means

Distance measures how close a component is to the ideal balance between abstraction and stability.

The Main Sequence is defined by:

```
A + I = 1
```

Components on this line:

* Are appropriately abstract if they are stable
* Appropriately concrete if they are unstable

---

### Interpretation of Values

| D value       | Meaning                                |
| ------------- | -------------------------------------- |
| 0.0           | Perfect balance; on main sequence      |
| Near 0        | Healthy; no structural concern         |
| Approaching 1 | Poor balance; likely needs examination |

---

### Deficiency Zones

Zone of Pain (stable + concrete)

* Hard to change
* Central to the system
* Few extension points

Zone of Uselessness (abstract + unstable)

* Provides abstractions
* No consumers depend on them
* "Frameworks looking for users"

Main Sequence

* Components are aligned to their roles
* Either stable and abstract, or unstable and concrete

---

### Examples

Balanced

```
A = 0.3, I = 0.6
D = |0.3 + 0.6 – 1| = 0.1
```

Zone of Pain

```
A = 0.0, I = 0.0
D = |0 + 0 – 1| = 1.0
```

---

### Why This Matters

Distance highlights:

* Structural imbalance
* Design pressure points
* Refactoring priorities

High D values justify inspection, not immediate refactoring.

One-sentence summary
Distance from Main Sequence shows how far a component lies from a healthy balance between abstractness and dependency structure.

---

## Cohesion (via LCOM)

### Original LCOM

```
LCOM = |P| – |Q|, if |P| > |Q|
        0 otherwise
```

Where:

* P = number of method pairs that do not share fields
* Q = number of method pairs that do share fields

Interpretation:

* Large P relative to Q → low cohesion → LCOM > 0
* Q ≥ P → cohesive → LCOM = 0

Meaning:

* LCOM = 0 → High cohesion (preferred)
* LCOM > 0 → Likely multiple responsibilities

---

### Henderson-Sellers (LCOM96b)

```
LCOM96b = (1 / m) Σ from j=1 to m [ (m – μ(Aj)) / m ]
```

Where:

* m = number of methods
* Aj = set of attributes referenced by method j
* μ(Aj) = number of methods referencing the same attribute

Interpretation:

* High overlap in used fields → high cohesion → low LCOM96b
* Each method uses its own fields → low cohesion → high LCOM96b

Range:

* 0 ≤ LCOM96b ≤ 1
  0 means cohesive, 1 means incohesive

Why this version exists:

* Original LCOM can grow without bound
* LCOM96b normalizes values for comparison

---

### Big Picture

| Metric                      | Range | Meaning                              |
| --------------------------- | ----- | ------------------------------------ |
| Original LCOM               | 0–∞   | Zero is good; higher indicates worse |
| LCOM96b (Henderson-Sellers) | 0–1   | Zero is good; closer to 1 is worse   |

Rules of thumb:

* LCOM = 0 → Class is cohesive
* LCOM > 0 → Class mixes concerns
* LCOM96b ≈ 0 → Good cohesion
* LCOM96b ≈ 1 → Low cohesion

---

Everything above now reads as a consistent document in one voice, structured for reference or knowledge capture.
Let me know when you want coupling, connascence, or modularity scoring added next.
