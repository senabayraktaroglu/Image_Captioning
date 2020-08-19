# IMAGE CAPTIONING PROJECT 

An image captioning project made with Tensorflow in Google Colab

# Goal

The goal of this project is producing meaningful captions for given images.
Captioning images is an attention taking task in recent years which connects Natural
Language Processing and Computer Vision. In this project a model is introduced that is a
combination of recurrent and convolutional neural network architectures. First 
convolutional network is used to extract features from images which describe the visual
characteristics of them like edges, shapes and color densities. Then a recurrent
network architecture is used to combine semantic information ,which gathered from given captions,
and visual characteristics of these images to make network learn how to produce meaningful
captions. Also  an attention module is used to focus on more related parts of images that
have relatively more impact on generating captions.

# Preprocessing 
Images are downloaded from different url's and they are resized to dimension (299,299,3).Dimension (299,299,3) is chosen due to the
requirements of InceptionV3. While resizing images a method used which is called inter area, it is resampling using pixel
area relation.Since an image have multiple captions, a single image entered to network multiple times.
Thus image augmentation used on some images to create modified versions of them. To have
robustness against different kinds of images. Some of the augmentation techniques used are,
adding gaussian noise, contrast normalization, %50 flipping and etc.


# Model Architecture
![image](https://user-images.githubusercontent.com/17252665/90516537-ce2d1500-e16c-11ea-92d1-57194d50d39a.png)
figure 1

Model has 2 main parts: Recurrent Neural Network (LSTM) and Convolutional Neural
Network (InceptionV3). CNN part is used for feature extraction and LSTM is used to learn
relation between images and corresponding captions by combining both semantic and visual
features which will be described in detail in next chapters. 

As seen from figure 1 an image first enters to the pretrained model of
inception-v3,then it passes a dense and relu layer. CNN module finishes after this, then
output of cnn enters into attention module, with cell state and hidden state of LSTM at time
(t-1). In the attention module, as seen from figure 8 , three dense layers used one for cnn
output,the other two are for for hidden state and cell state of lstm. Then those layers summed
and entered to tanh and then this result entered to softmax and multiplied with cnn output.
The resultant output vector can be called context vector.


# Optimization, Network AND Training hyperparameters

- Network  is trained with gradient descent algorithm.

- Adam optimizer is used. As hyperparameters in adam optimizer beta_1 chosen as 0.9,beta_2 chosen as 0.999 and
learning rate has been chosen as 0.001. These values are default values for Adam optimizer
function of Keras module,

- Categorical Cross Entropy Loss is used for loss function because it is well-suited for the classification tasks with large number of classes.

# Results 

As the main architecture, figure 8 is used however architecture’s performance is evaluated
with different hyperparameters. 
Hyperparameters that are changed in the model are:

-Embedding dimension 
-Lstm hidden state dimension 
- A new architecture without using
attention. 
While trying different hyperparameters, train set, validation set, test set initialized
as same, optimizer and loss function kept same.

