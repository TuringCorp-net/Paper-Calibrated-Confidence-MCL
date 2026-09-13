# Data

This directory holds the aggregate results behind the paper's tables, in a form that can
be checked against the published numbers.

## Published here

| File (to be added as sections are finalised) | Contents |
|---|---|
| `profbench-summary.csv` | task-level scores for the collaborative generator, the direct baseline and the official reference draft, per domain |
| `judge-calibration.csv` | confidence bands against observed accuracy, with the count in each band |
| `judge-benchmarks.csv` | JudgeBench and CJB per-split accuracy for the collaborative judge and the baseline |
| `selective-judgment.csv` | coverage and accuracy at each confidence threshold, per benchmark and per task family |
| `order-swap.csv` | the order-invariance control, task by task |
| `arbitration.csv` | the rubric-blind preference comparison, task by task |

Every table is aggregate: counts, rates and band statistics. Each carries the number of
items it was computed from, and the exclusions described in the paper are reflected in
those counts rather than silently dropped.

## Deliberately not published

- **Benchmark contents.** ProfBench, JudgeBench and ContextualJudgeBench are
  third-party datasets with their own licences. The paper links to them; their
  questions, reference answers and per-item labels are not reproduced here.
- **Raw per-call logs.** Per-item model outputs, per-call metering records and provider
  billing records are not published. They are operational records rather than results,
  and the aggregate tables above carry every number the paper reports.
- **Internal configuration.** Member selection, coordination depth, prompts and
  parameterisation of the operating points are out of scope for this paper; all
  reported measurements are of externally observable behaviour through the public
  interfaces.

## Reproducing a table

Scripts that regenerate each table from the aggregate inputs live alongside them and are
added with the sections they support. Where a table depends on third-party data, the
script reads the official download rather than a redistributed copy.
