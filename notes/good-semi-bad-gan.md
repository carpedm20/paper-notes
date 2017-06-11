## [Good Semi-supervised Learning that Requires a Bad GAN](https://arxiv.org/abs/1705.09783)

This paper was started from the question why semi-supervised learning from https://arxiv.org/abs/1606.03498 works well. The previous paper suggested a novel semi-supervised learning by adding additional label for fake/real and try to estimate the output of generator as this new label.

Now the question is, why discriminating generator output to a fake/real class helps model to make better prediction? The answer, in short, is the classifier is forced to discriminate the samples from boundaries between classes which are the output from generator. This can be considered as a multi-task problem, one for training discriminator and the other for training classifier. By solving multi-task problem, the model can learn better representation which can discriminate the samples from vague boundaries between classes.

Therefore, the authors suggested to train generator to minimize KL divergence between the generator distribution and a target distribution which assign high probabilities for data points with low probabilities in the true distribution which can lead to train a complement generator.

At first, it was quite hard for me to imagine why properly bad GAN helps to achieve good semi-supervised learning but this paper explain this phenomenon pretty well.
