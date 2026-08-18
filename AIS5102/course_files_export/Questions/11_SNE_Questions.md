# Chapter 11 — Stochastic Neighbour Embedding and t-SNE — Question Bank

> **The question this chapter answers.** *You want to see the structure of thousand-dimensional data on a page. What must a two-dimensional picture preserve, and what must it necessarily distort?*
>
> Write an answer here **before you look anything up**. You have the notes already; the point is to find out what you do not know first. Then open them, or ask an LLM, and correct what you wrote — keep both versions. The gap between your attempt and the answer is the part you will remember.

> **No answers are provided.** Sections A and B are prepared by the Friday before the Monday lecture, where they are quizzed in class. Section C is practised between the lecture and the Thursday lab — until you can do each unaided, without AI, on a lab desktop.
> Tiers are set by *composition*: how many distinct concepts a question requires (Section A), or how many functions you must write and connect (Section C). Section B is tiered differently — Easy asks you to state a definition, Medium to prove or state a property of one.
> **Assessed scope.** Sections A and B are quizzed in the **Monday lecture** — conceptual to Medium, mathematical to Easy. Section C is answered in the **Thursday lab** — coding to Medium. That is **19 of this chapter's 30 questions**. The tiers marked *stretch* are quizzed in neither session; attempt them if you finish early, and expect them in the block homework and the final examination.

**Notes:** [[Chapter11]] · [[Chapter11#Learning outcomes|Learning outcomes]] · [[Chapter11#Optional Reading and References|Optional reading]]

## A. Conceptual short-answer

*Where to look: [[Chapter11#Concept overview|Concept overview]] · [[Chapter11#Applications|Applications]]*

### Easy — a single concept

1. What question do neighbour-embedding methods ask that a linear projection does not?
2. Define perplexity and give its intuitive interpretation.
3. What is the crowding problem?
4. Name three features of a t-SNE plot that must not be interpreted scientifically.

### Medium — two or three concepts

5. Combining the per-point bandwidth with local density: explain why the bandwidth must vary from point to point rather than being set globally, and what would go wrong with a single global value.
6. Combining the KL divergence of Chapter 04 with the embedding objective: explain how the divergence's asymmetry makes omitting a true neighbour costlier than adding a false one, and why that is desirable when looking for clusters.
7. Combining PCA from Chapter 08 with t-SNE: explain why initialising the embedding from a linear projection improves the result, and what specifically improves.

### Hard — three or more concepts *(stretch — beyond the lab ceiling)*

8. Bring together the neighbourhood distribution, the heavy-tailed low-dimensional kernel, and the crowding problem to explain mechanically why t-SNE produces tight clusters with visible gaps, and why those gaps carry less information than they appear to.
9. Using entropy from Chapter 03, the perplexity parameter, and the notion of local density, explain how a single hyperparameter can control the effective neighbourhood size across a dataset whose density varies by orders of magnitude.
10. Combining the loss function of Chapter 01, the optimiser choice of Chapter 06, and t-SNE's non-convex objective, explain why two runs of the same embedding code produce different maps, whether this is a defect, and what you would report in a paper as a result.

## B. Mathematical

*Where to look: [[Chapter11#Key math|Key math]] · [[Chapter11#Concept overview|Concept overview]]*

### Easy — state a definition

1. Define the high-dimensional conditional neighbour probability, including the convention for the self-term.
2. Define the symmetrised joint distribution over pairs.
3. Define the low-dimensional Student-$t$ similarity and state its degrees of freedom.
4. Define perplexity in terms of the entropy of a neighbour distribution.
5. Write the t-SNE objective.

### Medium — prove or state a property *(stretch — beyond the lab ceiling)*

6. Explain why the self-term is excluded from the neighbour distribution and why normalisation is per point rather than global.
7. Compare the tail decay of the Student-$t$ kernel against a Gaussian, and state the consequence for how far apart dissimilar points are pushed.
8. Prove that the objective is non-negative, and state the condition for equality.
9. Show that the objective penalises placing true neighbours far apart more heavily than placing distant points close together.
10. Show that the entropy of a neighbour distribution increases with its bandwidth, and use this to justify a one-dimensional search for the bandwidth achieving a target perplexity.

## C. Coding

*Where to look: [[Chapter11#Code examples|Code examples]] · [[Chapter11#Key math|Key math]]*

### Easy — a single function

1. Write a function computing all pairwise squared distances in a dataset without an explicit Python loop.
2. Write a function converting a row of squared distances and a bandwidth into a normalised neighbour distribution.
3. Write a function returning the perplexity of a neighbour distribution.
4. Write a function that embeds a dataset in two dimensions with t-SNE and returns the coordinates.

### Medium — two or three functions

5. Using your distance and neighbour-distribution functions, plus a bisection routine you write, find the bandwidth achieving a target perplexity for several points and report the values found.
6. Write a function that embeds at a given perplexity and one that plots the result, and use them to produce a panel spanning very small to very large perplexity.
7. Write a function measuring neighbourhood preservation between an original dataset and an embedding, and apply it to embeddings at two different perplexities.

### Hard — three or more functions *(stretch — beyond the lab ceiling)*

8. Build the symmetrised high-dimensional distribution from scratch using separate functions for distances, per-point bandwidth search, conditional probabilities, and symmetrisation. Verify the result is correctly normalised.
9. Assemble functions for embedding, for measuring pairwise-distance agreement, and for repeating across seeds, into a study quantifying run-to-run variation at fixed perplexity. Report the measure you chose and what value would worry you.
10. Write functions to generate clusters with prescribed spreads, to embed them, and to measure the on-screen spread of each cluster. Use them to show that embedded cluster sizes do not track true spreads, and state the incorrect conclusion the plot invites.
