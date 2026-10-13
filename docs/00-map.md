# 00. The architecture of the proof on one page

## The statement

Theorem 1.1: there is one constant `C` such that every finite planar graph metric `d_G` embeds in `L1` with distortion at most `C`:
`d_G(x,y) ≤ ‖f(x) − f(y)‖₁ ≤ C·d_G(x,y)`. (Corollary: a uniform bound on the flow–cut gap for planar graphs, via Gupta–Newman–Rabinovich–Sinclair.)

An `L1` embedding is the same as a nonnegative combination of cut metrics `δ_S`. So the proof builds **a random family of cuts** whose total weight (i) never charges an edge more than a constant times its length and (ii) separates every pair in proportion to its distance.

## The one idea, in four moves

1. **Columns (§2).** Replace the plane graph by vertical lines ("columns") with zero-cost "switches" between them at chosen heights. Height = distance from a root in a shortest-path tree. The plane embedding gives a *circular order* of columns in which the switches do not cross. All planarity is used through this order.
2. **A structure that makes the upper bound automatic (§3).** Give every point `v` a set of labels `A_v = {ω : Z(ω) < h(v) + σ(ω)·κ·P(v)}`. If these sets grow with height along each column and agree at switches, then every cut distance is at most the length of every path. The upper bound `‖f(x)−f(y)‖ ≤ C·d` is therefore *invariant*: it survives any number of updates, if each update obeys *exact gluing*.
3. **Random local updates at decreasing scales give the lower bound (§5–§8).** At scale `r` try to separate pairs at distance in `[r, 2r)`. Two systems, **A** and **B**, each with local update rules, are run in a random mixture of four modes. One of the two always has a positive chance of separating a given "eligible" pair, by a case analysis:
   * main update in A raises the field at one endpoint, **or** the failure to raise supplies a *descending path* (§6.1);
   * a low *tip* of a switching link separates the pair by a component certificate (§6.2); **or**
   * the pair's endpoints are *seeds*; only boundedly many seed *groups* meet a small ball (§6.3 packing); a secondary clipping in B separates them (§8.1); **or**
   * if clipping fails in both orientations, the fixed ordered part of the field rises and falls along short paths, which by a topological argument (§7) puts the endpoints on *opposite arcs* of the circle, where a transverse increment separates them (§8.2).
4. **A schedule that keeps the gains (§9).** Successive scales differ by a large factor `Q`. Coarser scales rarely destroy the "same chart" condition a pair needs (probability `O(ρ)` per scale, geometric sum), and finer scales move labels too little to erase the separation already gained. Averaging over `m` interleaved schedules covers every distance. Result: `pb/(8m) · d ≤ ‖F(x)−F(y)‖ ≤ 2d`, so `C = 16m/(pb)`.

## Dependency map

```
§2 columns, circular order, portals, cells  ───────────────┐
        │                                                   │
        ▼                                                   ▼
§3 charts, exact gluing, component refinement      §4 interpolation theorem 4.1, Cor 4.6
        │                      │                            │
        │                      ▼                            │
        │          §5 constants and one step                │
        │                      │                            │
        ▼                      ▼                            ▼
§6.1 main update ──► §6.2 seeds ──► §6.3 packing ──┐   (all probability estimates)
                                                   ▼
§7 ordered fields, transverse field ──► §8 secondary update and increment
                                                   │
                                                   ▼
                                  §9 one-step estimates, chart persistence, schedule
                                                   │
                                                   ▼
                          Theorem 1.1  ──►  §10 almost-embeddable families (needs the bounded-treewidth companion)
```

## Where each of Hung Le's log entries lands

| His log (2026) | What he read | These notes |
|---|---|---|
| Oct 7 | first 12 pages: the non-crossing column model | 01 (and 02 for the first part of §3) |
| Oct 8 | early lemmas straightforward; §3 introduces the "chart" he found hard | **02** |
| Oct 9 | §3 lemmas are reformulations; Theorem 4.1 read, §4 proof skipped | 03 |
| Oct 10 | Corollary 4.6 "clever"; §5 "vague" | 03 (4.6), **04** |
| Oct 11 | reread §5, started §6.1; thinks §6–8 are the main arguments | 04, **05**, 06, 07, 08 |

## What this proof does *not* give

* It gives existence of `C`, not a usable value: with the paper's constants the packing number is about `1.6×10⁹` and `p` is about `2^(−3.2×10⁹)` (see [11](11-glossary-constants.md)). That is not a criticism, just what to expect.
* It does **not** prove closure under general clique sums, so it does not prove the full GNRS conjecture (the paper says so, §1.2 and after Corollary 10.1).
* Corollary 10.1 (almost-embeddable families) also needs a second preprint, the bounded-treewidth companion, which these notes do not cover.
