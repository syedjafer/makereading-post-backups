## Types of MEAN - ( Measure of Central Tendency )

### Introduction

To represent a dataset as a 1-number summary, we use the central tendency measure. There exist three central tendency measures i.e. Mean, Median & Mode. Why was there a need for these three measures when only one (Mean) could have done the job?  
In this article, we are going to see the different types of Mean and their functionalities. 
It's one of the most important concepts of statistics, a crucial subject to learn machine learning. 

### Arithmetic Mean

#### **Logic**
It's the mathematical expectation of a discrete set of numbers or averages. 
The mathematical symbol of Arithmetic mean is, 
![Arithmetic mean - machine learning - learnml.xyz](https://cdn.hashnode.com/res/hashnode/image/upload/v1648012694975/mWRi5yzXx.png)

It's pronounced as "**x-bar**". Its the sum of all discrete values in the set divided by the total number of values in the set. The formula to calculate the mean of n values is, 


![Arithmetic mean formula - machine learning  - statistics - learnml.xyz](https://cdn.hashnode.com/res/hashnode/image/upload/v1648012917083/UhERO2o5A.png)

#### **Example:**
> Values of the set = { 2, 6, 7, 5, 5 } <br>
> Sum = 25 <br>
> n, Total Values = 5 <br>
> Arithmetic Mean = 25/5 = 5 <br>

#### **Code:**

```python
import statistics
data = [  2, 6, 7, 5, 5 ]
x = statistics.mean(data)
print("Arithmetic Mean is ", x)
```

#### **Output:**
![arithmetic mean - machine learning - learnml.xyz](https://cdn.hashnode.com/res/hashnode/image/upload/v1648014584831/GT6X27Peu.png)

### Trimmed Mean

#### **Logic:** 
Arithmetic Mean is influenced by the outliers (extreme values) in the data. So, trimmed mean is used at the time of pre-processing when we are handling such kinds of data in machine learning. 

Its arithmetic has a variation (i.e) it is calculated by dropping a fixed number of **sorted values** from each end of the sequence of data given and then calculating the mean (average) of remaining values. 


![formula of trimmed mean - machine learning - learnml.xyz](https://cdn.hashnode.com/res/hashnode/image/upload/v1648014960278/I285wIiTZ.png)

#### **Example:**
> Values of the set = {  1, 3, 4, 8  } <br>
> k => n* alpha; alpha = 0.25; k = 4*0.25 = 1 <br>
> Remaining values of the set = { 3, 4 }
> **R**, denominator value  =  total values - 2k = 4 - 2(1) = 2

#### **Code:**
```python
data = [1, 3, 4, 8]
x = stats.trim_mean(data, 0.25)
print("Trimmed Mean is ", x)
```

#### **Output:**


![trimmed mean - machine learning - learnml.xyz](https://cdn.hashnode.com/res/hashnode/image/upload/v1648015455066/Gte9te8GK.png)

### Weighted Mean

#### Logic:
Arithmetic Mean or Trimmed Mean is giving equal importance to all the parameters involved. But whenever we are working in machine learning predictions, there is a possibility that some parameter values hold more importance than others, so we assign high weights to the values of such parameters. Also, there can be a chance that our data set a highly variable value of a parameter, so we assign lesser weights to the values of such parameters. 


![weighted mean formula - machine learning - learnml.xyz](https://cdn.hashnode.com/res/hashnode/image/upload/v1648015841285/KxgUum_Fy.png)

#### Example:

> Values of the set = [ 0, 2, 1, 3] <br>
> Weight = [ 1, 0, 1, 1] <br>
> Sum ( Weight * Values of the set ) = 0*1 + 2*0 + 1*1 + 3*1 = 4<br>
> Sum (Weight) = 3 <br>
> Weighted Mean = 4 / 3 = 1.3333 <br>

#### Code: 
```python
data = [0, 2, 1, 3]
x = np.average(data, weights=[1, 0, 1, 1])
print("Weighted Mean is :", x)
```

#### Output:


![Weighted Mean formula - machine learning - learnml.xyz](https://cdn.hashnode.com/res/hashnode/image/upload/v1648016211321/wDmmw78ou.png)

### Geometric Mean

#### Logic: 
As arithmetic mean is the sum of all the discrete values in the set, Geometric mean is the product of discrete values in the set. It's useful for the set of positive discrete values. 


![Geometric mean formula - machine learning - learnml.xyz](https://cdn.hashnode.com/res/hashnode/image/upload/v1648016502502/eFHBd75_V.png)

#### Example:

> Values of the set = { 1, 3, 9 } <br>
> product = 1*3*9 = 27 <br>
> n, Total values = 3 <br>
> Harmonic Mean = (27)^(1/3) <br>


#### Code: 
```python
x = stats.mstats.gmean([1, 3, 9])
print("Geometric Mean is ", x)
```

#### Output:


![Geometric mean formula - machine learning - learnml.xyz](https://cdn.hashnode.com/res/hashnode/image/upload/v1648016788098/yeRHNs8FF.png)

### Harmonic Mean

#### Logic: 
Harmonic mean plays it role when it comes to calculating the mean of the terms which are defined in relation to any unit. Its the reciprocal of the mean of the reciprocal of the data. It's used when inverse variation in relation is involved in the data. 


![Harmonic mean formula - machine learning - learnml.xyz](https://cdn.hashnode.com/res/hashnode/image/upload/v1648016995007/0E7WMHVAI.png)

#### Example:

> Values of the set : { 1, 3, 9 } <br>
> Sum of reciprocals = 1/1 + 1/3 + 1/9 <br>
> n, Total Values = 3 <br>
> Harmonic Mean  = 3 / (sum of reciprocals) <br>

#### Code:

```python
x = stats.mstats.hmean([1, 3, 9])
print("Harmonic Mean is ", x)
```

#### Output:


![Harmonic mean output - machine learning - learnml.xyz](https://cdn.hashnode.com/res/hashnode/image/upload/v1648017288730/KivnbZD3v.png)


### Conclusion

In this article, we have seen the various types of mean which could be imbibed into feature selection, feature transformation, feature engineering. This could be used in filling missing values aswell.  



