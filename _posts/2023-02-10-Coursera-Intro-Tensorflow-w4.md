---
layout: post
title:  "Coursera - Introduction to Tensorflow - Week 4 "
date:   2023-02-09 
categories: notes
learning_platform: [coursera, deeplearning.ai]
specialization: DeepLearning.AI TensorFlow Developer Professional Certificate
course: Introduction to Tensorflow
tags: [Coursera, Intro_Tensorflow] 
---

# Notes from Week 4 of auditing the course

Fashion MNIST images - extremely clean and structured images
In practice images will not be so structured. A handbag (as an example of a feature that we would like to detect) will likely not be centred in an image, but may appear anywhere in a larger picture e.g. on someone's arm

Image Generator in TF is used to generate training and test/validation images
## Image Generation

```python
from tensorflow.keras.preprocessing.image
import ImageDataGenerator

train_datagen = ImageDataGenerator(rescale=1./255)
Images can be resized at runtime
train_generator = train_datagen.flow_from_directory(
    # The name of the subdirectories in the training directory will be the labels for the images in that directory
    train_dir,
    # Images are processes as they are loaded from the directory
    target_size=(300,300),
    # Images are processes in batches. Batch size impact efficiency.
    batch_size=128,
    # Specifies that this is for binary classification
    class_mode='binary'

train_generator = train_datagen.flow_from_directory(
    # The name of the subdirectories in the training directory will be the labels for the images in that directory
    validation_dir,
    # Images are processes as they are loaded from the directory
    target_size=(300,300),
    # Images are processes in batches. Batch size impact efficiency.
    batch_size=32,
    # Specifies that this is for binary classification
    class_mode='binary'
)
```
## Defining the model

```python
model = tf.keras.models.Sequential([
    tf.keras.layers.Conv2D(16, (3,3), activation='relu', input_shape=(300, 300, 3)),
    tf.keras.layers.MaxPooling2D(2, 2),
    tf.keras.layers.Conv2D(32, (3,3), activation='relu'),
    tf.keras.layers.MaxPooling2D(2,2),
    tf.keras.layers.Conv2D(64, (3,3), activation='relu'),
    tf.keras.layers.MaxPooling2D(2,2),
    tf.keras.layers.Conv2D(64, (3,3), activation='relu'),
    tf.keras.layers.MaxPooling2D(2,2),
    tf.keras.layers.Conv2D(64, (3,3), activation='relu'),
    tf.keras.layers.MaxPooling2D(2,2),
    tf.keras.layers.Flatten(),
    tf.keras.layers.Dense(512, activation='relu'),
    tf.keras.layers.Dense(1, activation='sigmoid')
])

from tensorflow.keras.optimizers import RMSprop

model.compile(loss='binary_crossentropy',
              optimizer=RMSprop(learning_rate=0.001),
              metrics=['accuracy'])

```

* Input shape is (300, 300, 3) - The 3 indicates the three byte depth for pixels in a colour image
* The final layer has 1 output as this is a binary classifcifier (There are 2 classes and 1 value is sufficent to encode this information)
* The learning rate can be tweaked. If large flucations in accuracy are observed between epochs when training, then the learning rate should be tweaked down.

## Fitting the model

```python
history = model.fit(
      train_generator,
      steps_per_epoch=8,  
      epochs=15,
      verbose=1)
```

* The Steps per model is defined based on the batch size. 8 steps are needed in the example to load the training set in batches of size 128

## Validation using a test set

* The test of how good the model i determined by how it performs on images it has not previously seen. The accuracy of the model on training data is not enough.
* Accuracy on validation data can be expected to be lower than on the training data, as the model has not seen the validation data previosly.


## The effect of data compression on model accuracy

* Very high accuracy (~1 or >1) may be noted which indicates overfitting
* The lectures highlighted that using compression may result in faster training and higher accuracy, but performance on the model may be poorer. Specifically, images that are correctly trained using a larger dataset may be misclassfied.

## Jupyter Notebooks

* [Notebook - Week 4 - Lab 1](https://github.com/https-deeplearning-ai/tensorflow-1-public/blob/main/C1/W4/ungraded_labs/C1_W4_Lab_1_image_generator_no_validation.ipynb)
* [Notebook - Week 4 - Lab 2](https://github.com/https-deeplearning-ai/tensorflow-1-public/blob/main/C1/W4/ungraded_labs/C1_W4_Lab_2_image_generator_with_validation.ipynb)
* [Notebook - Week 4 - Lab 3 -  Using Compacted Images](https://github.com/https-deeplearning-ai/tensorflow-1-public/blob/main/C1/W4/ungraded_labs/C1_W4_Lab_3_compacted_images.ipynb)

## Links

* [Disease detection in Cassava plants](https://www.youtube.com/watch?v=NlpS-DhayQA)
* [Understanding different loss types](https://gombru.github.io/2018/05/23/cross_entropy_loss/)
* [Notes on Batch Gradient Descent](https://www.cs.toronto.edu/~tijmen/csc321/slides/lecture_slides_lec6.pdf)
* [TF RMSProp documentation](https://www.tensorflow.org/api_docs/python/tf/keras/optimizers/experimental/RMSprop)
* [Pixelbay - Free stock photographs](https://pixabay.com)

## To Do

To do: Understand Loss vs accuracy. Are terms being used interchanegably and is this correct to do?
