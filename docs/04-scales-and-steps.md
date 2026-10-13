# 04. Scales, constants and the local experiment (paper §5)

Tags as in the [README](../README.md). **[stated]** unless tagged **[hand]**.

This section fixes the parameters and the randomness of one step. It contains no new estimates; its role is to make every later inequality a consequence of an explicit choice of constants.

## 4.1 The constant hierarchy (§5.1)

$$\epsilon\ \ll\ j\ \ll\ g\ \ll\ R\ \ll\ D\ \ll\ 1.$$

| Symbol | Role |
|---|---|
| $D,\ R,\ g$ | main radial cell width; secondary-update radius; radial width for grouping seeds |
| $j,\ \epsilon$ | detectable drop at a separating tip; error in a descending path |
| $a_1,\ a_2$ | broad and narrow band widths (control vertical transfers and interpolation) |
| $E_A,\ E_B$ | interpolation errors in systems $A$, $B$ |
| $\kappa_A,\ \kappa_B$ | convert field variation into label mass while keeping vertical nesting |
| $\lambda$ | size of the auxiliary correction in system $B$ (§8.2) |
| $Q$ | scale ratio (controls earlier chart splitting and later movement) |

**Explicit values** (all other constants follow, in this order):
$$R=10^{-8},\ D=10^{-3},\ g=10^{-14},\ j=10^{-20},\ \epsilon=10^{-24},\ E_A=\tfrac{\epsilon}{1000},\ E_B=10^{-3}R,\quad\zeta_A=\tfrac{\epsilon}{100},\ \zeta_B=\tfrac1{10}.$$

1. Choose $a_1>0$ within the width bound of Theorem 4.1 for $(\zeta_A,E_A)$, within the bounds of Lemmas 2.11 and 2.12 for $D$ and $g$, and with $a_1\le10^{-6}E_A$. Set $\kappa_A=a_1/10^6$.
2. Choose $a_2>0$ within the bound of Theorem 4.1 for $(\zeta_B,E_B)$ and with $a_2\le10^{-6}\min\{a_1,\kappa_Aj\}$. Set $\kappa_B=a_2/10^6$.
3. Reserve $K=100$ as the Lipschitz bound for the auxiliary field in $B$ (Lemma 8.3); set $\lambda=R/(10^{12}K)$.
4. If necessary decrease $a_1,a_2$ further to meet the thin-band hypotheses of the geometric lemmas, then choose dependent constants in the order just given. Every step is an upper bound on a newly chosen positive number, so the choice is not circular.
5. The scale spacing $Q=2^m$ is chosen **last** (§9.3).

**Two inequalities used repeatedly** **[hand]** (both follow from the displayed choices): $E_A\le j/4$ since $E_A=10^{-27}\le\tfrac14\cdot10^{-20}$; and $a_2\le\kappa_Aj/4$ from step 2. (Lean statements of this kind are the subject of the pending Task C; see [12](12-lean-status.md).)

## 4.2 Scales and schedules

Choose finitely many dyadic scales so that every nonzero vertex distance lies in some $[r,2r)$. For each residue class of the exponent modulo $m$, run **one schedule** in decreasing order of its scales (so successive scales in a schedule differ by the factor $Q=2^m$). In the analysis of a step, distances, heights, fields and their additive constants are divided by the scale $r$; resulting changes are multiplied by $r$ before being applied in the original label space. A change $\Delta P$ in scale units moves label mass $r\kappa|\Delta P|$. The label coordinates $(Z,\sigma)$ are never resampled or renormalised.

## 4.3 The data of one step (§5.2)

