# Face Image Classification (Based on ethnicity)

Face Image Classification is an image classification project. The aim is to use various pre trained deep neural networks and transfer learning to build a classifier that can identify faces of different ethnicities.

## Data

The dataset used for this project is the UTKFace dataset available at the link below. It is a large scale dataset containing more than 20,000 images of faces all the way from ages 0 to more than 100 years old. There are 5 classes which are Asian, Black, Indian, White and Others. Since my aim is to build a classifier and explore the different methods of training and tuning deep learning models, I have trimmed down the dataset to include the 4 main classes (Asian, Black, Indian and White) and only ages between 15 and 50.

Source: https://susanqq.github.io/UTKFace/


## Model details

- The trimmed down dataset contains over 14000 images. This dataset is split into training and validation sets (80% training and 20% validation).
- Training a deep neural network from scratch requires a lot of time and computing resources. Instead we can use transfer learning where we get a pre-trained model and tune it to our specific data.
- For the first few experiments we use the VGG 16 Convolutional Neural Network trained on the imagenet dataset

### Basic workflow

- Import the VGG16 CNN from keras without the top dense layers. We will build our own fully connected layers and experiment with them
- Build our top dense layers
- Train the model and evaluate using the validation dataset
- Try and improve the model performance by exploring different methods


## Results

### Trial 1



### Trial 2
