
## Implementation Summary 

In this lab, first-visit Monte Carlo control was implemented using an ε-soft policy in the Blackjack-v1 environment from Gymnasium. The agent interacted with the environment by generating complete episodes, storing state-action-reward trajectories in Python lists, and computing returns using backward iteration. The Q-values were updated incrementally using first-visit updates to ensure efficient learning.

The experimental setup consisted of training the agent over 500,000 episodes with a discount factor of 1.0. An initial ε value of 0.1 was used for exploration, which decayed gradually to a minimum of 0.01. Performance was evaluated using smoothed learning curves and 3D visualizations of the value function for both usable and non-usable ace conditions.

## Key Results & Analysis

##Learning Performance

The learning curve demonstrated a clear improvement in the agent’s performance over time. Initially, the returns fluctuated significantly due to the high exploration rate enforced by the ε-soft policy. As training progressed and ε decayed, the variability in returns decreased, and the curve stabilized. This behavior aligned with theoretical expectations from Sutton and Barto (Chapter 5), where Monte Carlo methods gradually converge as more episodes are sampled.

The smoothed curve revealed that the agent’s performance plateaued after a large number of episodes, indicating convergence toward a near-optimal policy. This confirmed that sufficient exploration combined with incremental updates allowed the agent to learn effectively without requiring a model of the environment.

## Value Function Insights

The 3D value function plots provided deeper insights into the agent’s learned strategy. States with higher player sums (e.g., 20 or 21) consistently showed positive value estimates, reflecting a higher probability of winning. In contrast, lower player sums resulted in negative values, indicating a higher risk of losing.

The presence of a usable ace significantly improved expected returns across many states. This observation aligned with Blackjack strategy principles, where a usable ace provides flexibility and reduces the likelihood of busting. These findings supported the theoretical understanding that value functions represent expected returns under a given policy.

## Policy Behavior

The extracted policy closely resembled standard Blackjack strategy. The agent learned to “stick” when the player sum was high and “hit” when the sum was low. In intermediate states (12–16), the decisions depended on the dealer’s visible card, demonstrating that the agent had learned nuanced, state-dependent behavior.

This result reflected the effectiveness of ε-soft policies in ensuring sufficient exploration. As described in Sutton and Barto, maintaining non-zero probabilities for all actions prevented premature convergence to suboptimal policies.

## Effect of Hyperparameters

The choice of ε and its decay schedule played a critical role in learning performance. A higher ε initially encouraged exploration, while gradual decay allowed the agent to exploit learned knowledge over time. If ε decayed too quickly, the agent risked insufficient exploration; if too slowly, convergence was delayed. The selected parameters provided a balanced tradeoff.

## Key Takeaways

Overall, the results demonstrated that Monte Carlo control is a powerful approach for solving episodic reinforcement learning problems. The lab highlighted the importance of exploration strategies, efficient return computation, and sufficient training duration. It reinforced the theoretical concepts from Sutton and Barto while providing practical insights into implementing experience-based learning systems.
