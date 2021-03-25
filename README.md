# Face Image Classification (Based on ethnicity)

Face Image Classification is an image classification project. The aim is to use various pre trained deep neural networks and transfer learning to build a classifier that can identify faces of different ethnicities.

## Data

The dataset used for this project is the UTKFace dataset available at the link below. It is a large scale dataset containing more than 20,000 images of faces all the way from ages 0 to more than 100 years old. There are 5 classes which are Asian, Black, Indian, White and Others. Since my aim is to build a classifier and explore the different methods of training and tuning deep learning models, I have trimmed down the dataset to include the 4 main classes (Asian, Black, Indian and White) and only ages between 15 and 50.

Source: https://susanqq.github.io/UTKFace/

## Experiments

The first experiment is detailed in the 'Experiment_1_VGG16.md' markdown file
The corresponding notebook can be found at notebooks/faceClassification_VGG.ipynb
