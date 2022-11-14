# Project - IMDB Sentiment Classification for 50K Reviews

### Resources 
1. Notebook - https://www.kaggle.com/syedjaferk/imdb-sentiment-classification-using-naive-bayes
2. Github - https://github.com/syedjafer/Naive-Bayes-Sentiment-Classification
3. Heroku Endpoint - https://classification-imdb-naivebayes.herokuapp.com/docs#/default/get_prediction_prediction_post
4. Dataset - https://www.kaggle.com/datasets/lakshmi25npathi/imdb-dataset-of-50k-movie-reviews

### Introduction

In this project we will be creating a classifier model based on the IMDB movie reviews. And will be converting the models to end point using FastApi and deploying it to heroku. This will be a very breif flow of the project. Please tryout with different values in the endpoint. 

### Data cleaning and Preprocessing

In the dataset, currently we have some <br> tags and some slash / .

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656895082988/cxa2pnJw_.png align="left")

We can remove html tags using BeautifulSoup, punctuations using regex and stopwords using nltk. After doing the cleaning steps, we will be lemmatizing each word in the review. 
Please checkout the [notebook](https://www.kaggle.com/code/syedjaferk/imdb-sentiment-classification-using-naive-bayes) for more reference. 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656895286896/6BaBxjx-K.png align="left")

### Model Building

After preprocessing, we need to convert the textual data to vectors. For the Train dataset we will use CountVectorizer and for the target we will be using Label Encoder. Then we will feed the data into Multinomial Naive Bayes from sklearn and using grid search, find the optimal values for the parameters. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656897200943/BgSwk12IT.png align="left")

### Model Saving 

Now, we need to save the model and the vectorizer using joblib. So that in the FastApi we can include these files and convert the user given input to a required format needed by our Model. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656897289652/Bm6j0gu0w.png align="left")

### Fast API 

```
from typing import Union
from fastapi import FastAPI
from joblib import load
from pydantic import BaseModel


app = FastAPI()
vector = load('vectors.joblib')
model = load('classifier.joblib')

class get_review(BaseModel):
    review: str


@app.get("/")
def read_root():
    return {"Hello": "World"}


@app.post("/prediction")
def get_prediction(gr: get_review):
    text = [gr.review]
    vec = vector.transform(text)
    prediction = model.predict(vec)
    prediction = int(prediction)
    print(prediction)
    if prediction == 1:
        prediction = 'positive'
    else:
        prediction = 'negative'
    return {"sentence": gr.review, "prediction": prediction}

```

### Deployment 

This application is now deployed to heroku on https://classification-imdb-naivebayes.herokuapp.com/docs. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656897527897/R-Z8kwdBZ.png align="left")


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656897548710/7qjPlhPo3.png align="left")


 
