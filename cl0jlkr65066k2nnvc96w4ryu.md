## kNN - k Nearest Neighbour Algorithm

### Introduction
Consider a scenario, where we have an image of a creature that looks similar to a cat and dog, but we want to know whether it is a cat or dog. So for this identification, we can apply some similarity measures to classify. Based on the most similar features it will put it in either cat or dog category. This process Is known as kNN. In this article, we will see, 
1. Working of kNN
2. Implementation of kNN from scratch
3. Distance metrics to be used in kNN
4. Usage of kNN in regression
5. How to choose the k (no. of neighbors) values?
with a real-time dataset.


### What is kNN?

K-Nearest Neighbour is one of the simplest Machine Learning algorithms based on the Supervised Learning technique. It assumes the similarity between the new case/data and available cases and puts the new case into the category that is most similar to the available categories. It stores all the available data and classifies a new data point based on the similarity. This means when new data appears then it can be easily classified into a good suite category by using the kNN algorithm.

k Nearest Neighbour can be used for both classification and regression. But mostly it will be used for classification problems. 

### Why do we need a kNN Algorithm?

Suppose there are two categories, i.e., Category A and Category B, and we have a new data point x1, so this data point will lie in which of these categories. To solve this type of problem, we need a kNN algorithm. With the help of kNN, we can easily identify the category or class of a particular dataset. Consider the below diagram:

1.Two different categories of data points, 


