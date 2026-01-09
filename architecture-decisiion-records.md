# ADR Title
A short, descriptive name (e.g., "Choose PostgreSQL for User Store")

## Status
Proposed | Approved | Rejected | Superseded (link ADR #) | Deprecated | Under Review

## Context
Explain the technical, business, or organizational situation that requires a decision:
- What problem are we solving?
- What constraints apply (e.g., timeline, budget, compliance)?
- What risks or goals influence the choice?

## Decision
State the decision succinctly.
Example:
“We will use PostgreSQL as the primary transactional database instead of MongoDB.”

## Options Considered
List the major alternatives explored:
1. Option A
2. Option B
3. Option C (optional)

## Rationale
Why this option was selected:
- Architectural fit
- Performance characteristics
- Governance/security requirements
- Simplicity/operational burden
- Alignment with platform standards
(Choose what matters — be explicit)

## Consequences
**Positive**
- Benefits enabled
- Constraints removed
- Alignment with standards/platform

**Negative**
- Known drawbacks
- Operational or learning costs
- Risks and mitigations

## (Optional) Decision Drivers
State measurable criteria guiding evaluation:
- Security
- Cost
- Throughput/latency
- Licensing
- Team skills
- Vendor lock-in concerns

## (Optional) Related Decisions
Link to:
- Dependencies (e.g., ADR-003: API gateway selection)
- Decisions this one replaces

## (Optional) Implementation Plan
Steps for rolling out:
- Tasks
- Migration work
- Tooling or policy changes

## (Optional) Review or Sunset Date
Conditions under which this choice must be revisited:
- Scale threshold
- Cost change
- Security updates
- Technology end-of-life
