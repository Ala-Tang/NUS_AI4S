## Notes from the Chapter 01 page

**A1 — A machine-learning model is a parameterised function. Identify the roles of the input, the parameters, and the output, and state which one a learning algorithm changes.**

you choose the form, you should predict first?

**A10 — A collaborator proposes to fit a model with more parameters than measurements. Using the ideas of parameterisation, loss minimisation, and latent structure, explain what will go wrong, what would have to be true of the data for it to nonetheless work, and what you would check first.**

confused

**A classifier small enough to read — Murphy, Probabilistic Machine Learning: An Introduction, Fig. 1.4, p. 5**

simple enough

**The squared error, drawn — Murphy, Probabilistic Machine Learning: An Introduction, Fig. 1.5, p. 10**

line square sum

**Three fits, and the price of the third — Murphy, Probabilistic Machine Learning: An Introduction, Fig. 1.7, p. 12**

P<=N

**The same data, with the answer key withheld — Murphy, Probabilistic Machine Learning: An Introduction, Fig. 1.8, p. 15**

clear

**A cloud, and its shadow — Murphy, Probabilistic Machine Learning: An Introduction, Fig. 1.9, p. 15**

flower cloud!

**Concept overview**

amazing confused

**Key math**

hhh

**catalyst / adsorption — glossary**

cat吸附

**classification — glossary**

supervised learning with a categorical target

**cluster — glossary**

without using laber ;  optimuse a density criterion

**conditional probability — glossary**

Pr(A|B)=Pr(A,B)/Pr(B)

**dimension (of a space) — glossary**

The number of vectors in any basis of the space.

**feature — glossary**

A coordinate of xn∈ℝD. Also called a covariate, predictor or independent variable.

**function (code) — glossary**

def name(args): ... return value

**label / target — glossary**

yn, the output paired with xn. Also called a target, response or dependent variable.

**latent variable — glossary**

z in the chain x→z→y, with dim z ≪dim x so that something is genuinely discarded.

**loss function — glossary**

L(θ)=∑n ell(yn, f(xn;θ))

**manifold — glossary**

A space that looks locally like ℝd for some d below the ambient dimension

**model — glossary**

f(x;θ). You choose the form of f; the learning algorithm chooses θ.

**objective — glossary**

The scalar function optimised, together with the variables it is optimised over. Chapter 05 tabulates one per method.

**parameter — glossary**

the knobs learning turns

**probability density — glossary**

ρ(x)≥0 with ∫ρ(x) dx=1. The height may exceed 1; the area may not

**probability mass function — glossary**

p(xi)≥0 with ∑i p(xi)=1; no single value may exceed 1

**regression — glossary**

Supervised learning with a continuous target, y∈ℝ

**subscript index — glossary**

The small number saying which item you mean: xn is the n-th one.

**supervised learning — glossary**

Fitting f(x;θ)≈y from pairs {(xn,yn)}n=1N

**unsupervised learning — glossary**

Optimising a criterion over {xn} alone. "Correct" is undefined, which is why judging the result is its own problem

## Terms to learn again

- **classification** — Predicting which category something belongs to.

- **cluster** — A group of measurements that resemble each other more than they resemble the rest.

- **manifold** — A curved surface the data lies on, thinner than the space holding it — a sheet of paper crumpled inside a room.

- **probability mass function** — For outcomes you can count: the probability of each one. They add to 1.

- **regression** — Predicting a number.

- **dimension (of a space)** — How many independent numbers you need to name a point.

- **subscript index** — The small number saying which item you mean: xn is the n-th one.

- **catalyst / adsorption** — A catalyst speeds a reaction without being used up; adsorption is a molecule sticking to its surface.