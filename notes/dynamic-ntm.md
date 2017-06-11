## [Dynamic Neural Turing Machine with Soft and Hard Addressing Schemes](http://arxiv.org/abs/1607.00036)

The authors suggested variations of NTM and the main difference is

1. Remove location-based addressing and add Least Recently Used (LRU) memory addressing
2. Add one additional memory location, which is used as No-op to skip reading or writing (but they don’t include any empirical study about this)
3. Multi-step addressing like memory network’s 3-hop (but again no empirical study or detailed example run)
4. Trained discrete attention (w/ entropy regularized REINFORCE) NTM with several tricks
  - gradient variance reduction with input-dependent baseline (R-v(x)), {global baseline, variance normalization} with moving average
  - huber loss
  - curriculum learning : use sum of continuous and discrete weight but annealing the ratio of continuous weight
  - To avoid sub-optimal when using RNN controller, which only use RNN ignoring memory:
    - read/write consistency regularizer to avoid “consistently reading empty memory”
    - next input prediction in bAbI task (I think this is somewhat related to remembering name or object)
  - So, loss = cross_entropy + REINFORCE + entropy regularizer + r/w consistency regularizer + next input prediction

However, their ablation test doesn’t include how each of these tricks are helpful to make discrete attention trainable. Also, they don’t show any informative experimental results to understand how their new NTM works differently compared to previous NTM. Lastly, even their contribution is make discrete NTM trainable but still it’s performance is poor than soft attention in most of the experiments.


### My thoughts

I found that reviewers complaining about complicate model and loss and poor performance.

However, their model is not that different from MANN meta (one-shot) learning paper and it’s far simpler than DNC. Maybe most of the people may feel NTM-like model to be complicared.

Another thing people complained was complicated loss function. But I could feel their pain to make NTM working on toy data (bAbI) with our troublesome REINFORCE.. I can still see lots of typo in the paper..
