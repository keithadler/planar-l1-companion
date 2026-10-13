# 02. Threshold sets, charts, exact gluing, component refinement (paper §3)

Tags as in the [README](../README.md). **[Lean]** here means compiled and audited by the author in Lean 4 / Mathlib under the hypotheses listed in [12](12-lean-status.md); the Lean sources are not yet public. Identity (5) and rebasing are tagged **[hand]**; a Lean formalisation of them exists but has not yet had its statements reviewed against the paper.

## 2.1 Threshold sets

Fix, for each system, the label space $(\Omega,\mu)=\big(\mathbb R\times\{-1,1\}^{\mathbb N},\ \mathcal L\otimes\nu\big)$ with $\nu$ the product of fair sign measures. For a point $v$ of the column space, a field $P$ and chart variables $Z:\Omega\to\mathbb R$, $\sigma:\Omega\to\{-1,1\}$ whose joint law is $\mathcal L\otimes\tfrac12(\delta_{-1}+\delta_1)$,
$$A_v=\{\omega\in\Omega:\ Z(\omega)<h(v)+\sigma(\omega)\,\kappa\,P(v)\},\tag{4}$$
with $\kappa>0$ fixed per system ($\kappa_A,\kappa_B$ chosen in §5.1). With $P\equiv0$, $A_v=\{Z<h(v)\}$ is increasing in $h$, and $\mu(A_{(i,H)}\triangle A_{(i,H')})=|H-H'|$.

### Lemma 3.1 (vertical control and rebasing)

**(i) Identity.** For two points expressed in common chart variables,
$$\mu(A_v\triangle A_w)=\max\{|h(v)-h(w)|,\ \kappa|P(v)-P(w)|\}.\tag{5}$$
*Derivation* **[hand]**. For a fixed sign $s$, $\{Z<a_s\}\triangle\{Z<b_s\}$ is a half-open interval of Lebesgue length $|a_s-b_s|$, with $a_s-b_s=\Delta h+s\kappa\Delta P$. Averaging over $s=\pm1$ (each with weight $\tfrac12$) gives $\tfrac12(|\Delta h+\kappa\Delta P|+|\Delta h-\kappa\Delta P|)$, and $\tfrac12(|a+b|+|a-b|)=\max(|a|,|b|)$.

**(ii) Nesting.** If $\kappa\,\mathrm{Lip}_{\mathrm{vert}}(P)<1$ and $P$ respects switches, then $H\mapsto H+\sigma\kappa P(i,H)$ is strictly increasing for both signs; hence the sets are nested increasingly on every column interval of the chart, and $\mu(A_v\triangle A_w)$ equals the vertical length there. **[stated]**

**(iii) Rebasing.** Let $\psi:\mathbb R\to\mathbb R$ be Lipschitz with $\kappa\,\mathrm{Lip}(\psi)<1$ and $P(v)=\psi(h(v))$. Put $\varphi_\sigma(H)=H+\sigma\kappa\psi(H)$ (increasing bijections of $\mathbb R$) and $Z'=\varphi_{\sigma}^{-1}(Z)$. Then $\{Z<\varphi_\sigma(h)\}=\{Z'<h\}$ for every label, so the same sets are described by a chart with field $0$. **[stated]**

*The law of $Z'$* **[hand]**. For $a<b$,
$$\mu\{a<Z'<b\}=\tfrac12\big[(\varphi_+(b)-\varphi_+(a))+(\varphi_-(b)-\varphi_-(a))\big]=b-a,$$
because the $\pm\kappa(\psi(b)-\psi(a))$ terms cancel. **A point about independence.** Given the *old* sign $\sigma=s$, the conditional law of $Z'=\varphi_s^{-1}(Z)$ is $(\varphi_s^{-1})_*\mathcal L$, which depends on $s$; so $(Z',\sigma)$ is *not* distributed as $\mathcal L\otimes\mathrm{fair}$. This is consistent with the paper, which does not use the old sign: it takes a **fresh** sign coordinate $\sigma'$ "unused anywhere earlier in this execution", independent of $Z'$, so that $(Z',\sigma')$ has the required joint law. (The point is worth keeping in mind when reading later uses of rebased charts: independence is from $\sigma'$, not from $\sigma$.)

## 2.2 Charts

A **chart** is a region $\mathcal R\subset X$, a height band $I$ containing its heights, a field $P$ on the corresponding component of $X_I$ (or on $X_I$), and measurable $Z,\sigma$ as above; for $v\in\mathcal R$, $A_v$ is given by (4). At every stage there are finitely many chart identifiers, whose regions partition $X$ with a fixed tie rule; a region may be disconnected and its connected pieces do not receive different identifiers; when points receive a new chart the old identifier is retained on the rest. Initially each system has one chart with $P=0$, $Z$ the first Lebesgue coordinate, $\sigma$ the first sign coordinate.

*Why charts exist.* Formula (5) requires common chart variables. Different charts carry different $(Z,\sigma)$, so across charts only the *global* invariant is available (nested along columns, equal at switches, vertical-length bound). This is the reason for the **eligibility** condition of §3.3/§5.2: the radius-5 balls of both endpoints must lie in one chart region of each system.

*Ordinary charts.* $P=c+\eta s$, $\eta\in\{\pm1\}$, with $s(v)=d_I(o,v)$ for a fixed source $o$, or $s=0$. System $A$ uses only ordinary charts. System $B$ adds *ordered charts* ($P=s+\lambda u$, §7.4) and every recorded $B$-field has Lipschitz constant $<5$.

*Names.* Formulas carry names; an inherited formula keeps its name; the identifier of a new chart records the old chart, the interpolation and the winning formula's name. Distinct old charts are never merged merely because their formulas agree.

## 2.3 Exact gluing (§3.2)

A local update is first written in the old chart variables. The new field is $\max(P,\,Q)$, where $Q$ (a finite minimum of fields, combined over proposals by a finite maximum) lies **strictly below** $P$ on the boundary of its domain $D$ (at interval endpoints and at switches leading outside $D$), and all branches respect switches inside $D$ and satisfy $\kappa\,\mathrm{Lip}_{\mathrm{vert}}<1$.

**Proposition (exact gluing; the content of §3.2)** **[Lean]**. Under these hypotheses the new sets $\tilde A$ are measurable, nested increasingly on each column, equal at switches, and satisfy $\mu(\tilde A_{(i,H)}\triangle\tilde A_{(i,H')})\le|H-H'|$.

*Proof sketch (paper).* For two points of one updated interval use (i)–(ii). For points of different updated intervals (or unchanged points), compare the first with its interval endpoint, then use the old nested sets between the two interval endpoints, then compare with the second point; the three comparisons preserve nesting and their measures sum to the vertical length. The argument does not need finitely many updated intervals. Agreement of the new and old field on the boundary preserves switch-equality.

*Formalisation notes.* The Lean statement takes *one* proposal over *one* domain and proves $\le$ (the paper says "sum to"; $\le$ is all the invariant needs). The unrestricted column distance $\mathrm{colDist}$ is used in place of the band-restricted $d_I$. The label law is assumed only through $\mu\{\sigma=s,\ a\le Z<b\}=\tfrac12(b-a)$ for $s=\pm1$.

## 2.4 Lemma 3.2 (component refinement)

Let a system of sets $(A_p)$ be nested increasingly on each column, respect switches, and satisfy $\mu(A_p\triangle A_q)\le$ vertical length. For a label $\omega$ call a point *active* if $\omega\in A_p$ and **join columns $i,j$ whenever some $s\in S_{ij}$ has $\omega\in A_{(i,s)}$**. Assign to an active point the unit vector of its component and to an inactive point $0$; let $\rho_\omega(p,q)$ be the $\ell_1$ distance of the assigned vectors and $\tilde d(p,q)=\int\rho_\omega(p,q)\,d\mu(\omega)$.

**Lemma 3.2** **[Lean]**. (a) $\tilde d$ is a pseudometric, $\tilde d(p,q)\ge\mu(A_p\triangle A_q)$, and $\tilde d(p,q)\le L$ for every path of length $L$ from $p$ to $q$ (hence $\tilde d\le d$). (b) If $ab$ is a non-neighbour link with tip $(a,H_e)$ inactive for $\omega$, and $p,q$ are active for $\omega$ with columns strictly on opposite sides of $ab$, then $\rho_\omega(p,q)=2$; integrating over the labels where $p,q$ are active and the tip is inactive, $2\,\mu\big((A_p\cap A_q)\setminus A_{(a,H_e)}\big)\le\tilde d(p,q)$ (this integrated form is a direct corollary; the paper uses it in §6.2 and §9.3 but does not state it as a separate display).

*Proof sketch (paper).* On a vertical segment the vector changes only when activity changes, at $\ell_1$-cost equal to the original indicator cost; across an active switch the columns share a component; across an inactive switch both vectors vanish. For (b): every switch at an endpoint column of the link lies at or below the tip, so if the tip is inactive nesting makes them all inactive; a path of column indices between the two strict sides passes through an endpoint (Lemma 2.4), so no active path joins them. Measurability: the set $\{\omega:\ \text{active switch on }ij\}$ equals $A_{(i,\max S_{ij})}$ ($S_{ij}$ compact, nesting), so all finitely many component coordinates are measurable.

*Note on the refined map.* The paper subtracts the vector of a fixed reference point to obtain an element of $L_1$; the Lean file works with $[0,\infty]$-valued integrals, which suffices for every inequality above.

*Use.* Only system $A$ is refined, once, after the last scale. A **separation certificate** is therefore three memberships ($p,q$ active, tip inactive), and later changes of total symmetric-difference cost $\Delta_p,\Delta_q,\Delta_e$ at those three points reduce its mass by at most $\Delta_p+\Delta_q+\Delta_e$ (formula (29)); no control of the *names* of components is needed.

## 2.5 The three estimates required of a local update (§3.3)

There are constants $M,C_0<\infty$ and $b,p,\rho_0>0$, independent of the graph and of the history, such that an update at scale $r$ satisfies

1. **(Movement)** every unrefined label set moves by at most $Mr$ in symmetric difference, at every point of $X$;
2. **(Success)** for a pair at distance in $[r,2r)$, conditional on any past in which it is eligible, with probability $\ge p$ one of: unrefined separation $\ge br$ in one system; or a non-neighbour link separating the two representatives and a system-$A$ label set of measure $\ge br$ on which both are active and the tip is inactive;
3. **(Chart persistence)** if $B_d(v,\rho r)$ lies in one old region in each system, $0<\rho\le\rho_0$, it meets different new regions with probability $\le C_0(\rho+\eta_0)$.

Here $\eta_0$ is a relative mesh allowance for the finite grids used to sample parameters (§5.2). These are Propositions 9.1 and 9.2.

## 2.6 Points a reader may wish to check

1. **Where is (5) used across charts?** Only inside one chart. Collecting every use in §§6–9 and confirming the common-variable hypothesis is a useful audit.
2. **Disconnected chart regions.** Proposition 9.2 estimates the probability that a ball meets two new *identifiers*; the convention that connected pieces of one region share an identifier should be consistent with that count.
3. **Rebasing independence** (point above): confirm that every later use of $(Z',\sigma')$ needs only independence from the fresh sign, not from the old one.
4. **Exactness of the margin.** Gluing needs only $Q\le P$ on the boundary; the paper keeps a strict margin for the later probability bounds (e.g. Lemma 6.1, $F_C\le s-3E_A$ on the frontier).
