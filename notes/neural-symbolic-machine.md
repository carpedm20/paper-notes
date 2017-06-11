## [Neural Symbolic Machines: Learning Semantic Parsers on Freebase with Weak Supervision](https://arxiv.org/abs/1611.00020)


This paper is GOOGLE-scale paper so it’s usually not practical for us. However they also share some valuable experience to make another troublesome RL agent trainable (but they use extensive computing power).

The problem the authors tackled is learning a λ-program to do QA with freebase data. (tbh I didn’t understand what λ-program is but its should be just a set of program including argmax) Example query is “Largest city in the US”.

Neural Symbolic Machine (NSM) is nothing but a seq2seq agent with attention and additional memory to store variable. Unlike NTM, the value of external memory is not a vector but a reference for an entity in freebase. Writing (actually just appending) is executed after reading a query or executing a program (query for freebase). So the authors connect their model with NTM, NPI and pointer network (because it’s dynamic pointing mechanism to variable memory).

Because there is a step that accessing freebase data with query, the model has non-differentiability so here comes our REINFORCE! Reward is F1 score between candidates and answer. Okay, because the answering procedure is first query lots of possible candidates and reducing them so that’s why F1 is possible. This is why the problem is weak supervision.

### What they did is:

- beam search for gradient estimation, which use top-k action sequences to reduce variance of the gradient
- EM training: first train sub-optimal agent with Expectation Maximization (EM) and get so-called gold program which is a possible sub-solution for the problem
  - they use top-100 beam search for this
  - they give +0.1 probability when RL (which represents the small action space and short episode) to boost the initial convergence
- RL training: authors called this Augmented REINFORCE (augmenting prob of estimation)
- they reset θ because agent with EM get stuck in local optimum
- using 100 workers (and 50 freebase servers) to overcome bottleneck occurred by the network or search computation
- curriculum learning based on # of required command to get answer

### My thoughts

- EM training first maybe one useful trick to train program induction models like NPI with no-supervison
- But this work use F1 reward which is non-sparse. We may need to think about reducing candidates or giving non-sparse reward with candidates.
