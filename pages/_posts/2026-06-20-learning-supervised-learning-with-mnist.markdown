---
layout: post
title: "Learning Supervised Learning with MNIST"
date: 2026-06-20 20:00:00 +0900
categories: [machine-learning, python, keras]
type: Article
excerpt: "My first hands-on take on supervised learning — training a neural network to recognize handwritten digits with Keras and the MNIST dataset."
---

To get a feel for **supervised learning**, I built a small handwritten-digit classifier in my [Supervised-Learning](https://github.com/Waffle0823/Supervised-Learning) repo. It's the classic "hello world" of machine learning, but going through it end-to-end made the core ideas click.

## What supervised learning is

You train a model on **labeled data** — inputs paired with the correct answers. The model learns a mapping from input to output, and the goal is for it to generalize to inputs it has never seen. For digit recognition:

- **Input:** a 28×28 grayscale image of a handwritten digit
- **Label:** which digit it actually is (0–9)

## The dataset: MNIST

MNIST is 70,000 images of handwritten digits — 60,000 for training and 10,000 for testing. Keras ships it built in:

```python
from keras.datasets import mnist
(x_train, y_train), (x_test, y_test) = mnist.load_data()
```

## Preparing the data

Two things had to happen before training:

**1. Flatten and normalize the images.** Each 28×28 image becomes a flat 784-length vector, and pixel values are scaled from `0–255` down to `0–1` so the network trains more stably.

```python
x_train = x_train.reshape(60000, 784).astype('float32') / 255.0
x_test  = x_test.reshape(10000, 784).astype('float32') / 255.0
```

**2. One-hot encode the labels.** The digit `3` becomes `[0,0,0,1,0,0,0,0,0,0]`, matching the 10-way output of the network.

```python
from keras.utils import to_categorical
y_train = to_categorical(y_train)
y_test  = to_categorical(y_test)
```

## The model

A simple fully-connected (`Dense`) neural network with `Dropout` for regularization and a softmax output over the 10 digit classes:

```python
from keras.models import Sequential
from keras.layers import Dense, Activation, Dropout
```

## What I took away

- **Data prep is most of the work.** Reshaping, normalizing, and encoding matter as much as the model itself.
- **Classification = probabilities.** The network outputs a probability for each digit; the prediction is just the highest one (`np.argmax`).
- **Train vs. test split.** Keeping test data separate is how you honestly measure whether the model *learned* rather than *memorized*.
