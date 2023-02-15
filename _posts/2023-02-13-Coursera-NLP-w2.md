---
layout: post
title:  "Coursera - NLP in Tensorflow - Week 2"
date:   2023-02-09 
categories: notes
learning_platform: [coursera, deeplearning.ai]
specialization: DeepLearning.AI TensorFlow Developer Professional Certificate
course: NLP in Tensorflow
tags: [Coursera, NLP_Tensorflow] 
---

# Notes from Week 2 of auditing the course

## Word Embeddings 

* Tokens map words to a number
* Word Embeddings map tokens to vectors in higher dimensional spce
  * captures semantics e.g. dog and canine may both be vectors in an n-dimensional space that are pointing in similar directions
 
## Datasets in TF with Tensorflow Data Services

Use python 3 environment in Colab.

```python
import tensorflow as tf
print(tf.__version__)
import tensorflow_datasets as tfds
# with_info returns the metadata
imdb, info = tfds.load("imdb_reviews", with_info=True, as _supervised=True)
import numpy as np
# Split the imdb dataset into its training and test components (the values in these arrays are tensors)
train_data, test_data = imdb['train'], imdb['test']

# Separate the sentences and the labels in the training_data into separate numpy arrays. Do the same for the test_data
training_sentences = []
training_labels = []
for s, l in train_data:
    training_sentences.append(s.numpy.decode('utf8'))
    training_labels.append(l.numpy()) 
# Convert the arrays of tensors into numpy arrays
training_labels_final = np.array(training_labels)
testing_labels_final = np.array(testing_labels)

```
## Tokenization and Sequence Generation

In the exmample, a vocabulory size of 10,000 is set, each sequence has a max length = 120. The details are similar to previous set of notes.

## Embeddings
In the example, an embedding dimension = 16 is used.

Details of embedding are not in scope of this course. See the Coursera Deep Learning Specialization.

Intuitively, we are defining vectors in a 16-dimension space. Words that have similar sentiment (as determined by the labels) are assigned similar vectors in this 16-dimnension space and therefore cluster together.

## Observations from exercise in building a classifier for the sarcasm dataset

To Do.. Accuracy vs Loss.

## Loss

Training loss falls. Validation loss increased.
What does this imply?

Number of accurate predictions increased over time. Howerver, the confidence in the predictons decreased

Changing hyperparameters will have different impacts on accuracy and loss.

## Pre tokenised datasets
Many datasets are available pre-tokenised. For example, the IMDB dataset is available in TFDS with sub-word tokensization

The specific embedding used will have an impact on the layer definitions as well as the training.

## Jupyter Notebooks
[Week 2 Lab 1](https://github.com/https-deeplearning-ai/tensorflow-1-public/blob/main/C3/W2/ungraded_labs/C3_W2_Lab_1_imdb.ipynb)
[Week 2 Lab 2](https://github.com/https-deeplearning-ai/tensorflow-1-public/blob/main/C3/W2/ungraded_labs/C3_W2_Lab_2_sarcasm_classifier.ipynb)
[Week 2 Lab 3](https://github.com/https-deeplearning-ai/tensorflow-1-public/blob/main/C3/W2/ungraded_labs/C3_W2_Lab_3_imdb_subwords.ipynb)

## Links

[IMDB Embedding Visualiser](http://projector.tensorflow.org)
[IMDV Reviews Dataset](http://ai.stanford.edu/~amaas/data/sentiment/)
[Tensorflow Datasets](https://github.com/tensorflow/datasets/tree/master/docs/catalog)
[TF Subword encoder](https://www.tensorflow.org/datasets/api_docs/python/tfds/deprecated/text/SubwordTextEncoder)

