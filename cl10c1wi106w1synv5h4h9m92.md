## Google Colab - Run ML in PaaS

Learning about Machine learning is one of the trending things nowadays. But a lot of people face difficulties, as they don't have a good device, that is powerful enough to train even simpler machine learning models, and there are also a lot of issues, arising due to inefficient systems. 

In order to overcome these issues, Google provided us an Online Notebook kind of thing where we can write, compile, run the code, as well as can enter text ( Markdown - Same as Jupyter Notebook ). 


Link For Google Colab - https://colab.research.google.com/

The big benefit of using Google Colab is the code we run using the google collab notebook, runs on Google's servers, so you don't need a computer powerful enough to run that code. The basic requirements, your device should satisfy, is it should be able to let you easily use any browser, and you are good to go. 

Google Colab has a lot of Data Science, Machine Learning Libraries pre-installed. You can also temporarily install the packages you want ( All Packages will be removed once that session is inactivated for a longer period of time  ).

One of the drawbacks of Google Colab is you can't use it for things, where you design GUIs. But I think, that will not be an issue for most people. 


### How to use Google Colab?

Now let's see how to use Google Colab: 

1. Create a Google Account if you don't have one. 
2. go to **Google Colab** and here you will see information about Google Colab, I suggest you read it once. 
3. On the top right-hand corner, there is an option to sign in. Click on that and login with your Google Account, then you'll see a floating window like this: 



![google colab  - Machine Learning - learnml](https://cdn.hashnode.com/res/hashnode/image/upload/v1647844541854/Kk6yhfi1c.png)


For a first-time user, There is one pre-created notebook called "Welcome to Collaboratory". Now for your use, we will create a new Notebook, so click on **New notebook**.

Now you will see a window like this: 


![Google Colab - Machine Learning - Learnml - New Notebook](https://cdn.hashnode.com/res/hashnode/image/upload/v1647843032147/AI0C7zKiQ.png)

Now rename this notebook by clicking on **Untitled0.ipynb** and giving the name of your choice.

Now, this is your Notebook, where you can execute your Python Code. Now by going to the settings icon in the top right, you can change the theme to Dark mode, if you want. 

Now if you have renamed the file, next time you open Google Colab, with your Account logged in, you will see the option to choose a notebook, and you can choose the notebook of your choice here. 


### How to execute code?

It is the same way how we execute the code in jupyter notebook. 

![Colab code running - Machine Learning - learnml.xyz](https://cdn.hashnode.com/res/hashnode/image/upload/v1647843547754/C7nWMGdTN.png)

It can be executed by entering the code into the cells and then pressing **Shift + Enter** or Clicking on the play button (left of the cell).

Using the same way, you can install packages by typing **!pip install <package-name>** (with the exclamatory at the front) and run that instead of code.

You'll see an option to connect in the top right, that is your runtime, when you execute your code, your runtime starts, which means, you get connected to a Google server. This runtime is connected as long as you don't close that window. 

Also, if you pip install any package, that will be only installed until you get disconnected from runtime. 

If you want to do some work that needs to use a good GPU, you can click on the small arrow besides connect button, to connect to the GPU with runtime, don't use this feature if you don't need it. 

To change your runtime to runtime with GPU:

1. Click on the small arrow beside the **Connect** button.
2. Click on **View Resources**
3. At the bottom, you'll see **Change Runtime Type**, click on that. 
4. In the dropdown menu below Hardware Accelerator, Choose GPU or TPU as you need. 
5. Click **Save**


Selection of runtime from the menu options, 

![runtime GPU/TPU selection](https://cdn.hashnode.com/res/hashnode/image/upload/v1647844642529/Wn__ixYtZ.png)

Selection of the TPU/GPU runtime, 


![TPU GPU selection](https://cdn.hashnode.com/res/hashnode/image/upload/v1647844855235/j_Y3mmkVb.png)

In this way you can do python programming, running python ML Models, and almost all heavy Python-related tasks on Google Colab. 


 

