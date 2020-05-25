---
title: "Cyclical Learning Rates for Training Neural Networks"
categories:
  - Paper Summary
tags:
  - paper
  - lr policy
  - hyperparameter
  - cyclic lr
---


## Paper
- Title : Cyclical Learning Rates for Training Neural Networks
- Authors : Leslie N. Smith
- Citation/Link:	[arXiv:1506.01186](https://arxiv.org/abs/1506.01186) [cs.CV]
- Subjects:	Computer Vision and Pattern Recognition (cs.CV); Machine Learning (cs.LG); Neural and Evolutionary Computing (cs.NE)
- First proposed : Jun, 2015

## Summary

- What
  - Cyclic Learning rate policies to improve network performance.
  - reduces guess work in setting the learning rates and no. of training epochs
  - Better than adaptive learning rate strategies as this have no additional computation requirements

- How
  - Cyclic LR - Change LR cyclically throughout the training phase over some number of epochs.
  - Cyclic LR is able to bring network out of saddle point, one of the major reason for poor network performance
  - Use LR range test to determine boundaries for the cycle
  - We chose the cycle boundaries such that network is trained over near optimal learning rate throughout.
  - Different LR policies can be tried based on the dataset and architecture

- Results
 - Training performance improved
 - Better LR scheduler

  <!-- - [x]  Theorical effects
  - [x] Practical effects -->


## Rough chapter-wise notes

##### 1. Introduction
- Acknowledges that DNN are SOTA in many fields but training a deep NN is a difficult optimization problem.
 - Learning rate(LR) is a Hyperparameter. If learning rate is too small then network convergence very slowly and too large a learning rate then it diverges

- Conventionally LR is monotonically decreased during training, but the paper demonstrates that varying LR is beneficial overall and proposes to let LR vary cyclically within a range.

- Eliminates need to perform various experiments(i.e. Hyperparameter tuning) to find best value for LR and schedule ***with essentially no additional computation*** unlike adaptive LRs

- Demonstrated with different datasets and different SOTA networks


##### 2. Related work
- > The book “Neural Networks: Tricks of the Trade” is a
terrific source of practical advice. In particular, Yoshua
Bengio discusses reasonable ranges for learning rates
and stresses the importance of tuning the learning rate.
- > Adaptive learning rates can be
considered a competitor to cyclical learning rates because
one can rely on local adaptive learning rates in place of
global learning rate experimentation but there is a significant computational cost in doing so. CLR does not possess
this computational costs so it can be used freely

##### 3. Optimal Learning Rates
###### 3.1 Cyclical Learning Rates(CLR)

- min and max boundaries are set and LR is allowed to vary cyclically between these. Multiple functions have been tried like linear, parabolic, sinusoidal to vary the LR and all of them gave similar results. These functions and corresponding forms are referred to as ***Learning rate policies***. Linear function is discussed in the paper as it is the simplest function. _Linear fn. gives triangular window (linearly increasing then linearly decreasing)_

> "Experiments with numerous functional forms, such as a triangular window (linear), a Welch window (parabolic) and a
Hann window (sinusoidal) all produced equivalent results
This led to adopting a triangular window (linearly increasing then linearly decreasing), which is illustrated in Figure
2, because it is the simplest function that incorporates this
idea. The rest of this paper refers to this as the triangular
learning rate policy."

![Fig 2. Triangular LR Policy](https://github.com/hemanth346/hemanth346.github.io/tree/master/assets/images/cyclic_lr/triangular_lr.png "Triangular LR Policy")

- Intuition behind CLR working is due to the saddle points. _We decide the LR boundaries such that optimal learning rate is between the bounds, hence the network is trained with **near optimal learning rate** throughout_. Saddle points, a major problem during optimization as referred below, can be overcome when a relatively increased LR is used

> "An intuitive understanding of why CLR methods
work comes from considering the loss function topology.
Dauphin et al. [4] argue that the difficulty in minimizing the
loss arises from saddle points rather than poor local minima.Saddle points have small gradients that slow the learning
process. However, increasing the learning rate allows more
rapid traversal of saddle point plateaus."

- Two other LR policies are proposed
  - **Triagular2** : LR difference between boundaries is cut in half after every cycle
  - **exp range** : Boundary value declines by an exponential factor after every iteration

> "In addition to the triangular policy, the following CLR
policies are discussed in this paper:
1. triangular2; the same as the triangular policy except the learning rate difference is cut in half at the end
of each cycle. This means the learning rate difference
drops after each cycle.
2. exp range; the learning rate varies between the minimum and maximum boundaries and each boundary value declines by an exponential factor of
gamma^iteration."

---

###### 3.2. How can one estimate a good value for the cycle length?

- _Cycle or cycle length is the number of iterations until the learning rate returns to the initial value._
- _stepsize is half of the cycle length and is used as input_
- Experiments shows that often 2-10 times no. of iterations in an epoch is a good stepsize(i.e. half cycle length)
> For
example, setting stepsize = 8 ∗ epoch with the CIFAR-10
training run (as shown in Figure 1) only gives slightly better
results than setting stepsize = 2 ∗ epoch.

 > For example,
CIFAR-10 has 50,000 training images and the batchsize is 100 so an epoch = 500 iterations (50,000/100)

- Experiments show that training to be planned such that at the end of training (i.e. no of training epochs), the LR policy has completed at least 3 cycles(i.e. 6*stepsize)
> Experiments show that replacing each step of a constant learning rate with at least 3 cycles trains the network
weights most of the way and running for 4 or more cycles
will achieve even better performance.

- And the training has to be stopped when LR is at min value. i.e at the end of cycle or start of cycle. This can be calculated based on the stepsize set
> Also, it is best to stop
training at the end of a cycle, which is when the learning
rate is at the minimum value and the accuracy peaks.

###### 3.3. How can one estimate reasonable minimum and maximum boundary values?
- _As already discussed in 3.1, we aim to train the network with **near optimal learning rate** throughout. To achieve that we have to find a boundary that has the optimal LR_. It is found using ***LR range test***

- The network is trained for limited no. of epochs with linearly increasing LR within given range. Once done, we plot the accuracy(loss) vs LR graph and take the
 - *lower boundary/base_lr as the point where accuracy has started increasing fastly (or loss started decreasing)* and
 - *upper boundary/max_lr as the point when accuracy is high/started to drop/fluctuating (loss is minimum or started to increase/fluctuating)*

- Another approach is the consider max_lr using above strategy and decide base_lr as one-third or one-fourth the value of max_lr
>  the learning rate will increase linearly from the minimum value to the maximum value during this short run. Next, plot the accuracy versus learning
rate. Note the learning rate value when the accuracy starts to increase and when the accuracy slows, becomes ragged, or starts to fall. These two learning rates are good choices for bounds; that is, set base lr to the first value and set max lr to the latter value. Alternatively, one can use the rule of thumb that the optimum learning rate is usually within a factor of two of the largest one that converges [2] and set base lr to 1/3rd or 1/4th of max lr.

![Fig 3. LR Range Test ](https://github.com/hemanth346/hemanth346.github.io/tree/master/assets/images/cyclic_lr//lr_range_test.png "LR Range Test")


> Whenever one is starting with a new architecture or
dataset, a single LR range test provides both a good LR
value and a good range. Then one should compare runs with a fixed LR versus CLR with this range. Whichever wins can be used with confidence for the rest of one’s experiments
