# 03. Interpolation by single-source distance functions (paper §4)

Tags as in the [README](../README.md). Everything is **[stated]** unless tagged **[hand]**.

**Purpose.** Local updates need a *1-Lipschitz* field that approximates a given field $p$ of Lipschitz constant $<1$ and is built from pieces $c\pm d_J(k,\cdot)$ (so that each piece is an ordinary chart), while controlling *where the selected piece changes*. Theorem 4.1 supplies this; Corollary 4.6 turns it into the probability bound used for chart persistence (Proposition 9.2).

Throughout, $Y$ is a connected component of a closed band $X_J$, of width $a$ and midheight $H_*$; $d_J$ is its intrinsic distance; $o\in Y$ lies at height $H_*$; $b_i=d_J(o,(i,H_*))$ as in [01](01-columns-and-bands.md). Portals and $o$ are chosen *before* any noise is sampled.

## 3.1 Theorem 4.1 (thin-band interpolation)

Let $0<\zeta<1$, $E>0$ and
$$\delta=\tfrac E8,\quad a_0=10^{-6}\zeta\delta,\quad q=\tfrac{\zeta\delta}{20},\quad\rho_0=\tfrac{\zeta\delta}{1000},\quad M=\lceil15/\zeta\rceil+3,\quad N=6(M+1).\tag{6}$$
Suppose $0<a\le a_0$ and $p:Y\to\mathbb R$ is $(1-\zeta)$-Lipschitz for $d_J$. There is a random function $Q:Y\to\mathbb R$, built from finitely many independent noises uniform on $[q,2q]$, such that for every realisation:

1. $Q$ respects all switches, is $1$-Lipschitz for $d_J$, and $|Q-p|\le6\delta<E$.
2. $Q$ is a piecewise selection among *named atoms* $A(v)=C+\varepsilond_J(k,v)$ with $\varepsilon\in\lbrace \pm1\rbrace $, $k\in Y$; the source $k$ and sign $\varepsilon$ of each name are fixed before the noises, the intercept $C$ is random; a reused atom keeps its name.
3. For $x\in Y$ and $0<\rho\le\rho_0$ there is a list $\mathcal A(x,\rho)$ of at most $N$ names, determined without the noises, containing every atom selected by $Q$ on $B_{d_J}(x,\rho)$; except on an event of probability at most
$$\frac{N^2}{q}(8\rho+\eta),\tag{8}$$
a single named atom is selected throughout the ball. ($\eta=0$ for continuous noises; for noises uniform on an equally spaced grid including both endpoints of $[q,2q]$, $\eta$ may be the largest spacing.) The same holds for any set of points reached from $x$ by band paths of length $\le\rho$, including representatives met on those paths.

## 3.2 The construction (§4.1–4.2)

**Tree of superlevel components.** For $n\ge0$, the *nodes of depth $n$* are the components of the subgraph on columns with $b_i\ge n\delta$. The unique depth-0 node is the root; a node of depth $n+1$ lies in exactly one node of depth $n$ (its parent). The *layer* of a node $\nu$ of depth $n$ is the set of its columns with $n\delta\le b_i<(n+1)\delta$ (possibly empty). Every column lies in the layer of exactly one node. For a nonroot node choose a set $K_\nu$ of one or two **entrance portals** (Lemma 2.9); at the root $K_\nu=\lbrace o\rbrace $. By Lemma 2.13, for $v$ in the layer of $\nu$ or a child portal,
$$\min_{k\in K_\nu}d_J(k,v)\le\delta+220a,\qquad d_J(k,v)\ge\delta-10a\ (k\in K_\nu,\ v\text{ a child portal}),\qquad n\delta\le d_J(o,k)\le n\delta+2a.$$

**Formulas.** For every portal $k\in K_\nu$ sample independent $\alpha_{\nu k}\in[q,2q]$, and at nonroot nodes also $\alpha'_{\nu k},\alpha''_{\nu k}\in[q,2q]$. Define on all of $Y$, recursively down the tree:

