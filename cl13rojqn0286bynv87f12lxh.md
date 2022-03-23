## kNN Model Complexity

### Introduction

[K-Nearest Neighbour](https://blog.learnml.xyz/knn-k-nearest-neighbour-algorithm) is one of the simplest Machine Learning algorithms based on the Supervised Learning technique. It assumes the similarity between the new case/data and available cases and puts the new case into the category that is most similar to the available categories. It stores all the available data and classifies a new data point based on the similarity. This means when new data appears then it can be easily classified into a good suite category by using the kNN algorithm. In this article, we will see how to select the K value in the kNN algorithm. 

### Model Complexity

kNN is a machine learning algorithm that is used for both classifications ( using kNearestClassifier ) and Regression ( using kNearestRegressor ) problems. In the kNN algorithm, k is the **hyperparameter**. Choosing the right value of k matters. A machine learning model is said to have **high model complexity** if the built model is having **low bias and high variance. ** We know that, 

1. High Bias and Low Variance => Underfitting model. 
2. Low Bias and High Variance => Overfitting model [ indicated **highly complex model** ].
3. Low Bias and Low Variance => Best fitting model.
4. High training accuracy and Low test accuracy ( out of sample accuracy ) => High Variance.
5. High Variance => Overfitting model => More model complexity.
6. Low training accuracy and Low test accuracy => High Bias => underfitting model. 

### Explanation

Let's generate some regression dataset and try finding the k value for kNN Regressor. 

#### Generating sample dataset

In this article, we are using sklearn's make_regression functionality to generate the dataset. Once we generate the dataset, we can also try to plot the data in 2D view. 

```python
import matplotlib.pyplot as plt
from sklearn.datasets import make_regression
from sklearn.neighbors import KNeighborsRegressor
from sklearn.model_selection import train_test_split
import numpy as np

plt.figure()
plt.title("Data Generation")
x, y = make_regression(
    n_samples = 100, n_features = 1, 
    n_informative = 1, noise = 15,
    random_state = 3
)

plt.scatter(x, y, color='green', marker='o', s=30)
```

![dataset plotting - machine learning - learnml.xyz](https://cdn.hashnode.com/res/hashnode/image/upload/v1648050809086/_McZahLXv.png)

#### Train the model

Now let's train the model using the kNN regressor algorithm from sklearn library. 

```python
knn = KNeighborsRegressor(n_neighbors = 7)
x_train, x_test, y_train, y_test = train_test_split(
    x, y, test_size = 0.2, random_state = 0
)
knn.fit(x_train, y_train)
predict = knn.predict(x_test)

print("Test Accuracy : ", knn.score(x_test, y_test))
print("Training Accuracy : ", knn.score(x_train, y_train))

```


![train the model - machine learning - learnml.xyz](https://cdn.hashnode.com/res/hashnode/image/upload/v1648050948229/gS-jKW65l.png)

#### Visualizing the output

```python
x_new = np.linspace(-3, 2, 100).reshape(100, 1)
predict_new = knn.predict(x_new) 
plt.plot(
    x_new, predict_new, color='blue', label='K = 7'
)
plt.scatter(x_train, y_train, color='red')
plt.scatter(x_test, predict, marker='*', s=90)
plt.legend()
```


![Visualizing output - machine learning ](https://cdn.hashnode.com/res/hashnode/image/upload/v1648051100713/LZO8rQhXX.png)

#### Now let's vary the value of K (Hyperparameter) from low to high and observe the model complexity K = 1


![kNN with k = 1 - machine learning - learnml.xyz](https://cdn.hashnode.com/res/hashnode/image/upload/v1648051550282/ndKErg8Ax.png)

#### K = 10


![kNN with k = 10 - machine learning - learnml.xyz](https://cdn.hashnode.com/res/hashnode/image/upload/v1648051597573/QQkO02Rfc.png)

#### K = 20


![kNN with k = 20 - machine learning - learnml.xyz](https://cdn.hashnode.com/res/hashnode/image/upload/v1648051638031/VzyDbQc_y.png)

#### K = 50


![kNN with k = 20 - machine learning - learnml.xyz](https://cdn.hashnode.com/res/hashnode/image/upload/v1648051677280/6MHzsHfyV.png)

#### K = 70


![kNN with k = 70 - machine learning - learnml.xyz](https://cdn.hashnode.com/res/hashnode/image/upload/v1648051704925/hKBhIRWFF.png)

From the above tryouts of different k values we can see that as the value of k increases accuracy drops. 

### Visualizing with different values of K 

```python
p = list(range(1, 50))
lst_test = []
lst_train = []

for itr in p:
  knn = KNeighborsRegressor(n_neighbors = itr)
  knn.fit(x_train, y_train)
  z = knn.score(x_test, y_test)
  t = knn.score(x_train, y_train)
  lst_test.append(z)
  lst_train.append(t)

plt.plot(p, lst_test, color='red', label='Test Accuracy')
plt.plot(p, lst_train, color='b', label='Train Accuracy')
plt.xlabel('K Values')
plt.title('Finding optimal value for k')
plt.legend()
```

![Train accuracy and test accuracy for different values of K ](https://cdn.hashnode.com/res/hashnode/image/upload/v1648051804893/ZJCTwzgm3.png)

From the above graph, we can conclude that when K is small i.e. K=1, Training Accuracy is High but Test Accuracy is Low which means the model is over-fitting ( High Variance or **High Model Complexity**). When the value of K is large i.e. K=50, Training Accuracy is Low as well as Test Accuracy is Low which means the model is under-fitting ( High Bias or Low Model Complexity ).



### Conclusion

In this article, we have tried using a simple for-loop to find out the optimal K Value. So **Hyperparameter tuning **is necessary i.e. to select the best value of K in the kNN algorithm for which the model has Low Bias and Low Variance and results in a good model with high out-of-sample accuracy.

We can use **GridSearchCV** or **RandomSearchCv** to find the best value of hyperparameter K.