# 00. Architecture of the proof

Status tags: **[stated]** as in the paper; **[hand]** re-derived here; **[Lean]** machine-checked under listed hypotheses. See the [README](../README.md).

## 0.1 Reduction to cuts

An embedding $f:V\to L_1$ with $\|f(x)-f(y)\|_1=\sum_{\emptyset\neq S\subsetneq V} w_S\,|\mathbf 1_S(x)-\mathbf 1_S(y)|$, $w_S\ge 0$, is the same thing as a nonnegative combination of cut pseudometrics $\delta_S$ (paper §1.1). The construction therefore produces a random family of cuts whose total weight (i) charges each edge at most $O(1)$ times its length (upper bound) and (ii) separates each pair $(x,y)$ in expectation by $\Omega(d_G(x,y))$ (lower bound). **[stated]**

## 0.2 The four steps

**Step 1 (columns, §2).** A plane graph $G$ with root $o$ and a shortest-path tree $T$ is replaced by a *column model*: one copy $\{i\}\times\mathbb R$ of the height line per index $i$ of a cyclically ordered finite set, identified along closed bounded switch sets $S_{ij}\subset\mathbb R$, with *noncrossing* links and *terminal* tips (Definition 2.1). Heights are $h(v)=d_G(o,v)$. Planarity enters only through the cyclic order. (Proposition 2.3.) **[stated]**

**Step 2 (an invariant that gives the upper bound, §3).** Assign to each point $v$ a measurable $A_v\subset\Omega$ of labels. If (a) $A$ is nested increasingly along each column, (b) $A_{(i,H)}=A_{(j,H)}$ for $H\in S_{ij}$, and (c) $\mu(A_p\triangle A_q)\le$ vertical length along any column segment, then $\mu(A_p\triangle A_q)\le d(p,q)$ for all $p,q$. The paper realises (a)–(c) by
$$A_v=\{\omega=(Z,\sigma):\ Z(\omega)<h(v)+\sigma(\omega)\,\kappa\,P(v)\},\qquad \kappa\,\mathrm{Lip}_{\mathrm{vert}}(P)<1,$$
and proves that updates of the form $P\mapsto\max(P,\text{proposal})$, where the proposal lies strictly below $P$ on the boundary of its domain, preserve (a)–(c) (*exact gluing*, §3.2). **[stated]**; the identity $\mu(A_v\triangle A_w)=\max\{|h(v)-h(w)|,\kappa|P(v)-P(w)|\}$ is **[hand]**; exact gluing is **[Lean]** under the hypotheses in [12](12-lean-status.md).

**Step 3 (random local updates, §4–§8).** At a scale $r$ one tries to separate pairs $\{x,y\}$ with $d(x,y)\in[r,2r)$. Two systems, $A$ and $B$, are used; one step is one of four equally likely modes: no change, a main update in $A$, secondary clipping in $B$, an ordered increment in $B$. For a pair that is *eligible* (both radius-5 balls lie in one chart region in each system) the paper proves, by a case analysis, that with probability at least $p>0$ the pair acquires a separation certificate of size $\ge br$:

| Case | Mechanism | Where |
|---|---|---|
| an endpoint has no descending path | the main update raises the field there | Lemma 6.3, Cor. 6.4 |
| a non-neighbour link with low inactive tip separates the pair | component certificate in $A$ | Lemma 3.2, Lemma 6.5 |
| otherwise the endpoints are *seeds*; at most $M_{\mathrm{pack}}$ seed groups meet a ball | secondary clipping in $B$ at an admitted seed | Prop. 6.6, Lemma 8.2 |
| clipping fails in both orientations | the ordered part of the field rises and falls on short paths, forcing the endpoints onto opposite arcs of the circle, where a transverse increment separates them | Lemmas 7.6, 8.4 |

**Step 4 (scales and assembly, §9).** For a scale ratio $Q=2^m$ large, a ball $B_d(x,20r_f)$ that lies in one chart at a coarser scale $r$ is split with probability $\le 40C_0\,r_f/r$ (Proposition 9.2); the geometric sum is $<\tfrac12$. Subsequent finer scales move any set by $\le M r_f/(Q-1)$ in total. Mixing over $m$ residue-class schedules and subtracting a reference vertex yields $F$ with
$$\tfrac{pb}{8m}\,d(x,y)\le\|F(x)-F(y)\|_1\le 2\,d(x,y),\qquad C=\tfrac{16m}{pb}.$$
**[stated]**

## 0.3 Dependency graph

```
§2 columns, circular order, portals, cells ─────────────────┐
      │                                                       │
      ▼                                                       ▼
§3 charts, exact gluing, Lemma 3.2        §4 Thm 4.1, Lemma 4.5, Cor. 4.6
      │                │                                      │
      │                ▼                                      │
      │       §5 constants and the step                       │
      ▼                │                                      ▼
§6.1 main update ─► §6.2 seeds ─► §6.3 packing ─► (all probability estimates)
                                      │
§7 ordered fields, $t_s$, two arcs ──►§8 secondary update, increments
                                      │
                                      ▼
                    §9 estimates, schedule, final map  ──►  Theorem 1.1
                                      │
                                      ▼
                    §10 almost-embeddable families (also needs the bounded-treewidth companion)
```

## 0.4 Correspondence with the reading log

| Log entry | Content read | Note |
|---|---|---|
| 7 Oct | first 12 pages: the column model | [01](01-columns-and-bands.md), part of 02 |
| 8 Oct | early lemmas; §3 "chart" | 02 |
| 9 Oct | §3 lemmas; Thm 4.1 | 02, 03 |
| 10 Oct | Cor. 4.6; §5 | 03, 04 |
| 11 Oct | §5, start of §6.1; §6–8 expected to be the core | 04–08 |

## 0.5 What the argument does not give

* A usable constant. With $R=10^{-8}$, $g=10^{-14}$: $M_{\mathrm{pack}}=2+\lceil1600R/g\rceil\approx1.6\times10^{9}$ and $p=2^{-(2M_{\mathrm{pack}}+10)}\approx2^{-3.2\times10^{9}}$ (Proposition 9.1). The theorem is one of existence.
* Closure under clique-sums, hence the full GNRS conjecture (§1.2, after Corollary 10.1).
* Corollary 10.1 additionally depends on a second OpenAI preprint (bounded treewidth), not covered here.
