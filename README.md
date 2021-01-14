# Julia for adaptive high-order simulations

[![License: MIT](https://img.shields.io/badge/License-MIT-success.svg)](https://opensource.org/licenses/MIT)
<!-- [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/trixi-framework/talk-2021-julia-adaptive-multi-physics-simulations/main?filepath=getting_started_with_julia_and_trixi.ipynb)-->

This is the companion repository for the talk

**Julia for adaptive high-order simulations**  
*Michael Schlottke-Lakemper*  
Numerical Analysis Seminar, Lund University  
27th January 2021, 3:15pm CET

with additional material.

## Getting started

**NOTE: This repository will be updated several times before the talk, with the
final version of the notebook to be uploaded at least one day prior.**

## Abstract
Julia has been touted as a programming language especially well-suited for
numerical analysis and scientific computing. However, while its prevalence is
steadily increasing, it has not yet seen widespread adoption in the
computational science or high-performance computing communities. One of the
hurdles is a (perceived) lack of real-world examples that show how Julia can be
used to conduct numerical simulations and what its advantages and drawbacks are
for scientific applications.

To remediate this, in this talk we discuss the development of a purely
hyperbolic method for self-gravitating gas dynamics within our Julia-based open
source simulation framework
[Trixi.jl](https://github.com/trixi-framework/Trixi.jl). In this approach, we
reformulate
the elliptic gravity problem into a hyperbolic diffusion problem, which is
solved in pseudotime using the same explicit high-order discontinuous Galerkin
method we use for the flow solution. A key benefit is that in the resulting
multi-physics simulation problem, we can reuse existing hyperbolic solvers while
retaining advanced features such as non-conforming and solution-adaptive meshes.

Next to presenting numerical results, we will critically examine our experience
with building a multi-physics simulation framework with Julia. We will discuss
its strengths and weaknesses as a programming language for research software
engineering, including an assessment of how Julia's claimed benefits hold up
against scientific reality, and give a live demonstration of Julia and Trixi.jl
in action.

To make the shown examples reproducible by the audience, the Jupyter notebook
used for the live demonstration is available in this repository
(see [above](https://github.com/trixi-framework/talk-2021-julia-adaptive-multi-physics-simulations)).
It can be either run from a local Julia/Jupyter installation or in the cloud via
Binder (without having to install Julia locally).

## Authors
This repository was initiated by
[Michael Schlottke-Lakemper](https://www.mi.uni-koeln.de/NumSim/schlottke-lakemper).

## License
The contents of this repository are licensed under the MIT license (see [LICENSE.md](LICENSE.md)). 
