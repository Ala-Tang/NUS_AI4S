# Chapter 12 — UMAP — Question Bank

> **The question this chapter answers.** *How would you build a neighbour-preserving map of a very large dataset, and how would you stop it destroying the large-scale arrangement?*
>
> Write an answer here **before you look anything up**. You have the notes already; the point is to find out what you do not know first. Then open them, or ask an LLM, and correct what you wrote — keep both versions. The gap between your attempt and the answer is the part you will remember.

> **No answers are provided.** Sections A and B are prepared by the Friday before the Monday lecture, where they are quizzed in class. Section C is practised between the lecture and the Thursday lab — until you can do each unaided, without AI, on a lab desktop.
> Tiers are set by *composition*: how many distinct concepts a question requires (Section A), or how many functions you must write and connect (Section C). Section B is tiered differently — Easy asks you to state a definition, Medium to prove or state a property of one.
>
> ⚠️ **Environment note:** in the `np_veclib` environment, `import umap` must come *before* `import torch`.
> **Assessed scope.** Sections A and B are quizzed in the **Monday lecture** — conceptual to Medium, mathematical to Easy. Section C is answered in the **Thursday lab** — coding to Medium. That is **19 of this chapter's 30 questions**. The tiers marked *stretch* are quizzed in neither session; attempt them if you finish early, and expect them in the block homework and the final examination.

**Notes:** [[Chapter12]] · [[Chapter12#Learning outcomes|Learning outcomes]] · [[Chapter12#Optional Reading and References|Optional reading]]

## A. Conceptual short-answer

*Where to look: [[Chapter12#Concept overview|Concept overview]] · [[Chapter12#Applications|Applications]]*

### Easy — a single concept

1. Sketch the algorithm as a sequence of stages, one clause per stage.
2. What is the local-connectivity assumption, and which pathology does it fix?
3. Describe the effect of the neighbourhood-size hyperparameter on the embedding.
4. What does negative sampling do?

### Medium — two or three concepts

5. Combining the two hyperparameters: explain which one you would change to tighten clusters visually without altering what counts as a neighbour, and what each controls.
6. Combining UMAP's objective with t-SNE's from Chapter 11: state the structural difference between the two, and the practical consequence of the extra term in UMAP's.
7. Combining the neighbour graph with computational cost: explain why an approximate nearest-neighbour construction is acceptable here, and what would degrade if it were badly wrong.

### Hard — three or more concepts *(stretch — beyond the lab ceiling)*

8. Bring together the fuzzy graph construction, the cross-entropy objective, and the optimisation by negative sampling to explain why UMAP scales roughly linearly in sample size where a naive implementation would not.
9. Using the manifold picture, the local-connectivity assumption, and the curse of dimensionality from Chapter 08, explain why neighbour graphs in high dimension are pathological and what UMAP does about it.
10. Combining dimensionality reduction, clustering from a later chapter, and the caveat that embedded distances are unreliable, describe a defensible workflow for discovering groups in a high-dimensional scientific dataset. State at which step a false discovery is most likely to enter.

## B. Mathematical

*Where to look: [[Chapter12#Key math|Key math]] · [[Chapter12#Concept overview|Concept overview]]*

### Easy — state a definition

1. Define the distance to the nearest neighbour and the high-dimensional edge weight built from it.
2. State the normalisation condition imposed on each point's outgoing weights.
3. Define the fuzzy-set union used to symmetrise the graph.
4. Define the low-dimensional similarity together with its two shape parameters.
5. Write the UMAP objective as a sum over pairs.

### Medium — prove or state a property *(stretch — beyond the lab ceiling)*

6. Show that the nearest neighbour of any point always receives full weight, and explain why this constitutes the local-connectivity guarantee.
7. Verify that the fuzzy union maps the unit square into the unit interval, and evaluate its behaviour when one input is 0 and when one input is 1.
8. Show that a particular choice of the shape parameters recovers the heavy-tailed kernel used by t-SNE.
9. Identify the attractive and repulsive terms of the objective, and show that each edge's contribution is minimised when the two similarities agree.
10. Compare the cost of an exact nearest-neighbour graph against an approximate graph-descent construction as functions of sample size, and state where the difference becomes decisive.

## C. Coding

*Where to look: [[Chapter12#Code examples|Code examples]] · [[Chapter12#Key math|Key math]]*

### Easy — a single function

1. Write a function that embeds a dataset with UMAP at given hyperparameters and returns the coordinates.
2. Write a function that plots a two-dimensional embedding coloured by a label array.
3. Write a function that computes a $k$-nearest-neighbour index for a dataset.
4. Write a function that measures the fraction of each point's original neighbours retained in an embedding.

### Medium — two or three functions

5. Using your embedding and plotting functions, produce a grid sweeping neighbourhood size against minimum distance, and state which hyperparameter controls which visual property.
6. Using a precomputed neighbour graph from your index function, produce embeddings across several neighbourhood sizes and report the time saved against recomputing each time.
7. Combine your embedding function with your neighbourhood-preservation measure to compare UMAP and t-SNE on the same data, reporting both the measure and the wall-clock time of each.

### Hard — three or more functions *(stretch — beyond the lab ceiling)*

8. Build functions to generate data with a known large-scale geometry, to embed it by two methods, and to measure how far each embedding distorts that geometry. Report which method you would trust and under what caveats.
9. Assemble functions for data generation with an isolated outlier, for embedding, and for locating that outlier in the result. Use them to show how the local-connectivity assumption prevents the outlier being pushed arbitrarily far, and report how the behaviour changes with neighbourhood size.
10. Construct a full pipeline of separate functions — reduce with PCA, embed with UMAP, cluster the embedding, and score the clustering against known labels. Then vary the embedding hyperparameters and report how much the final clustering score moves, and what that implies about reporting a single embedding.
