# 11. Glossary and constants

Tags as in the [README](../README.md). Symbols are the paper's.

## 11.1 Objects

| Symbol | Meaning | First used |
|---|---|---|
| $X$, $h$, $d$, $d_I$ | quotient of the columns; height function; path metric; intrinsic metric of paths staying in $I$ | Def. 2.1 |
| $G_I$ | active column graph of a band $I$ | Def. 2.1 |
| $S_{ij}$ | closed bounded set of switch heights of the link $ij$ | Def. 2.1 |
| tip, $H_e$ | the unique switch height of a non-neighbour link, with nothing above it at either endpoint | Def. 2.1 |
| $b_i$ | radial coordinate $d_J(o,(i,H_*))$ | §2.2 |
| portal | one of $\le2$ entrance midpoints of a high component | Lemma 2.9 |
| cell, $\partial C$ | connected component of a radial layer; its frontier | Def. 2.10 |
| $\Omega=\mathbb R\times\{\pm1\}^{\mathbb N}$, $(Z,\sigma)$ | label space; threshold and sign coordinates | §3.1 |
| $A_v$ | label set of the point $v$: $\{Z<h(v)+\sigma\kappa P(v)\}$ | (4) |
| chart | region + band + field $P$ + label functions $(Z,\sigma)$ | §3.1 |
| ordinary chart | $P=c+\eta\,s$, $s=d_I(o,\cdot)$ or $0$ | §3.1 |
| ordered field | Definition 7.1 | §7 |
| $t_s$ | transverse coordinate of an ordered field $s$ | Def. 7.3 |
| ordered chart | $P=s+\lambda u$ with $s$ ordered, $u$ $K$-Lipschitz | §7.4 |
| named atom | $C+\varepsilon\,d_J(k,\cdot)$ with a fixed name | Thm. 4.1 |
| eligible pair | both radius-5 balls lie in one chart region in each system | §3.3 |
| descending path | shortest path with $s(z)\le s(w)-d_0+\epsilon$ | Def. 6.2 |
| seed, group | endpoints of surviving witness pairs; seeds grouped by bands, $g$-cell and chart identifiers | §6.2 |
| certificate | (a) unrefined separation $\ge br$, or (b) $A$-labels with $x,y$ active and the tip inactive | Prop. 9.1 |
| $A$, $B$ | the two systems of label sets | §3 |
| $A_\nu,B_\nu,T_\nu,F_\nu,[L_\nu,U_\nu]$ | envelopes, tentative formula, clamped formula at a node | §4.2 |

## 11.2 Constants (explicit values from §5.1 and §6)

| Constant | Value / definition | Used for |
|---|---|---|
| $R$ | $10^{-8}$ | secondary update radius; packing ball radius $4R$ |
| $D$ | $10^{-3}$ | main radial cell width (weak diameter $\le10D$) |
| $g$ | $10^{-14}$ | seed-grouping cell width |
| $j$ | $10^{-20}$ | detectable drop at a separating tip (28) |
| $\epsilon$ | $10^{-24}$ | error in a descending path (25) |
| $E_A$ | $\epsilon/1000$ | interpolation error in $A$ |
| $E_B$ | $10^{-3}R$ | interpolation error in $B$ |
| $\zeta_A,\ \zeta_B$ | $\epsilon/100,\ 1/10$ | Lipschitz slack in Theorem 4.1 |
| $a_1$ | free, within Thm. 4.1 bound for $(\zeta_A,E_A)$, Lemmas 2.11–2.12, and $a_1\le10^{-6}E_A$ | broad band width |
| $a_2$ | free, within Thm. 4.1 bound for $(\zeta_B,E_B)$, and $a_2\le10^{-6}\min\{a_1,\kappa_Aj\}$ | narrow band width |
| $\kappa_A,\ \kappa_B$ | $a_1/10^6,\ a_2/10^6$ | label-mass conversion |
| $K,\ \lambda$ | $100,\ R/(10^{12}K)$ | auxiliary field in $B$ |
| $Q=2^m$ | chosen last (§9.3) | scale ratio |
| $M_{\mathrm{pack}}$ | $2+\lceil1600R/g\rceil\approx1.6\times10^9$ | max number of seed groups meeting a $4R$-ball |
| $\rho_{\mathrm{pack}}$ | $j+\epsilon+2a_1$ | seed distance to the extreme paths (34) |
| $p$ | $2^{-(2M_{\mathrm{pack}}+10)}$ | success probability per step (Prop. 9.1) |
| $C$ | $16m/(pb)$ | the constant of Theorem 1.1 |

## 11.3 Theorem 4.1 parameters
$\delta=E/8$, $a_0=10^{-6}\zeta\delta$, $q=\zeta\delta/20$, $\rho_0=\zeta\delta/1000$, $M=\lceil15/\zeta\rceil+3$, $N=6(M+1)$; equality collar $c_0=\zeta\delta/50$; failure probability $\frac{N^2}{q}(8\rho+\eta)$.

## 11.4 Equation index (selected)
(2) radial bounds; (4) threshold sets; (5) cut-distance identity; (6) Thm. 4.1 parameters; (8) interpolation failure probability; (13)–(15) accuracy; (17) fresh-noise bound; (18) Cor. 4.6; (19) cutoffs for the detailed tests; (20) cell Lipschitz bound; (21)–(24) the main replacement; (25)–(26) descending paths; (28)–(29) tip drop and its robustness; (30) packing number; (35)–(40) clipping data and proposals; (41) increment; (42) chart persistence; (43) choice of $Q$.
