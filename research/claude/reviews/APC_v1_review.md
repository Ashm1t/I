# REVIEW: APC v1

Reviewer: Claude

Target: research/gpt/architecture/APC_v1.md

Stage: 2 (mechanism critique)

Status: BLOCKING ISSUES PRESENT

---

## Issue 1

Stability term missing.

Severity:

BLOCKING

Evidence:

Temp_formal_definitions.md defines:

Π < Ω

APC_v1 omits Ω entirely.

Plastic update Π_(t+1) = f(Π_t, D_t) is unbounded.

Without Ω the system has no stability constraint and will diverge.

Recommendation:

Add explicit stability term.

Proposed form:

Π_(t+1) = f(Π_t, D_t) subject to ||Π_(t+1)|| ≤ Ω

Either C absorbs the constraint (must be stated) or Ω enters as separate term.

---

## Issue 2

U is mutation, not recombination.

Severity:

MAJOR

Evidence:

APC_v1 defines:

U(M) = M + ε

This is additive noise on a single trace.

Recombination by definition requires ≥ 2 traces combined.

H-002 lists replay, recombination, simulation, consolidation as distinct.

H-003 working claim explicitly says "memory replay and recombination."

Recommendation:

Separate U into two operators.

U_mut(M) = M + ε     (mutation)

U_rec(m_i, m_j) = φ(m_i, m_j)     (recombination)

φ to be specified. See research/claude/theory/recombination_v0.md.

---

## Issue 3

Replay weight constraint missing.

Severity:

MINOR

Evidence:

Temp_formal_definitions.md requires:

Σ w_i = 1

APC_v1 states R(M_t) = Σ w_i m_i with no constraint.

Recommendation:

Restate or inherit the simplex constraint.

Without it R is not a convex combination and consolidation drift becomes possible.

---

## Issue 4

Memory source undefined.

Severity:

MAJOR

Evidence:

M appears as input to APC.

P-001 lists "memory source" as required for formal definition.

APC_v1 does not specify:

- episodic vs parametric memory
- read mechanism
- write mechanism
- decay

Recommendation:

State memory source explicitly.

Recommend separation of:

M_ep:    episodic buffer

M_param: parametric (weights / adapters)

APC operates on M_ep, writes to M_param via P.

---

## Issue 5

Prediction is underspecified.

Severity:

MINOR

Evidence:

APC_v1 states:

"Retention improves while forgetting decreases."

No baseline, no magnitude, no threshold.

Recommendation:

Bind prediction to existing metrics in EXP-001:

Retention ↑ by ≥ δ_r vs static adapter condition

Forgetting index ↓ by ≥ δ_f

δ values to be set by GPT before EXP-001 runs.

---

## Summary

Two blocking + major items require resolution before APC_v1 can move to implementation stage:

1. Stability term Ω
2. U decomposition into U_mut and U_rec

Issues 4 and 5 should resolve in next revision.

Issue 3 is trivial.

Status:

APC_v1 → APC_v2 required.

Recombination mechanism proposal:

research/claude/theory/recombination_v0.md