* **Bands.** Tile the height line by intervals $J_1$ of width $a_1$ with a common random shift, and independently by intervals $J_2$ of width $a_2$. Process every broad or narrow band meeting $[\min_vh(v)-6,\max_vh(v)+6]$ in current scale units, making no clipping update elsewhere; the decision to process a band is common to the whole band.
* **Radial data.** Fix radial basepoints in the band components *before* sampling radial layer origins. In every broad-band component form the width-$D$ and width-$g$ radial cells with independently shifted origins. The narrow bands determine the domains of the secondary proposals and the balls in the packing estimate. Interpolation basepoints and portals are fixed before any interpolation noise.
* **Interior vertices.** A vertex is *interior* if its narrow band lies in its broad band, its height avoids the outer tenths of both bands, and all its column representatives have radial values farther than $0.02D$ and $0.02g$ from the respective layer interfaces. A pair with height difference $<10^{-4}a_2$ is interior in common bands with probability $\ge\tfrac14$ (each of the two height tests fails with probability $\le0.21$; each radial test, for two vertices together, with probability $\le0.081$; the remaining allowance covers column-width and grid errors).
* **Eligible pairs.** At the current scale use the finite list of eligible original pairs with $1\le d(x,y)<2$ (scale units), eligibility meaning that the two closed balls $B_d(x,5)$, $B_d(y,5)$ lie in one old chart region in system $A$ and in one in system $B$. For the detailed tests impose
$$|h(x)-h(y)|<10^{-4}a_2,\qquad|s_A(x)-s_A(y)|<E_A,\qquad|P_B(x)-P_B(y)|<10^{-4}R,\tag{19}$$
where $s_A$ is the ordinary orientation and $P_B$ the full old field. Failure of a cutoff already gives positive separation by (5), so it is handled by the *no-change* mode.
* **Modes.** Four equally likely modes: *no change*, *main update in $A$*, *secondary clipping in $B$*, *ordered increment in $B$*. Surviving groups and admissions are defined in §§6.2 and 8. Cell and group coins are independent fair coins. Where the secondary construction calls for a fair sign, all points of one old chart identifier use the same sign, independent of the label sign $\sigma$.
* **Order of randomness.** Bands and cells, then eligible pairs, surviving groups and admissions, and *finally* fresh interpolation and branch offsets. Conditioning on the earlier choices leaves the offsets independent; in particular no admission decision examines a newly selected interpolation atom.
* **Finite grids.** All bounded-interval geometric randomisations may use finite equally spaced grids of relative mesh $\le\eta_0$ (smaller than every finer-to-coarser scale ratio). An interval probability bound $C\rho$ then becomes $C'(\rho+\eta_0)$. Everything is a finite execution tree, so the final random mixture is a finite direct sum and no selection-measurability issues arise.

## 4.4 What this section is *for*

Sections 6–8 prove, for a pair $(x,y)$ eligible at scale $r$, that one of the four modes produces a separation certificate with probability bounded below by a function of the constants above. Section 9 then needs exactly three consequences: movement $\le Mr$, success probability $\ge p$, chart persistence $\le C_0(\rho+\eta_0)$ (see [02, §2.5](02-charts.md)). The constants here ensure that $M,C_0,b,p,\rho_0$ depend on nothing else.

## 4.5 Points a reader may wish to check

1. **Consistency of the hierarchy.** Each later lemma assumes inequalities of the form "(small constant) $\le$ (larger constant)/(power of ten)"; collecting them in one table and checking each against the explicit values is a mechanical but useful audit. The values $R=10^{-8}$, $g=10^{-14}$ give $R/g=10^6$, hence $M_{\mathrm{pack}}=2+\lceil1600R/g\rceil\approx1.6\times10^9$.
2. **Why $Q$ is chosen last.** $Q$ must satisfy $Q>2000/R$ (Lemma 8.3), $20/Q<\rho_0$, $40C_0/(Q-1)<\tfrac12$ and $6M/(Q-1)<b/2$ (§9.3). These involve $M,C_0,b,\rho_0$, which depend on the other constants but not on $Q$.
3. **Randomness order.** The claim "no admission decision examines a newly selected interpolation atom" is what makes Corollary 4.6 applicable in Proposition 9.2; it is easy to lose track of in §§6–8.
4. **Finite grids.** The mesh $\eta_0$ is introduced "after the finite set of scales is fixed"; confirm that none of $C_0,\rho_0$ depends on it.
