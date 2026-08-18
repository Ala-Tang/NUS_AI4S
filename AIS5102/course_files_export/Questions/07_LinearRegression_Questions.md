# Chapter 07 — Linear Regression — Question Bank

> **The question this chapter answers.** *You want to predict one measured quantity from several others. What is the simplest thing that works, and how would you know it had failed?*
>
> Write an answer here **before you look anything up**. You have the notes already; the point is to find out what you do not know first. Then open them, or ask an LLM, and correct what you wrote — keep both versions. The gap between your attempt and the answer is the part you will remember.

> **No answers are provided.** Sections A and B are prepared by the Friday before the Monday lecture, where they are quizzed in class. Section C is practised between the lecture and the Thursday lab — until you can do each unaided, without AI, on a lab desktop.
> Tiers are set by *composition*: how many distinct concepts a question requires (Section A), or how many functions you must write and connect (Section C). Section B is tiered differently — Easy asks you to state a definition, Medium to prove or state a property of one.
> **Assessed scope.** Sections A and B are quizzed in the **Monday lecture** — conceptual to Medium, mathematical to Easy. Section C is answered in the **Thursday lab** — coding to Medium. That is **19 of this chapter's 30 questions**. The tiers marked *stretch* are quizzed in neither session; attempt them if you finish early, and expect them in the block homework and the final examination.

**Notes:** [[Chapter07]] · [[Chapter07#Learning outcomes|Learning outcomes]] · [[Chapter07#Optional Reading and References|Optional reading]]

## A. Conceptual short-answer

*Where to look: [[Chapter07#Concept overview|Concept overview]] · [[Chapter07#Applications|Applications]]*

### Easy — a single concept

1. State the geometric interpretation of ordinary least squares as a projection, naming the space being projected onto.
2. What is a basis function, and why does using one leave the model linear?
3. What does ridge regression do to the fitted coefficients, and in what circumstance is it defined when ordinary least squares is not?
4. Name the three things a residual plot can reveal that a single goodness-of-fit number cannot.

### Medium — two or three concepts

5. Combining the normal equations with rank from Chapter 02: explain what collinearity does to the fitted coefficients while leaving the fitted *predictions* stable, and say which of the two you should report.
6. Combining basis expansion with the bias–variance idea: explain why adding basis functions always improves training error but eventually worsens test error.
7. Combining the ridge and lasso penalties: explain geometrically why one produces exact zeros and the other does not, and state when you would want each.

### Hard — three or more concepts *(stretch — beyond the lab ceiling)*

8. Bring together the Gaussian likelihood of Chapter 05, the squared-error loss, and the normal equations to explain in what sense least squares is not an arbitrary choice — and identify the assumption that, if violated, makes it the wrong one.
9. Using the projection geometry, the residual, and the equal-variance assumption together, explain what a funnel-shaped residual plot indicates and what modification to the fit it calls for.
10. Bring together collinearity, the ridge shrinkage factor, and lasso's variable selection to describe what each penalty does to a set of three nearly identical features. State which coefficients you would report, and what you would refuse to claim about the importance of any one of the three.

## B. Mathematical

*Where to look: [[Chapter07#Key math|Key math]] · [[Chapter07#Concept overview|Concept overview]]*

### Easy — state a definition

1. Write the ordinary least-squares objective and the normal equations.
2. Define the hat matrix and write the fitted values in terms of it.
3. Write the ridge objective and its closed-form solution.
4. Write the lasso objective and state why it has no closed form.
5. Define the coefficient of determination and the variance inflation factor.

### Medium — prove or state a property *(stretch — beyond the lab ceiling)*

6. Prove that the hat matrix is symmetric and idempotent, and state its rank and its trace.
7. Prove that the residual vector is orthogonal to every column of the design matrix, and deduce that the residuals sum to zero when an intercept is included.
8. Working in the eigenbasis of $\mathbf{X}^\top\mathbf{X}$, derive the coordinate-wise shrinkage factor of ridge regression, and show that directions of smallest variance are shrunk hardest.
9. Show that the ridge solution exists and is unique for any positive penalty, even when the design matrix is rank-deficient, and identify what the penalty does to the eigenvalues.
10. Derive the weighted least-squares estimator for known per-point variances, and show it reduces to ordinary least squares when all variances are equal.

## C. Coding

*Where to look: [[Chapter07#Code examples|Code examples]] · [[Chapter07#Key math|Key math]]*

### Easy — a single function

1. Write a function that fits a linear model by solving the normal equations and returns the coefficients.
2. Write a function that returns the residuals of a fitted linear model.
3. Write a function that computes the coefficient of determination from targets and predictions.
4. Write a function that returns the variance inflation factor of a chosen feature.

### Medium — two or three functions

5. Using your fitting and residual functions, produce a residual-against-fitted plot, and write a third function that reports whether the residuals show a systematic trend.
6. Write a function that builds a polynomial basis and one that fits and scores a model on it. Use them to report train and test performance across several degrees.
7. Write a function that fits a ridge model at a given penalty and one that sweeps the penalty, and use them to plot the coefficient shrinkage path.

### Hard — three or more functions *(stretch — beyond the lab ceiling)*

8. Build functions for data generation with controllable collinearity, for fitting, and for reporting both the coefficients and the variance inflation factors. Use them to show that coefficient instability tracks collinearity while the predictions remain stable.
9. Write functions to generate data with known, non-constant per-point variances, to fit by ordinary least squares, and to fit by weighted least squares. Compare both estimators against the truth over many replicates, and report which you would use and what the unweighted fit costs you.
10. Write functions implementing ridge and lasso fits, a common evaluation routine, and a sparsity counter. Apply all of them to a dataset with more features than samples, report the counts of non-zero coefficients, and state which model you would publish and why.
