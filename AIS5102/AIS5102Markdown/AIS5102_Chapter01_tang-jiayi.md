# AIS5102 · Chapter 01 submission

**Name:** TANG JIAYI  
**Student ID:** A0355738N  
**Generated:** 2026-08-17

> 10 of 10 questions attempted · 12 of 20 glossary terms marked known, 8 to learn again.

---

## Part 1 — Attempt

*Written before reading the chapter, then corrected after. Sections A and B; the coding questions are answered in the notebook.*

### A. Conceptual short-answer

**A1** — A machine-learning model is a parameterised function. Identify the roles of the input, the parameters, and the output, and state which one a learning algorithm changes.

parameters change

**A2** — What distinguishes supervised from unsupervised learning? Give one example of each from your own subfield.

label

**A3** — What is a latent variable, and why do we normally insist that the latent space be much smaller than the input space?

otherwise will copy the x

**A4** — Distinguish a probability mass function from a probability density function. Explain why a density may exceed 1 while a mass function may not.

the density function calculate per unit of the continues quantity, while the integrated is 1 of the interval

**A5** — Combining a parameterised model with a loss function: state what a squared-error loss assumes about the measurements, and give a situation in which that assumption is wrong.

It breaks when outliers are common

**A6** — Combining supervised learning with the latent-variable picture: give a research question that could be attacked either supervised or unsupervised, and state what you gain and lose by each choice.

cell situation.Supervised: "I know what I'm looking for. Tell me if I found it." (Certain, but limited)
• Unsupervised: "Show me what's in the data." (Open-ended, but maybe irrelevant)

**A7** — Combining conditional probability with the notion of a model: explain what it means to say a classifier outputs a distribution over labels rather than a label, and what the normalisation condition guarantees.

sum to 1

**A8** — Bring together the parameterised model, the latent variable, and the loss function to describe a complete supervised pipeline for a measurement problem in your field. State what each of the three contributes, and identify which of them encodes your scientific assumptions.

Problem: Predict drug toxicity from cell images.

Model: CNN

Input: 512×512 pixels
Output: toxicity score (0-100)

Latent variable: 128 dimensions

Compresses image to 128 numbers
Represents "what the cell looks like"

Loss function: Squared error

L = (predicted - true)²
Assumes: measurement errors are Gaussian

Which encodes scientific assumptions?

All three:

Model assumes: toxicity is in the pixels
Latent assumes: 128 features are enough
Loss assumes: big errors are rare (← people forget this)

If data has outliers (contaminated samples),
squared error breaks.

**A9** — Using the model, the loss, and the distinction between densities and masses, explain why a regression problem and a classification problem require different losses even when the underlying model architecture is identical.

Regression: y is continuous → distance is defined → squared error
Classification: y is categorical → no distance → score distributions → cross-entropy

Same architecture. Different output type. Different loss.

**A10** — A collaborator proposes to fit a model with more parameters than measurements. Using the ideas of parameterisation, loss minimisation, and latent structure, explain what will go wrong, what would have to be true of the data for it to nonetheless work, and what you would check first.

P > N means more parameters than data points, so infinite parameter combinations can fit the training data perfectly. The model picks one randomly and might pick one that memorizes noise instead of learning real patterns — overfitting. But it works anyway if the data has true underlying structure (like only 5 cell types) because the model will prioritize learning that structure over noise, or if you use regularization (dropout, L1 penalty) to force the model to pick the simplest solution from all the tied solutions. Check first by holding out 20% of data for testing — if test accuracy is high, it learned real patterns; if test accuracy is low, it's overfitting.

---

## Part 2 — Glossary self-test

*20 terms make their first appearance in this chapter.*

### Terms I still need to learn

- **classification** — Predicting which category something belongs to.
- **cluster** — A group of measurements that resemble each other more than they resemble the rest.
- **manifold** — A curved surface the data lies on, thinner than the space holding it — a sheet of paper crumpled inside a room.
- **probability mass function** — For outcomes you can count: the probability of each one. They add to 1.
- **regression** — Predicting a number.
- **dimension (of a space)** — How many independent numbers you need to name a point.
- **subscript index** — The small number saying which item you mean: xn is the n-th one.
- **catalyst / adsorption** — A catalyst speeds a reaction without being used up; adsorption is a molecule sticking to its surface.

### Terms I could define

conditional probability, feature, label / target, latent variable, loss function, model, objective, parameter, probability density, supervised learning, unsupervised learning, function (code)

### My notes on these terms

**classification** — supervised learning with a categorical target

**cluster** — without using laber ;  optimuse a density criterion

**conditional probability** — Pr(A|B)=Pr(A,B)/Pr(B)

**feature** — A coordinate of xn∈ℝD. Also called a covariate, predictor or independent variable.

**label / target** — yn, the output paired with xn. Also called a target, response or dependent variable.

**latent variable** — z in the chain x→z→y, with dim z ≪dim x so that something is genuinely discarded.

**loss function** — L(θ)=∑n ell(yn, f(xn;θ))

**manifold** — A space that looks locally like ℝd for some d below the ambient dimension

**model** — f(x;θ). You choose the form of f; the learning algorithm chooses θ.

**objective** — The scalar function optimised, together with the variables it is optimised over. Chapter 05 tabulates one per method.

**parameter** — the knobs learning turns

**probability density** — ρ(x)≥0 with ∫ρ(x) dx=1. The height may exceed 1; the area may not

**probability mass function** — p(xi)≥0 with ∑i p(xi)=1; no single value may exceed 1

**regression** — Supervised learning with a continuous target, y∈ℝ

**supervised learning** — Fitting f(x;θ)≈y from pairs {(xn,yn)}n=1N

**unsupervised learning** — Optimising a criterion over {xn} alone. "Correct" is undefined, which is why judging the result is its own problem

**dimension (of a space)** — The number of vectors in any basis of the space.

**subscript index** — The small number saying which item you mean: xn is the n-th one.

**function (code)** — def name(args): ... return value

**catalyst / adsorption** — cat吸附
