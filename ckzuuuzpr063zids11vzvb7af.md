## Evaluation Metrics used in Regression

### Introduction

Machine Learning is a branch of Artificial Intelligence. It contains many algorithms to solve various real-world problems. Building a Machine learning model is not only the Goal of any data scientist but deploying a more generalized model is a target of every Machine learning engineer.

Regression is also one type of supervised Machine learning and in this tutorial, we will discuss various metrics for evaluating regression Models and How to implement them using the **sklearn library**.

### What is residual ?

We know that linear regression tries to fit a line that produces the smallest difference between predicted and actual values, where these differences are unbiased as well. This difference or error is also known as residual.

> **Residual = actual_vaue - predicted_value**

or <br>

> **e = y — ŷ**


![linear_regression_system_2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645320175663/qw0-TkUbm.png)

It is important to note that, before assessing or evaluating our model with evaluation metrics like 
R-squared, we must make use of residual plots.
Residual plots expose a biased model than any other evaluation metric. If your residual plots look normal, go ahead, and evaluate your model with various metrics. Residual plots show the residual values on the y-axis and predicted values on the x-axis. If your model is biased you cannot trust the results.
Residual plot showing the errors corresponding to the predicted values must be randomly distributed. However, if there are any signs of a systematic pattern, then your model is biased. 

#### What is bias ?

Consider the below graph, 


![Screenshot from 2022-02-20 06-38-28.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645319343478/3_aixs9Ow.png)


here, the sinusoidal line is our actual model value and the straight lines are derived by linear regression (best fit line). By seeing, its evident that there is a huge difference beween the actual value and the predicted value. This is having higher bias. Hope you got what bias means ?

#### But what does it mean by randomly distributed errors?

One of the assumptions of a linear regression model is that the errors must be normally distributed. This means, make sure your residuals are distributed around zero for the entire range of predicted values. Thus, if the residuals are evenly scattered, then your model may perform well.

### Why we require Evaluation Metrics ?

Most beginners and practitioners most of the time do not bother about the model performance. The talk is about building a well-generalized model, Machine learning model cannot have 100 per cent efficiency otherwise the model is known as a biased model. which further includes the concept of overfitting and underfitting.

It is necessary to obtain the accuracy on training data, But it is also important to get a genuine and approximate result on unseen data otherwise Model is of no use.

So to build and deploy a generalized model we require to Evaluate the model on different metrics which helps us to better optimize the performance, fine-tune it, and obtain a better result.

If one metric is perfect, there is no need for multiple metrics. To understand the benefits and disadvantages of Evaluation metrics because different evaluation metric fits on a different set of a dataset.

Now, I hope you get the importance of Evaluation metrics. let’s start understanding various evaluation metrics used for regression tasks.

### Dataset 

Here for the easy understanding, we can use simple linear regression dataset, it will be looking like this, 

![Screenshot from 2022-02-20 10-51-44.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645334521584/NKHmubepM.png)

```python
# Imports

import numpy as np
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

from sklearn.linear_model import LinearRegression

train_df = pd.read_csv("https://raw.githubusercontent.com/syedjafer/datasets/main/linear_regression/trains.csv")
test_df = pd.read_csv("https://raw.githubusercontent.com/syedjafer/datasets/main/linear_regression/test.csv")

```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645334631367/B56jQdfVm.png)


### Types of Evaluation Metrics

Evaluation metrics are a measure of how good a model performs and how well it approximates the relationship. Let us look at the most common ones, 
1. MSE - Mean Squared Error
2. MAE - Mean Absolute Error
3. R-squared 
4. Adjusted R-squared
5. RMSE - Root Mean Squared Error

We will derive each of these error functions logically and find the benefits of these, 

#### 1. Mean Squared Error ( MSE )

