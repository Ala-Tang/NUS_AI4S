# Chapter 20 — Cluster Validation — Question Bank

> **The question this chapter answers.** *Two clustering methods give different answers on the same data. Which is right, and how would you tell?*
>
> Write an answer here **before you look anything up**. You have the notes already; the point is to find out what you do not know first. Then open them, or ask an LLM, and correct what you wrote — keep both versions. The gap between your attempt and the answer is the part you will remember.

> **No answers are provided.** Sections A and B are prepared by the Friday before the Monday lecture, where they are quizzed in class. Section C is practised between the lecture and the Thursday lab — until you can do each unaided, without AI, on a lab desktop.
> Tiers are set by *composition*: how many distinct concepts a question requires (Section A), or how many functions you must write and connect (Section C). Section B is tiered differently — Easy asks you to state a definition, Medium to prove or state a property of one.
> **Assessed scope.** Sections A and B are quizzed in the **Monday lecture** — conceptual to Medium, mathematical to Easy. Section C is answered in the **Thursday lab** — coding to Medium. That is **19 of this chapter's 30 questions**. The tiers marked *stretch* are quizzed in neither session; attempt them if you finish early, and expect them in the block homework and the final examination.

**Notes:** [[Chapter20]] · [[Chapter20#Learning outcomes|Learning outcomes]] · [[Chapter20#Optional Reading and References|Optional reading]]

## A. Conceptual short-answer

*Where to look: [[Chapter20#Concept overview|Concept overview]] · [[Chapter20#Applications|Applications]]*

### Easy — a single concept

1. Distinguish internal, external, and relative validation by what each one requires you to already have.
2. What does a silhouette value near zero indicate about a point?
3. Why is a raw agreement score between two labellings inadequate, and what does the adjustment correct for?
4. What does cluster stability measure, and how is it estimated?

### Medium — two or three concepts

5. Combining the silhouette coefficient with the cluster geometry of Chapter 14: identify the cluster shape silhouette implicitly rewards, and give a clustering that is correct yet scores badly.
6. Combining mutual information from Chapter 04 with cluster comparison: explain why raw mutual information between two labellings must be normalised, and what quantity the normalisation removes.
7. Combining information criteria with the likelihood of Chapter 19: explain why a model-based method admits a selection criterion that density-based methods do not, and what replaces it for them.

### Hard — three or more concepts *(stretch — beyond the lab ceiling)*

8. Bring together internal indices, their built-in geometric assumptions, and the practice of choosing the cluster count by maximising one to explain why that procedure can be circular. Describe a defensible alternative.
9. Combining cluster validation with the conditions under which the measurements were acquired, describe how you would test whether a partition reflects the samples or the instrument. Name the statistic you would use and the result that would make you discard the clustering.
10. Combining dimensionality reduction from Chapters 08 to 12, clustering, and validation, explain where in that pipeline a spurious cluster is most likely to be created, and design a check that would catch it before publication.

## B. Mathematical

*Where to look: [[Chapter20#Key math|Key math]] · [[Chapter20#Concept overview|Concept overview]]*

### Easy — state a definition

1. Write the silhouette coefficient of a point, defining the two mean distances it compares.
2. Write the Davies–Bouldin index, defining each symbol.
3. Write the Calinski–Harabasz index in terms of between- and within-cluster dispersion.
4. Write the normalised mutual information between two labellings.
5. Write the AIC and BIC of a fitted model, defining the parameter count.

### Medium — prove or state a property *(stretch — beyond the lab ceiling)*

6. Show that the silhouette coefficient lies in $[-1,1]$, and state the configuration attaining each extreme.
7. Starting from the contingency table of two labellings, derive the expected value of the Rand index under a random model with fixed margins, and show that the adjusted index has expectation zero.
8. Show that raw mutual information between a labelling and a refinement of it never decreases, and use this to explain why an unnormalised criterion rewards more clusters.
9. Compare the penalty terms of AIC and BIC as functions of the sample size, and show that BIC selects a model no larger than AIC's once the sample exceeds a threshold you should state.
10. Show that homogeneity and completeness are conditional-entropy ratios, and that their harmonic mean is bounded by both.

## C. Coding

*Where to look: [[Chapter20#Code examples|Code examples]] · [[Chapter20#Key math|Key math]]*

### Easy — a single function

1. Write a function computing the silhouette coefficient of every point given data and labels.
2. Write a function returning the contingency table between two labellings.
3. Write a function computing an external agreement index between a clustering and known labels.
4. Write a function computing an information criterion from a model's log-likelihood, parameter count, and sample size.

### Medium — two or three functions

5. Using your silhouette function, write a second that reports the mean silhouette per cluster and the fraction of negative values in each, and interpret a case where the overall average conceals one bad cluster.
6. Write a function that measures the association between a clustering and each column of a table of recording conditions, and use it to report which condition best explains the partition.
7. Write a function that clusters at a given count and one that evaluates several internal indices, and use them to tabulate all indices across a range of cluster counts.

### Hard — three or more functions *(stretch — beyond the lab ceiling)*

8. Build functions to generate random labellings, to compute both an uncorrected and a corrected agreement index, and to sweep the number of clusters. Use them to show that only the corrected index stays near zero.
9. Assemble functions for bootstrap resampling, clustering, and co-association accumulation into a stability analysis. Report which cluster count is most stable and how that compares with the count preferred by an internal index.
10. Write functions to generate non-convex clusters, to cluster them by a centroid-based and a density-based method, and to score both by an internal index and against ground truth. Report the case where the internal index prefers the wrong answer, and state what you would report instead.
