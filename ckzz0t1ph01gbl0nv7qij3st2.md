## Feature Engineering in Time Series Data

### Colab Notebook

All Experiments done in this blog is available in this [notebook](https://colab.research.google.com/drive/143F00_jnWwTujwdpv_-eczNKXVfvq88z?usp=sharing). Please take a copy and try it. 

### Introduction

Time is the most essential concept in any business. We map our sales numbers, revenue, bottom line, growth, and even prepare forecasts – all based on the time component.

But consequently, this can be a complex topic to understand for beginners. There is a lot of nuance to time series data that we need to consider when we’re working with datasets that are time-sensitive.

Existing time series forecasting models undoubtedly work well in most cases, but they do have certain limitations. In this article we will be seeing the various feature engineering techniques for extracting useful information using the date-time column.

### What is Time Series Analysis ?

Time series analysis is a specific way of analyzing a sequence of data points collected over an interval of time. In time series analysis, analysts record data points at consistent intervals over a set period of time rather than just recording the data points intermittently or randomly.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645581534492/cudIJGlgM.png)

It refers to identifying the common patterns displayed by the data over a period of time. For this, experts employ specific methods to study the data’s characteristics characteristics and extract meaningful statistics that eventually aid in business forecasting.

So, what makes time series projects different from the traditional machine learning problems?

Let’s take a simple example to understand this. If we want to predict today’s stock price for a certain company, it would be helpful to have information about yesterday’s closing price, right? Similarly, predicting the traffic on a website would be a lot easier if we have data about the last few months or years.

There’s another thing we need to consider – time series data may also have certain trends or seasonality. Take a look at the plot shown below about the number of tickets booked for an airline over the years: 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645581779840/5TELHPC5R.png)
<small>Image Source : solver.com</small>

We can clearly see an increasing trend. Such information can be useful for making more accurate predictions. Now, let’s take a dataset with date-time variables and start learning about feature engineering!

### Dataset 

In this article we are going to use the JetRail dataset. 
> JetRail uses Jet propulsion technology to run rails and move people at a high speed! While JetRail has mastered the technology and they hold the patent for their product, the investment would only make sense, if they can get more than 1 Million monthly users with in next 18 months.