* tentative formula $T_\nu(v)=\min_{k\in K_\nu}\big(p(k)+d_J(k,v)+\alpha_{\nu k}\big)$; at the root $F_\nu=T_\nu$;
* for a node $\nu$ with parent $\pi$ (whose $F_\pi$ is $1$-Lipschitz):
$$A_\nu(v)=\min_{k\in K_\nu}\big(F_\pi(k)+d_J(k,v)-\alpha'_{\nu k}\big),\qquad B_\nu(v)=\max_{k\in K_\nu}\big(F_\pi(k)-d_J(k,v)+\alpha''_{\nu k}\big),$$
$$[L_\nu,U_\nu]=\big[\min(F_\pi,B_\nu),\ \max(F_\pi,A_\nu)\big],\qquad F_\nu=\min\lbrace U_\nu,\max(L_\nu,T_\nu)\rbrace .$$

The interval always contains $F_\pi(v)$ and *collapses* to it near the portals: **[hand]** if $d_J(k,v)<q/2$ then $A_\nu(v)\le F_\pi(k)+d_J(k,v)-\alpha'\le F_\pi(v)+2d_J(k,v)-\alpha'<F_\pi(v)$ (the parent is 1-Lipschitz and $\alpha'\ge q$), and symmetrically $B_\nu(v)>F_\pi(v)$; hence $L_\nu=U_\nu=F_\pi$ in a collar of the portals. All $F_\nu$ are $1$-Lipschitz (finite min/max of $1$-Lipschitz functions). The new atoms of a nonroot node are $p(k)+d_J(k,\cdot)+\alpha_{\nu k}$, $F_\pi(k)+d_J(k,\cdot)-\alpha'_{\nu k}$, $F_\pi(k)-d_J(k,\cdot)+\alpha''_{\nu k}$; the scalar $F_\pi(k)$ is an intercept, not an instruction to inherit an atom. A fixed priority order on names (smaller depth first) resolves ties; the same inherited atom always has the same name.

**Definition of $Q$.** On a representative $(i,H)$, $Q=F_\nu$ for the layer node $\nu$ of column $i$. Linked columns have $|b_i-b_j|\le 2a<\delta$, so their layer depths are equal or consecutive; at consecutive depths the upper node is a child of the lower one and its column is an entrance column, whose switch point is within $200a<c_0$ of an upper portal, so Lemma 4.2 gives the same value *and the same atom name* from both representatives. Hence $Q$ is well defined, respects switches, and is $1$-Lipschitz on each column and therefore for $d_J$.

## 3.3 Lemmas

**Lemma 4.2 (accuracy and equality collars).** $F_\nu$ has error $\le5\delta$ at every portal of a child of $\nu$ and $\le6\delta$ on its own layer. If $\mathrm{dist}_{d_J}(v,K_\nu)\le c_0:=\zeta\delta/50$ then $F_\nu(v)=F_\pi(v)$ with the same selected atom name.

*Key inequalities.* With $r_\nu(v)=\mathrm{dist}_{d_J}(v,K_\nu)$,
$$p(v)+\zeta r_\nu(v)+q\ \le\ T_\nu(v)\ \le\ p(v)+(2-\zeta)r_\nu(v)+2q,\tag{13}$$
and $A_\nu\ge p-5\delta+\zeta r_\nu-2q$, $B_\nu\le p+5\delta-\zeta r_\nu+2q$ ((14)–(15)). At a child portal (10) and $a\le10^{-6}\zeta\delta$ give $\zeta r_\nu\ge2q$, hence $U_\nu\ge p-5\delta$ and $L_\nu\le p+5\delta$; clamping a number in $[p,p+3\delta]$ (the range of $T_\nu$ there, by (13) and (9)) to an interval with these two properties yields a value in $[p-5\delta,p+5\delta]$.

**Lemma 4.3.** For $x\in Y$ and $0<\rho\le\rho_0$ there is a node $\nu$, determined without the noises, with $Q=F_\nu$ on $B_{d_J}(x,\rho)$ (including atom names); every point of the ball has a representative on a column with $b_i\ge n\delta$, $n=\mathrm{depth}(\nu)$. *(Radial values in the ball differ by $\le2\rho+2a<\delta$, so layer depths take at most two consecutive values; at the interface the equality collar identifies the formulas.)*

**Lemma 4.4 (bounded depth).** Every atom selected by $F_\nu$ on the ball originates in $\nu$ or one of its last $M$ ancestors; hence at most $N=6(M+1)$ names occur. *Obstruction:* if $\zetad_J(k,v)>13\delta$ for all $k\in K_\mu$, then $T_\mu>p+13\delta$, $A_\mu>p+7\delta$, $B_\mu<p-7\delta$; so if the parent value lies in $[p-6\delta,p+6\delta]$ then $L_\mu=B_\mu$, $U_\mu=A_\mu$, and $F_\mu=\min(A_\mu,T_\mu)>p+7\delta$: a value within $6\delta$ of $p$ cannot be obtained by selecting the parent atom at $\mu$. An ancestor $\mu$ of depth $n-M$ satisfies $d_J(k,v)\ge M\delta-3a$ for $k\in K_\mu$, which (by the definition of $M$) triggers the obstruction.

**Lemma 4.5 (fresh-noise comparison).** For two distinct names in the list of Lemma 4.4, $x\in Y$ and $t\ge0$,
$$\Pr\big(|A(x)-A'(x)|\le t\big)\le\frac{2t+\eta}{q}.\tag{17}$$
*(For atoms of different depths use the later atom's own noise; its intercept ($p(k)$ or $F_\pi(k)$) does not depend on that noise since parent formulas use only earlier nodes. After conditioning on all other noises the difference is $c+\varepsilon\alpha$ with $\alpha$ uniform on $[q,2q]$. For a grid with spacing $\eta'\le\eta$, an interval of length $2t$ contains at most $2t/\eta'+1$ grid points out of $q/\eta'+1$.)*

**Completion of Theorem 4.1.** The union bound with $t=4\rho$ over at most $N^2$ pairs shows that, except with probability $\le N^2(8\rho+\eta)/q$, no two listed atoms are within $4\rho$ of each other at $x$; since all atoms are $1$-Lipschitz, they differ everywhere on the ball and the continuous function $Q$ selects from this finite list with a locally constant, hence (connectedness through the centre) constant, name.

## 3.4 Corollary 4.6 (comparison with other branches)

Condition on arbitrary prior data. Let $W$ be the union of band paths of length $\le\rho$ issuing from $x$, fixed by the prior data. Let $Q_1,\dots,Q_s$ be interpolation constructions on bands containing all these paths (geometries, inputs and portals fixed beforehand, noise families mutually independent; constants $q_i,N_i,\rho_{0,i}$ as in (6)). Allow as inputs $c_i+\varepsilon_iQ_i$ ($c_i$ fixed, $\varepsilon_i=\pm1$), one fixed branch $f$, and $t$ branches $g_j+\beta_j$ with fixed $g_j$, $f$ whose restrictions to the paths are $L$-Lipschitz in arclength and $\beta_j$ fresh independent uniform noises on intervals of length $w_j>0$. Put
$$L_*=\max(1,L),\quad S=1+t+\sum_iN_i,\quad q_*=\min\lbrace q_i\rbrace \cup\lbrace w_j\rbrace .$$
If $\rho\le\min_i\rho_{0,i}$ (when $s>0$) and at least one input is randomised, then any fixed expression formed by finitely many minima and maxima of these inputs selects one branch, and for a selected interpolation one atom, throughout $W$, except with conditional probability at most
$$\frac{S^2}{q_*}(8L_*\rho+\eta).\tag{18}$$
*Proof idea.* For two distinct names at $x$ the comparison has the interval bound $(2u+\eta)/q_*$ at tolerance $u$ (Lemma 4.5, conditioning on all noises except the own noise of one of the two atoms; independence of the constructions makes the other atom independent of it; at most one branch has no fresh noise). Take $u=4L_*\rho$, sum over $\le S^2$ pairs; off this event no two listed values agree anywhere on $W$ (changes along each path from $x$ are $\le L_*\rho$), so the selection is constant on each path, hence on $W$.

**Remark 4.7 (as stated).** The conditional-independence hypotheses are substantive: a branch defined using the *current* interpolation noises cannot be treated as a fixed comparison branch, and two arbitrary fixed branches need not have small probability of meeting. Later applications use one old branch plus independently shifted height or ordered branches, after conditioning on bands, old charts, groups and admissions; all portals and interpolation inputs precede the noises being tested.

## 3.5 Points a reader may wish to check

1. **The recursion for $F_\nu$ is on $Y$, not on the layer.** $F_\nu$ is defined on all of $Y$; only the *selection* by layer matters for $Q$. Confirm that no estimate uses $F_\nu$ outside the region where Lemma 4.2's hypotheses hold.
2. **Lemma 4.4's constants.** The condition $\zeta d_J(k,v)>13\delta$ with $d_J\ge M\delta-3a$ and $M=\lceil15/\zeta\rceil+3$: $\zeta(M\delta-3a)\ge15\delta+3\zeta\delta-3\zeta a>13\delta$ for $a\le a_0$.
3. **Lemma 4.5 and the order of noises.** The independence argument relies on parent formulas using only earlier nodes' noises (so intercepts $F_\pi(k)$ are independent of a child's own noise). This is the load-bearing point behind Corollary 4.6, and Remark 4.7 flags it.
4. **Priority order and ties.** Names are totally ordered with smaller depth first; ties in $\min/\max$ resolve to the earliest name. Check this gives a *function* of the noises, so that (8) concerns a well-defined event.
