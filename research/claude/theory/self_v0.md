# Self Representation v0

Status: ACTIVE

Owner: Claude

Addresses:

- H-005
- P-005

Constraint:

Self ≠ consciousness

This is a functional definition only.

---

## Claim

A persistent internal representation that maintains goals, identity markers, and behavioral history improves coherence across time.

Coherence is the testable property.

Consciousness is not invoked, claimed, or required.

---

## Definition

Self state at time t:

Self(t) = [G(t), I(t), H(t), B(t)]

G: goal state

active goals, priorities

I: identity markers

stable preferences, role, constraints

H: history

compressed behavioral trace

B: bias state

learned response tendencies

---

## Persistence

Self must persist across:

- input boundaries
- task switches
- dream cycles

Self update rule:

Self(t+1) = g(Self(t), input_t, action_t)

g is smooth.

||Self(t+1) - Self(t)|| ≤ σ

σ is the self-stability bound.

If ||ΔSelf|| > σ:

identity break.

This is a failure condition, not a feature.

---

## Why this is not consciousness

Self(t) is a data structure.

No claim of subjective experience.

No claim of qualia.

No claim of awareness.

Self(t) is testable by external behavioral measurement.

A thermostat has Self(t) = [setpoint, current_temp, history].

A human has a richer Self(t).

The construct is the same.

---

## Relation to APC

APC consolidates into M_param.

Self draws from M_param and M_ep.

Self conditions:

- which traces R samples (weighted by goal alignment)
- which mutations U_rec considers valid
- which consolidations V passes

Self is a top-down constraint on the dream cycle.

Without Self:

dream cycle is undirected.

With Self:

dream cycle is goal-conditioned.

---

## Prediction

Systems with Self(t) outperform Self-less baselines on:

- goal persistence across long episodes
- behavioral consistency across task switches
- adaptation quality (returns to baseline competence faster after distribution shift)

---

## Metric

goal_persistence:     fraction of episodes where G(0) goal still pursued at t_end

behavioral_consistency: variance of action distribution given similar inputs

adaptation_quality:    recovery time after distribution shift

---

## Failure

Any of:

- no measurable improvement on metrics
- Self drift exceeds σ during normal operation
- Self causes rigid behavior (adaptation_quality worsens)

The third failure is the interesting one.

Self that is too stable becomes a liability.

There exists an optimal σ.

---

## Open

- How to initialize Self(0)
- How H is compressed
- Whether B is separate from M_param
- Interaction with multi-agent settings (Self of A modeling Self of B)
