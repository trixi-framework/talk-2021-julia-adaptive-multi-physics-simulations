# Julia for adaptive high-order multi-physics simulations

[![License: MIT](https://img.shields.io/badge/License-MIT-success.svg)](https://opensource.org/licenses/MIT)
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/trixi-framework/talk-2021-julia-adaptive-multi-physics-simulations/main?filepath=getting_started_with_julia_and_trixi.ipynb)

This is the companion repository for the talk

**Julia for adaptive high-order multi-physics simulations**  
*Michael Schlottke-Lakemper*  
Numerical Analysis Seminar, Lund University  
27th January 2021, 3:15pm CET

(see abstract [below](#abstract)). Here you can find the presentation slides
[talk-julia-adaptive-multi-physics-simulations-20200127.pdf](talk-julia-adaptive-multi-physics-simulations-20200127.pdf)
as well as the
the [Jupyter](https://jupyter.org) notebook
[getting_started_with_julia_and_trixi.ipynb](getting_started_with_julia_and_trixi.ipynb),
which was used during the talk for a live demonstration of Julia and
[Trixi.jl](https://github.com/trixi-framework/Trixi.jl).
Note that to play the video linked in the presentation, you also need to download the [media/](media/)
directory and place it in the same folder as the PDF.
There are also some additional
Trixi elixirs (simulation setups) in the [examples](examples/) directory.

## Getting started

### Using mybinder.org
The easiest way to get started is to click on the *Launch Binder* badge above (or
[here](https://mybinder.org/v2/gh/trixi-framework/talk-2021-julia-adaptive-multi-physics-simulations/main?filepath=getting_started_with_julia_and_trixi.ipynb)).
This launches the notebook for interactive use in your browser without the need
to download or install anything locally.

In this case, you can skip the rest of this *Getting started* section. A
Jupyter instance will be started automagically in the cloud via
[mybinder.org](https://mybinder.org), and the notebook will loaded directly from
this repository.

*Note:*  Depending on current usage and available resources,
it typically takes 1-2 minutes to launch a notebook with
[mybinder.org](https://mybinder.org) (sometimes a little longer), so try to
remain patient. Similarly, the first two cells of the notebook take much longer
to execute than usual (around 1.5 minutes for the first Trixi simulation and
about 1 minute for the first plot), since Julia compiles all methods
"just-ahead-of-time" at first use.  Subsequent runs will be much faster.

### Setting up a local Julia/Jupyter installation
Alternatively, you can also clone this repository and open the notebook on your
local machine. This is recommended if you already have a Julia + Jupyter setup
or if you plan to try out Julia anyways.

#### Installing Julia and IJulia
To obtain Julia, go to https://julialang.org/downloads/ and download the latest
stable release (v1.5.3 as of 2021-01-14; neither use the LTS release nor Julia Pro).
Then, follow the
[platform-specific instructions](https://julialang.org/downloads/platform/)
to install Julia on your machine. Note that there is no need to compile anything if you are using
Linux, MacOS, or Windows.

After the installation, open a terminal and start the Julia *REPL*
(i.e., the interactive prompt) with
```shell
julia
```
To use the notebook, you also need to get the
[IJulia](https://github.com/JuliaLang/IJulia.jl) package, which provides a Julia
backend for Jupyter. In the REPL, execute
```julia
using Pkg
Pkg.add("IJulia")
```
to install IJulia.

#### Installing the required Julia packages
To make the notebook fully reproducible, we have used Julia's package manager
to pin all packages to a fixed release. This ensures that you always have a
Julia environment in which all examples in this notebook work. Later you can
always install the latest versions of Trixi and its dependencies by following
the instructions in the Trixi
[documentation](https://trixi-framework.github.io/Trixi.jl/stable/).

If you have not done it yet, clone the repository where this notebook is stored:
```shell
git clone git@github.com:trixi-framework/talk-2021-julia-adaptive-multi-physics-simulations.git
```
Then, navigate to your repository folder and install the required packages:
```shell
cd talk-2021-julia-adaptive-multi-physics-simulations
julia --project=. -e 'using Pkg; Pkg.instantiate()'
```
This will download and build all required packages, including the ODE package
[OrdinaryDiffEq](https://github.com/SciML/OrdinaryDiffEq.jl), the visualization
package [Plots](https://github.com/JuliaPlots/Plots.jl), and of course
[Trixi](https://github.com/trixi-framework/Trixi.jl).
The `--project=.` argument tells Julia to use the `Project.toml`
and `Manifest.toml` files from this repository to figure out which packages to install.

#### Running the notebook
To run the notebook, open a Julia REPL and execute
```julia
using IJulia
notebook()
```
to start a Jupyter server in your browser. You can then navigate to the cloned
repository and launch the `getting_started_with_julia_and_trixi.ipynb` notebook.
At first invocation, it will ask if it should install a Julia-internal Jupyter
instance (which you should definitely do if you do not have an existing Jupyter
installation).
For more details, especially on how to use an existing Jupyter installation,
please refer to the [IJulia documentation](https://julialang.github.io/IJulia.jl/stable/).

As an alternative to running the examples in the notebook directly, you may
also just view the notebook *statically* by opening it within
[Jupyter NBViewer](https://nbviewer.jupyter.org/github/trixi-framework/talk-2021-julia-adaptive-multi-physics-simulations/blob/main/getting_started_with_julia_and_trixi.ipynb?flush_cache=true).
Then, you can copy the individual code snippets and execute them in the REPL by navigating to
the repository folder and starting Julia with
```shell
julia --project=.
```

*General note:* Make sure that you execute the examples (either in the notebook or in the
REPL) *in order*, at least for the first time. Both the notebook and the
Julia REPL maintain an internal state and and some snippets depend on
earlier statements having been executed.


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
(see [above](#getting-started)).
It can be either run from a local Julia/Jupyter installation or in the cloud via
Binder (without having to install Julia locally).

## Authors
This repository was initiated by
[Michael Schlottke-Lakemper](https://www.mi.uni-koeln.de/NumSim/schlottke-lakemper).

## License
The contents of this repository are licensed under the MIT license (see [LICENSE.md](LICENSE.md)). 
