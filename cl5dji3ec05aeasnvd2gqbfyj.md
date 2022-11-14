# Analysis Report - Predicting if income exceeds 50K per year based on US Census Data with Simple Classification Techniques

### Datasource

1. Kaggle Notebook: [US Adult Income Survey](https://www.kaggle.com/code/syedjaferk/us-adult-income-survey).
2. Dataset: [Us Adult income survey - dataset ](https://archive.ics.uci.edu/ml/datasets/adult)

### Introduction

The US Adult Census dataset is a repository of 48,842 entries extracted from the 1994 US 
Census database. In this article we will explore the data at face value in order to understand the trends and representations of certain demographics in the corpus. 

Then we will find the relationship between each column with the target value, and we will define the model to predict whether an individual made more or less than 50K in 1994. 

Then we will compare the models which better suits the dataset. 

### Exploratory Analysis

#### The Dataset Dictionary
The census income dataset has 48,842 entries. Each entry contains the following information 
about an individual.

1. **age**: The age of an individual. Integer greater than 0. 
2. **workclass**: A general term to represent the employment status of an individual 
(Private, Self­emp­not­inc, Self­emp­inc, Federal­gov, Local­gov, State­gov, Without­pay, Never­worked. )
3. **fnlwgt**: Final Weight. In other words, this is the number of people the census believes 
the entry represents. Integer greater than 0.
4. **education**: The highest level of education acheived an individual. (Bachelors, Some­college, 11th, HS­grad, Prof­school, Assoc­acdm, Assoc­voc, 9th, 7th­8th, 12th, Masters, 1st­4th, 10th, Doctorate, 5th­6th, Preschool.)
5. **education-num**: The **highest level of education** achieved in numerical form. Integer greater than 0.
6. **marital­status**: The marital status of an individual. Married­civ­spouse corresponds to a 
civilian spouse while Married­AF­spouse is a spouse in the Armed Forces. Married­civ­spouse, Divorced, Never­married, Separated, Widowed, Married­spouse­absent, Married­AF­spouse.  
7. **occupation**: The general type of occupation of an individual. (Tech­support, Craft­repair, Other­service, Sales, Exec­managerial, Prof­specialty, Handlers­cleaners, Machine­op­inspct, Adm­clerical, 
Farming­fishing, Transport­moving, Priv­house­serv, Protective­serv, Armed­Forces.  )
8. **relationship**: represents what this individual is relative to others. For example an 
individual could be a Husband. Each entry only has one relationship attribute and is 
somewhat redundant with marital status. We might not make use of this attribute at all. (Wife, Own­child, Husband, Not­in­family, Other­relative, Unmarried. )
9. **race**: Descriptions of an individual's race. (White, Asian­Pac­Islander, Amer­Indian­Eskimo, Other, Black. )
10. **sex**: The bilogical sex of the individual (Male, Female)
11. **Capital gain**: Capital gains for an individual 
12. **Capital loss**: Capital loss for an individual. 
13. **hours­per­week**: the hours an individual has reported to work per week (continuous.)
14. **native-country**:  Country of origin of an individual. (United­States, Cambodia, England, Puerto­Rico, Canada, Germany, Outlying­US(Guam­USVI­etc), India, Japan, Greece, South, China, Cuba, Iran, 
Honduras, Philippines, Italy, Poland, Jamaica, Vietnam, Mexico, Portugal, Ireland, France, Dominican­Republic, Laos, Ecuador, Taiwan, Haiti, Columbia, Hungary, Guatemala, Nicaragua, Scotland, Thailand, Yugoslavia, El­Salvador, Trinadad&Tobago, Peru, Hong, Holand­Netherlands. )
15. **the label**: whether or not an individual makes more than 50K annually.

The original dataset contains a distribution of 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1657343070330/Hgg763PLn.png align="left")

To gain insights about which features would be most helpful for this dataset, we look at the feature and the distribution of entries that are labelled >50k and <=50k. 

#### Column : Age. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1657343725948/cfCtQjydu.png align="left")

The age feature describes the age of the individual. **Fig. 1** shows the age distribution among the entries in our dataset. The ages range from 17 to 90 years old with the majority of entries between the ages of 25 and 50 years. Because there are so many ages being represented, we bucket the entries into age groups with intervals of ten years to present the data more concisely as seen in **​Fig 2**​. 
We are considering the starting age as 14 as per https://www.dol.gov/general/topic/youthlabor/agerequirements

Looking at the graph, we can see that there is a significant amount of **variance** between the ratio of  >50k to <=50k between the age groups. The most interesting ratios to note are those of groups 10s, 70s and 80s where there is almost no chance to have an income of greater than 50K.  The ratio of entries labeled >50k to <=50k for age groups 20s, 30s, 40s and 50s vary significantly as well. 

#### Column: Workclass


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1657344271196/uPidPZ5lT.png align="left")



