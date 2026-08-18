# Chapter 02 — NumPy and the Linear Algebra You Actually Need

> Companion notes for `NumpyBasics.ipynb` and `DesignMatrix.ipynb`. Audience: advanced undergraduate.
>
> **The question this chapter answers.** *Your measurements are a table of numbers. What is the smallest set of operations that lets you ask anything of it?*
>
> Work `Chapter02_Questions.md` **before** you read this. The full treatment — worked explanations, coding scaffolds, hints, deeper reading — is on the chapter page.

## Learning outcomes

By the end of this chapter, you should be able to:

- Manipulate NumPy arrays: creation, shape, dtypes, slicing, fancy, boolean and `np.ix_` indexing, broadcasting, step-indexing.
- Distinguish element-wise multiplication (`*`) from matrix multiplication (`@`), and say when broadcasting fires silently.
- Use the eight `np.linalg` operations you will reach for repeatedly — transpose, determinant, inverse, `solve`, `eig`, `eigh`, `svd`, `norm`.
- Read a **design matrix** $\mathbf{X}\in\mathbb{R}^{N\times D}$ as "$N$ measurements, each with $D$ features", and say why it is the canonical input to every algorithm in this course.
- State the Gram, covariance and scatter matrices in terms of $\mathbf{X}$, and say what each encodes.
- Recognise when an operation should be a factorisation rather than a literal inverse.

## Concept overview

