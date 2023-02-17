---
layout: post
title:  "Coursera - Browser Based Models in TF - Week 1"
date:   2023-02-09 
categories: notes
learning_platform: [coursera, deeplearning.ai]
specialization: DeepLearning.AI TensorFlow Developer Professional Certificate
course: NLP in Tensorflow
tags: [Coursera, Browser_Tensorflow] 
---

# Notes from Week 1 of auditing the course

Browsers are full fledged training / inference environments.

Coding the "Hello World" example in Javascript using Tensorflow.js

N.B. Numpy is not available in js. TF functions are used for arrays.

Tensor2d takes as input an array as the first parameter, and the shape of the array as the second parameter

The training code is written as an async function (As the amount of time taken for the training cannot be determined upfront, and we do not want to lock the browser when the training is going on)

## Jupyter Notebooks

[Lab Materials](https://github.com/https-deeplearning-ai/tensorflow-2-public)

## Links
[IRIS Dataset](https://archive.ics.uci.edu/ml/datasets/iris)


## Running the example code

Instructions use a deprecated chrome extension to run a local server to execute the code

Do the following instead,

* Open a terminal within the directory containing the code. 
* python -m http.server
* Open browser and enter localhost:8000
* Click on the required file in the listing
