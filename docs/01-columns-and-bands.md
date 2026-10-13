# 01. Columns, circular order, portals and cells (paper §2)

*Status: summary of the paper's statements. Proofs read, not independently checked.*

## Definition 2.1: the column model

* A finite **cyclically ordered** set of indices `V₀`; for each index `i` a copy `{i} × ℝ` of the real line (the "column").
* A finite set of **links** `ij`, each with a closed bounded set `S_ij ⊂ ℝ` of **switch heights**: at `H ∈ S_ij` the points `(i,H)` and `(j,H)` are identified. The quotient is `X`, with a height function `h`.
* A **path** is a finite concatenation of vertical segments and switches; its length is the sum of the vertical lengths (switches are free). `d` = infimum of path lengths.
* **Noncrossing links:** no two links have four distinct endpoints alternating in the cyclic order.
* **Terminal switches:** every link between *non-consecutive* indices is a single switch at one height `H_e` (its **tip**), and neither endpoint column has any switch *above* `H_e`.
* For a closed height interval `I`: `X_I = h⁻¹(I)`, `d_I` the intrinsic distance (paths staying in `I`), and `G_I` the *active column graph* (indices, with links whose switch sets meet `I`).

## Proposition 2.3: every planar graph is a column model

Fix a plane embedding and a root `o`; let `T` be a shortest-path tree and `h(v) = d_G(o,v)`.

* Each **non-tree edge** `e = uv` of length `ℓ_e` is replaced by two new branches ("twigs"): one attached to `u` of length `(ℓ_e + h(v) − h(u))/2`, one to `v` of length `(ℓ_e + h(u) − h(v))/2`. Both are `≥ 0` because `|h(u)−h(v)| ≤ ℓ_e`. Their tips have the same height `H_e = (ℓ_e + h(u) + h(v))/2` and are identified. Total length `ℓ_e`: the metric is recovered exactly.
* One column per root-to-leaf path of the enlarged tree, in the cyclic contour order of the plane leaves; neighbouring leaves are linked at the heights of their common root prefix.
* Noncrossing: the tip links are disjoint arcs in the complementary disk, and two disjoint arcs in a disk cannot have alternating endpoints. The prefix links join cyclic neighbours.
* Figure 1 of the paper is a worked example with `ℓ_e = 3`, `h(u) = 2`, `h(v) = 3`: twig lengths 2 and 1, tips at height 4.

**Why this matters later:** a non-neighbour link (a *chord* of the circle) is always a single tip switch. That single height is what makes the "inactive tip" certificate in §3.2/§6.2 meaningful.

## 2.1 Consequences of the circular order

All of these are about the column *graph*, so they hold for every height band simultaneously.

| Lemma | Content |
|---|---|
| 2.4 Chord separation | In a noncrossing circular graph, any path from the strict interior of one `u–v` arc to the strict interior of the other visits `u` or `v`. (Otherwise an edge with endpoints in the two interiors would alternate with `u,v`.) |
| 2.5 Gaps | Every path avoiding a connected vertex set `S` lies in one open circular gap between consecutive vertices of `S`. |
| 2.6 Skipping a column | A walk in an open arc that passes "over" index `i` either visits `i` or uses an edge with endpoints strictly on both sides of `i`, which is then a non-neighbour link; a second path starting strictly inside that link's interval and leaving it visits an endpoint. |
| 2.7 Outerplanarity | Every `G_I` is outerplanar with no `K₂,₃` minor (cone over `K₂,₃` would contain `K₃,₃`; a simple planar bipartite graph on 6 vertices has at most 8 edges, `K₃,₃` has 9). |
| 2.8 Connected sublevels | Sublevel sets `{i : d_I(o,(i,H)) ≤ t}` are connected in `G_I`. (Move any shortest path's visited columns vertically to height `H`; this does not increase the radial value.) |

## 2.2 Portals and radial cells

Work in a closed band `J` of width `a` with midheight `H*`; pick a basepoint `o`; the **radial coordinate** of column `i` is `b_i = d_J(o,(i,H*))`. Two facts: `d_J(o,v) − b_i ≤ a/2` and `|b_i − b_j| ≤ a` for linked `i,j` (eq. (2)).

* **Lemma 2.9 (two portals).** Let `C` be a component of the subgraph induced by `{i : b_i ≥ t}`. An *entrance column* is one adjacent to a column with value below `t`. There are at most **two** points ("portals") such that every point on every entrance column is within `200a` (in `d_J`) of one of them; each portal has radial value in `[t, t+a)`. *Proof idea:* three entrance points pairwise `>100a` apart would give three vertex-disjoint connectors from `C` to the connected low set `L`; contracting gives a `K₂,₃` minor, contradicting 2.7 (Figure 2).
* **Definition 2.10 (radial cells).** Cut the column indices into **layers** `[θ + nD, θ + (n+1)D)` by radial value, split each layer into connected components: a **cell**. Its **frontier** `∂C` is the part of the cell with an active link to a column outside it. Two cells sharing a quotient point both have that point in their frontier.
* **Lemma 2.11 (diameter).** If `a ≤ D/1000`, every cell is compact, path-connected, with weak diameter `≤ 10D` in `d_J` (it lies in the union of two balls of radius `D + 210a` around the portals).
* **Lemma 2.12 (padding).** If the radial value of `v` is more than `ρ + 2a` from the threshold set `T = θ + Dℤ`, then every point within band-path length `ρ` of `v` has all representatives in the same cell, and `d_J(v, ∂C) > ρ`. For uniform `θ ∈ [0,D)` this fails with probability at most `min{1, 2(ρ+2a)/D}`. Numerical corollary: with `a ≤ D/1000` and radial values more than `0.02D` from the thresholds, the distance to the frontier is `> 0.01D`.
* **Lemma 2.13 (successive portal levels).** With step `δ > 1000a`, components of `{b_i ≥ nδ}` form a rooted tree; portals of successive levels are within `δ + 220a` and at least `δ − 10a` apart. This is the geometry behind the interpolation in §4.

## What to check as a reader

* Lemma 2.9: is "three portals at pairwise distance >100a" really contradicting `K₂,₃`-freeness? The trimming step (each connector has a nonempty interior because radial values differ by at least `12a − a/2 > a` while adjacent columns differ by at most `a`) is where I would look.
* Lemma 2.11/2.12: the constants `10D`, `0.01D` feed directly into the numerical choices in §5.
* The paper says (§2 intro) that the estimates are independent of the number of columns; this holds because every constant above depends only on `a, D, δ`.
