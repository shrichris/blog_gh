---
layout: post
title:  "Coursera - CNNs in Tensorflow - Week 1"
date:   2023-02-09 
categories: notes
learning_platform: [coursera, deeplearning.ai]
specialization: DeepLearning.AI TensorFlow Developer Professional Certificate
course: CNNs in Tensorflow
tags: [Coursera, CNN_Tensorflow] 
---
# Notes from Week 4 of auditing the course

In course 1, the datasets consisted of small and structured imagaes
With smaller dataset (like the previous course in this specialization), there is a greater risk of overfitting.

In this course, the focus is on training on a larger dataset (to classift cats and dogs) with images that dpecit more action and have diverse locations in the image frame.

Data quality in public datasets is often not perfect.

Cropping mis-classifierd images to focus on the specific feature of interest can rectify mis-classifications.

## Visualizing the effects of convolutions

display_grid is constructed from the variable x which is read as a feature map and processed for visibility in the central loop. This is used to render each stage i.e.  the convolutions of the image, plus their pooling, then another convolution, etc.

## Visualizing the learning history

the "history" object (returned by model.fit) can be used to visualize the accuracy of training and validation.

## Jupyter Notebooks

[Week 1 - Lab 1](https://github.com/https-deeplearning-ai/tensorflow-1-public/blob/main/C2/W1/ungraded_lab/C2_W1_Lab_1_cats_vs_dogs.ipynb)

## Links
[Github Respository with notebooks for this course](https://github.com/https-deeplearning-ai/tensorflow-1-public)
[Kaggle - cats vs dogs dataset](https://www.kaggle.com/c/dogs-vs-cats)

## To Do

Review "Visualizing the effect of convolutions"

