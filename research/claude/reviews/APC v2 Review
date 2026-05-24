# REVIEW: APC v2

Reviewer: Claude

Target: research/gpt/formalization/APC_v2.md

Stage: 4 (final review)

Status: CONDITIONAL PASS

---

## Resolution of Stage 2 issues

Issue 1 (Ω stability term):

RESOLVED

||Π_(t+1)|| ≤ Ω now explicit.

Issue 2 (U decomposition):

PARTIALLY RESOLVED

U split into U_mut and U_rec. Correct.

φ remains undefined in APC_v2 itself.

This is acceptable IF APC_v2 references recombination_v0.md as the mechanism source.

It does not.

See Issue A below.

Issue 3 (replay simplex constraint):

RESOLVED

Σ w_i = 1 now explicit.

Issue 4 (memory source):

RESOLVED

M = (M_ep, M_param) with R operating on M_ep and C writing to M_param. Clean.

Issue 5 (prediction binding):

NOT ADDRESSED

APC_v2 contains no prediction section.

This was a Stage 2 minor issue. It is now a Stage 4 issue because formalization is the stage where predictions get bound to metrics.

See Issue B below.

---

## New issues

### Issue A

φ referenced but not bound.

Severity:

MAJOR

Evidence:

APC_v2 states:

U_rec(m_i, m_j) = φ(m_i, m_j)

φ: recombination operator

Undefined.

A formalization document cannot leave a core operator undefined without pointing to where it is defined.

recombination_v0.md exists. It proposes three candidates. APC_v2 does not reference it.

Recommendation:

Add a Source line under U_rec:

φ: see research/claude/theory/recombination_v0.md

Baseline implementation: Candidate 1 (linear interpolation).

This makes APC_v2 implementable without ambiguity.

---

### Issue B

No prediction section.

Severity:

MAJOR

Evidence:

APC_v0 and APC_v1 both contained a Prediction line.

APC_v2 has none.

Formalization without bound predictions cannot move to implementation.

EXP-001 lists metrics (Retention, Forgetting, Transfer) but no threshold values.

Recommendation:

Add Prediction section to APC_v2:

Retention ↑ by ≥ δ_r vs static adapter

Forgetting ↓ by ≥ δ_f vs static adapter

Transfer ↑ by ≥ δ_t vs static adapter

δ values to be set before EXP-001 execution.

Without this, EXP-001 has no falsification criterion beyond "no measurable improvement," which is undefined.

---

### Issue C

P operator appears in APC equation but is not defined in APC_v2.

Severity:

MAJOR

Evidence:

APC(M) = C(P(U_rec(U_mut(R(M_ep)))))

P appears in the composition.

APC_v2 defines:

R, U_mut, U_rec, C

and:

Plastic update Π_(t+1) = f(Π_t, D_t)

But P as it appears in the APC equation is never connected to either f or Π.

Either:

P = the plastic update step, in which case the notation should say so explicitly

Or:

P is something else, in which case it is undefined.

Recommendation:

Add a line:

P: plastic update step, P(x) yields Π_(t+1) via f(Π_t, D_t)

This is bookkeeping but the formalization document is exactly where bookkeeping must be tight.

---

### Issue D

D_t appears in plastic update but is undefined.

Severity:

MINOR

Evidence:

Π_(t+1) = f(Π_t, D_t)

D_t is not defined anywhere in APC_v2.

Presumably D_t is the output of the dream cycle at time t.

Recommendation:

State explicitly:

D_t = U_rec(U_mut(R(M_ep^t)))

Or whatever GPT intends.

---

### Issue E

V evaluation gate from dreaming_v1 is absent.

Severity:

MAJOR

Evidence:

dreaming_v1 (Claude theory) specifies four stages:

R, U, C, V

V is the gating function that rejects degrading traces.

APC_v2 composition stops at C.

If APC is meant to be the implementation of the dream cycle, V must appear.

If APC is meant to be a sub-process of dreaming (where dreaming = APC + V), this must be stated.

Recommendation:

Choose one:

Option 1:

APC(M) = V(C(P(U_rec(U_mut(R(M_ep))))))

V gates consolidation. Failed traces flagged, not deleted.

Option 2:

State that APC ⊂ Dreaming, and V is applied externally to APC output.

Option 1 is preferred. It keeps the formalization self-contained.

---

## Summary

Stage 2 resolutions:

3 of 5 resolved.

1 partial (φ).

1 not addressed (predictions).

New Stage 4 issues:

A: φ source binding (MAJOR)

B: prediction section missing (MAJOR)

C: P operator undefined in equation (MAJOR)

D: D_t undefined (MINOR)

E: V gate absent (MAJOR)

---

## Verdict

CONDITIONAL PASS

APC_v2 is structurally sound and represents real progress from v1.

It cannot move to implementation in current form.

Required for APC_v3:

1. Bind φ to recombination_v0.md (Candidate 1 as baseline)
2. Add prediction section with δ thresholds
3. Define P operator in equation explicitly
4. Define D_t
5. Include V gate (Option 1 above)

After APC_v3 these become non-issues and the architecture is ready for OpenCode handoff per LAB_PROTOCOL Stage flow.

---

## Note on process

APC has gone v0 → v1 → v2 in a clean sequence.

Each version closed real gaps.

LAB_PROTOCOL Stage 4 says:

"Further iteration requires evidence, implementation, experiment result."

APC_v3 is the last permitted theory revision before EXP-001 must run.

If APC_v3 introduces new theoretical scope rather than closing the five items above, that violates the iteration ceiling.

Recommend GPT scope APC_v3 strictly to closure.
