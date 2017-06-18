## [Learning to Reason: End-to-End Module Networks for Visual Question Answering](https://arxiv.org/abs/1704.05526)

### End-to-End Module Network (N2NMN)

Manual design of module

- possible input : 1 or 2 attention map, image feature, and textual vector for each module
- possible output : answer vocab

### Training

- estimation loss + REINFORCE ( + exponential moving average over loss as baseline)
- **Behavior cloning** (supervised initialization)
  - pre-training with KL-divergence between expert policy and agent policy + loss

## Test time

- beam search

### Thoughts

- Very similar to Justin’s work but poor performance
- Ronghang (+ Jacob) < Justin < DeepMind. why DeepMind (based on performance)
  - Pre-training + RL vs semi-supervised learning + RL vs RN
  - less # of programs
  - Attention vs no-Attention vs no-Attention
  - resize 480 x 320, VGG, 15 × 10 feature vs 244x244, VGG, 14 x 14 feature vs 128 x 128 + padding + (random crop + rotation), simple, 8 x 8
