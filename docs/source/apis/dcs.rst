======================
Dynamic Classifier Selection 
======================

Dynamic Classifier Selection (DCS) is a technique used in machine learning ensembles, where the most appropriate classifier or a subset of classifiers is selected for each new sample to be classified. This is done dynamically, based on the characteristics of the input data, with the goal of improving the overall classification performance of the ensemble. DCS algorithms typically use measures of classifier competence, which are estimates of the accuracy of each classifier for the given input data, to decide which classifier or subset of classifiers to use. 

.. image:: https://raw.githubusercontent.com/adv-panda/infodeslib_docs/main/docs/source/images/dcs_diagram.png 

Overall Local Accuracy (OLA) 
------------------------ 
.. code-block:: python  

  class deslib.dcs.ola.OLA(self, pool_classifiers=None, feature_subsets=None, k=7, DFP=False, knn_metric='minkowski',
                           dimensionality_reduction=False, reduction_technique='pca', n_components = 5, cbr_features = None, 
                           colors=None) 
                        
The OLA technique determines the competency of each classifier by measuring its accuracy in predicting labels within the area of competence around a given test sample. It then chooses the most competent classifier to predict the label of the sample. If multiple classifiers have the same level of competence, the one evaluated first is selected. The method for selecting the classifier can be changed by adjusting the hyper-parameter selection_method. 

Parameters
----------
        pool_classifiers : list of classifiers (Default = None)
                The generated_pool of classifiers trained for the corresponding
                classification problem. Each base classifiers should support the method
                "predict". If None, then the pool of classifiers is a bagging
                classifier.
        
        feature_subsets : list of feature sets (Default = None)
                Each feature set is a list of features (str) and assigned to each classifier in the pool.  

        k : int (Default = 7)
                Number of neighbors used to estimate the competence of the base
                classifiers. 
        
        DFP : Boolean (Default = False)
                Determines if the dynamic frienemy pruning is applied.   
                
        knn_metric: str or callable {'minkowski', 'cosine', 'manhattan', 'euclidean'}  (Default = 'minkowski') 
                The metric used by the k-NN classifier to estimate distances. 
        
        dimensionality_reduction : boolean (Default = False)  
                Determines if dimention reduction is applied or not. 
        
        reduction_technique : str or callable {'pca', 'kernel_pca'} (Default = 'pca') 
                A technique utilized for dimension reduction. 
        
        n_components : int (Default = 5)  
                Number of components to keep after applying dimension reduction.  
        
        cbr_features : list of features (Default = None) 
                A list of features to show for Cased-based reasoning XAI. 
        
        colors : dict (Default = None)  
                A dictionary of assigning colors for each class  
        
            
        
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
