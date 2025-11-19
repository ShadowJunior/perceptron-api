# Object-Oriented Perceptron API

## Purpose

This module implements a **Perceptron classifier** using an object-oriented approach. The Perceptron is a simple yet foundational supervised learning algorithm for binary classification tasks. It learns linear decision boundaries by iteratively updating weights based on misclassifications during training.

## What It Does

### Core Functionality

The `Perceptron` class provides:

1. **Training (fit)**: Learns optimal weights from training data using the perceptron learning rule
2. **Prediction (predict)**: Classifies new samples as either class 1 or class -1 based on a linear decision boundary
3. **Net Input Calculation (net_input)**: Computes the weighted sum of inputs plus bias

### Algorithm Overview

- **Initialization**: Randomly initializes weights with small values from a normal distribution
- **Training Loop**: For each epoch (pass over the dataset):
  - Makes predictions on each sample
  - Calculates the prediction error (actual vs. predicted)
  - Updates weights using the Perceptron rule: `w = w + eta * (y - y_pred) * x`
  - Tracks the number of misclassifications per epoch
- **Decision Boundary**: Uses a unit step function (threshold at 0) to assign class labels

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `eta` | float | 0.01 | Learning rate; controls the size of weight updates (0.0 - 1.0) |
| `n_iter` | int | 50 | Number of passes (epochs) over the training dataset |
| `random_state` | int | 1 | Seed for reproducible random weight initialization |

## Attributes (After Fitting)

| Attribute | Type | Description |
|-----------|------|-------------|
| `w_` | 1d-array | Final learned weights (includes bias at index 0) |
| `errors_` | list | Number of misclassifications in each epoch |

## Usage Example

```python
import numpy as np
from oo_perceptron_api import Perceptron

# Prepare training data
X_train = np.array([[1, 2], [2, 3], [3, 1], [4, 5]])
y_train = np.array([1, 1, -1, -1])

# Create and train the perceptron
ppn = Perceptron(eta=0.01, n_iter=10)
ppn.fit(X_train, y_train)

# Make predictions
X_test = np.array([[2.5, 3.5], [3.5, 1.5]])
predictions = ppn.predict(X_test)
print(predictions)  # Output: [1 -1]

# Check training errors per epoch
print(ppn.errors_)
```

## Key Methods

### `fit(X, y)`
Trains the perceptron on the provided dataset.
- **Input**: `X` (features), `y` (target labels)
- **Output**: Returns `self` for method chaining

### `predict(X)`
Predicts class labels for new samples.
- **Input**: `X` (feature array)
- **Output**: Array of predicted labels (1 or -1)

### `net_input(X)`
Calculates the weighted input (linear combination).
- **Input**: `X` (feature array)
- **Output**: Array of net input values

## Limitations

- **Binary Classification Only**: Works with two classes (typically labeled as 1 and -1)
- **Linear Separability**: Requires linearly separable data to converge properly
- **No Guarantee of Optimal Convergence**: May not find the best possible weights
- **Sensitive to Feature Scaling**: Works better when features are normalized

## Notes

- The algorithm is sensitive to the learning rate (`eta`) — too high may cause divergence, too low may slow convergence
- The `errors_` list helps diagnose whether the model is learning (should decrease or stabilize over epochs)
- Weights are stored with the bias term at index 0 (`w_[0]`)

## Requirements

- NumPy (for numerical operations and random number generation)

## Author Context

This implementation is part of a machine learning curriculum exploring foundational classification algorithms from an object-oriented perspective.


git remote add origin https://github.com/ShadowJunior/perceptron-api.git
git branch -M main
git push -u origin main

hands-on-housing-prediction.git