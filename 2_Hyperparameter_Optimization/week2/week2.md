# Week 2

## Optimization Algorithms

Train models with fast optimization algorithms.

1. ___Mini-Batch Gradient Descent__

___Batch vs Mini-batch Gradient Descent__

Vectorization allows you to efficiently compute on m examples. But what if m = 5M examples?

Mini-batch: Batches of 1000 each (5000 mini-batches).

__Batch__: Process entire train set all at the same time.
__Mini-batch__: Process mini-batches of your training set once at a time (forward propagation -> compute cost -> backward prop).

When having large training sets, mini-batch gradient descent runs much faster that normal batch gradient descent.

2. __Understanding Mini-batch Gradient Descent__

Mini-batch gradient descent cost function throught iterations is not a smooth curve but instead a noisier curve. This might be because one of the mini-batches is more easy to learn than the other mini-batches.

![Mini-batch learning curve](images/mini_batch_learning.png)

One of the __parameters__ that you need to choose is the __mini batch size__.

If mini-batch size = m -> Batch gradient descent. Really smooth curve and fast learning but too long for iteration.
If mini-batch size = 1 -> Stocastic gradient descent (every example is it own mini-batchs). Really noisy curve and lose speed-up obtained for vectorization.

In practice you should use somewhere in between (not too big or small) -> Faster learning and can also make progress without needing to wait to process entire training set.

__Choosing mini-batch size__

If training set is small (e.g. 5000) -> Use batch gradient descent.

Typical mini-batch sizes like power of 2: 64, 128, 256, 512, 1024

Make sure your mini-batch fit in your CPU/GPU RAM memory.    

3. __Exponentially Weighted Averages__

In order to use faster optimization algorithms than mini-batch gradient descent, you should understand __Exponentially Weighted Averages__ which is a key component on several optimization algorithms used to train DNN.

![Exponentially weighted Averages](images/exponentially_weighted_averages.png)

4. __Understanding Exponentially Weighted Averages__

5. __Bias Correction in EWA__

6. __Gradient Descent with Momentum__

Compute an EWA of your gradients and then use that gradients to update the weights.