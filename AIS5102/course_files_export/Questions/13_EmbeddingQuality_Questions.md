# Chapter 13 — Embedding Quality and Trustworthiness — Question Bank

> **The question this chapter answers.** *Two clusters look separated on your map. How would you check whether that separation is real?*
>
> Write an answer here **before you look anything up**. You have the notes already; the point is to find out what you do not know first. Then open them, or ask an LLM, and correct what you wrote — keep both versions. The gap between your attempt and the answer is the part you will remember.

> **No answers are provided.** Sections A and B are prepared by the Friday before the Monday lecture, where they are quizzed in class. Section C is practised between the lecture and the Thursday lab — until you can do each unaided, without AI, on a lab desktop.
> Tiers are set by *composition*: how many distinct concepts a question requires (Section A), or how many functions you must write and connect (Section C). Section B is tiered differently — Easy asks you to state a definition, Medium to prove or state a property of one.
> **Assessed scope.** Sections A and B are quizzed in the **Monday lecture** — conceptual to Medium, mathematical to Easy. Section C is answered in the **Thursday lab** — coding to Medium. That is **19 of this chapter's 30 questions**. The tiers marked *stretch* are quizzed in neither session; attempt them if you finish early, and expect them in the block homework and the final examination.

**Notes:** [[Chapter13]] · [[Chapter13#Learning outcomes|Learning outcomes]] · [[Chapter13#Optional Reading and References|Optional reading]]

## A. Conceptual short-answer

*Where to look: [[Chapter13#Concept overview|Concept overview]] · [[Chapter13#Applications|Applications]]*

### Easy — a single concept

1. Distinguish a false neighbour from a missed neighbour in an embedding.
2. What does trustworthiness penalise, and what does continuity penalise?
3. What does a Shepard diagram plot, and what does a tight monotone band indicate?
4. Why can two embeddings of the same data not be compared by their raw coordinates?

### Medium — two or three concepts

5. Combining trustworthiness with continuity: state which error each of the two measures penalises, and say which error is more damaging in a published figure.
6. Combining neighbourhood preservation with the neighbourhood size $k$: explain how sweeping $k$ turns a single number into a local-to-global profile, and what a method that scores well at small $k$ but poorly at large $k$ is doing.
7. Combining rank correlation with the objectives of Chapters 11 and 12: explain why a rank-based measure is the appropriate summary for neighbour-embedding methods rather than a linear correlation of distances.

### Hard — three or more concepts *(stretch — beyond the lab ceiling)*

8. Bring together local quality, global quality, and the caveats of Chapter 11 to explain how an embedding can be simultaneously trustworthy and misleading about the relationship between two clusters.
9. Using the quality measures, the stochastic initialisation of the embedding algorithms, and Procrustes alignment, describe how you would establish that a published embedding is reproducible. State what number you would report.
10. Combining preprocessing from Chapter 09, embedding quality, and the notion of scientific validity, explain how an embedding can score perfectly on trustworthiness and still support no valid conclusion. Describe the external check that would settle the matter.

## B. Mathematical

*Where to look: [[Chapter13#Key math|Key math]] · [[Chapter13#Concept overview|Concept overview]]*

### Easy — state a definition

1. Define the rank of a point among the neighbours of another point, in the original space and in the embedding.
2. Write the trustworthiness measure, defining the set summed over.
3. Write the continuity measure and state how it differs from trustworthiness.
4. Define neighbourhood preservation at $k$.
5. Write the metric MDS stress and the Procrustes disparity.

### Medium — prove or state a property *(stretch — beyond the lab ceiling)*

6. Show that both trustworthiness and continuity lie in the unit interval, and state which configuration attains the maximum.
7. Show that continuity is obtained from trustworthiness by exchanging the roles of the two spaces, and explain why this makes them a complementary pair rather than two measures of the same thing.
8. Show that neighbourhood preservation at $k=N-1$ is identically 1 for any embedding, and explain what this implies about choosing $k$.
9. Show that the Procrustes disparity is invariant to rotation, reflection, translation, and uniform scaling of either configuration, and derive the optimal rotation from a singular value decomposition.
10. Show that a rank correlation between the two distance sets is unchanged by any strictly monotone transformation of either, and state why this property is desirable here.

## C. Coding

*Where to look: [[Chapter13#Code examples|Code examples]] · [[Chapter13#Key math|Key math]]*

### Easy — a single function

1. Write a function that returns the $k$ nearest neighbours of every point in a dataset.
2. Write a function computing neighbourhood preservation at $k$ between an original dataset and an embedding.
3. Write a function returning the vector of all pairwise distances in a dataset.
4. Write a function that computes the rank correlation between two vectors of pairwise distances.

### Medium — two or three functions

5. Using your neighbour and preservation functions, produce a curve of neighbourhood preservation against $k$ for one embedding, and describe the profile.
6. Using your pairwise-distance function, produce a Shepard diagram and annotate it with the rank correlation from your correlation function.
7. Write a function computing continuity from a trustworthiness routine by exchanging its arguments, and report both measures for the same embedding.

### Hard — three or more functions *(stretch — beyond the lab ceiling)*

8. Build functions to embed a dataset by three different methods, to compute a panel of quality measures, and to assemble the results into a comparison table. Report which method you would choose for this dataset and on what evidence.
9. Assemble functions for repeated embedding across random seeds, for Procrustes alignment, and for summarising the disparities. Report a reproducibility number for the method and state what value would concern you.
10. Write functions to generate data with a known cluster geometry, to embed it, and to measure separately the preservation of local neighbourhoods and of the inter-cluster arrangement. Use them to construct a case that scores well locally and badly globally, and state the incorrect conclusion a reader would draw.
