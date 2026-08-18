# Chapter 18 — Variational Inference and Expectation–Maximization — Question Bank

> **The question this chapter answers.** *You could fit the model if you knew which group each point came from, and you could assign groups if you knew the model. How do you start?*
>
> Write an answer here **before you look anything up**. You have the notes already; the point is to find out what you do not know first. Then open them, or ask an LLM, and correct what you wrote — keep both versions. The gap between your attempt and the answer is the part you will remember.

> **No answers are provided.** Sections A and B are prepared by the Friday before the Monday lecture, where they are quizzed in class. Section C is practised between the lecture and the Thursday lab — until you can do each unaided, without AI, on a lab desktop.
> Tiers are set by *composition*: how many distinct concepts a question requires (Section A), or how many functions you must write and connect (Section C). Section B is tiered differently — Easy asks you to state a definition, Medium to prove or state a property of one.
> **Assessed scope.** Sections A and B are quizzed in the **Monday lecture** — conceptual to Medium, mathematical to Easy. Section C is answered in the **Thursday lab** — coding to Medium. That is **19 of this chapter's 30 questions**. The tiers marked *stretch* are quizzed in neither session; attempt them if you finish early, and expect them in the block homework and the final examination.

**Notes:** [[Chapter18]] · [[Chapter18#Learning outcomes|Learning outcomes]] · [[Chapter18#Optional Reading and References|Optional reading]]

## A. Conceptual short-answer

*Where to look: [[Chapter18#Concept overview|Concept overview]] · [[Chapter18#Applications|Applications]]*

### Easy — a single concept

1. Why is the marginal likelihood usually intractable?
2. State the central idea of variational inference in one sentence.
3. Why is the evidence lower bound a *lower* bound, and what constitutes the gap?
4. What does a factorised approximating family get wrong about a posterior?

### Medium — two or three concepts

5. Combining the bound with the KL divergence of Chapter 04: explain why maximising the bound over the approximating distribution is the same as minimising the divergence to the true posterior, and what is held fixed for that equivalence.
6. Combining the latent-variable idea of Chapter 01 with the alternating algorithm: explain what each of the two steps optimises and why neither alone suffices.
7. Combining the condition for a closed-form posterior with the general variational case: state when the simpler algorithm is available, and name one model from the course requiring the general approach.

### Hard — three or more concepts *(stretch — beyond the lab ceiling)*

8. Bring together Jensen's inequality, the bound, and the exact decomposition of the log marginal likelihood to explain both why the bound holds and exactly how much is lost.
9. Using the bound, the alternating updates, and the notion of monotone improvement, explain why the algorithm cannot decrease the likelihood — and why that guarantee is nonetheless compatible with converging to a poor solution.
10. Combining latent variables, the optimisation landscape of Chapter 06, and the model-selection problem, describe how you would fit a latent-variable model to real data and decide how many latent components it needs. State where a wrong answer is most likely to come from.

## B. Mathematical

*Where to look: [[Chapter18#Key math|Key math]] · [[Chapter18#Concept overview|Concept overview]]*

### Easy — state a definition

1. Define the marginal likelihood of the observed data.
2. Define the variational family and the approximating distribution chosen from it.
3. Write the evidence lower bound in both of its equivalent forms.
4. State Jensen's inequality for a concave function.
5. Write the two alternating steps of the expectation–maximization algorithm.

### Medium — prove or state a property *(stretch — beyond the lab ceiling)*

6. Apply Jensen's inequality to the marginal likelihood to derive the lower bound, stating where the inequality entered and in which direction.
7. Prove the exact identity decomposing the log marginal likelihood into the bound plus a divergence, and use it to show that maximising the bound minimises the divergence to the true posterior.
8. Using that identity, show the bound is maximised by the exact posterior and that its maximum equals the log marginal likelihood.
9. Show that after the expectation step the bound is tight.
10. Using the tightness result, prove that each full iteration cannot decrease the log-likelihood.

## C. Coding

*Where to look: [[Chapter18#Code examples|Code examples]] · [[Chapter18#Key math|Key math]]*

### Easy — a single function

1. Write a function generating data from a mixture of one-dimensional components with specified parameters.
2. Write a function computing the responsibility of each component for each point given the current parameters.
3. Write a function computing the log-likelihood of a dataset under a given mixture.
4. Write a function that updates the mixture parameters given a responsibility array.

### Medium — two or three functions

5. Combine your responsibility and update functions into one full iteration, and verify the log-likelihood does not decrease across it.
6. Assemble a complete fitting loop from your two step functions and a convergence check, and compare the fitted parameters against the generating ones.
7. Write a function recording the log-likelihood at every iteration and one that plots the trace, and use them to confirm monotone improvement and report where your tolerance was met.

### Hard — three or more functions *(stretch — beyond the lab ceiling)*

8. Build functions for the log marginal likelihood, for the bound under a given approximating distribution, and for the divergence gap. Use them to verify the exact decomposition numerically under both the correct posterior and a deliberately poor approximation.
9. Assemble generation, fitting, and scoring functions into a study of initialisation sensitivity: run many random starts, report the distribution of final log-likelihoods, and state how often the best solution was found.
10. Write functions to fit at several component counts, to compute an information criterion, and to compare against ground truth. Use them to select the number of components, then repeat on data generated from a model outside the assumed family and report what the criterion does when the model class is wrong.
