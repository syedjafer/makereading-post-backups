## High Correlation filter

%%[socialshare]

### Introduction

In the previous article, [Variance and Low variance filter](https://blog.learnml.xyz/variance-and-low-variance-filter) we saw a feature selection technique Missing Value Ratio. In this article, we’re going to cover another technique of feature selection known as the High Correlation filter.

### Dataset & Notebook
In this article, we are going to use the titanic dataset itself, with some imputed values. (Check out this notebook for reference ).


![titanic dataset for high correlation filter](https://cdn.hashnode.com/res/hashnode/image/upload/v1646279383310/UJREnYq6O.png)

> Notebook: https://colab.research.google.com/drive/1h7FbL7xrHXyhNY_n5nlNjU-4nRcHhS2t#scrollTo=QYOsfz4O2kSH

### What is a High Correlation Filter?

A high correlation between two variables means they have similar trends and are likely to carry similar information. This can bring down the performance of some models drastically (linear and logistic regression models, for instance).

We can calculate the correlation between **independent numerical variables** that are numerical. If the correlation coefficient crosses a certain threshold value, we can drop one of the variables (dropping a variable is highly subjective and should always be done keeping the domain in mind).

> Note: Same as Low Variance Filter, we can apply this only to numerical variables and not to categorical variables.

**As a general guideline, we should keep those variables that show a decent or high correlation with the target variable.**

### Explanation

Let us consider our titanic dataset,

```python
data = pd.read_csv("https://raw.githubusercontent.com/syedjafer/datasets/main/titanic.csv")
data.head()
```

![Titanic Dataset - High Correlation filter, dimensionality reduction](https://cdn.hashnode.com/res/hashnode/image/upload/v1646279646982/_9AnXWAhu.png)

Now we can calculate correlation between different variables, 

```python
data.corr()
```


![correlation of the titanic dataset - high correlation filter - dimensionality reduction](https://cdn.hashnode.com/res/hashnode/image/upload/v1646279723627/MLob_i55o.png)

we can try to visualize using seaborn, 


![sns heat map correlation of the titanic dataset - high correlation filter - dimensionality reduction](https://cdn.hashnode.com/res/hashnode/image/upload/v1646279757101/qO3ZpnyT7.png)

from the above, we can see the variables Parch and SibSp are having greater correlation so we can remove any one of them. 

Here were are removing the variable Parch. 

```python
data.drop(axis=1, columns=["Parch"])
```

![pandas data dropping parch from titanic dataset - high correlation filter](https://cdn.hashnode.com/res/hashnode/image/upload/v1646280073378/_uUv4eWRs.png)

Now we have reduced one variable, thus reduced one dimension of the data. 

> Note: Generally, if the correlation between a pair of variables is greater than 0.5-0.6, we should seriously consider dropping one of those variables.


### When to use a high correlation filter?

A pair of variables having high correlation increases multi-collinearity in the dataset. So, we can use this technique to find highly correlated features and drop them accordingly


### Conclusion
1. We have seen the implementation of a high correlation filter from scratch and we understood how it's reducing the dimensions of the data.
2. Apply these high correlation filters only to the numerical columns (don't apply them in the categorical variables).
3. Remember, when two variables are closely related to each other, then we need to select only one of them.

