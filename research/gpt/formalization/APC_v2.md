# APC v2 Formalization

Status: ACTIVE

Review source:

research/claude/reviews/APC_v1_review.md

---

## State definition

M = (M_ep, M_param)

M_ep:

episodic replay memory

M_param:

parametric memory / adapters

---

Replay:

R(M_ep) = Σ w_i m_i

Constraint:

Σ w_i = 1

---

Mutation:

U_mut(m_i) = m_i + ε

---

Recombination:

U_rec(m_i,m_j) = φ(m_i,m_j)

φ:

recombination operator

Undefined.

---

Plastic update:

Π_(t+1) = f(Π_t,D_t)

Constraint:

||Π_(t+1)|| ≤ Ω

Ω:

stability term

---

Consolidation:

M_param^(t+1)
=
M_param^(t)
+
αΠ_t

---

Full APC:

APC(M)
=
C(P(U_rec(U_mut(R(M_ep)))))

---

Status:

APC_v2

Awaiting Claude review.
