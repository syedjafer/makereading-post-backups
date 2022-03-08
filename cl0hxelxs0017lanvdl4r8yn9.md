## Machine Learning Pipeline and Feature Engineering

### Introduction
In this article, we are gonna see about the Machine Learning Pipeline and where exactly feature engineering will take place. Included with processes carried over on feature engineering. Before diving into feature engineering, let’s take a moment to take a look at the overall machine learning pipeline. This will help us get situated in the larger picture of the application.

### Machine Learning Pipeline

More and more businesses are collecting data with an eye toward Machine Learning (ML). But while most ML algorithms can only interpret tidy datasets, real-world data is usually messy and unstructured. Cortex bridges this gap through a multi-step framework that automatically organizes and cleans raw data transforms it into a machine-readable form, trains a model, and generates predictions — all continuously. Collectively, we refer to these steps as a Machine Learning Pipeline.


![Machine Learning Pipeline - learn ml from scratch - ml algorithms](https://cdn.hashnode.com/res/hashnode/image/upload/v1646726312343/hiYDjSNVw.png)

 Machine Learning Pipeline Steps,
1. Data Preprocessing
2. Data Cleaning
3. Feature Engineering
4. Model Selection
5. Prediction Generation - Insights

Let's see steps 1, 2, 4, and 5 in brief, 

#### Data Preprocessing 
The first step in any pipeline is data preprocessing. In this step, raw data is gathered and merged into a single organized framework. Data preprocessing is a Data Mining technique that involves transferring raw data into an understandable format. Real-world data is usually incomplete, inconsistent, and lacks certain behaviors or trends, most likely to contain many inaccuracies. The process of getting usable data for a Machine Learning algorithm follows steps such as Feature Extraction and Scaling, Feature Selection, Dimensionality reduction, and sampling. The product of Data Pre-processing is the final dataset used for training the model and testing purposes.

#### Data Cleaning
Next, this data flows to the cleaning step. To make sure the data paints a consistent picture that your pipeline can learn from. Data cleaning is the process of fixing or removing incorrect, corrupted, incorrectly formatted, duplicate, or incomplete data within a dataset. When combining multiple data sources, there are many opportunities for data to be duplicated or mislabeled.

#### Model Selection
Model selection is the process of choosing one among many candidate models for a predictive modeling problem. There may be many competing concerns when performing model selection beyond model performance, such as complexity, maintainability, and available resources. The two main classes of model selection techniques are probabilistic measures and resampling methods. we will see them in upcoming articles 

#### Prediction Generation
The prediction step of your pipeline comprises two processes:

Building features for all objects (e.g. users) that will get a prediction, and Feeding those features through the pipeline’s winning model. Together, these two actions result in a prediction being made for each object.

Below are a few notes that are important to understand about the prediction step.

During model selection, your pipeline learned a relationship between a certain set of features and a particular goal. So, the features that are built during the prediction step will match those selected during the feature engineering step. 

With this step, the end-user will be analyzing the insights. 

### Feature Engineering

Feature engineering is the process of using domain knowledge of the data to create features or variables to use in machine learning. 
A feature is a numeric representation of an aspect of raw data. Features sit between data and models in the machine learning pipeline. Feature engineering is the act of extracting features from raw data and transforming them into formats that are suitable for the machine learning model. 

It is a crucial step in the machine learning pipeline because the right features can ease the difficulty of modeling, and therefore enable the pipeline to output results of higher quality. Practitioners agree that the vast majority of time in building a machine learning pipeline is spent on feature engineering and data cleaning.

Yet, despite its importance, the topic is rarely discussed on its own. Perhaps this is because the right features can only be defined in the context of both the model and the data; since data and models are so diverse, it’s difficult to generalize the practice of feature engineering across projects.

Feature engineering is not just an ad hoc practice. There are deeper principles at work to make a better model. In this section, we will see about various feature engineering processes that we follow, 

1. Types of variables 
2. Variable characteristics 
3. Variable transformation 
4. Treating categorical variables 
5. Feature scaling 
6. Discretization or binning 
7. Missing value imputation 
8. Outlier treatment 

#### Types of Variables
- Numerical variable: can be discrete or continuous. The discrete variable takes only whole numbers. The continuous variable takes any value within some range. 

For example, total rainfall measured in inches is a numerical value, heart rate is a numerical value, the number of cheeseburgers consumed in an hour is a numerical value.

- Categorical variable: can be ordinal or nominal. The ordinal variable takes categories that can be meaningfully ordered. The nominal variable takes labels that have no intrinsic order. 

For example, hair color is a categorical value or hometown is a categorical variable. Species, treatment type, and gender are all categorical variables.

- Mixed variables: can have number/labels in different observations or number/labels in the same observation. 

#### Variable characteristics
- **Cardinality**: the number of different labels is known as cardinality. As cardinality increases the chances of over-fitting also increase. 

-** Skewed distribution**: One of the tails is longer than the other tail. For skewed distribution, the median is better than the mean for imputation. 

- **Magnitude**: impact the regression coefficients. Features with bigger magnitudes dominate over features with smaller magnitudes. Feature scaling helps to bring all the features in the same range. 

- **Missing data**: occurs when no data is stored for a certain observation in the variable. Can have a significant impact on the model. 

- **Outliers**: is a data point that is significantly different from the remaining data. Depending upon the context, outliers either deserve special attention or should be completely ignored. 

#### Variable transformation

If the distribution of the variable is skewed then transformations are applied to make the distribution closer to normal distribution. 

1. Logarithmic (X>0)
2. Exponential (X>>large; may lead to errors)
3. Reciprocal (X<>0)
4. Box-Cox (X>0)
5. Yeo-Johnson 

#### Treating categorical variables
Machine learning algorithms work only with numerical variables. Hence, replacing the categories with numerical representations is done, so that machine learning models can use these variables. 

1. **One hot encoding**: Consists of encoding each categorical variable with a set of Boolean variables K-1 dummies are created. One hot encoding of top categories only considers the most frequent categories. 
2. **Ordinal encoding**: Consists of replacing the categories by digits from 0 to 9. Numbers are assigned arbitrarily. This encoding method allows for quick benchmarking of machine learning models. 
Count of frequent encoding: Categories are replaced by the percentage of observations shown against that category. Captures representation of each label.
3. **Target guided encoding**: Helps to get a monotonic relationship between the variable and target. Categories are replaced with integers from 1 to K where k is the number of distinct categories in the variable, but the number is informed by the mean of the target for each category. Probability ratio encoding is where each category is replaced by the odds ratio or weight of evidence. 
4. **Mean encoding**: Replacing the category by an average of the target value for that category. 
5. **Rare label encoding:** Rare labels are those that appear only in a tiny proportion of the observations in the dataset. These labels are grouped into a single label. 
6. **Binary encoding**: Binary code is used to encode the meaning of the variable. However, it lacks human-readable meaning. 

#### Feature scaling
Feature scaling is the method used to normalize the range of values. This is done to bring all the variables at the same scale. 

1. **Standardization** [Z = (x-u)/s]: It preserves the shape of the variable with mean = 0 and standard deviation = 1. It preserves outliers.
2. **Mean normalization** [Z = (x-mean) / (max-min)]: Rescales the range of the variable with mean = 0. It may alter the shape of the variable. 
3. **Min max scalar** [Z = (x-min) / (max-min)]: Rescales the range of the variable and returns only positive values. It preserves outliers. 
4. **Maximum absolute scalar** [Z = x / max|x|]: Rescales the range of the variable. Mean is not centered to 0 and variance is not scaled. 
5. **Scaling to Median and IQR** [Z = (x – Median) / (Q3 – Q1)]: Median is centered to zero and it handles outliers. 

#### Discretization or binning 
Discretization is the process of transforming continuous variables into discrete variables by a set of continuous intervals. It is also called binning. 

1. **Equal width**: Divides the variable into K bins of the same width. It does not improve value spread and we observe the same distribution. 
2. **Equal frequency**: Divides the variable into K bins with the same number of observations. Interval boundaries correspond to quartiles. It handles outliers and improves the spread of the variable. 
3. **K means**: Applying K-means clustering to the continuous variable. Divides the variable into clusters according to the centroids. 
4. **Decision trees**: Consists of using decision trees to identify the optimal bins. It creates discrete variables as well as a monotonic relationship. It handles outliers. 
> On monotonic relationship: Re-order the intervals so that we get a monotonic relationship with the target. Monotonic relationship improves the performance of machine learning models and create shallower trees. 

#### Missing data imputation ([link to a detailed blog](https://blog.learnml.xyz/tactics-to-handle-missing-values))
Act of replacing the missing data with statistical estimates of missing values. The goal is to produce a whole dataset that can be used to train machine learning models. 

1. **Complete Case Analysis**: The list-wise deletion or discarding observations where values in any of the variables are missing. We analyze only those observations for which information is available for all the variables. Suitable for numerical and categorical variables. Should be used when data are missing at random and not more than 5% of data is missing. 
2. **Mean or Median Imputation**: consists of replacing all occurrences of missing values within a variable with either mean or median. Suitable for the numerical variables. If the variable is normally distributed then use mean if the distribution is skewed then use the median. Should be used when data are missing at random and missing observations mostly look like the majority of the data. Mean or median should be calculated only on the training set. The value should be used to replace missing values in both train and test datasets. This is to avoid over-fitting. 
3. **Arbitrary Value Imputation**: Consists of replacing a missing value with an arbitrary value. For categorical – ‘missing’ and for numerical – 999. This should be used when data is not missing at random. Works well with tree-based algorithms but not with linear regression or logistic regression. 
4. **Frequent Category Imputation**: Mode imputation consists of replacing all occurrences of missing values within a variable with mode. Suitable for categorical variables. Should be used when data are missing at random and the missing observations most likely look like the majority of observations. 
5. **Missing Category Imputation**: Consists of treating missing data as an additional label or category. This is a widely used method for categorical variables. 
6.** Random Sample Imputation**: Consists in taking random observations from the pool of available observations of the variable and using it to fill the missing values. Suitable for both numerical and categorical. 
7. **Missing indicator**: Additional binary variable is added which indicates whether the data was missing for observation or not. Suitable for numerical and categorical variables. It should be used together with other methods that assume data is missing at random (mean, median, or mode imputation and random sample imputation). If data is missing at random then it is captured by mean or median and if data is not missing at random then it is captured by the binary variable. If more than 5% of data is missing then it is advised to add a missing indicator. 
8. **KNN Imputation**: Determines missing data points as the weighted average of the values of its K nearest neighbors. KNN is trained on other variables, the K nearest neighbors are determined and a weighted average is taken to impute the missing value. Suitable when a small percentage of the data is missing.
9. **MICE**: A series of models whereby each variable is modeled conditional upon other variables in the data. Each incomplete variable is imputed by a separate model. 
10. **Miss Forest**: MICE is implemented using Random Forest. Works well with mixed data types and can handle non-linear relationships. 

#### Outlier treatment 
Outlier is a data point that is significantly different from the remaining data. Outliers may impact the performance of linear models, however, their impact is minimal on tree-based algorithms. Outliers can be identified using Gaussian distribution (u -/+ 3*s), Interquartile range (Q3 – Q1), and
 Quartiles (1 percentile and 99 percentile). 

1. Trimming: Remove outliers from the dataset. However, it can remove a large proportion of data.
2. Capping: No data is removed. However, it distorts variable distribution. 
3. Missing data: The outliers are treated as missing data.
4. Discretization: The outliers are put into lower and upper bins. 
5. Arbitrary capping: Domain knowledge of the variable is required to cap the min and max 

### Conclusion

In this article, we have seen a brief introduction to the machine learning pipeline and a nice explanation of feature engineering. In the upcoming articles, we will pick a use case and dive deeply into feature engineering. 
