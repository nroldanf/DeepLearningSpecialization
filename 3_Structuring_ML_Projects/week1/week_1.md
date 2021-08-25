# ML Strategy

Why is important to have a strategy?

Different ideas come when trying to optimize model performance:

- Collect more data
- Collect more diverse training set
- Train for longer span 
- Try Adam or another optimization algorithm
- Try bigger network (when deep learning is being used)
- Try different regularization methods
- Try different architectures

There are too many ideas that could take too much time to test so... YOU HAVE CHOOSE WISELY, TIME IS VALUABLE WHEN WORKING ON A PROJECT!

## Orthogonalization

What to tune in order to improve some metric?

- TV: Design controls to tune one things dependent of one variable, and to affect just one parameter of the tv.

Fit well on training set (human level performance)
    - Bigger network
    - Different optimizers
Fit well on dev/validation set well on cost function
    - Regularization
    - Bigger training set
Fit well on test set on cost function
    - Bigger dev set (if does well in dev set but not in test set)
Performs well in real world
    - if doing well on test set but not in real world -> change cost function or change dataset (dev/test set distribution is not set correctly)

There are some "knobs" which tuning ends affecting different things and not only one, for example early stopping would affect performance on training set and validation set.

## Setting the goal

1. __Set a single number evaluation metric__

In cat classifier:

__Precision:__ Of examples that were recognized as cats, what % is actually a cat.

__Recall:__ Of all images that all actually cats, what % are correctly recognized.

With 2+ evaluation metrics is difficult to know which is better. 

__Solution__: Add them into one metric if possible, in this case __F1 Score__, which is a average of both (harmonic mean).

__Key Idea__: Having a single number metric, speed up iteration.

Imagine having that classifier but in different geographies:

- Different variants of the algorithm are deployed over the world, and for choosing the best one, it's better to have a single number, so can take average among the differents countries and choose based on it.

2. __When it's not easy to condense everything into a single number__

In cat a classifier that has a single metric and running time.

You can have a __optimizing metric__ and a __Satisficing metric__.

- Optimizing metric: Maximize the accuracy of the classifier.
- Satisficing metric: Have at least certain running time latency.

For N metrics:
- 1 optimizing metric
- N-1 Satisficing metric.

3. __Choosing train, dev, and test sets__

Set up datasets dev (hold-out cross validation set) and test for efficiency. 

Find a way so both sets come from the same distribution. 

You might spend months iterating to do well on the dev set, only to get surprised how bad you are performing on test set, all this because you are using different distributions.

Randomly shuffle the data all mixed together and get your dev and test sets from all the data.

__Guideline__: Choose a dev and test set to reflect data you expect to get in the future and consider important to do well on. And both sets, come from the same distribution.

4. __Choosing the size of dev and test sets__

This depends on the full dataset size. If dataset if too large (millions), the percentage is lower (1-5% should be enough for dev and test sets).

Set you test set to be big enough to give high confidence in the overall performance of your system. 

Recommended to have a both, dev and test sets or have a dev set big enough to be sure you are not overfiiting.

5. __When to change evaluation metrics?__

Misprediction: Wrongly classifying, even if the metric is better for another algorithm. 

Possible solutions: Add weighting parameters to mitigate misclassification.

You can separate this changing problem into 2 steps:

First: Define a new metric that better captures what is intended (place the target).

Second: Worry about how to do well on this metric (how to shoot to the target).

Even if you can define the perfect evaluation metric, choose a good one quicly and later change it at other time, so you can improve team iteration.

## Comparing to Human-level performance

__Why human level performance?__

Deep learning advances are working much better to the point that are competitive with human-level performance.

As time progress, the performance comes near but never surpasses a theoretical threshold called "Bayes Optimal Error" think of best possible error. 

There is no way of a function that maps x to y to surpasses this threshold, e.g. for speech recognition, some audio is so noisy that is practically impossible to tell what is being said.

In general, human level performance is near Bayes optimal error thresh, so the advance after surpassing human-level performance is slow.

So long as ML is worse than human, you can:

- Get labeled data from humans.
- Gain insight from manual error analysis: why did a person get this right?
- Better analysis of bias variance.


__Avoidable Bias__

Human level performance can tell you how well you want your algorithm to do on training set.

When you can find a huge gap between human-level performance and training error: __Focus on bias__

When you can't find a huge gap between human-level performance and training error, __Focus on variance__, reducing the difference between the training error and the dev error.

You can think of human-level error as a proxy for Bayes error.

__Understanding Human-level performance__

You can see human-level performance as a proxy for Bayes error.

Suppose medical image classification:
- Typical human: 3% error
- Typical doctor: 1% error
- Experienced doctor: 0.7% error
- Team of experienced doctors: 0.5% error.

What is human-level error in this case?: The optimal error would be according of what do you want to achieve; to surpass single human or a groud of experienced ones.

Compare between avoidable bias (gap between human-level performance and training error performance) and variance (gap between performance in dev and train sets) so you know which to choose as proxy. So you know, in which to focus, if bias (bigger models and more data) or variance (regularization tecniques) reduction tecniques.

Instead of comparing error to 0%, compare to Bayes error (human-level performance), to try to understand how big our bias is.

__Surpassing Human-level performance__

When you surpass human-level performance, it's not clear on how you can get better.

It's more easy to find cases of this on non-natural perception tasks (e.g. vision, hearing, understanding language, etc.).

- Loan approvals
- Logistics
- Product recommendations

But also, in natural perception tasks you can find examples, althought it was harder to surpass it.

__Guidelines on how to improve you model performance__

Two fundamental assumptions of supervised learning:

1. You can fit the training set very well (not too bad avoidable bias)
    - Bigger network
    - Train longer or use better optimization algorithms
    - NN architecture/hyperparameter search

2. The training set performance generalizes pretty well to the dev/test set.
    - Regularization (L2, Dropout, data augmentation)
    - Getting more training data (generalizes better)
    - NN architecture/hyperparameter search
