## [FeUdal Networks for Hierarchical Reinforcement Learning](http://arxiv.org/abs/1703.01161)

### Main contribution

- To avoid loosing the semantic meaning of the goal of manager, use different **policy gradient** (PG) from the PG of worker.
- Encourage manager to predict advantageous direction in latent space and give intrinsic reward to worker to follow the direction
- Goal : advantageous direction in the latent state space at a horizon $c$.

$\delta g_t = A_t^M \delta_\theta d_cos(s_{t_c} - s_t, g_t(\theta))$

where

$A_t^M = R_t - V_t^M(x_t, \theta)$

and $\delta \pi_t \ A_t^D \delta_\theta log \pi(a_t|x_t;\theta)$.

- Used dilated LSTM to preserve the memories for long periods

### Difference between option framework

- Option learning:
  - bottom level : option, a sub-policy with terminal condition
  - top level : policy-over-options

- Feudal framework:
  - bottom level : action
  - top level : provide meaningful & explicit goal for bottom level
  - sub-goal : a direction in latent space

### Misc

- $c=r=10$
- cut the trajectory and run back-propagation through time (BPTT) of 400 steps
- temporal resolution: precision of a measurement with respect to time