Let us consider our [linear regression problem](https://learnml.hashnode.dev/linear-regression-with-gradient-descent-scratch), 


![linear_regression_system_2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645321862181/IM3nwH357.png)

those red lines are the difference, 

Now we need to find the overall error of our to check how our model is working, 
Consider, [ -5, 10, -3, 5, -5, -2 ] are the differences between actual point and the predicted point. 
. <br>
. <br>
. <br>
. <br>
So this is simple right, why don't we use this itself as a metric, 
The problem is in this case, if we are finding the average error we would get zero ( Which means no error  ), but that is not right. 

> Note: We will get zero when we sum up the error values -5 + 10 + -3 + 5 + -5 + -2 = 0.

To avoid this effect of negative sign, we introduced squares and absolute. So the square and the absolute of a negative number is positive so the above effect is nullified. 

So now, we can focus on MSE,

By applying Squaring on error values, 

(-5)<sup>2</sup> + (10)<sup>2</sup> + (-3)<sup>2</sup> + (5)<sup>2</sup> + (-5)<sup>2</sup> + (-2)<sup>2</sup> 

= 25 + 100 + 9 + 25 + 25 + 4 (we can see now all errors are positive. )

= 188

This is a summed error value, so we can take the average, 

= 188 / 6 = 31.33

The formula that we used above is , 


![Screenshot from 2022-02-20 07-32-17.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645322554356/dSYmaGzV6.png)

 
MSE is a most used and very simple metric with a little bit of change in mean absolute error. Mean squared error states that finding the squared difference between actual and predicted value.

```python
from sklearn.metrics import mean_squared_error
print("MSE",mean_squared_error(y_test,y_pred))
```


**Advantages of MSE**
1. The graph of MSE is differentiable, so you can easily use it as a loss function.


**Disadvantages of MSE**
1. The value you get after calculating MSE is a squared unit of output. for example, the output variable is in meter(m) then after calculating MSE the output we get is in meter squared.

2. If you have outliers in the dataset then it penalizes the outliers most and the calculated MSE is bigger. So, in short, It is not Robust to outliers which were an advantage in MAE.

#### 2. Mean Absolute Error( MAE )

MAE is a very simple metric which calculates the absolute difference between actual and predicted values.

To better understand, let’s take an example you have input data and output data and use [Linear Regression](https://learnml.hashnode.dev/linear-regression-with-gradient-descent-scratch), which draws a best-fit line.

Now you have to find the MAE of your model which is basically a mistake made by the model known as an error. Now find the difference between the actual value and predicted value that is an absolute error but we have to find the mean absolute of the complete dataset.

so, sum all the errors and divide them by a total number of observations And this is MAE. And we aim to get a minimum MAE because this is a loss.

We can use the above scenario itself, 

Now we need to find the overall error of our to check how our model is working, 
Consider, [ -5, 10, -3, 5, -5, -2 ] are the differences between actual point and the predicted point. 

Instead of applying Squaring, we apply absolute on error values, 

|-5| + |10| + |-3| + |5| + |-5| + |-2|

= 5 + 10 + 3 + 5 + 5 + 2 (we can see now all errors are positive. )

= 25

This is a summed error value, so we can take the average, 

= 25 / 6 = 4.1


![Screenshot from 2022-02-20 08-24-34.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645325688880/iwK2aOlJw.png)

```python
from sklearn.metrics import mean_absolute_error
print("MAE",mean_absolute_error(y_test,y_pred))
```

**Advantages of MAE**
1. The MAE you get is in the same unit as the output variable.
2. It is most Robust to outliers.

**Disadvantages of MAE**
1. The graph of MAE is not differentiable so we have to apply various optimizers like Gradient descent which can be differentiable.

#### 3. Root Mean Squared Error (RMSE)

As RMSE is clear by the name itself, that it is a simple square root of mean squared error.


![Screenshot from 2022-02-20 08-32-39.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645326174116/4TdGSF2Enf.png)


> Note: RMSD and RMSE are same. 

```python
print("RMSE",np.sqrt(mean_squared_error(y_test,y_pred)))
```

**Advantages of RMSE **
1. The output value you get is in the same unit as the required output variable which makes interpretation of loss easy.

**Disadvantages of RMSE**
1. It is not that robust to outliers as compared to MAE.


#### 4. Root Mean Squared Log Error ( RMSLE )

Taking the log of the RMSE metric slows down the scale of error. The metric is very helpful when you are developing a model without calling the inputs. In that case, the output will vary on a large scale.

To control this situation of RMSE we take the log of calculated RMSE error and resultant we get as RMSLE.

It is a very simple metric that is used by most of the datasets hosted for Machine Learning competitions.

The Root Mean Squared Log Error (RMSLE) can be defined using a slight modification on sklearn's mean_squared_log_error function, which itself a modification on the familiar Mean Squared Error (MSE) metric.


![Screenshot from 2022-02-20 08-36-19.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645326394253/wTLleibyc.png)

```python
print("RMSE",np.log(np.sqrt(mean_squared_error(y_test,y_pred))))
````

Comparison between RMSE and RMSLE, 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645329414360/Dge5JxOQ3.png)

**Advantages of RMSLE**
1. Robustness to the effect of outliers ->  the outliers are drastically scaled down therefore nullifying their effect.
2. RMSLE metric only considers the relative error between the Predicted and the actual value and the scale of the error is not significant.

#### 5. R Squared (R2)

<iframe width="800" height="500" src="https://www.youtube.com/embed/2AQKmw14mHM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

What is R in R<sup>2</sup> ? If R is there, then why R<sup>2</sup>. 

R - Correlation of the dependent variables, The Correlation value exists between -1 to 1. If the correlation value of the variable is closer to -1 or 1 then we can say its having good relationship. If its closer to 0 then its lame. 

R<sup>2</sup> is just the Square of R. so it exists between 0 to 1. 

R2 score is a metric that tells the performance of your model, not the loss in an absolute sense that how many wells did your model perform.

In contrast, MAE and MSE depend on the context as we have seen whereas the R2 score is independent of context.


![Screenshot from 2022-02-20 10-40-29.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645333854541/Z9ASzFiS3.png)

So, with help of R squared we have a baseline model to compare a model which none of the other metrics provides. The same we have in classification problems which we call a threshold which is fixed at 0.5. So basically R2 squared calculates how must regression line is better than a mean line.

Hence, R2 squared is also known as Coefficient of Determination or sometimes also known as Goodness of fit.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645333735984/6nNGSYgxP.png)

Now, how will you interpret the R2 score? suppose If the R2 score is zero then the above regression line by mean line is equal means 1 so 1-1 is zero. So, in this case, both lines are overlapping means model performance is worst, It is not capable to take advantage of the output column.

Now the second case is when the R2 score is 1, it means when the division term is zero and it will happen when the regression line does not make any mistake, it is perfect. In the real world, it is not possible.

So we can conclude that as our regression line moves towards perfection, R2 score move towards one. And the model performance improves.

The normal case is when the R2 score is between zero and one like 0.8 which means your model is capable to explain 80 per cent of the variance of data.

```python
residual_of_mean_line = mean_squared_error(y_test, [np.mean(train_df['x'])]*len(test_df['y']))
residual_of_regression_line = mean_squared_error(y_test, y_pred)
r_squared = (residual_of_mean_line - residual_of_regression_line)/residual_of_mean_line
print(r_squared)
```

#### 6. Adjusted R Squared

The disadvantage of the R2 score is while adding new features in data the R2 score starts increasing or remains constant but it never decreases because It assumes that while adding more data variance of data increases.

But the problem is when we add an irrelevant feature in the dataset then at that time R2 sometimes starts increasing which is incorrect.

Hence, To control this situation Adjusted R Squared came into existence.

![Screenshot from 2022-02-20 09-59-22.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645331380537/t_XvW4qcu.png)

Now as p increases by adding some features so the denominator will decrease, N - 1 will remain constant. R2 score will remain constant or will increase slightly so the complete answer will increase and when we subtract this from one then the resultant score will decrease. so this is the case when we add an irrelevant feature in the dataset.

And if we add a relevant feature then the R2 score will increase and 1 - R2 will decrease heavily and the denominator will also decrease so the complete term decreases, and on subtracting from one the score increases.

### Notebook: 

Colab Notebook : https://colab.research.google.com/drive/1Hxuwh8PTKbCOyGbsFCqkBrex-8VohwN-?usp=sharing

### Conclusion

In the above we have seen how each metric is been derived and the intuitive reason behind it. There is not anyone metric that always performs well and helps to build the generalized model. There can be situations where you have to use different evaluation metrics and if you are a beginner then you should try all these metrics which will help you to get a better understanding of each to evaluate when you can use which metric.
