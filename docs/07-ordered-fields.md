# 07. Ordered fields and separation on the two arcs (paper §7)

Tags as in the [README](../README.md). **[stated]** unless tagged. Throughout, $\mathcal C$ denotes the circular order of columns and $I$ a closed band; all fields are defined on all of $X_I$, including separate components.

**Purpose.** When secondary clipping fails (no seed admitted in either orientation), §8.4 produces, at both endpoints, short paths along which a fixed *ordered* field rises and falls. This section constructs (a) ordered fields below a point-distance function, and (b) a *signed transverse coordinate* $t_s$ which, by a topological argument on the circle, takes opposite signs at the two endpoints; an increment proportional to $t_s$ then separates them.

## 7.1 Ordered fields

**Definition 7.1.** Let $a\ne b$ be column indices. A real field $s$ on $X_I$ is **ordered from $a$ to $b$ with slope bound $M$** if it respects every switch, is $M$-Lipschitz on every vertical column, and for each $H\in I$ is nondecreasing on each of the two circular arcs oriented from $a$ to $b$ (the *positive* and *negative* arcs, either assignment). In particular $s(a,H)$ is a minimum and $s(b,H)$ a maximum at height $H$. Adding constants preserves the notion; multiplication by $c>0$ multiplies the slope bound by $c$; $-s$ is ordered with $a,b$ interchanged; a function of height alone is ordered for any choice of $a,b$.

**Lemma 7.2 (ordered support of a point distance).** Let $k,w$ lie in one component of $X_I$. There is an ordered field $L$ of slope bound $1$ with
$$L(k)=0,\qquad L(w)=d_I(k,w),\qquad L(v)\le d_I(k,v)\quad(v\in X_I)$$
($d_I=+\infty$ across components).

*Proof sketch.* If $D=d_I(k,w)=0$ take $L\equiv0$; if $k,w$ share a column take $L(v)=\min\lbrace |h(v)-h(k)|,D\rbrace $. Otherwise choose representatives $a\ni k$, $b\ni w$ on different columns and put $f_i(H)=\min\lbrace d_I(k,(i,H)),D\rbrace $ ($=D$ on components not containing $k$): each $f_i$ is $1$-Lipschitz, respects switches, and $f_a(H)=\min\lbrace |H-h(k)|,D\rbrace =\min_if_i(H)$ (7.2.1). For $t\le D$ the strict sublevel $\lbrace i:f_i(H)<t\rbrace $ is connected in $G_I$ and contains $a$ (the prefix of a path of length $<t$ followed by vertical travel stays below $t$). For a link $pq$ at height $H$ with $c=f_p(H)=f_q(H)$ and $a\notin\lbrace p,q\rbrace $, with $[p,q]_a$ the closed circular interval from $p$ to $q$ not containing $a$:
$$f_z(H)\ge c\qquad(z\in[p,q]_a)\tag{7.2.2}$$
(a strict-sublevel path from $z$ with $f_z<c$ to $a$ would avoid $p,q$ while $z$ is strictly inside $[p,q]_a$, contradicting Lemma 2.4). Cut the circle at $a$ and put
$$L(i,H)=\min_{z\in[i,b]_a}f_z(H),\qquad L(a,H)=f_a(H).\tag{7.2.3}$$
These are finite minima of $1$-Lipschitz functions; along either arc from $a$ to $b$ the intervals shrink so $L$ is nondecreasing, with initial value a lower bound by (7.2.1). Switches are checked explicitly using (7.2.2) (if the link meets $a$ both values are the global minimum; otherwise the minimum over the shorter interval equals $c$ and the longer interval is the union with $[p,q]_a$, whose minimum is $\ge c$). Finally $L\le f_i\le d_I(k,\cdot)$, $L(k)=0$, $L(w)=D$. $\square$

## 7.2 The transverse coordinate

