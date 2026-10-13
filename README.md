# Companion notes on *Planar Graph Metrics Embed into $L_1$ with Constant Distortion*

Section-by-section notes on the OpenAI preprint of 23 September 2026 ([PDF](https://github.com/openai/math/blob/main/preprints/Planar-Graph-Metrics-Embed-into-L1-with-Constant-Distortion-September-23-2026/paper.pdf)), written to support **a human reader's own verification**. They were prompted by Hung Le's public reading log ([*Rambling on Graphs*, "OpenAI Math Dump Hits My Home"](https://minorfree.github.io/OpenAIDump/), 7–11 October 2026).

## Standing of these notes

* **Unverified.** Written by Claude (an AI) for Keith Adler from a close reading of the PDF. No domain expert has checked them. Every item below carries one of three status tags:
  * **[stated]**: as stated or proved in the paper; reproduced here, not independently checked;
  * **[hand]**: a computation re-derived by the note's author;
  * **[Lean]**: machine-checked in Lean 4 / Mathlib, *under the hypotheses listed*, in the sibling repository [`planar-l1-lean`](https://github.com/keithadler/planar-l1-lean) (status in [12](docs/12-lean-status.md)). A Lean check establishes that a *formalised statement* follows from *stated hypotheses*; it does not establish that those hypotheses or that statement are the paper's.
* **No verdict on the main theorem is given or implied.**
* Keith Adler is not certain these notes help. They are offered because they may save a reader time on a single lemma; they are not a substitute for reading the paper.
* Numbering (Definition, Lemma, Proposition, equation) is the paper's own. The paper is 45 pages.

## The result

> **Theorem 1.1 (paper).** There is a universal constant $C\ge 1$ such that for every finite connected planar graph $G=(V,E)$ with positive edge lengths there are a measure space $(\Omega,\mathcal F,\mu)$ and $f:V\to L_1(\Omega,\mathcal F,\mu;\mathbb R)$ with
> $$d_G(x,y)\le \|f(x)-f(y)\|_1\le C\,d_G(x,y)\qquad(x,y\in V).$$

Equivalently, the flow–cut gap of planar graphs is uniformly bounded (via Gupta–Newman–Rabinovich–Sinclair). It settles the planar case of the GNRS conjecture; closure under clique-sums, hence the full conjecture, is **not** claimed.

![The four moves](images/1-four-moves.png)

## Contents

| Note | Paper | Subject |
|---|---|---|
| [00 map](docs/00-map.md) | all | Architecture, dependency graph, and the correspondence with the reading log |
| [01 columns and bands](docs/01-columns-and-bands.md) | §2 | Column models, the circular order, portals, radial cells |
| [02 charts](docs/02-charts.md) | §3 | Threshold sets $\{Z<h+\sigma\kappa P\}$, charts, exact gluing, component refinement |
| *(in progress)* 03 interpolation | §4 | Theorem 4.1 and Corollary 4.6 |
| *(in progress)* 04 scales and steps | §5 | Constant hierarchy, schedules, the step |
| *(in progress)* 05 the main update | §6.1–6.2 | Raise-or-descend, low-tip certificates, seeds |
| *(in progress)* 06 packing | §6.3 | Proposition 6.6 |
| *(in progress)* 07 ordered fields | §7 | Ordered fields, transverse coordinate, two arcs |
| *(in progress)* 08 secondary update | §8 | Clipping near admitted seeds; ordered increments |
| *(in progress)* 09 assembly | §9–10 | One-step estimates, chart persistence, the schedule, the constant |
| *(in progress)* 10 where to look | all | Load-bearing steps and precise questions |
| *(in progress)* 11 glossary | all | Symbols and parameters |
| *(in progress)* 12 Lean status | §3 | What is machine-checked, with hypotheses |

Notes marked *(in progress)* are being written and are added as they are finished.

## Licence

Copyright 2026 Keith Adler. Licensed under the [Apache License, Version 2.0](LICENSE), the licence Mathlib uses, so the notes and any Lean material can be combined with it freely. The paper itself is OpenAI's; these notes paraphrase it and quote only short formulas. Corrections are welcome as issues or pull requests.
