---
layout: post
title:  "Coursera - NLP in Tensorflow - Week 1"
date:   2023-02-09 
categories: notes
learning_platform: [coursera, deeplearning.ai]
specialization: DeepLearning.AI TensorFlow Developer Professional Certificate
course: NLP in Tensorflow
tags: [Coursera, NLP_Tensorflow] 
---

# Notes from Week 1 of auditing the course

## Preparing and encoding text for training in a neural network

Encoding letters in a word in ASCII - semantics not covneyed
e.g. of LISTEN vs SILENT

Encode words/Tokenize
e.g.
I love my cat -> [1,2,3,4]
I love my dog -> [1,2,3,5]

```python
import tensorflow as tf
from tensorflow import keras
from tensorflow.keras.preprocessing.text import Tokenizer
from tensorflow.keras.preprocessing.seuence import pad_sequences

sentences = [
    'I love my dog'
    'I love my cat'
    'You love my dog!'
    'Do you think my dog is amazing?'
]

# Instruct model to encode top 100 words by volume. In this case there are fewer words, but where the number of words is unknown, this will encode the top 100 words.
tokenizer = Tokenizer(num_words=100, oov_token="<OOV>")
tokenizer.fit_on_words(sentences)
# word_index has a dictionary of unique words and their tokens (a corpus). 
# The Tokenizer strips punctuation and lowercases words.
word_index = tokenizer.word_index
print(word_index)

# Encode the sentences into lists, replacing individual words with tokens
# If there are words the tokenizer has not seen, then these are omitted when generating sequences or with the oov_token if specified. 
sequences = tokenizer.texts_to_sequences(sentences)

print(sequences)

# Sentences of different lengths need to be padded so they can be used as input into a network for training. 
# Padding is applied before the sentence by default. padding = post can be used so that padding is applied to the end rather than the start. 
# maxlen can be used to force the length of the padded sequences. This will truncate the sequences at the start. This can be overridden using the truncatin = 'post' option.

padded = pad_sequences(sequences, padding='post', maxlen=5, truncating='post')

print(padded)

```

## Jupyter Notebooks

[Week 1 Lab 1](https://github.com/https-deeplearning-ai/tensorflow-1-public/blob/main/C3/W1/ungraded_labs/C3_W1_Lab_1_tokenize_basic.ipynb)
[Week 2 Lab 2](https://github.com/https-deeplearning-ai/tensorflow-1-public/blob/main/C3/W1/ungraded_labs/C3_W1_Lab_2_sequences_basic.ipynb)
[Week 1 Lab 3](https://github.com/https-deeplearning-ai/tensorflow-1-public/blob/main/C3/W1/ungraded_labs/C3_W1_Lab_3_sarcasm.ipynb)

## Links
[Repo for this specialization](https://github.com/https-deeplearning-ai/tensorflow-1-public)
[Sarcasm Dataset](https://www.kaggle.com/datasets/rmisra/news-headlines-dataset-for-sarcasm-detection)
[Sarcasm Dataset, amended for easy json loading into python]()