**Definition 7.3.** Let $s$ be ordered from $a$ to $b$ with slope bound $4$. In $\mathbb R^2$ put
$$Z_s=\lbrace (s(a,H),H),(s(b,H),H):H\in I\rbrace \ \cup\ \lbrace (s(p,H),H):\ H\in I\cap S_{pq},\ p,q\text{ on opposite open arcs}\rbrace .$$
For a representative $(i,H)$ set $t_s(i,H)=+\mathrm{dist}_\infty\big((s(i,H),H),Z_s\big)$ if $i$ is on the positive arc, $-\mathrm{dist}_\infty(\cdot)$ if on the negative arc, and $0$ for $i\in\lbrace a,b\rbrace $.

**Lemma 7.4.** $t_s$ is well defined on $X_I$, respects all switches, and is $4$-Lipschitz for $d_I$. *(The map $H\mapsto(s(i,H),H)$ is $4$-Lipschitz for the max norm and distance to a fixed nonempty set is $1$-Lipschitz; at a switch between two columns of one open arc both values coincide because $s$ and $h$ do; at a switch between opposite open arcs, or involving $a$ or $b$, the common image lies in $Z_s$ so both values vanish.)*

## 7.3 Excursions force opposite arcs

A path "stays within length $A$ of $x$" if each of its points is joined to $x$ by a path of length $\le A$ in $X_I$.

**Lemma 7.5 (overlapping traversals on one arc).** Let $J\subset I$ have width $\eta$; $s$ ordered with slope bound $4$; $\Gamma_x,\Gamma_y$ paths in $X_J$ using only columns of the same open arc, $\Gamma_x$ within length $A_x$ of $x$, $\Gamma_y$ within $A_y$ of $y$. If the range of $s$ on each path contains an interval $[u,v]$ with $v-u>32\eta$, then $d(x,y)\le A_x+A_y+2\eta$.

*Proof sketch.* With $H_*\in J$ and $q_i=s(i,H_*)$ (nondecreasing in the linear order of the arc and $|s(i,H)-q_i|\le4\eta$), pick a point of $\Gamma_x$ of value $c=(u+v)/2$ on a column $i$. The initial column of $\Gamma_y$ has reference value $\le u+4\eta<q_i$ and its terminal column $\ge v-4\eta>q_i$, so its column word starts strictly before $i$ and ends strictly after. Either it visits $i$ (join vertically, cost $\le\eta$) or Lemma 2.6 gives a switch $pq$ on $\Gamma_y$ with $p<i<q$, $|q_p-q_q|\le8\eta$, $q_p\le q_i\le q_q$; the endpoints of $\Gamma_x$ lie strictly outside the interval bounded by $pq$ (as $(v-u)/2>16\eta$) while the middle point is strictly inside, so by Lemma 2.4 $\Gamma_x$ visits $p$ or $q$; connect at cost $\le2\eta$. $\square$

**Lemma 7.6 (quantitative separation on the two arcs).** Let $R=10^{-8}$, $s$ ordered with slope bound $4$ on $X_I$, and $x,y\in X_I$ with
$$1\le d(x,y)\le2,\qquad d_I(x,y)=d(x,y),\qquad|s(x)-s(y)|\le10^{-3}R.$$
Let $J\subset I$ be a common height interval of width $\eta\le10^{-6}R$ containing $x,y$. Suppose for each $z\in\lbrace x,y\rbrace $ there are paths $\gamma_z^\pm$ in $X_J$ from $z$ of length $\le2R$ with terminal points $z^\pm$ satisfying $s(z^-)<s(z)-0.4R$ and $s(z^+)>s(z)+0.4R$. Then $t_s(x),t_s(y)$ have **opposite signs** and
$$0.01R\le|t_s(x)|,|t_s(y)|\le8.$$

