# Chapter 19 — Gaussian Mixture Models — Question Bank

> **The question this chapter answers.** *Some measurements clearly belong to one group; others sit between two. How would you describe the ones in between?*
>
> Write an answer here **before you look anything up**. You have the notes already; the point is to find out what you do not know first. Then open them, or ask an LLM, and correct what you wrote — keep both versions. The gap between your attempt and the answer is the part you will remember.

> **No answers are provided.** Sections A and B are prepared by the Friday before the Monday lecture, where they are quizzed in class. Section C is practised between the lecture and the Thursday lab — until you can do each unaided, without AI, on a lab desktop.
> Tiers are set by *composition*: how many distinct concepts a question requires (Section A), or how many functions you must write and connect (Section C). Section B is tiered differently — Easy asks you to state a definition, Medium to prove or state a property of one.
> **Assessed scope.** Sections A and B are quizzed in the **Monday lecture** — conceptual to Medium, mathematical to Easy. Section C is answered in the **Thursday lab** — coding to Medium. That is **19 of this chapter's 30 questions**. The tiers marked *stretch* are quizzed in neither session; attempt them if you finish early, and expect them in the block homework and the final examination.

**Notes:** [[Chapter19]] · [[Chapter19#Learning outcomes|Learning outcomes]] · [[Chapter19#Optional Reading and References|Optional reading]]

## A. Conceptual short-answer

*Where to look: [[Chapter19#Concept overview|Concept overview]] · [[Chapter19#Applications|Applications]]*

### Easy — a single concept

1. Write a mixture model in words and state the constraints on the mixing weights.
2. Define a responsibility, stating its range and what it sums to.
3. Name the common covariance structures a component can be given, ordered by number of free parameters.
4. Describe the singularity pathology of maximum-likelihood mixture fitting.

### Medium — two or three concepts

5. Combining soft assignment with the hard assignment of Chapter 14: describe what information a responsibility carries that a label destroys, and give a measurement situation where that information matters.
6. Combining the covariance structure with the number of samples: explain how you would choose between a full and a constrained covariance, and what happens if you choose the richer model with too little data.
7. Combining the latent assignment with Bayes' rule from Chapter 04: explain how the responsibility is a posterior, and identify the prior and the likelihood within it.

### Hard — three or more concepts *(stretch — beyond the lab ceiling)*

8. Bring together the mixture density, the latent assignment, and the alternating algorithm of Chapter 18 to explain why the fitting procedure works and what it is guaranteed to achieve.
9. Using the singularity pathology, the likelihood surface, and the notion of regularisation, explain why an unbounded likelihood does not indicate a good fit, and describe two distinct remedies with what each costs.
10. Combining the mixture model, the shrinking-covariance limit, and the clustering objective of Chapter 14, explain precisely what is discarded when you use centroid clustering in place of a mixture model — and describe a scientific setting in which that loss would change your conclusion.

## B. Mathematical

*Where to look: [[Chapter19#Key math|Key math]] · [[Chapter19#Concept overview|Concept overview]]*

### Easy — state a definition

1. Write the mixture density and state the constraints on the mixing weights.
2. Write the multivariate Gaussian density, naming every symbol.
3. Define the responsibility of a component for a data point.
4. Write the complete-data likelihood using an indicator form.
5. Write the observed-data log-likelihood.

### Medium — prove or state a property *(stretch — beyond the lab ceiling)*

6. Derive the responsibility by applying Bayes' rule to the latent assignment.
7. Derive the update for the component means by maximising the expected complete-data log-likelihood.
8. Derive the update for the mixing weights using a Lagrange multiplier to enforce normalisation.
9. Explain why the sum inside the logarithm of the observed-data log-likelihood prevents a closed-form solution.
10. Show that as the component covariances shrink towards isotropy with vanishing scale the responsibilities become hard indicators, and identify which step becomes which step of centroid clustering.

## C. Coding

*Where to look: [[Chapter19#Code examples|Code examples]] · [[Chapter19#Key math|Key math]]*

### Easy — a single function

1. Write a numerically stable function returning the log-density of a multivariate Gaussian, using a matrix factorisation rather than an explicit inverse.
2. Write a function computing responsibilities from current parameters, in the log domain.
3. Write a function performing the parameter update given responsibilities.
4. Write a function computing an information criterion from a fitted model's log-likelihood and parameter count.

### Medium — two or three functions

5. Combine your log-density and responsibility functions into one full expectation step, and verify that each point's responsibilities sum to one.
6. Assemble your two step functions into a complete fitting loop with a convergence check, and compare your fitted parameters against a library implementation allowing for component permutation.
7. Write a function that fits at a given component count and one that evaluates held-out log-likelihood, and use them to compare two covariance structures on the same data.

### Hard — three or more functions *(stretch — beyond the lab ceiling)*

8. Build functions for fitting, for computing at least two information criteria, and for plotting them against component count. Report where the criteria agree and disagree, and which you would follow.
9. Assemble generation, fitting, and component-ellipse plotting functions into a comparison of all available covariance structures on data that genuinely requires a full covariance. Report held-out log-likelihood for each and display the best and worst fits.
10. Write functions to simulate two nearby sources with realistic scatter, to fit a two-component mixture, and to measure the error in the recovered source positions. Sweep the separation and report the point at which the fit stops resolving the two sources, relating it to the measurement precision.
