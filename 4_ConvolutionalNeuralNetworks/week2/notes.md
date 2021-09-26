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
- When you add __residual blocks__ this allows to keep decreasing the training error while number of layers increase.

3. __Inception__



4. __MobileNet__



5. __EfficientNet__