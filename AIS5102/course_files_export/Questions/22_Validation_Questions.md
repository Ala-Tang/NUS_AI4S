# Chapter 22 — Validation for Supervised Learning — Question Bank

> **The question this chapter answers.** *Your classifier is 97 % accurate on the data you built it from. What would convince you it will work on data you have not seen?*
>
> Write an answer here **before you look anything up**. You have the notes already; the point is to find out what you do not know first. Then open them, or ask an LLM, and correct what you wrote — keep both versions. The gap between your attempt and the answer is the part you will remember.

> **No answers are provided.** Sections A and B are prepared by the Friday before the Monday lecture, where they are quizzed in class. Section C is practised between the lecture and the Thursday lab — until you can do each unaided, without AI, on a lab desktop.
> Tiers are set by *composition*: how many distinct concepts a question requires (Section A), or how many functions you must write and connect (Section C). Section B is tiered differently — Easy asks you to state a definition, Medium to prove or state a property of one.
> **Assessed scope.** Sections A and B are quizzed in the **Monday lecture** — conceptual to Medium, mathematical to Easy. Section C is answered in the **Thursday lab** — coding to Medium. That is **19 of this chapter's 30 questions**. The tiers marked *stretch* are quizzed in neither session; attempt them if you finish early, and expect them in the block homework and the final examination.

**Notes:** [[Chapter22]] · [[Chapter22#Learning outcomes|Learning outcomes]] · [[Chapter22#Optional Reading and References|Optional reading]]

## A. Conceptual short-answer

*Where to look: [[Chapter22#Concept overview|Concept overview]] · [[Chapter22#Applications|Applications]]*

### Easy — a single concept

1. Define overfitting in terms of two quantities you can actually measure.
2. Name the three terms in the bias–variance decomposition and state which one no model can reduce.
3. What is data leakage? Name three structurally different ways it arises.
4. When is stratification necessary rather than merely convenient?

### Medium — two or three concepts

5. Combining hold-out with $K$-fold cross-validation: compare them on cost, bias, and variance of the estimate, and state when each is the right choice.
6. Combining model complexity with the bias–variance terms: describe how each term moves as complexity grows, and what the resulting test-error curve looks like.
7. Combining preprocessing with the cross-validation loop: explain exactly what goes wrong if you scale before splitting, and how pipelining fixes it.

### Hard — three or more concepts *(stretch — beyond the lab ceiling)*

8. Bring together class imbalance, the confusion matrix, and the choice of metric to explain how a classifier can reach 95 % accuracy while performing no better than always predicting the majority class. Name the metrics you would report instead, and the baseline you would report them against.
9. Combining a null model, the baseline rate, and the reported metric, describe the controls you would run before believing a classification result. State what score on permuted labels would make you withdraw the finding.
10. Combining the penalties of Chapter 07, the units of the individual features, and cross-validated selection of the penalty strength, describe how you would fit a predictive model to a dataset with more features than samples. State what a penalty on the coefficient vector does when the features are on different scales, and name the two places a careless analysis would go wrong.

## B. Mathematical

*Where to look: [[Chapter22#Key math|Key math]] · [[Chapter22#Concept overview|Concept overview]]*

### Easy — state a definition

1. Write the $K$-fold cross-validation error estimate, defining every symbol.
2. Define the four entries of a binary confusion matrix.
3. Define precision, recall, and their harmonic mean.
4. Write the bias–variance decomposition for squared error, naming each term.
5. Define the standard error of a mean.

### Medium — prove or state a property *(stretch — beyond the lab ceiling)*

6. State how many models are fitted under $K$-fold, under leave-one-out, and under a grid search nested inside $K$-fold, in terms of the relevant counts.
7. Derive the bias–variance decomposition for squared error, stating the independence assumption used.
8. Show that the harmonic mean is the appropriate combination of precision and recall, and what would go wrong with an arithmetic mean.
9. For a strongly imbalanced problem, compute the accuracy of a majority-class predictor and use it to argue why accuracy alone is inadequate.
10. Given the sample standard deviation of fold scores, derive the standard error of their mean, and explain why quoting the spread overstates the uncertainty in mean performance.

## C. Coding

*Where to look: [[Chapter22#Code examples|Code examples]] · [[Chapter22#Key math|Key math]]*

### Easy — a single function

1. Write a function producing a stratified train/test split and returning both halves.
2. Write a function computing precision, recall, and their harmonic mean from a confusion matrix.
3. Write a function that generates the index pairs for $K$-fold cross-validation.
4. Write a function that fits a model on given training indices and returns a score on the held-out indices.

### Medium — two or three functions

5. Combine your fold-generation and fit-and-score functions into a complete cross-validation routine, and report the mean score with its standard error.
6. Write a pipelining function that applies preprocessing inside each fold, and compare its cross-validated score against a version that preprocesses the whole dataset first. Report the optimism.
7. Write a function generating an imbalanced dataset and one comparing stratified against unstratified folds, reporting per-fold class counts and the resulting metric spread.

### Hard — three or more functions *(stretch — beyond the lab ceiling)*

8. Assemble functions for building a feature basis, for fitting at a given penalty, and for cross-validated scoring, into a complete model-selection pipeline. Sweep the basis size and the penalty together, plot training against validation error, and report the pair you would choose and what the gap between the two curves tells you.
9. Build functions for group-structured data generation, for group-respecting folds, and for group-ignoring folds. Report both cross-validated scores, quantify the leakage as the gap, and state which number a careless analysis would have published.
10. Implement nested cross-validation from scratch using separate functions for the outer loop, the inner hyperparameter search, and the final scoring. Compare its estimate against the best inner score from a single non-nested search on the same data, and report the gap as a measure of selection bias.
