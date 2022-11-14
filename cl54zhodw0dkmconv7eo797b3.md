# Project 3 - MNIST Handwritten Digit Recognition

### Introduction

Tensorflow.js lets you develop or execute ML models in JavaScript, and use ML directly in the browser client side, server side via Node.js, mobile native via React Native, desktop native via Electron, and even on IoT devices via Node.js on Raspberry Pi. 

One of the other beauty in TensorFlow.js is that you can train a Machine Learning Model in Python using Keras or Tensorflow and deploy it on a browser using TensorFlow.js. No need for an external service (flask api or something like that) to run your queries. 

Checkout the Digit Recognizer Web app : https://syedjafer.github.io/digit-recognizer-webapp/

### MNIST Digit Recognizer
Everyone who started learning ML, would have  reached [kaggle](https://www.kaggle.com/code/syedjaferk/99-6-digit-recognizer) to do some handson. And they would have definitely seen the [Digit Recognizer](https://www.kaggle.com/competitions/digit-recognizer) competition to startby. This web application is the conversion of the digit recognizer model to a standalone web application without any external services. 

#### Steps Involved in creating the application.
1. I consider two different datasets [QMNIST - The Extended MNIST Dataset](https://www.kaggle.com/datasets/fedesoriano/qmnist-the-extended-mnist-dataset-120k-images) and [Digit Recognizor](https://www.kaggle.com/datasets/khotijahs1/digitrecognizer). 
2. Then I have used CNN for the model training. Please refer to my kaggle notebook for the training part and model generation. 
3. Convert the model object to model.json using tensorflowjs-converter. [Refer Notebook]
4. For the frontend part, i have used bootstrap and canvas for drawing the image by the user. 
5. Using tensorflow.js, we will be using the **model.json** generated and use that to predict the input image. 

### Deployment

Since this is a standalone html page, i deployed it directly in Github Pages. Please checkout the webapp [here](https://syedjafer.github.io/digit-recognizer-webapp/). 




