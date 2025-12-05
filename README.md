# Number Identification model
Two-headed CNN model built with Keras, trained on a Street View House Number (SVHN) dataset from [Kaggle](https://www.kaggle.com/datasets/stanfordu/street-view-house-numbers).

By:
- Walter Võikar
- Urmas Akerman

# Content guide

**data/**   
Has test,train and extra folders for pictures and .mat files that contain bounding box and label data for pictures in the folders
Also contains .npy files created during preprocessing.
- `test/` — Model testing pictures
- `train/` — Model training pictures
- `extra/` — Extra pictures for training

**src/**  
The codebase for model components:
- `CNN.ipynb` — Notebook that contains code for creating and training the CNN model as well as visualizing training results.
- `preprocessing.ipynb` — classification and bounding-box regression heads  
- `D2_report.pdf` — Homework 10 report

**models/**  
Trained model files.

# Before running the code

Download the full Kaggle SVHN dataset and extract the contents into the data folder. Make sure not to change the template
folder structure. `test/`, `train/` and `extra/` folders should contain only the corresponding images and no additional subdirectories:
- For example `data/test/1.png`

.mat files need to be in the `data/` folder.
- For example `data\test_digitStruct.mat`

# Running the code

Make sure you have downloaded and extracted the Kaggle dataset as described in the previous task.
Open `preprocessing.ipynb` and execute all the cells in order. This creates the numpy files
containing the picture data, bounding box data and digit label data.

Open `CNN.ipynb` and execute all the cells in order. This will read in the image, bounding box and test data 
and train/validate/test the model. Finally, the model will be saved to the `models/` folder.

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

