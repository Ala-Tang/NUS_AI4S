# Chapter 21 — Logistic Regression — Question Bank

> **The question this chapter answers.** *You have labels for some of your measurements. How would you predict the label of a new one, and how confident should you be?*
>
> Write an answer here **before you look anything up**. You have the notes already; the point is to find out what you do not know first. Then open them, or ask an LLM, and correct what you wrote — keep both versions. The gap between your attempt and the answer is the part you will remember.

> **No answers are provided.** Sections A and B are prepared by the Friday before the Monday lecture, where they are quizzed in class. Section C is practised between the lecture and the Thursday lab — until you can do each unaided, without AI, on a lab desktop.
> Tiers are set by *composition*: how many distinct concepts a question requires (Section A), or how many functions you must write and connect (Section C). Section B is tiered differently — Easy asks you to state a definition, Medium to prove or state a property of one.
> **Assessed scope.** Sections A and B are quizzed in the **Monday lecture** — conceptual to Medium, mathematical to Easy. Section C is answered in the **Thursday lab** — coding to Medium. That is **19 of this chapter's 30 questions**. The tiers marked *stretch* are quizzed in neither session; attempt them if you finish early, and expect them in the block homework and the final examination.

**Notes:** [[Chapter21]] · [[Chapter21#Learning outcomes|Learning outcomes]] · [[Chapter21#Optional Reading and References|Optional reading]]

## A. Conceptual short-answer

*Where to look: [[Chapter21#Concept overview|Concept overview]] · [[Chapter21#Applications|Applications]]*

### Easy — a single concept

1. Write the model and state the geometric role of the weight vector's direction.
2. Why is a classification method called a regression?
3. What does convexity of the training objective guarantee, and what does it not?
4. Contrast the two standard routes to multiclass classification.

### Medium — two or three concepts

5. Combining the weight vector's direction with its magnitude: explain what the magnitude controls given that the boundary depends only on the direction, and describe the classifier's behaviour in both extremes.
6. Combining the model's linearity with feature transformation: describe two ways to obtain a non-linear boundary without abandoning the model, and state what each costs.
7. Combining the cross-entropy loss of Chapter 04 with maximum likelihood from Chapter 05: explain in what sense training this classifier is maximum likelihood, and identify the assumed noise model.

### Hard — three or more concepts *(stretch — beyond the lab ceiling)*

8. Bring together the sigmoid, the Bernoulli likelihood, and the convexity of the objective to explain why this model is so widely trusted as a baseline, and identify the single assumption most likely to be wrong in your own field.
9. Using convexity, the optimiser taxonomy of Chapter 06, and the structure of the Hessian, explain why second-order methods are practical here but not for most deep networks.
10. Combining feature expansion, regularisation, and the validation ideas you will need next chapter, describe how you would fit a classifier to a small scientific dataset and defend the reported accuracy. State the two places over-optimism is most likely to enter.

## B. Mathematical

*Where to look: [[Chapter21#Key math|Key math]] · [[Chapter21#Concept overview|Concept overview]]*

### Easy — state a definition

1. Define the logistic function and state its range.
2. Write the model and define the decision boundary.
3. Write the binary negative log-likelihood.
4. Write the softmax probability for a multiclass model.
5. Define the Hessian of the training objective.

### Medium — prove or state a property *(stretch — beyond the lab ceiling)*

6. Derive the derivative of the logistic function in terms of the function itself, and use it in deriving the gradient of the objective.
7. Starting from a Bernoulli likelihood, derive the training objective and show its gradient takes the form of the design matrix transposed against the prediction error.
8. Prove the Hessian is positive semi-definite, hence that the objective is convex, stating where the bounded link range was used.
9. Show that the softmax parameterisation is invariant to adding a common vector to every class's weights, and state the consequence for identifiability.
10. Show that for perfectly separable data the unregularised estimate does not exist, then show that a quadratic penalty restores a finite optimum.

## C. Coding

*Where to look: [[Chapter21#Code examples|Code examples]] · [[Chapter21#Key math|Key math]]*

### Easy — a single function

1. Write a logistic function that does not overflow at large-magnitude inputs.
2. Write a function returning the negative log-likelihood of a dataset given weights.
3. Write a function returning the gradient of that objective.
4. Write a function that converts predicted probabilities into class labels at a given threshold.

### Medium — two or three functions

5. Combine your objective and gradient functions into a gradient-descent fitting loop, and compare the resulting weights against a library implementation.
6. Using your fitting loop and a recording function, plot the objective against iteration for a learning rate that converges and one that does not.
7. Write a function evaluating the model on a mesh grid and one that plots the resulting decision boundary over the training data.

### Hard — three or more functions *(stretch — beyond the lab ceiling)*

8. Assemble functions for polynomial feature expansion, fitting, boundary plotting, and scoring into a study of a non-linearly-separable dataset across several expansion degrees. Report train and test accuracy for each and identify where overfitting begins.
9. Build functions for data generation with controllable separability, for unregularised fitting, and for recording the weight norm. Use them to demonstrate the divergence on separable data, then add a regularised variant and report how the norm stabilises.
10. Write functions implementing both multiclass routes, a common evaluation function, and a confusion-matrix reporter. Compare the two routes on the same multiclass problem, report both confusion matrices, and identify a class pair where the simpler route visibly suffers.
