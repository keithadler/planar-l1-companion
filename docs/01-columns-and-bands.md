# 01. Column models, circular order, portals, radial cells (paper §2)

Status tags as in the [README](../README.md). Everything in this note is **[stated]** unless tagged.

## 1.1 Definition 2.1 (column model)

A *column model* consists of a finite cyclically ordered index set $V_0$; for each $i\in V_0$ a copy $\lbrace i\rbrace \times\mathbb R$; and a finite set of *links* $ij$, each with a closed bounded set $S_{ij}=S_{ji}\subset\mathbb R$ of *switch heights*. The quotient $X$ identifies $(i,H)\sim(j,H)$ for $H\in S_{ij}$; $h(i,H)=H$. A *path* is a finite concatenation of vertical segments and switches; its length is the sum of the vertical lengths; $d$ is the infimum of lengths.

* **Noncrossing.** No two links have four distinct endpoints alternating in the cyclic order.
* **Terminal switches.** Every link $ab$ between *nonconsecutive* indices has $S_{ab}=\lbrace H_e\rbrace $ (the *tip*), and neither $a$ nor $b$ has a switch above $H_e$.
* For a closed interval $I\subset\mathbb R$: $X_I=h^{-1}(I)$; $d_I$ is the intrinsic metric of paths staying in $I$ (distance $+\infty$ between components); $G_I$ is the *active column graph*, with vertex set $V_0$ and an edge $ij$ whenever $S_{ij}\cap I\ne\varnothing$.

*Lemma 2.2.* $d_I$ is a metric on each component of $X_I$; finite distances are attained by paths using each column at most once; components of $X_I$ correspond to components of $G_I$; bounded closed subsets of components are compact.

## 1.2 Proposition 2.3 (planar graphs have column models)

Let $G$ be a finite connected plane graph with positive edge lengths, $o$ a root, $T$ a shortest-path tree, $h(v)=d_G(o,v)$. For each non-tree edge $e=uv$ of length $\ell_e$ attach twigs at $u$ and $v$ of lengths
$$\frac{\ell_e+h(v)-h(u)}{2},\qquad\frac{\ell_e+h(u)-h(v)}{2}\qquad(\ge 0\text{ since }|h(u)-h(v)|\le\ell_e),$$
whose tips both have height $H_e=\tfrac12(\ell_e+h(u)+h(v))$ and are identified. The enlarged tree has one column per root-to-leaf path, in the cyclic contour order of the plane leaves; consecutive leaves are linked at the heights of their common root prefix. The tip links are noncrossing because two disjoint arcs in a disc cannot have alternating endpoints; every non-neighbour link is a single terminal switch. Extra tails do not shorten original distances. (Figure 1 of the paper: $\ell_e=3$, $h(u)=2$, $h(v)=3$ gives twigs of lengths $2,1$ and $H_e=4$.)

## 1.3 Consequences of the circular order (§2.1)

Let $\Gamma$ be a noncrossing circular graph.

* **Lemma 2.4 (chord separation).** For an edge $uv$, any path from the strict interior of one $u$–$v$ arc to the strict interior of the other visits $u$ or $v$.
* **Lemma 2.5 (gaps).** If $S$ is a nonempty connected vertex set, every path avoiding $S$ lies in one open circular gap between consecutive vertices of $S$.
* **Lemma 2.6 (skipping).** A walk in an open arc passing over an index $i$ either visits $i$ or uses an edge with endpoints strictly on both sides of $i$ (a non-neighbour link); a second path starting strictly inside that edge's interval and leaving it visits an endpoint.
* **Lemma 2.7.** Every $G_I$ is outerplanar and has no $K_{2,3}$ minor. *(Proof: join a new vertex of the complementary disc to all column vertices; a $K_{2,3}$ minor would give $K_{3,3}$ in a planar graph on six vertices, but simple planar bipartite graphs on six vertices have at most 8 edges.)*
* **Lemma 2.8.** For a component of $X_I$, a source $o$, and $H\in I$, the sets $\lbrace i:d_I(o,(i,H))\le t\rbrace $ are connected in $G_I$.

## 1.4 Portals and radial cells (§2.2)

Fix a closed band $J$ of width $a>0$ with midheight $H_*$, a component $Y$ of $X_J$, a basepoint $o\in Y$ at height $H_*$, and the *radial coordinate* $b_i=d_J\big(o,(i,H_*)\big)$. Then for $v=(i,H)\in X_J$ and linked $i,j$:
$$d_J(o,v)-b_i\le a/2,\qquad|b_i-b_j|\le a.\tag{2}$$

* **Lemma 2.9 (two portals).** Let $C$ be a component of the subgraph of $G_J$ induced by $\lbrace i:b_i\ge t\rbrace $; an *entrance column* is an $i\in C$ adjacent to some $j$ with $b_j<t$. If entrance columns exist, there are at most two points (*portals*), each of radial value in $[t,t+a)$, such that every point on every entrance column is within $d_J$-distance $200a$ of a portal. *(Proof idea: three entrance points pairwise $>100a$ apart give three vertex-disjoint connectors between the connected sets $C$ and $L=\mathrm{proj}B_{d_J}(o,t-12a)$; contraction gives a $K_{2,3}$ minor, contradicting Lemma 2.7.)*
* **Definition 2.10 (radial cells).** For $D>0$ and an offset $\theta\in[0,D)$, group indices by $\lfloor (b_i-\theta)/D\rfloor$ into *layers*, and split each layer into connected components of its induced subgraph of $G_J$. A *cell* is the image in $X_J$ of the corresponding column intervals. Its *frontier* $\partial C$ is the image of the columns adjacent in $G_J$ to an index outside the cell. A quotient point shared by two cells lies in the frontier of both.
* **Lemma 2.11.** If $a\le D/1000$, every cell is compact and path-connected and has weak diameter (measured in $d_J$) at most $10D$.
* **Lemma 2.12 (padding).** If $\mathrm{dist}(b_i,\theta+D\mathbb Z)>\rho+2a$, every point reachable from $v=(i,H)$ by a band path of length $\le\rho$ has all its representatives in the cell of $i$, and $d_J(v,\partial C)>\rho$. For $\theta$ uniform on $[0,D)$ the condition fails with probability at most $\min\lbrace 1,2(\rho+2a)/D\rbrace $. In particular, if $a\le D/1000$ and the radial values of two points are at distance $>0.02D$ from the thresholds, their distances to the frontier exceed $0.01D$, and points in different cells are at $d_J$-distance $>0.01D$.
* **Lemma 2.13 (successive portal levels).** For a step $\delta>1000a$, the components of $\lbrace b_i\ge n\delta\rbrace $ ($n\ge0$) form a rooted tree; each node's own layer and its children's portals lie within $\delta+220a$ of its own portals, and child portals are at distance $\ge\delta-10a$ from own portals.

## 1.5 Points a reader may wish to check

1. *Lemma 2.9, trimming of connectors.* Each connector is trimmed to the segment after its last visit to $C$ and before its first visit to $L$; the claim that its interior is nonempty rests on $|b_i-b_j|\le a$ for adjacent columns versus a radial gap of at least $12a-a/2>a$.
2. *Lemma 2.11, weak diameter.* The bound $4(D+210a)<10D$ uses that a connected set in a union of two balls either lies in one or meets their intersection.
3. *Lemma 2.12.* The statement that no factor for the number of representatives of $v$ is needed rests on their radial values differing pairwise by at most $a$.
4. All constants in this section depend only on $a,D,\delta$, not on $|V_0|$; this is what makes the later estimates uniform in the graph.
