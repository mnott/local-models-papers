# arXiv submission plan (prepared, not submitted)

## Target
- Category: cs.LG (primary), cs.SE (cross-list) — empirical ML systems work
- Type: paper 3 standalone first ("Quantisation, serving and harness repair..."),
  papers 1-2 later as companion lab reports if wanted.

## Blocking condition
Paper 3's ranking rests partly on diff-level `check` verdicts. The daylight
build-verification pass (grade.sh on local30x8 + ornith8 log-size/box-press arms)
must confirm before submission. Tracked as the first post-night task.

## Per-submission checklist
1. Verify numbers: build-graded verdicts match rows/rows-diff; spot-check every
   number in the tex against night3-results.md.
2. arXiv metadata: title, abstract (rewrite from intro), author Matthias Nott
   (affiliation + email decision is the operator's).
3. Source package: tex + bbl (arXiv compiles bbl itself — no bst run needed
   there) + figures; NO .fdb_latexmk/build cruft; single Bibliography.bib is
   fine but bbl must be embedded.
4. License: default arXiv non-exclusive (operator decision: CC-BY vs arXiv-only).
5. Submit as new submission; lab-report series note in the comments field
   ("third in a series of lab reports, prior reports available at
   github.com/mnott/local-models-papers").

## Prepared artifacts
- papers/2026-10-17-quant-and-ssd/paper3.tex + paper3.pdf (source of truth)
- This repo's tags give per-paper immutable snapshots for citation.
