# 

## Error analysis

This gives you a sense on which approach to pursue when you are looking to improve performance.

If you are trying to develop an algorithm that make what humans do, and if its not yet at the performance of a human, then manually examining errors that your algorithm is making, can give you insights in what to do next.

Is worth an effor to fix misclassification errors?

__Idea__

1. Get ~100 mislabeled dev set examples.
2. Count up how many are the problematic label.

- Analyze the proportion of the misclassified label to see what will happen if you design something to better classify this label with the general error. Depending on this, you can decide if spending time on improving performance for this label.

The key point is deciding in which direction go to do the effort actually worth.

You can evaluate multiple ideas en parallel, using kind of spreadsheet analysis and commenting on describing the example that was misclassified. With this, you can decide which is your main problem and in what to focus. With this, different persons on a team can focus on different things.

You can add more columns to this spreadsheet to give you an estimate on how it behaviors on this category of error.

1. __Cleaning Out error analysis__

Sometimes examples are mislabeled, which can affect on how the functionn is mapping x to y.

Deep Learning algorithms are robust to this kind of random errors if the total percentage of errors is not too high, but less robust to systematic errors (e.g. labeled white dogs as white cats).

You can add this incorrectly labeled as a column to error analysis.

2. __Build your first system quicly then iterate__

Build your first system quickly then iterate.

There are a lot of different ways to improve your system. Build initial system quickly. Don't overthink, do something simple first, quick and dirty don't worry.

Use Bias\Variance analysis and Error Analysis to prioritize next steps.

## Mismatched training and dev/test set 

1. __Training and testing on different distributions__

When you train and test with different distrivutions there are different practices to mitigate this.

e.g Cat example app. Data from webpages and data from mobiles app photos. The app will be running on mobile, so you care about performance with the former distribution.

- Option 1: Randomly shuffle it and split them into train, dev and test sets. Not recommended.
- Option 2: Train set will include some images from mobile app and dev and test sets are all mobile photos. This will in the long term give better performance althougt you have different distributions.

e.g. Speech recognition example. Voice activation in car.

- Training, gather data from the past applications related to speech recognition. For dev/test set, get dataset specific for the application, the one you actually care about.

- You can put some of the data that you care specifcally into the train set, or just put it in the dev and test sets.

2. __Bias and variance with mismatched data distributions__

The way of analyzing bias and variance changes when your training set come from different distribution that your dev and test set.

When analyzing the error that you got from train and dev sets, if the data came from different distributions you can't actually say that the performance is better, because the data might be more easy to classify accurately.

- Define a new piece of data can called __training-dev set__, same distribution as training set but not used for training.

To carry out error analysis, measure the training-dev set error too.

Key quantities to look at for assesing bias, variance and mismatching:

- Human level error
- Training set error
- Training-dev error
- Dev set error
- Test set error

Comparisons between these will tell us is there is avoidable bias, variance, and data mismatch, or if there is overfitting.

There are some cases where training set tends to be much harder than dev and test sets.

3. __Addressing data mismatch__

- 

## Learning from Multiple Tasks

1. __Transfer Learning__

Take knowledge of one task and use in a similar task. 

e.g. in image classification you can take the pretrained feature extractor and train a new classifier or output node/nodes with new data. 

Couple of options:

- __Pretraining:__ Keep paremeters freeze and just train the classifier.
- __Finetuning:__ Train the full network (fine-tuning).

**When to use it?** -> A lot of data from problem you are transfering from but few for the problem you are transfering to. e.g. COCO dataset to radiology or medical dataset.

- Task A and Task B have the same input.
- You have a lot more data for Task A than Task B.
- Low level features from Task A could be helpful for learning Task B.

2. __Multi-task Learning__

__Multi-label classification__, e.g. multiple objects can be identified in an image at the same time. Train one neural network to detect all objects (better performance) or train one neural network per object. 

When makes sense?: 

- Training on a set of tasks thaat could benefit from having shared low-level features.
- Amount of data you have for each task is quite similar. Help other tasks with similar data.
- Can train a big enough neural network to do well on all the tasks.

## End-to-end Deep Learning

1. __What is end-to-end deep learning__

Data processing or learning processing systems that requires multiple stages of processing that can be replaced with a single neural network.

e.g Speech recognition

Traditional pipeline approach: (X) Audio -> Extract Features -> ML to identify phonemes -> Words -> Transcription (Y)

- With 3000h of audio works well

DNN implementation: Audio -> Transcription

- With 10.000h to 100.000h start working better.

e.g. Face recognition

Decompose the task in easier tasks allows to have a better performance, instead of trying to learn the full task. Also, might be more likely to have more data for each subtask that for the full task.

For doing end-to-end dl you might need a lot of data for doing well.

Sometimes, breaking the task into smaller ones that does not require too much data and are easier to solve and learn is better. End-to-end deep learning is not a silver bullet.

2. __Wheter to use end-to-end deep learning__


