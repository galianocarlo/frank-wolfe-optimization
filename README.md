# Frank-Wolfe Optimization for Matrix Completion in Recommender Systems

## Project Overview

This repository contains the mathematical formulation and Python from-scratch implementation of first-order optimization algorithms for the Matrix Completion problem in recommender systems. The goal is to reconstruct a target matrix $X \in \mathbb{R}^{n_1 \times n_2}$ from a sparse set of observations $\Omega$. The optimization is based on minimizing the squared error subject to a nuclear norm constraint ($\Vert{}X\Vert{}_* \le \tau$) to promote low-rank reconstructions.

## Algorithmic Implementation

The following algorithms have been implemented and compared:

* **Standard Frank-Wolfe (FW):** Iteratively solves the problem using a Linear Minimization Oracle (LMO) based on 1-SVD to extract the principal singular vectors and compute a rank-1 update.

* **Away-Step Frank-Wolfe (AFW):** Extends the standard algorithm by allowing the removal of weight from suboptimal historical atoms, in order to mitigate the zig-zagging phenomenon at the boundaries of the domain.

* **Pairwise Frank-Wolfe (PFW):** Modifies the Away-Step logic by combining the movements towards the best atom and away from the worst atom into a single weight-swapping operation.

## Analysis and Metrics

* **Gradient Computation and LMO:** The gradient of the objective function is highly sparse and is evaluated exclusively on the observed indices. The LMO identifies the direction of steepest descent by minimizing the inner product between the gradient and the set of rank-1 atoms.

* **Optimality Certificate:** The algorithms compute the Frank-Wolfe duality gap to empirically track the theoretical $\mathcal{O}(1/k)$ convergence and establish a rigorous stopping criterion.

* **Exact Line Search:** The step size $\gamma_k$ is computed algebraically via Exact Line Search, maximizing the progress at each iteration without requiring iterative approximations.

## Datasets Used

Empirical evaluations on convergence and predictive accuracy were conducted on the following real-world datasets:

* **MovieLens 100k**

* **Amazon Video Games**

* **MyAnimeList (Anime_UserRatings)**

## Repository Structure

```
📦 pairwise-frank-wolfe-optimization
 ┣ 📂 notebooks
 ┃ ┗ 📜 matrix_completion_experiments.ipynb  # Mathematical implementation and training logs
 ┣ 📂 report
 ┃ ┣ 📜 ODS_PROJECT_20.tex                   # LaTeX source code
 ┃ ┗ 📜 ODS_PROJECT_20.pdf                   # Complete mathematical report
 ┣ 📜 requirements.txt                       # Dependencies (NumPy, SciPy, Matplotlib)
 ┗ 📜 README.md
```
