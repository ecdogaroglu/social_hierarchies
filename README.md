# Social Hierarchies with Strategic Ability


[![pre-commit.ci status](https://results.pre-commit.ci/badge/github/ecdogaroglu/social_hierarchies/main.svg)](https://results.pre-commit.ci/latest/github/ecdogaroglu/social_hierarchies/main)
[![image](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)

A Python implementation for analyzing the emergence and stability of social hierarchies through evolutionary game theory and stochastic processes.
Description
This repository contains a collection of tools for modeling strategic interactions between players using Markov chains and graph theory. The main focus is on identifying stochastically stable states and minimum stochastic potential equilibria, which help understand how social hierarchies emerge and persist over time.

See social_hierarchies.pdf for the related research paper including the theory developed and a discussion of the computational results.

An implementation of Young (1993) can be found here: https://github.com/ecdogaroglu/evolution_of_conventions.git

## Usage

To get started, create and activate the environment with

```console
$ conda/mamba env create
$ conda activate social_hierarchies
```

To build the project, type

```console
$ pytask
```

Project Structure
social-hierarchies/
├── src/
│   └── social_hierarchies/
│       ├── config.py            # Project configuration
│       ├── dynamics/            # Core stochastic process implementations
│       │   ├── graph.py         # Directed graph analysis
│       │   ├── markov_chain.py  # Markov chain computations
│       │   ├── probabilities.py # Probability calculations
│       │   └── task_dynamics.py # Pytask definitions for dynamics
│       ├── final/               # Results processing
│       │   ├── plot.py          # Plotting functions
│       │   └── task_final.py    # Pytask definitions for plotting
│       ├── game/                # Game theory components
│       │   ├── game.py          # State space and best response
│       │   └── task_game.py     # Pytask definitions for games
│       └── task_parameters.py   # Parameter management
├── paper/                       # Documentation/research outputs
└── bld/                         # Build directory for results


Example: Setting Parameters
Edit src/social_hierarchies/task_parameters.py to configure your simulation:
pythonparameters = {
    "m": 2,              # memory size
    "k": 1,              # sample size
    "epsilon": 0.0001,   # experimentation probability
    "num_act": 2,        # number of actions
    "num_players": 2,    # number of players (only 2 is supported)
    "l": 2,              # hierarchy levels
}

# Define game payoffs
parameters["payoffs"] = np.array([
    [(1, 1), (0, -1)],
    [(-1, 0), (1, 1)]
])
Key Concepts

State Space: Represents the history of play between agents
Transition Matrices: Capture how the system evolves with and without perturbations
Recurrent Communication Classes (RCC): Sets of states that communicate with each other
Stochastic Potential: Measures the difficulty of transitioning between RCCs
Edmonds' Algorithm: Finds the minimum stochastic potential states

Outputs
The analysis produces several outputs in the bld/ directory:

Transition matrices for perturbed and unperturbed processes
Stochastically stable states
Visualizations of:

RCC graphs
Stationary distributions
Edmonds' arborescences
Shortest paths between states

## Credits

This project was created with [cookiecutter](https://github.com/audreyr/cookiecutter)
and the
[econ-project-templates](https://github.com/OpenSourceEconomics/econ-project-templates).


## References

Young, H. Peyton. "The evolution of conventions." Econometrica: Journal of the Econometric Society (1993): 57-84.


License
This project is licensed under the MIT License - see the LICENSE file for details.
