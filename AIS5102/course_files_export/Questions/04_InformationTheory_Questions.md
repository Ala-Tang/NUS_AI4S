# Chapter 04 — Information Theory and Simple Bayesian Inference — Question Bank

> **The question this chapter answers.** *Two measurements are clearly related, but not along a straight line. How would you measure how much one tells you about the other?*
>
> Write an answer here **before you look anything up**. You have the notes already; the point is to find out what you do not know first. Then open them, or ask an LLM, and correct what you wrote — keep both versions. The gap between your attempt and the answer is the part you will remember.

> **No answers are provided.** Sections A and B are prepared by the Friday before the Monday lecture, where they are quizzed in class. Section C is practised between the lecture and the Thursday lab — until you can do each unaided, without AI, on a lab desktop.
> Tiers are set by *composition*: how many distinct concepts a question requires (Section A), or how many functions you must write and connect (Section C). Section B is tiered differently — Easy asks you to state a definition, Medium to prove or state a property of one.
> **Assessed scope.** Sections A and B are quizzed in the **Monday lecture** — conceptual to Medium, mathematical to Easy. Section C is answered in the **Thursday lab** — coding to Medium. That is **19 of this chapter's 30 questions**. The tiers marked *stretch* are quizzed in neither session; attempt them if you finish early, and expect them in the block homework and the final examination.

**Notes:** [[Chapter04]] · [[Chapter04#Learning outcomes|Learning outcomes]] · [[Chapter04#Optional Reading and References|Optional reading]]

## A. Conceptual short-answer

*Where to look: [[Chapter04#Concept overview|Concept overview]] · [[Chapter04#Applications|Applications]]*

### Easy — a single concept

1. Name the four components of Bayes' rule and state what each means in a classification problem from your own field.
2. Define conditional independence and give a scientific example.
3. What does mutual information measure, and what does a value of zero imply?
4. State the MAP decision rule in words.

### Medium — two or three concepts

5. Combining Bayes' rule with conditional independence: explain why a Naive Bayes classifier is justified when features are conditionally independent given the class, and describe a symptom you would observe when that assumption fails.
6. Combining entropy from Chapter 03 with mutual information: explain how mutual information can be written as a reduction in uncertainty, and what "uncertainty about what, given what" means in a measurement context.
7. Combining KL divergence with cross-entropy: explain why minimising either gives the same answer when the target distribution is fixed, and why the two are nonetheless not interchangeable in general.

### Hard — three or more concepts *(stretch — beyond the lab ceiling)*

8. Bring together the prior, the likelihood, and the evidence to explain why a highly sensitive diagnostic test can still yield mostly false positives. Identify which of the three quantities does the damage, and what would have to change to fix it.
9. Using Bayes' rule, marginalisation over a latent variable, and the MAP rule together, describe a complete inference pipeline for classifying a measurement whose class is not directly observed. State what each step contributes.
10. Combining mutual information, correlation from Chapter 03, and the notion of a feature from Chapter 01, design a procedure for screening which measured variables are worth keeping as model inputs. State what your procedure would miss and how you would detect that.

## B. Mathematical

*Where to look: [[Chapter04#Key math|Key math]] · [[Chapter04#Concept overview|Concept overview]]*

### Easy — state a definition

1. Write Bayes' rule and define the prior, likelihood, evidence, and posterior.
2. Define independence and conditional independence for discrete random variables.
3. Define entropy, joint entropy, and conditional entropy.
4. Define mutual information as a KL divergence, naming the two distributions involved.
5. State the MAP decision rule in both its direct and logarithmic forms.

### Medium — prove or state a property *(stretch — beyond the lab ceiling)*

6. Derive Bayes' rule from the definition of conditional probability, and write the evidence explicitly as a sum over the latent class.
7. For a test of known sensitivity and specificity on a low-prevalence condition, derive the posterior probability given a positive result, and explain why it can fall far below the sensitivity.
8. Prove Gibbs' inequality, and use it to derive the identity relating cross-entropy, entropy, and KL divergence.
9. Prove that mutual information equals entropy minus conditional entropy, show it is symmetric in its arguments, and state what a value of zero implies.
10. Show that the direct and logarithmic MAP forms select the same class, and explain why the logarithmic form is numerically preferred.

## C. Coding

*Where to look: [[Chapter04#Code examples|Code examples]] · [[Chapter04#Key math|Key math]]*

### Easy — a single function

1. Write a function that returns all marginals of a discrete joint distribution given as an array.
2. Write a function that computes a conditional distribution by normalising a joint along a chosen axis.
3. Write a function computing mutual information from a two-dimensional joint table.
4. Write a function that returns the MAP class from a posterior array.

### Medium — two or three functions

5. Using your marginal and conditional functions, verify Bayes' rule numerically on a joint you construct: compute the posterior directly and via the rule, and assert they agree.
6. Write a function testing a joint for independence and another testing conditional independence given a third variable. Construct cases that pass and fail each.
7. Combine your mutual-information and marginalisation functions to compute the mutual information between each feature and the class label in a labelled dataset, and rank the features.

### Hard — three or more functions *(stretch — beyond the lab ceiling)*

8. Build functions to estimate class-conditional distributions from data, to form the posterior, and to apply the MAP rule. Assemble them into a working classifier and report its accuracy.
9. Extend the classifier from the previous question with a function that supplies an arbitrary prior. Use it to show how accuracy and the per-class error rates respond to a deliberately misspecified prior, and explain which classes suffer most.
10. Construct a pipeline of functions that builds a joint distribution over two features and a latent class in which the features are marginally dependent but conditionally independent given the class, verifies both properties numerically, and then demonstrates that a Naive Bayes classifier is exactly correct on it. Then perturb the construction so the assumption fails, and report how the classifier degrades.
