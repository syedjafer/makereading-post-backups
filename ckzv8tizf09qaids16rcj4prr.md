## The Polynomial Regression

### Prerequisite

1. Linear Regression from Scratch - https://learnml.hashnode.dev/linear-regression-with-gradient-descent-scratch
2. Project on Linear Regression - https://learnml.hashnode.dev/project-predicting-salary-with-simple-linear-regression

### Notebook

Colab Notebook : https://colab.research.google.com/drive/1GACG2UAucdcQqaR1a2qY4N-_AK3RtYSW?usp=sharing

Feel free to tryout the learning in this article. 

### Introduction

In the linear regression, we had one assumption ; that the data should be linear in nature. Simple Linear Regression can't handle the **non-linearity** in the data. This could be solved by introducing quadratic variables inside the function and this is called as polynomial regression. We will see in detail of these steps and lets derive the polynomial regression. 

### What is the problem with Linear regression ?

Let us create a dataset, 

```python
# Imports

import numpy as np
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

from matplotlib import rcParams
plt.style.use('fivethirtyeight')
# figure size in inches
rcParams['figure.figsize'] = 11.7,5.27

np.random.seed(0)
x = 2 - 3 * np.random.normal(0, 1, 20)
y = x - 2 * (x ** 2) + 0.5 * (x ** 3) + np.random.normal(-3, 3, 20)
plt.scatter(x,y, s=10)
plt.show()

```  

Output will look like this, 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645350532994/jMjiTMSLG.png)

Now let us try applying Linear Regression on top of this dataset, 

```python

from sklearn.linear_model import LinearRegression

# transforming the data to include another axis
x = x[:, np.newaxis]
y = y[:, np.newaxis]

model = LinearRegression()
model.fit(x, y)
y_pred = model.predict(x)

plt.scatter(x, y, s=10)
plt.plot(x, y_pred, color='r')
plt.show()

```

Resultant linear model will look like this, 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645350648726/bCDWRcIqz.png)

Now let us evaluate the model using the [Regression Evaulation Metrics](https://learnml.hashnode.dev/evaluation-metrics-used-in-regression) . Here we can use RMSE and R<sup>2</sup>

```python
from sklearn.metrics import mean_squared_error
from sklearn.metrics import r2_score

rmse = np.sqrt(mean_squared_error(y, y_pred))
r2 = r2_score(y, y_pred)

print(f"RMSE of linear regression is {rmse}.")
print(f"R2 score of linear regression is {r2}")
```


![Screenshot from 2022-02-20 15-26-37.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645351041248/64Ei7Icro.png)

we can see the RMSE is pretty high and R<sup>2</sup> score is also low. Its perfoming low. we can't bend the curve to get it fit for the data. Since our line equation is 

> Y = mX + C

There is no quadratic part in our equation. 
.
.
.
.
.
.
.
💡Wait, did you got the idea, Why can't we introduce the quadratic or polynomial variables inside the equation to create a curve and apply gradient descent on top of it to get the best fit line . 

### Rise of Polynomial Regression 

Polynomial regression is a form of Linear regression where only due to the Non-linear relationship between dependent and independent variables we add some polynomial terms to linear regression to convert it into Polynomial regression.

To generate a higher order equation we can add powers of the original features as new features. The linear model,

> ![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645358759935/3paIxMGu7.png)

can be transformed to,

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645358784683/r3AYmnAfC.png)

This is still considered to be linear model as the coefficients/weights associated with the features are still linear. x² is only a feature. However the curve that we are fitting is quadratic in nature.

To convert the original features into their higher order terms we will use the **PolynomialFeatures** class provided by **scikit-learn**. Next, we train the model using Linear Regression.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645358905179/rpnBwzdtg.png)



It is quite clear from the plot that the quadratic curve is able to fit the data better than the linear line. Computing the RMSE and R²-score of the quadratic plot gives:


![Screenshot from 2022-02-20 17-43-03.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645359197396/qFqbgeeDz.png)

> We can see that RMSE has decreased and R²-score has increased as compared to the linear line.

we can try to increase the degree of the polynomial and experiment, 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645359255019/rw8XA6tqT.png)

if we are trying to substitute degree = 20, then we can see the line is connecting most of the data points ( Line is swiggled more to fit those points ) and this leads to **Curse of Dimensionality**

### Advantages of polynomial regression
1. You can model non-linear relationships between variables
2. There is a large range of different functions that you can use for fitting.
3. Good for exploration purposes: you can test for the presence of curvature and its inflections.

### Disadvantages of polynomial regression
1. Even a single outlier in the data plot can seriously mess up the results.
2. PR models are prone to overfitting. If enough parameters are used, you can fit anything. As John von Neumann reportedly said: “**with four parameters I can fit an elephant, with five I can make him wiggle his trunk.**”
3. As a consequence of the previous, PR models might not generalize well outside of the data used.

### Conclusion

Polynomial regression is a simple yet powerful tool for predictive analytics. It allows you to consider non-linear relations between variables and reach conclusions that can be estimated with high accuracy. This type of regression can help you predict disease spread rate, calculate fair compensation, or implement a preventative road safety regulation software.