## Machine Learning - (Not the Traditional Learning)

### 1. Short History: 

First, we can see the when the concept of machine learning started. Many genius individuals contributed to its development. But there's one person who stands out when thinking about when ML was invented. **Arthur Samuel**, a computer scientist at IBM and a pioneer in AI and computer gaming, coined the term “**Machine Learning**” in **1952**.

### 2. Definition :
According to *Arthur Samuel*, 
> "the field of study that gives computers the ability to learn without being explicitly programmed."
This is an older, informal definition. 

Tom Mitchell, another pioneer in AI, provides a more modern definition. 
> A computer program is said to learn from experience E with respect to some class of tasks T and performance measure P, if its performance at tasks in T, as measured by P, improves with experience E. <br><br>
> **Example:** playing checkers. <br>
>    E = the experience of playing many games of checkers. <br>
>    T = the task of playing checkers. <br>
>    P = the probability that the program will win the next game. <br>

Yeah, I can understand, the above definition also kind of difficult to understand and get something out of it . But if you are in India, pursuing some courses, the above definition will gain you 5 marks. 

Okay, Now we will try to understand the jargon/process Machine Learning. 

Machine learning is a branch of artificial intelligence (AI) and computer science which focuses on the use of data and algorithms to imitate the way that humans learn, gradually improving its accuracy. 

Machine learning is an important component of the growing field of data science. Through the use of statistical methods, algorithms are trained to make classifications or predictions, uncovering key insights within data mining projects. These insights subsequently drive decision making within applications and businesses, ideally impacting key growth metrics. 

As big data continues to expand and grow, the market demand for data scientists will increase, requiring them to assist in the identification of the most relevant business questions and subsequently the data to answer them.

### 3. Explanation: 
We will try to compare Machine learning with Traditional software/program. 

In the traditional software development, We will be having the input and algorithm (rules/formulas) , then by applying the input data on formula we will get the output (as expected.)

In the machine learning ( so called process ), we will give the input and the output to the system, then the machine/computer will give us the algorithm or rule. Simple. 


![Screenshot from 2022-02-12 17-08-40.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644669506213/7iXMCvHam.png)


### 4. Explanation with Code:
Now, we can consider an example, Calculating Fahrenheit with Celsius given. 

![Screenshot from 2022-02-12 17-10-23.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644669609301/6du5hUSYB.png)


Traditional System, 

```python
c = [0, 8, 15, 22, 38]

def calculate_farenheit(celcius):
    _farenheit = celcius * 1.8 + 32
    return _farenheit

for celcius in c:
    print(calculate_farenheit(celcius))

``` 

> Output: 
32.0
46.4
59.0
71.6
100.4

<iframe width="800" height="500" src="https://www.youtube.com/embed/andLU_LKIXM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



Using Machine Learning, 

![Screenshot from 2022-02-12 17-11-25.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644670886023/Ly1u6wxmY.png)

