# 2D SEIR Dorm Intervention Model - QuarantineQueens
A 2D agent-based simulation of infection spread and intervention dynamics in a college dormitory using the SEIR framework.

This project uses Julia's Agents.jl package to simulate how infection spreads in a dorm setting based on public health interventions such as masking and vaccination. Each student is represented by an agent that interacts with neighbors and transitions between states (Susceptible, Exposed, Infected, Recovered) over time.

## Features
1. Spatially explicit 2D grid-based simulation of a dorm.
2. Agent movement constrained by dorm layout (walls and doors).
3. Risk-aware agent behavior (unprotected, masked, or vaccinated).
4. SEIR transitions based on exposure time and probabilistic infection.
5. Visualizations of infection trends over time and by risk class.
6. Supports multiple simulation runs for averaging results.

## Model Overview
Each agent (student) has the following properties:
1. health_status: 0: Susceptible, 1: Exposed, 2: Infected, 3: Recovered
2. days_exposed: Tracks time since exposure.
3. days_infected: Tracks time since infection.
4. risk_class: 0: Unprotected, 1: Masked, 2: Vaccinated

### Movement and Environment
Agents live in a 20×20 grid with central wall partitions and defined doorways. Agents move randomly each timestep, constrained by walls but allowed through doors. Movement avoids overlap with other agents.

### Transition Dynamics
Exposed agents may become infected based on transmission_prob. Risk class modifies infection chance (e.g., masking reduces probability). Infected agents recover after d_infected days.

## Running the Simulation
1. Set Parameters -  At the bottom of the script, modify the following: timesteps, num_runs, plot_graphs. Additionally modify ENV/RISK parameters to suit a unique pathogen. 
2. Run the Simulation - Call run_sims(num_runs, timesteps, plot_graphs). This will simulate the model num_runs times and generate plots if plot_graphs = true.

## Sample Results

![seir](https://github.com/karthik-krishnan-28/Dorm-Infection-SEIR-Model/blob/main/extras/seir.png)

## Visualizing agents

Agents can also be visualized over time. Red agents are infected, yellow are exposed, blue and susceptible, and green are recovered. For instance, here is a sample initial condition:
![seir](https://github.com/karthik-krishnan-28/Dorm-Infection-SEIR-Model/blob/main/extras/start.png)

And here is a sample final condition:
![seir](https://github.com/karthik-krishnan-28/Dorm-Infection-SEIR-Model/blob/main/extras/end.png)
