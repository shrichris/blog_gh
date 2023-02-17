---
layout: post
title:  "Coursera - CNNs in Tensorflow - Week 4"
date:   2023-02-09 
categories: notes
learning_platform: [coursera, deeplearning.ai]
specialization: DeepLearning.AI TensorFlow Developer Professional Certificate
course: CNNs in Tensorflow
tags: [Coursera, CNN_Tensorflow] 
---
# Notes from Week 4 of auditing the course

Multi-class learning - moving from binary (2 class)classification problem, to 3 possible classes.

Fashion MNIST was an example of a 10 class classification problem

Computer graphics can be used to generate image data for training. We see this in the rock, paper, scissors classification exercise.

## Key changes compared to binary classification

* For multi-class classification, the class mode has be set to be "categorical"
* In the model definition - for binary classification, the output layer used a sigmoid activation fucntion which outputs a value close to 1 for one value and close to zero for the other. For multi-class classification, the the output later will need a softmax activation function. Softmax will turn the outputs in the last layer into probabilities that sum to one.
* For binary classification, when compiling the model, we used the binary cross entropy loss fucntion. For multi-class classification, we will use the categorical_cross entropy (or spare cross entropy) 

## Jupyter Notebooks

[Week 4, Lab 1](https://github.com/https-deeplearning-ai/tensorflow-1-public/blob/main/C2/W4/ungraded_lab/C2_W4_Lab_1_multi_class_classifier.ipynb)

## Links
[Rock, Paper, Scissors Dataset](http://www.laurencemoroney.com/rock-paper-scissors-dataset/)
[Rock Paper Scissors Prediction Set (neither training not test/validation to simulate readl world images)](https://storage.googleapis.com/laurencemoroney-blog.appspot.com/rps-validation.zip)


