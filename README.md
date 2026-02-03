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

## AI disclosure policy

All GSoC-related issues and pull requests must disclose AI usage.

If AI tools were used, end the issue or PR with a sentence beginning:

> AI assistance was used for ...

If no AI tools were used at all, end with the sentence:

> No AI tools were used in this contribution.

Submissions that omit a disclosure may be closed without review.

## Project Ideas

### Extend MathOptAI.jl

#### Short description

[MathOptAI.jl](https://github.com/lanl-ansi/MathOptAI.jl) is a package for
embedding trained machine learning predictors into JuMP models. The field is
moving fast, and many new models and formulations are being proposed. The
goal is this project is to add support for new predictors to MathOptAI.jl
so that it remains state-of-the-art.

#### Project Scope

The contributor will conduct a literature review of the field to construct a
prioritized list new formulations that are of interest to the mathematical
optimization community. Then, as time permits, they will add new predictors
to MathOptAI.jl.

#### Expected Deliverables

For each new predictor added to MathOptAI.jl, the contributor must add:

 - tests that achieve 100% code coverage
 - integration with relevant package extensions
 - documentation, including new tutorials that use the predictor

#### Skills Required

There are two strong prerequisites:

 - Strong knowledge of mathematical optimization (an ideal candidate will be
   enrolled in a Ph.D. course in optimization)
 - Strong knowledge of Julia and JuMP (an ideal candidate will have prior
   experience contributing to open-source Julia repositories that depend on JuMP
   or MathOptInterface)

and two weak prerequisites:

 - Basic knowledge of Python
 - Basic knowledge of machine learning frameworks such as PyTorch

Candidates looking to apply for this project are strongly discouraged from
opening issues in MathOptAI.jl (pull requests will be closed without review).
Instead, we would prefer candidates submit in their application a portfolio
of work on other JuMP/Julia based projects.

#### Project Size

 - **350 hours (Large)**: at least eight (8) new predictors

#### Mentors

 - [Oscar Dowson](https://github.com/odow)
 - [Robert Parker](https://github.com/robbybp)

### Improve AMPL Converter in JuMPConverter.jl

#### Short description

[JuMPConverter.jl](https://github.com/blegat/JuMPConverter.jl) is a converter for AMPL™ models
in `.mod` and GAMS™ models in `.gms` to [JuMP](https://github.com/jump-dev/JuMP.jl/) models.
The goal of this project is to extend the AMPL converter to support a broader range of AMPL
language features, enabling conversion of well-known benchmark collections that are widely
used in the optimization community.

#### Project Scope

The contributor will extend the AMPL converter in JuMPConverter.jl to handle the AMPL
constructs required by benchmark collections. This includes support for AMPL `.mod` files
with associated `.dat` data files, complementarity constraints (as used in MPECs), and
the nonlinear expressions commonly found in standard test problems. The work will be
validated against real-world benchmark sets with known solutions.

Given AMPL models as input, the converter generates equivalent Julia code using the JuMP framework. Algebraic expressions are delegated to Julia's native parser, simplifying the translation process and improving reliability.

**Note:** Direct reading of an AMPL model into a MathOptInterface (MOI) model—thereby implementing the [MathOptInterface.FileFormats](https://jump.dev/MathOptInterface.jl/dev/file-formats/) API is out of the scope and is not a requirement for completing the proposal; see [JuMPConverter.jl Issue #4](https://github.com/blegat/JuMPConverter.jl/issues/4).

#### Expected Deliverables

For the AMPL converter improvements, the contributor must add:

 - tests that achieve high code coverage for new AMPL constructs
 - support for reading `.mod` files with `.dat` data files
 - documentation of supported and unsupported AMPL features
 - integration tests using models from [MacMPEC.jl](https://github.com/blegat/MacMPEC.jl/) and [CUTE.jl](https://github.com/GiovanniKarra/CUTE.jl)

#### Skills Required

The following skills would be valuable for the project:

 - Good knowledge of mathematical optimization (MPECs, nonlinear programming)
 - Good knowledge of Julia and JuMP
 - Basic knowledge of parsing techniques
 - Familiarity with AMPL syntax and modeling

#### Project Size

 - **350 hours (Large)**: Extend the AMPL converter to successfully convert all models
   in [MacMPEC.jl](https://github.com/blegat/MacMPEC.jl) (the [MacMPEC](https://wiki.mcs.anl.gov/leyffer/index.php/MacMPEC)
   collection of Mathematical Programs with Equilibrium Constraints in AMPL format) and
   [CUTE.jl](https://github.com/GiovanniKarra/CUTE.jl) (the [CUTE](https://arnold-neumaier.at/glopt/coconut/Benchmark/Library2_new_v1.html)
   constrained and unconstrained testing environment benchmark set)

#### Mentors

 - [Benoît Legat](https://github.com/blegat)
 - [Oscar Dowson](https://github.com/odow)