Here we have used the simple linear regression algorithm with gradient descent (for time being don't think too much on algorithm ). 

 <iframe width="800" height="500" src="https://www.youtube.com/embed/1RrfWxWino4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Colab Link to [Simple Linear Regression](https://colab.research.google.com/drive/1WvU255eTURQF8phwiuaTvX8pTQZk-RQX?usp=sharing) using gradient descent. We will see in detail in upcoming articles (stay tuned).


```python
import numpy as np

farenheit = np.array([32, 46.4, 59, 71.6, 100.4]) 
celcius = np.array([0, 8, 15, 22, 38])

def to_farenheit(celcius): # Traditional Way 
  return celcius*1.8 + 32

# Model Weights
m = 0.1
c = 0.1

# Hyperparameters
learning_rate = 0.001 # The learning Rate 0.1, 0.001, 0.0001 # adaptive lr
epochs = 8000 # The number of iterations to perform gradient descent

n = len(celcius)
error_vals = []

# Performing Gradient Descent
for i in range(epochs):
  # Forward propagation (basically multiplication)
  y_hat = m*celcius + c # The current predicted value of Y

  # Find the Gradients
  de_dm = (-2/n) * np.sum(celcius * (farenheit - y_hat)) # Derivative of error function wrt m
  de_dc = (-2/n) * np.sum(farenheit - y_hat) # Derivative of error function wrt c

  # Back propagation (update the weights)
  m = m - (de_dm * learning_rate)
  c = c - (de_dc * learning_rate)

for _c in celcius:
  print( _c*round(m,2) + round(c) , to_farenheit(_c) )

``` 

### 5. Applications of Machine Learning:

![Screenshot from 2022-02-12 17-13-32.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644672485629/nBMMeIfYl.png)


- **Speech Recognition:**  It is also known as automatic speech recognition (ASR), computer speech recognition, or speech-to-text, and it is a capability which uses natural language processing (NLP) to process human speech into a written format. Many mobile devices incorporate speech recognition into their systems to conduct voice search—e.g. Siri—or provide more accessibility around texting.

- **Customer Service: ** Online chatbots are replacing human agents along the customer journey. They answer frequently asked questions (FAQs) around topics, like shipping, or provide personalized advice, cross-selling products or suggesting sizes for users, changing the way we think about customer engagement across websites and social media platforms. Examples include messaging bots on e-commerce sites with virtual agents, messaging apps, such as Slack and Facebook Messenger, and tasks usually done by virtual assistants and voice assistants.

- **Computer Vision:** This AI technology enables computers and systems to derive meaningful information from digital images, videos and other visual inputs, and based on those inputs, it can take action. This ability to provide recommendations distinguishes it from image recognition tasks. Powered by convolutional neural networks, computer vision has applications within photo tagging in social media, radiology imaging in healthcare, and self-driving cars within the automotive industry.

- **Recommendation Engines:** Using past consumption behavior data, AI algorithms can help to discover data trends that can be used to develop more effective cross-selling strategies. This is used to make relevant add-on recommendations to customers during the checkout process for online retailers.

- **Automated stock trading:** Designed to optimize stock portfolios, AI-driven high-frequency trading platforms make thousands or even millions of trades per day without human intervention.

### 6. Types of Machine Learning Algorithm :

Generally, there are 3 types of machine learning algorithm, 
1. Supervised Learning ( We know the output )
2. Unsupervised Learning ( We don't know the output )
3. Reinforment Learning ( Learning from mistake and reward )

![machine-learning-types-infographics_1-1536x695.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644672773924/aYfC6nU7I.png)


1.Supervised Learning: 
It consist of a target / outcome variable (or dependent variable) which is to be predicted from a given set of predictors (independent variables). Using these set of variables, we generate a function that map inputs to desired outputs. The training process continues until the model achieves a desired level of accuracy on the training data.

Example: 

- Regression
- Decision Tree
- Random Forest
- KNN
- Logistic Regression

2.Unsupervised Learning:
In this algorithm, we do not have any target or outcome variable to predict / estimate. It is used for clustering population in different groups, which is widely used for segmenting customers in different groups for specific intervention.

Example: 

- Apriori Algorithm
- K-means Algorithm

3.Reinforcement Learning:
Using this algorithm, the machine is trained to make specific decisions. It works this way: the machine is exposed to an environment where it trains itself continually using trial and error. This machine learns from past experience and tries to capture the best possible knowledge to make accurate business decisions

Example:

- Markov Decision process



### 7. Conclusion :
I hope you understood what is a machine learning algorithm is and you might be interested in learning this concept. In the upcoming articles we will see various algorithms from scratch with example projects from kaggle. Will see you in the next article !. Until then bye from **LearnML.** 

### 8. Interview questions : 

- What is machine learning ?
- Why people choose machine learning ?
- How machine learning is different from conventional/traditional learning ?
- What is supervised algorithm ?
- I am having a dataset, but not sure what to do with it. So how can i get the insights from the data. 

> Answers will be discussed in the next article. 
.
.
.
I got it. How will you know when i will be publishing the next article. Please subscribe to mail letter. 
