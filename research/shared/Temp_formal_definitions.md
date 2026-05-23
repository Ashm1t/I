# FORMAL DEFINITIONS

Status:

WORKING

These definitions are provisional and temporary and are subject to change, this just to give an idea.

---

## Intelligence

Operational definition:

Intelligence is adaptation capability over changing tasks.

Let:

E = environment

P = performance

t = time

A = adaptation

Define:

A(t) = dP(E,t)/dt

Intelligence:

I ∝ A(t)

Higher adaptation → higher intelligence.

Constraint:

Intelligence ≠ parameter count

Intelligence ≠ static benchmark score

---

## Plasticity

Definition:

Ability to modify internal state during runtime.

State:

S(t)

Plasticity:

Π(t) = ||S(t+1)-S(t)||

Forms:

Weight plasticity:

Πw = ||W(t+1)-W(t)||

Adapter plasticity:

Πα = ||α(t+1)-α(t)||

Memory plasticity:

Πm = ||M(t+1)-M(t)||

Constraint:

Excess plasticity:

Π → instability

Need:

stability term:

Ω

Objective:

maximize:

A

subject to:

Π < Ω

---

## Adaptation

Let:

Pbefore

Pafter

Adaptation score:

Adapt = Pafter - Pbefore

Adaptation efficiency:

ηadapt = Adapt / Δt

Goal:

maximize:

ηadapt

---

## Dreaming

Definition:

Offline internal computation.

Dream cycle:

D:

Replay:

R

Mutation:

U

Consolidation:

C

Evaluation:

V

Dream process:

D = V(C(U(R(M))))

where:

M:

memory source

---

## Replay

Memory samples:

mi

Replay:

R(M)=Σwi*mi

weights:

wi:

importance

Constraint:

Σwi = 1

---

## Self

Self state:

Self(t)

Components:

goal state:

G(t)

identity state:

I(t)

history:

H(t)

Self vector:

Self(t)=

[G,I,H]

Constraint:

Self ≠ consciousness

---

## Retention

Task performance:

P0

Delayed performance:

Pt

Retention:

Ret = Pt / P0

Goal:

maximize:

Ret

---

## Forgetting

Previous performance:

Pold

Current:

Pnew

Forgetting:

F = Pold - Pnew

Goal:

minimize:

F

---

## APC

WORKING FORM

APC(M):

Replay:

R

Mutation:

U

Plastic update:

P

Consolidation:

C

APC:

APC(M)=C(P(U(R(M))))

Status:

UNDEFINED

---

## GRM

Memory graph:

G=(V,E)

Reconstruction:

GRM(G)

Current hypothesis:

GRM:

reorganizes graph memory.

Candidate:

GRM(G)=G'

Status:

UNDEFINED