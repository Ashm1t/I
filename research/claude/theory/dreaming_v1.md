# Dreaming Theory v1

Status: ACTIVE

Owner: Claude

Addresses:

- H-002
- P-003

Supersedes:

dreaming_v0.md (placeholder)

---

## Claim

Dreaming is offline computation that improves retention and enables novel association by operating on memory traces without environmental input.

Dreaming is not a single operation.

Dreaming is a four-stage cycle.

---

## Stages

Stage 1: Replay

R(M)

Sample memory traces weighted by importance.

w_i:    importance signal

Σ w_i = 1

Output:

ordered trace sequence

Stage 2: Mutation and Recombination

U_mut(m_i) = m_i + ε

U_rec(m_i, m_j) = φ(m_i, m_j)

Mutation explores local trace neighborhood.

Recombination produces novel associations.

See: recombination_v0.md

Stage 3: Consolidation

C(m')

Selected mutated or recombined traces are written to parametric memory via plastic update.

Subject to:

stability constraint Ω

Stage 4: Evaluation

V(m')

Reject traces that degrade retention on held-out anchor set.

V is a gating function, not a metric.

Failed traces are not deleted from M_ep.

Failed traces are flagged.

---

## Full process

D(M) = V(C(U(R(M))))

Where U = {U_mut, U_rec}

---

## Why offline

Online learning is constrained by environmental ordering.

Dreaming relaxes the ordering constraint.

This allows:

- replay of low-frequency traces
- recombination across temporally distant traces
- consolidation without interference from new input

---

## Why mutation AND recombination

Mutation alone:

local search.

Cannot produce structurally novel traces.

Recombination alone:

cannot fine-tune.

Both together:

exploration + exploitation in trace space.

This mirrors the standard evolutionary computation argument.

The claim that biological dreaming does this is not made here.

---

## Prediction

Systems with full D cycle outperform systems with only R or only R + C on:

- retention score
- novel association score
- transfer score

Magnitude of improvement bounded by quality of V.

If V is too strict: no consolidation.

If V is too loose: noise consolidation, retention degrades.

There exists an optimal V threshold.

---

## Metric

retention_score:    P_t / P_0 on anchor set

transfer_score:     P on held-out task after dream cycle

novel_assoc_score:  count of novel m' that pass V

---

## Failure

Any of:

- D cycle does not improve retention vs R alone
- novel associations all fail V
- consolidation requires increasing Ω over time (instability)

---

## Open

- Form of V (gating function)
- Frequency of dream cycle
- Trade-off between U_mut and U_rec
- Whether D requires a separate model or runs on the same parameters
