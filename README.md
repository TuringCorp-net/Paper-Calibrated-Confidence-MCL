# Paper: Cross-Model Confidence in the MCL Framework

**Cross-Model Confidence in the MCL Framework: Calibrated Uncertainty for Selective Judgment**

Preprint (work in progress). Author: Li Zhang. Affiliation: TuringCorp.

> **Status: framework v0.1.** The section structure, the evaluation protocol and the
> results that are already measured are in place. One planned experiment — eliciting
> self-reported confidence from a single model on the same judged items, to contrast it
> with cross-model confidence — is not run yet; those subsections are marked
> `[pending]` in the LaTeX source and carry no numbers.

## What this paper studies

A single model answers, and when asked reports a confidence about its own answer. That
signal is introspective: nothing external checks it. This paper studies the alternative
produced by the **Meta-Coordination Layer (MCL)** framework, in which several
heterogeneous models generate and cross-examine independently and an arbitration step
selects among the resulting candidates — emitting a confidence with every decision.

The framework is studied through its two deployed instantiations, and the paper treats
them as two sides of one mechanism:

- **generation** — a collaborative system that returns a complete deliverable (content
  plus the reasoning it states for it), evaluated on **ProfBench**;
- **judgment** — an arbitration system that, given a task and two candidate answers,
  returns the better option with a calibrated confidence, evaluated on **JudgeBench**
  and **ContextualJudgeBench (CJB)**.

## Questions

1. Is cross-model confidence calibrated against outcomes?
2. Does it support **selective judgment** — and how much accuracy does a confidence
   threshold actually buy at what coverage?
3. Where does the signal hold and where does it degrade?
4. Is the collaborative decision invariant to presentation order, and how does it
   compare with a single model used as a judge?
5. On questions with no single correct answer, does preference-based judgment separate
   systems differently from rubric scoring?

## Files

```
paper/main.tex              LaTeX source (compile with pdfLaTeX)
data/README.md              what is published here, and what is not
CITATION.cff                citation metadata (DOI added on preprint release)
LICENSE-CC-BY-4.0.md        license
```

## Evaluated on public benchmarks

The benchmarks are third-party and public; this repository links to them and does not
redistribute their contents.

- **ProfBench** — 40 expert-level tasks, ten each in Physics PhD, Chemistry PhD,
  Finance MBA and Consulting MBA, scored criterion by criterion against an official
  rubric. NVIDIA. <https://huggingface.co/datasets/nvidia/ProfBench>
- **JudgeBench** — 620 judgment pairs across knowledge, reasoning, mathematics and code
  items.
- **ContextualJudgeBench (CJB)** — Salesforce; full official set of 2,000 pairs across
  all 8 splits.

## Results already measured

Aggregate numbers, all from our own runs on the official protocols, with failures and
exclusions disclosed. Per-criterion and per-band tables are added under `data/` as the
paper is written.

- **Judgment accuracy.** JudgeBench 92.5% (568/614) against 92.7% for a direct
  direct call to DeepSeek V4 Flash on the same judged set — the raw pick rate ties. CJB 67.1%
  (1,336/1,991 pairs, consistent accuracy, random floor 25%) against 65.4% for the
  baseline on the same judged set.
- **Calibration.** JudgeBench confidence bands (share of judgments, observed accuracy):
  ≥90% — 45.6%, 99.6%; 80–90% — 29.7%, 94.0%; 70–80% — 13.2%, 84.1%; <70% — 10.5%,
  67.7%. CJB bands: 83.3% / 76.4% / 63.6% / 55.4%.
- **Generation.** ProfBench, same judging pipeline, same 38 tasks: collaborative 63.3,
  DeepSeek V4 Flash called directly 57.4, official o3 draft 55.6. Judge calibration against official
  per-criterion labels: 74.0% agreement, F1 0.761.
- **Order invariance.** Swapping the two candidates between the two option positions
  on a 10-task sample kept the same pick in 10 of 10 cases.

## What we do not claim

This paper does not claim that collaboration is more accurate than a single model in
general, nor that its confidence is a substitute for domain review. It measures where
the confidence signal carries information and where it does not, and reports the
comparisons in which the collaborative system does not come out ahead.

## Open items

- Naming of the baseline model in the main text is pending a disclosure review.
- The single-model self-reported confidence comparison is planned; until it is run,
  the abstract reports only measured values.

## Related preprints

- MCL conceptual framework — <https://doi.org/10.6084/m9.figshare.30645869>
- MCL-Team: minimal multi-model collaboration — <https://doi.org/10.6084/m9.figshare.32824352>
- Exploring Execution-Form Boundaries in Brain–Cerebellum Collaboration —
  <https://doi.org/10.6084/m9.figshare.33413569>

## License

CC BY 4.0 — see `LICENSE-CC-BY-4.0.md`.
