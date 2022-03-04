## The Missing Value Ratio

### Introduction
Feature Selection plays a key role in reducing the dimensions of any dataset. There are various benefits of dimensionality reduction including reduced computational/training time of a dataset, lesser dimensions leading to better visualization, etc. And Missing Value Ratio is one of the basic feature selection techniques. 

### What is the Missing Value Ratio and how do we calculate it?

In a dataset, there might be the presence of values in different columns. We can try to fill those missing values using the techniques mentioned here. Else, we need to find the missing value ratio of the particular column and if the percentage of the missing value is greater than the threshold then we need to eliminate the column from the dataset. 

Formula to calculate the missing value ratio, 


![formula to calculate missing value ratio - missing value ratio - dimensionality reduction](https://cdn.hashnode.com/res/hashnode/image/upload/v1645765096204/F6TDa7Rbp.png)

### Explanation

Let us consider our titanic dataset, 

```python
data = pd.read_csv("https://raw.githubusercontent.com/syedjafer/datasets/main/titanic.csv")
data.head()
```


![titanic dataset head - missing value ratio - dimensionality reduction ](https://cdn.hashnode.com/res/hashnode/image/upload/v1645765158947/68-taWCu6.png)

In the above image, we are able to see some **NaN** (Not A Number) values present in the **Cabin** column. Now let us find out the missing value's percentage on each column. 

```python
data.isnull().sum()/len(data)*100
```


![titanic dataset null - missing value ratio - dimensionality reduction](https://cdn.hashnode.com/res/hashnode/image/upload/v1645765286821/c6qRx1EtO.png)


We can see that column **cabin** has the highest missing value percentage of 77. Now let's apply the threshold level (subjected to the project) of 40% and filter it. So that, if any column is having a higher percentage than the threshold level it would be eliminated. 

```python
missing_val_percentage = data.isnull().sum()/len(data)*100
filtered_columns = [ ]
threshold_level = 40
for index, column in enumerate(data.columns):
    if missing_val_percentage[index] <= threshold_level:
        filtered_columns.append(column)

filtered_columns
```

![missing value ration - dimensionality reduction - threshold level](https://cdn.hashnode.com/res/hashnode/image/upload/v1645765484840/gkYp6qwpT.png)

And then we can create a new dataset from the filtered columns like below. 

```python
new_data = data[filtered_columns]
```

![titanic dataset filtration - missing value ratio - dimensionality reduction](https://cdn.hashnode.com/res/hashnode/image/upload/v1645765562637/lELNHXaiz.png)

### When to use this?
If the dataset has too many missing values, we use this approach to reduce the number of variables. We can drop the variables having a large number of missing values in them

### Notebook Link : 
Please find this [colab notebook](https://colab.research.google.com/drive/1h7FbL7xrHXyhNY_n5nlNjU-4nRcHhS2t?usp=sharing), where you can try to execute all the python code experimented here. 

### Conclusion

In this article, we have covered one of the most common feature selection techniques Missing Value Ratio, which will also be helpful in reducing the dimensions of the features.
 