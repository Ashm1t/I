# VALIDATION PROTOCOL

## Purpose

Define the pipeline for moving findings from research to validated status.

## Flow

```
research (proposal)
  → main (implementation)
  → master (validated finding)
```

## Rules

1. **Validated findings only** — no speculative content enters master.
2. **Preserve failures** — experiments that refute a hypothesis are valuable and must be retained.
3. **No speculative validation** — every entry in validated/ must be backed by implementation and metrics.

## Process

| Step | Stage | Action |
|------|-------|--------|
| 1 | research | Hypothesis proposed, architecture defined |
| 2 | main | Implementation built, experiment runs |
| 3 | review | Results evaluated against metrics |
| 4 | master | Finding promoted only if validated |

## Structure

Each validated finding includes:
- Original hypothesis ID
- Claim tested
- Implementation reference
- Metric results
- Failure conditions (if any)
- Date of validation
