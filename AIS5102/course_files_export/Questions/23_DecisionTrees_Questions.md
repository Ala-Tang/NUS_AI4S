# Chapter 23 — Decision Trees (CART) — Question Bank

> **The question this chapter answers.** *You want a model a domain expert can read and argue with. What would it look like, and what does the readability cost?*
>
> Write an answer here **before you look anything up**. You have the notes already; the point is to find out what you do not know first. Then open them, or ask an LLM, and correct what you wrote — keep both versions. The gap between your attempt and the answer is the part you will remember.

> **No answers are provided.** Sections A and B are prepared by the Friday before the Monday lecture, where they are quizzed in class. Section C is practised between the lecture and the Thursday lab — until you can do each unaided, without AI, on a lab desktop.
> Tiers are set by *composition*: how many distinct concepts a question requires (Section A), or how many functions you must write and connect (Section C). Section B is tiered differently — Easy asks you to state a definition, Medium to prove or state a property of one.
> **Assessed scope.** Sections A and B are quizzed in the **Monday lecture** — conceptual to Medium, mathematical to Easy. Section C is answered in the **Thursday lab** — coding to Medium. That is **19 of this chapter's 30 questions**. The tiers marked *stretch* are quizzed in neither session; attempt them if you finish early, and expect them in the block homework and the final examination.

**Notes:** [[Chapter23]] · [[Chapter23#Learning outcomes|Learning outcomes]] · [[Chapter23#Optional Reading and References|Optional reading]]

## A. Conceptual short-answer

*Where to look: [[Chapter23#Concept overview|Concept overview]] · [[Chapter23#Applications|Applications]]*

### Easy — a single concept

1. Describe the partition of feature space a tree induces, and what is predicted inside each region.
2. Name the common impurity measures.
3. What does "greedy" mean in tree training, and what is given up?
4. Name three structurally different mechanisms for controlling tree overfitting.

### Medium — two or three concepts

5. Combining impurity with the shape of the impurity function: explain why the smooth measures are preferred to counting misclassifications, referring to concavity.
6. Combining entropy from Chapter 03 with the splitting rule: explain what information gain measures, and why the same quantity that describes a distribution's uncertainty also chooses a split.
7. Combining a regression tree with vector quantisation from Chapter 15: explain in what sense they are the same object, identifying what plays the role of the codebook.

### Hard — three or more concepts *(stretch — beyond the lab ceiling)*

8. Bring together the greedy search, impurity gain, and the stopping rules to explain why a tree overfits and how each control mechanism intervenes at a different point in that process.
9. Using feature scaling from Chapter 09, the axis-aligned splitting rule, and mixed data types, explain why trees need no preprocessing where linear models do. State what trees give up in exchange.
10. Combining impurity-based importance, the greedy search, and validation from Chapter 22, explain how a feature can rank high on impurity-based importance while carrying no predictive signal. Describe the procedure you would use to establish that a feature genuinely carries signal.

## B. Mathematical

*Where to look: [[Chapter23#Key math|Key math]] · [[Chapter23#Concept overview|Concept overview]]*

### Easy — state a definition

1. Define the Gini, entropy, and misclassification impurities for a node with given class proportions.
2. Define the impurity gain of a split.
3. Write the best-split objective over feature–threshold pairs.
4. Write the regression-tree objective and define the leaf value.
5. Write the cost-complexity objective, defining the leaf count and the penalty parameter.

### Medium — prove or state a property *(stretch — beyond the lab ceiling)*

6. Evaluate all three impurity measures at a pure node, a maximally impure node, and an intermediate case, and tabulate the results.
7. Prove the impurity gain is non-negative for the concave measures, invoking Jensen's inequality.
8. Construct a binary example where counting misclassifications gives zero gain but a smooth impurity gives positive gain, and explain what this means for tree growth.
9. Show that the optimal value at a leaf of a regression tree is the mean of the labels it contains.
10. Describe the sequence of trees produced as the cost-complexity penalty grows from zero to infinity, and identify both endpoints.

## C. Coding

*Where to look: [[Chapter23#Code examples|Code examples]] · [[Chapter23#Key math|Key math]]*

### Easy — a single function

1. Write a function computing an impurity measure from a label array.
2. Write a function that splits a dataset on a given feature and threshold, returning both halves.
3. Write a function computing the weighted child impurity of a proposed split.
4. Write a function returning the impurity-based feature importances of a fitted tree.

### Medium — two or three functions

5. Combine your split and impurity functions into a best-split finder that searches all feature–threshold pairs, and verify it reproduces the root split chosen by a library implementation.
6. Write a function that plots impurity against class proportion for a binary node, using your impurity function, and overlay all three measures on one axis.
7. Write a function fitting a tree at a given complexity setting and one that scores it, and use them to sweep a complexity hyperparameter and identify where overfitting begins.

### Hard — three or more functions *(stretch — beyond the lab ceiling)*

8. Assemble your split, impurity, and best-split functions into a recursive tree-growing routine with a depth limit, plus a prediction function. Verify its accuracy against a library implementation on the same data.
9. Build functions for cost-complexity pruning, for cross-validated scoring, and for counting leaves. Use them to select a penalty, and report both the chosen value and the resulting tree size.
10. Write functions to generate data whose signal lies in one low-cardinality feature alongside an uninformative high-cardinality feature, to fit a deep tree, and to compute importance by both an impurity-based and a permutation-based method. Report how the ranking differs and which you would trust.
