## Supervised Machine Learning

### 1. Introduction

Supervised learning or supervised machine learning is a process where you already have both the i**nput variables (x)** and **an output variable (Y)** and you use an algorithm to learn the mapping function from the input to the output.

> Y = f(X)

The goal is to approximate the mapping function so well that when you have new input data (x) that you can predict the output variables (Y) for that data.

It is called supervised learning because the process of an algorithm learning from the training dataset can be thought of as a teacher supervising the learning process. We know the correct answers, the algorithm iteratively makes predictions on the training data and is corrected by the teacher. Learning stops when the algorithm achieves an acceptable level of performance.

<iframe width="800" height="400" src="https://www.youtube.com/embed/bQI5uDxrFfA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### 2. Explanation
In simpler terms, consider you are having a labelled data. A dataset with the input values and the output values like below . 


![Screenshot from 2022-02-13 12-54-45.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644737185837/5EXJeWAZf.png)

We are feeding this information into a black box ( ML Algorithm - We will figure it out soon ) and the black box understands that this image 🥭 is **mango**.

So from now onwards whenever we ask the black box, what is this image it will tell its mango. This is supervised learning. You are supervising a model by providing both the input and the output for training (learning). 

Supervised learning uses a training set to teach models to yield the desired output. This training dataset includes inputs and correct outputs, which allow the model to learn over time. The algorithm measures its accuracy through the loss function, adjusting until the error has been sufficiently minimized.

### 3. Types of Supervised Algorithm
Supervised learning requires that the algorithm’s possible outputs are already known and that the data used to train the algorithm is already labeled with correct answers. If the output is a **real number,** we call the task **regression**. If the output is from the limited number of values, where these values are unordered, then it’s **classification**.

Its has two types,
1. Classification (Defined Labels)
2. Regression (Not Defined Labels)


![1__P2Y7wi_B7o8MERuabnE9Q@2x.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644738091931/7iiJcbAKt.png)

### 4. Classification


![Screenshot from 2022-02-13 13-30-11.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644739249403/9LiNKkMPAI.png)

It is a Supervised Learning task where output is having defined labels(**discrete value**). For example in above figure, Output – Purchased has defined labels i.e. 0 or 1; 1 means the customer will purchase and 0 means that customer won’t purchase. 

The goal here is to predict discrete values belonging to a particular class and evaluate them on the basis of accuracy. It can be either binary or multi-class classification. In binary classification, the model predicts either 0 or 1; yes or no but in the case of multi-class classification, the model predicts more than one class. 

**Example**:  Classifying groceries and vegetables bought from the market in to two classes. 

![classification.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1644738426596/42Uo7H3WY.jpeg)

Below is a Naive Bayes Classifier algorithms working. (At this point, dont think about the circles, just see how its been classifying. )

![Naive_Bayes_Classifier.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1644738753037/nqckWlAlK.gif)

#### Types of Classification algorithms : 
1. Logistic Regression
2. Naive Bayes
3. Decision Tree
4. K Nearest Neighbour
5. Support Vector Machine
6. Random Forest
7. Stochastic Gradient Descent
8. Kernel Approximation Algorithm

We will see everything stated above in detail. 

### 5. Regression:

![Screenshot from 2022-02-13 13-30-22.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644739304038/BLHZu2uly.png)

It is a Supervised Learning task where output is having continuous value.  

Example in above figure, Output – Wind Speed is not having any discrete value but is continuous in the particular range. The goal here is to predict a value as much closer to the actual output value as our model can and then evaluation is done by calculating the error value. The smaller the error the greater the accuracy of our regression model.

In simpler terms, we plot the data points in a graph, and then we try to draw a straight or curved line which covers most of the data points.


![1_eeIvlwkMNG1wSmj3FR6M2g.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1644739532679/5ALhoOqc4.gif)


#### Types of Regression algorithm :
1. Linear Regression - [Click Here](https://learnml.hashnode.dev/linear-regression-with-gradient-descent-scratch)
2. Polynomial Regression
3. Lasso Regression
4. Ridge Regression
5. Decision Tree Regression
6. Support Vector Machine
7. KNN Model
8. Elastic Net Regression

### 6. Challenges in supervised learning: 
A wide range of supervised learning algorithms are available, each with its strengths and weaknesses. There is no single learning algorithm that works best on all supervised learning problems.

1. Irrelevant input feature present training data could give inaccurate results
2. Data preparation and pre-processing is always a challenge.
3. Accuracy suffers when impossible, unlikely, and incomplete values have been inputted as training data.
4. If the concerned expert is not available, then the other approach is “brute-force.” It means you need to think that the right features (input variables) to train the machine on. It could be inaccurate.


### 7. Advantages of Supervised Learning
Here are the advantages of Supervised Machine learning:

1. Supervised learning in Machine Learning allows you to collect data or produce a data output from the previous experience
2. Helps you to optimize performance criteria using experience
3. Supervised machine learning helps you to solve various types of real-world computation problems.

### 8. Disadvantages of Supervised Learning
Below are the disadvantages of Supervised Machine learning:

1. Decision boundary might be overtrained if your training set which doesn’t have examples that you want to have in a class
2. You need to select lots of good examples from each class while you are training the classifier.
3. Classifying big data can be a real challenge.
4. Training for supervised learning needs a lot of computation time.

### 9. Interview Questions
1. What is Supervised Learning ?
2. Why Logistic Regression is mentioned under Classification ?
3. How trustworthy is the regression using Decision tree ?
4. If you are having the labelled data. What is it called ?
5. Which category gives you the discrete output ?
6. How Do You Design an Email Spam Filter?
7. If the output is categorical, what kind of algorithms do you use ?

### 10. References: 
1. Wikipedia - https://en.wikipedia.org/wiki/Supervised_learning

