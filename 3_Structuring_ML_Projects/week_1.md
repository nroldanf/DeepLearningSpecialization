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

3. __Choosing train, dev, and test sets distribution__

