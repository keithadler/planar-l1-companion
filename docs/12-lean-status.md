# 12. Lean status: what is machine-checked, and what that does and does not mean

Tags as in the [README](../README.md). **The Lean sources are not yet public.** They live in a private repository and are being prepared for publication under Apache-2.0 (the licence Mathlib uses). Until then, everything below is the notes' author's report; once published, each claim can be checked by running the Lean compiler.

## 12.1 What a Lean check does and does not establish

A formalised theorem is a statement in Lean's logic together with a proof checked by Lean's kernel. It establishes that the *formal statement* follows from the *stated hypotheses* using only the three standard axioms (`propext`, `Classical.choice`, `Quot.sound`). It does **not** establish that:

* the formal statement says what the paper says (this is checked by a human reading both side by side);
* the hypotheses taken from other sections (Theorem 4.1, Lemmas 2.11/2.12, …) are true, or are the authors' own;
* the paper's overall argument is correct.

This work is **conditional**: every result from another section that a formalised lemma depends on is an explicit hypothesis, never an axiom and never `sorry`.

## 12.2 What exists

Three pieces of Lean 4 / Mathlib (toolchain `v4.34.1`), one per area. Each file compiles with no errors or warnings, contains no `sorry`, no `native_decide`, no new `axiom`; an audit of *every* theorem and definition in each file (not only the headline ones) found no axiom outside the three standard ones.

| Piece | Paper | Declarations audited | Compile time |
|---|---|---|---|
| Refinement and gluing | §3.2 | all in the file | 39 s |
| Charts: identity (5), nesting, rebasing | §3.1 | 50 | 17 s |
| Constants | §5.1 | 59 | 10 s |
| Main update, descending paths, certificates | §6.1–6.2 | 84 | 8 s |

### Refinement and gluing (§3.2)

* **Lemma 3.2.** (a) $\tilde d\ge\mu(A_p\triangle A_q)$ and $\tilde d\le L$ for every path of length $L$; pseudometric axioms; measurability of the integrand. (b) $\rho_\omega(p,q)=2$ for a non-neighbour link with inactive tip and strictly opposite active points; and the integrated form $2\mu((A_p\cap A_q)\setminus A_e)\le\tilde d(p,q)$.
* **Exact gluing.** One proposal over one domain: nested, switch-respecting, vertical-length bound for the glued system, for arbitrarily many updated intervals.
* *Hypotheses (structure fields):* a column model with compact switch sets, noncrossing links and the terminal condition (Definition 2.1; the circle is cut open into a linear order); a system of sets (measurable, nested, respecting switches, vertical-length bound); the label law only through $\mu\{\sigma=s,\ a\le Z<b\}=\tfrac12(b-a)$; for gluing, $\kappa L<1$, old sets equal chart sets of $P$ on the domain, $P$ and the proposal vertically $L$-Lipschitz and switch-respecting inside the domain, proposal $<P$ on the boundary.
* *Differences from the paper:* distances are $[0,\infty]$-valued integrals (no subtraction of a reference vector); unrestricted column distance in place of $d_I$; one proposal at a time; "sum to the vertical length" is proved as $\le$.

### Charts (§3.1, Lemma 3.1)

* Identity (5) for $\kappa\ge0$ on an arbitrary label space carrying chart labels; nesting and the vertical-length equality for points of a set on which $P$ is $L$-Lipschitz in height with $\kappa L\le1$ (the paper has $<1$; the weaker hypothesis is more general); the pointwise rebasing identity $\{Z<\varphi_\sigma(h)\}=\{Z'<h\}$; and the law of $Z'$ together with a *fresh* sign, on both a concrete space $\mathbb R\times\{\pm1\}$ and the paper's $\mathbb R\times\{\pm1\}^{\mathbb N}$.
* *Not modelled:* "respects switches" (this belongs to the column graph).

### Constants and the main update (§5.1, §6.1–6.2)

* Every numerical inequality of §5.1 that later lemmas use, as named theorems, from the explicit values; a structure `Choice` for the free choices $a_1,a_2$ with exactly the paper's hypotheses, together with a proof that it is nonempty.
* Lemma 6.1 (frontier and band-end margins; $0\le s'-s\le1+10D$; vertical Lipschitz constant with $\kappa_A\max\{1,3/(0.09a_1)\}<1$; agreement of two cells at a common frontier point; the label-measure bound $\kappa_A(1+10D)$), Definition 6.2 and (26), Lemma 6.3, Corollary 6.4 (probability $\ge\tfrac14$ over the two cell coins), Lemma 6.5 and formula (29).
* *Hypotheses (structure fields or arguments):* the paper's inequality (23) and the $1$-Lipschitz property of $F_C$ (a `Setup` structure; a constructor builds one from a Theorem 4.1 output, so nothing is lost); Lemma 2.11 (cell diameter $\le10D$, compact frontier); Lemma 2.12 (padding $d(w,z)>0.01D$); existence of shortest paths; Lemma 3.2 enters Lemma 6.5 and (29) as a hypothesis on per-label contributions and is **not** connected to the column model of the refinement piece.
* *Differences:* one sign coordinate; the plateau hypothesis is the weaker $0.09a_1$ margin, so the Lean statement is stronger than the paper's "outer tenths" requirement; Corollary 6.4 does not need $d\le2$; Lemma 6.5's link-geometry hypotheses are omitted because the measure computation does not use them.

## 12.3 How these were checked (and by whom)

* **Compilation and axiom audit:** by the notes' author, independently of the agents that wrote the Lean files, by compiling each file with Lean and running an audit that collects the axioms of every declaration in it.
* **Fidelity of statements:** the author read the definitions and the main statements side by side with the paper (Definition 2.1, Lemma 3.2, identity (5), rebasing, Lemma 6.1, 6.3, 6.4, 6.5, (29), Constants). The proofs were **not** read; they are checked by Lean's kernel.
* **No expert has reviewed any of this.** A reader who finds a statement that differs from the paper should treat that as a defect of the formalisation.

## 12.4 Not done

Theorem 4.1 and the geometric Lemmas 2.9–2.13; the charts-and-identifiers bookkeeping and the probability space of a step; Sections 6.3, 7, 8 and 9; the connection between the refinement piece and the update piece. These are exactly the parts in [10](10-where-to-look.md) where human attention matters most.
