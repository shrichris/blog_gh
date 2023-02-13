---
layout: post
title:  "Coursera - CNNs in Tensorflow - Week 2"
date:   2023-02-09 
categories: notes
learning_platform: [coursera, deeplearning.ai]
specialization: DeepLearning.AI TensorFlow Developer Professional Certificate
course: CNNs in Tensorflow
tags: [Coursera, CNN_Tensorflow] 
---

# Notes from Week 4 of auditing the course

Overfitting - model is very good at spotting features from a limited training datatset, but not so good at spotting features on data the model has not seen before.

This can be observed by graphing the plot of training accuracy (and validation accuracy) against the epochs. If the training accuracy is high but the validation accurcay is lower and plateaues, this is a good indication of overfitting.

Data augmentation via image transformations - mirroing/flipping, zooming, rotation, shearing, skewing, flipping increases the available training data.

Image augmentation introduces an element of randomness in the training. If the validation set is small and does not demosntrate similar variety nd randomness, then image augmentation may not solve the overfitting issue.

TF allows data augmentation to be done on the fly.

## Image Generation

```python

```

## Jupyter Notebooks

[Week 2- Lab 1](https://github.com/https-deeplearning-ai/tensorflow-1-public/blob/main/C2/W2/ungraded_labs/C2_W2_Lab_1_cats_v_dogs_augmentation.ipynb)
[Week 2 - Lab 2](https://github.com/https-deeplearning-ai/tensorflow-1-public/blob/main/C2/W2/ungraded_labs/C2_W2_Lab_2_horses_v_humans_augmentation.ipynb)

## Links

[Preporcessing/augmentation in Keras](https://keras.io/api/layers/preprocessing_layers/)
[Image data preprocessing](https://keras.io/api/preprocessing/image/)

## To Do

