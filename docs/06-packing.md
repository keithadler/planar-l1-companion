# 06. The packing bound for seed groups (paper §6.3)

Tags as in the [README](../README.md). **[stated]** unless tagged.

**Purpose.** The secondary update (§8) can act on a small ball only through the groups of seeds meeting it. Proposition 6.6 bounds their number by a constant independent of the graph, the number of columns and the history. This gives (a) a lower bound $2^{-(2M_{\mathrm{pack}}+1)}$ on the chance of isolating one group's proposal at a pair (Lemma 8.2), and (b) a bounded number of competing interpolation families on a ball (Proposition 9.2).

## 6.1 Statement

**Proposition 6.6 (restricted packing bound).** Fix a narrow band $J_2$. In any component of $X_{J_2}$, every closed $d_{J_2}$-ball of radius $4R$ meets seeds from at most
$$M_{\mathrm{pack}}=2+\Big\lceil\frac{1600R}{g}\Big\rceil\tag{30}$$
groups.

Remark 6.7 (as stated): the conclusion concerns seeds of surviving witness pairs; it does *not* assert bounded overlap of all broad-band cells or of their neighbourhoods. Padded cells separate the chosen seeds, and exclusion of the component barrier (Lemma 6.5) brings those seeds close to two short paths.

## 6.2 Proof, step by step

Let $B$ be a closed $d_{J_2}$-ball of radius $4R$ with centre $z$ containing a seed $w_*$.

**(i) One band, one chart.** Only a narrow band contained in a broad band can contain seeds, so the broad band $J_1\supseteq J_2$ is unique and the $J_2$-paths from $z$ to the seeds show all seeds lie in one $J_1$-component. Since $d(z,w)\le4R<5$ for every seed $w$ of $B$, $z$ lies in the common chart of $w$'s eligible witness pair; charts partition $X$, so all seeds of $B$ have the same chart identifier in each system. Write $I$ for the common old $A$-band and $s=d_I(o,\cdot)$ for its distance field. All center-to-seed paths of length $\le4R$, all descending witness paths (length $\le0.02$), and the vertical connectors (length $\le a_1$) lie in the old chart band, hence $J_1\subset I$.

**(ii) A connected low set.** Let $H=h(w_*)$, $q_i=s(i,H)$ ($+\infty$ outside the old component), and
$$t=s(w_*)-12\cdot10^{-5},\qquad S=\{i:\ q_i\le t\}.\tag{31}$$
For every seed $w\in B$: $|s(w)-s(w_*)|\le8R$ (the path through $z$) and $|s(w')-s(w)|\le E_A$. The terminal column $i$ of either chosen descending path of the pair $(w,w')$ therefore satisfies $q_i\le s(w_*)+8R+E_A-10^{-5}+\epsilon+a_1<t$, using $8R+E_A+\epsilon+a_1<12\cdot10^{-5}$. So $S\ne\varnothing$, and it is connected in the active graph of $I$ (Lemma 2.8).

**(iii) The ball avoids $S$.** Every column visited by a center-to-seed path of length $\le4R$ has $q_i\ge s(v)-a_1\ge s(w_*)-8R-a_1>t$, so lies outside $S$. By the gap property (Lemma 2.5) all these path words and their endpoint representatives lie in **one linear circular gap of $S$**; fix a representative of $z$ to order it.

**(iv) Two extreme paths.** Choose one representative seed from each group meeting $B$. In the linear order of the gap choose a seed of minimum index among those to the left of the centre index and one of maximum index to the right; let $P_-$, $P_+$ be shortest $J_2$-paths from $z$ to them (constant at $z$ on a side with no seed), each of length $\le4R$. For every chosen seed $w$, at least one of these two paths **visits $w$'s column or makes a switch strictly over its index** (Lemma 2.6).

