# Chapter 15 — Vector Quantisation for Segmentation — Question Bank

> **The question this chapter answers.** *You want to replace every measurement with one of a small set of representatives. How many do you need, and what do you lose?*
>
> Write an answer here **before you look anything up**. You have the notes already; the point is to find out what you do not know first. Then open them, or ask an LLM, and correct what you wrote — keep both versions. The gap between your attempt and the answer is the part you will remember.

> **No answers are provided.** Sections A and B are prepared by the Friday before the Monday lecture, where they are quizzed in class. Section C is practised between the lecture and the Thursday lab — until you can do each unaided, without AI, on a lab desktop.
> Tiers are set by *composition*: how many distinct concepts a question requires (Section A), or how many functions you must write and connect (Section C). Section B is tiered differently — Easy asks you to state a definition, Medium to prove or state a property of one.
> **Assessed scope.** Sections A and B are quizzed in the **Monday lecture** — conceptual to Medium, mathematical to Easy. Section C is answered in the **Thursday lab** — coding to Medium. That is **19 of this chapter's 30 questions**. The tiers marked *stretch* are quizzed in neither session; attempt them if you finish early, and expect them in the block homework and the final examination.

**Notes:** [[Chapter15]] · [[Chapter15#Learning outcomes|Learning outcomes]] · [[Chapter15#Optional Reading and References|Optional reading]]

## A. Conceptual short-answer

*Where to look: [[Chapter15#Concept overview|Concept overview]] · [[Chapter15#Applications|Applications]]*

### Easy — a single concept

1. Define a vector quantiser as a function, naming its domain, codomain, and codebook.
2. What is distortion, and what happens to it as the codebook grows?
3. What is the rate in a rate–distortion trade-off, and in what units is it measured?
4. How does a quantiser become a segmentation of an image or volume?

### Medium — two or three concepts

5. Combining quantisation with clustering from Chapter 14: state the different question each framing asks of the same fitted model, and give a problem where each is the more natural framing.
6. Combining the distortion curve with the elbow heuristic: explain what regime change the elbow marks, and why it is a more defensible criterion here than in plain clustering.
7. Combining dimensionality reduction from Chapters 08 and 12 with quantisation: give two reasons to quantise in a reduced space and one risk it introduces.

### Hard — three or more concepts *(stretch — beyond the lab ceiling)*

8. Bring together the distortion scaling, the data dimension, and the elbow heuristic to explain why the elbow is sharp in low dimension and washed out in high dimension, and how this justifies reducing dimension first.
9. Using the codebook, the assignment step, and the interpretation of a cluster centroid from Chapter 14, explain what it means scientifically when two spatially distant regions of a volume receive the same label — and whether that is a defect.
10. Combining PCA, a nonlinear embedding, quantisation, and the caveat that embedded distances are unreliable, describe a complete segmentation pipeline for a three-dimensional scientific volume. Identify the step at which an artefact is most likely to be introduced, and how you would test for it.

## B. Mathematical

*Where to look: [[Chapter15#Key math|Key math]] · [[Chapter15#Concept overview|Concept overview]]*

### Easy — state a definition

1. Define a vector quantiser as a function, naming its domain, codomain, and codebook.
2. Define the expected and the empirical distortion.
3. Define a Voronoi cell of a codebook.
4. State the asymptotic scaling law relating optimal distortion to codebook size and data dimension.
5. Define the rate of a quantiser in bits per vector.

### Medium — prove or state a property *(stretch — beyond the lab ceiling)*

6. Show that for a fixed codebook the distortion-minimising assignment is nearest-neighbour, and that for a fixed assignment the distortion-minimising codeword is the cell mean.
7. Derive the predicted slope of the distortion curve on log-log axes from the scaling law.
8. Using that scaling, explain quantitatively why the elbow in the distortion curve sharpens as dimension falls.
9. Derive the number of bits required per vector and the compression ratio against storing the original floating-point features.
10. Prove that adding a codeword can never increase the optimal distortion, and state the consequence for selecting codebook size from distortion alone.

## C. Coding

*Where to look: [[Chapter15#Code examples|Code examples]] · [[Chapter15#Key math|Key math]]*

### Easy — a single function

1. Write a function that assigns each vector to its nearest codebook entry.
2. Write a function computing the per-point distortion given data, a codebook, and assignments.
3. Write a function that fits a codebook of a given size to a set of feature vectors.
4. Write a function that orders the rows of a design matrix by their assigned codeword, and use it to display the matrix with its block structure visible.

### Medium — two or three functions

5. Using your fitting and distortion functions, build a rate–distortion curve across a wide range of codebook sizes and plot it on log-log axes.
6. Write a function that fits a straight line to the log-log curve and returns the slope, and compare that slope against the theoretical prediction for your data's dimension.
7. Combine your assignment and distortion functions with a dimension-reduction step to compare quantising in the reduced space against the original space, reporting distortion measured consistently in one space.

### Hard — three or more functions *(stretch — beyond the lab ceiling)*

8. Build a pipeline of separate functions — extract features, reduce dimension, quantise, and map the codeword labels back onto the original measurements — and apply it end to end. Report the codebook size you chose and the evidence for it.
9. Assemble functions for quantisation, for reconstruction, and for measuring both distortion and bits per element, into a study of image colour quantisation across codebook sizes. Display the reconstructions and plot both quantities on shared axes.
10. Write functions to quantise in two different spaces, to map both labellings back to the original data, and to score their agreement. Use them to report how much the segmentation depends on where the quantisation was performed, and state which result you would publish and why.
