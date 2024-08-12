In reinforcement learning, if the probability of the next state, given the current state and action, is independent of the history of interactions, we call memoryless property of [[Markov Decision Process, MDP | MDPs]] as the *Markov property*. 

The probability of moving from one state $s$ to another state $s$ on two separate occasions, given the same action $a$, is the same regardless of all previous states or actions encountered before that point.

But why do you care about this? Because most RL (and DRL) agents are designed to take advantage of the Markov assumption, you must make sure you feed your agent the necessary variables to make it hold as tightly as possible (completely keeping the Markov assumption is impractical, perhaps impossible).

For example, if you're designing an agent to learn to land a spacecraft, the agent must receive all variables that indicate velocities along with its locations. Locations alone are not sufficient to land a spacecraft safely, and because you must assume the agent is memoryless, you need to feed the agent more information than just its $x, y, z$ coordinates away from the landing pad.

But, you probably know that acceleration is to velocity what velocity is to position: the derivative. You probably also know that you can keep taking derivatives beyond acceleration. To make the MDP completely Markovian, how deep do you have to go? This is more of an art than a science: the more variables you add, the longer it takes to train an agent, but the fewer variables, the higher the chance the information fed to the agent is not sufficient, and the harder it is to learn anything useful. For the spacecraft example, often locations and velocities are adequate, and for grid-world environments, only the state id location of the agent is sufficient.


