## Project - Predicting Salary with Simple Linear Regression

### Prerequisite
1. Linear Regression from Scratch with Gradient Descent [Click Here](https://learnml.hashnode.dev/linear-regression-with-gradient-descent-scratch)
2. Project Folder Structure [Click Here](https://learnml.hashnode.dev/folder-structure-for-machine-learning-projects)

### Links

1. Blog Link - [Linear Regression](https://learnml.hashnode.dev/linear-regression-with-gradient-descent-scratch)
2. Notebook Link - [Colab Notebook](https://colab.research.google.com/drive/1Hs0n6ApzcePHvDZd7VgPCTABxBR1EiMb?usp=sharing)
3. Dataset Link - [Data Source](https://github.com/syedjafer/project-simple_linear_regression/blob/main/data/Salary_Data.csv)
4. Github Repo - [Repo Link](https://github.com/syedjafer/project-simple_linear_regression)

### Introduction
In this article we will be implementing what we learned in [Linear Regression from Scratch with Gradient Descent](https://learnml.hashnode.dev/linear-regression-with-gradient-descent-scratch). We will be creating a simple Flask API and Angular frontend with Plotly to Visualize the usage. The final screen will look like below, 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645067890474/kH2F8bzMe.png)

### Dataset
In this project we will be using salary_data with two columns, Experience and Salary. 

Source : https://github.com/syedjafer/project-simple_linear_regression/blob/main/data/Salary_Data.csv

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645068019117/dULGTx5xS.png)

After plotting the dataset will look like, 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645068197664/Do0wfQF0S.png)

From the above plot, we are sure that all assumptions discussed in [linear regression]((https://learnml.hashnode.dev/linear-regression-with-gradient-descent-scratch)) is satisfied.

### Notebook

Applied the data visualization, outlier detection and created a model in this [colab](https://colab.research.google.com/drive/1Hs0n6ApzcePHvDZd7VgPCTABxBR1EiMb?usp=sharing) notebook.  


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1645068412490/qYfYwhG__.png)

### Flask API

Created a simple flask api with endpoints. one to give the entire dataset and the other to predict the salary for the given experience.

```python
#!flask/bin/python
from crypt import methods
from flask import Flask, jsonify, request
from flask_cors import CORS, cross_origin
import pandas as pd

# Model Loader
import statsmodels.api as sm

DATA_FILE = '../data/Salary_Data.csv'
MODEL_FILE = '../model/linear_regression.pickle'

app = Flask(__name__)
cors = CORS(app)
app.config['CORS_HEADERS'] = 'Content-Type'

@app.route('/datasets', methods=['GET'])
@cross_origin()
def get_dataset():
    df = pd.read_csv(DATA_FILE)
    x = df['YearsExperience'].tolist()
    y = df['Salary'].tolist()
    return jsonify({'x':x, 'y':y})

@app.route('/get-predicted-value', methods=['POST'])
@cross_origin()
def get_predicted_value():
    model = sm.load(MODEL_FILE)
    _intercept, _slope = model.params
    print(request.json, request.args, request.form, request.values, request.data)
    salary = (request.json['value']*_slope) + _intercept
    return jsonify({
        'y': salary
    })

if __name__ == '__main__':
    app.run(debug=True)

```

### Angular Component
Simple angular component to show plotly graph with a small form to trigger the prediction api. 

```typescript
import { Component, OnInit } from '@angular/core';
import { RestApiService } from 'src/services/api.service';

@Component({
  selector: 'app-lr',
  templateUrl: './lr.component.html',
  styleUrls: ['./lr.component.css']
})
export class LrComponent implements OnInit {
  x_val_line: any = [];
  y_val_line: any = [];

  x_scatter: any = [];
  y_scatter: any = [];

  experience :any;

  public graph: any = {
    data: [
        { x: this.x_scatter, y: this.y_scatter, type: 'scatter',  marker: {color: 'red'} },
        { x: this.x_val_line, y: this.y_val_line, type: 'line' },
    ],
    layout: {width: 800, height: 400, title: 'A Fancy Plot'}
};

  constructor(public restApi: RestApiService) { }

  ngOnInit(): void {
    this.restApi.getData().subscribe({
      next: data => {
          this.x_val_line = data.x;
          this.y_val_line = data.y;
          console.log("Data ", data);
          this.graph = {
            data: [
                { x: this.x_scatter, y: this.y_scatter, type: 'scatter',  marker: {color: 'red'} },
                { x: this.x_val_line, y: this.y_val_line, type: 'line' },
            ],
            layout: {width: 800, height: 400, title: 'Experince vs Salary'}
        };
      },
      error: error => {
          
          console.error('There was an error!', error);
      }
  })
  }

  getExperience(){
console.log(this.experience);
    this.restApi.getPredictedValue(this.experience).subscribe({
      next: data =>{
        this.x_scatter = [this.experience];
        this.y_scatter = [data.y];
        this.graph = {
          data: [
              { x: this.x_scatter, y: this.y_scatter, type: 'scatter',  marker: {color: 'red'} },
              { x: this.x_val_line, y: this.y_val_line, type: 'line' },
          ],
          layout: {width: 800, height: 400, title: 'Experince vs Salary'}
      };

      },
      error: error => {
          
        console.error('There was an error!', error);
    }
    })
  }


}

```

### Demo

<iframe width="700" height="400" src="https://www.youtube.com/embed/GXqXQi-RMUU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### Installation

#### For API
Step 1: Create an environment, 
```bash
python -m venv <environment_name>
```

Step 2: Install the packages
```bash
source <environment_name>/bin/activate
pip install -r api/requirements.txt
```

Step 3: Run the Flask API
```bash
cd api
python app.py
```

#### For Angular

Step 1: Move to frontend/linear-regression folder
```bash
cd frontend/linear-regression
```

Step 2: Install the node modules,
```bash
npm install
```

Step 3: Run the project, 
```bash
ng serve
```

### Github

Repository Link : https://github.com/syedjafer/project-simple_linear_regression