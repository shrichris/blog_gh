---
layout: post
title:  "Coursera - NLP in Tensorflow - Week 3"
date:   2023-02-09 
categories: notes
learning_platform: [coursera, deeplearning.ai]
specialization: DeepLearning.AI TensorFlow Developer Professional Certificate
course: NLP in Tensorflow
tags: [Coursera, NLP_Tensorflow] 
---

# Notes from Week 3 of auditing the course

## Sequence Models 

* Moving from sentiment in individual words to sentiment obtained from sequence of words (e.g. fun vs not fun)

## RNN

Outputs from previous stage are fed to the next stage.
See details in the Deep Learning Specialization

## LSTM (Long Short Term memory)
The keyword with the context comes from much earlier in the sequence.
"I grew in Ireland and when I was in school I was taight to speak ..."
In LSTM, a pipeline of "conexts" is fed both in the forward and reverse directions in a network.

Is an LSTM a type of RNN?

## LSTMs in code

```python
model = tf.keras.Sequential([
    tf.keras.layers.Embedding(tokenizer.vocan_szie,64),
    # LSTM(64) signifies the number of outputs we desire from the LSTM layer 
    # Bidirectional propogates model state in both directions (output of bidirectionlayer will be 128, rather than 64)
    # return_sequences=True is required when stacking LSTMs to ensure that output of first LSTM match the desited input of the next layer (why would this be any difefrent?)
    tf.keras.layers.Bidirectional(tf.keras.layers.LSTM(64), return_sequences = True),
    tf.keras.layers.Bidirectional(tf.keras.layers.LSTM(32)),
    tf.keras.layers.Dense(64,activation='relu'),
    tf.keras.layers.Dense(1,activation='sigmoid'),
])

```

With text/language models, the likleihood of overfitting is greater as the validation set will most likely have out of vocabulory words.

## Jupyter Notebooks
[Week 3, Lab 1, Single layer LSTM](https://github.com/https-deeplearning-ai/tensorflow-1-public/blob/main/C3/W3/ungraded_labs/C3_W3_Lab_1_single_layer_LSTM.ipynb)
[Week 3, Lab 2, Multi layer LSTM](https://github.com/https-deeplearning-ai/tensorflow-1-public/blob/main/C3/W3/ungraded_labs/C3_W3_Lab_2_multiple_layer_LSTM.ipynb)
[Week 3, Lab 3, Using Convolutions](https://github.com/https-deeplearning-ai/tensorflow-1-public/blob/main/C3/W3/ungraded_labs/C3_W3_Lab_3_Conv1D.ipynb)
[Week 3, Lab 4](https://github.com/https-deeplearning-ai/tensorflow-1-public/blob/main/C3/W3/ungraded_labs/C3_W3_Lab_4_imdb_reviews_with_GRU_LSTM_Conv1D.ipynb)
[Week 3, Lab 5, Sracasm with LSTM](https://github.com/https-deeplearning-ai/tensorflow-1-public/blob/main/C3/W3/ungraded_labs/C3_W3_Lab_5_sarcasm_with_bi_LSTM.ipynb)
[Week 3, Lab 6, Sarcasm with 1D convolution](https://github.com/https-deeplearning-ai/tensorflow-1-public/blob/main/C3/W3/ungraded_labs/C3_W3_Lab_6_sarcasm_with_1D_convolutional.ipynb)

## Links

[Sequence Models Course](https://www.coursera.org/lecture/nlp-sequence-models/deep-rnns-ehs0S)
[LSTM Course](https://www.coursera.org/lecture/nlp-sequence-models/long-short-term-memory-lstm-KXoay)

## To Do