As seen in **​Fig. 3**, the majority of the individuals work in the **private sector**. The one 
concerning statistic is the number of individuals with an **Missing** work class. The probabilities 
of making above 50K are similar among the work classes except for **self­emp­inc and 
federal government**. Federal government is seen as the most elite in the public sector, which 
most likely explains the higher chance of earning more than 50k. **self­emp­inc** implies that the individual owns their own company, which is a category with an almost infinite ceiling when it comes to earnings. The complete Work Class vs Income graph can be seen in ​**Fig. 4**.  From **Fig.4**, we can see that individuals who work in private workclass, has more probabilities of making more than 50k. 


#### Column: fnlgwt

Final Weight. final weight. In other words, this is the number of people the census believes the entry represents. Since this is not having any predictive power, we can remove this column. 

#### Column: Education, Education num. 

Since these two columns are representing the same data on education, we can ignore any one of them. Here to avoid more work we can ignore the categorical column  
1. Education: the highest level of education achieved by an individual. (Bachelors, Some­college, 11th, HS­grad, Prof­school, Assoc­acdm, Assoc­voc, 9th, 7th­8th, 12th, Masters, 1st­4th, 10th, Doctorate, 5th­6th, Preschool)
2. education­num​: the highest level of education achieved in numerical form. 



![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1657345974137/P2XsWKa29.png align="left")


There is relationship between the highest level of education and the number of people labeled >50k and <=50k. For the most part, **a higher level of education** is correlated to a **higher percentage of individuals with the label >50k.**


#### Column: Maritalstatus


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1657346212665/S8tmI4hHJ.png align="left")

From the **Fig. 6**, Married-civ-spouse is having the highest probabilities of earning above 50k. Also people who never-married and divorcee, were having almost equal ratios of earning above 50k. And people who are separated, Married-AF-Spouse, Widowed were no probabilities of earning above 50k. 


#### Column: Occupation 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1657347537815/OM0XFdfM8.png align="left")

As seen in **​Fig. 7**​, there is a somewhat uniform distribution of occupations in the dataset, 
disregarding the absence of Armed Forces. However, looking at ​**Fig. 8** Occupation vs 
Income​, exec­-managerial and prof­-specialty stand out as having very high percentages of 
individuals making over 50K. 
In addition, the percentages for Farming­fishing, Other­service and Handlers­cleaners are significantly lower than the rest of the distribution. The one concerning statistic looking at **​Fig. 8** ​is the high number of individuals with unknown occupations.


#### Column: Relationship


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1657347764485/Mcq5nuWL7.png align="left")

1. Husbands are having higher probabilities of making over 50k
2. Not-in-family and Wife were having the same probabilities of making above 50k
3. Individuals who are unmarried is having lower probabilities of making above 50k

#### Column: Sex


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1657347995073/ENT1Bqb-_.png align="left")

In the given dataset, there is not a normal distribution found. Percentage of male is higher than the female. 

In ​**Fig 11​, ** we can see that there is almost double the sample size of males in comparison 
to females in the dataset. While this may not affect our predictions too much, the distribution 
of income can. As seen in ​**Fig 12​,** the percentage of males who make greater than 50K is much greater than the percentage of females that make the same amount. This will certainly be a significant factor, and should be a feature considered in our prediction model.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1657348165345/P-6CmlC1k.png align="left")

#### Column: Race. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1657348238279/KCsLDtLiH.png align="left")

Looking at the ​above image​, it seems like the feature could be useful in our prediction model, as 
Whites and Asians have a larger percentage of entries greater than 50k than the rest of the races. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1657348337613/TiuH4-S3c.png align="left")

However, the sample size of Whites in the dataset is disproportionately large in comparison to all other races. The second most represented group is Blacks with less than 5000 entries. The lack of equal distribution caused us to consider not utilizing this attribute in our prediction model.


#### Column: Capital Gain


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1657348462630/9YELU8ARR.png align="left")

For the column, capital_gain we can see, there are many zero values. These wont have the predictive power. So we can remove this column


#### Column: Capital Loss


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1657348515324/L6cOK1oZA.png align="left")

For the column, capital_loss we can see, there are many zero values. These wont have the predictive power. so we can remove this column. 

