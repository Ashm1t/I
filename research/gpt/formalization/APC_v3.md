# APC v3 Formalization

Status: FINAL THEORY REVISION

## Scope

APC ⊂ Dream

Dream = (R,U,V)

APC operates as consolidation machinery within the dream process.

---

## State definition

M = (M_ep, M_param)

M_ep:
Episodic replay memory

M_param:
Parametric memory / adapters

---

Replay:

R(M_ep)=Σ w_i m_i

Constraint:

Σ w_i = 1

---

Mutation:

U_mut(m_i)=m_i+ε

---

Recombination:

U_rec(m_i,m_j)=φ(m_i,m_j)

Source:
research/claude/theory/recombination_v0.md

Baseline:
Candidate 1 (linear interpolation)

---

Dream state:

D_t = U_rec(U_mut(R(M_ep^t)))

Dream gate:

V(D_t)

Reject degrading traces.

---

Plastic update operator:

P(x) yields Π_(t+1)

Π_(t+1)=f(Π_t,D_t)

Constraint:

||Π_(t+1)|| ≤ Ω

---

Consolidation:

M_param^(t+1)=M_param^(t)+αΠ_t

---

APC:

APC(M)=C(P(V(U_rec(U_mut(R(M_ep))))))

---

Prediction:

Retention_APC - Retention_static ≥ δ_r

Forgetting_static - Forgetting_APC ≥ δ_f

Transfer_APC - Transfer_static ≥ δ_t

δ values fixed before EXP-001.

---

Next:
EXP-001
STOP
