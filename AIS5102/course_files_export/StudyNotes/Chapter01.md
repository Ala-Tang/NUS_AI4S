# Chapter 01 — Introduction to Machine Learning

> Companion notes for `IntroToML.ipynb` and `Introduction to Machine Learning.pdf`. Audience: advanced undergraduate in physics, chemistry, biology, or engineering.
>
> **The question this chapter answers.** *Your instrument has produced ten thousand measurements. What could a computer tell you about them that you could not see by looking?*
>
> Work `Chapter01_Questions.md` **before** you read this. The full treatment — worked explanations, scaffolds, deeper reading — is on the chapter page.

## Learning outcomes

By the end of this chapter, you should be able to:

- Define an ML model as a parameterised function $f(x_n;\theta)\to y_n$, and name $\theta$ as the part a learning algorithm changes.
- Describe latent factors $z$ in the chain $x_n\to z\to y_n$ as compressed, hidden representations of the input.
- Distinguish supervised regression ($y_n$ continuous) from supervised classification ($y_n$ categorical), and read the parallel vocabulary across communities: features ↔ covariates ↔ predictors, outputs ↔ labels ↔ targets ↔ responses.
- Write a quadratic loss for regression, and explain training as minimising a loss over $\theta$.
- Define unsupervised learning and name three kinds: clustering, manifold learning, self-supervised learning.
- Distinguish a probability mass function from a probability density function, and state the normalisation condition for a conditional probability.

## Concept overview

