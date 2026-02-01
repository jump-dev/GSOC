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

 - **175 hours (Medium)**: at least four (4) new predictors
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

 - **175 hours (Medium)**: extend the AMPL converter to successfully convert all models
   in [MacMPEC.jl](https://github.com/blegat/MacMPEC.jl) (the [MacMPEC](https://wiki.mcs.anl.gov/leyffer/index.php/MacMPEC)
   collection of Mathematical Programs with Equilibrium Constraints in AMPL format)
 - **350 hours (Large)**: in addition to MacMPEC, successfully convert all models in
   [CUTE.jl](https://github.com/GiovanniKarra/CUTE.jl) (the [CUTE](https://arnold-neumaier.at/glopt/coconut/Benchmark/Library2_new_v1.html)
   constrained and unconstrained testing environment benchmark set)

#### Mentors

 - [Benoît Legat](https://github.com/blegat)

### Batched parameters in MathOptInterface and solvers

#### Short description

[MathOptInterface (MOI)](https://github.com/jump-dev/MathOptInterface.jl) is the abstraction
layer between solvers and high-level modeling languages like [JuMP](https://github.com/jump-dev/JuMP.jl).
Many use cases (e.g. sensitivity analysis, scenario optimization, or GPU-accelerated solving)
require solving the same model for many different parameter values. Batched solvers that can
exploit this structure are now emerging—see [MadIPM.jl#78](https://github.com/MadNLP/MadIPM.jl/pull/78)
and recent work on [batched first-order methods for GPU](https://arxiv.org/abs/2601.21990). The
goal of this project is to add native support for *batched parameters* in MOI so that these
solvers can be used from JuMP, and to provide a fallback for solvers that do not support batching
so that JuMP models using the batching interface remain solver-agnostic.

#### Project Scope

The contributor will implement the `Batched{S}` set described in
[MathOptInterface.jl#2904](https://github.com/jump-dev/MathOptInterface.jl/issues/2904):
parameters can be set to a vector of values, and the model is solved once per batch element,
with results accessible via `result_count`. This design allows solvers to natively support
batched parameters (e.g. on GPU) while remaining compatible with the rest of the MOI stack.

The work involves implementing support across the full stack:
1. Add the `Batched{S}` set in [MathOptInterface.jl](https://github.com/jump-dev/MathOptInterface.jl)
2. Add batched parameter support in [NLPModels.jl](https://github.com/JuliaSmoothOptimizers/NLPModels.jl),
   continuing the work started in [NLPModels.jl#521](https://github.com/JuliaSmoothOptimizers/NLPModels.jl/pull/521)
3. Add support for MOI's `Batched{S}` sets to [NLPModelsJuMP.jl](https://github.com/JuliaSmoothOptimizers/NLPModelsJuMP.jl)
   by converting them to NLPModels' batch representation
4. Test the whole pipeline with [MadIPM](https://github.com/MadNLP/MadIPM.jl)
   (that supports batch solve thanks to [MadIPM.jl#78](https://github.com/MadNLP/MadIPM.jl/pull/78))

This creates the complete path: **JuMP → MOI Batched set → NLPModelsJuMP → NLPModels → MadIPM**.
MadIPM will be the first solver to support batched solves through JuMP, providing a concrete
implementation to test the interface end-to-end (once established, other solvers can adopt it).

#### Expected Deliverables

 - Add the `Batched{S}` set and related MOI API (get/set, copy, etc.) in MathOptInterface
 - Extend NLPModels.jl to support batched parameters (continuing PR #521)
 - Implement the MOI `Batched{S}` to NLPModels conversion in NLPModelsJuMP.jl
 - Tests and documentation for the new API at each layer

#### Skills Required

 - Good knowledge of Julia and [MathOptInterface](https://jump.dev/MathOptInterface.jl/)
 - Good knowledge of mathematical optimization and solver interfaces
 - Familiarity with [ParametricOptInterface](https://github.com/jump-dev/ParametricOptInterface.jl)
   or parameter handling in MOI is helpful

#### Project Size

 - **175 hours (Medium)**: implement the `Batched{S}` set in MathOptInterface (#2904) and
   interface it through the full stack (NLPModels.jl continuing PR #521, NLPModelsJuMP.jl,
   and MadIPM PR #78), so that batched solves work end-to-end from JuMP to MadIPM
 - **350 hours (Large)**: in addition, implement the fallback in
   [ParametricOptInterface.jl](https://github.com/jump-dev/ParametricOptInterface.jl): a
   wrapper optimizer that supports batched parameters by solving each instance in turn when
   the underlying solver does not support batching natively (analogous to the
   `MathOptBatchOptimizer` sketch in the issue)

#### Mentors

 - [Benoît Legat](https://github.com/blegat)
