# Chapter 08 — Principal Component Analysis — Question Bank

> **The question this chapter answers.** *You have two thousand measured channels and suspect only a handful of things are actually varying. How would you find out how many, and what they are?*
>
> Write an answer here **before you look anything up**. You have the notes already; the point is to find out what you do not know first. Then open them, or ask an LLM, and correct what you wrote — keep both versions. The gap between your attempt and the answer is the part you will remember.

> **No answers are provided.** Sections A and B are prepared by the Friday before the Monday lecture, where they are quizzed in class. Section C is practised between the lecture and the Thursday lab — until you can do each unaided, without AI, on a lab desktop.
> Tiers are set by *composition*: how many distinct concepts a question requires (Section A), or how many functions you must write and connect (Section C). Section B is tiered differently — Easy asks you to state a definition, Medium to prove or state a property of one.
> **Assessed scope.** Sections A and B are quizzed in the **Monday lecture** — conceptual to Medium, mathematical to Easy. Section C is answered in the **Thursday lab** — coding to Medium. That is **19 of this chapter's 30 questions**. The tiers marked *stretch* are quizzed in neither session; attempt them if you finish early, and expect them in the block homework and the final examination.

**Notes:** [[Chapter08]] · [[Chapter08#Learning outcomes|Learning outcomes]] · [[Chapter08#Optional Reading and References|Optional reading]]

## A. Conceptual short-answer

*Where to look: [[Chapter08#Concept overview|Concept overview]] · [[Chapter08#Applications|Applications]]*

### Easy — a single concept

1. State the two equivalent framings of PCA and explain why they give the same answer.
2. What does centring do for PCA, and what goes wrong if you skip it?
3. How do you read a scree plot, and what is it used to decide?
4. Distinguish a score from a loading. State which has one entry per sample and which has one entry per feature, and give a question that only the loadings can answer.

### Medium — two or three concepts

5. Combining the covariance matrix of Chapter 02 with the eigendecomposition: explain in what precise sense PCA is optimal, naming the class of methods it is optimal within and the criterion used.
6. Combining standardisation with the interpretation of components: give a scientific situation in which failing to standardise would let one measurement dominate entirely, and state how you would notice.
7. Combining the loadings, the eigenvalue spectrum, and the feature covariance of Chapter 03: explain in what sense a truncated PCA is a model of the correlation structure between features, and say what you would learn from the part of the covariance matrix it fails to reproduce.

### Hard — three or more concepts *(stretch — beyond the lab ceiling)*

8. Bring together the contribution of a feature to a component, the $\cos^2$ of that feature, and the arbitrariness of the eigenvector sign to state precisely which claims a loading plot licenses and which it does not. Give one claim of each kind about the same figure.
9. Using the design matrix, the curse of dimensionality, and the correlation structure of Chapter 03, explain why thousands of correlated measurements so often reduce to a handful of components — and what it would mean scientifically if they did not.
10. Combining PCA, the manifold picture, and the loss-function idea of Chapter 01, explain what PCA is minimising, what a nonlinear method minimises instead, and how you would decide which your data requires before running either.

## B. Mathematical

*Where to look: [[Chapter08#Key math|Key math]] · [[Chapter08#Concept overview|Concept overview]]*

### Easy — state a definition

1. Define the centred design matrix and the scatter matrix.
2. Define the principal directions, the latent coordinates, and the reconstruction.
3. Write the PCA optimisation objective together with its orthonormality constraint.
4. Define an eigenvalue of the covariance matrix and the explained-variance ratio.
5. Define the loading of a feature on a component, the contribution of that feature to the component, and the correlation loading.

### Medium — prove or state a property *(stretch — beyond the lab ceiling)*

6. Show that maximising the variance of a projection subject to a unit-norm constraint yields an eigenvector equation, and identify what the Lagrange multiplier equals.
7. Given the singular value decomposition of the centred design matrix, express the principal directions, the latent coordinates, and the eigenvalues in terms of its factors.
8. Prove that the total variance equals the sum of the eigenvalues, and derive the reconstruction error of a truncated representation in terms of the discarded eigenvalues. State the corresponding error for the truncated covariance matrix, and account for the difference between the two expressions.
9. Prove that the principal directions are mutually orthogonal, naming the property of the covariance matrix that guarantees it. Use the resulting spectral decomposition to show that a feature's variance is $\sum_l \lambda_l u_{dl}^2$, and state what the partial sum over the retained components measures.
10. Show that rescaling each feature by its own constant does not in general preserve the principal directions, and use this to argue when standardisation is mandatory.

## C. Coding

*Where to look: [[Chapter08#Code examples|Code examples]] · [[Chapter08#Key math|Key math]]*

### Easy — a single function

1. Write a function that returns, for a given component, the features with the largest contributions, together with their loadings and signs.
2. Write a function returning the principal directions and eigenvalues by eigendecomposition of the covariance matrix.
3. Write a function returning the principal directions by singular value decomposition.
4. Write a function that projects data onto a given number of components and returns the latent coordinates.

### Medium — two or three functions

5. Write a function returning the correlation loadings of every feature on the first two components, and one that plots them inside the unit circle. Use them to name two features that co-vary and one that the projection does not represent.
6. Write a reconstruction function and use it with your projection function to verify that the reconstruction error matches the sum of discarded eigenvalues.
7. Write a function producing a scree plot and one producing a cumulative explained-variance curve. Use both to select a latent dimension and defend the choice.

### Hard — three or more functions *(stretch — beyond the lab ceiling)*

8. Write functions to build the rank-$L$ model of the feature covariance matrix, to compare it against the sample covariance, and to display the residual. Use them to report how many components are needed before the residual holds no visible structure, and name one pair of features whose correlation the model does not reproduce.
9. Write functions to generate data on a known curved manifold, to apply PCA, and to measure distance distortion between original and projected data. Use them to quantify PCA's failure, and compare against the same measurement on data genuinely occupying a linear subspace.
10. Assemble functions for standardising, for PCA, and for comparing component loadings, then use them to show how the leading components change when one feature's units are altered. Report which conclusions change, and state the preprocessing rule you would adopt.
