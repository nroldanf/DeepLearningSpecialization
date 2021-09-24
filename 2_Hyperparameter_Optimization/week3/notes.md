# Hyperparameter Tuning

## Tuning

1. __Tuning Process__

- __alpha__ (Most important)
- __beta (momentum)__ (2nd)
- beta1, beta2, epsilon -> never actually really tuned
- num. layers (3rd)
- __num. hidden units__ (2nd)
- learning rate decay (3rd)
- __mini-batch size__ (2nd)

__How to tune them?__

- __Random sampling__: Don't use a grid, choose them randomly. This allows to search over different values of every dimension, you have more chance to look for different combinations.
- __Coarse to fine__: When sampling different combinations of values you found that certain points worked best and points around it. You might zoom in into that region and sample more densely.

2. __Using scale and appropiate scale to pick hyperparameters__

- Uniform distribution (e.g. 1 to 4 when looking for the n_layers)
- Searching on log scale (e.g. for a range 0.0001 and 1)
- For hyperparameters for EWA, better to look in log scale (log scale)

3. __Hyperparameters tuning in practice: Panda vs Caviar__

- Babysitting one model: when you don't have enough computing power, trying to make this one an only work __(Panda)__
- Train different models in parallel: You have a lot of computing resources, choose the best __(Caviar)__

## Batch Normalization




