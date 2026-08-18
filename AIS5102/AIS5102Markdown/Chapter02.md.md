## Notes from the Chapter 02 page

**A4 — State the rule NumPy uses to broadcast two arrays of different shapes, and give a pair of shapes that broadcasts silently when the intended operation was an error.**

I like it.

**Least squares as a projection — Hastie, Tibshirani &amp; Friedman, The Elements of Statistical Learning (2nd ed.), Fig. 3.2, p. 46**

* **Covariance matrix:** `Eigenvectors set ellipse directions; eigenvalues determine axis lengths.`
* **SVD shapes:** `Economy SVD keeps only the factors needed for reconstruction.`
* **Rank-two approximation:** `A rank-two approximation projects data onto its best plane.`
* **Least squares:** `Least squares projects targets onto the design matrix column space.`
* **Nullspace and range:** `Nullspace vectors map to zero and cannot be distinguished.`
* **Normalisation:** `Standardisation rescales axes; whitening removes correlations between features.`
* **Vector, matrix, tensor:** `Shape determines how the same stored numbers are indexed.`
* **Memory order:** `Memory order changes computational speed, not mathematical results.`

**Row-major against column-major — Murphy, Probabilistic Machine Learning: An Introduction, Fig. 7.2, p. 225**

* **Covariance matrix:** `Eigenvectors set ellipse directions; eigenvalues determine axis lengths.`
* **SVD shapes:** `Economy SVD keeps only the factors needed for reconstruction.`
* **Rank-two approximation:** `A rank-two approximation projects data onto its best plane.`
* **Least squares:** `Least squares projects targets onto the design matrix column space.`
* **Nullspace and range:** `Nullspace vectors map to zero and cannot be distinguished.`
* **Normalisation:** `Standardisation rescales axes; whitening removes correlations between features.`
* **Vector, matrix, tensor:** `Shape determines how the same stored numbers are indexed.`
* **Memory order:** `Memory order changes computational speed, not mathematical results.`

**Concept overview**

Covariance compares features; Gram compares samples; SVD connects both

**Key math**

* **SVD:** `SVD decomposes a matrix into rotation, scaling, and rotation.`
* **PCA:** `SVD finds PCA directions without explicitly forming covariance.`
* **Sigma:** `Sigma means singular values or covariance; check context.`
* **SVD factors:** `V acts on features, Sigma scales, U acts on samples.`
* **Rank:** `Rank counts the non-zero singular values.`
* **Condition number:** `Condition number measures sensitivity to small errors.`
* **Element-wise multiplication:** `Use * to multiply corresponding elements.`
* **Matrix multiplication:** `Use @ for row-by-column matrix multiplication.`
* **Broadcasting:** `Broadcasting expands compatible shapes; always check the result.`
* **Linear systems:** `Use solve instead of explicitly computing an inverse.`

**Gram matrix — glossary**

G=X̃X̃⊤∈ℝN×N; the matrix of inner products between rows

**SVD — glossary**

X=UΣV⊤ with U⊤ U=V⊤ V=I and Σ diagonal, non-negative, decreasing. A very important glossary.

**array / ndarray — glossary**

have a shape and the same dtype

**axis — glossary**

axis=0 collapses down the rows

**broadcasting — glossary**

match or be 1

**condition number — glossary**

κ= σmax/σmin

**design matrix — glossary**

X∈ℝN×D, the canonical input to every method in this course

**determinant — glossary**

how much a matrix scale volume

**dtype — glossary**

What kind of number each cell holds  .   cell?hiehie

**eigenvalue / eigenvector — glossary**

Au=λu with u≠0: u the eigenvector, λ the eigenvalue

**matrix — glossary**

rows and columns

**matrix inverse — glossary**

undoes another one

**matrix multiplication — glossary**

(AB)ij=∑k AikBkj; needs the inner dimensions to agree

**ptychography / tomography — glossary**

micro instrument

**rank — glossary**

The number of non-0 singular values

**scRNA-seq — glossary**

cell gene

**slicing — glossary**

choose interval?

**transpose — glossary**

(A⊤)ij=Aji

**vector — glossary**

An element of ℝD

**wavenumber — glossary**

ν~=1/λ, in cm−1

## Terms to learn again

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