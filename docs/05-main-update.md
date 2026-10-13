# 05. The main update, descending paths, certificates and seeds (paper §6.1–6.2)

Tags as in the [README](../README.md). **[stated]** unless tagged. Notation: $s$ is the ordinary-chart field $s=d_I(o,\cdot)$ of system $A$ on an old band $I$; all lengths are in units of the current scale, so the pairs considered satisfy $1\le d(x,y)\le2$.

## 5.1 Setting (§6 introduction)

Cells are the connected radial cells of Lemma 2.11, in the broad band $J_1$; $J_2\subset J_1$ denotes a narrow band contained in its broad band. The **frontier** $\partial C$ of a cell $C$ is the union, within $J_1$, of the column intervals of columns having an active link to a column outside $C$; frontier values are always left unchanged. An ordinary $A$-chart has $P=C_0+\tau s$, $\tau\in\{\pm1\}$; comparisons are done in the $s$-orientation (replacing $s$ by $s'$ means replacing $P$ by $C_0+\tau s'$).

## 5.2 The main replacement (§6.1)

Let $C$ be a cell of width $D$ in $J_1$. It is **available** if its closed $d$-neighbourhood of radius $1$ lies in one old ordinary $A$-chart; then every path of length $\le10D$ starting in $C$ is evaluated in that chart, and
$$|s(v)-s(w)|\le d_{J_1}(v,w)\le10D\qquad(v,w\in C).\tag{20}$$
Fix $v_C\in C$, $s_C=s(v_C)$. On the whole $J_1$-component of $C$ define the $(1-\zeta_A)$-Lipschitz function
$$p_C(v)=\min\Big\{s_C+1,\ \inf_{z\in\partial C}\big[s(z)+(1-\zeta_A)\,d_{J_1}(v,z)\big]\Big\}\tag{21}$$
(the infimum over an empty frontier is $+\infty$), apply Theorem 4.1 with error $E_A$ to obtain $\tilde p_C$, and put
$$F_C=\tilde p_C-4E_A,\qquad p_C-5E_A\le F_C\le p_C-3E_A.\tag{22, 23}$$
For a fresh offset $\alpha_C\in[0,E_A]$ define a height function $p_{h,C}$: equal to $s_C-1+\alpha_C$ at both ends of $J_1$, to $s_C+2+\alpha_C$ on the interval obtained by deleting outer portions of width $0.09a_1$, and linear in between (Lipschitz constant $3/(0.09a_1)$), extended constantly. If the independent fair coin of $C$ is kept, set on $C$
$$s'(v)=\max\{\,s(v),\ \min\{F_C(v),\ p_{h,C}(h(v))\}\,\}.\tag{24}$$
Otherwise, and for unavailable cells, leave the cell unchanged.

*Intuition.* $p_C$ is a cone over the frontier values, capped at $s_C+1$; the update raises the field inside the cell as far as that cone (smoothed) and the height plateau allow, never lowers it, and leaves it unchanged on the frontier and at the band ends.

**Lemma 6.1 (validity and size).** The simultaneous replacements (24) respect switches, preserve vertical nesting and the vertical upper bound for $A$, and admit ordinary charts on every new branch; at any point the change of the $A$-label set has measure at most $\kappa_A(1+10D)$. *Proof ingredients.* At a frontier point $z$, $p_C(z)\le s(z)$ so $F_C(z)\le s(z)-3E_A$; at the band ends (20) gives $p_{h,C}\le s-1+10D+E_A<s$; so the replacement equals the old field on every frontier and at every height endpoint *with a strict margin*. The vertical Lipschitz constants are $\max\{1,\,3/(0.09a_1)\}$ and $\kappa_A\cdot$ that is $<1$ by the choice of $\kappa_A$ (§5.1). Finally $s'\ge s$ and $F_C\le s_C+1-3E_A\le s+1+10D$, so $0\le s'-s\le1+10D$ and (5) gives the bound.

## 5.3 Descending paths and the dichotomy

**Definition 6.2.** A *descending path at $w$* is a shortest path in $J_1$ of length $d_0\in[10^{-5},0.02]$ whose terminal point $z$ satisfies
$$s(z)\le s(w)-d_0+\epsilon.\tag{25}$$
Parametrised by arclength $t\in[0,d_0]$ it satisfies $s(\gamma(t))\le s(w)-t+\epsilon$ (26).

**Lemma 6.3 (raise or descend).** Let $w$ satisfy the height and radial interior requirements for its width-$D$ cell, and let the cell be available. For every choice of interpolation parameters, the kept replacement raises $s(w)$ by more than $2E_A$, unless a descending path at $w$ exists.

*Proof* **[stated]**. Suppose the raise is $\le2E_A$. The height-interior requirement puts $w$ on the plateau, so $p_{h,C}(h(w))\ge s(w)+2-10D>s(w)+2E_A$; therefore $F_C(w)\le s(w)+2E_A$, and (23) gives $p_C(w)\le s(w)+7E_A$ (27). The branch $s_C+1$ exceeds this bound, so the infimum in (21) is attained at some $z\in\partial C$: $s(z)+(1-\zeta_A)d_{J_1}(w,z)\le s(w)+7E_A$. Put $d_0=d_{J_1}(w,z)$. Lemma 2.12 gives $d_0\ge0.01D=10^{-5}$, the weak diameter bound gives $d_0\le10D<0.02$, the path lies in the old chart band by availability, and since $\zeta_Ad_0+7E_A\le(\epsilon/100)(10D)+7\epsilon/1000<\epsilon$ it satisfies (25). For (26), the old field's Lipschitz bound on the remaining subpath of length $d_0-t$ gives $s(\gamma(t))\le s(z)+(d_0-t)\le s(w)-t+\epsilon$. $\square$

