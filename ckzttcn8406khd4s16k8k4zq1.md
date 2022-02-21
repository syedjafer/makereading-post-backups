## Distance Metrics in Machine Learning

> Note: COLAB Notebook : https://colab.research.google.com/drive/1FTpcP8friChkdBPqJzPfcGaIvsgxCaf2?usp=sharing

### Introduction

Everywhere is within walking distance if you have the time, said Steve Wright, an American comedian, writer and actor. This is true, but who has the time these days? As a result, distance becomes an important metric.

Both supervised and unsupervised algorithms in machine learning use **Distance Metrics** to understand patterns in the input data. This metric is also used for the **identification of similarities** between results. A strong distance metric helps to dramatically improve the efficiency of Clustering or Classification algorithm’s performance.

Ideally, distance metrics use a distance function that tells us the mathematically driven distance between various elements throughout the data set. Closer the distance, the more similar they are and vice-versa. In both supervised and unsupervised learning, these distance metrics are used, typically to measure the similarity between data points.

There are several measures of distance that can be used, and it is important to be aware of them while considering the best solution for a given situation to avoid errors and interpretation issues.

### Why do we need Distance Metrics ?

The reason that we should care about this is because these distance metrics are used in many of our favourite algorithms like K-Nearest Neighbours Classification algorithm, K-Means Clustering algorithm, or Self-Organising Maps (SOM). Some Kernel Algorithms like Support Vector Machines use calculations that can be considered as ‘distance calculations’ too. 

Because of this, it is important to understand what the logic behind each distance metric to know when we should use one versus another, as this can have a big impact in the results of these previous algorithms or models. 

Depending on the kind of data we have, the algorithm that we are using, and the intuition behind it, we might want to use one distance metric over another one, so it is good to have at least a basic understanding on what each metric represents. 

Now that we know that Distance Metrics are, and why they are so relevant, lets take a look at the most widely used metrics. 

### Where do we use Distance metrics ?
In the KNN algorithm, a classification or regression prediction is made for new examples by calculating the distance between the new example (row) and all examples (rows) in the training dataset. The k examples in the training dataset with the smallest distance are then selected and a prediction is made by averaging the outcome (mode of the class label or mean of the real value for regression).

KNN belongs to a broader field of algorithms called case-based or instance-based learning, most of which use distance measures in a similar manner. Another popular instance-based algorithm that uses distance measures is the learning vector quantization, or LVQ, algorithm that may also be considered a type of neural network.

A short list of some of the more popular machine learning algorithms that use distance measures at their core is as follows:

1. K-Nearest Neighbors
2. Learning Vector Quantization (LVQ)
3. Self-Organizing Map (SOM)
4. K-Means Clustering

There are many kernel-based methods may also be considered distance-based algorithms. Perhaps the most widely known kernel method is the support vector machine algorithm, or SVM for short.

### Types of Distance Metrics

There are many types of distance metrics are available. But predominantly we use only 4 types of metrics.
1. Euclidean Distance
2. Manhattan Distance
3. Minkowski Distance
4. Hamming Distance

#### 1. Euclidean Distance

Euclidean Distance represents the** shortest distance **between two points.

Most machine learning algorithms including K-Means use this distance metric to measure the similarity between observations. Let’s say we have two points as shown below:


![distance_metric.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645270721169/fGhxh1Ldw.png)

So, the Euclidean Distance between these two points A and B will be:


![euclidean.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645270812685/SmP9qGoxk.png)

**Formula **

![Screenshot from 2022-02-19 15-14-58.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645270767905/hNNP0CZ3w.png)

We use this formula when we are dealing with 2 dimensions. We can generalize this for an n-dimensional space as:


![Screenshot from 2022-02-19 17-10-56.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645270872862/lWrUDt5dj.png)

Where,

- n = number of dimensions
- pi, qi = data points

We will first import the required libraries. I will be using the SciPy library that contains pre-written codes for most of the distance functions used in Python:

```python
# importing the library
from scipy.spatial import distance

# defining the points
point_1 = (1, 2, 3)
point_2 = (4, 5, 6)
point_1, point_2

# computing the euclidean distance
euclidean_distance = distance.euclidean(point_1, point_2)
print('Euclidean Distance b/w', point_1, 'and', point_2, 'is: ', euclidean_distance)

```

![Screenshot from 2022-02-19 17-12-56.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645270987340/yN2vlDBVL.png)

Euclidean (and squared Euclidean) distances are usually computed from raw data, and not from standardized data. One advantage of this method is that the distance between any two objects is not affected by the addition of new objects to the analysis, which may be outliers . However, the distances can be greatly affected by differences in scale among the dimensions from which the distances are computed. 

For example, if one of the dimensions denotes a measured length in centimeters, and
you then convert it to millimeters (by multiplying the values by 10), the resulting Euclidean can be greatly affected (i.e., biased by those dimensions which have a larger scale), and consequently, the results of cluster analyses may be very different. Generally, it is good practice to transform the dimensions so that they have similar scales

