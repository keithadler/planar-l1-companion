# 09. One-step estimates, chart persistence, the schedule and the final map (paper §9–10)

Tags as in the [README](../README.md). **[stated]** unless tagged **[hand]**. Estimates are those required in [02, §2.5](02-charts.md).

## 9.1 Proposition 9.1 (movement and success)

There are constants $M<\infty$ and $b,p>0$, depending only on the choices of §5.1, such that at every step of scale $r$:

* **(i)** at every point of $X$, in either system, the unrefined set moves by at most $Mr$ in symmetric difference;
* **(ii)** given any past in which a pair at distance in $[r,2r)$ is eligible, with probability at least $p$ the step produces (a) unrefined separation $\ge br$ in one system, or (b) a non-neighbour tip $e$ and a set of labels of measure $\ge br$ in system $A$ on which both vertices are active and $e$ is inactive, the vertices lying strictly on opposite sides of that link.

*Proof (outline).* (i): Lemma 6.1 (main clipping), Lemma 8.1 (secondary), Lemma 8.3 (increments); there are no simultaneous main updates at a point except at cell overlaps, where every update is unchanged; secondary updates take a maximum, whose movement is bounded without summing over groups. (ii): work in scale units. If one cutoff in (19) fails, no change gives separation at least $\min\{10^{-4}a_2,\kappa_AE_A,\kappa_B10^{-4}R\}$. Otherwise the interior requirements hold with probability $\ge\tfrac14$. A missing descending path is handled by Corollary 6.4 (keep that endpoint's cell, suppress the other: probability $\ge\tfrac14$ given the main mode). If both exist, an excluded pair has the component certificate on a label set of measure $\ge\kappa_Aj/4$, preserved by the no-change mode (Lemma 6.5). For a surviving pair, admission at an endpoint is Lemma 8.2; if neither orientation admits either endpoint, Lemma 8.4 applies. Each case uses one of four modes, at most one fair orientation, and at most $2M_{\mathrm{pack}}+1$ prescribed group coins; for example
$$p=2^{-(2M_{\mathrm{pack}}+10)}$$
is a permissible lower bound after all interior and mode probabilities; $b$ is chosen below all displayed gains and certificate masses. $\square$

## 9.2 Proposition 9.2 (chart persistence)

There exist $C_0<\infty$ and $\rho_0>0$ such that, conditional on the past at a step of scale $r$, if a closed ball $B_d(v,\rho r)$ lies in a single old region in each system and $0<\rho\le\rho_0$, the probability that it is split between different new regions in either system is at most
$$C_0(\rho+\eta_0).\tag{42}$$

*Proof (outline).* Normalise $r=1$. Every point of $B=B_d(v,\rho)$ has a shortest path to $v$ inside $B$, so any two points of $B$ are joined by a path of length $\le2\rho$. A split can arise only if a domain ends inside the ball or different formulas win there; strict margins at domain boundaries prevent the first, and Corollary 4.6 controls the second.

* **Height bands.** The probability that an endpoint of either random height tiling lies within $\rho$ of $h(v)$ is $O(\rho+\eta_0)$; excluding it, the ball lies in one component of a broad and of a narrow band, each processed in its entirety or left unchanged; a narrow band not inside a broad band has no secondary seeds.
* **Main clipping.** If $B$ meets more than one width-$D$ cell (including through different representatives of a quotient point), for any touched available cell $C$ and $w\in B\cap C$ a path to another cell reaches a frontier point $z\in B\cap\partial C$ within length $2\rho$, so $F_C(w)\le s(z)+(1-\zeta_A)d_{J_1}(w,z)-3E_A\le s(w)+4\rho-3E_A$; for $\rho_0<E_A/10$ the proposal cannot raise the field anywhere on $B\cap C$, and the ball keeps its identifier (no radial boundary crossing needs to be excluded). If $B$ lies in one cell, the comparison expression on $B$ is $\max\{s,\min\{F_C,p_{h,C}\}\}$ with $F_C$ one interpolation, $p_{h,C}$ a fixed height function plus independent offset, and $s$ the only branch with no fresh noise; the inputs, portals and bands are fixed before the noises, so Corollary 4.6 (with the fixed Lipschitz bound of the height function) gives one winning branch and, for the interpolation, one named atom throughout $B$ except with conditional probability $O(\rho+\eta_0)$.
* **Secondary clipping.** Condition on cells, surviving groups, orientations, admissions and group coins (all before the fresh clipping noises). A group whose domain meets $B$ has an admitted seed within band distance $R+2\rho<4R$ of $v$, so by Proposition 6.6 there are at most $M_{\mathrm{pack}}$ of them. If a group's domain meets but does not contain $B$, Lemma 8.1 puts its proposal below the old field at the spatial boundary by a fixed margin, so (for small $\rho_0$) it does not act on $B$ and is discarded. Each remaining relevant domain contains $B$ and lies in the ball's common old chart, so all proposals use the same old comparison orientation and label variables; the combined expression is the maximum of $p_*$ and the group proposals, each the minimum of $T_F,H_F$ and (ordinary charts) $O_F$, the only input without fresh noise being $p_*$. Corollary 4.6 applies with at most $M_{\mathrm{pack}}$ interpolation lists.
* No-change and increment modes introduce no chart identifiers. Summing the exceptional probabilities (with $\rho_0$ below the finitely many bounds used) gives (42). $\square$

## 9.3 Choice of spacing, and the final map

Choose $Q=2^m$ so large that: $Q>2000/R$ (Lemma 8.3); $20/Q<\rho_0$; and
$$\frac{40C_0}{Q-1}<\frac12,\qquad\frac{6M}{Q-1}<\frac b2.\tag{43}$$
Choose the mesh allowance so that $\eta_0\le r_f/r$ for every pair of scales $r_f<r$ in the finite collection of schedules, so the mesh term in (42) is no larger than the corresponding scale ratio (this does not change any constant above).

**Fix a pair and its designated scale $r_f$**, and consider $B_d(x,20r_f)$. Initially it lies in one chart in each system. Conditional on having stayed so up to a coarser scale $r$, the first loss probability is at most $40C_0r_f/r$, so
$$\Pr[\text{a first loss before }r_f]\le40C_0\sum_{k\ge1}Q^{-k}=\frac{40C_0}{Q-1}<\tfrac12.$$
On the complementary event the pair is eligible at scale $r_f$; moreover any $D$-cell needed for its main update has its whole 1-neighbourhood in this ball (weak diameter $\le10D$), and the old chart bands contain all short paths used in the tests. By Proposition 9.1(ii), conditional on this event the scale produces a certificate with probability $\ge p$.

Later unrefined movement at any one point is deterministically at most $M\sum_{k\ge1}r_fQ^{-k}=Mr_f/(Q-1)$. An ordinary pair separation loses at most twice this. For a component certificate, remove the labels whose membership later changes at either vertex or at the tip; their total measure is at most three times this quantity. At least $br_f/2$ of the original certificate therefore remains, and Lemma 3.2 gives final separation for those labels regardless of changes elsewhere. In either case the final sum of the refined $A$-distance and the unrefined $B$-distance is at least $br_f/2$ on the successful event, so its expectation in the designated schedule is at least
$$\tfrac12\,p\,\tfrac{br_f}{2}\ \ge\ \tfrac{pb}{8}\,d(x,y).$$

**Mixing.** The designated schedule is the residue class containing the dyadic exponent of $r_f$; every other schedule contributes a nonnegative distance. Mix uniformly over the $m$ schedules. Within each, an outcome is a branch of the finite execution tree, weighted by the product of the conditional probabilities along the branch (weights sum to one although later geometric choices depend on earlier outcomes); take the finite direct sum of the measure spaces with these weights, and of the two systems. Subtracting the assignment at a fixed reference vertex in every summand puts $F$ in a real $L_1$ space (Lemma 3.2), with
$$\frac{pb}{8m}\,d(x,y)\le\|F(x)-F(y)\|_1\le2\,d(x,y)\qquad(x,y\in V).$$
Writing it with finitely many cut coordinates (for each final outcome and each $B$-label the active subset of $V$; for $A$, separately for each active column component the subset of vertices active in it) gives weights $w_S\ge0$ with $\|F(x)-F(y)\|_1=\sum_{\emptyset\ne S\subsetneq V}w_S|\mathbf 1_S(x)-\mathbf 1_S(y)|$, each finite by the upper bound. Rescaling by $8m/(pb)$ gives Theorem 1.1 with
$$C=\frac{16m}{pb}.$$

## 9.4 Section 10 (almost-embeddable families)

Lee and Sidiropoulos reduce fixed-parameter almost-embeddable families to planar and bounded-treewidth pieces joined by 1-sums. **Corollary 10.1** combines this with Theorem 1.1 and the bounded-treewidth theorem of a *second* OpenAI preprint (reference [17]; not covered by these notes): for fixed $g,k,w,a$, every finite connected simple graph in $\mathrm{AE}(g,(k,w),a)$ with positive edge lengths embeds in $L_1$ with distortion at most $K=D\max\{C_{\mathrm{pl}},C_{\hat h+1}\}$, where $D$ is the stochastic distortion bound supplied by Lee–Sidiropoulos, $C_{\mathrm{pl}}$ the constant of Theorem 1.1 and $C_t$ the companion's constant for bags of size $\le t$; the same $K$ bounds the flow–cut gap. The paper states that this does **not** give closure under general clique-sums and hence does not prove the full GNRS conjecture.

## 9.5 Points a reader may wish to check

1. **The order of conditioning in 9.2.** Every appeal to Corollary 4.6 needs: geometry, portals, inputs, group data fixed before the noises tested; branches other than $p_*$ carrying fresh independent noise. Remark 4.7 flags this; here is where it is used.
2. **The first-loss sum.** $40C_0\sum_{k\ge1}Q^{-k}$ counts one loss probability per coarser scale in the schedule, with the mesh term absorbed by $\eta_0\le r_f/r$. Check that the ball radius $20r_f$ is large enough for eligibility ($5r_f$ balls around both endpoints, plus the $1$-neighbourhoods of $D$-cells of diameter $\le10D$).
3. **Movement accounting for component certificates.** "At most three times $Mr_f/(Q-1)$" counts the three points $x,y,e$; confirm that movement at the tip $e$ is bounded by Proposition 9.1(i) even though $e$ is not a vertex of $V$ (the statement is for *every point of $X$*, which is why (i) is stated that way).
4. **The constant.** $C=16m/(pb)$ with $p=2^{-(2M_{\mathrm{pack}}+10)}$ and $M_{\mathrm{pack}}\approx1.6\times10^9$; it is an existence statement.