*Proof outline.* (1) $Z_s$ misses the rectangle $\mathcal Q=[s_0-0.2R,s_0+0.2R]\times[H_x-0.02R,H_x+0.02R]$, $s_0=s(x)$: a point $(c,H_0)\in Z_s\cap\mathcal Q$ would come from a boundary column (contradicting extremality, as low-path endpoints have value $<c$ and high-path endpoints $>c$ at height $H_0$, with margin because moving to height $H_0$ changes values by $\le4(0.02R+\eta)\le0.080004R$) or from a crosslink between opposite arcs; in the latter case $(\gamma_z^-)^{-1}\gamma_z^+$ must visit an endpoint of the crosslink (Lemma 2.4), giving an $x$–$y$ path of length $\le4R+2(0.02R+\eta)<1$, contradicting $d(x,y)\ge1$. (2) Hence the $\ell_\infty$-ball of radius $0.01R$ around $(s(x),h(x))$ and around $(s(y),h(y))$ avoids $Z_s$: $|t_s|\ge0.01R$ at both. (3) In the value strip $S=\lbrace s_0-0.18R\le s\le s_0+0.18R\rbrace \cap X_J$ no representative lies on a boundary column and no switch joins opposite open arcs, so any path inside $S$ stays on one open arc. For each of $x,y$ the concatenation $(\gamma_z^-)^{-1}\gamma_z^+$ crosses the strip; the subpath $\Gamma_z$ between the last visit to the lower boundary before the first visit to the upper boundary stays in $S$ on one arc and traverses the full value interval. If $\Gamma_x,\Gamma_y$ were on the same arc, Lemma 7.5 (interval length $0.36R>32\eta$) gives $d(x,y)\le4R+2\eta<1$. So they lie on opposite arcs. (4) Comparing initial subpaths $\Pi_z$ (until first exit from $S$, value range $\ge0.179R$) with $\Gamma_{z'}$ and applying Lemma 7.5 again shows the *centres* are on opposite arcs, hence $t_s(x),t_s(y)$ have opposite signs. (5) Lemma 7.4 and $d_I=d$ give $|t_s(x)|+|t_s(y)|=|t_s(x)-t_s(y)|\le4d_I(x,y)\le8$. $\square$

## 7.4 Ordered charts in system $B$

An ordered chart has field $P=s+\lambda u$, where $s$ is ordered with vertical Lipschitz constant $\le4$ and $u$ is $K$-Lipschitz for $d_I$ ($u=0$ at creation; §8.2 changes $u$ preserving the bound). With $\lambda=R/(10^{12}K)$: $\mathrm{Lip}(P)\le4+\lambda K<5$ for finite $d_I$, as required by the chart invariant. The band $I$, the ordered part $s$, its two boundary columns, the choice of positive arc and the label functions $(Z,\sigma)$ are fixed in original units for the lifetime of an identifier; hence $t_s$ is fixed; the region may shrink and $u$ changes by the prescribed increments.

## 7.5 Points a reader may wish to check

1. **Lemma 7.2, the sublevel connectivity.** "Every nonempty strict sublevel $\lbrace i:f_i(H)<t\rbrace $ is connected and contains $a$" is used with *strict* inequality in (7.2.2); check the case $t=D$ and the convention for components not containing $k$.
2. **Lemma 7.4 and representatives.** The definition of $t_s$ depends on a choice of representative column only through $Z_s$, which contains the images of all switches between opposite arcs; confirm this is what makes $t_s$ independent of the representative.
3. **Lemma 7.6 (3)–(4).** The passage from "full traversals $\Gamma_x,\Gamma_y$ on opposite arcs" to "the centres are on opposite arcs" uses $\Pi_z$, the initial subpath until the first exit from $S$, of value range $\ge0.179R$; the constants $0.18R$ (strip), $0.2R$ (rectangle) and $0.01R$ (ball) must be consistent. The numerical margins quoted in step (1), $0.080004R$, can be re-derived from $4(0.02R+10^{-6}R)$.
4. **Hypothesis $d_I(x,y)=d(x,y)$.** Verified in §8.4 from eligibility (a shortest $x$–$y$ path of length $\le2$ lies in the radius-5 ball, hence in the old band); the section depends on this being supplied by the caller.
