---
layout: post
title:  "Coursera - Introduction to Tensorflow - Week 3"
date:   2023-02-09 
categories: notes
tags: Coursera Intro_Tensorflow 
---

# Notes from Week 3 of auditing the course

Introduces Convolutional Neural Networks (CNNs) as an improvement over the naive implementation of week 2.

## Insights

Pooling is way of compressing images e.g. using a 2*2 grid to pick out the pixel with the highest value to quarter the size of the image.
Convolutions are essentially filters that can be passed over input data to emphasise features e.g. using fliters to highlight vertical or horizontal lines in an image.

{% highlight python %}
model = keras.Sequential([
    # Adding convolution and pooling layers
    # (28,28,1) - The 1 is to indicate the single byte depth for the grascale images in FMNIST.
    # The 64 filters in the convolution layer are not random. They are a set of known good filters. See Course 4 of deep learning specialization to understand the details of convolution and pooling layers
    keras.layers.Conv2D(64, (3,3), activation='relu', input_shape=(28,28,1))
    keras.layers.MaxPooling2d(2,2)
    keras.layers.Conv2D(64, (3,3), activation='relu')
    keras.layers.MaxPooling2d(2,2)
    # End of convolution and pooling layers. Input content size has been greatly reduced.
    keras.layers.Flatten(),
    keras.layers.Dense(128, activation=tf.nn.relu),
    keras.layers.Dense(10,activation=tf.nn.softmax)
])
{% endhighlight %}

## Output shape changes at each layer due to the effects of convolution and pooling

model.summary can be used to inspect the layers of the model, including the output shapes of each layer

* Inspecting the model above will show that the shape of the initial layer as (26,26,64) rather than (28,28,64)
* This is due to the effect of the (3,3) filter meaning that the filter cannot be applied on the edges of the image, along a 1 pixel margin. 
* For a (5,5) filter, the output shape will be 4 pixels less on x and y axes.
* 2dMax pooling halves the output along each axis. For odd dimensions, max pooling will round down i.e. (11,11,64) -> (5,5,64)
* The result of convolution and pooling will be is that the 28*28 images are reduced to 5*5 images
* Remember that there are 64 convolutions. Meaning that the input to the flatten layer is 1600 pixels (rather than 784)

## Links

* [Tensorflow documentation](https://www.tensorflow.org/api_docs/python/tf/)
* [Conv2D in TF](https://www.tensorflow.org/api_docs/python/tf/keras/layers/Conv2D)
* [Pooling in TF](https://www.tensorflow.org/api_docs/python/tf/keras/layers/MaxPool2D)
* [Convolution and Pooling details in the Deep Learning Specialization](https://www.youtube.com/playlist?list=PLkDaE6sCZn6Gl29AoE31iwdVwSG-KnDzF)
* [Week3 Workbook, Using convolutions with FMNIST for computer vision, Lab 1](https://github.com/https-deeplearning-ai/tensorflow-1-public/blob/main/C1/W3/ungraded_labs/C1_W3_Lab_1_improving_accuracy_using_convolutions.ipyn)
* [Week3 Workbook - Exploring convolutions - Lab 2](https://github.com/https-deeplearning-ai/tensorflow-1-public/blob/main/C1/W3/ungraded_labs/C1_W3_Lab_2_exploring_convolutions.ipynb)
* [Lode's Computer Graphics Tutorial](https://lodev.org/cgtutor/filtering.html)

## To Do

* Review the walkthrough lecture "Improving the Fashion classifier with convolutions"
