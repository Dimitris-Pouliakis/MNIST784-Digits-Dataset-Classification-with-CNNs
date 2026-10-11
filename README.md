# MNIST784-Digits-Dataset-Classification-with-CNNs
Today we are living in a world that changes rapidly and certainly is digital, a lot of previous paperworks done in offices, handwritten forms needs to be transferred to digital databases. Doing it manually, it is a burden. In this repository we achieved digits classification using 2 CNN Models for the famous MNIST784 Digits Dataset 

Disclaimer: This is a final project for machine learning seminars @AUTH 2026

# Scenario
The scenario we were interested in was to make a model that classify digits from handwritten images, make an error analysis and a comparison between one model and a second updated one and to assess if it can be deployed as a software for a sorting postal center or a bank, that sorts postal codes or distinct account numbers on handwritter forms correspondingly. It is noted, that this task is a high-stakes one, because a mistake can send letters in a different city or misdirect payments.

# Keras Model
Backend: **TensorFlow** <br>
Keras version: **3.13.2** <br>
You can find these also in the notebook

# Data
To train our models we used, the popular for starters in the machine learning world, the MNIST784 version 1, provided by openml, that includes 70,000 images with 784 features each one with a pixel value of the 28x28 = 784 pixels images. In the images there are depicted different number digits. You can find sample images of the dataset in the notebook in the corresponding section. 

# Model
For the construction of the 2 models, one simpler and one deeper one (with 2 Conv2D and 2 Pooling layers) we used **Keras 3 Sequential API** <br>
_Model1:_
1. Input Layer of the raw normalized greyscale images, Shape: (28, 28, 1)
2. Convolutional 2D Layer with 32 filters, 3x3 grid (32, 28, 28, 1) procuded feature maps
3. Pooling Layer 2x2 window
4. Flatten Layer
5. Dense Layer with 64 neurons, relu activation
6. Dropout Layer with a default value of 0.3
7. Dense Output Layer with 10 neurons, one for each predicted digit with activation "softmax" as it is a 10-class classification digit task

For the second model, we chose to add one extra set of Convolutional and Pooling layer to deepen our model, it was the Option A transformation for the final project: <br>
_Model2:_ <br>
Added 2 layers between 3. and 4. for previous model
Extra Convolutional 2D Layer with same parameters
Extra Pooling Layer
All the other parameteres stayed the same so we could achieve a fair comparison between the 2 models

# Compiling the Models
For compiling the models we used the following <br>
_Optimiser:_ Adam a strong default option with learning rate 0.001 <br>
_Loss:_ "sparse_categorical_crossentropy" as a default for many classes tasks <br>
_Metrics:_ "accuracy"

# Fitting the Models
We used Early Stopping to avoid overfitting, but as we saw in the learning curve of model, an overfitting achieved after epoch 7, so there is a room for improvement
_Patience:_ 3 <br>
_Monitor Loss:_ "val_loss" <br>
_Validation Split:_ 10% of the trained data <br>
_Epochs:_ 15 <br>
_Batch size:_ 128

# Evaluation
We kept track in the **learning curves of loss and validation loss**, as provided in the result section below and notebook's corresponding section
The **accuracy and loss for test images** that was kept aside through training, and used only for fair evaluation at the already trained model
**Confusion Matrices** with predicted digits from the model and true labeled digits from the dataset, to make an error analysis as it was a central question for this project
Comparison between the first and second model.

# Limitation
During evaluating the results, we trained the second model a second time (noted as second run in the notebook) and we spotted a better performance as shown and discussed in the notebook. So, a limitation of this project is to assess if there is a sensitivity to the splits, for this in the future can be used StratifiedKFold. <br>
Also, ethical considerations are discussed in the notebook, this model achieving high accuraccy doesn't mean, that it is ready to classify every handwritten digit image, people have different educational background and variety in their handwriting style. In MNIST dataset could also be some bias from the starting images we trained our model. So this task isn't that easy. For future project, we could upload ours handwritten digit images to test if the model could classify correctly, images outside of the MNIST dataset. <br>
A bigger task is also classifying handwritten letters, in my university years I always was thinking how can I digitilise my notes to my computer, so there is also this task to be addressed.

In this repository also we added the confusion matrix, the training epochs and the test accuracy of the second model in the second run that you can look for.

