# Similarity Learning based Clustering
**(Work in Progress)**
The main objective is to build one program to automatically train similarity learning based metrics with entities and apply clustering algorithms with specified metrics to predict clusters.


![SimilarityLearnClusters](https://user-images.githubusercontent.com/61123728/122810863-d7f83b00-d29d-11eb-96ca-acc2ccf352f2.png)

# Prerequisites
-  The project is developed in a Python environment. 
   - Get the Anaconda Navigator for Python 3.7.3 and up: https://www.anaconda.com/download/
- Create virtual environment to download required libraries. 
   - If you want to create your python's virtual environment, please install and configure virtualenv. 
     You could install virtualenv and create virtual environment `virtualenv venv`. To activate your virtual environment on Windows,  `C:\Users\SomeUser\python_training> venv\Scripts\activate.bat`.
     For more information, please check following [link1](https://docs.python-guide.org/dev/virtualenvs/) and [link2](https://programwithus.com/learn-to-code/Pip-and-virtualenv-on-Windows/).
   - If you want to use Anaconda Navigator to create your conda environment. Please refer the following [link](https://uoa-eresearch.github.io/eresearch-cookbook/recipe/2014/11/20/conda/).
- The project requires number of installed libraries such as scikit-learn, xgboost, and pytorch. 
   - In the virtual environment you created, install necessary libraries listed in the file <a href="./requirements.txt">requirements.txt</a> `pip install --user -r requirements.txt`<br/>


**Program Arguments**

There are 4 arguments that can be specified by users. It allows users to apply the program to acheive different objectives. 
   - **username**: your own user name. It will be used for logging and saving results with input name. The default username is anonymous.
   - **datasetname**: the full name of the dataset that will be used to train models or predict clusters. The pipeline is designed for raw data.
   - **mode**: user can specify mode as training, predict_raw, predict_clean or exploratory to achieve different objective.
   - **select**: user can specify what group_name (one categorical variable) which is used to prevent pairwise comparion explosion. If "select" is True, user can input multiple ID or randomly select two ID. If "select" is False, all categories in group_name will be considered.


To see more details, you could run Command Prompt in the directory with `python pipeline.py --help`. 


**Run Command with Arguments**
User can input different commands for different purposes. 
   - Train models for all possible group_name.
   - Explore input data for all possible group_name.
   - Predict cluster ID for raw txt data.
   - Predict cluster ID for clean data.


## Project Organization
------------
    ├── README.md              <-- The top-level README for developers using this project.
    │
    │
    ├── datasets               <-- One dataset contains  entities and related group_name.
    │
    │
    ├── requirements.txt       <-- The requirements file for reproducing the analysis environment.
    │            
    │
    ├── src                   
    │   │
    │   ├── training.py        <-- Main pipeline scrips to create serilized models and optimal epsilons.
    │   │
    │   ├── data               <-- Scripts to shuffle and make entities based on group_name.
    │   │
    │   ├── features           <-- Scripts to turn raw entities into pairwise comparisons for modeling.
    │   │
    │   ├── modeling           <-- Scripts to train models and predict scores of pairwise comparisons.               
    │   │
    │   └── clustering         <-- Scripts to cluster with distance matrix and find optimal epsilon based on performance.          
    │
    │
    ├── config.yaml            <-- Configuration parameters used for training and predictive pipelines.
    │
    │
    ├── pipeline.py            <-- Scripts of one program process entities for exploration, training and prediction.
    │
    │
    ├── results                <-- The folder contains saved models, feature importances, optimal epsilons, clustering perforamces, etc. 
--------

