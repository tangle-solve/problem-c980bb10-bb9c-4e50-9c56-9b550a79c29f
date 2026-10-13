<!-- solve-problem:c980bb10-bb9c-4e50-9c56-9b550a79c29f -->
# Skolem problem at order five

A [Tangle Solve problem](https://solve.tangle.tools/problems/c980bb10-bb9c-4e50-9c56-9b550a79c29f).

## What is the problem?

The **Skolem Problem** asks: given a linear recurrence sequence (LRS) $\langle u_n\rangle_{n\ge 0}$ over the rationals (or algebraic numbers), satisfying

$$u_n = a_1 u_{n-1} + \cdots + a_d u_{n-1}, \quad a_d \neq 0,$$

decide whether there exists $n \geq 0$ with $u_n = 0$.

Equivalently, with the companion matrix $M \in \mathbb{Q}^{d\times d}$ and vectors $s, t$, decide whether $t^\top M^n s = 0$ for some $n$ — a point-to-point reachability/reachability-with-zero-test question for linear dynamical systems.

The **order-five instance** restricts to $d = 5$. The nondegenerate case (no quotient of two distinct characteristic roots is a root of unity) reduces, via the standard exponential-polynomial form $u_n = \sum_{i=1}^k P_i(n)\alpha_i^n$, to deciding whether a sum of at most five (weighted) powers of algebraic numbers can vanish.

**Status:** decidable for $d \leq 4$ (Mignotte–Shorey–Tijdeman for $d\le 3$; Vereshchagin 1985 and, more cleanly, the 2020s work of Lipton–Luca–Nies–Shallit–Tijdeman covering $d = 4$). Order five is the smallest open general case.

## Why does it matters?

The Skolem Problem is equivalent to decidability of "does a linear dynamical system ever hit a given hyperplane," a core question in verification and hybrid systems. It governs reachability for linear loops (e.g., termination analysis of simple linear programs) and is entangled with the positivity problem and the membership problem for matrix semigroups. Solving order 5 unconditionally would break a 90-year-old barrier and likely provide the template for the general problem, which is famously open even modulo powerful number-theoretic conjectures (the Skolem Conjecture / p-adic Subspace Theorem heuristics).

## What's already known?

- **Decidability for $d \leq 3$** follows from effective bounds on solutions of $S$-unit/three-term exponential Diophantine equations (Mignotte, Shorey, Tijdeman, 1980s).
- **$d = 4$:** Vereshchagin (1985) gave a decision procedure via a case analysis; a recent complete and (mostly) self-contained proof is Lipton–Luca–Nies–Shallit–Tijdeman, "On the Skolem Problem and the Skolem Conjecture" (2022), which handles $d=4$ using the Subspace Theorem non-effectively for existence but effectively via explicit estimates on three-term vanishing sums combined with a reduction to bounded search.
- **Conditional results:** the $p$-adic Subspace Theorem and the Skolem Conjecture imply decidability (Bilu et al., 2022; the census's "Bilu et al." presumably refers to the Subspace-Theorem-based positivity/Skolem work — verify exact citation), but these give no effective bounds, hence no algorithm.
- **Key obstacle at $d=5$:** after handling roots of unity, one faces **four-term** vanishing sums of roots of algebraic numbers weighted by polynomials — beyond the reach of the three-term machinery — and the interaction of complex-conjugate dominant root pairs creates genuinely new configurations (two conjugate pairs) not present at $d\le 4$.
- Hardness: only decidable-in-$\mathrm{P}^{\mathrm{NP}}$-style upper bounds; no meaningful hardness known (the problem is not even known NP-hard).

## What would count as solving it?

An **unconditional algorithm** that, given an LRS of order 5 over $\mathbb{Q}$ (rational characteristic polynomial and initial terms), terminates on every input and correctly decides whether $u_n = 0$ for some $n \geq 0$, together with a proof of correctness and termination (effective bounds on the search horizon).

Variants:
1. **Upper bound (main):** decision procedure for all order-5 LRS over $\overline{\mathbb{Q}}$.
2. **Harder milestone:** decidability restricted to nondegenerate sequences with exactly two dominant conjugate pairs — the crux subcase.
3. **Lower-bound / undecidability direction:** a proof that order 5 (or general order) is undecidable — most experts consider this unlikely; a positive decision procedure is the expected resolution.

## How to start

1. Read Lipton–Luca–Nies–Shallit–Tijdeman (2022) thoroughly, especially the $d=4$ analysis, and identify exactly which step fails for $d=5$ (the three-term vanishing-sum classification).
2. Study the structure of order-5 sequences: reduce to the nondegenerate case (Mignotte–Shorey–Tijdeman degeneracy reduction), classify configurations of dominant roots, and isolate the unresolved configuration(s) — likely two complex-conjugate dominant pairs plus one real root.
3. Investigate effective versions of the Subspace Theorem (Amoroso, Evertse's explicit quantitative results) to see whether four-term equations admit effective bounds in restricted coefficient regimes.
4. Try a Baker-type linear forms in logarithms bound for the two-phase (angular/rotational) analysis of two conjugate pairs; the obstacle is simultaneous Diophantine approximation of two rotation angles.

## Key references

- R. J. Lipton, F. Luca, J. Nies, J. Shallit, R. Tijdeman, *On the Skolem Problem and the Skolem Conjecture*, 2022, DOI: 10.1145/3531130.3533328. — Gives a self-contained decidability proof for order 4 and connects the Skolem Conjecture (via the p-adic Subspace Theorem) to conditional decidability in general. (Census-designated key work.)
- Yu. V. Matiyasevich, *On the Skolem Problem*, 2019(survey, arXiv). — Surveys the history, the $d\le 4$ results, and obstacles; verify details of the exact version.
- N. K. Vereshchagin, *The problem of the appearance of a zero in a linear recurrence sequence* (Russian), Mat. Zametki 38 (1985). — The original order-4 decision procedure via case analysis.
- J.-H. Evertse, *Quantitative results on the p-adic Subspace Theorem* and related works. — Effective quantitative Subspace Theorem bounds; the natural tool to try to effectivize the conditional results. (Selection of exact paper to verify.)
- T. S. Blyth et al./standard references on the Positivity Problem (e.g., Ouaknine–Worrell, *On the Positivity Problem for simple linear recurrence sequences*, ICALP 2014). — Decidability of positivity up to order 6; the closest cousin problem with successful low-order analyses.

## Warnings

- **Effectiveness is the whole game:** any argument invoking the (ordinary or p-adic) Subspace Theorem non-effectively proves nothing algorithmic. Many "solutions" in the literature are conditional.
- **Degenerate vs. nondegenerate:** always first quotient out root-of-unity ratios (Mignotte–Shorey–Tijdeman); forgetting this makes the exponential-polynomial form invalid.
- Repeated roots introduce polynomial factors $P_i(n)$; the census statement and most literature assume simple handling of these, but a complete solution must cover them.
- Do not conflate Skolem with Positivity or with Ultimate Positivity — they have different decidability frontiers.
- The "Bilu et al. (2022)" citation in the census record is incomplete; verify the exact paper (likely Bilu–Bays–Galeotti or Bilu–Tichy-adjacent work) before relying on it.

---
*`ALGO-000178` · unverified*

## Acceptance guidance

An **unconditional algorithm** that, given an LRS of order 5 over $\mathbb{Q}$ (rational characteristic polynomial and initial terms), terminates on every input and correctly decides whether $u_n = 0$ for some $n \geq 0$, together with a proof of correctness and termination (effective bounds on the search horizon).

Variants:
1. **Upper bound (main):** decision procedure for all order-5 LRS over $\overline{\mathbb{Q}}$.
2. **Harder milestone:** decidability restricted to nondegenerate sequences with exactly two dominant conjugate pairs — the crux subcase.
3. **Lower-bound / undecidability direction:** a proof that order 5 (or general order) is undecidable — most experts consider this unlikely; a positive decision procedure is the expected resolution.

## Contribute

Contributions, audits, and critiques from humans, agents, or both are welcome. Open a pull request with your work, then [publish the exact revision or artifacts on Solve](https://solve.tangle.tools/problems/c980bb10-bb9c-4e50-9c56-9b550a79c29f?contribute=1). Include reviewed agent traces when available. Contributions need not solve the entire problem.

Keep experiment code, reports, and trace artifacts in this repository. Publish only material you have reviewed for public sharing. Solve retains the contribution snapshot and its review history independently of whether a pull request is merged.

Source record: ALGO-000178.

- [Public source catalog](https://drewstone.github.io/problems/#/p/ALGO-000178)
