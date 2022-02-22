## Quartiles and Percentiles

### Introduction

Usually, partition values are those values of the variable which divide the distribution into
a certain number of equal parts. 

As a matter of fact, commonly used partition values are **quartiles, deciles, and percentiles.**
For example, quartiles divide the data into four equal parts. Similarly, deciles and percentiles divide
the distribution into ten and hundred equal parts, respectively.

### Quartiles 

Quartiles are values that divide data into quarters. the data is divided into four segments according to where the numbers fall on the number line. 

The four quarters that divide a data set into quartiles are:

**First Quartile:** The lowest 25% of numbers.
**Second Quartile:** The next lowest 25% of numbers (up to the median).
**Third Quartile:** The second highest 25% of numbers (above the median).
**Fourth Quartile: **The highest 25% of numbers.

> **Median: ** The value separating the higher half from the lower half of a data sample. In other words, Median is the **middle element in the sorted elements** (ascending or descending) , which can be more descriptive than the average of the elements.

This parting of data to 4 parts 


Let us consider the below data, 

```python
data = [  3, 3, 4, 5, 2, 4, 3, 5, 6, 10, 9 , 12, 34, 12, 45, 7 ]
```
Let's Sort the data, 

```python
data.sort()
print(data)

# Output
[2, 3, 3, 3, 4, 4, 5, 5, 6, 7, 9, 10, 12, 12, 34, 45]
```
we can see its having 16 numbers, so we can take middle two numbers and take average of it, 


![Screenshot from 2022-02-22 09-23-29.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645502206150/nvMSNV6Kd.png)

We can see the middle numbers are 5 (at index 7) and 6 (at index 8). so the average of these two numbers is 5.5. So Our Median is 5.5

So now we have separated our dataset in to two halves, 

Now, if we are repeating this process one time on the right hand side of the median and one time on the left hand side of the median, we will derive the interquartile regions. 

#### Deriving Q2 (Left Hand Side)

On the left hand side, we need to find median between index 0 (start) and index of median (here 7).

![Screenshot from 2022-02-22 09-40-33.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645503134655/DcvzP5yV5.png)
 
#### Deriving Q3 (Right Hand Side)

On the right hand side, we need to find the median between index of median (here 8) and the last element (index 15)


![Screenshot from 2022-02-22 09-44-45.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645503302472/1mpaPpeyg.png)

Repeating the same for first element and Q2 is Q1. Similarly between Q3 and last element is Q4. For visualizing the quartiles, there is a special kind of graph is available named "Box Plot"


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645503460412/emTKgVfIg.png)

In the above box plot, we are able to see some dots at the end ( at 35 and 45 ). These are Outliers. we will discuss in detail in further session. 

> **Outlier** : An outlier is a data point that is noticeably different from the rest. They represent errors in measurement, bad data collection, or simply show variables not considered when collecting the data.

#### What are Quartiles used for ? : 
1. To Calculate Interquartile Range: The measure of how the data is spread out around the mean. (used to identify the outliers)
2. To Calculate Bowley’s Coefficient of Skewness.

### Percentiles
A percentile is a measure at which that percentage of the total values are the same as or below that measure. For example, 90% of the data values lie below the 90th percentile, whereas 10% of the data values lie below the 10th percentile.


In similar fashion, Percentiles divide the whole distribution into 100 equal parts.

Put another way, P1, P2, …, P99 are known as 1st percentile, 2nd percentile,…,99th percentile, and ith percentile contains the (iN/100)th part of data.

Here, please note that we should arrange data in ascending or descending order of magnitude.

### Notebook

Colab Notebook: https://colab.research.google.com/drive/1mr5gTTbK_liZEiWfl_Kvq5hsqn9CSxyg?usp=sharing

### Conclusion

So far we have answered the question of "What ?". In the upcoming articles we will see the actual usage in Feature Transformation, Outlier Detection and many more. 