#### 2. Manhattan Distance

Manhattan Distance is the sum of absolute differences between points across all the dimensions.
The shortest distance between the two points is along the hypotenuse, which is the Euclidean distance. The City block distance is instead calculated as the distance in x plus the distance in y, which is similar to the way we move in a city (like Manhattan) where we have to move around the buildings instead of going straight through. 

We can represent Manhattan Distance as:


![manhattan.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645271323909/DelU7Vtcz.png)

Since the above representation is 2 dimensional, to calculate Manhattan Distance, we will take the sum of absolute distances in both the x and y directions. So, the Manhattan distance in a 2-dimensional space is given as:


![Screenshot from 2022-02-19 15-25-51.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645271360435/dCJRlNKxN.png)

And the generalized formula for an n-dimensional space is given as:


![Screenshot from 2022-02-19 17-19-50.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645271409560/3S4uKD7yo.png)

Where,

- n = number of dimensions
- pi, qi = data points
Now, we will calculate the Manhattan Distance between the two points:

```python

# importing the library
from scipy.spatial import distance

# defining the points
point_1 = (1, 2, 3)
point_2 = (4, 5, 6)

manhattan_distance = distance.cityblock(point_1, point_2)
print('Manhattan Distance b/w', point_1, 'and', point_2, 'is: ', manhattan_distance)
```


![Screenshot from 2022-02-19 17-21-09.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645271481387/-tXDs8VeQ.png)

> Note: Manhattan Distance is also known as city block distance. SciPy has a function called cityblock that returns the Manhattan Distance between two points.

#### 3. Minkowski Distance

Minkowski Distance is the generalized form of Euclidean and Manhattan Distance.

The formula for Minkowski Distance is given as:

![Screenshot from 2022-02-19 17-26-19.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645271789515/Uz81usabK.png)

Here, p represents the order of the norm. 



![Screenshot from 2022-02-19 17-32-25.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645272190343/y1YVeIZxx.png)


Let’s calculate the Minkowski Distance of the order 3:

```python

# importing the library
from scipy.spatial import distance

# defining the points
point_1 = (1, 2, 3)
point_2 = (4, 5, 6)

# computing the minkowski distance
minkowski_distance = distance.minkowski(point_1, point_2, p=3)
print('Minkowski Distance b/w', point_1, 'and', point_2, 'is: ', minkowski_distance)
```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645271890189/rWrb9OrLI.png)

The p parameter of the Minkowski Distance metric of SciPy represents the order of the norm. When the order(p) is 1, it will represent Manhattan Distance and when the order in the above formula is 2, it will represent Euclidean Distance.

> Note: Try substituing the value of p = 1 and 2 in the formula and see whether you can derive the equations of Euclidean and Manhattan.

Some common values of ‘p’ are:-
p = 1, Manhattan Distance
p = 2, Euclidean Distance
p = infinity, Chebychev Distance

So far, we have covered the distance metrics that are used when we are dealing with continuous or numerical variables. But what if we have categorical variables? How can we decide the similarity between categorical variables? This is where we can make use of another distance metric called Hamming Distance.

#### 4. Hamming Distance

Hamming Distance measures the similarity between two strings of the same length. The Hamming Distance between two strings of the same length is the number of positions at which the corresponding characters are different.

Let’s understand the concept using an example. Let’s say we have two strings:

“euclidean” and “manhattan”

Since the length of these strings is equal, we can calculate the Hamming Distance. We will go character by character and match the strings. The first character of both the strings (e and m respectively) is different. Similarly, the second character of both the strings (u and a) is different. and so on.

Look carefully – seven characters are different whereas two characters (the last two characters) are similar:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645272017735/FK17nJnpy.png)

Hence, the Hamming Distance here will be 7. Note that larger the Hamming Distance between two strings, more dissimilar will be those strings (and vice versa).

Let’s see how we can compute the Hamming Distance of two strings in Python. First, we’ll define two strings that we will be using:

> Note: Length of the strings should be same. 

```python
# defining two strings
string_1 = 'euclidean'
string_2 = 'manhattan'

# computing the hamming distance
hamming_distance = distance.hamming(list(string_1), list(string_2))*len(string_1)
print('Hamming Distance b/w', string_1, 'and', string_2, 'is: ', hamming_distance)
```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645272096928/WRqKLupIW.png)

### Notebook

Colab Notebook Link : https://colab.research.google.com/drive/1FTpcP8friChkdBPqJzPfcGaIvsgxCaf2?usp=sharing

Implementation of the distance metric's discussed in this article. 

### Conclusion

Manhattan distance is usually preferred over the more common Euclidean distance when there is high dimensionality in the data. Hamming distance is used to measure the distance between categorical variables

### Interview Questions
1. When to use Euclidean Distance ?
2. What is called as  City Block Distance ?
3. In Minkowski, when the degree is one, its similar to which algorithm ?