(checkout the [notebook](https://colab.research.google.com/drive/143F00_jnWwTujwdpv_-eczNKXVfvq88z?usp=sharing) for practising and tryouts.)

```python
import numpy as np
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

from matplotlib import rcParams
plt.style.use('fivethirtyeight')
# figure size in inches
rcParams['figure.figsize'] = 11.7,5.27

train_df = pd.read_csv('https://raw.githubusercontent.com/syedjafer/datasets/main/time_series_data_1/Train_SU63ISt.csv')
test_df = pd.read_csv('https://raw.githubusercontent.com/syedjafer/datasets/main/time_series_data_1/Test_0qrQsBZ.csv')

train_df.head()
```

![Screenshot from 2022-02-23 08-53-35.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645586637781/RYejv4PAr.png)

If we are looking to the data types of the columns, 

```python
train_df.dtypes
```


![Screenshot from 2022-02-23 08-56-34.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645586806154/veCpPN_p8.png)


We have two columns here – so it’s clearly a univariate time series. Also, the data type of the date variable is taken as an object, i.e. it is being treated as a categorical variable. Hence, we will need to convert this into a DateTime variable. We can do this using the appropriately titled datetime function in Pandas:


![Screenshot from 2022-02-23 08-57-55.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645586887603/kChhyIgz7.png)

Now that we have the data ready, let’s look at the different features we can engineer from this variable. Along with each of these feature engineering techniques, we will discuss different scenarios where that particular technique can be useful.

### Date-Related Features

Have you ever worked in a product company? You’ll be intimately familiar with the task of forecasting the sales for a particular product. We can find out the sales pattern for weekdays and weekends based on historical data. Thus, having information about the day, month, year, etc. can be useful for forecasting the values.

Let’s get back to our JetRail project.

We have to forecast the count of people who will take the JetRail on an hourly basis for the next 7 months. This number could be higher for weekdays and lower for weekends or during the festive seasons. Hence, the day of the week (weekday or weekend) or month will be an important factor.

Extracting these features is really easy in Python:

```python
train_df['year']=train_df['Datetime'].dt.year 
train_df['month']=train_df['Datetime'].dt.month 
train_df['day']=train_df['Datetime'].dt.day

train_df['dayofweek_num']=train_df['Datetime'].dt.dayofweek  
train_df['dayofweek_name']=train_df['Datetime'].dt.weekday

train_df.head()

```


![Screenshot from 2022-02-23 09-00-30.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645587056815/lsL2ENFHK.png)

### Time-Based Features

We can similarly extract more granular features if we have the time stamp. For instance, we can determine the hour or minute of the day when the data was recorded and compare the trends between the business hours and non-business hours.

If we are able to extract the ‘hour’ feature from the time stamp, we can make more insightful conclusions about the data. We could find out if the traffic on JetRail is higher during the morning, afternoon or evening time. Or we could use the value to determine the average hourly traffic throughout the week, i.e. the number of people who used JetRail between 9-10 am, 10-11 am, and so on (throughout the week).

Extracting time-based features is very similar to what we did above when extracting date-related features. We start by converting the column to DateTime format and use the .dt accessor. Here’s how to do it in Python:

```python

train_df['Hour'] = train_df['Datetime'].dt.hour 
train_df['minute'] = train_df['Datetime'].dt.minute 

train_df.head()
```

![Screenshot from 2022-02-23 09-01-52.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645587130846/qZkHu5PZr.png)

Similarly, we can extract a number of features from the date column. 

### Lag Features

we can also use the target variable for feature engineering. 

Consider this – you are predicting the stock price for a company. So, the previous day’s stock price is important to make a prediction, right? In other words, the value at time t is greatly affected by the value at time t-1. The past values are known as lags, so t-1 is lag 1, t-2 is lag 2, and so on.

```python

train_df['lag_1'] = train_df['Count'].shift(1)
train_df = train_df[['Datetime', 'lag_1', 'Count']]
train_df.head()
```

![Screenshot from 2022-02-23 09-04-13.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645587265674/izqh-Q_tF.png)

### Rolling Window Feature

The Method of calculating the statistical values based on the past values is called the rolling window method because the window would be different for every data point.

![3hotmk.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1645587458916/3SDCaIRLz.gif)

Since this looks like a window that is sliding with every next point, the features generated using this method are called the ‘rolling window’ features.

Now the question we need to address – how are we going to perform feature engineering here? Let’s start simple. We will select a window size, take the average of the values in the window, and use it as a feature. Let’s implement it in Python:

```python
train_df = pd.read_csv('https://raw.githubusercontent.com/syedjafer/datasets/main/time_series_data_1/Train_SU63ISt.csv')


train_df['Datetime'] = pd.to_datetime(train_df['Datetime'],format='%d-%m-%Y %H:%M')

train_df['rolling_mean'] = train_df['Count'].rolling(window=7).mean()
train_df = train_df[['Datetime', 'rolling_mean', 'Count']]
train_df.head(10)
```

![Screenshot from 2022-02-23 09-08-58.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645587561751/Ki6uZVsO-.png)

Similarly, you can consider the sum, min, max value, etc. (for the selected window) as a feature and try it out on your own machine.

Recency in an important factor in a time series. Values closer to the current date would hold more information.

Thus, we can use a weighted average, such that higher weights are given to the most recent observations. Mathematically, weighted average at time t for the past 7 values would be:

> w_avg = w1*(t-1) + w2*(t-2) + .  .  .  .  + w7*(t-7)

where, w1>w2>w3> .  .   . . >w7.

### Expanding Window Feature

In the case of a rolling window, the size of the window is constant while the window slides as we move forward in time. Hence, we consider only the most recent values and ignore the past values. The idea behind the expanding window feature is that it takes all the past values into account. 

Here’s a gif that explains how our expanding window function works:


![output_B4KHcT.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1645587712483/huoqm0Y87.gif)

As you can see, with every step, the size of the window increases by one as it takes into account every new value in the series. This can be implemented easily in Python by using the expanding() function. Let’s code this using the same data:


![Screenshot from 2022-02-23 09-12-47.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645587788984/QEOrX4Crv.png)

### Domain-Specific Features

Having a good understanding of the problem statement, clarity of the end objective and knowledge of the available data is essential to engineer domain-specific features for the model.

Want to dive into this more? Let’s take an example.

Below is the data provided by a retailer for a number of stores and products. Our task is to forecast the future demands for the products. We can come up with various features, like taking a lag or averaging the past values, among other things.

But hold on. Let me ask you a question – would it be the right way to build lag features from lag(1) to lag(7) throughout the data?


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645587855934/D4d5rJ90h.png)


Certainly not! There are different stores and products, and the demand for each store and product would be significantly different. In this case, we can create lag features considering the store-product combination. Moreover, if we have knowledge about the products and the trends in the market, we would be able to generate more accurate (and fewer) features.

Not only this, having a good understanding about the domain and data would help us in selecting the lag value and the window size. Additionally, based on your domain knowledge, you would be able to pull external data that adds more value to the model.

Here’s what I mean – are the sales affected by the weather on the day? Will the sales increase/decrease on a national holiday? If yes, then you can use external datasets and include the list of holidays as a feature.

### Validation set creation technique for Time Series

All the feature engineering techniques we have discussed can be used to convert a time series problem into a supervised machine learning problem.

Once we have that, we can easily go ahead with machine learning algorithms like linear regression and random forest. But there is one important step that you should know before you jump to the model building process – creating a validation set for time series.

For the traditional machine learning problems, we randomly select subsets of data for the validation and test sets. But in these cases, each data point is dependent on its past values. If we randomly shuffle the data, we might be training on future data and predicting the past values!

It is important that we carefully build a validation set when working on a time series problem, without destroying the sequential order within the data.

Let’s create a validation set for our problem. But first, we must check the duration for which we have the data:

```python
train_df['Datetime'].min(), train_df['Datetime'].max(), (train_df['Datetime'].max() -train_df['Datetime'].min())
```

![Screenshot from 2022-02-23 09-16-56.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645588029743/jmp3HaPPi.png)

We have data for almost 761 days. Let’s save 100 days for validation and use the remaining for training:


![Screenshot from 2022-02-23 09-19-06.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645588164681/cwFcIHXvg.png)

### Conclusion

Time Series is often considered a difficult topic to master. That’s understandable because there are a lot of moving parts when we’re working with the date and time components. But once you have a hang of the basic concepts and are able to perform feature engineering, you’ll be gliding through your projects in no time.

In this article, we discussed some simple techniques that you can use to work with time series data. Using these feature engineering techniques, we can convert any time series problem into a supervised learning problem and build regression models.

