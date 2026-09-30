<div align="center">

# Introduction to Convex Optimization

A tutorial that goes from convex sets to working algorithms.

</div>

---

## About

This repository contains a complete tutorial on convex optimization, written as a single
LaTeX document of about 60 pages. It starts from the geometry of convex sets and convex
functions, develops the theory through duality and the KKT conditions, and then moves to
computation: gradient descent, Newton's method, ADMM, accelerated first-order methods, and
algorithms for nonlinear least squares.

The tutorial mainly follows Prof. Ling Qing's open course at USTC, and adds several
chapters on algorithms that go beyond both that course and Boyd's textbook.

## Who this is for

You should be comfortable with linear algebra — matrices, eigenvalues, matrix
multiplication. That is the only hard prerequisite. No prior exposure to optimization is
assumed.

The material is development-first rather than proof-first. If you want a reference that
develops the theory rigorously and in full generality, read Boyd's *Convex Optimization*
alongside this one; it is cited throughout as the place to go deeper.

## Contents

The book has three parts, and the split is deliberate: the first two chapters are the
vocabulary, the next two are the theory, and the last three are the algorithms.

### Part I — Foundations

- **1. Convex Sets** — affine sets, convex sets, and convex cones, together with the
  affine, convex, and conic hulls they generate. The standard examples: hyperplanes and
  halfspaces, Euclidean balls, ellipsoids, polyhedra and simplices, and the cone of
  positive semidefinite matrices. Closes with the operations that preserve convexity —
  intersection, affine maps (including linear matrix inequalities), perspective functions,
  and linear fractional functions.

- **2. Convex Functions** — the definition, extended-value extensions, and the first- and
  second-order conditions. A catalogue of examples worth memorizing: exponentials, powers,
  norms, the max function, log-sum-exp, the geometric mean, and log-determinant. Jensen's
  inequality; the operations that preserve convexity (nonnegative weighted sums,
  composition, pointwise maximum and supremum, the perspective); the conjugate function;
  quasiconvex functions; and log-concave functions.

### Part II — Theory

- **3. Convex Optimization Problems** — the vocabulary of optimization: objective,
  constraints, feasible set, optimal value, active and inactive constraints. Standard form,
  equivalent problems, slack variables, and constraint elimination. The central fact that
  every local minimum of a convex problem is global, and the optimality criterion
  ∇f₀(x\*)ᵀ(y − x\*) ≥ 0, worked out for the unconstrained, equality-constrained, and
  nonnegativity-constrained cases. Then a tour of the standard problem classes: linear
  programs (and the diet problem), quadratic and quadratically constrained programs, least
  squares with ℓ₁ (LASSO) and ℓ₂ (ridge) regularization, Markowitz portfolio optimization,
  and semidefinite programming. Ends with Pareto optimality and multicriterion problems.

- **4. Duality** — the Lagrangian and the Lagrange dual function, which is always concave
  and always a lower bound on the primal optimum, even when the primal is not convex. Weak
  and strong duality, the duality gap, and Slater's condition with its refinement for affine
  constraints. Three interpretations — geometric, saddle-point, and economic — and the fact
  that equivalent problems can have very different duals. Everything converges on the
  Karush–Kuhn–Tucker conditions: primal feasibility, dual feasibility, complementary
  slackness, and stationarity, worked in full on a quadratic program and on the
  water-filling problem. Closes with sensitivity analysis and the penalty methods that lead
  to the interior-point idea.

### Part III — Algorithms

- **5. Unconstrained Minimization** — the optimality condition ∇f(x\*) = 0, and the
  reduction of the problem to solving a nonlinear equation. Strong convexity and smoothness,
  and the bounds they give on the optimal value and on the distance to the optimum. Descent
  methods, search directions, and line search (exact and backtracking). Gradient descent
  with its step-size choices and the 1 − m/M convergence rate. Steepest descent with respect
  to an arbitrary norm, including the ℓ₁ and subgradient variants. Newton's method, the
  Newton decrement, and its two convergence phases.

- **6. Equality Constrained Minimization** — the KKT conditions collapse into a single
  linear system, which is exactly what you solve when f is quadratic. Newton's method
  applied to that system rather than to f itself, and the structured symmetric indefinite
  matrix that interior-point methods spend most of their time on. The second half builds up
  the modern approach to constraints in three steps — Lagrange dual ascent, the augmented
  Lagrangian, and ADMM — with each step fixing a concrete failure of the previous one.

- **7. Advanced Optimization Algorithms** — the tools that modern solvers actually use.
  Lipschitz continuity of the gradient and the descent lemma, and how to estimate the
  constant, including by power iteration. Proximal operators as the extension of the
  gradient step to non-smooth functions. The composite problem f = g + h, and
  forward-backward splitting as the framework that unifies projection, ISTA, FISTA, and FGP
  — with Nesterov's momentum buying the O(1/k²) rate. Finally, nonlinear least squares:
  Gauss–Newton, Levenberg–Marquardt, and quasi-Newton methods (BFGS and L-BFGS).

### Appendix

- **A. Quiz** — three worked problems taken from the course videos, each of which forces a
  technique from the main chapters rather than a definition. Full solutions are given, with
  the advice to cover the solution and try the problem first.

## What this tutorial does not cover

Being explicit about the scope, so you know where to look next:

- **Interior-point methods** are only touched on, at the end of Chapter 4, as the limit of
  the log-barrier penalty. They are not developed, even though they dominate commercial
  solvers.
- **Robust optimization**, **applications of semidefinite programming**, and **non-convex
  heuristics** are each worth a chapter of their own and are not covered here.
- **No code listings.** The algorithms are given as pseudocode and formulas. There are no
  MATLAB, Python, or Julia implementations in this repository — writing them is left to you,
  which is arguably the point.

## Building the PDF

You need a TeX distribution with XeLaTeX. A **full** TeX Live installation is required
rather than a minimal one, because the `elegantbook` class loads `ctex`/`xeCJK`. The
document class is bundled in this repository, so there is nothing extra to install.
(Tested with TeX Live 2023.)

```bash
latexmk
```

A `.latexmkrc` is included, so `latexmk` selects XeLaTeX automatically and runs as many
passes as the cross-references need. You do not need to invoke XeLaTeX directly, and you do
not need to compile twice by hand.

```bash
latexmk -c    # remove auxiliary files, keep the PDF
latexmk -C    # remove everything, including the PDF
```

The output is `Introduction to Convex Optimization.pdf`.

## Acknowledgements

Thanks to Prof. Ling Qing for making his USTC lectures freely available. Stephen Boyd's
*Convex Optimization* remains the standard reference for readers who want to go deeper.

The typesetting uses the ElegantBook document class.

## License

This tutorial is released under
[CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). See [LICENSE](LICENSE).
