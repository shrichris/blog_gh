---
layout: post
title:  "Coursera - Introduction to Tensorflow - Week 1"
date:   2023-02-09 
categories: notes
learning_platform: [coursera, deeplearning.ai]
specialization: DeepLearning.AI TensorFlow Developer Professional Certificate
course: Introduction to Tensorflow
tags: [Coursera, Intro_Tensorflow] 
---
# Notes from Week 1 of auditing the course

## Insights

In traditional programming, a programmer has to formulate or code rules manually, whereas, in Machine Learning, the algorithm automatically formulates the rules from the data.

The Traditional Programming Paradigm
> (Rules, Data) -> Answers

The Machine Learning Paradigmß
> (Answers/Labels, Data) -> Rules
## The "Hello World" of Deep Learning with Neural Networks

Figuring out the relationship between x and y, given a training set with a small number of data points (the training set). The following shows how to fit a line between x and y variables.

```python

import tensorflow as tf
import numpy as np
from tensorflow import keras
print(tf.__version__)

## Build a simple Sequential model
model = tf.keras.Sequential([keras.layers.Dense(units=1, input_shape=[1])])

## Compile the model
model.compile(optimizer='sgd', loss='mean_squared_error')

## Declare model inputs and outputs for training
xs = np.array([-1.0,  0.0, 1.0, 2.0, 3.0, 4.0], dtype=float)
ys = np.array([-3.0, -1.0, 1.0, 3.0, 5.0, 7.0], dtype=float)

## Train the model
model.fit(xs, ys, epochs=500)

## Make a prediction
print(model.predict([10.0]))
```
## Jupyter Notebooks

* [Notebook - Week 1 - Lab 1](https://github.com/https-deeplearning-ai/tensorflow-1-public/blob/main/C1/W1/ungraded_lab/C1_W1_Lab_1_hello_world_nn.ipynb)

## Links

* [Lecture Notes for this course](https://community.deeplearning.ai/t/tf1-course-1-lecture-notes/124222)
* [Tensorflow Playground](http://playground.tensorflow.org/)
  * [Repo for the Tensorflow Playground](https://github.com/tensorflow/playground)
  * [Convnet Demo - Andrej Karpathy](https://cs.stanford.edu/people/karpathy/convnetjs/demo/classify2d.html)
  * [Book: Neural Networks and Deep Learning, Michael Nielson](http://neuralnetworksanddeeplearning.com/index.html)
  * [Book: Deep Learning, Ian Goodfellow, Yoshua Bengio, and Aaron Courville.](https://www.deeplearningbook.org/)
  
## To Revisit

The Tensorflow playground was a not entirely intuitive. The explanation of orange vs blue colours (positive and negative values) and how the datasets are depicted on screen do not seem to align. What are the pictorial representation of the datasets conveying?
