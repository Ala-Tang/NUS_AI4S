# Chapter 17 — HDBSCAN — Question Bank

> **The question this chapter answers.** *Your data is dense in some regions and sparse in others. How would you find groups without committing to a single definition of “dense”?*
>
> Write an answer here **before you look anything up**. You have the notes already; the point is to find out what you do not know first. Then open them, or ask an LLM, and correct what you wrote — keep both versions. The gap between your attempt and the answer is the part you will remember.

> **No answers are provided.** Sections A and B are prepared by the Friday before the Monday lecture, where they are quizzed in class. Section C is practised between the lecture and the Thursday lab — until you can do each unaided, without AI, on a lab desktop.
> Tiers are set by *composition*: how many distinct concepts a question requires (Section A), or how many functions you must write and connect (Section C). Section B is tiered differently — Easy asks you to state a definition, Medium to prove or state a property of one.
> **Assessed scope.** Sections A and B are quizzed in the **Monday lecture** — conceptual to Medium, mathematical to Easy. Section C is answered in the **Thursday lab** — coding to Medium. That is **19 of this chapter's 30 questions**. The tiers marked *stretch* are quizzed in neither session; attempt them if you finish early, and expect them in the block homework and the final examination.

**Notes:** [[Chapter17]] · [[Chapter17#Learning outcomes|Learning outcomes]] · [[Chapter17#Optional Reading and References|Optional reading]]

## A. Conceptual short-answer

*Where to look: [[Chapter17#Concept overview|Concept overview]] · [[Chapter17#Applications|Applications]]*

### Easy — a single concept

1. Define the core distance and say what a large value tells you about a point.
2. Define the mutual reachability distance and describe what it does to sparse regions.
3. What is cluster stability, and what kind of cluster earns a high score?
4. What does a high outlier score mean, and how does it differ from simply being labelled noise?

### Medium — two or three concepts

5. Combining the mutual reachability distance with the minimum spanning tree: explain why the tree is the right object to build, and what an edge weight represents.
6. Combining the two principal hyperparameters: state which controls the smoothness of the density estimate and which controls what may count as a cluster, and describe the effect of increasing each.
7. Combining the condensation step with the notion of a cluster hierarchy: explain why splitting off a small branch is recorded as the parent losing points rather than as a genuine split.

### Hard — three or more concepts *(stretch — beyond the lab ceiling)*

8. Bring together the single-threshold failure of Chapter 16, the density hierarchy, and stability-based extraction to explain how examining all density levels at once resolves the variable-density problem.
9. Using stability, the antichain constraint, and the notion of model selection, explain why stability is a more defensible criterion for choosing clusters than cluster count or size — and what it can still get wrong.
10. Combining outlier scores, the cluster hierarchy, and the scientific practice of anomaly detection, describe how you would use this method to flag suspect measurements in a dataset with no labels. State what evidence would convince you a flagged point is genuinely anomalous rather than merely rare.

## B. Mathematical

*Where to look: [[Chapter17#Key math|Key math]] · [[Chapter17#Concept overview|Concept overview]]*

### Easy — state a definition

1. Define the core distance of a point with respect to a neighbour count.
2. Define the mutual reachability distance.
3. Define the density level $\lambda$ and state its relationship to the neighbourhood radius.
4. Define the stability, or excess of mass, of a cluster.
5. Define an antichain in the cluster hierarchy.

### Medium — prove or state a property *(stretch — beyond the lab ceiling)*

6. Prove that the mutual reachability distance is never smaller than the underlying metric distance, and state the condition under which they are equal.
7. Show that the mutual reachability distance is symmetric, then determine whether it satisfies the triangle inequality — prove it or give a counterexample.
8. Examine the stability functional term by term and explain why it rewards clusters that persist across a wide range of densities.
9. Explain why the extracted clusters must form an antichain, and describe what an invalid selection would mean.
10. Given a small one-dimensional dataset and a neighbour count, compute the core distance for every point, then the mutual reachability distance for several pairs, identifying which was inflated most.

## C. Coding

*Where to look: [[Chapter17#Code examples|Code examples]] · [[Chapter17#Key math|Key math]]*

### Easy — a single function

1. Write a function returning the core distance of every point for a given neighbour count.
2. Write a function returning the full mutual reachability distance matrix given core distances and pairwise distances.
3. Write a function that fits a hierarchical density-based clusterer and returns labels, membership probabilities, and outlier scores.
4. Write a function that flags the top quantile of points by outlier score.

### Medium — two or three functions

5. Using your core-distance and mutual-reachability functions, construct the minimum spanning tree of the transformed distances and return its edges.
6. Write a function generating data with clusters at two clearly different densities plus noise, and use it with your fitting function to report the labels found.
7. Combine your fitting and flagging functions with a plotting routine to display the data coloured by membership probability, with flagged outliers marked distinctly.

### Hard — three or more functions *(stretch — beyond the lab ceiling)*

8. Assemble your core-distance, mutual-reachability, and spanning-tree functions into a from-scratch pipeline, and compare the distribution of transformed edge weights against that of a tree built on plain distances. Explain what the difference implies about where the algorithm cuts.
9. Build functions to generate variable-density data, to cluster it with both a single-threshold and a hierarchical method, and to score both against ground truth. Report the gap and identify which clusters the single-threshold method loses.
10. Write functions to sweep each hyperparameter, to record cluster and noise counts, and to score against known labels. Use them to produce a two-dimensional sensitivity map over both hyperparameters, and state the region you would recommend as a default with your reasoning.
