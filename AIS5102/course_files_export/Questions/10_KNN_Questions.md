# Chapter 10 — Distance Metrics and Nearest Neighbours — Question Bank

> **The question this chapter answers.** *What does it mean for two measurements to be close, and does that still mean anything when each one has a thousand numbers in it?*
>
> Write an answer here **before you look anything up**. You have the notes already; the point is to find out what you do not know first. Then open them, or ask an LLM, and correct what you wrote — keep both versions. The gap between your attempt and the answer is the part you will remember.

> **No answers are provided.** Sections A and B are prepared by the Friday before the Monday lecture, where they are quizzed in class. Section C is practised between the lecture and the Thursday lab — until you can do each unaided, without AI, on a lab desktop.
> Tiers are set by *composition*: how many distinct concepts a question requires (Section A), or how many functions you must write and connect (Section C). Section B is tiered differently — Easy asks you to state a definition, Medium to prove or state a property of one.
> **Assessed scope.** Sections A and B are quizzed in the **Monday lecture** — conceptual to Medium, mathematical to Easy. Section C is answered in the **Thursday lab** — coding to Medium. That is **19 of this chapter's 30 questions**. The tiers marked *stretch* are quizzed in neither session; attempt them if you finish early, and expect them in the block homework and the final examination.

**Notes:** [[Chapter10]] · [[Chapter10#Learning outcomes|Learning outcomes]] · [[Chapter10#Optional Reading and References|Optional reading]]

## A. Conceptual short-answer

*Where to look: [[Chapter10#Concept overview|Concept overview]] · [[Chapter10#Applications|Applications]]*

### Easy — a single concept

1. State what cosine similarity is invariant to, and what Euclidean distance is not.
2. What is a $k$-nearest-neighbour graph, and why is it directed rather than symmetric?
3. How does $k$ control the flexibility of a nearest-neighbour predictor?
4. State what distance concentration is and what it does to the meaning of "nearest".

### Medium — two or three concepts

5. Combining the metric choice with preprocessing from Chapter 09: explain why standardising and then using Euclidean distance is itself a choice of metric, and name a case where it is the wrong one.
6. Combining $k$ with the bias–variance idea: describe the predictor at $k=1$ and at $k=N$, and say which error component dominates at each extreme.
7. Combining the neighbour graph with two later methods: name two chapters whose algorithms consume this graph, and state what each takes from it.

### Hard — three or more concepts *(stretch — beyond the lab ceiling)*

8. Bring together distance concentration, the volume of a high-dimensional ball, and the neighbourhood radius to explain why density-based reasoning degrades in high dimension, and what the course does about it.
9. Using the metric, the neighbour graph, and the notion of a hub point, explain how a high-dimensional pathology in the graph can propagate into an embedding or a clustering built on top of it.
10. Combining exact search, tree-based search, and approximate search with the accuracy requirements of a downstream method, explain why approximate neighbours are acceptable for a visualisation but might not be for a nearest-neighbour classifier used to make a decision.

## B. Mathematical

*Where to look: [[Chapter10#Key math|Key math]] · [[Chapter10#Concept overview|Concept overview]]*

### Easy — state a definition

1. Write the Minkowski distance and identify the values of $p$ giving the Manhattan, Euclidean, and Chebyshev distances.
2. Write cosine similarity and the distance derived from it.
3. Write the Mahalanobis distance, defining every symbol.
4. State the four metric axioms.
5. Write the $k$-nearest-neighbour prediction rules for regression and for classification.

### Medium — prove or state a property *(stretch — beyond the lab ceiling)*

6. Determine whether cosine distance satisfies the triangle inequality — prove it or give an explicit counterexample.
7. Show that Mahalanobis distance is Euclidean distance computed after whitening, and deduce what linear transformations it is invariant to.
8. Show that for vectors normalised to unit length, squared Euclidean distance is an affine function of cosine similarity, and state the consequence for neighbour rankings.
9. For a uniform distribution in a $D$-dimensional ball, derive the fraction of volume lying within the outer shell of relative thickness $\varepsilon$, and evaluate the limit as $D$ grows.
10. State the distance-concentration result as a limit of the ratio between farthest and nearest distances, and explain what assumption on the features it requires.

## C. Coding

*Where to look: [[Chapter10#Code examples|Code examples]] · [[Chapter10#Key math|Key math]]*

### Easy — a single function

1. Write a function that computes all pairwise distances in a dataset under a chosen metric, without an explicit Python loop.
2. Write a function that returns the indices of the $k$ nearest neighbours of every point.
3. Write a function implementing $k$-nearest-neighbour classification by majority vote.
4. Write a function that returns the ratio of the largest to smallest distance from a query point to a set of points.

### Medium — two or three functions

5. Using your neighbour function under two different metrics, write a third that reports the mean overlap between the two neighbour lists.
6. Using your classifier and a scoring function, report train and test accuracy across a wide range of $k$ and identify where each error component dominates.
7. Write a function that builds a symmetrised neighbour graph and one that reports its degree distribution, and use them to detect hub points.

### Hard — three or more functions *(stretch — beyond the lab ceiling)*

8. Build functions to generate data in a chosen dimension, to measure the distance contrast from a query point, and to summarise across many queries. Use them to plot contrast against dimension and identify where nearest-neighbour reasoning fails.
9. Assemble functions for exact and approximate neighbour search plus a timing harness and an agreement measure. Report both the speed-up and the fraction of neighbours the approximate method gets right, across increasing sample size.
10. Write functions to scale data, to find neighbours, and to score a nearest-neighbour classifier. Use them to show how much accuracy depends on the preprocessing choice, and report the metric-and-scaling combination you would adopt for the dataset.
