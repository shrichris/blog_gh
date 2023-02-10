---
layout: post
title:  "Coursera - Introduction to Tensorflow for Deep Learning - Week 1"
date:   2023-02-09 
categories: notes
tags: Coursera Intro_Tensorflow 
---

# Notes from Week 1 of auditing the course

## Insights

In traditional programming, a programmer has to formulate or code rules manually, whereas, in Machine Learning, the algorithm automatically formulates the rules from the data.

The Traditional Programming Paradigm
> (Rules, Data) -> Answers

The Machine Learning Paradigmß
> (Answers, Data) -> Rules

## The "Hello World" of Deep Learning with Neural Networks

Figuring out the relationship between x and y, given a training set with a small numnber of data points (the training set)

[Workbook](https://github.com/https-deeplearning-ai/tensorflow-1-public/blob/main/C1/W1/ungraded_lab/C1_W1_Lab_1_hello_world_nn.ipynb)

{% highlight python %}

import tensorflow as tf
import numpy as np
from tensorflow import keras
print(tf.__version__)

# Build a simple Sequential model
model = tf.keras.Sequential([keras.layers.Dense(units=1, input_shape=[1])])

# Compile the model
model.compile(optimizer='sgd', loss='mean_squared_error')

# Declare model inputs and outputs for training
xs = np.array([-1.0,  0.0, 1.0, 2.0, 3.0, 4.0], dtype=float)
ys = np.array([-3.0, -1.0, 1.0, 3.0, 5.0, 7.0], dtype=float)

# Train the model
model.fit(xs, ys, epochs=500)

# Make a prediction
print(model.predict([10.0]))

{% endhighlight %}

## Links

[Tensorflow Playground](http://playground.tensorflow.org/)