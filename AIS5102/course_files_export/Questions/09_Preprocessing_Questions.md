# Chapter 09 — Preprocessing and Feature Scaling — Question Bank

> **The question this chapter answers.** *One feature is measured in nanometres and another in volts. What has to happen before you can compute a distance between two samples?*
>
> Write an answer here **before you look anything up**. You have the notes already; the point is to find out what you do not know first. Then open them, or ask an LLM, and correct what you wrote — keep both versions. The gap between your attempt and the answer is the part you will remember.

> **No answers are provided.** Sections A and B are prepared by the Friday before the Monday lecture, where they are quizzed in class. Section C is practised between the lecture and the Thursday lab — until you can do each unaided, without AI, on a lab desktop.
> Tiers are set by *composition*: how many distinct concepts a question requires (Section A), or how many functions you must write and connect (Section C). Section B is tiered differently — Easy asks you to state a definition, Medium to prove or state a property of one.
> **Assessed scope.** Sections A and B are quizzed in the **Monday lecture** — conceptual to Medium, mathematical to Easy. Section C is answered in the **Thursday lab** — coding to Medium. That is **19 of this chapter's 30 questions**. The tiers marked *stretch* are quizzed in neither session; attempt them if you finish early, and expect them in the block homework and the final examination.

**Notes:** [[Chapter09]] · [[Chapter09#Learning outcomes|Learning outcomes]] · [[Chapter09#Optional Reading and References|Optional reading]]

## A. Conceptual short-answer

*Where to look: [[Chapter09#Concept overview|Concept overview]] · [[Chapter09#Applications|Applications]]*

### Easy — a single concept

1. Name the four standard scalings and state, for each, what it preserves and what it destroys.
2. Why is min–max scaling sensitive to a single outlier in a way that robust scaling is not?
3. What does a log transform do to a distribution that no affine scaling can do?
4. Distinguish column scaling from row normalisation, and say what each is correcting for.

### Medium — two or three concepts

5. Combining scaling with the covariance matrix of Chapter 03: explain why rescaling features changes which directions carry the most variance, and name a downstream method that inherits the change.
6. Combining categorical encoding with the notion of a distance: explain when an ordinal encoding injects a false claim about the data, and what one-hot encoding costs you in return.
7. Combining missing data with the reason for its absence: distinguish the three missingness mechanisms, and state which one no imputation scheme can repair.

### Hard — three or more concepts *(stretch — beyond the lab ceiling)*

8. Bring together the design matrix, feature scaling, and the distinction between scale-sensitive and scale-invariant methods to explain how you would decide the preprocessing for a new dataset. Give the rule you would apply and one method on each side of it.
9. Using row normalisation, column scaling, and a variance-stabilising transform together, describe a defensible preprocessing pipeline for measurements whose overall intensity varies from one measurement to the next. Justify the order of the steps and state what changes if you reverse two of them.
10. Combining preprocessing parameters, the train/test split, and the idea of an honest performance estimate, explain precisely how scaling before splitting inflates a reported score. Identify what information crosses the boundary and describe the pipeline discipline that prevents it.

## B. Mathematical

*Where to look: [[Chapter09#Key math|Key math]] · [[Chapter09#Concept overview|Concept overview]]*

### Easy — state a definition

1. Write the min–max scaling of a feature to the unit interval, defining every symbol.
2. Write the standardisation of a feature, defining the mean and the sample standard deviation.
3. Write the robust scaling of a feature in terms of quartiles.
4. Write the row normalisation of a measurement to unit $\ell_p$ norm.
5. Define a variance-stabilising transform and state the condition a logarithmic transform requires of the data.

### Medium — prove or state a property *(stretch — beyond the lab ceiling)*

6. Show that standardisation and min–max scaling are both affine, and prove that no affine map can change the skewness of a distribution.
7. For a diagonal rescaling $\mathbf{X}' = \tilde{\mathbf{X}}D^{-1}$, derive the transformed covariance matrix, and show that its eigenvectors are not in general those of the original.
8. Show that min–max scaling of a feature containing one extreme outlier compresses all remaining points into an interval whose width you should quantify in terms of the outlier's magnitude.
9. Show that row-normalising to unit $\ell_2$ norm and then taking Euclidean distance is a monotone function of the cosine similarity between the original rows.
10. Show that estimating a scaling parameter from the full dataset and then splitting makes the training and test statistics dependent, and identify the quantity that leaks.

## C. Coding

*Where to look: [[Chapter09#Code examples|Code examples]] · [[Chapter09#Key math|Key math]]*

### Easy — a single function

1. Write a function that min–max scales a design matrix by column and returns the scaled data together with the fitted minima and maxima.
2. Write a function that standardises a design matrix by column, returning the scaled data and the fitted means and standard deviations.
3. Write a function that row-normalises a design matrix to unit norm under a chosen order.
4. Write a function that reports, per column, the fraction of missing entries in a design matrix.

### Medium — two or three functions

5. Write a function that applies a set of quality-control rules to a design matrix and returns the cleaned matrix together with the indices of every row and column removed and the rule that removed each one. Report the totals.
6. Write a function that applies a fitted scaling to new data, and use it with your fitting functions to demonstrate the correct train-then-apply pattern on a split dataset.
7. Write a function that imputes missing values by a chosen strategy and a second that adds an explicit missingness indicator column. Apply both and report the resulting shape.

### Hard — three or more functions *(stretch — beyond the lab ceiling)*

8. Build functions to inject an outlier of controllable magnitude, to apply all four scalings, and to summarise the resulting distributions. Use them to show which scalings are damaged by the outlier and by how much.
9. Assemble functions for scaling, for principal-component extraction, and for comparing component loadings into a demonstration that the leading directions change when features are rescaled. Report which conclusions change.
10. Write functions implementing a leaky pipeline (scale then split) and a correct one (split then scale inside each fold), plus a common evaluation routine. Report both cross-validated scores and quantify the optimism as their difference.
