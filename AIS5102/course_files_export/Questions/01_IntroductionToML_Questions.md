# Chapter 01 — Introduction to Machine Learning — Question Bank

> **The question this chapter answers.** *Your instrument has produced ten thousand measurements. What could a computer tell you about them that you could not see by looking?*
>
> Write an answer here **before you look anything up**. You have the notes already; the point is to find out what you do not know first. Then open them, or ask an LLM, and correct what you wrote — keep both versions. The gap between your attempt and the answer is the part you will remember.

> **No answers are provided.** This chapter is **conceptual only** — it carries no mathematical or coding questions. Chapter 01 sets up the vocabulary and the framing that the rest of the course builds on; the mathematics arrives from Chapter 02 and the coding practice begins with the NumPy self-study.
> Tiers are set by *composition*: how many distinct concepts a question requires.
> **Assessed scope.** Sections Easy and Medium are quizzed in the **Monday lecture** — **7 of this chapter's 10 questions**. The Hard tier is marked *stretch*: quizzed in neither session, but fair game for the block homework and the final examination.

**Notes:** [[Chapter01]] · [[Chapter01#Learning outcomes|Learning outcomes]] · [[Chapter01#Optional Reading and References|Optional reading]]

## A. Conceptual short-answer

*Where to look: [[Chapter01#Concept overview|Concept overview]] · [[Chapter01#Applications|Applications]]*

### Easy — a single concept

1. A machine-learning model is a parameterised function. Identify the roles of the input, the parameters, and the output, and state which one a learning algorithm changes.
2. What distinguishes supervised from unsupervised learning? Give one example of each from your own subfield.
3. What is a latent variable, and why do we normally insist that the latent space be much smaller than the input space?
4. Distinguish a probability mass function from a probability density function. Explain why a density may exceed 1 while a mass function may not.

### Medium — two or three concepts

5. Combining a parameterised model with a loss function: state what a squared-error loss assumes about the measurements, and give a situation in which that assumption is wrong.
6. Combining supervised learning with the latent-variable picture: give a research question that could be attacked either supervised or unsupervised, and state what you gain and lose by each choice.
7. Combining conditional probability with the notion of a model: explain what it means to say a classifier outputs a *distribution* over labels rather than a label, and what the normalisation condition guarantees.

### Hard — three or more concepts *(stretch — beyond the lab ceiling)*

8. Bring together the parameterised model, the latent variable, and the loss function to describe a complete supervised pipeline for a measurement problem in your field. State what each of the three contributes, and identify which of them encodes your scientific assumptions.
9. Using the model, the loss, and the distinction between densities and masses, explain why a regression problem and a classification problem require different losses even when the underlying model architecture is identical.
10. A collaborator proposes to fit a model with more parameters than measurements. Using the ideas of parameterisation, loss minimisation, and latent structure, explain what will go wrong, what would have to be true of the data for it to nonetheless work, and what you would check first.
