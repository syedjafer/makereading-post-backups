## The Curse of Dimensionality

### Prerequisite
- Polynomial Regression - https://learnml.hashnode.dev/the-polynomial-regression

### Introduction

Curse of Dimensionality refers to a set of problems that arise when working with high-dimensional data. The dimension of a dataset corresponds to the number of attributes/features that exist in a dataset. A dataset with a large number of attributes, generally of the order of a hundred or more, is referred to as high dimensional data. Some of the difficulties that come with high dimensional data manifest during analyzing or visualizing the data to identify patterns, and some manifest while training machine learning models. The difficulties related to training machine learning models due to high dimensional data is referred to as ‘**Curse of Dimensionality**’. 

> Note: All the Experiments executed in this article is available in this [colab notebook](https://colab.research.google.com/drive/1g3xfikqXZmBg-nePiAxzZ2GoX4wWHxK8?usp=sharing)

### What is the problem with more dimension ?

Let us consider a dataset , 

```python
np.random.seed(0)
x = 2 - 3 * np.random.normal(0, 1, 20)
y = x - 2 * (x ** 2) + 0.5 * (x ** 3) + np.random.normal(-3, 3, 20)
```


![Screenshot from 2022-02-21 07-37-25.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645409265218/JRxzgZvtS.png)

We can plot this data in dimension wise, 

#### 1 D - One Dimension.

```python
ax = sns.rugplot(x=x)
plt.xlabel("X-Axis")
plt.title("1D")
```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645409344653/PXmNULIDq.png)

we can see the points in the x-axis (at the bottom) are more close to each other.

#### 2D - Two Dimension

Now we can consider y-axis also and plot the graph in 2D

```python
plt.scatter(x,y, s=10)
plt.show()
```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645409442191/B9ZVTRPmD.png)

Now, we can see the points are moved some distance from each other . Its closer, but not as much closer as in 1D. 

#### 3D - Three Dimension

Now let us introduce some more features using polynomial and then plot the same. 

```python
from sklearn.preprocessing import PolynomialFeatures
polynomial_features= PolynomialFeatures(degree=1)
x_poly = polynomial_features.fit_transform(x)
```

<iframe src="https://syedjafer.github.io/ML-Vault/" height="400" width="800" title="Iframe Example"></iframe>

In the 3 Dimensional Space, we can see the points are getting far again from each other. 

So we figured the first problem, 

**When the Dimension Increases,  the data points are moving from denser to sparse area. ** 

There is also another problem when data points are in higher dimensions , every point is of approx. equi distance from each other. This affects the algorithms that are based on distance ( kNN and more. )

Mathematical Proof : https://journalofbigdata.springeropen.com/articles/10.1186/s40537-017-0083-6 

Distance concentration refers to the problem of all the pairwise distances between different samples/points in the space converging to the same value as the dimensionality of the data increases. Several machine learning models such as clustering or nearest neighbours’ methods use distance-based metrics to identify similar or proximity of the samples. Due to distance concentration, the concept of proximity or similarity of the samples may not be qualitatively relevant in higher dimensions. 

### Explanation

Let's take our previous article on [Polynomial Regression](https://learnml.hashnode.dev/the-polynomial-regression) and let's see what happens when we increase the dimensions (adding more features) 

```python

degree = []
rmse_list = []
r2_list = []
for deg in range(2, 200, 3):
  polynomial_features= PolynomialFeatures(degree=deg)
  x_poly = polynomial_features.fit_transform(x)
  degree.append(deg)
  model = LinearRegression()
  model.fit(x_poly, y)
  y_poly_pred = model.predict(x_poly)

  rmse = np.sqrt(mean_squared_error(y,y_poly_pred))
  r2 = r2_score(y,y_poly_pred)
  rmse_list.append(rmse)
  r2_list.append(r2)
  print(rmse, r2)
```

will result in the below graph, 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645415972429/7bYmzy1uwd.png)

As we increasing the dimensions (new features), after a certain point both the RMSE and R<sup>2</sup> score is getting reduced drastically . This observation is called as **Hughes phenomenon**

> Hughes Phenomenon: For a fixed size dataset the performance of a machine learning model decreases as the dimensionality increases.

### Notebook

COLAB Notebook : https://colab.research.google.com/drive/1g3xfikqXZmBg-nePiAxzZ2GoX4wWHxK8?usp=sharing

### Conclusion

Curse of Dimensionality is affecting the model when we have many features. By this, we need to neglect less contributing features for the training. So that we don't fall into this pit or else we need to combine n features to 1 features to solve this probem.
. <br>
. <br>
. <br>
Wait 
. <br>
. <br>
. <br>
. <br>
Is there any way to combine n features to 1, like reducing the dimensions. yes, there is one. 
Dimensionality reduction is an important technique to overcome the curse of dimensionality in data science and machine learning. As the number of predictors (or dimensions or features) in the dataset increase, it becomes computationally more expensive (ie. increased storage space, longer computation time) and exponentially more difficult to produce accurate predictions in classification or regression models. Moreover, it is hard to wrap our head around to visualize the data points in more than 3 dimensions.

We will see more about dimensionality reduction in upcoming articles.

### Interview Questions
1. What is the Curse of Dimensionality?
2. What is the Curse of Dimensionality and how can Unsupervised Learning help with it? 
3. Why is data more sparse in a high-dimensional space?
4. How does the Curse of Dimensionality affect Machine Learning models?
5.  How does High Dimensionality affect Distance-Based Mining Applications?
6. Does kNN suffer from the Curse of Dimensionality and if it why?
7. How does the Curse of Dimensionality affect k-Means Clustering?
 
