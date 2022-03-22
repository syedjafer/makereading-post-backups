## Normalization Vs Standardization

### Introduction

Feature Scaling is one of the most important data preprocessing steps in machine learning. Algorithms that compute the distance between the features are biased towards numerically larger values if the data is not scaled. Tree-based algorithms are fairly insensitive to the scale of the features. Also, feature scaling helps machine learning, and deep learning algorithms train and converge faster. There are some feature scaling techniques such as **Normalization and Standardization** that are the most popular and at the same time, the most confusing ones. 


### Normalization or Min-Max Scaling 

It used to transform features to be on a similar scale. The new point is calculated as, 


![Normalization Formula - Machine learning - learnml.xyz](https://cdn.hashnode.com/res/hashnode/image/upload/v1647949073708/DR-6W3HM8.png)

This scales the range to [0,1] or sometimes [-1, 1]. Geometrically speaking, transformation squished the n-dimensional data into an n-dimensional unit hypercube. Normalization is useful when there are no outliers as it cannot cope with them. Usually, we would scale age and not incomes because only a few people have high incomes but the age is close to uniform. 


### Standardization or Z-Score Normalization

Its the transformation of features by subtracting from mean and dividing by standard deviation. This is often called a Z-Score. 


![Normalization Formula - Machine learning - learnml.xyz](https://cdn.hashnode.com/res/hashnode/image/upload/v1647949340964/1r_zVdxVv.png)

Standardization can be helpful in cases where the data follows a Gaussian distribution. However, this does not have to be necessarily true. Geometrically speaking, it translates the data to the mean vector of original data to the origin and squishes or expands the points If **std** is 1 respectively. 

We can see that we are just changing mean and standard deviation to a standard normal distribution which is still normal thus the shape of the distribution is not affected. 

Standardization does not get affected by the outliers because there is no predefined range of the transformed features. 

