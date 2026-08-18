# Chapter 06 — Optimisation Methods — Question Bank

> **The question this chapter answers.** *You can write down the number that says how bad a fit is. How do you find the parameters that make it smallest?*
>
> Write an answer here **before you look anything up**. You have the notes already; the point is to find out what you do not know first. Then open them, or ask an LLM, and correct what you wrote — keep both versions. The gap between your attempt and the answer is the part you will remember.

> **No answers are provided.** Sections A and B are prepared by the Friday before the Monday lecture, where they are quizzed in class. Section C is practised between the lecture and the Thursday lab — until you can do each unaided, without AI, on a lab desktop.
> Tiers are set by *composition*: how many distinct concepts a question requires (Section A), or how many functions you must write and connect (Section C). Section B is tiered differently — Easy asks you to state a definition, Medium to prove or state a property of one.
> **Assessed scope.** Sections A and B are quizzed in the **Monday lecture** — conceptual to Medium, mathematical to Easy. Section C is answered in the **Thursday lab** — coding to Medium. That is **19 of this chapter's 30 questions**. The tiers marked *stretch* are quizzed in neither session; attempt them if you finish early, and expect them in the block homework and the final examination.

**Notes:** [[Chapter06]] · [[Chapter06#Learning outcomes|Learning outcomes]] · [[Chapter06#Optional Reading and References|Optional reading]]

## A. Conceptual short-answer

*Where to look: [[Chapter06#Concept overview|Concept overview]] · [[Chapter06#Applications|Applications]]*

### Easy — a single concept

1. Describe the three orders of optimiser by the derivative information each uses, and name a method in each.
2. State how the number of points in an exhaustive parameter grid scales with the number of parameters, and give the consequence for search.
3. What does momentum do to a gradient-descent trajectory?
4. What is the condition number of a Hessian, and what does a large value mean for optimisation?

### Medium — two or three concepts

5. Combining the loss surface with the choice of optimiser: explain what happens to gradient descent when curvatures differ greatly across directions, and name two distinct remedies with what each changes.
6. Combining second-order convergence with per-iteration cost: resolve the apparent contradiction that Newton-type methods converge in far fewer iterations yet first-order methods dominate large-scale machine learning.
7. Combining the conditioning of a matrix from Chapter 02 with the geometry of the loss surface: explain why rescaling the inputs speeds up gradient descent. Answer in terms of the curvature of the surface.

### Hard — three or more concepts *(stretch — beyond the lab ceiling)*

8. Bring together the likelihood of Chapter 05, the loss surface, and the choice of optimiser to describe how you would fit a parameter in a real experiment, from writing the objective to trusting the result. State what could go wrong at each stage.
9. Using convexity, local minima, and initialisation together, explain why two runs of the same fitting code on the same data can return different answers, and describe how you would establish which — if either — to believe.
10. Combining finite-difference gradients, conditioning, and floating-point precision, explain why a numerically computed gradient can be badly wrong even when the analytic formula is correct. Describe the diagnostic you would run and what a passing result would establish.

## B. Mathematical

*Where to look: [[Chapter06#Key math|Key math]] · [[Chapter06#Concept overview|Concept overview]]*

### Easy — state a definition

1. Define the gradient and the Hessian of a scalar loss, stating the shape of each.
2. Write the gradient-descent update and define the learning rate.
3. Write the momentum update and define its coefficient.
4. Write Newton's update.
5. Define the condition number of a symmetric positive-definite matrix.

### Medium — prove or state a property *(stretch — beyond the lab ceiling)*

6. For a one-dimensional quadratic loss, derive the range of step sizes for which gradient descent converges, and state what happens at each boundary of that range.
7. Derive Newton's step from a second-order Taylor expansion, and show that on a quadratic loss it reaches the minimum in one step from any start.
8. For a quadratic loss with a diagonal Hessian of widely differing entries, derive the largest stable learning rate and show that progress along the flattest direction is slowed by the ratio of curvatures.
9. State how the condition number of the Hessian controls the convergence rate of gradient descent, and what this implies for a badly scaled problem.
10. Derive the leading error term of the central finite-difference approximation, and explain why the total error worsens for both very large and very small step sizes.

## C. Coding

*Where to look: [[Chapter06#Code examples|Code examples]] · [[Chapter06#Key math|Key math]]*

### Easy — a single function

1. Write a function that evaluates a scalar loss with a known minimum.
2. Write a function that returns a finite-difference estimate of a derivative at a point.
3. Write a function performing exhaustive grid search over a bounded interval and returning the minimiser.
4. Write a function performing one gradient-descent step given a current point, a gradient function, and a step size.

### Medium — two or three functions

5. Using your loss and your grid searcher, plus a random-search function you write, compare the two zeroth-order methods at equal evaluation budget and report both minimisers.
6. Combine your gradient and single-step functions into a full gradient-descent loop that records its iterates, and plot the trajectory over the loss curve.
7. Write a momentum variant of your descent loop and compare it against plain descent on the same loss, reporting the iteration count each needs to reach a fixed tolerance.

### Hard — three or more functions *(stretch — beyond the lab ceiling)*

8. Build functions for a two-dimensional anisotropic quadratic loss, its analytic gradient, plain descent, and momentum descent. Plot both trajectories over the contours and report the iteration counts, then rescale the coordinates and report how plain descent improves.
9. Assemble a loss, a gradient, a descent loop, and a step-size sweep into a stability study: report which step sizes converge, diverge, or oscillate, and compare the observed boundary against your analysis in Section B.
10. Write functions implementing a loss, its analytic gradient, its analytic Hessian, and a Newton iteration. Apply them to a non-convex objective, report the iteration count against gradient descent from the same start, and add a check that detects when the Hessian is not positive definite and states what your code does about it.