**Corollary 6.4 (separation supplied by the main test).** Let $(x,y)$ be eligible, interior, $1\le d(x,y)\le2$, $|s(x)-s(y)|\le E_A$. If either endpoint has no descending path, then conditional on main-update mode, with probability $\ge\tfrac14$ the independent cell coins give $A$-symmetric-difference separation at least $\kappa_AE_A$ at this step. *(The endpoints lie in different cells since a cell has diameter $\le10D<1$; keep the coin at the endpoint with no descending path and suppress the other: probability $\tfrac14$. By Lemma 6.3 the first value rises by more than $2E_A$ while the second is unchanged, so the new field difference is $\ge E_A$; apply (5).)*

## 5.4 The component barrier and the seeds (§6.2)

Retain only eligible pairs $(x,y)$ with $1\le d\le2$ satisfying all interior requirements and both cutoffs in (19), lying in common bands $J_2\subset J_1$, with descending paths at **both** endpoints. Their common field $s$ is nonconstant (a constant field cannot satisfy (25) with $d_0\ge10^{-5}>\epsilon$). Fix one representative column for every vertex. A chord *separates two representatives strictly* if they lie in the strict interiors of the two complementary circular arcs of its endpoint columns.

**Lemma 6.5 (label mass at a separating tip).** Suppose a retained pair has a non-neighbour link separating its representatives strictly, with tip $e$ at a height in $J_2$ and $d(e,x)\le1$ or $d(e,y)\le1$. If
$$s(e)<s(w)-j\tag{28}$$
for at least one endpoint $w$, there is a label set of measure $\ge\kappa_Aj/4$ on which both endpoints are active and $e$ is inactive; in no-change mode this gives component-refined $A$-separation $\ge\kappa_Aj/2$. More generally, if later changes have unrefined symmetric-difference costs $\Delta_x,\Delta_y,\Delta_e$ at the three points, the final refined separation is at least
$$2\big(\kappa_Aj/4-\Delta_x-\Delta_y-\Delta_e\big)_+.\tag{29}$$
*Proof.* Eligibility puts $x,y,e$ in one old ordinary chart, $P=C_0+\tau s$; restrict to labels with $\sigma=\tau$, where the threshold at $v$ is $T_v=h(v)+\kappa_A\tau C_0+\kappa_As(v)$. Since $|s(\cdot)-s(w)|\le E_A$ for the other endpoint, $E_A\le j/4$ and all heights lie in $J_2$ with $a_2\le\kappa_Aj/4$: $T_v-T_e\ge\kappa_A(j-E_A)-a_2\ge\kappa_Aj/2$ for $v=x,y$. Labels with $\sigma=\tau$ and $T_e\le Z<\min\{T_x,T_y\}$ have the three required memberships and mass $\ge\kappa_Aj/4$ (one half of the label space carries $\sigma=\tau$). By Lemma 3.2 each such label contributes $2$ to the refined distance, and later changes destroy at most mass $\Delta_x+\Delta_y+\Delta_e$. $\square$

**The seed set.** Exclude every retained pair to which Lemma 6.5 applies. The **seeds** are the endpoints of the remaining pairs; a vertex occurring in several remaining pairs is one seed with a fixed *witness* pair, and descending paths for both members of each chosen witness pair are fixed, all from the old fields and bands, *before* any secondary interpolation noise. Seeds are **grouped** by broad and narrow band, their width-$g$ cell in the broad band, and their old chart identifiers in both systems. Groups only organise the update (they introduce no chart boundaries); two seeds of one group are at $d_{J_1}$-distance $\le10g$, their ordinary fields differ by $\le10g$, their full $B$-fields by $\le50g$ (old-chart Lipschitz constants $<5$).

## 5.5 Points a reader may wish to check

1. **Lemma 6.3, the plateau step.** "Height interior" is invoked to place $w$ on the plateau of $p_{h,C}$ (the outer $0.09a_1$ portions are excluded by the outer-tenths requirement of §5.2). The inequality $p_{h,C}(h(w))\ge s(w)+2-10D$ uses (20) with $s_C\ge s(w)-10D$.
2. **Lemma 6.3, the use of Lemma 2.12.** The lower bound $d_0\ge0.01D$ is exactly where the "$0.02D$ from the thresholds" interior condition of §5.2 enters.
3. **Lemma 6.5.** The restriction to $\sigma=\tau$ halves the mass; the stated $\kappa_Aj/4$ already accounts for this. Check that "(28) for *at least one* endpoint" suffices because the other endpoint's $s$-value differs by $\le E_A$.
4. **Which charts?** All of $x,y,e$ lie in one old ordinary $A$-chart because $d(e,\cdot)\le1<5$; this is the only place Lemma 6.5 uses chart structure.
