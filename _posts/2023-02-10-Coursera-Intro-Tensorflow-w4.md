---
layout: post
title:  "Coursera - Introduction to Tensorflow - Week 4 "
date:   2023-02-09 
categories: notes
tags: Coursera Intro_Tensorflow 
---

# Notes from Week 4 of auditing the course

Fashion Mnist images - extremely clean and structured images
In practive images will not be so structured. A handbag (as an example of a feature that we would like to detect) will likely not be centred in an image, but may appear anywhere in a larger picture e.g. on someone's arm

Image Generator in TF is used to generate training and test/validation images

## Insights

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

* Input share is (300, 300, 3) - The 3 indicates the three byte depth for pixels in a colour image
* The final layer has 1 output as this is a binary classifcifier (There are 2 classes and 1 value is sufficent to encode this information)

## Fitting the model

```python
history = model.fit(
      train_generator,
      steps_per_epoch=8,  
      epochs=15,
      verbose=1)
```

* The Steps per model is defined based on the batch size. 8 steps are needed in the example to load the training set in batches of size 128

## Links

*[Disease detection in Cassava plants](https://www.youtube.com/watch?v=NlpS-DhayQA)
*[Week 4 - Workbook](https://github.com/https-deeplearning-ai/tensorflow-1-public/blob/main/C1/W4/ungraded_labs/C1_W4_Lab_1_image_generator_no_validation.ipynb)

## To Do