**(v) The skipped case.** Suppose the path switches over $w$ at a link $ab$ with $w$'s representative in $(a,b)$ (order within the gap). The link is not a circular-neighbour link ($(a,b)$ contains a column and the complementary arc contains the nonempty set $S$), hence a single terminal switch at a tip $e$ with height in $J_2$, lying on $P_\pm$, with
$$d(w,e)\le8R<1,\qquad(a,b)\cap S=\varnothing.\tag{32}$$
*Claim: the witness partner $w'$ has representative strictly outside $[a,b]$.* If it were in $(a,b)$, its descending path, which ends in $S$, would have to visit column $a$ or $b$ (Lemma 2.4); joining that visit vertically to $e$ and returning along the extreme path and a shortest centre-to-$w$ path gives an $x$–$y$ path of length $\le0.02+a_1+8R<1$, contradicting $d(w,w')\ge1$ (the case $w'\in\{a,b\}$ is similar without the descending segment).

*Consequence.* The link at $e$ separates the two witness representatives strictly. The pair was **not excluded** in §6.2 and (32) holds, so it fails the barrier-drop condition (28):
$$s(e)\ge s(w)-j.\tag{33}$$

**(vi) The skipped seed is near the path.** The descending path from $w$ starts in $(a,b)$ and ends in $S$, so it first hits $a$ or $b$ at some $v$ after arclength $p$. By Lemma 6.3 and a vertical comparison with $e$: $s(v)\le s(w)-p+\epsilon$ and $s(v)\ge s(e)-a_1\ge s(w)-j-a_1$, so $p\le j+\epsilon+a_1$. The descending prefix and the vertical segment from $v$ to $e$ lie in $J_1$, hence
$$d_{J_1}(w,e)\le j+\epsilon+2a_1=:\rho_{\mathrm{pack}}.\tag{34}$$
Thus every chosen seed lies within $\rho_{\mathrm{pack}}$ of $P_-\cup P_+$ in $d_{J_1}$ (in the visited-column case within $a_1$ by a vertical interval).

**(vii) Counting.** Distinct chosen groups have distinct width-$g$ cells (same bands, band component and old identifiers have already been shown), and the seeds are radially padded, so Lemma 2.12 gives pairwise $d_{J_1}$-separation $\ge b_0=0.01g$. Assign to each chosen seed a path point within $\rho_{\mathrm{pack}}$ of it, on one of the two paths. Points assigned to different seeds are at $d_{J_1}$-distance $\ge b_0-2\rho_{\mathrm{pack}}\ge b_0/2$, hence at arclength separation $\ge b_0/2$ on a path. A path of length $4R$ holds at most $1+8R/b_0$ such points, so the two paths hold at most
$$2+\frac{16R}{b_0}=2+\frac{1600R}{g}$$
assigned points. $\square$

## 6.3 Numerics **[hand]**

With $R=10^{-8}$ and $g=10^{-14}$: $1600R/g=1.6\times10^{9}$, so $M_{\mathrm{pack}}=2+1.6\times10^{9}$. In Proposition 9.1 the success probability is $p=2^{-(2M_{\mathrm{pack}}+10)}$. These are existence constants, not practical ones.

## 6.4 Points a reader may wish to check

1. **Step (iii), "one gap".** Lemma 2.5 is applied to the set $S$ with *paths in a larger graph $G_I$* while the ball's paths live in $G_{J_2}$; the paper notes "connectivity of $S$ and the path may be witnessed using different subgraphs of the same noncrossing graph". Confirm that noncrossing is a property of the full column graph (Definition 2.1), so this is legitimate.
2. **Step (v), "not a neighbour link".** The tip structure (single switch at $H_e$, nothing above at either endpoint) is used to place $e$ on the extreme path with height in $J_2$ and to conclude that the tip is the *only* switch of the link.
3. **Step (vi), the first-hit argument.** The inequality $s(v)\ge s(e)-a_1$ uses that $v$ is on column $a$ or $b$, whose switches are at or below the tip, and a vertical comparison within $J_1$ of width $a_1$.
4. **Why the pair survives (28).** The packing bound depends on the **negation** of Lemma 6.5's hypothesis; if the exclusion in §6.2 were defined with a different threshold than $j$, (33) would change. The constants must be consistent between the two places.
