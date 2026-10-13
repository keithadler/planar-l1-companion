# 10. Where a verifier might look hardest

Tags as in the [README](../README.md). This note lists **load-bearing steps** and **precise questions**. None is an assertion of an error: each is a place where the argument depends on a delicate point, so that a human check there is worth the most. The ordering is by how much of the proof rests on the step, not by suspected weakness.

## 10.1 Steps on which the whole lower bound rests

| # | Step | Where | Why it carries weight |
|---|---|---|---|
| 1 | Conditional independence of noises in the chart-persistence estimate | Cor. 4.6, Remark 4.7, Prop. 9.2 | Every $O(\rho+\eta_0)$ bound comes from here. The statement is true only if portals, geometry, groups and admissions precede the noises being compared and every branch except one carries fresh independent noise. |
| 2 | Bounded depth of a selected atom ($M$ ancestors) | Lemma 4.4 | Gives the list of at most $N=6(M+1)$ names that makes the union bound uniform in the graph. |
| 3 | Packing bound $M_{\mathrm{pack}}$ | Prop. 6.6 | Makes the number of competing proposals uniform; enters both $p$ (Lemma 8.2) and the persistence estimate (Prop. 9.2). |
| 4 | The raise-or-descend dichotomy | Lemma 6.3 | The entire case analysis of §6–8 is organised around "no descending path, or two of them". |
| 5 | Opposite-arcs separation | Lemma 7.6 (with 7.4, 7.5) | The only place a purely topological property of the circle produces separation; the last case of the dichotomy depends on it. |
| 6 | Choice of $Q$ and the first-loss sum | §9.3 | Closes the argument: $40C_0/(Q-1)<\tfrac12$ and $6M/(Q-1)<b/2$ require $C_0,M,b$ to be independent of $Q$. |

## 10.2 Precise questions, section by section

**§2.** (a) Lemma 2.9: in the trimmed connector, the interior is nonempty because radial values differ by $\ge12a-a/2>a$ at the ends while adjacent columns differ by $\le a$; confirm the three connectors are *vertex-disjoint* after trimming (the argument uses that a common column would permit a vertical transfer of length $\le a$ giving distance $\le13a+a+13a<100a$). (b) Lemma 2.12: the claim that no factor for the number of representatives of $v$ is needed.

**§3.** (a) Which comparisons are made in common chart variables (formula (5)) and which only through the global invariant? (b) Rebasing: confirm every later use needs independence from the *fresh* sign $\sigma'$ only (see [02, §2.1](02-charts.md)). (c) The treatment of disconnected chart regions in Proposition 9.2.

**§4.** (a) Lemma 4.2's equality collar: $c_0=\zeta\delta/50<q/2$ and $200a<c_0$; both rely on $a\le a_0=10^{-6}\zeta\delta$. (b) Lemma 4.5: that a parent's intercept $F_\pi(k)$ does not depend on a child's own noise. (c) Ties and the priority order: confirm the selected name is a measurable function of the noises.

**§5.** The numerical hierarchy: every inequality used later is an *upper bound on a newly chosen constant*, so there is no circularity; the table of explicit values should be cross-checked against each lemma (a mechanical but valuable audit).

**§6.** (a) Lemma 6.3: the plateau step $p_{h,C}(h(w))\ge s(w)+2-10D>s(w)+2E_A$ and the use of (23) to reach (27). (b) Lemma 6.5: the factor $\tfrac12$ from restricting to $\sigma=\tau$. (c) Prop. 6.6 step (iii): applying Lemma 2.5 to a connected $S$ in $G_I$ and paths in $G_{J_2}$.

**§7.** (a) Lemma 7.2: strictness conventions in (7.2.1)–(7.2.2). (b) Lemma 7.6: consistency of the margins $0.18R$ (strip), $0.2R$ (rectangle), $0.01R$ (ball), $0.4R$ (excursions).

**§8.** (a) Lemma 8.3 with $Q>2000/R$: disjoint supports of increments at distinct scheduled scales. (b) Lemma 8.4: the hypothesis $d_I(x,y)=d(x,y)$ supplied from eligibility.

**§9.** (a) Eligibility at scale $r_f$ from a single ball $B_d(x,20r_f)$ in one chart. (b) The accounting of three points ($x,y,$ tip) in the component-certificate case.

## 10.3 A short audit that can be done by hand

These are computations a reader can verify in minutes:

1. Identity (5): $\tfrac12(|a+b|+|a-b|)=\max(|a|,|b|)$. **[hand]**
2. Rebasing law: $\tfrac12[(\varphi_+(b)-\varphi_+(a))+(\varphi_-(b)-\varphi_-(a))]=b-a$. **[hand]**
3. $E_A=\epsilon/1000=10^{-27}\le j/4=2.5\times10^{-21}$; $a_2\le\kappa_Aj/4$ from $a_2\le10^{-6}\kappa_Aj$. **[hand]**
4. With $D=10^{-3}$, $\epsilon=10^{-24}$, $d_0\le10D=10^{-2}$: $\zeta_Ad_0+7E_A\le\frac{\epsilon}{100}\cdot10^{-2}+\frac{7\epsilon}{1000}=\epsilon(10^{-4}+7\times10^{-3})<\epsilon$. **[hand]**
5. $8R+E_A+\epsilon+a_1<12\cdot10^{-5}$ (step (ii) of the packing proof): $8R=8\times10^{-8}$, the rest are far smaller. **[hand]**
6. $4(0.02R+\eta)\le0.080004R$ for $\eta\le10^{-6}R$. **[hand]**
7. The interior probability budget: $2(0.21)+2(0.081)=0.582\le\tfrac34$, giving success probability $\ge\tfrac14$. **[hand]**
8. $M_{\mathrm{pack}}=2+\lceil1600R/g\rceil$ with $R/g=10^{6}$: $1.6\times10^{9}+2$. **[hand]**

## 10.4 Standing of this list

The notes' author has read all of §1–§10 once, re-derived the items in 10.3, and **not** independently checked the proofs of Lemmas 2.9, 4.4, 4.5, 6.6, 7.2, 7.6, 8.3 or Propositions 9.1–9.2. Everything in 10.1–10.2 is therefore a suggestion for where human attention is most valuable.
