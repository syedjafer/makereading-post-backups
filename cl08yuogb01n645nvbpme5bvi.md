## Variance & Low Variance Filter

### Prerequisite

**Variance:** Variance tells us about the **spread of the data**.  It tells us how far the points are from the mean. Its the average square of the difference between each data point with the mean of the data points. 


![linear_regression_naive_1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646185728800/N-2Gz8gZg.png)

From the above image, we can see that variance is the difference between blue point (data point) with the yellow line (mean)

Formula to calculate the Variance is , 


![Screenshot from 2022-03-02 08-29-11.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646190089193/mWoF96Luj.png)


### Introduction

In the previous article,  [Missing Value Ratio and its Implementation](https://blog.learnml.xyz/the-missing-value-ratio), we saw a feature selection technique Missing Value Ratio. In this article, we’re going to cover another technique of feature selection known as Low variance Filter.

### Dataset & Notebook

We can consider the titanic dataset itself, with some imputed values. ( Checkout this notebook for reference ). 

![Screenshot from 2022-03-02 07-28-21.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646186318702/IV9iEje7P.png)

after imputing the 'travelled' column with all values as 1. 


![Screenshot from 2022-03-02 07-29-01.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646186356729/1IF7h6ZGk.png)

Notebook Link : Please checkout this [notebook](https://colab.research.google.com/drive/1h7FbL7xrHXyhNY_n5nlNjU-4nRcHhS2t?usp=sharing), which contains the experiments done in this article.  

### What is low variance filter ?

Low variance filter, is the process of removing the variables which are less contributing to/affecting the target variable. In order to accomplish this, we will set a threshold level and filter out the variables which are having variance less than the threshold level . 

### Explanation

Let us consider our imputed titanic dataset, 

![Screenshot from 2022-03-02 07-29-01.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646186911471/Ybxh8TbkE.png)

We can see the column "travelled", is almost having the same values. Do you think the variable "travelled" will affect the survival ? Remember all the values of "travelled" are the same.

The answer is, No. It will not affect the "Survived" variable. If we check the variance of "travelled", it will come out to be zero.


![Screenshot from 2022-03-02 07-40-56.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646187067922/AOdMn6qJr.png)


We can see that variables with low variance have less impact on the target variable. Next, we can set a threshold value of variance. And if the variance of a variable is less than that threshold, we can see if drop that variable, but there is one thing to remember and it’s very important, **Variance is range-dependent,** therefore we need to do **normalization** before applying this technique.

### implementation of Low Variance Filter

Now let’s implement it in Python and see how it works in a practical scenario. As always we’ll first import the required libraries-

```python
import pandas as pd
from sklearn.preprocessing import normalize
```
We discuss the use of normalization while calculating variance. Hence, we are importing it into our implementation here. Don’t worry we’ll see where to apply it.

```python
data.head()
```


![Screenshot from 2022-03-02 07-48-27.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646187518879/YdXYnT5aA.png)


Again, have a few independent variables and a target variable, which is essentially **Survived** . A quick look at the shape of the data-

```python
data.shape
```

![Screenshot from 2022-03-02 07-49-37.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646187588886/JI3X0zoEh.png)

It confirms we are working with 13 variables or columns and have 891 observations or rows. Now, let’s check whether we have missing values or not-

```python
data.isnull().sum()/len(data)*100
```


![Screenshot from 2022-03-02 07-50-45.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646187660572/AQ0ecQHAj.png)


we are having some missing values, so we can apply "Missing Value Ratio" (from the previous article)  methodology here to reduce dimensions. 

```python
# Missing Value Ratio

missing_val_percentage = data.isnull().sum()/len(data)*100
filtered_columns = [ ]
threshold_level = 40
for index, column in enumerate(data.columns):
    if missing_val_percentage[index] <= threshold_level:
        filtered_columns.append(column)
new_data = data[filtered_columns]
new_data.shape

```

![Screenshot from 2022-03-02 07-53-44.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646187835820/uHehHWFLi.png)


Our next step is to normalize the variables because variance remember is range dependent. And as we saw in our dataset, the variables have a pretty high range, which will skew our results. So go ahead and do that

For easy purpose, we can consider only number variables for our calculations


```python
data = new_data[['Survived', 'Pclass', 'Age', 'SibSp', 'Parch', 'Fare', 'travelled' ]]
```

![Screenshot from 2022-03-02 07-59-38.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646188204559/oyhNsWDPs.png)

We need to handle the [missing values in a meaningful way](https://blog.learnml.xyz/tactics-to-handle-missing-values). For time being we can fill all the NaN to 0. 

```python
data.fillna(0, inplace=True)
normalize = normalize(data)
```

Save the result in a data frame called data_scaled, and then use the .var() function to calculate the variance

```python

data_scaled = pd.DataFrame(normalize)
data.columns, data_scaled.var()
```


![Screenshot from 2022-03-02 08-04-15.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646188470802/b9cH3crxc.png)

Something strange, 
. <br>
.<br>
.<br>
.<br>
.<br>
.<br>
.<br>
.<br>
.<br>
.<br>

The columns survived, pclass, SibSp, Parch were also having low variance. Its because these are categorical variables. 

> Note: Remember we should apply the variance filter only on numerical variables. If we have categorical variables, we can look at the frequency distribution of the categories. And if a single category is repeating more frequently, let’s say by 95% or more, you can then drop that variable. 

For understanding low variance filter, we can ignore the above condition. 

We’ll store the variance results in a new column and the column names in a different variable

```python
#storing the variance and name of variables

variance = data_scaled.var()
columns = data.columns
```

Next comes the for loop again. We’ll set a threshold of 0.004. So if the variable has a variance greater than a threshold, we will select it and drop the rest. So let me go ahead and implement that,

```python
#saving the names of variables having variance more than a threshold value

variable = [ ]

for index, var in enumerate(variance):
    if var>=0.004: #setting the threshold as 1%
        variable.append(columns[index])
```


![Screenshot from 2022-03-02 08-11-18.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646188892465/48YtoxQU2.png)


All right. So let’s see what we have

```python
variable
```

![Screenshot from 2022-03-02 08-11-50.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646188922945/IIp_v-eKd.png)

We can see some columns has been dropped, 

```python
# creating a new dataframe using the above variables
new_data = data[variable]

# first five rows of the new data
new_data.head()
```


![Screenshot from 2022-03-02 08-13-17.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646189010038/_aMPyT9iW.png)
 
Now, we have reduced the dimensions of the data and its better than the initial one. 

### Conclusion
1. We have seen the implementation of the low variance filter from scratch and we understood how its reducing the dimensions of the data. 
2. Apply these low variance filter only to the numerical columns (dont apply it in the categorical variables).


