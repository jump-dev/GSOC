# GSOC2026

JuMP is a modeling interface and a collection of supporting packages for
mathematical optimization that is embedded in Julia. With JuMP, users formulate
various classes of optimization problems with easy-to-read code, and then solve
these problems using state-of-the-art open-source and commercial solvers. JuMP
also makes advanced optimization techniques easily accessible from a high-level
language.

[JuMP](https://jump.dev/) will be participating as a sub-organization in
[NumFOCUS](http://numfocus.org/)'s application for
[Google Summer of Code 2026](https://summerofcode.withgoogle.com/).

For more information about this application see:
[NumFOCUS's main GSoC page](https://github.com/numfocus/gsoc)

## Project Ideas

### Extend MathOptAI.jl

#### Short description

MathOptAI.jl is a package for embedding trained machine learning predictors into
JuMP models. The field is moving fast, and many new models and formulations are
being proposed. The goal is this project is to add support for new predictors to
MathOptAI.jl so that it remains state-of-the-art.

#### Project Scope

The contributor will conduct a literature review of the field to construct a
prioritized list new formulations that are of interest to the research
community. Then, as time permits, they will add new predictors to MathOptAI.jl.

#### Expected Deliverables

For each new predictor added to MathOptAI.jl, the contributor must add:

 - tests that achieve 100% code coverage
 - integration with relevant package extensions
 - documentation, including new tutorials that use the predictor

#### Skills Required

 - Knowledge of mathematical optimization
 - Basic knowledge of Python, Julia, and JuMP
 - Basic knowledge of machine learning frameworks such as PyTorch

#### Project Size

 - **175 hours (Medium)**: at least four (4) new predictors
 - **350 hours (Large)**: at least eight (8) new predictors

#### Mentors

 - [Oscar Dowson](https://github.com/odow)
