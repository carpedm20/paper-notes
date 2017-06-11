## [Learning Neural Programs To Parse Programs](https://arxiv.org/abs/1706.01284)


This work tries to train a parser with NPI like program. They used complicated reward function as our tangram project (but way more complicate to train a program with input/output (code, parsed tree) only). They applied LL parser concept in computer language parser and tries to build Abstract Syntax Tree (AST) which is also used in A Syntactic Neural Model for General-Purpose Code Generation (https://arxiv.org/pdf/1704.01696.pdf).

Sadly, model, reward, training algorithm is complicated to achieve 100% train accuracy without strong supervision. To get 100% valid accuracy and to reduce the possible search space while training, they use ground truth parser to reduce the # of candidates. But Section 5.2 and Appendix C, which are training details, are (maybe…) useful ideas.

### Weakly supervised learning idea

If a execution trace is given, training turns into a supervised learning to predict correct argument.

### Training details

Training model with weak supervision is hard due to the fact that the possible valid execution traces are not unique for a given input-output example. Below is algorithm that I understood based on the paper. I strongly think that the authors should include algorithm like this in the paper..

# 1. valid candidate instruction

    for i in range(M_2=10000):
        x, y = get_data()
        tentative ground truth = random sample with exploration constant

      # to check whether sampled trace is wrong, or only the arguments are predicted wrongly
      for j in range(M_1=20): 
            do weakly supervised learning with tentative ground truth
            keep a **set of candidates** that produce correct output

      if no candidates found:
            revert model parameter
            continue

      if i % M_3 (=2000) and lesson > 1: # to escape from a sub-optimal model
          reset model weight learned from the previous lesson

    # they said # of candidate *instruction type traces* is usually 3 ~ 5

    # 2. a satisfiable specification
    while True:
        x, y = get_data()
        trace = sampled from $d$ candidates with prob $\theta \in \mathcal{R}^d$

        do weakly supervised learning

I don’t fully understand the last *2. a satisfiable specification* part but I guess they use candidate to make problem supervised learning or something
