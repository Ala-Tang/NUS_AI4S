# Chapter 02 — NumPy and Linear Algebra — Question Bank

> **The question this chapter answers.** *Your data is one rectangle of numbers. How would you find which rows resemble each other, and which columns move together?*
>
> Write an answer here **before you look anything up**. You have the notes already; the point is to find out what you do not know first. Then open them, or ask an LLM, and correct what you wrote — keep both versions. The gap between your attempt and the answer is the part you will remember.

> **No answers are provided.** Sections A and B are prepared by the Friday before the Monday lecture, where they are quizzed in class. Section C is practised between the lecture and the Thursday lab — until you can do each unaided, without AI, on a lab desktop.
> Tiers are set by *composition*: how many distinct concepts a question requires (Section A), or how many functions you must write and connect (Section C). Section B is tiered differently — Easy asks you to state a definition, Medium to prove or state a property of one.
> **Assessed scope.** Sections A and B are quizzed in the **Monday lecture** — conceptual to Medium, mathematical to Easy. Section C is answered in the **Thursday lab** — coding to Medium. That is **19 of this chapter's 30 questions**. The tiers marked *stretch* are quizzed in neither session; attempt them if you finish early, and expect them in the block homework and the final examination.

**Notes:** [[Chapter02]] · [[Chapter02#Learning outcomes|Learning outcomes]] · [[Chapter02#Optional Reading and References|Optional reading]]

## A. Conceptual short-answer

*Where to look: [[Chapter02#Concept overview|Concept overview]] · [[Chapter02#Applications|Applications]]*

### Easy — a single concept

1. Define the design matrix and state what a row and a column each represent.
2. What does it mean for a design matrix to be rank-deficient? Give an experimental circumstance that would produce one.
3. Why is solving a linear system preferable to forming an explicit inverse?
4. State the rule NumPy uses to broadcast two arrays of different shapes, and give a pair of shapes that broadcasts silently when the intended operation was an error.

### Medium — two or three concepts

5. Combining the design matrix with the two derived square matrices: state the shape of the feature-space and measurement-space matrices, describe what each encodes, and explain what it means to call them dual.
6. Combining rank with the normal equations of Chapter 01: explain what rank deficiency does to a least-squares fit, and what it implies about your choice of features.
7. Combining eigendecomposition with the singular value decomposition: explain why the SVD of the data is preferred over the eigendecomposition of the covariance matrix, giving both a numerical and a practical reason.

### Hard — three or more concepts *(stretch — beyond the lab ceiling)*

8. Bring together the design matrix, the covariance matrix, and the eigendecomposition to explain what it would mean for a dataset to have one dominant eigenvalue. State what you would conclude scientifically, and what you would check before believing it.
9. Using rank, conditioning, and the choice between solving and inverting, explain why two collaborators fitting the same linear model to the same data can obtain visibly different parameters. Describe what you would compute to diagnose which result to trust.
10. Combining the design matrix, centring, the covariance and Gram matrices, and the SVD, explain how a single factorisation of the data gives you access to structure in both feature space and measurement space at once. State what each factor of the decomposition is used for.

## B. Mathematical

*Where to look: [[Chapter02#Key math|Key math]] · [[Chapter02#Concept overview|Concept overview]]*

### Easy — state a definition

1. Define the design matrix. State its shape and what each of its two indices ranges over.
2. Define the scatter, covariance, and Gram matrices in terms of the centred design matrix, and give the shape of each.
3. Define the singular value decomposition of a matrix: name the three factors, give their shapes, and state the constraint each satisfies.
4. Define the $\ell_1$, $\ell_2$, and $\ell_\infty$ norms of a vector.
5. Define the centring operator in matrix form, and state what it does to a design matrix.

### Medium — prove or state a property *(stretch — beyond the lab ceiling)*

6. Prove that the scatter matrix is symmetric and positive semi-definite, and state what this guarantees about its eigenvalues.
7. Given the singular value decomposition of a matrix, derive the eigendecomposition of its Gram and covariance matrices, and state the relationship between singular values and eigenvalues.
8. Show that $\mathbf{X}\mathbf{X}^\top$ and $\mathbf{X}^\top\mathbf{X}$ share the same non-zero eigenvalues, and state the maximum number of them in terms of the matrix dimensions.
9. Prove that the centring operator is symmetric and idempotent, and determine its rank.
10. Derive the matrix that orthogonally projects onto the span of a single vector. Prove it is idempotent and that the residual is orthogonal to the projection direction.

## C. Coding

*Where to look: [[Chapter02#Code examples|Code examples]] · [[Chapter02#Key math|Key math]]*

### Easy — a single function

1. Write a function that centres a design matrix by column and returns the result.
2. Write a function that returns the scatter, covariance, and Gram matrices of a centred design matrix.
3. Write a function that projects one vector onto another with no explicit loops.
4. Write a function that estimates the numerical rank of a matrix from its singular values, taking a tolerance as an argument.

### Medium — two or three functions

5. Using your centring and covariance functions, compute the principal directions by eigendecomposition, and write a second function that computes them by SVD. Assert numerically that the two agree.
6. Write a function that solves a linear system and one that inverts and multiplies, plus a third that reports the residual of each. Compare them on a well-conditioned and a badly conditioned matrix.
7. Using your projection function, write a routine that orthogonalises a small set of vectors one at a time, and verify the result is orthonormal.

### Hard — three or more functions *(stretch — beyond the lab ceiling)*

8. Combine matrix generation, rank estimation, and noise injection into a study of how the estimated rank of a known low-rank matrix degrades as noise grows. Report the noise level at which the true rank is no longer recoverable, and state the criterion you used.
9. Build a set of functions that construct a design matrix with a controllable degree of collinearity, fit a linear model, and report both the fitted parameters and the condition number. Use them to show how parameter instability tracks conditioning.
10. Write separate functions to centre, to form the covariance and Gram matrices, to decompose each, and to compare their spectra. Use them to demonstrate on real data that the two matrices share their non-zero eigenvalues, and report where numerical agreement breaks down.
