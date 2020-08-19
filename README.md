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

- Resizing images with inter area interpolation to dimension (299,299,3), it is resampling using pixel
area relation
- Image augmentation to have robustness against different kinds of images.Some of the augmentation techniques used are,
adding gaussian noise, contrast normalization, %50 flipping and etc.

# Model Architecture
![image](https://user-images.githubusercontent.com/17252665/90516537-ce2d1500-e16c-11ea-92d1-57194d50d39a.png)
figure 1


Model has 3 main parts:
- Recurrent Neural Network (LSTM) 
- Convolutional Neural Network (InceptionV3)
- Attention Module



# Optimization, Network 

- Network  is trained with gradient descent algorithm.

- Adam optimizer is used. As hyperparameters in adam optimizer beta_1 chosen as 0.9,beta_2 chosen as 0.999 and
learning rate has been chosen as 0.001. These values are default values for Adam optimizer
function of Keras module,

- Categorical Cross Entropy Loss is used for loss function because it is well-suited for the classification tasks with large number of classes.

# Training Hyperparameters

As the main architecture, figure 8 is used however architecture’s performance is evaluated
with different hyperparameters. 
Hyperparameters that are changed in the model are:

- Embedding dimension 
- Lstm hidden state dimension 
- A new architecture without using
attention. 

While trying different hyperparameters, train set, validation set, test set initialized
as same, optimizer and loss function kept same.

# Samples of the project 

Sample results of the project when hyperparameters are:
- lstm state dimension= 500
- embedding_dim = 200
- with attention


![image](https://user-images.githubusercontent.com/17252665/90626398-97fe9c80-e223-11ea-8af3-da9b57ac2df8.png)
![image](https://user-images.githubusercontent.com/17252665/90626407-9a60f680-e223-11ea-8451-fe6ece118999.png)
![image](https://user-images.githubusercontent.com/17252665/90626411-9c2aba00-e223-11ea-982f-45112b3aff28.png)
![image](https://user-images.githubusercontent.com/17252665/90626418-9f25aa80-e223-11ea-9525-7d502f6088c0.png)
![image](https://user-images.githubusercontent.com/17252665/90626423-a0ef6e00-e223-11ea-817d-b7ffbb5b8a0a.png)
![image](https://user-images.githubusercontent.com/17252665/90626473-ae0c5d00-e223-11ea-982d-03a1dd98436a.png)

