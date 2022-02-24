## Tactics to Handle Missing Values

### Introduction

In our daily life, we might have come across different surveys, polls, forms to fill in our view. In all those stuffs, as an individual we might not give all the information that is been asked or we might neglect some of the details, or we might not need to tell the other person what we feel. 

The problem of missing value is quite common in many real-life datasets. Missing value can bias the results of the machine learning models and/or reduce the accuracy of the model. This article describes what is missing data, how it is represented, and the different reasons for the missing data. Along with the different categories of missing data, it also details out different ways of handling missing values with examples.

### Dataset and Notebook

in this article we are going to use the ["Titanic"](https://github.com/syedjafer/datasets/blob/main/titanic.csv) dataset to explore. Please checkout this colab notebook which covers all the functions done here. 

### What is a Missing Value?
Missing data is defined as the values or data that is not stored (or not present) for some variable/s in the given dataset. Below is a sample of the missing data from the Titanic dataset. You can see the columns ‘Age’ and ‘Cabin’ have some missing values.


![Screenshot from 2022-02-23 14-50-31.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645608546662/RftxJPsLu.png)

### How is Missing Value Represented In The Dataset?

In the dataset, blank shows the missing values. In Pandas, usually, missing values are represented by NaN (Not a Number.)


![Screenshot from 2022-02-23 14-59-57.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645608611542/3fsEgEdl4.png)

### Why Is Data Missing From The Dataset ?

1. Data might have been corrupted to poor maintainance / loss.
2. Data might not be collected due to human error.
3. The user has not provided the values intentionally.
4. Data, might not have been avaialble in the first end. 

### Types Of Missing Values in Data

Missing values is been categorized into 3. They are, 
1. Missing Completely At Random (MCAR)
2. Missing At Random (MAR)
3. Missing Not At Random (MNAR)


![Screenshot from 2022-02-23 15-32-29.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645610576121/Fp66gjAlI.png)

#### 1. Missing Completely At Random
In MCAR, the probability of data being missing is the same for all the observations.

In this case, there is no relationship between the missing data and any other values observed or unobserved (the data which is not recorded) within the given dataset. That is, missing values are completely independent of other data. There is no pattern.

In the case of MCAR, the data could be missing due to human error, some system/equipment failure, loss of sample, or some unsatisfactory technicalities while recording the values.

For Example, suppose in a library there are some overdue books. Some values of overdue books in the computer system are missing. The reason might be a human error like the librarian forgot to type in the values. So, the missing values of overdue books are not related to any other variable/data in the system.
It should not be assumed as it’s a rare case. The advantage of such data is that the statistical analysis remains unbiased.

##### 2. Missing At Random (MAR)

Missing at random (MAR) means that the reason for missing values can be explained by variables on which you have complete information as there is some relationship between the missing data and other values/data.

In this case, the data is not missing for all the observations. It is missing only within sub-samples of the data and there is some pattern in the missing values.

For example, if you check the survey data, you may find that all the people have answered their ‘Gender’ but ‘Age’ values are mostly missing for people who have answered their ‘Gender’ as ‘female’. (The reason being most of the females don’t want to reveal their age.)

So, the probability of data being missing depends only on the observed data. In this case, the variables ‘Gender’ and ‘Age’ are related and the reason for missing values of the ‘Age’ variable can be explained by the ‘Gender’ variable but you can not predict the missing value itself.

Suppose a poll is taken for overdue books of a library. Gender and the number of overdue books are asked in the poll. Assume that most of the females answer the poll and men are less likely to answer. So why the data is missing can be explained by another factor that is gender.

In this case, the statistical analysis might result in bias. Getting an unbiased estimate of the parameters can be done only by modelling the missing data.

#### 3. Missing Not At Random (MNAR)

Missing values depend on the unobserved data.

If there is some structure/pattern in missing data and other observed data can not explain it, then it is Missing Not At Random (MNAR).

If the missing data does not fall under the MCAR or MAR then it can be categorized as MNAR.

It can happen due to the reluctance of people in providing the required information. A specific group of people may not answer some questions in a survey.

For example, suppose the name and the number of overdue books are asked in the poll for a library. So most of the people having no overdue books are likely to answer the poll. People having more overdue books are less likely to answer the poll.

So in this case, the missing value of the number of overdue books depends on the people who have more books overdue. Another example, people having less income may refuse to share that information in a survey. In the case of MNAR as well the statistical analysis might result in bias.

### Why Do We Need To Care About Handling Missing Value?

It is important to handle the missing values appropriately.

- Many machine learning algorithms fail if the dataset contains missing values. However, algorithms like K-nearest and Naive Bayes support data with missing values.
- You may end up building a biased machine learning model which will lead to incorrect results if the missing values are not handled properly.
- Missing data can lead to a lack of precision in the statistical analysis.

### Checking for missing values

The first step in handling missing values is to look at the data carefully and find out all the missing values.

The following code shows the total number of missing values in each column. It also shows the total number of missing values in entire data set.

```python
data = pd.read_csv("https://raw.githubusercontent.com/syedjafer/datasets/main/titanic.csv")
data.isnull().sum()
```


![Screenshot from 2022-02-23 15-41-33.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645611106915/0860KhQWd.png)

From the above output, we can see that there are 3 columns, Age, Cabin, Embarked are having missing values. 

### Figure Out How To Handle The Missing Data
Analyze each column with missing values carefully to understand the reasons behind the missing values as it is crucial to find out the strategy for handling the missing values.
There are 2 primary ways of handling missing values:

1. Deleting the Missing values
2. Imputing the Missing Values 

### Deleting the Missing value

Generally, this approach is not recommended. It is one of the quick and dirty techniques one can use to deal with missing values.

If the missing value is of the type Missing Not At Random (MNAR), then it should not be deleted.

If the missing value is of type Missing At Random (MAR) or Missing Completely At Random (MCAR) then it can be deleted.

The disadvantage of this method is one might end up deleting some useful data from the dataset.

There are 2 ways one can delete the missing values:
#### 1. Deleting the entire row

If a row has many missing values then you can choose to drop the entire row.
If every row has some (column) value missing then you might end up deleting the whole data.

```python

data.dropna(axis=0, inplace=True)
data.isnull().sum()
```

![Screenshot from 2022-02-23 16-52-23.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645615363684/Pn8lAv6F2.png)

#### 2. Deleting the entire column

If a certain column has many missing values then you can choose to drop the entire column.
Code to drop the entire column is as follows:


![Screenshot from 2022-02-23 16-56-33.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645615618552/fJr06T-dm.png)

In the above image, we can see that "Cabin" column is having more number of null values. So we can remove the entire column. 

```python
df = data.drop(['Cabin'],axis=1)
df.isnull().sum()
```

![Screenshot from 2022-02-23 16-58-11.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645615701645/B-LiL5o72.png)

### Imputing the Missing Value

There are different ways of replacing the missing values. You can use the python libraries Pandas and Sci-kit learn as follows:

#### 1. Replacing With Arbitrary Value

If you can make an educated guess about the missing value then you can replace it with some arbitrary value using the following code.

Ex. In the following code, we are replacing the missing values of the ‘Age’ column with ‘20’.

```python
data['Age'] = data['Age'].fillna(20)
data['Age'].isnull().sum()
```

![Screenshot from 2022-02-23 17-16-23.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645616794973/xwEpAWigk.png)

#### 2. Replacing With Mean

This is the most common method of imputing missing values of numeric columns. If there are outliers then the mean will not be appropriate. In such cases, outliers need to be treated first.

You can use the ‘fillna’ method for imputing the columns ‘Age’  with the mean of the column values.

```python
data = pd.read_csv("https://raw.githubusercontent.com/syedjafer/datasets/main/titanic.csv")
data["Age"] = data["Age"].fillna(data["Age"].mean())
data["Age"].isnull().sum()
```

![Screenshot from 2022-02-23 17-20-12.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645617025663/FgnoQgZ2T.png)

#### 3. Replacing With Mode

Mode is the most frequently occurring value. It is used in the case of categorical features.

You can use the ‘fillna’ method for imputing the categorical columns 'Embarked'

```python
data["Embarked"] = data["Embarked"].fillna(data["Embarked"].mode())
data["Embarked"].isnull().sum()
```

![Screenshot from 2022-02-23 17-24-43.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645617306652/qjQ3X8Obn.png)


#### 4. Replacing With Median

Median is the middlemost value. It’s better to use the median value for imputation in the case of outliers.
You can use ‘fillna’ method for imputing the column ‘Age’ with the median value.

```python
data = pd.read_csv("https://raw.githubusercontent.com/syedjafer/datasets/main/titanic.csv")
data['Age'] = data['Age'].fillna(data['Age'].median())

```


![Screenshot from 2022-02-24 20-55-22.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645716367524/MpOuOCbgR.png)

#### 5. Replacing with previous value – Forward fill

In some cases, imputing the values with the previous value instead of mean, mode or median is more appropriate. This is called forward fill. It is mostly used in time series data.

You can use ‘fillna’ function with the parameter 'method = ffill'

```python
test = pd.Series(range(6))
test.loc[2:4] = np.nan
test.fillna(method=‘ffill')
```


![Screenshot from 2022-02-24 20-57-56.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645716548867/LW3bxHEcu.png)

#### 6. Replacing with next value – Backward fill

In backward fill, the missing value is imputed using the next value.
```python
test.fillna(method='bfill')
```


![Screenshot from 2022-02-24 21-00-14.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645716642766/pyl-tHKEQ.png)


#### 7. Interpolation

Missing values can also be imputed using interpolation. Pandas interpolate method can be used to replace the missing values with different interpolation methods like ‘polynomial’, ‘linear’, ‘quadratic’. Default method is ‘linear’.

```python
test.interpolate()
```


![Screenshot from 2022-02-24 21-02-08.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645716740914/T25C777iB.png)


### Imputing Missing Values For Categorical Features

There are two ways to impute missing values for categorical features as follows:

#### 1. Impute the Most Frequent Value

We will make use of ‘SimpleImputer’ in this case and as this is a non-numeric column we can’t use mean or median but we can use most frequent value and constant.

```python
import pandas as pd
import numpy as np
X = pd.DataFrame({'Shape':['square', 'square', 'oval', 'circle', np.nan]})

```


![Screenshot from 2022-02-24 21-06-35.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645717006666/Ovs44XZzn.png)

```python
from sklearn.impute import SimpleImputer
imputer = SimpleImputer(strategy='most_frequent')
imputer.fit_transform(X)
```
![Screenshot from 2022-02-24 21-06-59.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645717033463/0lVTfukQg.png)

#### 2. Impute the Value “missing”, which treats it as a Separate Category

```python
imputer = SimpleImputer(strategy='constant', fill_value='missing')
imputer.fit_transform(X)
```


![Screenshot from 2022-02-24 21-09-01.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645717151190/5xQb1BcTT.png)

In any of the above approaches, you will still need to OneHotEncode the data (or you can also use some other encoder of your choice). After One Hot Encoding, in case 1, instead of the values ‘square’, ‘oval’,’ circle’, you will get three feature columns. And in case 2, you will get four feature columns (4th one for the ‘missing’ category). So it’s like adding the missing indicator column in the data. There is another way to add a missing indicator column, which we will discuss further.

### Imputation of Missing Value Using sci-kit learn Library

#### Univariate Approach
In a Univariate approach, only a single feature is taken into consideration. You can use the class SimpleImputer and replace the missing values with mean, mode, median or some constant value.

```python
import numpy as np
from sklearn.impute import SimpleImputer
imp = SimpleImputer(missing_values=np.nan, strategy='mean')
imp.fit([[1, 2], [np.nan, 3], [7, 6]])

X = [[np.nan, 2], [6, np.nan], [7, 6]]
print(imp.transform(X))

```

![Screenshot from 2022-02-24 21-12-18.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645717351327/Tee2gRA_l.png)


#### Multivariate Approach

In a multivariate approach, more than one feature is taken into consideration. There are two ways to impute missing values considering the multivariate approach. Using KNNImputer or IterativeImputer classes.

Let’s take an example of a titanic dataset.

Suppose the feature ‘age’ is well correlated with the feature ‘Fare’ such that people with lower fares are also younger and people with higher fares are also older.

In that case, it would make sense to impute low age for low fare values and high age for high fares values. So here we are taking multiple features into account by following a multivariate approach.

```python
import pandas as pd
df = pd.read_csv('http://bit.ly/kaggletrain', nrows=6)
cols = ['SibSp', 'Fare', 'Age']
X = df[cols]
```

![Screenshot from 2022-02-24 21-14-50.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645717501258/JjAeRjP6J.png)


```python
from sklearn.experimental import enable_iterative_imputer
from sklearn.impute import IterativeImputer
impute_it = IterativeImputer()
impute_it.fit_transform(X)
```

![Screenshot from 2022-02-24 21-15-31.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645717541852/LnBVUAEdo.png)

Let’s see how IterativeImputer works. For all rows, in which ‘Age’ is not missing sci-kit learn runs a regression model. It uses ‘Sib sp’ and ‘Fare’ as the features and ‘Age’ as the target. And then for all rows for which ‘Age’ is missing, it makes predictions for ‘Age’ by passing ‘Sib sp’ and ‘Fare’ to the training model. So it actually builds a regression model with two features and one target and then makes predictions on any places where there are missing values. And those predictions are the imputed values.


#### Nearest Neighbors Imputations (KNNImputer)

Missing values are imputed using the k-Nearest Neighbors approach where a Euclidean distance is used to find the nearest neighbors.

```python
from sklearn.impute import KNNImputer
impute_knn = KNNImputer(n_neighbors=2)
impute_knn.fit_transform(X)
```

![Screenshot from 2022-02-24 21-18-22.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645717713695/5ST_JCbo0.png)


### Conclusion
- It is critical to reduce the potential bias in the machine learning models and get the precise statistical analysis of the data.
- Handling missing values is one of the challenges of data analysis.
- Understanding different categories of missing data help in making decisions on how to handle it.
- We explored different categories of missing data and the different ways of handling it in this article.
- Missing values handling is a gigantic topic. In any case, it’s very important to understand your data well and why it’s missing, talk to the experts if possible to figure out what’s going on with the data before blindly following any of the above methods.

### References
1. sklearn library - https://scikit-learn.org/stable/modules/impute.html
2. sklearn github tips - https://github.com/justmarkham/scikit-learn-tips
3. Krish Naik - https://github.com/krishnaik06/Feature-Engineering-Live-sessions
