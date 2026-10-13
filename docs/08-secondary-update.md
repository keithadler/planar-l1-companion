# 08. The secondary update: clipping near admitted seeds, and ordered increments (paper §8)

Tags as in the [README](../README.md). **[stated]** unless tagged. Seeds, groups and $M_{\mathrm{pack}}$: [05](05-main-update.md), [06](06-packing.md); ordered fields and $t_s$: [07](07-ordered-fields.md).

**Purpose.** For a pair surviving the main test and the component barrier, either (a) an endpoint is *admitted* in some orientation and *clipping* raises the field near it, or (b) in neither orientation, and then the ordered part of the field rises and falls near both endpoints; Lemma 7.6 puts them on opposite arcs and an *increment* proportional to the transverse field separates them. Clipping and increment are alternative modes at a scale; a newly created ordered chart is available for increments at later scales.

## 8.1 Clipping near admitted seeds

Fix the orientation of the old $B$ chart. The comparison field is $p_*=s$ in an ordinary chart, and one of $P,-P$ in an ordered chart (chosen fairly, shared by the whole old identifier). For each group choose a representative $w_c$, $p_c=p_*(w_c)$. By the weak diameter bound of its $g$-cell and old-chart eligibility,
$$|p_*(w)-p_c|\le60g\qquad\text{at every seed }w\text{ of the group.}\tag{35}$$

**Ordered support.** In an ordinary chart choose (Lemma 7.2, source of $s$, target $w_c$) an ordered $L$ with
$$L\le p_*,\qquad L(w_c)=p_c,\qquad\mathrm{Lip}_{\mathrm{vert}}(L)\le1\tag{36}$$
($L=0$ in a constant chart). All seeds of an ordinary chart are *admitted*. In an ordered chart a seed $w$ is **admitted in the chosen orientation** if
$$p_*(v)\ge p_c-0.65R\quad\text{whenever }d_{J_2}(w,v)=R\tag{37}$$
(vacuous if the sphere is empty). These decisions use no fresh clipping noise.

**Proposals.** Each group gets one independent fair coin; $w_c$, $p_c$, the orientation and $L$ are common to all its narrow-band components. For a kept group let $F$ be its admitted seeds in one narrow-band component (if nonempty), $d_F(v)=\min_{w\in F}d_{J_2}(w,v)$. Apply Theorem 4.1 to $0.9d_F$ on the whole component with error $E_B$ to get $Q_F$; on $U_F=\lbrace d_F\le R\rbrace $ the proposal is the minimum of
$$T_F=p_c+0.05R-Q_F\ (38),\qquad O_F=p_c+0.05R+4(L-p_c)+\alpha_F\ \text{(ordinary charts only)}\ (39),\qquad H_F=\psi_F(h)\ (40).$$
Here $\alpha_F\in[0,E_B]$ is uniform and independent of the interpolation noises; $\psi_F$ equals $p_c-1+\alpha_h$ at both ends of $J_2$, rises linearly to $p_c+2+\alpha_h$ within $0.09a_2$ of each end and is constant on the plateau ($\alpha_h$ uniform on $[0,E_B]$, independent). $p_*$ is replaced by its maximum with the proposals of all kept groups on their domains, and converted back to the old orientation. Conditional on old charts, bands, groups, orientations, admissions and coins, all interpolation and branch noises are fresh, and the noise families of different groups are independent.

**Lemma 8.1 (validity).** The secondary update preserves the nested-set and chart invariants, and its movement at each point, in symmetric difference, is bounded by a universal constant in scale units.

*Key estimates.* At a point with $d_F(v)=R$: $T_F(v)\le p_c+0.05R-0.9R+E_B=p_c-0.849R$. In an ordered chart a nearest admitted seed gives $p_*(v)\ge p_c-0.65R$, a margin of $0.199R$; in an ordinary chart the same margin applies when that inequality holds, and otherwise $L\le p_*$ gives $O_F-p_*\le0.05R+3(p_*-p_c)+E_B<-1.899R$. So every proposal lies below the old field by a uniform margin on every distance boundary. At height ends the shield gives a margin as well: each domain point lies within $R$ of a seed within $10g$ of $w_c$, and the old comparison has Lipschitz constant $<5$ on these eligible paths, so its difference from $p_c$ is $<5(R+10g)<\tfrac12$. The spatial branches have Lipschitz constant $\le4$ and the shield $3/(0.09a_2)<1/\kappa_B$. A winning atom of $Q_F$ gives a fresh ordinary chart on its narrow-band component; a winning $O_F$ branch becomes the ordered part of a new chart with $u=0$ and slope $\le4$ (reversing the boundary columns if the conversion negates the field); a height branch is rebased (Lemma 3.1). Movement is bounded because $Q_F$ is within $E_B$ of $0.9d_F$, so the shallow branch is at most $p_c+0.051R$ while the old field is within $5(R+10g)$ of $p_c$ where a group can act; a maximum over any number of groups does not add these bounds; then (5).

**Lemma 8.2 (separation at admitted seeds).** If a surviving pair has a seed admitted for one comparison orientation, the no-change and secondary-clipping modes together separate it by a universal positive amount with probability bounded below by a universal positive constant.