> **Objective** — None. This chapter frames the question every later method minimises. · [[Chapter05#Chapters that minimise nothing|objective table]]

**A model is a function with adjustable parts.** Write it $f(x;\theta)$. The input $x$ is your measurement, $\theta$ is a list of numbers you may change, and the output is the prediction. Learning means searching over $\theta$. Nothing else about the function moves.

**Two camps, split by what you hold.** In **supervised** learning you hold inputs $\{x_n\}$ *and* matching outputs $\{y_n\}$, and you want $f(x_n;\theta)\approx y_n$. Continuous $y$ is **regression** — pendulum period from length, catalyst activity from descriptors. Categorical $y$ is **classification** — star type from spectrum, healthy against apoptotic cell. In **unsupervised** learning you hold only $\{x_n\}$ and look for structure: clusters, low-dimensional latent variables $z$, or tasks you invent yourself.

**Latent variables are the compressed middle.** The chain $x\to z\to y$ says the input first collapses to a few hidden coordinates, and those coordinates do the predicting. We insist that $\dim z \ll \dim x$, because a $z$ as large as $x$ has compressed nothing and explains nothing.

**Training is minimising a loss.** In either camp you write one number that says how wrong you are, then make it small. The simplest choice is the quadratic loss. Chapter 05 shows that this choice is a claim about your noise, and derives the alternatives.

**Two facts about probability, used all term.** A **probability mass function** gives the probability of each discrete outcome, and those probabilities sum to 1, so none may exceed 1. A **probability density** applies to continuous quantities and means nothing until you integrate it over an interval, so the density itself may exceed 1 — only the total area is fixed. A **conditional** probability $\Pr(A\mid B)$ normalises over $A$ with $B$ held fixed.

From these two ideas alone, Chapter 04 recovers Bayes' rule, maximum likelihood, entropy, mutual information, and the cross-entropy loss behind every modern classifier.

## Key math

$$
f(x_n;\theta)\to y_n,\qquad x_n\in\mathbb{R}^D,\ \theta\in\mathbb{R}^P,\ y_n\in\mathbb{R}\ \text{or}\ \{1,\dots,K\}.
$$

$$
x_n \longrightarrow z \longrightarrow y_n,\qquad \dim z \ll \dim x_n.
$$

$$
\mathcal{L}(\theta) = \sum_{n=1}^{N} \big\lvert y_n - f(x_n;\theta)\big\rvert^{2},\qquad \hat\theta = \arg\min_{\theta}\mathcal{L}(\theta).
$$

$$
p(X=x_i)\ \text{(mass)},\qquad \rho(X=x)\,dx \approx \Pr(x\le X \le x+dx)\ \text{(density)},\qquad \sum_{A}\Pr(A\mid B) = 1.
$$

## Code examples

> **Functions used.** *NumPy* — `np.array`, `np.linalg.solve`, `np.mean`, `np.random.default_rng`, `np.sum` · *scikit-learn* — `LinearRegression` · *Written here* — `loss`

```python
import numpy as np
from sklearn.linear_model import LinearRegression

rng = np.random.default_rng(0)
X = rng.normal(size=(200, 5))                   # design matrix: rows = measurements
theta_true = np.array([1.0, -0.5, 0.0, 2.0, 0.3])
y = X @ theta_true + 0.1 * rng.normal(size=200) # y_n = f(x_n; theta) + noise

model = LinearRegression(fit_intercept=False).fit(X, y)
print("quadratic loss:", np.mean((y - model.predict(X))**2))

theta_hat = np.linalg.solve(X.T @ X, X.T @ y)   # the same fit, closed form
```

## Applications

- **Materials science.** Features are Raman intensities, output is thermal conductivity, $\theta$ holds the regression coefficients.
- **Structural biology.** Features are an amino-acid sequence, output is a 3-D structure, $\theta$ holds AlphaFold's millions of weights.
- **Catalysis.** Features are $[E_{\mathrm{ads}}, d\text{-band centre}, \sigma_{\text{surface}}, a_{\text{lattice}}, \rho_{\text{surface}}]$; output is either current density (regression) or a high/low label (classification).
- **Astronomy.** Features are a stellar spectrum, output is a distribution over $\{\text{main sequence}, \text{red giant}, \text{white dwarf}\}$.
- **Microscopy.** Features are raw pixels, latent $z\in\mathbb{R}^{50}$ encodes shape and texture, output is a phenotype class — the $x\to z\to y$ pattern in one sentence.
- **Single-cell biology.** Features are $\sim\!10^4$ gene expressions, no labels at all; clustering in a learned $z$-space recovers known cell types.

<!-- glossary:start -->

## Glossary

*Every term below makes its first appearance in the course here. Plain words first, then the precise statement. Terms introduced in earlier chapters are in their glossaries.*

### Machine-learning concepts

- **Bayes' rule** — The arithmetic for updating what you believe once evidence arrives. *Precisely:* $\Pr(A\mid B)=\Pr(B\mid A)\Pr(A)/\Pr(B)$: posterior $\propto$ likelihood $\times$ prior.
- **classification** — Predicting which category something belongs to. *Precisely:* Supervised learning with a categorical target, $y\in\{1,\dots,K\}$.
- **cluster** — A group of measurements that resemble each other more than they resemble the rest. *Precisely:* A subset of rows chosen to optimise a compactness, density or connectivity criterion, without using labels.
- **conditional probability** — The chance of one thing given that you already know another. *Precisely:* $\Pr(A\mid B)=\Pr(A,B)/\Pr(B)$, normalised over $A$ with $B$ held fixed.
- **cross-entropy** — How surprised your predicted probabilities are by the outcome that actually occurred. *Precisely:* $H(p,q)=-\sum_i p_i\log q_i$. Minimised over $q$ when $q=p$.
- **entropy** — How much you do not know about an outcome before it happens. *Precisely:* $H(p)=-\sum_i p_i\log p_i$; bits if the log is base 2, nats if natural.
- **feature** — One measured number describing a sample: one column of your table. *Precisely:* A coordinate of $x_n\in\mathbb{R}^D$. Also called a covariate, predictor or independent variable.
- **label / target** — The answer you are trying to predict. *Precisely:* $y_n$, the output paired with $x_n$. Also called a target, response or dependent variable.
- **lasso** — Ridge's sibling: it shrinks some coefficients to exactly zero, so it selects features as well as fitting. *Precisely:* Least squares with an $\ell_1$ penalty, $\min_\beta \lVert y-X\beta\rVert^2 + \lambda\lVert\beta\rVert_1$.
- **latent variable** — A small set of hidden numbers the model invents to summarise each measurement. *Precisely:* $z$ in the chain $x\to z\to y$, with $\dim z \ll \dim x$ so that something is genuinely discarded.
- **least squares** — Fitting by making the total of the squared misses as small as possible. *Precisely:* $\hat\theta=\arg\min_\theta\sum_n\big(y_n-f(x_n;\theta)\big)^2$.
- **likelihood** — How probable your observed data would be, read as a function of the parameters. *Precisely:* $p(\mathcal{D}\mid\theta)$ with the data held fixed and $\theta$ varying. Not a probability over $\theta$.
- **loss function** — One number saying how wrong you are. Training makes it small. *Precisely:* $\mathcal{L}(\theta)=\sum_n \ell\big(y_n, f(x_n;\theta)\big)$.
- **manifold** — A curved surface the data lies on, thinner than the space holding it — a sheet of paper crumpled inside a room. *Precisely:* A space that looks locally like $\mathbb{R}^d$ for some $d$ below the ambient dimension.
- **maximum likelihood** — Choose the parameters that make what you actually saw most probable. *Precisely:* $\hat\theta=\arg\max_\theta p(\mathcal{D}\mid\theta)$, in practice by minimising the negative log-likelihood.
- **model** — A function with adjustable numbers that turns a measurement into a prediction. *Precisely:* $f(x;\theta)$. You choose the form of $f$; the learning algorithm chooses $\theta$.
- **mutual information** — How much knowing one quantity tells you about another. *Precisely:* $I(X;Y)=D_{\mathrm{KL}}\big(p(x,y)\,\Vert\,p(x)p(y)\big)$; zero exactly when the two are independent.
- **objective** — The quantity a method is trying to make as small, or as large, as possible. *Precisely:* The scalar function optimised, together with the variables it is optimised over. Chapter 05 tabulates one per method.
- **parameter** — The adjustable numbers inside a model — the knobs learning turns. *Precisely:* $\theta\in\mathbb{R}^P$, fixed by fitting rather than by you.
- **probability density** — For continuous quantities: probability *per unit* of the quantity. Only the area under it is a probability. *Precisely:* $\rho(x)\ge0$ with $\int\rho(x)\,dx=1$. The height may exceed 1; the area may not.
- **probability mass function** — For outcomes you can count: the probability of each one. They add to 1. *Precisely:* $p(x_i)\ge 0$ with $\sum_i p(x_i)=1$; no single value may exceed 1.
- **regression** — Predicting a number. *Precisely:* Supervised learning with a continuous target, $y\in\mathbb{R}$.
- **supervised learning** — Learning from examples where you already have the right answers. *Precisely:* Fitting $f(x;\theta)\approx y$ from pairs $\{(x_n,y_n)\}_{n=1}^N$.
- **unsupervised learning** — Looking for structure when nobody gave you any answers. *Precisely:* Optimising a criterion over $\{x_n\}$ alone. "Correct" is undefined, which is why judging the result is its own problem.

### Mathematics and notation

- **arg min / arg max** — The input that achieves the smallest (or largest) value — not the value itself. *Precisely:* $\arg\min_\theta g(\theta)$ is the $\theta$ attaining the minimum; $\min_\theta g(\theta)$ is the value.
- **big-O complexity** — How the running time or memory grows as the problem gets bigger, ignoring constants. *Precisely:* $g=O(h)$ if $|g|\le C|h|$ for all sufficiently large arguments.
- **closed form** — An answer you can write down as a formula and evaluate in one go, with no iterating. *Precisely:* A solution expressible in finitely many elementary operations.
- **dimension (of a space)** — How many independent numbers you need to name a point. *Precisely:* The number of vectors in any basis of the space.
- **integral** — The area under a curve, found by adding up infinitely many infinitesimally thin slices. *Precisely:* $\int_a^b f(x)\,dx$, the limit of Riemann sums.
- **matrix** — A rectangle of numbers arranged in rows and columns. *Precisely:* $A\in\mathbb{R}^{m\times n}$ with entries $A_{ij}$.
- **matrix inverse** — The matrix that undoes another one. In code you almost always want `solve` instead. *Precisely:* $A^{-1}$ with $AA^{-1}=I$. Exists only for square matrices of full rank.
- **scalar** — A single number, as opposed to a vector or a matrix. *Precisely:* An element of $\mathbb{R}$.
- **set membership ∈** — Reads as "is in": $x\in S$ says $x$ belongs to the collection $S$. *Precisely:* The membership relation between an element and a set.
- **subscript index** — The small number saying which item you mean: $x_n$ is the $n$-th one. *Precisely:* $x_n$ selects an element of a list; $A_{ij}$ the entry in row $i$, column $j$.
- **summation notation ∑** — Shorthand for "add all of these up". *Precisely:* $\sum_{n=1}^{N} a_n = a_1 + a_2 + \dots + a_N$.
- **ℝ^D (real vector space)** — The set of all lists of $D$ real numbers — the space one measurement lives in. *Precisely:* $\mathbb{R}^D$, a $D$-dimensional real vector space.

### Statistics

- **distribution** — How probability is spread over the possible outcomes. *Precisely:* A mass or density function assigning non-negative weight to outcomes, totalling 1.
- **random seed** — A number that makes "random" results repeatable, so a colleague can reproduce your figure. *Precisely:* The initial state of a pseudo-random generator, e.g. `np.random.default_rng(0)`.
- **sample (statistical)** — One measurement — one row of your table. Confusingly, also used for the whole collected set. *Precisely:* One realisation $x_n$ of the data-generating process; also the collection $\{x_n\}$.
- **sample mean** — The average of your measurements. *Precisely:* $\bar{x}=\frac{1}{N}\sum_{n=1}^N x_n$.

### Programming

- **array / ndarray** — NumPy's grid of numbers. Every computation in this course runs on one. *Precisely:* `np.ndarray`: a dense, fixed-`dtype`, N-dimensional buffer with a shape.
- **axis** — Which direction an operation runs along: `axis=0` collapses down the rows, `axis=1` across the columns. *Precisely:* The dimension index removed by a reduction such as `sum` or `mean`.
- **fit / transform / predict** — scikit-learn's three verbs: learn from data, apply what was learned, produce predictions. *Precisely:* `.fit(X, y)` sets internal state; `.transform(X)` and `.predict(X)` apply it to new data.
- **function (code)** — A named block of code that takes inputs and hands back a result. *Precisely:* `def name(args): ... return value`.
- **library / API** — Someone else's tested code you call instead of writing your own. The API is the set of calls it offers. *Precisely:* A distributed package plus its documented public interface.
- **notebook** — A document mixing runnable code, its output, and prose. *Precisely:* A `.ipynb` file of cells executed by a Jupyter kernel, in whatever order you run them.
- **pipeline (code)** — A chain of steps applied in a fixed order, so nothing is forgotten and nothing leaks. *Precisely:* `sklearn.pipeline.Pipeline`: transformers ending in an estimator, fitted as one object inside cross-validation.
- **return value** — What a function gives back when it finishes. *Precisely:* The object produced by `return`; `None` if omitted.
- **shape (of an array)** — The size of the grid: `(200, 5)` means 200 rows and 5 columns. *Precisely:* A tuple of dimension lengths. Mismatched shapes are the commonest NumPy error.
- **time / space cost** — How long a computation takes and how much memory it needs. *Precisely:* Asymptotic runtime and working memory as functions of $N$ and $D$.

### Scientific vocabulary

- **apoptotic** — A cell in the middle of programmed self-destruction — the unhealthy class in these examples. *Precisely:* Undergoing apoptosis, the regulated cell-death pathway, as against necrosis.
- **catalyst / adsorption** — A catalyst speeds a reaction without being used up; adsorption is a molecule sticking to its surface. *Precisely:* Adsorption energy $E_{\mathrm{ads}}$ and the d-band centre are standard descriptors of catalytic activity.
- **cell type** — What kind of cell it is — neuron, T cell, and so on. *Precisely:* A discrete biological identity, usually assigned from a gene-expression profile.
- **gene expression** — How strongly each gene is switched on in a cell. *Precisely:* Transcript abundance per gene; $\sim\!10^4$ features form one row of a single-cell design matrix.
- **Iris dataset** — A 150-flower table that has been the standard teaching dataset since 1936. *Precisely:* Four petal and sepal measurements for three iris species, 50 each.
- **lattice constant** — The repeat spacing of the atoms in a crystal. *Precisely:* The edge length of the unit cell, in ångström.
- **microscopy** — Imaging things too small to see. Each image, flattened, is one row of the table. *Precisely:* Optical or electron imaging producing a pixel array per field of view.
- **MNIST** — Seventy thousand small pictures of handwritten digits, the standard image benchmark. *Precisely:* $28\times28$ greyscale images in ten classes; flattened, a $784$-dimensional design matrix.
- **protein structure** — The three-dimensional shape a chain of amino acids folds into, which determines what it does. *Precisely:* The spatial coordinates of a folded polypeptide; AlphaFold predicts them from sequence alone.
- **Raman** — A spectroscopy that shines a laser at a sample and reads the light shifted by molecular vibrations. *Precisely:* Inelastic scattering; intensity against wavenumber shift, in cm$^{-1}$.
- **spectrum / spectra** — Intensity measured across a range of wavelengths or energies: one curve per sample. *Precisely:* A vector of intensities indexed by wavelength, wavenumber or energy. Flattened, it is one row of the design matrix.
- **stellar spectrum** — The light from a star split by wavelength; its shape says what kind of star it is. *Precisely:* Flux against wavelength, classified into main sequence, red giant, white dwarf and others.
- **wavenumber** — The horizontal axis of a Raman spectrum: how many wave cycles fit in a centimetre. *Precisely:* $\tilde\nu = 1/\lambda$, in cm$^{-1}$.

<!-- glossary:end -->

---

*Questions: `Chapter01_Questions.md` · Full treatment, scaffolds and deeper reading: the chapter page.*
