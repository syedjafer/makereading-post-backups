## Linear Regression with Gradient Descent ( Scratch )

> Colab Notebook For Tryout : [Linear Regression with Gradient Descent ( Scratch )](https://colab.research.google.com/drive/1dprgWzcNYFhVRfdEmDlQbqFJGyaGimMb?usp=sharing)

### Prerequisite

I would recommend you to go through the below youtube video on Gradient Descent. 

<iframe width="1000" height="600" src="https://www.youtube.com/embed/sDv4f4s2SB8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### 1. Introduction

Linear Regression is a machine learning algorithm based on **supervised learning**. It performs a **regression** task. Regression models a target prediction value based on independent variables. It is mostly used for finding out the relationship between variables and forecasting. Different regression models differ based on – the kind of relationship between dependent and independent variables, they are considering and the number of independent variables being used.

### 2. Explanation

Simple linear regression is useful for finding relationship between two continuous variables. One is predictor or independent variable and other is response or dependent variable. It looks for statistical relationship but not deterministic relationship. Relationship between two variables is said to be deterministic if one variable can be accurately expressed by the other. 

For example, using temperature in degree Celsius it is possible to accurately predict Fahrenheit. Statistical relationship is not accurate in determining relationship between two variables. For example, relationship between height and weight.

The core idea is to obtain a line that best fits the data. The best fit line is the one for which total prediction error (all data points) are as small as possible. Error is the distance between the point to the regression line.


![1_eeIvlwkMNG1wSmj3FR6M2g.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1644921182105/-XPy0z10l.gif)

Here, we can consider a dataset of height and weight. Then we will try to build a system from scratch to develop Simple linear regression. 


1.Consider the below dataset, 


```python
height = [150, 160, 155, 173, 180, 169]
weight = [48, 63, 60, 67, 72, 66]
``` 

![newplot.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644853811318/63SKkw_Op.png)



2.Now, the user is giving a new height - 165 of a person. We need to find the weight (approx.) of the person. 
As a first go, we can think of a general solution. We can take a **mean** value of the weight. Then we can say for a person with any height, we will return a **constant mean** value. ( Naive Idea )

```
mean_weight = weight.mean()
```

> Mean Weight = 62.666666666666664


![linear_regression_naive_1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644854514154/ycxUXXLntz.png)

3.We know that, Taking a mean wont be a good solution. So we can think of a different idea, we will take a look in to the data. 

```python
height = [150, 160, 155, 173, 180, 169]
weight = [48, 63, 60, 67, 72, 66]
``` 

From the data we can see, that height divided by 3 gives an approximated value of the weight. Its better than the Idea 1 (Taking Average.).


![linear_regression_system_2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644854814961/_JbuG7OFU.png)

Before going to the next idea, we need to define a mechanism to tell the validation of our model. For that we can try to find the residuals between the line and point. 
 
> Note: Residuals = Actual Point - Predicted Point. 


![linear_regression_system_2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644889677669/-IahR3VMi.png)

4.We can use the MSE ( Mean Squared Error ) Validation. 
```python
def mse(y, y_hat):
  return np.mean((y - y_hat)**2)
```
So, Now if we are trying to reduce the error, we can get the optimal solution to solve our problem. 

5.Since we are trying to plot the line, the equation of the line will be , 
> Y = M * X + C <br>
Y - Predicted Value <br>
M - Slope of the Line <br>
X - Actual Value <br>
C - Intercept of the X axis ( Point which crosses the X-axis )

So here, in our scenario Y is the Weight, X is the Height. We need to substitute some values for M (Slope) and Intercept (C) to get the equation of the **Best Fit Line**.

6.Now the problem is narrowed down to substitute some values for both M and C to get the optimal solution. Initially we can try to generate random values and will calculate the error value for analyzing. 

```python
for temp_m in zip(np.linspace(0, 1, num=100)):
  for temp_c in np.linspace(0, 1, num=100):
    line = temp_m*x + temp_c
    print(temp_m, "error", mse(weight, line))
```
> Note: Try running this code in this Colab Notebook. [Linear Regression with Gradient Descent ( Scratch )](https://colab.research.google.com/drive/1dprgWzcNYFhVRfdEmDlQbqFJGyaGimMb?usp=sharing)

7.After executing the code you will see the error is getting increased with the values. We can try to set between some start and end ranges to find the values. But this process is also tiresome. Is there any way to resolve this issue. 
. <br>
.<br>
.<br>
.<br>
.<br>
.<br>
.<br>
Yeah, We can use gradient descent algorithm ( I assume you went through the youtube video suggested at beginning )

Here, we can see a small overview of the gradient descent and the need for it. 

Let us consider a constant value for C, then we can change the values for M (random values). Then we can see how the error is behaving. 

```python
c = 1
error_val = []
temp_m_vals = np.linspace(0, 1, num=100)

for temp_m in zip(temp_m_vals):
    line = temp_m*x + c
    error_val.append(mse(weight, line))
```

If we plot temp_m_vals on x-axis and error_val on y-axis we can see a plot like this, 

![linear_regression_system_random_error_val.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644889919462/ckjpsBeVV.png)

From the above image its clear like error is minimum in the range of 0.3 to 0.45  of the model value. Our optimal solution is also hidden in there. We can go again and do the same above steps by just changing the linspace range with 0.3 to 0.45. But that wont be a generic approach for all problems. 

At the same time, we need to avoid more calculations to get the optimal solution. What to do ?
. <br>
. <br>
. <br>
. <br>
. <br>
. <br>

Let's look at the nature, 


![pexels-pixabay-414171.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1644890282241/3gAw0IiXl.jpeg)

Our motive is to attain the lowest point in the error value, 

![linear_regression_system_random_error_val_2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644890426501/1V48VpkEQ.png)

On seeing the above two images, we can consider a person who is climbing down the mountain ( U shaped mountain )



What will be his approach while climbing down, 


![1_N5WjbzwsCFse-KPjBWZZ6g.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1644899012737/RFUzHRukP.jpeg)

1. When there is a steep slope, he will be taking a big step. 
2. When there is a less steep slope, he will be taking smaller steps. 

By making this in an iteration he will reach the minimum point ( in his view, its the ground ). 

This process is known as Gradient Descent Algorithm (  Taking big steps when we are away from the minimum point and  small steps when we are near to the minimum point ). 

In our scenario, we need to simply take larger steps when the slope is having more steep, and smaller step when we have lesser steep. 


![linear_regression_system_random_error_val_3.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644900772524/qLbCrjjJy.png)

So now our problem is narrowed to find the slope of the curve and and move to a different point and continue the process, till we are having the error ideally to 0 or close to 0 ( Which mean less error ). 

To find the slope of the curve, we can use calculus ( Differenciation ).  The curve in the above image is formed with the MSE equation. 


![Screenshot from 2022-02-15 10-25-38.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644900960199/MipTgfLg0w.png)

```python
def mse(y, y_hat):
  return np.mean((y - y_hat)**2)
```

Lets differentitate and solve it, 

1.Initially let m = 0 and c = 0. Let L be our learning rate ( how fast ). This controls how much the value of m changes with each step. L could be a small value like 0.0001 for good accuracy.

2.Calculate the partial derivative (to find the slope of the curve) of the loss function (MSE) with respect to m, and plug in the current values of x, y, m and c in it to obtain the derivative value D.

![Screenshot from 2022-02-15 10-39-04.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644901791512/YNTJjHgXk.png)

3.D<sub>m</sub> is the value of the partial derivative with respect to m. Similarly lets find the partial derivative with respect to c, D<sub>c</sub>,

![Screenshot from 2022-02-15 15-14-58.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644918319965/NZ5xYsdYI.png)

4.After finding the slope w.r.t m and slope w.r.t c, we can update these values, 

![Screenshot from 2022-02-15 15-14-58.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644918385456/CMkgFKG8F0.png)

5.We repeat this process until our loss function is a very small value or ideally 0 (which means 0 error or 100% accuracy). The value of m and c that we are left with now will be the optimum values.

#### Model Implementation
```python
# Imports
import numpy as np

# Dataset
height = np.array([150, 160, 155, 173, 180, 169]) 
weight = np.array([48, 63, 60, 67, 72, 66])

# Define error function
def error(y_hat):
  return np.mean(np.square(y-y_hat))

def normalize(x):
  x = (x - min(x))/(max(x)-min(x))
  return x

x = normalize(height)
y = normalize(weight)


# Model Weights
m = 0.1
c = 0.1

# Hyperparameters
learning_rate = 0.001 # The learning Rate 0.1, 0.001, 0.0001 # adaptive learning rate
epochs = 30000 # The number of iterations to perform gradient descent

n = len(x)
error_vals = []

# Performing Gradient Descent
for i in range(epochs):
  # Forward propagation (basically multiplication)
  y_hat = m*x + c # The current predicted value of Y

  # Calculate Mean Squared Error
  error_vals.append(error(y_hat)) # Just for plotting purpose.

  # Find the Slope
  de_dm = (-2/n) * np.sum(x * (y - y_hat)) # Derivative of error function w.r.t m
  de_dc = (-2/n) * np.sum(y - y_hat) # Derivative of error function w.r.t c

  # Updating the weights
  m = m - (de_dm * learning_rate)
  c = c - (de_dc * learning_rate)

print("Intercept", c)
print("Slope", m)

```

> Note: In the model implementation, we are normalizing the values to avoid infinity error. Since we are squaring big numbers it will lead to infinity value (+inf, -inf). To avoid such issues, we are using normalizing functionality. 

#### Comparison with SkLearn Module. 

> Colab Link : [Linear Regression with Gradient Descent ( Scratch )](https://colab.research.google.com/drive/1dprgWzcNYFhVRfdEmDlQbqFJGyaGimMb?usp=sharing)

Sklearn is a python package dedicated for Machine learning, Now let us compare our implementation with the external package implementation. 

```python
from sklearn.linear_model import LinearRegression
import pandas as pd
train_df = pd.DataFrame({'x': x})
X = train_df[['x']]
y = y

reg = LinearRegression()
reg.fit(X, y)

# Our Scatch Implementation
print(f"From Scratch M {m}, C {c}")
print(f"From sklearn module M {reg.coef_[0]} C {reg.intercept_}")

```

![Screenshot from 2022-02-15 15-46-24.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644920210000/dImSTIKtY.png)

Try this in the shared colab notebook. Please comment below if you have any queries on the implementation. 

### 3. Advantages of Linear Regression. 
1. Linear regression has a considerably lower time complexity when compared to some of the other machine learning algorithms.
2. Linear regression fits linearly seperable datasets almost perfectly and is often used to find the nature of the relationship between variables.
3. When you know the relationship between the independent and dependent variable have a linear relationship, this algorithm is the best to use because of it’s less complexity to compared to other algorithms.
4. Linear Regression is susceptible to over-fitting but it can be avoided using some dimensionality reduction techniques, regularization (L1 and L2) techniques and cross-validation. (We will discuss these concepts )

### 4. Disadvantages of Linear Regression.
1. Linear Regression is Prone to underfitting.
2. Linear Regression is Sensitive to outliers. 
3. Diversely, linear regression assumes a linear relationship between dependent and independent variables. That means it assumes that there is a straight-line relationship between them. It assumes independence between attributes.
4. Prone to multicollinearity: Before applying Linear regression, multicollinearity should be removed (using dimensionality reduction techniques) because it assumes that there is no relationship among independent variables.

### 5. When to use Linear Regression
1. The relationship between the variables is linear.
2. The data is homoskedastic, meaning the variance in the residuals (the difference in the real and predicted values) is more or less constant.
3. The residuals are independent, meaning the residuals are distributed randomly and not influenced by the residuals in previous observations. If the residuals are not independent of each other, they’re considered to be autocorrelated.
4. The residuals are normally distributed. This assumption means the probability density function of the residual values is normally distributed at each x value. I leave this assumption for last because I don’t consider it to be a hard requirement for the use of linear regression, although if this isn’t true, some manipulations must be made to the model.

### 6. Interview Questions
1. What is Linear Regression Algorithm?
2. What are the basic assumptions of the Linear Regression Algorithm?
3. Explain the Gradient Descent algorithm with respect to linear regression.
4. Justify the cases where the linear regression algorithm is suitable for a given dataset.
5. What are the different validation models available for Linear Regression.
6. Which evaluation metric should you prefer to use for a dataset having a lot of outliers in it?
7. What is Multicollinearity?
8. Is linear regression suitable for time series analysis?
9. Can linear regression be used for representing quadratic equations? 
10. Explain what the Intercept Term means.
11. What is Heteroscedasticity?
12. What are the disadvantages of the linear regression model?
13. Give an example scenario where a multiple linear regression model is necessary. 
14. If your training error is 10% and your test error is 70%, what do you infer?

### 7. Implementation

Check out the project implemented with flask and angular based on the above article. 
Link to the project - https://learnml.hashnode.dev/project-predicting-salary-with-simple-linear-regression 

#machine-learning #linear-regression