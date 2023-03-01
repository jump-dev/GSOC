# GSOC2023

JuMP is a modeling interface and a collection of supporting packages for mathematical optimization that is embedded in Julia. With JuMP, users formulate various classes of optimization problems with easy-to-read code, and then solve these problems using state-of-the-art open-source and commercial solvers. JuMP also makes advanced optimization techniques easily accessible from a high-level language.

[JuMP](https://jump.dev/) will be participating as a sub-organization in [NumFOCUS](http://numfocus.org/)'s application for [Google Summer of Code 2023](https://summerofcode.withgoogle.com/). For more information about this application see:
- [NumFOCUS's main GSoC page](https://github.com/numfocus/gsoc)

## Mentors

- [Oscar Dowson](https://github.com/odow)
- [Joaquim Dias Garcia](https://github.com/joaquimg)
- [Mario Souto](https://github.com/mariohsouto)
- [Mathieu Besançon](https://github.com/matbesancon)

## Ideas

###  Robust Optimization in JuMP

#### Abstract

Robust optimization is an important subfield of optimization.
Latest versions of JuMP do not support such class of problems.
A unmaintened package that works with early JuMP versions is [JuMPeR](https://github.com/IainNZ/JuMPeR.jl).

| **Priority** | **Involves** | **Mentors** |
| ------------ | ------------ | ----------- |
|  Medium  | Creating a JuMP Extension for Robust Optimization | [Joaquim Dias Garcia](https://github.com/joaquimg), [Mario Souto](https://github.com/mariohsouto) |

#### Abstract

Robust optimization is an important subfield of optimization that addresses the challenges of having uncertainty associated with the parameters of the problem. Robust optimization is a powerful tool from decision theory that has several applications of interest such as control, power systems and finance.

The goal of this project is to create a layer on top of JuMP to facilitate the use of robust optimization and foster the adoption of this methodology among practitioners. This new modelling layer should be user friendly and leverage the modularity of MathOptInterface.

#### Technical details

This project will focus on modelling tractable reformulations of uncertainty. We plan to address the following in order: box, ellipsoidal, polyhedral and conic.

It will be necessary to extract matrix representation from MOI with MatrixOfConstraints and apply the required transformations to obtain a robust reformulation. An interface for handling results and uncertainties must be developed along the project.

#### Helpful Experience

- Knowledge of mathematical optimization (robust optimization)
- Basic knowledge of MathOptInterface

#### Steps

**Initial steps**

- Read the MathOptInterface manual and get familiar with the data structures used to represent scalar and vector functions
- Read [The Price of Robustness](https://www.robustopt.com/references/Price%20of%20Robustness.pdf), [A Practical Guide to Robust Optimization](https://arxiv.org/pdf/1501.02634.pdf) as introductions to the theme and notation, it might be useful to review relevant chapters of Robust Optimization by A Ben-Tal, L El Ghaoui, A Nemirovski .
- Read the implementation of [JuMPeR](https://github.com/IainNZ/JuMPeR.jl)
- Read about new extensions such as [Dualization](https://github.com/JuMP-dev/Dualization.jl)

**Key deliverables**

- Implement the box uncertainty reformulation
- Implement the ellipsoidal uncertainty reformulation
- Implement the polyhedral uncertainty reformulation

**Stretch goals**

- Handle conic uncertainty

###  Chordal decomposition of SDP

#### Abstract

Chordal decomposition is a key step in the formulation of sparse SDP.
Implementations are already available
in [SumOfSquares](https://github.com/jump-dev/SumOfSquares.jl/)
and [COSMO](https://github.com/oxfordcontrol/COSMO.jl).

| **Priority** | **Involves** | **Mentors** |
| ------------ | ------------ | ----------- |
|  Medium  | Creating Chordal extension and decomposition packages | [Joaquim Dias Garcia](https://github.com/joaquimg), [Mathieu Besançon](https://github.com/matbesancon) [Benoît Legat](https://github.com/blegat) |

#### Abstract

Many semidefinite problems are sparse and exploiting this sparsity can significantly
reduce the computation time and memory needed to solve the problem.

The goal of this project is to refactor existing implementation of chordal sparsity reduction into a MathOptInterface layer that is easy to plug into any SDP solver as a transformation layer.

#### Technical details

Chordal decomposition and PSD matrix completion for SDPs are not currently accessible through MathOptInterface.
The core goal of this project is to create an MOI layer for chordal decomposition and allow these capabilities to be easy options from JuMP that work with any SDP solver.
Then, this package will be used to create sparse SDP examples for JuMP, drawing from several application areas.
Finally, there is the possibility of working on improvements to chordal graph algorithms themselves.

#### Helpful Experience

- Knowledge of mathematical optimization (semidefinite programming)
- Knowledge of graph theory and chordal graphs (see *Chordal Graphs and Semidefinite Optimization* by Lieven Vandenberghe and Martin S. Andersen)
- Basic knowledge of MathOptInterface

#### Steps

**Initial steps**

- Read the MathOptInterface manual and get familiar with the data structures used to represent scalar and vector functions
- Read [*Chordal Graphs and Semidefinite Optimization*](http://www.seas.ucla.edu/~vandenbe/publications/chordalsdp.pdf) by Lieven Vandenberghe and Martin S. Andersen and [*A Clique Graph Based Merging Strategy for Decomposable SDPs*](https://arxiv.org/pdf/1911.05615.pdf) by Michael Garstka, Mark Cannon, and Paul Goulart to familiarize yourself with the use of chordal sparsity in semidefinite programming
- Read the implementation of algorithms on chordal graphs
in [SumOfSquares](https://github.com/jump-dev/SumOfSquares.jl/), [COSMO](https://github.com/oxfordcontrol/COSMO.jl), and [ChordalDecomp.jl](https://github.com/tjdiamandis/ChordalDecomp.jl)

**Key deliverables**

- Create a ChordalOptInterface.jl package an MOI layer doing chordal sparsity decomposition
- Allow chordal decomposition to be an easy to use option from JuMP that works with any semidefinite solver
- Add examples that use chordal decomposition to solve large-scale sparse semidefinite programs in applications of interest

**Stretch goals**

- Improve algorithms for chordal decomposition in the currently-under-development [ChordalDecomp.jl](https://github.com/tjdiamandis/ChordalDecomp.jl)

