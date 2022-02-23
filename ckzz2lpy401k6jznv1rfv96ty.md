## The Dimentionality Reduction

### Prerequisite
1. Polynomial Regression - [study link](https://learnml.hashnode.dev/the-polynomial-regression)
2. Curse of Dimentionality - [study link](https://learnml.hashnode.dev/the-curse-of-dimensionality)

### Introduction

Have you ever worked on a dataset with more than a thousand features? How about over 50,000 features? I have, and let me tell you it’s a very challenging task, especially if you don’t know where to start! Having a high number of variables is both a boon and a curse. It’s great that we have loads of data for analysis, but it is challenging due to size.

It’s not feasible to analyze each and every variable at a microscopic level. It might take us days or months to perform any meaningful analysis and we’ll lose a ton of time and money for our business! Not to mention the amount of computational power this will take. We need a better way to deal with high dimensional data so that we can quickly extract patterns and insights from it. So how do we approach such a dataset?

Using dimensionality reduction techniques, of course. You can use this concept to reduce the number of features in your dataset without having to lose much information and keep (or improve) the model’s performance. It’s a really powerful way to deal with huge datasets, as you’ll see in this article.

In this article we will first understand what this concept is and why we should use it, before diving into the 12 different techniques (in upcoming articles)

### What is Dimensionality Reduction?

We are generating a tremendous amount of data daily. In fact, 90% of the data in the world has been generated in the last 3-4 years! The numbers are truly mind boggling. Below are just some of the examples of the kind of data being collected:

- Facebook collects data of what you like, share, post, places you visit, restaurants you like, etc.
- Your smartphone apps collect a lot of personal information about you
- Amazon collects data of what you buy, view, click, etc. on their site
- Casinos keep a track of every move each customer makes

As data generation and collection keeps increasing, visualizing it and drawing inferences becomes more and more challenging. One of the most common ways of doing visualization is through charts. '

Suppose we have 2 variables, Age and Height. We can use a scatter or line plot between Age and Height and visualize their relationship easily:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645590778074/h6oS6yVCu.png)

Now consider a case in which we have, say 100 variables (p=100). In this case, we can have 100(100-1)/2 = 5000 different plots. It does not make much sense to visualize each of them separately, right? In such cases where we have a large number of variables, it is better to select a subset of these variables (p<<100) which captures as much information as the original set of variables.

Let us understand this with a simple example. Consider the below image:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645590802837/7q_rs-Fft.png)

Here we have weights of similar objects in Kg (X1) and Pound (X2). If we use both of these variables, they will convey similar information. So, it would make sense to use only one variable. We can convert the data from 2D (X1 and X2) to 1D (Y1) as shown below:


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645590823143/6US635hn5.png)

Similarly, we can reduce p dimensions of the data into a subset of k dimensions (k<<n). This is called dimensionality reduction.

### Why is Dimensionality Reduction required?

In the previous articles on **The Curse of Dimensionality** , we saw the effect of how the RMSE and R<sup>2</sup> value were increasing and decreating respectively with the rise of dimensions in to the data. That is a big problem to sort it out. Dimensionality reduction will help us in reducing the dimensions of the features. 

Here are some of the benefits of applying dimensionality reduction to a dataset:

- Space required to store the data is reduced as the number of dimensions comes down
- Less dimensions lead to less computation/training time
- Some algorithms do not perform well when we have a large dimensions. So reducing these dimensions needs to happen for the algorithm to be useful
- It takes care of multicollinearity by removing redundant features. For example, you have two variables – ‘time spent on treadmill in minutes’ and ‘calories burnt’. These variables are highly correlated as the more time you spend running on a treadmill, the more calories you will burn. Hence, there is no point in storing both as just one of them does what you require
- It helps in visualizing data. As discussed earlier, it is very difficult to visualize data in higher dimensions so reducing our space to 2D or 3D may allow us to plot and observe patterns more clearly

### Common Dimensionality Reduction Techniques
Dimensionality reduction can be done in two different ways:

By only keeping the most relevant variables from the original dataset (this technique is called feature selection)
By finding a smaller set of new variables, each being a combination of the input variables, containing basically the same information as the input variables (this technique is called dimensionality reduction)

1. Missing Value Ratio
2. Low Variance Filter
3. High Correlation filter
4. Random Forest
5. Backward Feature Elimination
6. Forward Feature Selection
7. Factor Analysis
8. Principal Component Analysis (PCA)
9. Independent Component Analysis
10. Methods Based on Projections
11. t- Distributed Stochastic Neighbor Embedding (t-SNE)
12. UMAP
13. NCVIS

We will see each one of them in detail in upcoming articles. (stay tuned. Subscribe to the mail letter to get notification)

### Conclusion

Dealing with thousands and millions of features is a must-have skill for any data scientist. The amount of data we are generating each day is unprecedented and we need to find different ways to figure out how to use it. Dimensionality reduction is a very useful way to do this and has worked wonders for me, both in a professional setting as well as in machine learning hackathons.

