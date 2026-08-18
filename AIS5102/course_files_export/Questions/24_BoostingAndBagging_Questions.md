# Chapter 24 — Bagging and Boosting — Question Bank

> **The question this chapter answers.** *You have many models, each individually mediocre. How would you combine them into one that is better than any of them — and does it matter whether you build them independently or one after another?*
>
> Write an answer here **before you look anything up**. You have the notes already; the point is to find out what you do not know first. Then open them, or ask an LLM, and correct what you wrote — keep both versions. The gap between your attempt and the answer is the part you will remember.

> **No answers are provided.** Sections A and B are prepared by the Friday before the Monday lecture, where they are quizzed in class. Section C is practised between the lecture and the Thursday lab — until you can do each unaided, without AI, on a lab desktop.
> Tiers are set by *composition*: how many distinct concepts a question requires (Section A), or how many functions you must write and connect (Section C). Section B is tiered differently — Easy asks you to state a definition, Medium to prove or state a property of one.
> **Assessed scope.** Sections A and B are quizzed in the **Monday lecture** — conceptual to Medium, mathematical to Easy. Section C is answered in the **Thursday lab** — coding to Medium. That is **19 of this chapter's 30 questions**. The tiers marked *stretch* are quizzed in neither session; attempt them if you finish early, and expect them in the block homework and the final examination.

**Notes:** [[Chapter24]] · [[Chapter24#Learning outcomes|Learning outcomes]] · [[Chapter24#Optional Reading and References|Optional reading]]

## A. Conceptual short-answer

*Where to look: [[Chapter24#Concept overview|Concept overview]] · [[Chapter24#Applications|Applications]]*

### Easy — a single concept

1. State which component of the generalisation error bagging primarily attacks, and by what mechanism.
2. What does bootstrap resampling do, and what is the out-of-bag sample?
3. What single ingredient do random forests add to plain bagging?
4. State what plays the role of the gradient in gradient boosting, and what quantity it is a gradient with respect to.

### Medium — two or three concepts

5. Combining tree instability from Chapter 23 with averaging: explain why high-variance, low-bias learners are the natural base for an averaging ensemble, and what would be gained by averaging a strongly biased learner instead.
6. Combining the correlation between ensemble members with the variance of their average: explain why de-correlating members improves the ensemble beyond what more members alone can achieve.
7. Combining the sequential reweighting with the notion of a weak learner: describe what happens to a member that performs no better than chance, and what the algorithm does with it.

### Hard — three or more concepts *(stretch — beyond the lab ceiling)*

8. Bring together the bias–variance decomposition of Chapter 22, bootstrap resampling, and feature subsampling to explain exactly where a random forest's advantage over a single tree comes from, and where that advantage stops.
9. Using the loss function of Chapter 01, the functional-gradient view, and the shrinkage parameter, explain how gradient boosting generalises simple residual fitting to an arbitrary differentiable loss, and what the shrinkage buys you.
10. Combining ensemble size, the shrinkage rate, and validation from Chapter 22, describe how you would tune a gradient-boosted model on a modest scientific dataset without over-fitting the tuning itself. State the two hyperparameters most likely to cause trouble and the failure each produces.

## B. Mathematical

*Where to look: [[Chapter24#Key math|Key math]] · [[Chapter24#Concept overview|Concept overview]]*

### Easy — state a definition

1. Write the bias–variance decomposition and name each term.
2. Define a bootstrap replicate and the out-of-bag set.
3. Define the weighted error of a weak learner.
4. Write the AdaBoost learner weight and the sample-weight update.
5. Write the gradient-boosting update, defining the shrinkage parameter.

### Medium — prove or state a property *(stretch — beyond the lab ceiling)*

6. Derive the variance of an average of $M$ identically distributed predictors with pairwise correlation $\rho$, and evaluate the large-$M$ limit for several values of $\rho$.
7. Show that the probability a sample is omitted from a bootstrap replicate approaches a specific constant as sample size grows, and state the resulting out-of-bag fraction.
8. Derive the optimal weight for a weak learner by minimising an exponential loss at a single boosting round, in terms of its weighted error.
9. Show that after the sample-weight update the just-fitted learner has weighted error exactly one half under the new weights, and interpret this.
10. Derive the pseudo-residual for gradient boosting under squared error and under logistic loss, showing what familiar quantity each reduces to.

## C. Coding

*Where to look: [[Chapter24#Code examples|Code examples]] · [[Chapter24#Key math|Key math]]*

### Easy — a single function

1. Write a function that draws a bootstrap replicate of a dataset and returns both the in-bag and out-of-bag indices.
2. Write a function that fits a single shallow base learner to weighted data.
3. Write a function that computes the weighted error of a learner on a dataset.
4. Write a function that combines a list of learners and weights into a single prediction.

### Medium — two or three functions

5. Combine your bootstrap and base-learner functions into an averaging ensemble, and compare its accuracy against a single learner on the same data.
6. Combine your weighted-error and combination functions with a weight-update function to implement one full boosting round, and verify the reweighted error behaves as theory predicts.
7. Write a function that returns out-of-bag predictions from your averaging ensemble, and compare the resulting score against a held-out test score.

### Hard — three or more functions *(stretch — beyond the lab ceiling)*

8. Assemble your base learner, weighted-error, weight-update, and combination functions into a complete from-scratch sequential ensemble. Record the weighted error and learner weight at every round, plot both, and compare final accuracy against a library implementation.
9. Build functions to fit both ensemble types across a range of ensemble sizes, to score each, and to plot the curves together. Report where each saturates and explain the difference.
10. Write functions to fit an averaging ensemble with and without feature subsampling, to extract individual member predictions, and to compute their average pairwise correlation on held-out data. Report both correlations alongside both accuracies, and check the numbers against the variance formula from Section B.
