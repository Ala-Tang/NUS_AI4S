# Chapter 03 — Design Matrix, Correlations, and the CLT — Question Bank

> **The question this chapter answers.** *How would you know whether two of your measurements are telling you the same thing?*
>
> Write an answer here **before you look anything up**. You have the notes already; the point is to find out what you do not know first. Then open them, or ask an LLM, and correct what you wrote — keep both versions. The gap between your attempt and the answer is the part you will remember.

> **No answers are provided.** Sections A and B are prepared by the Friday before the Monday lecture, where they are quizzed in class. Section C is practised between the lecture and the Thursday lab — until you can do each unaided, without AI, on a lab desktop.
> Tiers are set by *composition*: how many distinct concepts a question requires (Section A), or how many functions you must write and connect (Section C). Section B is tiered differently — Easy asks you to state a definition, Medium to prove or state a property of one.
> **Assessed scope.** Sections A and B are quizzed in the **Monday lecture** — conceptual to Medium, mathematical to Easy. Section C is answered in the **Thursday lab** — coding to Medium. That is **19 of this chapter's 30 questions**. The tiers marked *stretch* are quizzed in neither session; attempt them if you finish early, and expect them in the block homework and the final examination.

**Notes:** [[Chapter03]] · [[Chapter03#Learning outcomes|Learning outcomes]] · [[Chapter03#Optional Reading and References|Optional reading]]

## A. Conceptual short-answer

*Where to look: [[Chapter03#Concept overview|Concept overview]] · [[Chapter03#Applications|Applications]]*

### Easy — a single concept

1. State the Central Limit Theorem precisely, including every condition it requires.
2. What does a large off-diagonal entry in a feature covariance matrix tell you about a dataset?
3. Define Shannon entropy and state what a high value and a low value each mean.
4. Two variables have zero linear correlation but are strongly dependent. Describe such a relationship.

### Medium — two or three concepts

5. Combining covariance with the Gram matrix from Chapter 02: explain why a statement about co-varying features and a statement about similar measurements are different scientific claims, and give a dataset where you would care about each.
6. Combining the CLT with the maximum-entropy principle: explain why so many measured quantities turn out approximately Gaussian, giving both arguments and saying how they relate.
7. Combining correlation with entropy-based dependence: explain what is lost by summarising a dataset with a correlation matrix alone, and what you would report alongside it.

### Hard — three or more concepts *(stretch — beyond the lab ceiling)*

8. Bring together the design matrix, the covariance matrix, and the CLT to explain why the noise on a derived quantity in your own field is usually treated as Gaussian, and identify the step in that reasoning most likely to fail in practice.
9. Using entropy, cross-entropy, and KL divergence together, explain why a single dataset can be described as "high entropy" and yet be well predicted by a model, and what each of the three quantities is measuring in that situation.
10. Combining the CLT, the Gaussian's maximum-entropy property, and the notion of a loss function from Chapter 01, explain why squared error is the default loss in so much of science — and construct the argument for when that default should be abandoned.

## B. Mathematical

*Where to look: [[Chapter03#Key math|Key math]] · [[Chapter03#Concept overview|Concept overview]]*

### Easy — state a definition

1. Define the covariance of two random variables, and the covariance matrix of a design matrix.
2. Define the Pearson correlation coefficient and state its range.
3. Define Shannon entropy, and state its units under a base-2 and a natural logarithm.
4. Define cross-entropy and KL divergence for two discrete distributions.
5. State the Central Limit Theorem, defining every symbol and every condition it requires.

### Medium — prove or state a property *(stretch — beyond the lab ceiling)*

6. Derive $\mathrm{Cov}(X, Y) = \mathbb{E}[XY] - \mathbb{E}[X]\mathbb{E}[Y]$, then prove that the magnitude of the correlation cannot exceed 1 using the Cauchy–Schwarz inequality.
7. Explain the role of the $1/\sqrt{N}$ scaling in the CLT: state what goes wrong under $1/N$ scaling and under no scaling at all.
8. Show how cumulants above the second scale with $N$ after standardisation, and explain why this leaves only a Gaussian.
9. Prove that the KL divergence is non-negative with equality only when the distributions coincide, then show by explicit counterexample that it is not symmetric.
10. Derive the differential entropy of a Gaussian, and argue that among all densities of a given variance the Gaussian maximises it.

## C. Coding

*Where to look: [[Chapter03#Code examples|Code examples]] · [[Chapter03#Key math|Key math]]*

### Easy — a single function

1. Write a function that returns the correlation matrix of a design matrix, given its covariance.
2. Write a function computing Shannon entropy in bits from a set of counts.
3. Write a function computing the KL divergence between two discrete distributions, with a guard against zero probabilities.
4. Write a function that returns the indices and value of the largest off-diagonal entry of a symmetric matrix.

### Medium — two or three functions

5. Using your entropy and KL functions, verify at least two identities relating entropy, cross-entropy, and KL divergence numerically, on distributions you construct.
6. Write a function that draws standardised sums of $N$ samples from a chosen distribution, and a second that plots the resulting histograms for several values of $N$. Use them to demonstrate the CLT and comment on how fast convergence is for your chosen distribution.
7. Combine your covariance and correlation functions with a plotting routine to display both matrices for the same dataset, and report where they differ in appearance and why.

### Hard — three or more functions *(stretch — beyond the lab ceiling)*

8. Build a set of functions to estimate mutual information by binning, to compute Pearson correlation, and to generate data with a controllable nonlinear dependence. Use them to show that the two measures disagree, and report how the disagreement varies with the strength of the nonlinearity.
9. Write functions to draw samples, to estimate cumulants, and to standardise partial sums. Use them to verify the cumulant-decay prediction of the CLT empirically, fitting the decay exponent and comparing it against theory.
10. Construct a pipeline of functions that loads a real design matrix, centres it, computes both derived square matrices, extracts the leading structure of each, and reports which features co-vary and which measurements resemble each other. Present both findings as a single interpretation of the dataset.