> **Objective** — None. Supplies the linear algebra in which every objective is written. · [[Chapter05#Chapters that minimise nothing|objective table]]

**Everything starts as a table.** Almost every algorithm in this course consumes a **design matrix**: one measurement per row, one feature per column.

$$
\mathbf{X} \in \mathbb{R}^{N\times D}.
$$

A Raman spectrum is one row. A vector of expression levels at $10^4$ genes is one row. A microscopy patch, flattened, is one row.

**Two derived matrices, and they are duals.** Centre the columns first, writing $\tilde{\mathbf{X}}$ for the centred matrix. Then

$$
\boldsymbol{\Sigma} = \tfrac{1}{N-1}\tilde{\mathbf{X}}^{\top}\tilde{\mathbf{X}} \in \mathbb{R}^{D\times D},
\qquad
\mathbf{G} = \tilde{\mathbf{X}}\tilde{\mathbf{X}}^{\top} \in \mathbb{R}^{N\times N}.
$$

$\boldsymbol{\Sigma}$ is the **feature covariance** and lives in feature space: it says which wavenumbers, genes or pixels move together. $\mathbf{G}$ is the **Gram** or similarity matrix and lives in measurement space: it says which spectra, cells or images resemble each other. Their non-zero eigenvalues coincide, and one SVD of $\tilde{\mathbf{X}}$ delivers both.

## Key math

**One factorisation covers most of the course.**

$$
\mathbf{X} = U\Sigma V^{\top},
\qquad
\mathbf{X}^{\top}\mathbf{X} = V\Sigma^{2}V^{\top},
\qquad
A = Q\Lambda Q^{\top}\ \text{(symmetric } A).
$$

Eigenvectors of $\boldsymbol{\Sigma}$ are the directions of greatest variance — the PCA components of Chapter 08. The SVD reaches them without ever forming $\boldsymbol{\Sigma}$, which is why it is preferred.

**Rotate, scale, rotate.** Read $U\Sigma V^{\top}\mathbf{x}$ right to left, in the order the factors touch $\mathbf{x}$. $V^{\top}$ rotates the special directions onto the coordinate axes; $\Sigma$ stretches axis $i$ by $\sigma_i$ and mixes nothing; $U$ rotates the result into the output space. Feed in the unit circle and an ellipse comes out, with semi-axes $\sigma_1,\sigma_2,\dots$. Every matrix, of any shape, is exactly these three motions. Rank counts the non-zero singular values — the axes the ellipse still has — and the condition number $\sigma_{\max}/\sigma_{\min}$ says how eccentric it is.

> Here $\Sigma$ is the diagonal matrix of singular values and $\boldsymbol{\Sigma}$ is the covariance. The collision is unfortunate and universal; watch the boldface.

**Element-wise is not matrix multiplication.**

$$
(A \odot B)_{ij} = A_{ij}B_{ij},
\qquad
(AB)_{ij} = \sum_{k}A_{ik}B_{kj}.
$$

In NumPy the first is `*` and the second is `@`. Broadcasting will stretch shapes to make `*` succeed, so an expression can run silently and return the wrong answer. Check shapes, not just for errors.

**Solve, never invert.** Write $\mathbf{x} = A^{-1}\mathbf{b}$ on paper; write `np.linalg.solve(A, b)` in code. Forming the inverse does extra work, discards conditioning information, and amplifies floating-point error.

## Code examples

> **Functions used.** *NumPy* — `np.allclose`, `np.arange`, `np.ix_`, `np.linalg.eigh`, `np.linalg.solve`, `np.linalg.svd`, `np.random.default_rng`, `np.sort`

```python
import numpy as np

Xc = X - X.mean(axis=0, keepdims=True)   # centre every column first

S     = Xc.T @ Xc                        # scatter,    (D, D)
Sigma = S / (N - 1)                      # covariance, (D, D)
G     = Xc @ Xc.T                        # Gram,       (N, N)

eigvals, eigvecs = np.linalg.eigh(Sigma)          # symmetric -> eigh, not eig
U, s, Vt = np.linalg.svd(Xc, full_matrices=False) # same information, one shot
assert np.allclose(np.sort(s**2 / (N - 1))[::-1], np.sort(eigvals)[::-1])

x = np.linalg.solve(A, b)                # never np.linalg.inv(A) @ b
```

## Applications

The course's first dataset — Raman spectra of multilayer graphene from Prof. Ariando's lab at NUS — is a design matrix and nothing more. Each row is one spectrum, each column the intensity at one wavenumber. The Gram matrix says which spectra resemble each other, which later becomes clustering; the covariance says which wavenumbers co-vary, which later becomes PCA and peak identification.

The same representation appears verbatim in:

- **scRNA-seq.** $N$ cells × $10^4$ genes. Rows are cells, columns are genes. PCA → UMAP → cluster.
- **High-throughput spectroscopy.** $N$ samples × $D$ wavenumbers; t-SNE or UMAP exposes impurity classes (Chapters 11–12).
- **3-D ptychotomography.** Voxels become rows, depth profiles become features, and vector quantisation segments them.

<!-- glossary:start -->

## Glossary

*Every term below makes its first appearance in the course here. Plain words first, then the precise statement. Terms introduced in earlier chapters are in their glossaries.*

### Machine-learning concepts

- **collinearity** — Two or more features carrying nearly the same information, so the fit cannot tell them apart. *Precisely:* Near-linear dependence among columns; diagnosed by the variance inflation factor or by $\kappa$.
- **condition number** — How much a matrix amplifies small errors. Large means the answer is untrustworthy. *Precisely:* $\kappa = \sigma_{\max}/\sigma_{\min}$. Solving inflates relative error by roughly this factor.
- **covariance** — Whether two features move together, and by how much. *Precisely:* $\boldsymbol{\Sigma}=\frac{1}{N-1}\tilde{\mathbf{X}}^\top\tilde{\mathbf{X}}\in\mathbb{R}^{D\times D}$ for centred $\tilde{\mathbf{X}}$.
- **design matrix** — Your whole dataset as one rectangle: one row per measurement, one column per feature. *Precisely:* $\mathbf{X}\in\mathbb{R}^{N\times D}$, the canonical input to every method in this course.
- **dimensionality reduction** — Describing each measurement with far fewer numbers while keeping what matters. *Precisely:* A map $\mathbb{R}^D\to\mathbb{R}^L$ with $L\ll D$, chosen to preserve a stated property.
- **eigendecomposition** — Rewriting a symmetric matrix as: rotate, stretch along the axes, rotate back. *Precisely:* $A=Q\Lambda Q^\top$ with $Q$ orthonormal and $\Lambda$ diagonal. Exists for every real symmetric $A$.
- **eigenvalue / eigenvector** — A direction a matrix does not turn, and the factor by which it stretches that direction. *Precisely:* $A\mathbf{u}=\lambda\mathbf{u}$ with $\mathbf{u}\ne\mathbf{0}$: $\mathbf{u}$ the eigenvector, $\lambda$ the eigenvalue.
- **Gaussian / normal** — The bell curve. The Central Limit Theorem is why it turns up everywhere. *Precisely:* $\mathcal{N}(\mu,\sigma^2)$ with density $\propto\exp\!\big(-(x-\mu)^2/2\sigma^2\big)$.
- **Gram matrix** — Whether two measurements resemble each other, and by how much. *Precisely:* $\mathbf{G}=\tilde{\mathbf{X}}\tilde{\mathbf{X}}^\top\in\mathbb{R}^{N\times N}$; the matrix of inner products between rows.
- **norm** — The length of a vector — with more than one sensible way to measure it. *Precisely:* $\lVert x\rVert_1=\sum_i|x_i|$, $\lVert x\rVert_2=\sqrt{\sum_i x_i^2}$, $\lVert x\rVert_\infty=\max_i|x_i|$.
- **normal equations** — The linear system whose solution is the least-squares fit. *Precisely:* $\mathbf{X}^\top\mathbf{X}\hat\beta = \mathbf{X}^\top\mathbf{y}$; solve it, never invert.
- **orthogonality** — At right angles — and so carrying no shared information. *Precisely:* $\mathbf{u}^\top\mathbf{v}=0$. Orthonormal adds $\lVert\mathbf{u}\rVert=1$.
- **PCA / principal component** — The directions along which your data varies most, found without using any labels. *Precisely:* Eigenvectors of $\boldsymbol{\Sigma}$, ordered by eigenvalue; equivalently the right singular vectors of $\tilde{\mathbf{X}}$.
- **positive semi-definite** — A matrix that never turns a vector back on itself — the matrix version of "not negative". *Precisely:* $\mathbf{v}^\top A\mathbf{v}\ge 0$ for all $\mathbf{v}$. Equivalent, for symmetric $A$, to all eigenvalues $\ge 0$.
- **projection** — The shadow one vector casts on another direction, or on a plane. *Precisely:* $P=\mathbf{v}\mathbf{v}^\top/(\mathbf{v}^\top\mathbf{v})$; idempotent, $P^2=P$, with residual orthogonal to $\mathbf{v}$.
- **rank** — How many genuinely independent directions your data spans, as opposed to how many columns it has. *Precisely:* The number of non-zero singular values; equivalently the dimension of the column space.
- **residual** — What the model failed to explain: observed minus predicted. *Precisely:* $r_n = y_n - f(x_n;\hat\theta)$.
- **scatter matrix** — The covariance before you divide by the sample count. *Precisely:* $\mathbf{S}=\tilde{\mathbf{X}}^\top\tilde{\mathbf{X}}$; identical eigenvectors to $\boldsymbol{\Sigma}$, eigenvalues larger by $N-1$.
- **SVD** — Every matrix is a rotation, then a stretch, then another rotation. *Precisely:* $\mathbf{X}=U\Sigma V^\top$ with $U^\top U=V^\top V=I$ and $\Sigma$ diagonal, non-negative, decreasing.
- **t-SNE** — A way to draw high-dimensional data in two dimensions so that near neighbours stay near. *Precisely:* Minimises $D_{\mathrm{KL}}(P\Vert Q)$ between neighbour distributions, with a Student-$t$ kernel in the embedding.
- **UMAP** — Like t-SNE, but faster and better at keeping the large-scale layout. *Precisely:* Fuzzy simplicial set construction followed by cross-entropy minimisation on a $k$-nearest-neighbour graph.
- **variance** — How spread out a set of numbers is. *Precisely:* $\mathrm{Var}(X)=\mathbb{E}[(X-\mu)^2]$; estimated by $\frac{1}{N-1}\sum_n (x_n-\bar x)^2$.
- **vector quantisation** — Replacing each measurement by the nearest entry in a short catalogue of representatives. *Precisely:* Assignment to the nearest codebook vector; the prediction step of $k$-means, scored by distortion.

### Mathematics and notation

- **determinant** — How much a matrix scales volume. Zero means it flattens space and cannot be undone. *Precisely:* $\det A$; $A$ is invertible exactly when $\det A \ne 0$.
- **diagonal matrix** — Numbers on the leading diagonal, zeros everywhere else. Multiplying by one just rescales each axis. *Precisely:* $D_{ij}=0$ for $i\ne j$.
- **inner / dot product** — Multiply two vectors entry by entry and add. Big when they point the same way. *Precisely:* $\mathbf{a}^\top\mathbf{b}=\sum_i a_ib_i = \lVert a\rVert\lVert b\rVert\cos\vartheta$.
- **limit** — What a quantity approaches as you push something to zero or to infinity. *Precisely:* $\lim_{x\to a}f(x)$.
- **linear combination** — Scale some vectors and add them up. *Precisely:* $\sum_i c_i\mathbf{v}_i$ for scalars $c_i$.
- **logarithm** — The exponent you need: $\log_{10}1000=3$. It turns multiplication into addition. *Precisely:* $\log_b x = y \iff b^y = x$. Natural log unless stated otherwise.
- **matrix multiplication** — Row-by-column: each output entry is one dot product. Not the same as multiplying entry by entry. *Precisely:* $(AB)_{ij}=\sum_k A_{ik}B_{kj}$; needs the inner dimensions to agree.
- **orthogonal (geometry)** — At right angles. *Precisely:* Perpendicular; the inner product vanishes.
- **span / column space** — Everywhere you can reach by scaling and adding a given set of vectors. *Precisely:* $\mathrm{span}\{\mathbf{v}_i\}$; the column space of $\mathbf{X}$ is what a linear model can predict.
- **subspace** — A flat slice through the origin — a line, a plane, and so on. *Precisely:* A subset closed under addition and scalar multiplication.
- **symmetric matrix** — A matrix unchanged by flipping it over its diagonal. *Precisely:* $A=A^\top$. Guarantees real eigenvalues and orthogonal eigenvectors.
- **transpose** — Flip a matrix over its diagonal: rows become columns. *Precisely:* $(A^\top)_{ij}=A_{ji}$.
- **vector** — An ordered list of numbers; also an arrow with a direction and a length. *Precisely:* An element of $\mathbb{R}^D$.

### Statistics

- **Bessel's correction** — Dividing by $N-1$ rather than $N$, because you estimated the mean from the same data. *Precisely:* Makes the sample variance unbiased for the population variance.

### Programming

- **argument / parameter (code)** — The values you hand to a function when you call it. *Precisely:* Positional or keyword; distinct from a *model* parameter $\theta$.
- **assert** — A line that stops the program if something you believe is not true. *Precisely:* `assert cond`; with `np.allclose` it is the standard way to check two routes agree numerically.
- **boolean mask** — Selecting entries with an array of True/False rather than with positions. *Precisely:* `a[a > 0]`; the mask must match the axis length.
- **broadcasting** — NumPy silently stretching a smaller array so shapes match. Convenient, and a common source of silent bugs. *Precisely:* Dimensions are aligned from the right; each must match or be 1.
- **dtype** — What kind of number each cell holds — 64-bit float, 32-bit integer, and so on. *Precisely:* `np.float64` by default. Mixing dtypes silently upcasts, and integer division truncates.
- **fancy indexing** — Selecting arbitrary positions at once with a list of indices. *Precisely:* `a[[0, 3, 7]]` or `np.ix_` for outer-product selection. Returns a copy, not a view.
- **floating point** — How computers store real numbers: finitely many digits, so almost nothing is exact. *Precisely:* IEEE 754 binary64 here: about 16 significant decimal digits, machine epsilon $\approx 2.2\times10^{-16}$.
- **loop** — Repeating a block of code once per item. *Precisely:* `for x in xs:`. In NumPy, usually the sign that a vectorised form exists.
- **row-major / memory layout** — The order the numbers actually sit in memory. It changes speed, never answers. *Precisely:* C order walks the last index fastest; Fortran order the first. NumPy defaults to C.
- **slicing** — Taking a chunk of an array with `a[2:7]`, without copying it. *Precisely:* A view described by start, stop and step; writing to it writes to the original.
- **tolerance** — How close is close enough, when exact equality is meaningless. *Precisely:* The threshold in `np.allclose(a, b, rtol, atol)` or in a rank estimate.
- **vectorisation** — Writing an operation over whole arrays instead of looping element by element. *Precisely:* Pushing the loop into compiled code; typically one to two orders of magnitude faster.

### Scientific vocabulary

- **graphene** — A single layer of carbon atoms in a honeycomb. Stacking more layers changes the Raman spectrum. *Precisely:* A two-dimensional carbon allotrope; layer count is read from the G and 2D band shapes.
- **ptychography / tomography** — Reconstructing an image from many overlapping diffraction snapshots; tomography adds depth. *Precisely:* Coherent diffractive imaging with overlapping probes, extended to three dimensions by rotation.
- **scRNA-seq** — Measuring which genes are switched on, one cell at a time. *Precisely:* Single-cell RNA sequencing: an $N$ cells $\times$ $\sim\!10^4$ genes count matrix.
- **voxel** — A pixel with depth — one cell of a 3-D volume. *Precisely:* The volumetric sampling element; flattened over depth it becomes one row of a design matrix.

<!-- glossary:end -->

---

*Questions: `Chapter02_Questions.md` · Full treatment, scaffolds and deeper reading: the chapter page.*
