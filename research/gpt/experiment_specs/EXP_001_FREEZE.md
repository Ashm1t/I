# EXP-001 Freeze

Status: FROZEN

Replay:

w_i ∝ α r_i + β s_i

Constraint:

Σ w_i = 1

r_i:
recency

s_i:
surprise / loss

---

Recombination:

φ(m_i,m_j)=λm_i+(1−λ)m_j

λ ~ U(0.3,0.7)

---

Mutation:

ε ~ N(0,σ_i²)

Scaled by trace variance.

---

Dream gate metric:

ρ_v = accepted / generated

Expected:

0.2 ≤ ρ_v ≤ 0.6

ρ_v ≈ 0 => invalid experiment

---

Consolidation:

C(Π_t)=M_param^(t+1)=M_param^(t)+αΠ_t

---

Success criteria (ALL required):

Retention gain ≥ 0.05

Forgetting reduction ≥ 0.03

Transfer gain ≥ 0.02