![Machine Learning - Knn Algorithm - Data points - learnml.xyz](https://cdn.hashnode.com/res/hashnode/image/upload/v1646803442087/JHhCzMhMq.png)


2.Now, a new data point is coming into place. Now the question is; **To which category does this data point belong to?**


![Machine Learning - kNN Algorithm - New category in Data points - learnml.xyz](https://cdn.hashnode.com/res/hashnode/image/upload/v1646803585895/MMYXnAR-Y.png)

3.This problem could be solved by checking the nearest neighbors and finding the similarities between them. In other words by applying the kNN algorithm. 


![Screenshot from 2022-03-09 10-52-41.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1646803706412/bULeqEVIZ.png)

### Assumptions of the Data

The kNN algorithm assumes that similar things exist nearby. In other words, similar things are near to each other. **"Birds of a feather flock together."** 
 kNN captures the idea of similarity (sometimes called distance, proximity, or closeness) with some mathematics we might have learned in our childhood— calculating the distance between points on a graph. 

As we discussed in the previous article on [Distance Metrics](https://blog.learnml.xyz/distance-metrics-in-machine-learning), we will be using all of them in algorithms like kNN.

> Do you think the kNN algorithm needs testing data? Please comment on your view. 

### What is k in the kNN algorithm?

**k** in kNN is the number of nearest neighbors considered for assigning a label to the current point. **k** is an extremely important parameter and choosing the value of **k** is the most critical problem when working with the kNN algorithm. The process of choosing the right value of **k** is referred to as parameter tuning and is of great significance in achieving better accuracy. If the value of **k** is too small then there is a probability of overfitting the model and if it is too large then the algorithm becomes computationally expensive. Most data scientists usually choose an odd number value for **k** when the number of classes is 2.  Another formula that works well for choosing **k** is, k - sqrt(n) where n is the total number of data points.

Selecting the value of **k** depends on individual cases and sometimes the best method of choosing **k** is to run through different values of **k** and verify the outcomes. Using cross-validation, the kNN algorithm can be tested for different values of **k** and the value of **k** that results in good accuracy can be considered as an optimal value for **k**.

### How kNN algorithm works?

The kNN working can be explained based on the below algorithm:

**Step-1:** Select the number k of the neighbors. <br>
**Step-2:** Calculate the Euclidean distance of k number of neighbors. <br>
**Step-3: **Take the k nearest neighbors as per the calculated Euclidean distance. <br>
**Step-4:** Among these k neighbors, count the number of the data points in each category. <br>
**Step-5:** Assign the new data points to that category for which the number of the neighbor is maximum. <br>
**Step-6:** Our model is ready. <br>

### Explanation

Let us consider the iris dataset, 

> Dataset : https://github.com/learnml-xyz/datasets/tree/main/iris


![Iris dataset - knn algorithm - machine learning - learnml.xyz](https://cdn.hashnode.com/res/hashnode/image/upload/v1646808228485/7s1jOv6vl.png)


**Step 1: ** After visualizing, we can see like this, 

<iframe src="https://learnml-xyz.github.io/kNN-Algorithm/src/initial_iris_3d_plot.html" height="600" width="800" title="Iframe Example"></iframe>

**Step 2:** Setup distance parameter

In our previous article, we have discussed [Distance Metrics](https://blog.learnml.xyz/distance-metrics-in-machine-learning). In this article, we are going to use Euclidean distance as a distance measurement. 

![Euclidean formula for n-dimensional dataset](https://cdn.hashnode.com/res/hashnode/image/upload/v1645270872862/lWrUDt5dj.png?auto=compress,format&format=webp)


```python
def calculate_euclidean_distance(point_1, point_2, n_dim=2):
  val = 0
  for dim in range(n_dim):
    val += (point_1[dim] - point_2[dim])**2
  return math.sqrt(val)
```

**Step 3:** Decide on the k Value (No. of neighbors to be considered)

For example, if we consider k = 5, 


![Knn algorithm - Machine Learning - Neighbours with 5](https://cdn.hashnode.com/res/hashnode/image/upload/v1646818516238/bh1Nuawdz.png)

Based on the distance metrics, we can see the 5 data points have been highlighted. 

> Note: We should use only use odd numbers of **k** (No. of neighbors). 

The problem with the even number of neighbors, there is a possibility that value gets evenly separated between categories like below. 

![KNN Algorithm - machine learning - neighbors with 4 - learnml](https://cdn.hashnode.com/res/hashnode/image/upload/v1646819051740/iPmf2S77J.png)

A small value of k means that noise will have a higher influence on the result. A large value makes it computationally expensive and kinda defeats the basic philosophy behind kNN (that points that are near might have similar densities or classes ). A simple approach to select k is to set **k = n^(1/2).**

**Step 4:** 
Considering a new Datapoint (5.0, 3.0, 1.5). We need to find the distance between this new data point with all other data points and find top K items from that we need to select the group it belongs to. 

```python
distances = []
new_data_point = [5.0, 3.0, 1.5]
for point in dataset:
  _distance = calculate_euclidean_distance(point_1=point, point_2=new_data_point, n_dim=3)
  distances.append(_distance)

print(distances)
```

![euclidean distance - learnml.xyz - machine learning](https://cdn.hashnode.com/res/hashnode/image/upload/v1646829249692/TmJMQdgz6.png)

**Step 5:** 
After calculating the distances, we need to sort the dataset by shortest distance, with the limit of k ( Nearest Neighbour ).

```python
k = 5
for index in indices[:k]:
  print(dataset[index])
```


![Output of kNN ](https://cdn.hashnode.com/res/hashnode/image/upload/v1646830619534/-qXbcDkrh.png)

The above-mentioned steps are practiced in classification. For regression, we will repeat the same steps at the last we will take the average of the top k nodes. 

### Colab Notebook

Notebook Link: https://colab.research.google.com/drive/1z78gX1U1ZXUwXr4AWgVxjR6CVVztASxw?usp=sharing

### Advantages of kNN algorithm
1. No Training Period: kNN is called Lazy Learner (Instance-based learning). It does not learn anything in the training period. It does not derive any discriminative function from the training data. In other words, there is no training period for it. It stores the training dataset and learns from it only at the time of making real-time predictions. This makes the kNN algorithm much faster than other algorithms that require training e.g. SVM, Linear Regression, etc.

2. Since the kNN algorithm requires no training before making predictions, new data can be added seamlessly which will not impact the accuracy of the algorithm.

3. kNN is very easy to implement. There are only two parameters required to implement kNN i.e. the value of k and the distance function (e.g. Euclidean or Manhattan etc.)

4. It constantly evolves: Given its instance-based learning; kNN is a memory-based approach. The classifier immediately adapts as we collect new training data. It allows the algorithm to respond quickly to changes in the input during real-time use.

5. Very easy to implement for the multi-class problem: Most of the classifier algorithms are easy to implement for binary problems and need the effort to implement for multi-class whereas kNN adjusts to multi-class without any extra efforts.

6. Can be used both for Classification and Regression: One of the biggest advantages of kNN is that kNN can be used both for classification and regression problems.

7. One Hyper Parameter: kNN might take some time while selecting the first hyperparameter but after that rest of the parameters are aligned to it.


### Disadvantages of kNN algorithm

1. Does not work well with large datasets: In large datasets, the cost of calculating the distance between the new point and each existing point is huge which degrades the performance of the algorithm.

2. Does not work well with high dimensions: The kNN algorithm doesn't work well with high dimensional data because, with a large number of dimensions, it becomes difficult for the algorithm to calculate the distance in each dimension.

3. Need feature scaling: We need to do feature scaling (standardization and normalization) before applying the kNN algorithm to any dataset. If we don't do so, kNN may generate wrong predictions.

4. Sensitive to noisy data, missing values, and outliers: kNN is sensitive to noise in the dataset. We need to manually impute missing values and remove outliers.

5. Curse of Dimensionality: kNN works well with a small number of input variables but as the numbers of variables grow kNN algorithm struggles to predict the output of new data points.

6. kNN needs homogeneous features: If you decide to build kNN using a common distance, like Euclidean or Manhattan distances, it is completely necessary that features have the same scale, since absolute differences in features weigh the same, i.e., a given distance in feature 1 must mean the same for feature 2.

7. The Optimal number of neighbors: One of the biggest issues with kNN is to choose the optimal number of neighbors to be considered while classifying the new data entry.

8. Imbalanced data causes problems: kNN doesn’t perform well on imbalanced data. If we consider two classes, A and B, and the majority of the training data is labeled as A, then the model will ultimately give a lot of preference to A. This might result in getting the less common class B wrongly classified.

9. Missing Value treatment: kNN inherently has no capability of dealing with the missing value problem.