*Proof sketch.* At an admitted seed $|Q_F(w)|\le E_B$, and (35)–(36) imply every applicable spatial branch exceeds $p_*(w)+0.04R$ (for $O_F$ use $|L(w)-p_c|\le10g$); the height shield is on its interior plateau; the other endpoint lies outside this group's domains because a group's seeds have unrestricted diameter $\le10g$ and the pair distance is $\ge1$. At either endpoint all groups that could act have a seed within $R$ in the narrow band, so at most $2M_{\mathrm{pack}}$ groups can act; keeping the designated group and suppressing the others has probability $\ge2^{-(2M_{\mathrm{pack}}+1)}$; the orientation, when needed, has probability $\tfrac12$. On this event one endpoint is unchanged and the other moves by $\ge0.04\kappa_BR$. If $\mu(B_x\triangle B_y)\ge0.01\kappa_BR$ the no-change mode already gives the separation; otherwise the triangle inequality gives $\mu(B'_x\triangle B'_y)>0.03\kappa_BR$. Each mode has probability $\tfrac14$.

## 8.2 The increment in ordered charts

For an ordered identifier the ordered part $s$, band $I$ and arc assignment stay fixed, so $t_s$ is fixed. Let $\mathfrak H:[0,\infty)\to[0,1]$ be the trapezoid vanishing off $[0.005R,10]$, equal to $1$ on $[0.01R,8]$ and linear in between. At scale $r$ (original units) add to $u$
$$\pmt_s(v)\mathfrak H\big(|t_s(v)|/r\big)\min\lbrace 1,\ d(v,X\setminus\mathcal R)/r\rbrace ,\tag{41}$$
with a fair sign common to the old identifier ($\mathcal R$ = current region; the factor is $1$ if the complement is empty). Old terms of $u$ are retained.

**Lemma 8.3 (increment bound).** If $Q>2000/R$, all increments of one ordered identifier together have $d_I$-Lipschitz constant $\le K=100$; they preserve the nested sets, introduce no chart interfaces, and move each point by at most a universal constant times the scale.

*Proof sketch.* $t_s$ is $4$-Lipschitz in $d_I$ (Lemma 7.4); $\tau\mapsto\tau\mathfrak H(|\tau|/r)$ has Lipschitz constant $\le6$ and magnitude $\le10r$; the distance factor has constant $\le1/r$; each increment therefore has constant $\le24+10=34$. Its support lies in $0.005Rr<|t_s|<10r$; as $t_s$ is fixed for this identifier, supports at distinct scheduled scales are disjoint when $Q>2000/R$; in a comparison of two points at most two summands are nonzero at either endpoint, giving $\mathrm{Lip}(u)\le68<K$. The distance factor makes the movement vanish continuously at the region boundary; inside the region the new field has constant $\le4+\lambda K<5<1/\kappa_B$.

**Lemma 8.4 (the remaining pairs).** If a surviving pair has no admitted endpoint in either ordered orientation, the increment mode separates it by a universal positive amount with uniformly positive probability.

*Proof sketch.* Normalise the scale to $1$. Ordinary charts admit every seed, so the old $B$ chart is ordered. Failure of each admission test supplies a point on the $d_{J_2}$-sphere of radius $R$ and an attaining path of length $R$; failure for $P$ gives a decrease of $P$, failure for $-P$ an increase, each of magnitude $>0.65R-60g$ by (35). The correction $\lambda u$ changes by $\le\lambda KR$ on either path, so $s$ has a positive and a negative change of magnitude $>0.65R-60g-\lambda KR>0.4R$ along paths from each endpoint. A shortest $x$–$y$ path has length $\le2$ and lies in the eligible radius-5 ball, hence in the old band $I$, so $d_I(x,y)=d(x,y)$ and $u$ changes by $\le2K$ along it; the $B$-cutoff (19) gives $|s(x)-s(y)|\le10^{-4}R+2\lambda K<0.001R$. The four excursion paths lie in the common band $J_2$, whose width satisfies the hypothesis of Lemma 7.6, which gives opposite signs of $t_s$ and $0.01R\le|t_s(x)|,|t_s(y)|\le8$. These values lie on the plateau of $\mathfrak H$; eligibility puts the radius-5 balls in $\mathcal R$ so the distance factor is $1$. For one of the two increment signs $|P_{\rm new}(x)-P_{\rm new}(y)|\ge\lambda|t_s(x)-t_s(y)|\ge0.02\lambda R$, hence by (5) separation $\ge0.02\kappa_B\lambda R$, with probability $\ge\tfrac12$.

## 8.3 Points a reader may wish to check

1. **(37) and the sphere.** The admission test is on the $d_{J_2}$-sphere of radius $R$; Lemma 8.4 extracts from its failure a path of length exactly $R$ on which $p_*$ changes by more than $0.65R-60g$. Check that the group-wise bound (35) applies in *both* orientations.
2. **Lemma 8.3, disjoint supports.** It uses $t_s$ fixed per identifier; scheduled scales in one schedule differ by $Q=2^m$ and the support ratio is $10/(0.005R)=2000/R$.
3. **Lemma 8.1 at the height ends.** The bound $5(R+10g)<\tfrac12$ is generous; the shield only needs to lie below the old field there.
4. **Lemma 8.2's probability.** $2^{-(2M_{\mathrm{pack}}+1)}$ is a lower bound for isolating one designated group among at most $2M_{\mathrm{pack}}$ others by independent fair coins; the orientation coin contributes a further factor $\tfrac12$.