#### Column: Hours Week


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1657348741394/Zre1dzDMw.png align="left")


Looking at the distribution in ​**Fig. 13 **​, the vast majority of individuals are working 40 hour 
weeks which is expected as the societal norm. Regardless of the nonuniform distribution, 
**Fig. 14**​ shows that the percentage of individuals making over 50k drastically decreases when less than 40 hours per week, and increases significantly when greater than 40 hours per week. 


#### Column: Country


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1657348879737/tv8rCJ3GN.png align="left")

The country column is been divided into two categories US / Not Us. From the above comparison image, we can see that people is us is having a higher probabilities of making more than 50k. 

#### Removal of Features 
We also opted to not use the features: ‘fnlwgt’, ‘relationships’, and ‘capitalGains/Loss’. These 
features either were not useful for our analysis or had too much bad data i.e. zero­values, 
unknown/private values. 

### Model 

#### Logistic Regression 

```
from sklearn.linear_model import LogisticRegression
lg_model = LogisticRegression()
lg_model.fit(X_train, y_train)
y_pred = lg_model.predict(X_test)
print("Accuracy Score: {}".format(accuracy_score(y_test, y_pred)))
print("Confusion Matrix:\n {}".format(confusion_matrix(y_test, y_pred)))
print("Classification Report:\n {}".format(classification_report(y_test, y_pred)))

```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1657349059855/_1RPqunZ2.png align="left")


#### Multinomial Naive Bayes

```


from sklearn.naive_bayes import MultinomialNB
clf = MultinomialNB()
clf.fit(X_train, y_train)
y_pred = clf.predict(X_test)
print("Accuracy Score: {}".format(accuracy_score(y_test, y_pred)))
print("Confusion Matrix:\n {}".format(confusion_matrix(y_test, y_pred)))
print("Classification Report:\n {}".format(classification_report(y_test, y_pred)))


```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1657349116854/LHqRrhf1I.png align="left")


#### Decision Tree

```
from sklearn.tree import DecisionTreeClassifier
clf = DecisionTreeClassifier()
clf = clf.fit(X_train, y_train)
y_pred = clf.predict(X_test)
print("Accuracy Score: {}".format(accuracy_score(y_test, y_pred)))
print("Confusion Matrix:\n {}".format(confusion_matrix(y_test, y_pred)))
print("Classification Report:\n {}".format(classification_report(y_test, y_pred)))
```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1657349154588/OA0irGSvz.png align="left")

#### Random Forest

```


from sklearn.ensemble import RandomForestClassifier
clf = RandomForestClassifier()
clf = clf.fit(X_train, y_train)
y_pred = clf.predict(X_test)
print("Accuracy Score: {}".format(accuracy_score(y_test, y_pred)))
print("Confusion Matrix:\n {}".format(confusion_matrix(y_test, y_pred)))
print("Classification Report:\n {}".format(classification_report(y_test, y_pred)))


```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1657349195152/nSPYHf193.png align="left")

#### Ada Boost Classifer

```


from sklearn.ensemble import AdaBoostClassifier
clf = AdaBoostClassifier(random_state=40)
clf = clf.fit(X_train, y_train)
y_pred = clf.predict(X_test)
print("Accuracy Score: {}".format(accuracy_score(y_test, y_pred)))
print("Confusion Matrix:\n {}".format(confusion_matrix(y_test, y_pred)))
print("Classification Report:\n {}".format(classification_report(y_test, y_pred)))


```


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1657349286535/PYRKS0FTu.png align="left")


#### Light GBM

```


import lightgbm as lgb
clf = lgb.LGBMClassifier()
clf.fit(X_train, y_train)
y_pred = clf.predict(X_test)
print("Accuracy Score: {}".format(accuracy_score(y_test, y_pred)))
print("Confusion Matrix:\n {}".format(confusion_matrix(y_test, y_pred)))
print("Classification Report:\n {}".format(classification_report(y_test, y_pred)))


```

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1657349321467/We5K_g5sG.png align="left")

#### Model Comparison

| Algorithm |  Accuracy |
|---|---|
| Logistic Regression  | 0.8388206388206388  |
| Multinomial Naive Bayes  | 0.807002457002457  |
| DecisionTreeClassifier  |  0.8116707616707617 |
| ExtraTreesClassifier  |  0.8182432432432433 |
| AdaBoostClassifier  | 0.8385749385749386 |
| LightGBM | 0.842997542997543 |

### Inference

From the above analysis we can say that 'Light GBM ' is performing good for this dataset. 







