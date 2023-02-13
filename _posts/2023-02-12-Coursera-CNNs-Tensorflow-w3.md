---
layout: post
title:  "Coursera - CNNs in Tensorflow - Week 3"
date:   2023-02-09 
categories: notes
learning_platform: [coursera, deeplearning.ai]
specialization: DeepLearning.AI TensorFlow Developer Professional Certificate
course: CNNs in Tensorflow
tags: [Coursera, CNN_Tensorflow] 
---

# Notes from Week 4 of auditing the course

Transfer Learning - use an "inception" model, trained by others on larger complex datasets to augment your own model, usually with a smaller dataset. 

In practice this involves for example, "locking" a certian number of layer of a pre-trained model, resuing the convolutuion and pooling layers of the inception model, and adding your own DNN to it. 

This allows for models to be trained faster and also achieve higher accuracy as the inception model will have learnt many more features that will augment the model you require.

Keras has Inception model definition built in

```python
import os
from tensorflow.keras import layers
from tensorflow.kers import Model
from tensorflow.keras.applications.inception_v3 import InceptionV3

local_weights_file = ""

pre_trained_model = InceptionV3(
    # Specify the input shape for our data
    input_shape = (150,150,3),
    # inception V3 has a fully-connected layer at the "top" (end?) for classification. By setting include_top to false, the fully connected layer is ignored and we go straight to the convolutions. 
    include_top = False,
    # Do not use built in weights. 
    weights = None
)

# load the snapshot of pre-traind weights
pre_trained_model.load_weights(local_weights_file)

# Lock layers (so they are trainable with our code)

for layer in pre_trained_model.layers:
    layer.trainable = False

# Print summary of pre-trained model

pre_trained_model.summary()

#Specify the last layer from the pre-trained model that we want to use. In this example, rather than the very last 3*3 convolution, we are using a previous 7*7 convolution layer (can be located by using the summary)

last_layer = pre_trained_model.get_layer('mixed7')
last_output = last_layer.output

# Adding your own DNN

from tensorflow.keras.optimizers import RMSprop

x = layers.Flatten()(last_output)
x = layers.Dense(1024, activation = 'relu')(x)
x = layers.Dense(1, activation='sigmoid')(x)

model = Model(pre_trained_model.input,x)
model.compile(
    optimizer = RMSprop(learning_rate=0.0001),
    loss = 'binary_crossentropy',
    metrics = ['acc']
)

```

# Dropout

What is "Dropout"?
It is a type of layer in Keras

Using Dropout is a stratgey to address overfitting by remove a random number of neurons in your neural network.

From course content:
"This works very well for two reasons: The first is that neighboring neurons often end up with similar weights, which can lead to overfitting, so dropping some out at random can remove this. The second is that often a neuron can over-weigh the input from a neuron in the previous layer, and can over specialize as a result. Thus, dropping out can break the neural network out of this potential bad habit! "

```python

from tensorflow.keras.optimizers import RMSprop

x = layers.Flatten()(last_output)
x = layers.Dense(1024, activation = 'relu')(x)
# Specifies fraction of neurons to drop.
x = layers.Dropout(0.2)(x)
x = layers.Dense(1, activation='sigmoid')(x)

```

## Jupyter Notebooks
[Week 3, Lab 1](https://github.com/https-deeplearning-ai/tensorflow-1-public/blob/main/C2/W3/ungraded_lab/C2_W3_Lab_1_transfer_learning.ipynb)

## Links

[Imagenet](https://image-net.org)
[Copy of pre-trained weights for Inception]()
[Keras freeze/locl layers documentation](https://www.tensorflow.org/tutorials/images/transfer_learning)

## To Do

