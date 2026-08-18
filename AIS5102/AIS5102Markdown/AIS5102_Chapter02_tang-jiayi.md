# AIS5102 · Chapter 02 submission

**Name:** TANG JIAYI  
**Student ID:** A0355738  
**Generated:** 2026-08-17

> 12 of 20 questions attempted · 0 of 20 glossary terms marked known, 20 to learn again.

---

## Part 1 — Attempt

*Written before reading the chapter, then corrected after. Sections A and B; the coding questions are answered in the notebook.*

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

**A8** — Bring together the design matrix, the covariance matrix, and the eigendecomposition to explain what it would mean for a dataset to have one dominant eigenvalue. State what you would conclude scientifically, and what you would check before believing it.

_not attempted_

**A9** — Using rank, conditioning, and the choice between solving and inverting, explain why two collaborators fitting the same linear model to the same data can obtain visibly different parameters. Describe what you would compute to diagnose which result to trust.

_not attempted_

**A10** — Combining the design matrix, centring, the covariance and Gram matrices, and the SVD, explain how a single factorisation of the data gives you access to structure in both feature space and measurement space at once. State what each factor of the decomposition is used for.

_not attempted_

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

**B6** — Prove that the scatter matrix is symmetric and positive semi-definite, and state what this guarantees about its eigenvalues.

_not attempted_

**B7** — Given the singular value decomposition of a matrix, derive the eigendecomposition of its Gram and covariance matrices, and state the relationship between singular values and eigenvalues.

_not attempted_

**B8** — Show that XXᵀ and XᵀX share the same non-zero eigenvalues, and state the maximum number of them in terms of the matrix dimensions.

_not attempted_

**B9** — Prove that the centring operator is symmetric and idempotent, and determine its rank.

_not attempted_

**B10** — Derive the matrix that orthogonally projects onto the span of a single vector. Prove it is idempotent and that the residual is orthogonal to the projection direction.

_not attempted_

---

## Part 2 — Glossary self-test

*20 terms make their first appearance in this chapter.*

### Terms I still need to learn

- **condition number** — How much a matrix amplifies small errors. Large means the answer is untrustworthy.
- **design matrix** — Your whole dataset as one rectangle: one row per measurement, one column per feature.
- **eigenvalue / eigenvector** — A direction a matrix does not turn, and the factor by which it stretches that direction.
- **Gram matrix** — Whether two measurements resemble each other, and by how much.
- **rank** — How many genuinely independent directions your data spans, as opposed to how many columns it has.
- **SVD** — Every matrix is a rotation, then a stretch, then another rotation.
- **determinant** — How much a matrix scales volume. Zero means it flattens space and cannot be undone.
- **matrix** — A rectangle of numbers arranged in rows and columns.
- **matrix inverse** — The matrix that undoes another one. In code you almost always want solve instead.
- **matrix multiplication** — Row-by-column: each output entry is one dot product. Not the same as multiplying entry by entry.
- **transpose** — Flip a matrix over its diagonal: rows become columns.
- **vector** — An ordered list of numbers; also an arrow with a direction and a length.
- **array / ndarray** — NumPy's grid of numbers. Every computation in this course runs on one.
- **axis** — Which direction an operation runs along: axis=0 collapses down the rows, axis=1 across the columns.
- **broadcasting** — NumPy silently stretching a smaller array so shapes match. Convenient, and a common source of silent bugs.
- **dtype** — What kind of number each cell holds — 64-bit float, 32-bit integer, and so on.
- **slicing** — Taking a chunk of an array with a[2:7], without copying it.
- **ptychography / tomography** — Reconstructing an image from many overlapping diffraction snapshots; tomography adds depth.
- **scRNA-seq** — Measuring which genes are switched on, one cell at a time.
- **wavenumber** — The horizontal axis of a Raman spectrum: how many wave cycles fit in a centimetre.

### My notes on these terms

**condition number** — κ= σmax/σmin

**design matrix** — X∈ℝN×D, the canonical input to every method in this course

**eigenvalue / eigenvector** — Au=λu with u≠0: u the eigenvector, λ the eigenvalue

**Gram matrix** — G=X̃X̃⊤∈ℝN×N; the matrix of inner products between rows

**rank** — The number of non-0 singular values

**SVD** — X=UΣV⊤ with U⊤ U=V⊤ V=I and Σ diagonal, non-negative, decreasing. A very important glossary.

**determinant** — how much a matrix scale volume

**matrix** — rows and columns

**matrix inverse** — undoes another one

**matrix multiplication** — (AB)ij=∑k AikBkj; needs the inner dimensions to agree

**transpose** — (A⊤)ij=Aji

**vector** — An element of ℝD

**array / ndarray** — have a shape and the same dtype

**axis** — axis=0 collapses down the rows

**broadcasting** — match or be 1

**dtype** — What kind of number each cell holds  .   cell?hiehie

**slicing** — choose interval?

**ptychography / tomography** — micro instrument

**scRNA-seq** — cell gene

**wavenumber** — ν~=1/λ, in cm−1
