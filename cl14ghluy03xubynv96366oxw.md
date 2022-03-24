## What are Model Parameters and Hyperparameters?

### Introduction

The two most confusing terms in Machine Learning are model parameters and hyperparameters. In this article, we will try to understand what these terms mean and how they are different from each other. 


### Model Parameter

A model parameter is a variable of the selected model which can be estimated by fitting the given data to the model. 

![simple linear regression - machine learning - learnml.xyz](https://cdn.hashnode.com/res/hashnode/image/upload/v1648092973380/rg2vKXM_A.png)

> Linear Regression Formula => **y = mx + c**

in the above plot, x is the independent variable, and y is the dependent variable. The objective is to fit a regression line to the data. This line (the model) is then used to predict the y-value for unseen values of x. Here, m is the slope and c is the intercept of the line. These two parameters (m and c) are estimated by fitting a straight line to the data by minimizing the RMSE (root mean squared error). Hence, these parameters are called the model parameters. 

**Examples: **
- m (slope) and c (intercept) in Linear Regression
- Weights and biases in Neural Networks. 

### Model Hyperparameter

A model hyperparameter is a parameter whose value is set before the model starts training. They cannot be learned by fitting the models to the data. 


![model hyperparameter - machine learning - learnml.xyz](https://cdn.hashnode.com/res/hashnode/image/upload/v1648093134288/1uPJwIYgm.png)

In the above plot, the x-axis represents the number of epochs and the y-axis represents the number of epochs. We can see after the certain point when epochs are more than then although the training accuracy increases but the validation and test accuracy starts decreasing. This is a case of overfishing. Here the number of epochs is a hyperparameter and is set manually. Setting this number to a small value may cause underfitting and a high value may cause overfitting.

**Model hyperparameters in different models:**

1. Learning rate in gradient descent
2. Number of iterations in gradient descent
3. Number of layers in a Neural Network
4. Number of neurons per layer in a Neural Network
5. Number of clusters(k) in k means clustering

### Conclusion

In this article, we have seen the functionality of parameters and hyperparameters. I hope now it would be clear to you. Now let's see the key difference between them, 

| PARAMETERS                                                                                      | HYPERPARAMETER                                                                                                                                                                                       |
|-------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| They are required for making predictions                                                        | They are required for estimating the model parameters                                                                                                                                                |
| They are estimated by optimization algorithms(Gradient Descent, Adam, Adagrad)                  | They are estimated by hyperparameter tuning                                                                                                                                                          |
| They are not set manually                                                                       | They are set manually                                                                                                                                                                                |
| The final parameters found after training will decide how the model will perform on unseen data | The choice of hyperparameters decides how efficient the training is. In gradient descent, the learning rate decide how efficient and accurate the optimization process is in estimating the parameters |

