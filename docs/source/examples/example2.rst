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
```

Selecting one instance  
--------------------------  

.. code-block:: python    

  index = 18
  query = X_test.iloc[[index]]

  ## Make plot=True 
  knorau.predict(query, plot=True)

