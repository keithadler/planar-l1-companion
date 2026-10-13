# Companion notes: "Planar Graph Metrics Embed into L1 with Constant Distortion"

A section-by-section breakdown of OpenAI's preprint (23 September 2026), written to support **a human reader's own verification**:

> https://github.com/openai/math/blob/main/preprints/Planar-Graph-Metrics-Embed-into-L1-with-Constant-Distortion-September-23-2026/paper.pdf

It was prompted by Hung Le's public reading log of the paper (*Rambling on Graphs*, "OpenAI Math Dump Hits My Home", 7–11 Oct 2026).

## Please read this first

* **These notes are unverified.** They were written by Claude (an AI) working for Keith Adler, from a close reading of the PDF. No domain expert has checked them. Treat everything here as a second reader's *questions and summaries*, never as a claim that a step is right or wrong.
* **Keith is not sure this helps.** If it saves a reader even a little time on any one lemma, it was worth publishing; if it doesn't, ignore it. The point is to support human verification, not to replace it.
* **Nothing here says the paper's theorem is true or false.** Where a computation was checked by hand, the note says so; everything else is "as stated in the paper".
* The paper has 45 pages (the blog says the expanded version is longer). Page and equation numbers below are the paper's own.

## Status: work in progress

Written so far: this README, [the map](docs/00-map.md), [§2 columns and bands](docs/01-columns-and-bands.md), and four summary cards in [`images/`](images/). The remaining documents in the table below are being written and will be added as they are finished; rows marked *(coming)* do not exist yet.

![How the proof is built](images/1-four-moves.png)

## How to use these notes

Start with [`docs/00-map.md`](docs/00-map.md) (the architecture of the proof on one page), then read the part you are stuck on:

| Doc | Paper | One line |
|---|---|---|
| [01 columns and bands](docs/01-columns-and-bands.md) | §2 | The plane graph becomes vertical columns; circular order, portals, cells |
| *(coming)* [02 charts](docs/02-charts.md) | §3 | The label sets `{Z < h + σκP}`; why charts exist; exact gluing; component refinement |
| *(coming)* [03 interpolation](docs/03-interpolation.md) | §4 | Theorem 4.1: approximating a field by `c ± d(k,·)` with a few "named atoms" |
| *(coming)* [04 scales and steps](docs/04-scales-and-steps.md) | §5 | The constants hierarchy, the schedules, what one step does |
| *(coming)* [05 the main update](docs/05-main-update.md) | §6.1–6.2 | The raise-or-descend dichotomy; the low-tip certificate; the seeds |
| *(coming)* [06 packing](docs/06-packing.md) | §6.3 | Why only boundedly many seed groups meet a small ball |
| *(coming)* [07 ordered fields](docs/07-ordered-fields.md) | §7 | Ordered fields, the transverse field `t_s`, the two-arcs argument |
| *(coming)* [08 the secondary update](docs/08-secondary-update.md) | §8 | Clipping near admitted seeds; the ordered increment |
| *(coming)* [09 assembly](docs/09-assembly.md) | §9–10 | One-step estimates, the schedule, the final map and the constant |
| *(coming)* [10 where to look hardest](docs/10-where-to-look.md) | all | Load-bearing steps, questions, and an honest confidence table |
| *(coming)* [11 glossary and constants](docs/11-glossary-constants.md) | all | Symbols, parameters, and the numbers |
| *(coming)* [12 Lean status](docs/12-lean-status.md) | §3.2 etc. | What has been machine-checked so far, and what it does and does not mean |

## Provenance and licence

The notes paraphrase and summarise the paper; they quote only short formulas. The paper is OpenAI's. These notes are released under the MIT licence. Corrections are welcome: open an issue or a pull request.
