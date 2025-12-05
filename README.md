# Number Identification model
Two-headed CNN model built with Keras, trained on a Street View House Number (SVHN) dataset from [Kaggle](https://www.kaggle.com/datasets/stanfordu/street-view-house-numbers).

By:
- Walter Võikar
- Urmas Akerman

## Motivation:
Street View images can contain many distracting features and overlapping digits making digit recognition difficult.
With this “messy” data hope to create a general number identification model, and also a way to experiment with and 
learn more about machine learning and data science.


## Replicating our results
This is a guide to our methods if you wish to replicate our results.

### Data preperation
The image labels are contained in .mat files that were cumbersome to open, so we read their contents and wrote them 
into .npy files for easier training.

The original RGB images were grayscaled to [0, 255] and then resized to 128x128 px, because while the images ranged 
from 25x12 px to 876x501 px, but most of them inside 128x128 px. Then they are normalized to [0, 1] for training.

### Model architecture
Backbone consists of 5 convolutional blocks each containing:
    - Convolution 
    - Batch Normalizaiton
    - Activation (ReLu)
    - Pooling

This is followed by a regression head and a classification head for the bounding boxes and digit classification tasks 
respectively.

