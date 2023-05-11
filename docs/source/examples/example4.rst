====================
Evaluating the given test sample 
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

   knorau.get_rareness_score(n_clusters=10, query = query)


.. image:: https://raw.githubusercontent.com/adv-panda/infodeslib_docs/main/docs/source/images/rareness_1.PNG


.. image:: https://raw.githubusercontent.com/adv-panda/infodeslib_docs/main/docs/source/images/rareness_2.PNG

