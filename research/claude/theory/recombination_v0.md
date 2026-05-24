# Recombination Mechanism v0

Status: ACTIVE

Owner: Claude

Addresses:

- Issue 2 in APC_v1 review
- Mechanism gap in dreaming_v1

---

## Problem

APC_v1 defines U(M) = M + ε.

This is mutation.

Recombination requires combining ≥ 2 traces into a structurally novel trace.

No mechanism for this currently exists in the formalization.

---

## Claim

Recombination can be implemented as alignment-then-mixing in trace representation space.

Three candidate mechanisms are proposed.

Selection between them is an implementation question.

---

## Candidate 1: Linear interpolation

U_rec(m_i, m_j) = α m_i + (1-α) m_j

α ∈ (0, 1)

Pros:

trivial to implement

differentiable

Cons:

produces trace averages, not novel structure

linear in representation space

likely insufficient

Verdict:

baseline only.

---

## Candidate 2: Component swap

Decompose m into components:

m = (c_1, c_2, ..., c_k)

U_rec(m_i, m_j) = (c^i_1, c^j_2, c^i_3, ...)

Pros:

produces structurally novel traces

closer to biological recombination analogy

Cons:

requires component decomposition

components must be meaningful units

risk of incoherent combinations

Verdict:

promising if decomposition is solved.

Requires a separate trace-segmentation step.

---

## Candidate 3: Latent crossover

Project to latent z:

z_i = E(m_i)

z_j = E(m_j)

Crossover in z:

z' = mask ⊙ z_i + (1 - mask) ⊙ z_j

Decode:

m' = D(z')

Pros:

structurally novel

operates where structure is encoded

mask can be learned

Cons:

requires encoder/decoder pair

z space must be regular enough for crossover to produce valid traces

Verdict:

most likely to produce useful novel associations.

Highest implementation cost.

---

## Gating

All three candidates produce candidates.

Evaluation V (from dreaming_v1) decides which m' survive.

This means:

high recombination yield is fine

low V pass rate is the actual constraint

The system can afford to generate many bad recombinations if V is reliable.

---

## Prediction

In order of expected performance:

Candidate 3 > Candidate 2 > Candidate 1

In order of implementation cost:

Candidate 3 > Candidate 2 > Candidate 1

Recommend starting with Candidate 1 as baseline.

Promote to 2 then 3 only if baseline shows insufficient novel_assoc_score.

---

## Metric

novel_assoc_score:    count of m' that pass V and are not near-duplicates of M

trace_validity_rate:  fraction of U_rec outputs passing V

structural_novelty:   distance of m' to nearest m in M

---

## Failure

Any of:

- All three candidates produce m' indistinguishable from mutation
- V pass rate near zero (recombination produces only invalid traces)
- novel_assoc_score does not correlate with downstream transfer

---

## Open

- Component decomposition for Candidate 2
- Encoder/decoder architecture for Candidate 3
- Whether U_mut and U_rec should be applied sequentially or in parallel
- Whether mask in Candidate 3 should be learned or random
