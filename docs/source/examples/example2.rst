====================
Explainability Example
====================

Following the code from Basic Usage. 


Initializing 
--------------------------  
.. code-block:: python   

  import shap 
  from infodeslib.des.knorau import KNORAU  
   
  colors = {0: 'red', 1: 'green'}  

  knorau = KNORAU(model_pool, feature_sets, k=7, colors=colors)
  knorau.fit(X_dsel, y_dsel) 


Selecting one instance  
--------------------------  

.. code-block:: python    

  index = 18
  query = X_test.iloc[[index]]

  ## Make plot=True 
  knorau.predict(query, plot=True)

Estimating Region of competence (RoC) in validation dataset 

.. image:: https://raw.githubusercontent.com/adv-panda/infodeslib_docs/main/docs/source/images/xai_1.PNG

Detailed information about the selected samples in RoC: 

.. image:: https://raw.githubusercontent.com/adv-panda/infodeslib_docs/main/docs/source/images/xai_2.PNG

The contribution of each selected classifier on the final decision: 

.. image:: https://raw.githubusercontent.com/adv-panda/infodeslib_docs/main/docs/source/images/xai_3.PNG 

The local feature importance of each selected classifier: 

.. image:: https://raw.githubusercontent.com/adv-panda/infodeslib_docs/main/docs/source/images/xai_4.PNG 
