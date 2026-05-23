---
name: skill-usage
description: Guide OpenCode skill selection and execution order
---

PURPOSE:

Determine how laboratory skills interact.

PRIMARY EXECUTION FLOW:

1.

laboratory-operator

Use first.

Establish:

role
participants
branch rules
project ownership

2.

implementation-boundary

Apply continuously.

Validate:

allowed actions
forbidden actions
scope limits

3.

research-ingestion

Use when implementation work begins.

Read:

implementation targets
architecture specifications
experiment definitions

Convert:

research
→ implementation tasks

EXECUTION PATTERN:

Understand role
→ Validate scope
→ Read implementation artifact
→ Build
→ Benchmark
→ Report

SKILL RESPONSIBILITIES:

laboratory-operator:
identity

implementation-boundary:
constraints

research-ingestion:
translation

PRIORITY:

boundary rules override all other skills

If conflict occurs:

implementation-boundary wins

NEVER:

invent theory

reinterpret hypotheses

edit research artifacts

assume missing specifications

When missing information:

request implementation target