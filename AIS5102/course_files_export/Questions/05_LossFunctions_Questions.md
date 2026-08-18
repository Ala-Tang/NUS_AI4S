# Chapter 05 — Loss Functions and Maximum Likelihood — Question Bank

> **The question this chapter answers.** *You have two candidate fits to the same noisy data. What number tells you which is better, and where does that number come from?*
>
> Write an answer here **before you look anything up**. You have the notes already; the point is to find out what you do not know first. Then open them, or ask an LLM, and correct what you wrote — keep both versions. The gap between your attempt and the answer is the part you will remember.

> **No answers are provided.** Sections A and B are prepared by the Friday before the Monday lecture, where they are quizzed in class. Section C is practised between the lecture and the Thursday lab — until you can do each unaided, without AI, on a lab desktop.
> Tiers are set by *composition*: how many distinct concepts a question requires (Section A), or how many functions you must write and connect (Section C). Section B is tiered differently — Easy asks you to state a definition, Medium to prove or state a property of one.
> **Assessed scope.** Sections A and B are quizzed in the **Monday lecture** — conceptual to Medium, mathematical to Easy. Section C is answered in the **Thursday lab** — coding to Medium. That is **19 of this chapter's 30 questions**. The tiers marked *stretch* are quizzed in neither session; attempt them if you finish early, and expect them in the block homework and the final examination.

**Notes:** [[Chapter05]] · [[Chapter05#Learning outcomes|Learning outcomes]] · [[Chapter05#Optional Reading and References|Optional reading]]

## A. Conceptual short-answer

*Where to look: [[Chapter05#Concept overview|Concept overview]] · [[Chapter05#Applications|Applications]]*

### Easy — a single concept

1. State the maximum-likelihood principle in one sentence.
2. Why do we minimise the negative log-likelihood rather than maximising the likelihood directly? Give two distinct reasons.
3. Name the noise model corresponding to squared loss, and the one corresponding to absolute loss.
4. What must be specified beyond a deterministic model before you can write down a likelihood?

### Medium — two or three concepts

5. Combining a surrogate loss with the distinction between the objective you minimise and the metric you report: explain why a classifier is trained on cross-entropy but reported on accuracy, and give a case where the two disagree.
6. Combining maximum likelihood with the entropy ideas of Chapters 03–04: explain the sense in which minimising cross-entropy is maximum likelihood for a categorical outcome.
7. Combining the likelihood with unmodelled measurement noise: explain how such noise can bias an estimate systematically rather than merely adding scatter, and give a case where the direction of the bias is predictable in advance.

### Hard — three or more concepts *(stretch — beyond the lab ceiling)*

8. Bring together the physical model, the noise model, and the estimator to explain how the same dataset can yield two different published values of a physical constant, neither of which involves an arithmetic error. State what you would need from each paper to adjudicate.
9. Using maximum likelihood, the Gaussian assumption, and the CLT from Chapter 03, construct the argument for why Gaussian likelihoods are so often defensible — and then identify the specific circumstance in your own field where that argument breaks.
10. Combining a likelihood, a nuisance parameter, and the idea of an estimator's bias, explain why fitting *more* parameters can produce a *less* biased estimate of the one you care about. State what you pay for this, and how you would decide whether the trade is worthwhile.

## B. Mathematical

*Where to look: [[Chapter05#Key math|Key math]] · [[Chapter05#Concept overview|Concept overview]]*

### Easy — state a definition

1. Define the likelihood and the negative log-likelihood for independent data.
2. Define the maximum-likelihood estimator.
3. Write the Gaussian density and its negative log-likelihood at fixed variance.
4. Define the quadratic, absolute, and Huber losses, and name the transition parameter of the last.
5. Define the bias of an estimator.

### Medium — prove or state a property *(stretch — beyond the lab ceiling)*

6. Write the maximum-likelihood estimator as both an argmax and an argmin, and show the two are equivalent.
7. Starting from a Gaussian likelihood with fixed variance, derive the negative log-likelihood and identify the quadratic-loss term and the term constant in the parameters.
8. For a process whose increments are Gaussian with variance proportional to a parameter of interest, derive the maximum-likelihood estimator for that parameter and verify it is a minimum.
9. Suppose each observation carries additive independent noise of unknown variance. Derive how the observed variance relates to the true and noise variances, and show that ignoring the noise biases the estimate in a definite direction.
10. Derive the maximum-likelihood estimator for the variance of a Gaussian with known mean, state whether it is biased, and relate this to dividing by $N$ versus $N-1$.

## C. Coding

*Where to look: [[Chapter05#Code examples|Code examples]] · [[Chapter05#Key math|Key math]]*

### Easy — a single function

1. Write a function that simulates a stochastic process with a given parameter and returns the simulated data.
2. Write a function that returns the negative log-likelihood of a dataset as a function of a single parameter.
3. Write a function that computes the closed-form maximum-likelihood estimate from a summary statistic.
4. Write a function implementing the Huber loss with a tunable transition point.

### Medium — two or three functions

5. Using your simulator and your closed-form estimator, recover the parameter from synthetic data and report the relative error.
6. Using your likelihood function, evaluate it on a grid, and write a second function that returns the grid minimiser. Compare it against the closed-form estimate.
7. Write a function that adds measurement noise to a simulation and a second that applies the naive estimator. Use them to demonstrate the bias and compare it against your analytic prediction.

### Hard — three or more functions *(stretch — beyond the lab ceiling)*

8. Build functions for simulation, for a two-parameter likelihood that models the measurement noise explicitly, and for numerical minimisation. Assemble them to recover both parameters and report each against the truth.
9. Combine simulation, both estimators, and a repetition harness into a systematic bias study: sweep the noise level, run many trials at each, and plot the mean of each estimator against the truth. Report where the naive estimator becomes unacceptable and state your criterion.
10. Write functions implementing squared, absolute, and Huber losses, plus a common fitting routine and a data generator that injects gross outliers. Use them to compare the three fits on the same contaminated data, and report which loss you would choose and why.
