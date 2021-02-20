# COVID-19 Individual Based Modelling

A simple infection model for educational purposes to demonstrate the statistical concepts behind public health decisions.

Created over an evening in early March 2020 by a Computational Physicist, this is essentially a modified Ising model with infections rather than spin states.

TOY MODEL ONLY - No quantifiable results here!

## Theory

Basic COVID-19 individual-based model where infection occurs with probability

P = exp(-I/R_0)

I: intervention level

R_0 : base infection level

Infections last for 10 days with infections granting immunity from reinfection for 365 days.

There is a base chance of 1% for a re-emergence of the disease through the random infecting of a member of the population if there are no present infections.

The model treats each member of the population separately, hence individual based modelling. In this simple model each individual exists with two binary properties: *infected* and *immune*.

The simulation first creates the population to be studied and then infects an inital seed sample. The simulation then occurs by simulating a given number of daily interactions over a time period with the intervention and infection levels provided. This occurs as follows:

* Choose two random members of the population
* If both are immune continue to next daily interaction
* If neither are infected continue to next daily interaction
* Else one must be infected while the other is not immune
  * Generate a random number between 0 and 1
  * If the number falls below the probability then infection occurs
  * Set the individual to be *infected* and *immune*
* Continue to next daily interaction
* At the end of each day the infection and immunity of each member of the population is advanced
  
## Usage

The simulator is initialised with a population size and starting seed infection level:

> sim = Simulation(pop_size = 1000, seed_pop = 1)

The simulation can then be allowed to run for a given number of days with desired parameters:

> sim.run(time=100, daily_interactions=100, intervention_level=10, r_0=2.5)

The statistics for the simulation are available:

> sim.total_infections

> sim.current_infection_level

> sim.immunity_level

## Example

### Comparison of low, medium, and high interventions on total infection rates

![Intervention comparison](/images/interventions.png)

