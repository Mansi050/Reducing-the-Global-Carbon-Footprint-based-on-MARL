
# Future work on “Reducing the Global Carbon Footprint based on MARL" ~ Valentin Kahn



# Abstract.
This research paper intends to model the investment of groups of countries into carbon emission reductions based on a Mixed Markov Game setting, applying the principles of off-policy single-agent Reinforcement Learning to a multi-agent setting with a Markov Decision Process (MDP). The study shows that countries which are choosing their carbon emission reduction actions under the constraint of optimizing their and their partners‘ mid-term economic benefit, achieve both higher cumulative rewards and higher reductions in their per capita CO2 consumption, than their counterparts. It also shows that action choices considering immediate and future rewards for the individual agents, as well as the cumulative reward of all agents, converge to large reductions in the carbon emission level per capita of these countries. Multi-agent reinforcement learning (MARL) bears important problem-solving potential by modeling economic and political decision makers in simulated environments.


# Overview
This study models the behavior of multiple agents representing groups of countries (categorized on the basis of being affected by the effects of global warming) in reducing their CO2 consumption while taking actions selfishly but not competitively, in a mixed Markov game setting with a global state and correlated reward functions and policies, modeled based on Coordination Equilibrium Q-Learning (CE-Q) reaching a utilitarian equilibrium, and reinforcement learning. The goal of the Markov game is to overcome the, where multiple agents deplete a natural resource by purely maximizing their individual benefit.


# Issues Resolved / Approch Taken
Fixed the equation used in Dynamic Paper.
Using the Air polution, CO2 emission and population data. Action space now contains realistic values.
Instead of talking in terms of reduction. This work talks in terms of consumption. and still produces the same result.

# Variables
Consider a global CO2 amount: 4.025 (metric ton/capita) [actual amount in 1984]
Consider 3 agents.
LT: Group of countries with which show impact of CO2 emission in long run.
MT: Group of countries with which show impact of CO2 emission in medium run.
ST: Group of countries with which show impact of CO2 emission in short run.
Each agent has an action space i.e. the amount they are likely to produce in a year.
Each agent is also associated with a epsilon. It is sort of coefficient of randomness, higher the epsilon, higher is the chance to choose between the action_space else they will end up with the lowest. Since LT doesn't care much about environment therefore it has a higher epsilon. this value decreases overtime.
Each agent is also associated with a reward_factor. Larger the action chosen larger the reward. Since LT doesn't care much about environment therefore it has a lower epsilon.
Goal is to have a lower cumulative reward at the end of simulation.
Along with reward_factor, cost_of_action is a bias which is added in during calculation.

# Workflow
Each agent choses from action_space according to associated epsilon and get rewarded with ( reward_fator * action ) + cost_of_action
Each chosen action impacts Global_CO2_state
We run this simulation over and over again for 32 games, each game consists of 12 years discontinuous years.

# Creating Action Space
To measure the impact of CO2 emission, we took air pollution in account.

we sort the countries according to gradient of air pollution using k-means cluttering.



Take population data and total CO2 emission data. Divide them. Now you have action_space of each agent according to years.




# Policies
Three different policies emerge from training the agents in the simulation:

Synergistic: Agents will take path which leads to lowest cumulative reward.
Selfish Planning: Agents will take path which leads lowest reward at the end of all years.
Greedy: Agents will take path which leads to lowest reward in next year.



# Result
Global Trend According to World Bank:

[4.025, 4.03, 4.035, 4.038, 4.043, 4.046, 4.053, 4.056, 4.059, 4.064, 4.066, 4.069, 4.072, 4.075, 4.082, 4.085, 4.09, 4.097, 4.105, 4.112, 4.115, 4.118, 4.125, 4.133, 4.136, 4.143, 4.15, 4.153, 4.156, 4.159, 4.162]

Global Trend According to Synergistic Policy:

[4.025, 4.03, 4.035, 4.038, 4.043, 4.046, 4.053, 4.056, 4.059, 4.064, 4.066, 4.069, 4.072, 4.075, 4.082, 4.085, 4.09, 4.097, 4.105, 4.112, 4.115, 4.118, 4.125, 4.133, 4.136, 4.143, 4.15, 4.153, 4.156, 4.159, 4.162]

Global Trend According to Selfish Policy:

[4.025, 4.039, 4.049, 4.052, 4.064, 4.069, 4.082, 4.094, 4.099, 4.108, 4.111, 4.126, 4.143, 4.15, 4.158, 4.173, 4.178, 4.205, 4.221, 4.236, 4.251, 4.256, 4.273, 4.295, 4.307, 4.315, 4.332, 4.34, 4.342, 4.352, 4.355]

Global Trend According to Greedy Policy:

[4.025, 4.054, 4.083, 4.113, 4.133, 4.162, 4.191, 4.211, 4.24, 4.269, 4.298, 4.328, 4.357, 4.386, 4.415, 4.444, 4.473, 4.502, 4.532, 4.561, 4.59, 4.619, 4.648, 4.677, 4.707, 4.736, 4.765, 4.794, 4.816, 4.845, 4.875] 



# Conclusion


The results show that Synergistic policies achieve a lower per capita CO2 consumption, than selfish and greedy policies. In order to realize Synergistic policies, the current soft law approach on international climate policy needs to be enhanced by local commitments of smaller groups of countries and increased political and economic pressure. The policies of the modeled agents show that significantly reducing the global per capita CO2 consumption is not an option, but a rational thing to do, both from an economic and ecological perspective. Bringing these two worlds together, the cost of carbon emissions needs to be internalized in our economic systems, to incentivize both direct polluters and consumers to rethink their CO2 choices. Multi-agent reinforcement learning can help us to model and compare the economic and political dynamics and implications of new approaches to climate policy.

# Future Works
Some of the potential areas of improvement include but are not limited to: the number and diversity of agents, the cost and variety of mitigation measures, the different cost and impact of these measures depending on which period they are applied to, the state transition function, mapping the global state to its, mapping this impact to the agent‘s reward functions, the reward functions in general

Modelling the environment in a partially observable MDP which includes the additional mapping from observations to states, more sophisticated models to change the parameters depending on time

The use of different MARL algorithms depending on the model (such as Team-Q, WoLF-PHC, SG-SP, different variations of CE-Q or Nash-Q, to name just a few),

Accounting for models of cooperation between agents and finally, modelling real-time parallelization of and communication between.




# Acknowledgements
A special thanks to author of original paper Valentin Kahn and thanks the School of AI and its Director, Siraj Raval.
