# Convolutional Neural Networks

## Computer vision

You can borrow some of the ideas of computer vision architectures for other problems for example in  natural language processing. 

Types of applications with DL in computer vision are:

__Image classification__

__Object Detection__

__Neural Style Transfer__: Content and Style combination.


Some of the challenges:

- Big inputs (n_channels * width * height): This means that parameters in feed forward neural network can get too big too handle.

## Edge Detection

Convulution operation is one of the most fundamental operation in computer vision deep learning.

In a neural network you go from low level features (edges) to more complex features in the images until you got to classification layer.

Multiply a filter/kernel by an image using the convolution operation. Sliding element-wise product and add them up, this gives you a new pixel, and so, ending up with a new image, called feature mapping.

In all dl frameworks you can find this simple operation as 2D Convolution.

Using different filters allows you to find different kind of edges (vertical and horizontal). Others are:

- Sobel Filter
- Scharr Filter

In convolutional neural network you are looking to learn this weigths or values of the kernel using an iterative process like Backpropagation/Gradient Descent that allows you to detect the features that are interesting for your task (e.g. classification).

## Padding

You can add some variation to the convolutional operation such as padding.

If you convolve an nxn image with a fxf kernel, you end up with a filter map of (n - f+1) x (n - f+1). You can only do this convolution a few times before result image can't shrink anymore.

Problem with this slidding approach is that pixels that are on the edeges of the image are less used for the result, so you are throwing away some information about the image.

Problems of simple convolution operation:

- __Shrinking output__
- __Throwing away informaton ffrom the edges__

In order to fix them the __solution is__: Before doing convolution, pad the image with zeros. Less information loss from the edges is reduced.

So the calculation of output image dimensions stay like:

(n + 2p - f+1) x (n + 2p - f+1)

Where:

p = padding
n: widht and height
f: kernel dimension

In terms of how much padd to add there are some common choices:

- __Valid convolution__: nxn * fxf -> (n - f+1) *  (n - f+1)

= __Same convolution__: Pad so that __output size = input size.__ That implies that p = (f - 1) / 2

__Note__: By convention in computer vision filter size is usually odd (3*3, 5*5, 7*7)

## Strided Convolution

Step of the sliding element-wise multiplication (convolution).

floor((((n + 2p - f) / s) + 1) * (((n + 2p - f) / s) + 1))

Where:

n: widht and height of the image 
f: kernel dimensions
s: strides
p: padding

floor: round the number to the nearest integer.

## Cross-correlation vs Convolution

In __convolution__, you flip the kernel with respect to horizontal and vertical axes, then multiply element wise.

In __cross-correlation__, you don't flip the kernel.

In Deep Learning, the operation called convolution is defined as cross-correlation in signal processing and mathematics but by convention the operation is called convolution.

Omitting this flipping step simplifies things and make things works as well.

## Convolution over volume

### RGB Images

Convolve images of widht * height * n_channels by a kernel of n * n * n_channels, resulting in just one image.

Can use __multiple filters__ to detect different kind of features inside the image, ending with a number of resulting images equal to the number of filters used.

## Convution Layer

Do for every filter:
    Multiply by filter -> Add bias term -> Introduce non-linearity (e.g. ReLU).
    Stack

Number of parameters in a layer equal to: 

((width * height * n_channels) + 1) * n_filters

## Pooling Layer

NO PARAMETERS TO LEARN is just a fixed function.

### Max Pooling

Divide into regions and take the max over it.

Hyperparameters in pooling are:

- f: filter size (region size)
- s: stride

Preserving important detected features in the different regions/quadrants. If the feature is not present, the number resulting from applying the maxima still very small. But, this is not well known if is the underlying reason for max pooling to work very well with cnn.

Usually, padding is not used with max pooling.

__Output size:__

Same applies as with convolutio operation.

floor(((n + 2p - f) / s) + 1)

## Average Pooling

Instead of taking maxima, taking the average. It's not used as much as average pooling. Except in the case of very deep neural networks para comprimir la representación.

## Why Convolutions?

Parameter sharing and sparsity of connections.

Imagine:

- Inputs: 32x32x3 = 3072
- Filters: f_size=5 -> 28x28x6 = 4704

__In a fully connected layer:__ 3072x4704 ~ 14M parameters

__In a conv layer:__ (5x5) * 6 -> 156 parameters

There are 2 reasongs why a conv net has relatively small number of parameters:

_Parameter Sharing_

A feature detector (such a vertical edge detector) that's useful in one part of the image is probably useful in another part of the image. This is true for both, low and high level features.

_Sparsity of connections_

In each layer, each output value depends only on a small number of inputs.

Convolutional neural networks are very good capturing translation invariance (conv layers helps to encode the fact that a shifted image should result in pretty similar features).

