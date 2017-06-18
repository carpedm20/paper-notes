## [Feature Control as Intrinsic Motivation for Hierarchical Reinforcement Learning](https://arxiv.org/abs/1705.06769)

It’s not a secret that people are extracting reward from features to make sparse-reward environment into dense one. The authors also incorporate this strategy in their work and use it to solve hierarchical RL. The model, the training is all simple.

In this work, the authors solve Montezuma faster than FuN with option framework (but without dynamic terminal condition). The agent is encouraged to change pixel or visual-feature given the option from meta-control and this dense feedback makes agent to learn basic skill under high sparsity.
