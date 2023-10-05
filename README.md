# Introduction to Computational Science
Introduction to Computational Science - University course for 1st year MSc Computational Science (joint programme UvA/VU)

## Canvas
https://canvas.uva.nl/courses/39305

## Assignment 2
Topics: stochastic discrete event models & spatial modelling.

### Problem 1: Gillespie’s Direct Algorithm and Stochastic Hallmarks
Five hallmarks of stochastic SIR dynamics using an event drive SIR model:
1. variability;
2. negative co-variances;
3. increased transients;
4. stochastic resonance;
5. extinctions.

Steps:
1. Implement Gillespies ALgorithm:
   - define the events and rates of each event for the SIR model;
   - potentially compare GA stochastic simulation with a deterministic ODE counterpart;
   - BONUS: think about and and implement a way to control the noise level in the GA.
2. Investigate Simulation Variability and Negative Co-variance:
   - investigate how varying the model parameters changes the behaviour of the stochastic dynamics;
     - variance between runs;
     - impact on negative covariance between S and I.
  - compare the mean of the stochastic simulations with the equivalent deterministic model output (for multiple settings of the model parameters).
3. Stochastic Resonance and Increased Transients:
  - show how the stochastic model can induce stochastic resonance around the equilibrium and how the resonance relates (to?) the model parameters (e.g. N, $\beta$)
  - show some examples of increased transients away from the deterministic equilibrium (which parameter values lead to the largest transients?)
4. Extinction Events and Critical Community Size:
  - design an experiment to show how varying $R_0$ impacts extinction of the virus (in the closed system randomness will always lead to extinction);
  - how are extinction events impacted by population size?
  - show how $R_0$ and N interact to impact the extinction process.


## Problem 2: Spatial Models - Networks
Develop a set of experiments to design and evaluate vaccination strategies using a network model. Using NDLib (https://ndlib.readthedocs.io/en/latest/tutorial.html) asses the spread of SIR accross different types of networks (Barabasi Albert, Watts-Strogatz, Erdos-Reyni). Run a simulated vaccination campaign on a real contact network collected by sociopatterns (http://www.sociopatterns.org/publications/simulation-of-an-seir-infectious-disease-model-on-the-dynamic-contact-network-of-conference-attendees/ , modified version on Canvas).

1. Implement SIR and Simulate:
 - apply SIR on network - which parameters do we want to vary?
 - design code that allows running multiple simulations while varying the disease parameter.
3. Generate Networks of Equivalent Form:
 - using NetworkX generate multiple model networks with similar characteristics (parameters - number of nodes, connection probability, ...);
 - pick network statistics (centrality measures, degree distributions, etc.) for measuring the spread on the network;
 - generate multiple instances of each network type and plot the statistics;
 - discuss how these statistics differ between network types and for different parameter settings.
4. Simulate SIR Spread on the Network:
   - simulate epidemic spreading (think about random seeds and repetitions)
   - vary different parameters - fraction of the initially infected, which nodes are initially infected, others.
   - compare and discuss differences.
5. Dynamic Vaccination Campaign:
  - design code to load in the sociopatterns dataset (disregard weights of the original datasets and assume all contacts involve equal length of contact, equal chance of transmission);
  - run multiple experiments of a disease spread (always start with a random selection of 5 nodes infected);
  - design a dynamic vaccination strategy with a limited testing budget and number of vaccinations per iteration period:
    - $N$ tests in total (e.g. 200), $N_i$ maximum tests per iteration;
    - tests can be used at any point during the spread, can be repeated on a node as often as we like;
    - assume that we know the network structure but we can only discover the the disease status of a node after a test;
    - vaccinations can only be applied to S (immediately -> R);
    - assume no waning immunity;
    - BONUS: consider situations where the tests are not always accurate but have a probability of being accurate;
    - compare strategy against a simple null strategy that randomly assigns vaccinations
