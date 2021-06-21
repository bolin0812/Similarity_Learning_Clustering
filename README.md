# Similarity Learning based Clustering (Work in Progress)
The main objective is to build one program to automatically train similarity learning based metrics and apply clustering algorithms with trained metrics to predict clusters.


![SimilarityLearnClusters](https://user-images.githubusercontent.com/61123728/122810863-d7f83b00-d29d-11eb-96ca-acc2ccf352f2.png)


# Prerequisites
-  The project is developed in a Python environment. 
    - Get the Anaconda Navigator for Python 3.7.3 and up: https://www.anaconda.com/download/
- Create virtual environment to download required libraries. 
    - If you want to create your python's virtual environment, please install and configure virtualenv. You could install virtualenv and create virtual environment `virtualenv venv`. 
    - To activate your virtual environment on Windows, run `folder\venv\Scripts\activate.bat`.For more information, please check following [link1](https://docs.python-guide.org/dev/virtualenvs/) and [link2](https://programwithus.com/learn-to-code/Pip-and-virtualenv-on-Windows/).
   - If you want to use Anaconda Navigator to create your conda environment. Please refer the following [link](https://uoa-eresearch.github.io/eresearch-cookbook/recipe/2014/11/20/conda/).
- The project requires number of installed libraries such as scikit-learn and xgboost. 
   - In the virtual environment you created, install necessary libraries listed in the file <a href="./requirements.txt">requirements.txt</a> by inputting `pip install --user -r requirements.txt`<br/>


## Training Models and Optimal Epsilons

Afer installing required python packages, make sure you are in the directory (`folder\python_training\`) that contains main pipeline `reconcile_pipeline.py`. 

To run the program with default arguments, you could simple run `python pipeline.py` in Command Prompt Interface.

**Program Arguments**
There are 4 arguments that can be specified by users. It allows users to apply the program for different objectives. 
   - **username**: your own user name. It will be used for saving results with input user name. The default username is anonymous.
   - **datasetname**: the full name of transactions dataset. In phase 1, we experimented with clean CSV file. In phase 2, the pipeline is designed for raw TXT data from PROD.
   - **mode**: user can specify mode as training, predict_raw, predict_clean or exploratory to achieve different objective.
   - **select**: user can specify what Matcher ID AI will be processed. If select is True, user can input multiple ID or randomly select two ID. If select is False, all Matcher ID AI will be considered.

To see more details, you could run Command Prompt in the directory with `python pipeline.py --help`. 


**Run Command with Arguments**
User can input different commands to achieve different objectives. 
   - Train models for all possible Matcher ID AI, you can input following command:
      `python pipeline.py --username=User_Name --datasetname=data.txt --mode=training --select=False`
   - Explore transactions data for all possible Matcher ID AI, you can input following command:
      `python pipeline.py --username=User_Name --datasetname=data.txt --mode=exploratory --select=False`
   - Predict cluster ID for raw transactions data from PROD:
      `python pipeline.py --username=User_Name --datasetname=data.txt --mode=predict_raw --select=False`
   - Predict cluster ID for raw transactions data from PROD:
      `python pipeline.py --username=User_Name --datasetname=data.txt --mode=predict_clean --select=False`


## Project Organization
------------
    ├── README.md              <-- The top-level README for developers using this project.
    │
    │
    ├── datasets               <-- Transactions dataset that contains Process and Activity.
    │
    │
    ├── requirements.txt       <-- The requirements file for reproducing the analysis environment.
    │            
    │
    ├── src                   
    │   │
    │   ├── training.py        <-- Main pipeline scrips to create serilized models and optimal epsilons.
    │   │
    │   ├── data               <-- Scripts to shuffle and make datasets based on Type-Process-Activity.
    │   │   ├── data_preprocess.py
    │   │   ├── data_loader.py
    │   │   ├── data_process.py
    │   │   ├── data_shuffle_select.py
    │   │   └── train_valid_test.py
    │   │
    │   ├── features           <-- Scripts to turn raw data into pairwise comparisons for modeling.
    │   │   └── pair_compare.py
    │   │
    │   ├── modeling           <-- Scripts to train models and predict scores of pairwise comparisons.               
    │   │   ├── train_model.py
    │   │   ├── model_predict.py
    │   │   └── model_evaluate.py
    │   │
    │   └── clustering         <-- Scripts to cluster with distance matrix and find optimal epsilon based on performance.          
    │       ├── custom_dbscan.py
    │       ├── cluster_evaluate.py
    │       └── optimal_eps.py
    │
    │
    ├── config.yaml            <-- Configuration parameters used for training and predictive pipelines.
    │
    │
    ├── pipeline.py  <-- Scripts of one program that process transactions for exploration, training and prediction.
    │
    │
    ├── results                <-- The folder contains saved models, feature importances, optimal epsilons, clustering perforamces, etc. 
--------

