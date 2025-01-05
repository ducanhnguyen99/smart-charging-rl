# Smart Charging Using Reinforcement Learning

## Project Overview

This project focuses on designing an intelligent charging system for electric taxi drivers using reinforcement learning. The goal is to optimize the charging strategy by adjusting the charging power every 15 minutes between 0 kW and 22 kW, ensuring the vehicle has sufficient energy for the day's demands while minimizing recharging costs. The energy demand is modeled as a stochastic variable following a normal distribution (μ=30 kWh, σ=5 kWh).

## Methodology

- **Markov Decision Process (MDP):**  
  - **State Space:** Defined by the State of Charge (SoC) and time steps within the 2-hour charging window (2-4 p.m.).
  - **Action Space:** Four discrete charging rates: 0 kW, 7 kW, 15 kW, and 22 kW.
  - **Reward Function:** Balances charging costs (modeled exponentially) and penalties for insufficient charge.

- **Environment Setup:**  
  - Developed a discrete event simulation environment using OpenAI Gym.
  - Implemented a Double Deep Q-Network (Double DQN) to learn optimal charging policies.

- **Model Training:**  
  - Trained the Double DQN agent over 5000 episodes using an epsilon-greedy strategy.
  - Hyperparameter tuning and environment adjustments were conducted to enhance performance.

## Key Findings

- **Model Performance:**  
  - The Double DQN model effectively optimized the charging strategy, predominantly selecting the medium charging rate (15 kW) to balance cost and energy sufficiency.
  - After 2000 episodes, the model stabilized, showing improved rewards and reduced penalties, though it consistently favored a single charging strategy.

- **Variance in Results:**  
  - Significant variance was observed in model performance across different data splits, highlighting the need for robust validation techniques.
  - Hyperparameter and environment tuning led to minor improvements but did not significantly diversify the agent's actions.

- **Challenges:**  
  - Balancing charging costs with penalties for unmet energy demands proved difficult, often resulting in simplistic charging policies.
  - The model's tendency to favor a single charging rate limited its adaptability to varying conditions.

## Conclusion

The study demonstrates that reinforcement learning, specifically Double DQN, can be utilized to develop intelligent charging strategies for electric taxis. While the model achieved basic optimization by consistently selecting a medium charging rate, further refinement is necessary to create more nuanced and adaptable policies. Future work should explore more complex model architectures and refined reward structures to enhance the agent's decision-making capabilities.
