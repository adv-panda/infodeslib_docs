========================
Basic Usage
========================


Initializing libraries
--------------------------
.. code-block:: python 

   import warnings
   warnings.filterwarnings('ignore') 

   import pandas as pd 
   from sklearn.datasets import load_breast_cancer
   from sklearn.model_selection import train_test_split

   from sklearn.svm import SVC 
   from sklearn.ensemble import RandomForestClassifier 
   from sklearn.neighbors import KNeighborsClassifier 

   from sklearn.metrics import accuracy_score 
   
   
Initializing dataset
--------------------------

We use open dataset: Breast Cancer 

.. code-block:: python 

   data = load_breast_cancer()
   df = pd.DataFrame(data.data, columns = data.feature_names)
   df['target'] = data.target 
   
   
Split dataset 
-------------------------- 

Split the dataset into training, validation for DES (DSEL) and testing: 

.. code-block:: python  

   X = df.drop(['target'], axis=1) 
   y = df.target 

   X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.30, random_state=42)
   X_pool, X_dsel, y_pool, y_dsel   = train_test_split(X_train, y_train, test_size=0.30, random_state=42) 
   

Models and Feature sets Generation  
-------------------------- 

model1 = SVC(probability=True, random_state=42)
model2 = RandomForestClassifier(random_state=42) 
model3 = KNeighborsClassifier()

.. code-block:: python  

   feature_set1 = data.feature_names[:10] 
   feature_set2 = data.feature_names[10:20]
   feature_set3 = data.feature_names[20:]

   model_pool = [model1, 
                 model2, 
                 model3]

   feature_sets = [feature_set1, 
                   feature_set2, 
                   feature_set3] 
                   
                          
Train the models (pool) 
--------------------------   

.. code-block:: python   

   for i in range(len(model_pool)): 
       model_pool[i].fit(X_pool[feature_sets[i]], y_pool)

       acc = round(model_pool[i].score(X_dsel[feature_sets[i]], y_dsel), 3) 
       print("[DSEL] Model {} acc: {}".format(i, acc)) 

       acc = round(model_pool[i].score(X_test[feature_sets[i]], y_test), 3)  
       print("[Test] Model {} acc: {}".format(i, acc))  
       

Usage of our library 
--------------------------  

.. code-block:: python   

   import shap 
   from infodeslib.des.knorau import KNORAU 

   # initializing 
   knorau = KNORAU(model_pool, feature_sets, k=7)
   knorau.fit(X_dsel, y_dsel)
   
   
Testing
-------------------------- 

.. code-block:: python   

   preds =  knorau.predict(X_test)  

   acc = round(accuracy_score(y_test, preds), 3) 
   print("[Test] acc: {}".format(acc))
