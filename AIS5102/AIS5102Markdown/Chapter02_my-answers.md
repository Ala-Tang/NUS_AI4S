
## My answers — Chapter 02 (2026-08-17)

> Sections A and B only — the coding questions are answered in the notebook.
> Written cold, then corrected after reading. 12 of 20 attempted.

### A. Conceptual short-answer

**A1** — Define the design matrix and state what a row and a column each represent.

rows are samples; columns are features

**A2** — What does it mean for a design matrix to be rank-deficient? Give an experimental circumstance that would produce one.

Rank deficiency means some features contain redundant information

**A3** — Why is solving a linear system preferable to forming an explicit inverse?

solve directly

**A4** — State the rule NumPy uses to broadcast two arrays of different shapes, and give a pair of shapes that broadcasts silently when the intended operation was an error.

dimensions must match

**A5** — Combining the design matrix with the two derived square matrices: state the shape of the feature-space and measurement-space matrices, describe what each encodes, and explain what it means to call them dual.

feature covariance and sample gram matrices share nonzero eigenvalues

**A6** — Combining rank with the normal equations of Chapter 01: explain what rank deficiency does to a least-squares fit, and what it implies about your choice of features.

redundant features make least-squares coefficients non-unique or unstable

**A7** — Combining eigendecomposition with the singular value decomposition: explain why the SVD of the data is preferred over the eigendecomposition of the covariance matrix, giving both a numerical and a practical reason.

SVD is simple

### B. Mathematical

**B1** — Define the design matrix. State its shape and what each of its two indices ranges over.

X_nd records feature d for sample n.

**B2** — Define the scatter, covariance, and Gram matrices in terms of the centred design matrix, and give the shape of each.

gram compares samples N*N, the other two D*D

**B3** — Define the singular value decomposition of a matrix: name the three factors, give their shapes, and state the constraint each satisfies.

SVD uses orthogonal U,V and nonnegative diagonal Σ

**B4** — Define the ℓ₁, ℓ₂, and ℓ∞ norms of a vector.

L1 sums, L2 measures length, Linfinity takes maximum

**B5** — Define the centring operator in matrix form, and state what it does to a design matrix.

H subtracts each column mean from every observation. HHHH
