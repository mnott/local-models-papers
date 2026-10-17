# Local Model Workers — Lab Report Series

Measured experiments running agentic coding workers on local open-weight models,
on one Apple workstation (M5 Max, 128 GB unified memory), against cloud yardsticks.
Every number in these reports comes from a run on real tasks with recorded logs;
nothing is estimated.

## Papers

| # | Date | Title | Status | PDF |
|---|------|-------|--------|-----|
| 1 | 2026-10-15 | Can open-weight local models act as the workers in an agentic coding workflow? | lab report | [paper.pdf](papers/2026-10-15-local-model-workers/paper.pdf) |
| 2 | 2026-10-16 | Can a local coding setup run beside normal work? (serving stack, prompt shape, harness repair) | lab report | [paper2.pdf](papers/2026-10-16-serving-and-harness/paper2.pdf) |
| 3 | 2026-10-17 | Quantisation, serving and harness repair: what it takes to run a local coder beside real work | lab report — numbers pending daylight build verification | [paper3.pdf](papers/2026-10-17-quant-and-ssd/paper3.pdf) |

Each directory holds the LaTeX source, the compiled PDF and the shared bibliography.

## Findings in one line each

1. **Paper 1**: No for real application fixes at night-1 state — the local models find
   the code only when the task names the file and function.
2. **Paper 2**: The bottleneck was the serving stack, not the model — fixing the
   prefix-cache path took a local model from unusable to ~2× Sonnet wall time on
   one-function fixes; the harness itself needs repair hooks (path repair) for
   local models to function at all.
3. **Paper 3**: Quant lift replicates across families (4-bit→8-bit: 4/6→5/6 on two
   families); a 30B-A3B at 8-bit delivers rank-1 quality at half the resident memory;
   SSD-paged 125B-class models complete real tasks at ~3 tok/s — paging, not the
   model, is the limit; the remaining failure classes (invented paths, dotted tool
   names) are model-side and partly harness-repairable.

## Method notes

- Suite: paired A/B arms on replayed real fixes with known answers; buildless
  diff-grading during runs, build-verified verdicts in a separate daylight pass.
- Machine: one 128 GB M5 Max, one model server at a time, memory watchdog.
- Replication rule: no single-run verdicts.
- Instrumentation: PAI (open source), runs recorded in the reports.

## Plans

- arXiv submission of the series once the daylight build-verification pass
  confirms paper 3's rankings.
