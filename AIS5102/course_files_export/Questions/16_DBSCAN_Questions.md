# Chapter 16 — DBSCAN — Question Bank

> **The question this chapter answers.** *Some of your measurements form groups of irregular shape, you do not know how many, and some points belong to no group at all. How would you find the groups?*
>
> Write an answer here **before you look anything up**. You have the notes already; the point is to find out what you do not know first. Then open them, or ask an LLM, and correct what you wrote — keep both versions. The gap between your attempt and the answer is the part you will remember.

> **No answers are provided.** Sections A and B are prepared by the Friday before the Monday lecture, where they are quizzed in class. Section C is practised between the lecture and the Thursday lab — until you can do each unaided, without AI, on a lab desktop.
> Tiers are set by *composition*: how many distinct concepts a question requires (Section A), or how many functions you must write and connect (Section C). Section B is tiered differently — Easy asks you to state a definition, Medium to prove or state a property of one.
> **Assessed scope.** Sections A and B are quizzed in the **Monday lecture** — conceptual to Medium, mathematical to Easy. Section C is answered in the **Thursday lab** — coding to Medium. That is **19 of this chapter's 30 questions**. The tiers marked *stretch* are quizzed in neither session; attempt them if you finish early, and expect them in the block homework and the final examination.

**Notes:** [[Chapter16]] · [[Chapter16#Learning outcomes|Learning outcomes]] · [[Chapter16#Optional Reading and References|Optional reading]]

## A. Conceptual short-answer

*Where to look: [[Chapter16#Concept overview|Concept overview]] · [[Chapter16#Applications|Applications]]*

### Easy — a single concept

1. Define core, border, and noise points in terms of the two hyperparameters.
2. What is density-reachability, and why must intermediate points in a chain be core?
3. What is the principal failure mode of a single global density threshold?
4. How do you read a radius off a sorted nearest-neighbour distance curve?

### Medium — two or three concepts

5. Combining density-based clustering with centroid-based clustering from Chapter 14: name two capabilities the density approach has that the centroid approach lacks, and give a dataset where each is decisive.
6. Combining the noise label with scientific reporting: explain why an explicit "no cluster" output is valuable, and what the risk is of tuning the radius until no noise remains.
7. Combining the neighbourhood radius with the curse of dimensionality from Chapter 08: explain why density-based clustering degrades in high dimension, identifying which geometric property fails.

### Hard — three or more concepts *(stretch — beyond the lab ceiling)*

8. Bring together the core-point condition, the reachability chain, and the equivalence-class construction to explain how clusters of arbitrary shape emerge from a purely local rule.
9. Using the two hyperparameters, the density they jointly imply, and the notion of variable density, explain why no single parameter pair can resolve two clusters whose densities differ by a large factor. State what you would do instead.
10. Combining dimensionality reduction from Chapters 08 and 12, density-based clustering, and the caveat that embedded distances are distorted, explain the risk in the common workflow of embedding first and clustering the embedding. Describe how you would check that the clusters are not artefacts of the embedding.

## B. Mathematical

*Where to look: [[Chapter16#Key math|Key math]] · [[Chapter16#Concept overview|Concept overview]]*

### Easy — state a definition

1. Define the $\epsilon$-neighbourhood of a point.
2. Define core, border, and noise points in terms of the two hyperparameters.
3. Define directly density-reachable and density-reachable.
4. Define density-connected, and state how a cluster is read off from it.
5. Define the $k$-distance of a point.

### Medium — prove or state a property *(stretch — beyond the lab ceiling)*

6. Write the reachability relation as a chain condition and explain precisely why it is not symmetric.
7. Prove that density-connectivity is an equivalence relation on the set of core points, verifying each required property.
8. For a uniform density in $D$ dimensions, compute the expected number of points within a fixed radius, and derive how the radius must scale with dimension to hold that count constant.
9. Given a small one-dimensional dataset and both hyperparameters, classify every point as core, border, or noise and list the resulting clusters. Then change one hyperparameter and report what changes.
10. For two clusters whose densities differ by a large factor, write the two inequalities a single radius would have to satisfy simultaneously, and show they are incompatible.

## C. Coding

*Where to look: [[Chapter16#Code examples|Code examples]] · [[Chapter16#Key math|Key math]]*

### Easy — a single function

1. Write a function returning the indices of all points within a given radius of a query point.
2. Write a function that labels each point core, border, or noise given a radius and a minimum count.
3. Write a function returning the sorted $k$-th nearest-neighbour distances for a dataset.
4. Write a function that scores a clustering against known labels using an appropriate agreement measure.

### Medium — two or three functions

5. Using your neighbourhood and core-labelling functions, expand a single cluster by breadth-first traversal from one core point and return its members.
6. Using your $k$-distance function, plot the curve, identify the knee, and pass the value to a library clusterer, reporting the clusters found.
7. Write a function sweeping one hyperparameter and returning cluster and noise counts, and use it with your scoring function to report which setting best matches known labels.

### Hard — three or more functions *(stretch — beyond the lab ceiling)*

8. Assemble your neighbourhood, core-labelling, and expansion functions into a complete from-scratch implementation. Verify its labels against a library version and report any points where they differ.
9. Build functions to generate data with clusters at different densities, to cluster it across a grid of both hyperparameters, and to score each result. Report the best achievable agreement and show that no single setting recovers all clusters.
10. Write functions to generate separated clusters in a chosen dimension, to search for the best radius, and to record both the best score and the width of the radius range achieving near-best performance. Sweep the dimension and report how that usable range narrows, with a comment on what this means for practice.
