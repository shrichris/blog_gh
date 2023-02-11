---
layout: post
title:  "Coursera - Introduction to Tensorflow - Week 2"
date:   2023-02-09 
categories: notes
tags: Coursera Intro_Tensorflow 
---

# Notes from Week 2 of auditing the course

"If it doesn't work on MNIST, it won't work at all" VS If it does work on MNIST, it may still fail on others."

Fashion_MNIST

Training vs Test sets: 
60k images from Fashion_MNISt are used as training images and 10k as test.
The test data is used to check the accuracy of a model that has been trained on the training data. The test data has not previously been seen by the model, so it is a good measure of how well the model has been trained.

## Insights

```python
model = keras.Sequential([
# Fashion MNIST images are 28*28 grayscale. The first layer loads an image and flattens from vector to a linear array of values
    keras.layers.Flatten(input_shape=(28,28)),
# Hidden layer with 128 neurons. We can think of each neuron as a fucntion that takes  the 28*28 = 784 input values from the previous layer and converts it into an output value corresponding to an item in the training dataset. 
    keras.layers.Dense(128, activation=tf.nn.relu),
# There are 10 items in the training set. Hence, the output layer has 10 neurons.
    keras.layers.Dense(10,activation=tf.nn.softmax)
])

```

The loss function is used to calculate how well the model did with a guess in a particular iteration.
The optimzer is used to generate a new guess.
Relu activation throws away negative values

To do: Understand Loss vs accuracy. The code in the workboom apears to use loss and accuracy interchangeably. Understand why
## Links

* [Fashion MNIST](https://github.com/zalandoresearch/fashion-mnist)
* [Responsible AI practices](https://ai.google/responsibilities/responsible-ai-practices/)
* [Week 2: Fashion MNISt workbook](https://github.com/https-deeplearning-ai/tensorflow-1-public/blob/main/C1/W2/ungraded_labs/C1_W2_Lab_1_beyond_hello_world.ipynb)
* [Week 2: Using callbacks to control training](https://github.com/https-deeplearning-ai/tensorflow-1-public/blob/main/C1/W2/ungraded_labs/C1_W2_Lab_2_callbacks.ipynb)

