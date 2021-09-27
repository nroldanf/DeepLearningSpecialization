# Case Studies (Types of architectures)

Read and see other examples where convnets are applied for different tasks.

1. __Classical Networks__

_LeNet-5_

![LeNet-5](images/lenet5.png)

_AlexNet_

![AlexNet](images/alexnet.png)

__Num. Parameters__: 60k parameters.

__Note:__ Numbers only make sense if you take 227*227*3 input, instead of 224.

_VGG-16_

![VGG16](images/vgg16.png)

- Number of filters in each conv layer double the last layer filters (except for the last one) while the pooling layers reduce by a half the feature maps size.
- VGG-19 is a larger version of 16.

__Num. Parameters__: 138M parameters.

2. __ResNet__

ResNets are build of something called a _Residual Block_. Multiple residual blocks are stacked together to form a deeper network.

_Residual Block_: Pass the input much deeper into the network and add it. Now it follows a path called _short cut_/_skip connection_. 

![Residual Block](images/residual_block.png)

- __Main attribution of residual block__: Using residual blocks allows to train much deeper neural networks, really helping with vanishing and exploding gradient problems.

![ResNet](images/resnet.png)

- In reality, training error tends to increase when number of layers increase.
- When you add __residual blocks__/skipping connections this allows to keep decreasing the training error while number of layers increase.

__Why ResNets work?__

![Why](images/why_resnets.png)

- Identify function is easy for residual block to learn (because of the skip connections).
- But the goal is not to just to hurt performance but also improve performance, so the added hidden units can actually learned something that could be better than the identity function.
- Generally you used same convolutions in residual networks so you can add skipping connections without worrying about dimensions (adding between equal dimension vectors).
- When you have different dimensions in the output of a residual block you usually add another matrix to match the dimensions. It could be a matrix which parameters are learned or just a fixed matrix that implements zero padding (e.g for example, when you add a pooling layer that shrinks the dimension).

![Plain vs ResNet](images/plain_v_resnet.png)

3. __Networks in Networks and 1x1 Convolution__

_Why does a 1x1 convolution do?_

![Network in network](images/network_in_network.png)

_Use cases_

![1x1 Convs](images/conv_1x1.png)

- If you want to reduce/shrink the number of channels (e.g. from 28x28x192 to 28x28x32 using 32 filters of 1x1)

4. __Inception Module__

_Main Idea_: Try whatever combination of filter sizes at once, apply them, and stack the results together. This allows to implement wider convolutional neural networks.

- Some layers like the max pooling layer might need padding to be able to fit into the same dimensions.

![Inception Main Idea](images/inception_idea.png)

Computational cost is a problem, for that reason a 1x1 convolution is applied to reduce that producing first a bottleneck, without affecting the performance of the resultant network.

![Inception computational problem](images/inception_problem.png)

![Inception 1x1 conv](images/inception_conv_1x1.png)

The usage of 1x1 convolutions reduce the number of operations by 10x in this case.

__Inception Network__

Inception Network is just various inception modules stacked together, with some variations, but in general terms they followed the same pattern.

![Inception Module](images/inception_module.png)

Sides branches in inception network act like a regularization, preventing overfitting via ensuring that the outputs in hidden units are not too bad, taking those and trying to predict the output.

![Inception Module](images/inception_branches.png)

5. __MobileNet__



6. __EfficientNet__