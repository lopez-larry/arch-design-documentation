# **Measuring Modularity Concepts — Summary**

---

## **Cohesion**

**Definition:**
How strongly related and focused the responsibilities of a module are.

**Key idea:**

* High cohesion → a module does **one thing well**
* Low cohesion → a module handles **unrelated responsibilities**

**Why it matters:**

* High cohesion makes systems easier to maintain, test, and evolve
* Cohesive modules change for **one reason** (Single Responsibility Principle)

**Cohession Measures**
* Functionsl: Every part of the module is related to the other, and the module contains everything essential to functions.

* Sequential: Two modules interact, where one outputs data that becomes the input fo rthe other.

* Communicational: Two moduels from a communication chain, where each operates on information and/or contributes to some output. 

* Procedural: Tow modules must execute code in a particular order.

* Temporal: Modules are related based on timing dependencis. 

* Logical: The data wihtin modules is related locially but not functionally.  

* Coincidental: Elements in a module are not related other than being in the smae source file; this represents the most negative form of cohesion.


---

## **Coupling**

**Definition:**
The degree to which modules depend on each other.

**Types (by strength):**

* Loose/low coupling → modules rely on well-defined interfaces
* Tight/high coupling → modules require intimate knowledge of each other

**Why it matters:**

* Highly coupled systems are **hard to change**, because one module’s change breaks another
* Good architectures aim for **high cohesion + low coupling**

---

## **Abstractness**

**Definition:**
Measures how much a module uses abstract types (interfaces, base classes) vs. concrete classes.

**Scale:**

* 1.0 → fully abstract
* 0.0 → fully concrete

**Why it matters:**

* Abstract modules are easier to extend
* Concrete modules are easier to execute but harder to evolve

---

## **Instability**

**Definition:**
How likely a module is to change when something else changes.

**Formula (Robert Martin):**

```
Instability = Fan-out / (Fan-in + Fan-out)
```

* Fan-out → outgoing dependencies
* Fan-in → incoming dependencies

**Interpretation:**

* 1.0 = very unstable (depends on many others)
* 0.0 = very stable (many depend on it)

---

## **Distance from the Main Sequence**

**Definition:**
How far a module lies from the *ideal balance* between abstractness and stability.

**Main sequence line:**

```
Stability increases → Abstractness should increase
```

**Meaning:**

* If a module is **stable + abstract**, others can extend it safely (great)
* If it is **stable + concrete**, it can’t change and can’t be extended → “worst zone”
  (called the **Zone of Pain**)

---

## **Connascence**

**Definition:**
A measure of how **changes in one module force changes in another**.

**Terrific book concept — stronger than coupling.**

### Degrees of connascence (ordered from weakest to strongest):

* **Name** — components must agree on a name
* **Type**
* **Meaning**
* **Position**
* **Algorithm**
* **Execution**
* **Timing**
* **Identity**

**Rules of thumb (from the book):**

* Prefer lower forms (Name, Type)
* Avoid higher forms (Timing, Identity)
* Reduce connascence across boundaries (especially service/module borders)

---

## **Unified Coupling + Connascence Metrics**

**Intent:**
Richards & Ford combine **classical coupling** with **connascence** to evaluate modularity more realistically.

**Takeaway:**

* Coupling tells you *whether* modules depend on each other
* Connascence tells you *how painful* that dependence is

Architects should:

* **Minimize connascence strength**
* **Localize strong connascence inside modules**
* **Weaken it across module/service boundaries**

---

## **From Modules to Components**

**Concept:**
Modules are logical units; components are deployable/replaceable units.

**Key distinction:**

* A **module** is a design-time concept
* A **component** is a runtime artifact (jar, DLL, Docker service)

**Progression from the book:**

1. Improve modularity through cohesion/coupling/connascence
2. Identify natural boundaries
3. Turn modules → components → services (if justified)

**Why it matters:**

* Good module boundaries allow:

  * easier refactoring
  * clean deployment boundaries
  * scaling into microservices or plugins later
