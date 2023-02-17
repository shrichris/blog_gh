---
layout: post
title:  "Coursera - NLP in Tensorflow - Week 4"
date:   2023-02-09 
categories: notes
learning_platform: [coursera, deeplearning.ai]
specialization: DeepLearning.AI TensorFlow Developer Professional Certificate
course: NLP in Tensorflow
tags: [Coursera, NLP_Tensorflow] 
---
# Notes from Week 4 of auditing the course
## Text generation as a prediction problem

Text generation can be thought of as as prediction problem.

Essentially, given a sequence of text (Xs), we want to predict what is a likely sequence (Ys) that follows.
### The key insights:

For every sentence in our corpus of sentences:
* we can generate a number of sub-sequences on the tokenised sentences.
* For every sub-sequence, all the tokens minus the last can be thought of as the input (X), and the very last token is the label(Y). This  provides our training data and training labels

Then,for text generation,
* Given an input sequence of words, we predict what the next word is
* Add the predicted word back to the input sequence and used to predict the next word… ad-infinitum!
  * Certainty of prediction will reduce with each prediction.
### Encoding

The labels can be one-hot encoded so it is suitable for training.

One-hot encoding of unique words in a corpus works well for small datasets. With larger datasets, the number of words will increase and so too will the memory requirements for one hot encoding these words.

Character encoding can then be used - the number of characters will be less than the number of unique 

## Jupyter Notebooks

[Week 4, Lab 1](https://github.com/https-deeplearning-ai/tensorflow-1-public/blob/main/C3/W4/ungraded_labs/C3_W4_Lab_1.ipynb)
[Week 4, Lab 2](https://github.com/https-deeplearning-ai/tensorflow-1-public/blob/main/C3/W4/ungraded_labs/C3_W4_Lab_2_irish_lyrics.ipynb)

## Links
[Poetry Dataset](https://github.com/https-deeplearning-ai/tensorflow-1-public/blob/main/C3/W4/misc/Laurences_generated_poetry.txt)
[TF Text generation Tutorial](https://www.tensorflow.org/tutorials/sequences/text_generation)