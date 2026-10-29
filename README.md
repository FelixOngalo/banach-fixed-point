# The Banach Fixed-Point Theorem: Proof, Iteration, and Numerical Verification in R

## Overview

This project explores the **Banach Fixed-Point Theorem** through a rigorous mathematical proof and a computational investigation implemented in **R**.

The theorem establishes that a contraction mapping on a non-empty complete metric space has a unique fixed point and that successive iterations converge to it. It connects fundamental concepts in real analysis and metric space theory with practical numerical methods.

The project develops the mathematical theory first, then implements **fixed-point iteration and Newton’s method from scratch in R**. The numerical experiments examine convergence behaviour, approximation errors, and the relationship between observed results and the theorem’s theoretical error bound.

## Mathematical Foundations

### 1. Banach Fixed-Point Theorem

Let \((X,d)\) be a non-empty complete metric space, and let \(T:X\to X\) be a contraction. Then there exists a constant \(q\in[0,1)\) such that

\[
d(Tx,Ty)\leq qd(x,y)
\]

for all \(x,y\in X\).

The theorem guarantees:

- Existence of a fixed point \(x^*\) satisfying \(T(x^*)=x^*\).
- Uniqueness of the fixed point.
- Convergence of the iteration \(x_{n+1}=T(x_n)\) to \(x^*\) for any initial point \(x_0\in X\).

### 2. Proof and Error Bound

The proof establishes that the sequence of iterates is Cauchy by using the contraction condition:

\[
d(x_{n+1},x_n)\leq q^n d(x_1,x_0).
\]

Completeness guarantees convergence to a point in \(X\), and the contraction property establishes existence and uniqueness of the fixed point.

The theorem also provides an a priori error bound:

\[
d(x_n,x^*)\leq
\frac{q^n}{1-q}d(x_1,x_0).
\]

The project derives this bound and uses it to assess the accuracy of the numerical approximations produced in R.

## Numerical Methods in R

### 1. Fixed-Point Iteration

The fixed-point algorithm is implemented using base R:

\[
x_{n+1}=T(x_n).
\]

The implementation tracks successive iterates, calculates differences between consecutive approximations, and stops when a specified convergence tolerance is reached or a maximum iteration limit is exceeded.

### 2. Newton’s Method

Newton’s method is implemented independently to approximate solutions of \(f(x)=0\):

\[
x_{n+1}=x_n-\frac{f(x_n)}{f'(x_n)}.
\]

The R implementation records the iteration history, monitors convergence, and evaluates the final approximation.

Newton’s method is compared with fixed-point iteration in terms of convergence speed, numerical accuracy, and sensitivity to the initial approximation. The project also distinguishes Newton’s practical convergence from the guarantees of the Banach theorem, which require appropriate contraction conditions.

## R Implementation and Analysis

The computational component uses **base R** to make the numerical procedures transparent and reproducible.

Key implementation features include:

- Defining contraction mappings as R functions.
- Writing iterative algorithms without relying on specialised numerical-solver packages.
- Recording iteration histories in vectors or data frames.
- Calculating successive differences and approximation errors.
- Evaluating theoretical error bounds.
- Comparing observed errors against predicted bounds.
- Implementing convergence tolerances and maximum iteration safeguards.
- Comparing fixed-point iteration with Newton’s method.
- Producing plots of convergence and error behaviour.

Where the exact fixed point is known or can be computed independently to sufficient accuracy, the observed absolute error can be compared directly with the theoretical bound. Otherwise, the project distinguishes estimated error from a rigorously established upper bound.

## Numerical Verification

The R experiments investigate:

- Whether fixed-point iteration converges under the theorem’s assumptions.
- How the contraction constant affects convergence speed.
- Whether observed errors remain within the theoretical error bound.
- How fixed-point iteration compares with Newton’s method.
- How initial values and stopping tolerances affect numerical performance.

These experiments illustrate how computational results can support the understanding of a mathematical theorem without replacing its proof.

## Key Concepts and Skills

**Pure Mathematics**
- Metric spaces and completeness
- Contraction mappings
- Fixed-point existence and uniqueness
- Cauchy sequences
- Convergence proofs
- Geometric series and error bounds

**Numerical Analysis**
- Fixed-point iteration
- Newton’s method
- Convergence criteria
- Error estimation
- Numerical stability and stopping conditions

**R Programming**
- Base R functions and iterative algorithms
- Vector operations and data frames
- Conditional statements and loops
- Function definition and numerical computation
- Data visualisation
- Reproducible computational experiments

## Limitations

Numerical verification tests selected examples; it cannot establish the theorem for every admissible mapping. The general guarantee comes from the mathematical proof.

Newton’s method also requires separate convergence analysis. Its convergence is not guaranteed for every function or initial value, and it satisfies the Banach framework only when an appropriate contraction mapping and domain can be established.

## Purpose

This project forms part of a **Pure Mathematics portfolio**, demonstrating the ability to prove a mathematical result, translate mathematical ideas into algorithms, and use R to investigate their numerical consequences.

The central approach is:

> **Prove the theorem, derive the error bound, implement the algorithms in R, and use numerical experiments to examine the theoretical predictions.**
