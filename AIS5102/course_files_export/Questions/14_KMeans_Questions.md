# Chapter 14 — K-Means Clustering — Question Bank

> **The question this chapter answers.** *You think your measurements fall into a few groups. How would you find them without being told what they are?*
>
> Write an answer here **before you look anything up**. You have the notes already; the point is to find out what you do not know first. Then open them, or ask an LLM, and correct what you wrote — keep both versions. The gap between your attempt and the answer is the part you will remember.

> **No answers are provided.** Sections A and B are prepared by the Friday before the Monday lecture, where they are quizzed in class. Section C is practised between the lecture and the Thursday lab — until you can do each unaided, without AI, on a lab desktop.
> Tiers are set by *composition*: how many distinct concepts a question requires (Section A), or how many functions you must write and connect (Section C). Section B is tiered differently — Easy asks you to state a definition, Medium to prove or state a property of one.
> **Assessed scope.** Sections A and B are quizzed in the **Monday lecture** — conceptual to Medium, mathematical to Easy. Section C is answered in the **Thursday lab** — coding to Medium. That is **19 of this chapter's 30 questions**. The tiers marked *stretch* are quizzed in neither session; attempt them if you finish early, and expect them in the block homework and the final examination.

**Notes:** [[Chapter14]] · [[Chapter14#Learning outcomes|Learning outcomes]] · [[Chapter14#Optional Reading and References|Optional reading]]

## A. Conceptual short-answer

*Where to look: [[Chapter14#Concept overview|Concept overview]] · [[Chapter14#Applications|Applications]]*

### Easy — a single concept

1. State the K-means objective in words and describe the two alternating steps.
2. Why does the algorithm converge but not necessarily to the best solution?
3. Name the assumptions K-means makes about cluster geometry.
4. Describe the elbow heuristic for choosing the number of clusters.

### Medium — two or three concepts

5. Combining the objective with initialisation: explain what a distance-proportional seeding scheme achieves, and what it costs relative to uniform random seeding.
6. Combining the geometry assumptions with a dataset that violates them: pick one assumption, describe a violating dataset, and say what the fitted clustering does instead of the right answer.
7. Combining the elbow heuristic with the monotonicity of the objective: explain why the objective alone cannot select the number of clusters, and what the elbow is actually detecting.

### Hard — three or more concepts *(stretch — beyond the lab ceiling)*

8. Bring together the objective, the alternating updates, and the convergence argument to explain why each iteration cannot increase the objective and why this implies termination in finitely many steps.
9. Using cluster geometry, cluster population, and the squared-distance objective together, explain why a small cluster adjacent to a large one is often absorbed. State what you would compute to detect that this had happened.
10. Combining the loss-minimisation view of Chapter 01, the optimisation landscape of Chapter 06, and K-means's non-convexity, explain why restarts are standard practice here but not for linear regression. Describe how you would report a clustering result honestly given this.

## B. Mathematical

*Where to look: [[Chapter14#Key math|Key math]] · [[Chapter14#Concept overview|Concept overview]]*

### Easy — state a definition

1. Write the K-means objective with explicit assignment variables, and state the constraints those variables satisfy.
2. Define a centroid.
3. Write the assignment rule and the centroid update rule.
4. Define the within-cluster sum of squares as a function of the number of clusters.
5. Write the sampling probability used by distance-proportional seeding.

### Medium — prove or state a property *(stretch — beyond the lab ceiling)*

6. Derive the optimal assignment rule with the centroids held fixed.
7. Derive the centroid update by differentiating the objective with the assignments held fixed, showing it returns the cluster mean.
8. Prove that a full iteration cannot increase the objective, and use the finiteness of the assignment space to argue convergence in finitely many steps.
9. Prove that the objective is non-increasing in the number of clusters, and state what this implies about choosing the number of clusters by minimising the objective.
10. For two clusters of equal spread but very unequal population, show the objective is dominated by the larger, and describe the consequence for the fitted boundary.

## C. Coding

*Where to look: [[Chapter14#Code examples|Code examples]] · [[Chapter14#Key math|Key math]]*

### Easy — a single function

1. Write a function that assigns each point to its nearest centroid and returns the labels.
2. Write a function that updates centroids given data and assignments.
3. Write a function that computes the clustering objective given data, labels, and centroids.
4. Write a function implementing distance-proportional seeding for a given number of clusters.

### Medium — two or three functions

5. Combine your assignment and update functions into a full alternating loop, and verify the labels agree with a library implementation up to a permutation.
6. Using your objective function inside a loop over the number of clusters, produce an elbow curve and select a value, justifying the choice.
7. Write a function implementing an automatic elbow criterion and compare its selection against your visual choice from the previous question.

### Hard — three or more functions *(stretch — beyond the lab ceiling)*

8. Assemble your seeding, assignment, update, and objective functions into a complete from-scratch implementation that records the objective at each iteration. Plot the trace and confirm it never increases.
9. Build functions to generate data violating a chosen geometric assumption, to cluster it, and to score the result against ground truth. Use them to quantify the failure, then apply an alternative method from a later chapter and compare the scores.
10. Write functions for repeated restarts, for objective evaluation, and for comparing labellings. Use them to report how the final objective is distributed across many random initialisations, how often the best solution is found, and what number of restarts you would recommend as a default.
