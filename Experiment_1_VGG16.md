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

- Base Model: VGG16 (Weights - frozen/non trainable)
- Top layer: 2 Dense layers with 1024 and 512 nodes
- Activation: ReLU
- Optimization: ADAM (Learning rate - 0.00001)
- Epochs: 100

#### Interpretation
- Training accuracy got close to 100% but validation accuracy peaked at 78% and slowly started dropping down to 72.5%
- Training loss decreased constantly and stabilized at 0 while validation loss kept increasing and fluctuating and peaked at 1.9.
- The model is clearly overfitting.


<p align = "center">
<img src="images/trial_1.jpg" width = "800">
</p>

### Trial 2

#### Changes from previous trial
- Added dropout layers for each fully connected layer
- Changed the optimization function to RMSProp
- Used L2 Regularization
<br>

- Base Model: VGG16 (Weights - frozen/non trainable)
- Top layer: 2 Dense layers with 1024 and 512 nodes with a dropout layer with 50% drop probability for each dense layer
- Activation: ReLU
- Optimization: RMSProp (Learning rate - 0.0001)
- Epochs: 50

#### Interpretation
- Regularization and dropout layers have reduced overfitting to a large extent.
- The training and validation losses now show a similar trend unlike the first trial.

<p align = "center">
<img src="images/trial_2.jpg" width = "800">
</p>


### Trial 3

#### Changes from previous trial
- Reduced the sizes of the dense layers
- Added model fine tuning. After the initial training the base model weights are made trainable and the entire neural network is trained for a few more epochs
<br>

- Base Model: VGG16
- Top layer: 3 Dense layers
    - 512 node dense layer
    - Dropout 0.5
    - 256 node dense layer
    - Dropout 0.4
    - 128 node dense layer
    - Dropout 0.2
- Activation: ReLU
- Optimization: RMSProp (Learning rate - 0.00001)
- Epochs: 90 (With a frozen base model) + 10 (With fully trainable weights)

#### Interpretation
- While the model is still overfitting, the validation accuracy has improved and is very close to 80%
- This means the model is generalizing well on unseen data.

<p align = "center">
<img src="images/trial_3.jpg" width = "800">
</p>

#### After Tuning
- Fine tuning the model improved the validation accuracy beyond 80%
- But the model is back to overfitting because the training accuracy is very high at 97%

<p align = "center">
<img src="images/tune_3.jpg" width = "800">
</p>


### Trial 4

#### Changes from previous trial
- Further reduced the sizes of the dense layers
<br>

- Base Model: VGG16
- Top layer: 3 Dense layers
    - 100 node dense layer
    - Dropout 0.5
    - 50 node dense layer
    - Dropout 0.4
    - 25 node dense layer
    - Dropout 0.2
- Activation: ReLU
- Optimization: RMSProp (Learning rate - 0.00001)
- Epochs: 90 (With a frozen base model) + 10 (With fully trainable weights)

#### Interpretation
- There is significant improvement in the model performance with very little overfitting

<p align = "center">
<img src="images/trial_4.jpg" width = "800">
</p>

#### After Tuning
- The final model has an accuracy of 82% and the final training accuracy is a little more than 88%
- This has been the best result so far

<p align = "center">
<img src="images/tune_4.jpg" width = "800">
</p>
