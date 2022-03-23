## Histogram - Visualize how frequently data in each class occur in the dataset

### Introduction

In this article are going to see about what is a histogram graph and different interpretations of the histogram graphs. Histograms group the data in bins and are the fastest way to get an idea about the distribution of each attribute in the dataset. It looks very much like a bar chart, but there are important differences between them.


### Histogram

A Histogram is a variation of a bar chart in which data values are grouped together and put into different classes. This grouping enables you to see how frequently data in each class occurs in the dataset. 

The histogram graphically shows the following, 
1. Frequency of different data points in the datasets. 
2. Location of the center of the data. 
3. The spread of the dataset. 
4. Skewness/variance of dataset. 
5. Presence of outliers in the dataset. 

The feature provides a strong indication of the proper distributional model in the data. The probability plot or a goodness-of-fit test can be used to verify the distributional model. 

The histogram contained the following axes:
- **Vertical Axis: ** Frequency/count of each bin. 
- **Horizontal Axis: ** List of bins/categories.


### When to use histogram?

1. The data are numerical.
2. You want to see the shape of the data’s distribution, especially when determining whether the output of a process is distributed approximately normally.
3. Analyzing whether a process can meet the customer’s requirements.
4. Analyzing what the output from a supplier’s process looks like.
5. Seeing whether a process change has occurred from one time period to another.
6. Determining whether the outputs of two or more processes are different.
7. You wish to communicate the distribution of data quickly and easily to others.


### Interpretations of Histogram: 

#### 1. Normal Histogram
It is a classical** bell-shaped** histogram with most of the frequency counts focused in the middle with diminishing tails and there is symmetry with respect to the median.  Since the normal distribution is most commonly observed in real-world scenarios, you are most likely to find these in the Normally distributed histogram mean almost equal to the median.  


![Normal histogram - machine learning - learnml.xyz](https://cdn.hashnode.com/res/hashnode/image/upload/v1648039175724/TRd5kJNfO.png)


#### 2. Non-Normal Short-tailed/ long-tailed histogram

In short-tailed distribution tail approaches 0 very fast, as we move from the median of data, in the long-tailed histogram, the tail approaches 0 slowly as we move far from the median. Here, we refer to tail as the extreme regions in the histogram where most of the data is not-concentrated and this is on both sides of the peak. 


#### 3. Bimodal Histogram
A mode of data represents the most common values in the histogram (i.e peak of the histogram.) A bimodal histogram represents that there are two peaks in the histogram. The histogram can be used to test the unimodality of data. The bimodality (or for instance non-unimodality) in the dataset represents that there is something wrong with the process. 

Bimodal histogram many one or both of two characters. Bimodal normal distribution and symmetric distribution. 


![bimodal histogram - machine learning - learnml.xyz](https://cdn.hashnode.com/res/hashnode/image/upload/v1648039267625/WFVsraugo.png)

#### 4. Skewed left/right histogram

Skewed histograms are those where the one-side tail is quite clearly longer than the other-side tails. A right-skewed histogram means that the right-sided tail of the peak is more stretched than its left and vice-versa for the left-sided. In a left-skewed histogram, the mean is always lesser than the median, while in a right-skewed histogram mean is greater than the histogram. 


![left skewed histogram - machine learning - learnml.xyz](https://cdn.hashnode.com/res/hashnode/image/upload/v1648039325581/FepqxpoyP.png)


![right skewed histogram - machine learning - learnml.xyz](https://cdn.hashnode.com/res/hashnode/image/upload/v1648039354851/3CNkqYcWl.png)


#### 5. Uniform Histogram
In the uniform histogram, each bin contains approximately the same number of counts (frequency). An example of the uniform histogram is as a die is rolled n (n>>30) a number of times and record the frequency of the different outcomes. 


![uniform histogram - machine learning - learnml.xyz](https://cdn.hashnode.com/res/hashnode/image/upload/v1648039410520/BDU-_Kuyr.png)

#### 6. Normal Distribution with an outlier

This histogram is similar to a normal histogram except it contains an outlier where the count/probability of the outcome is substantive. This is mostly due to some system errors in the process, which led to a faulty generation of products etc.


![normal distribution with an outlier - machine learning - learnml.xyz](https://cdn.hashnode.com/res/hashnode/image/upload/v1648039444755/mDhowHEPS.png)


### Conclusion

In this article, we have seen different types of histograms plots which could help us identify the dataset which helps in understanding the dataset better. 