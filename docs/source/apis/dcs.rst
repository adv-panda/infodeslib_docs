======================
Dynamic Classifier Selection 
======================

Overall Local Accuracy (OLA) 
------------------------ 

Parameters
----------
        pool_classifiers : list of classifiers (Default = None)
                The generated_pool of classifiers trained for the corresponding
                classification problem. Each base classifiers should support the method
                "predict". If None, then the pool of classifiers is a bagging
                classifier.

        k : int (Default = 7)
                Number of neighbors used to estimate the competence of the base
                classifiers. 
        
------------------------------------------------------------------------------- 

Local Class Accuracy (LCA)
------------------------ 

.. automodule:: infodeslib.dcs.lca 

.. autoclass:: infodeslib.dcs.lca.LCA
    :members: __init__

------------------------------------------------------------------------------- 

Modified Local Accuracy (MLA)
------------------------ 

.. automodule:: infodeslib.dcs.mla 

.. autoclass:: infodeslib.dcs.mla.MLA
    :members: __init__

------------------------------------------------------------------------------- 

Modified Rank (Rank)
------------------------ 

.. automodule:: infodeslib.dcs.rank 

.. autoclass:: infodeslib.dcs.rank.Rank
    :members: __init__

------------------------------------------------------------------------------- 
