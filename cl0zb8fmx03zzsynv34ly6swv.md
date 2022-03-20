## The Cross Validation - [Theory]

### Introduction

Cross-validation is a technique for validating the model efficiency by training it on the subset of input data and testing on a previously unseen subset of the input data. We can also say that it is a technique to check how a statistical model generalizes to an independent dataset.

In machine learning, there is always the need to test the stability of the model. It means based only on the training dataset; we can't fit our model on the training dataset. For this purpose, we reserve a particular sample of the dataset, which was not part of the training dataset. After that, we test our model on that sample before deployment, and this complete process comes under cross-validation. This is something different from the general train-test split.

### What is Cross Validation ?

Cross-validation is a technique in which we train our model using the subset of the data-set and then evaluate using the complementary subset of the data-set.

The three steps involved in cross-validation are as follows :
1. Reserve some portion of the sample dataset.
2. Using the rest data-set train the model.
3. Test the model using the reserve portion of the dataset.

### Methods of Cross Validation

There are some common methods that are used for cross-validation. These methods are given below:

#### Validation

This process of deciding whether the numerical results quantifying hypothesized relationships between variables, are acceptable as descriptions of the data, is known as validation. Generally, an error estimation for the model is made after training, better known as evaluation of residuals. In this process, a numerical estimate of the difference in predicted and original responses is done, also called the training error. However, this only gives us an idea about how well our model does on data used to train it. Now its possible that the model is underfitting or overfitting the data. So, the problem with this evaluation technique is that it does not give an indication of how well the learner will generalize to an independent/ unseen data set. Getting this idea about our model is known as Cross-Validation.

#### Holdout Method

Now a basic remedy for this involves removing a part of the training data and using it to get predictions from the model trained on the rest of the data. The error estimation then tells how our model is doing on unseen data or the validation set. This is a simple kind of cross-validation technique, also known as the holdout method. Although this method doesn’t take any overhead to compute and is better than traditional validation, it still suffers from issues of high variance. This is because it is not certain which data points will end up in the validation set and the result might be entirely different for different sets.

#### K-Fold Cross-Validation

As there is never enough data to train your model, removing a part of it for validation poses a problem of underfitting. By reducing the training data, we risk losing important patterns/ trends in the data set, which in turn increases error induced by bias. So, what we require is a method that provides ample data for training the model and also leaves ample data for validation. K Fold cross-validation does exactly that.

In K Fold cross-validation, the data is divided into k subsets. Now the holdout method is repeated k times, such that each time, one of the k subsets is used as the test set/ validation set and the other k-1 subsets are put together to form a training set. The error estimation is averaged over all k trials to get the total effectiveness of our model. As can be seen, every data point gets to be in a validation set exactly once and gets to be in a training set k-1 times. This significantly reduces bias as we are using most of the data for fitting, and also significantly reduces variance as most of the data is also being used in the validation set. Interchanging the training and test sets also adds to the effectiveness of this method. As a general rule and empirical evidence, K = 5 or 10 is generally preferred, but nothing’s fixed and it can take any value.

#### Stratified K-Fold Cross-Validation

In some cases, there may be a large imbalance in the response variables. For example, in the dataset concerning the price of houses, there might be a large number of houses having a high price. Or in the case of classification, there might be several times more negative samples than positive samples. For such problems, a slight variation in the K Fold cross-validation technique is made, such that each fold contains approximately the same percentage of samples of each target class as the complete set, or in case of prediction problems, the mean response value is approximately equal in all the folds. This variation is also known as Stratified K Fold.

The above-explained validation techniques are also referred to as Non-exhaustive cross-validation methods. These do not compute all ways of splitting the original sample, i.e. you just have to decide how many subsets need to be made. Also, these are approximations of the method explained below, also called Exhaustive Methods, that computes all possible ways the data can be split into training and test sets.

#### Leave-P-Out Cross-Validation

This approach leaves p data points out of training data, i.e. if there are n data points in the original sample then, n-p samples are used to train the model, and p points are used as the validation set. This is repeated for all combinations in which the original sample can be separated this way, and then the error is averaged for all trials, to give overall effectiveness.

This method is exhaustive in the sense that it needs to train and validate the model for all possible combinations, and for moderately large p, it can become computationally infeasible.

A particular case of this method is when p = 1. This is known as Leave one out cross-validation. This method is generally preferred over the previous one because it does not suffer from intensive computation, as a number of possible combinations are equal to the number of data points in the original sample or n.

Cross-Validation is a very useful technique for assessing the effectiveness of your model, particularly in cases where you need to mitigate overfitting. It is also of use in determining the hyperparameters of your model, in the sense that which parameters will result in the lowest test error. There are all the basics you need to get started with cross-validation. You can get started with all kinds of validation techniques using Scikit-Learn, which gets you up and running with just a few lines of code in python.


### Comparison of Cross-validation to train/test split in Machine Learning

- **Train/test split**: The input data is divided into two parts, which are training set and test set on a ratio of 70****:30, 80:20, etc. It provides a high variance, which is one of the biggest disadvantages.
 1. **Training Data**: The training data is used to train the model, and the dependent variable is known.
 2. **Test Data:** The test data is used to make the predictions from the model that is already trained on the training data. This has the same features as training data but is not part of that.
    
- **Cross-Validation dataset:** It is used to overcome the disadvantage of train/test split by splitting the dataset into groups of train/test splits, and averaging the result. It can be used if we want to optimize our model that has been trained on the training dataset for the best performance. It is more efficient as compared to train/test split as every observation is used for the training and testing of both.


### Limitations of Cross-Validation

There are some limitations of the cross-validation technique, which are given below:

1. For the ideal conditions, it provides the optimum output. But for inconsistent data, may produce a drastic result. So, it is one of the big disadvantages of cross-validation, as there is no certainty of the type of data in machine learning.
2. In predictive modeling, the data evolves over a period, due to which, it may face the differences between the training set and validation sets. Such as if we create a model for the prediction of stock market values, and the data is trained on the previous 5 years' stock values, but the realistic future values for the next 5 years may be drastically different, so it is difficult to expect the correct output for such situations.



### Applications of Cross-Validation

1. This technique can be used to compare the performance of different predictive modeling methods.
2. It has great scope in the medical research field.
3. It can also be used for meta-analysis, as it is already being used by data scientists in the field of medical statistics.


### Conclusion 

So far we have seen the different types of cross-validations. In upcoming articles, we will see individual methods in detail. 





