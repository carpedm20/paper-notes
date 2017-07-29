## [beta-VAE: Learning Basic Visual Concepts with a Constrained Variational Framework](https://openreview.net/forum?id=Sy2fzU9gl)

Beta-VAE is a VAE with beta coefficient in KL divergence term where `beta=1` is exactly same formulation of vanilla VAE. By increasing beta, VAE loss its reconstruction power but the weighted factor force model to learn more disentangled representation than VAE. The authors also proposed disentanglement metric by training a simple classifier with low capacity and use it’s prediction accuracy. But the metric can be only calculated in simulator (ground truth generator) setting where we can control independent factors to generate different samples with controlled property.

## [DARLA: Improving Zero-Shot Transfer in Reinforcement Learning](http://proceedings.mlr.press/v70/higgins17a/higgins17a.pdf)

DARLA (DisentAngled Representation Learning Agent) is a RL framework to achieve better Domain adaptation. The final goal of adaptation is to learn two different task where state is different but action space is same and have similar transition and reward function. The training of DARLA is composed of two stage:

- Learn beta-VAE (Learn to see…)
- Learn policy network (of course Learn to act)

I had some interest on learning structured latent variable where the model can explicitly discriminate objects or parts in the state. This method will help us to make “Programmable Agents” in vision. The advantages of this method are:

- controllable and safe
- interpretable
- maybe more logical by enforcing the size of hidden vector (latent variable) to be small to make the state space smaller and make exploration easier.

The remaining challenges are how to learn explicit object in unsupervised manner and how to remove two step learning. This approach may make “pixel control” more applicable to various environment and can be considered as Engine learning (https://medium.com/@mark_riedl/automated-game-understanding-e8c9107c5ac2) or Inverse RL.

Another related paper in this domain is Attend, infer, repeat from (again) Deepmind.
