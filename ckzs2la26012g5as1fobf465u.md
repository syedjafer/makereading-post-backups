## Confusion Matrix in Machine Learning: Everything You Need to Know

### Introduction

In Machine Learning, the problem of classification involves predicting the categorical class label to which the query data point belongs. And the confusion matrix is a tabular representation of the classification model’s performance.


![confusion matrix - machine learning - meme](https://cdn.hashnode.com/res/hashnode/image/upload/v1645163380561/2LAbm26qs.png)

This tutorial will help you understand the confusion matrix and the various metrics that you can calculate from the confusion matrix.

We’ll start by explaining what classification is, the types of classification problems, and how to interpret the confusion matrix for a **binary classification** problem.

### What is Classification ?

![classification algorithm - machine learning - supervised learning - binary classification](https://cdn.hashnode.com/res/hashnode/image/upload/v1645156110657/1Ct9-QZvu.png)

It is a Supervised Learning task where output is having defined labels(discrete value). For example in above figure, Output – Purchased has defined labels i.e. 0 or 1; 1 means the customer will purchase and 0 means that customer won’t purchase.

The goal here is to predict discrete values belonging to a particular class and evaluate them on the basis of accuracy. It can be either binary or multi-class classification. In binary classification, the model predicts either 0 or 1; yes or no but in the case of multi-class classification, the model predicts more than one class.

Example: Classifying groceries and vegetables bought from the market in to two classes.


![categorical variables - machine learning classification - binary classification](https://cdn.hashnode.com/res/hashnode/image/upload/v1645158625636/ilxlI31Yi.png)

Below is a Naive Bayes Classifier algorithms working. (At this point, dont think about the circles, just see how its been classifying. )


![gif of naive bayes classification - machine learning - learnml.xyz](https://cdn.hashnode.com/res/hashnode/image/upload/v1645160083621/ATEmZhHt4.gif)

In essence, classification algorithms aim at answering the question:

> “Given labeled training data points, what’s the class label of a previously unseen test, or query data point?”

A classification problem could be as simple as classifying a given image as that of a cat or a dog.

<iframe src="https://giphy.com/embed/l1aDnRwIz7pmLS9FVW" width="480" height="405" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/cat-dog-jinzhan-l1aDnRwIz7pmLS9FVW">via GIPHY</a></p>

Or it could be as complex as examining brain scans to detect the presence or absence of tumors.

<iframe src="https://giphy.com/embed/l44QzsOLXxcrigdgI" width="480" height="360" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/stupid-smart-l44QzsOLXxcrigdgI">via GIPHY</a></p>


### Types of Classification
#### Binary Classification

In binary classification, the class labels 1 and 0 are used.

Suppose you’re given a large dataset of student loans containing features such as the name of the university, tuition and employment details.

You’d like to predict whether or not a new student with a specific tuition fee and employment status will default on the student loan. Notice how you’re trying to answer the question “Will the student default on the loan?”—and the answer is either a ‘Yes’ or a  ‘No’.

You might as well think of other examples, say, identifying spam emails - the answers in this case are ‘Spam’ or ‘Not Spam’.

In these examples,

- the answers ‘Yes’, ‘Spam’ indicate relevant classes, and in practice are encoded as class 1, and
- the answers ‘No’ and ‘Not Spam’ are encoded as class 0.

Using disease diagnosis as another example, if the problem is to detect the presence of a disease: label 1 indicates that the patient has the disease; and label 0 indicates the absence of the disease.

This classification problem where the data points belong to one of the two classes is called binary classification. And we’ll build on binary classification in this tutorial.

#### Multiclass Classification

You can also have classification problems where you have more than two classes, called multiclass classification.

For instance, classifying an email as ‘Spam’ or ‘Not Spam’ is a binary classification problem, whereas, categorizing emails as ‘School’, ‘Work’ or ‘Personal’ is a multiclass classification problem.

Now that you’ve gained an understanding of the types of classification, let’s proceed to understand the confusion matrix. 

We will see the explanation of multiclass confusion matrix towards the end. First we see the working of binary class confusion matrix . 

### General Structure of the Confusion Matrix

The general structure of the confusion matrix for binary classification is shown below:


![general structure of confusion matrix - classification metric - supervised learning - machine learning](https://cdn.hashnode.com/res/hashnode/image/upload/v1645158931104/oq16-0oyO.png)

Let’s now define a few terms:

#### **1. True Positive (TP) ** 
When the actual label is 1, and the classifier also predicted the label to be 1

#### **2. False Positive (FP)**
When the actual label is 0, but the classifier falsely predicted it to be 1

#### **3. True Negative (TN)**
When the actual label is 0, and classifier also predicted as 0

#### **4. False Negative (FN)**
When the actual label is 1, but the classifier predicted the label to be 0

Let’s now head over to the next section to understand the evaluation metrics for classification.

You’ll learn them by asking questions and following up with answers—and the answers explain what the metric signifies.

### How to Calculate Evaluation Metrics from Confusion Matrix

#### Accuracy

> "How often is the model correct?”

**The number of times the classifier correctly predicted class 1, plus the number of times it correctly predicted class 0.**

Now, look up from the matrix above, it’s the count of **True Positive (TP) + True Negative (TN)**. And the total number of predictions is the sum of counts in all 4 quadrants.

This this leads to the formula for accuracy as given below:

> Accuracy = TP + TN/(Total Predictions)

where, **Total Predictions = TP + TN + FP + FN**

At the outset accuracy may seem like a good metric for evaluation. However, it is not a reliable metric when you have an imbalance in the class labels.

**Explanation **
Suppose you’re designing a model to predict if a person has a particular medical condition that is rare—say affects only 0.5% of the population.

So in a population of 1000 people, about 5 people will likely have the disease. You clearly have a class imbalance in this case!

The majority class is class 0 indicating that the person doesn’t have that particular medical condition.

In this case, a naive model that predicts the majority class all the time will be 99.5% accurate. However, such a model clearly isn't very helpful.

Can you see why this is the case? The confusion matrix for this example will look like this:


![confusion matrix of the accuracy - supervised machine learning algorithms - machine learning - learnml.xyz](https://cdn.hashnode.com/res/hashnode/image/upload/v1645159398257/XMyqMVQpT.png)

1. You’re making 1000 predictions. And for all of them, the predicted label is class 0.
2. And 995 of them are actually correct (True Negatives!)
3. And 5 of them are wrong.
4. The accuracy score still works out to 995/1000 = 0.995

🎯 To sum up, Imbalanced class labels distort accuracy scores. And the model is projected to perform better than what is truly warranted.

Examples include problems like:

1. Credit card transactions that are potentially fraudulent
2. A medical condition that affects a very small fraction of the total population

**If the percentage of the minority class is p%, a model that predicts the majority class all the time will have an accuracy score of 1-p.**

As you might have guessed by now, the error rate is 1-accuracy score.

Instead of saying “My model is correct 98% of the time”, if you’d like to say “My model is wrong 2% of the time”, then you’re talking error rates!

#### Recall

> “When it actually is a positive case, how often is the model correct? Or, What fraction of the positive labels does the model predict correctly?”

In essence, it’s the number of relevant cases that have been found by the model.

Now, go back to the confusion matrix and look up the Actual row to identify which predictions correspond to an actually positive label—that is, class 1.


![recall classification machine learning algorithm - binary classification -  machine learning](https://cdn.hashnode.com/res/hashnode/image/upload/v1645159543906/eFyIKfWM1.png)

Alright. So it’s the **TP + FN** count.

And the number of times the model got it right is equal to the TP count. So here’s our formula for recall:

> Recall = TP/ (TP + FN)

Our previous model for disease detection did not identify any positive cases—so the TP count = 0. And that leaves us with a recall score of 0.

So the model has a recall score of 0 even though its accuracy score is 0.995.

#### Precision

> “When the prediction is positive, how often is it correct?”

Once again, go back to the confusion matrix and look up under the Predicted column to identify which predictions correspond to a predicted positive label. 

And it’s the TP + FP count, as shown below:

![precision of the confusion matrix - classification - machine learning algorithm](https://cdn.hashnode.com/res/hashnode/image/upload/v1645159710034/gBCqiWAAK.png)

> **Precision = TP/ (TP + FP)**

In practice, you’ll often hear people talk about the Precision-Recall Trade-off.

This means you cannot maximize both precision and recall, and will have to choose one over the other depending on the problem at hand.

#### F-measure


![f measure formula - formula based on recall and precision - supervised machine learning - machine learning algorithms](https://cdn.hashnode.com/res/hashnode/image/upload/v1645160284655/NOmF86nFm.png)


It is difficult to compare two models with low precision and high recall or vice versa. So to make them comparable, we use F-Score. F-score helps to measure Recall and Precision at the same time. It uses Harmonic Mean in place of Arithmetic Mean by punishing the extreme values more.


#### High Precision vs High Recall - When to Choose What?

For the problem that you’re solving, ask yourself the question: Which is worse - a False Positive (FP) or a False Negative (FN)?

If you cannot have a False Negative (FN) – Maximize recall

If you cannot have a False Positive (FP) – Maximize precision

**Explanation **

Let's revisit the previous examples of disease detection and spam detection.

In which of the above cases would you prefer a higher recall?

Well, you probably guessed it right. It’s in the case of disease detection that you cannot afford to have a False Negative—therefore, you’ll need a high recall.

You would rather misclassify a patient as having the disease—which is a False Positive(FP). And you’ll follow up with additional medical examination, and be extra cautious—rather than misclassify someone with the disease as healthy. In the worst case it could cost the person's life.

📧 Let us now look at the example of spam detection.

Here, False Positives(FP) can be dangerous.

Recall that in the problem of spam classification tagging an email spam is said to be predicting a positive label.

A spam or two in your inbox does not cost much but what if an email from a recruiter was misclassified as spam? And you never cared to look at it?😟

You’d lose a potential job opportunity. And here’s where you should maximize precision.

📁Not detecting a spam email (False Negative) is not as impactful as predicting a recruiter’s email to be spam (False Positive).

### Explanation of Multiclass Confusion matrix

How would a confusion matrix work for a multi-class classification problem? Well, don’t scratch your head! We will have a look at that here.

Let’s draw a confusion matrix for a multiclass problem where we have to predict whether a person loves Mango, Apple or Orange. The confusion matrix would be a 3 x 3 matrix like this:



![multiclass classification - machine learning - multi-class confusion matrix - learnml.xyz ](https://cdn.hashnode.com/res/hashnode/image/upload/v1645166014558/4N_1eJg7C.png)


| Mango                                  | Orange                                 | Apple                                  |
|----------------------------------------|----------------------------------------|----------------------------------------|
| TP = Cell 1                            | TP = Cell 5                            | TP = Cell 9                            |
| FP = Cell2 + Cell3                     | FP = Cell 4 + Cell 6                   | FP = Cell 7 + Cell 8                   |
| TN = Cell 5 + Cell 6 + Cell 8 + Cell 9 | TN = Cell 1 + Cell 3 + Cell 7 + Cell 9 | TN = Cell 1 + Cell 2 + Cell 4 + Cell 5 |
| FN = Cell 4 + Cell 7                   | FN = Cell 2 + Cell 8                   | FN = Cell 3 + Cell 6                   |

That’s it! You are ready to decipher any N x N confusion matrix!

### Advantages of Confusion Matrix
1. It gives information about errors made by the classifier and the types of errors that are being made.
2. It reflects how a classification model is disorganized and confused while making predictions.
3. This feature assists in prevailing over the limitations of deploying classification accuracy alone.
4. It is practised in conditions where the classification problem is profoundly imbalanced and one class predominates over other classes.
5. The confusion matrix is hugely suitable for calculating Recall, Precision, Specificity, Accuracy and AUC-ROC Curve.

### Conclusion
A confusion matrix is a remarkable approach for evaluating a classification model. It provides accurate insight into how correctly the model has classified the classes depending upon the data fed or how the classes are misclassified. 


### Interview Questions
1. What error metric would you use to evaluate how good a binary classifier is? What if the classes are imbalanced? What if there are more than 2 groups?
2. What do you understand about the true-positive rate and false-positive rate?
3. What is recall ?
4. What is precision ?
5. In which process, we combine precision and recall as weighted harmonic mean ?

### References
1.  Confusion Matrix Calculator -> http://www.marcovanetti.com/pages/cfmatrix/
