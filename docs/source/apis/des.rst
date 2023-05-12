======================
Dynamic Ensemble Selection 
======================

Dynamic Ensemble Selection Performance (DESP)
------------------------ 

.. code-block:: python  

  class deslib.dcs.desp.DESP(self, pool_classifiers=None, feature_subsets=None, k=7, DFP=False, knn_metric='minkowski',
                             dimensionality_reduction=False, reduction_technique='pca', n_components = 5, cbr_features = None, 
                             colors=None) 
                        
The DES-P technique selects all base classifiers whose classification performance in the region of competence exceeds that of a random classifier (RC). The RC's performance is calculated as RC = 1/L, where L is the number of classes in the problem. If none of the base classifiers meet the criteria, the entire pool of classifiers is used for classification.

**Parameters**

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

k-Nearest Oracles Eliminate (KNORA-E) 
------------------------ 

.. code-block:: python  

  class deslib.dcs.knorae.KNORAE(self, pool_classifiers=None, feature_subsets=None, k=7, DFP=False, knn_metric='minkowski',
                                 dimensionality_reduction=False, reduction_technique='pca', n_components = 5, cbr_features = None, 
                                 colors=None) 
                        
The KNORA-E method looks for a local Oracle, which is a base classifier that correctly classifies all samples in the region of competence of the test sample. All classifiers with perfect performance in the region of competence are chosen as local Oracles. If no classifier achieves perfect accuracy, the competence region's size is reduced by removing the farthest neighbor, and the classifiers' performance is re-evaluated. The outputs of the selected ensemble of classifiers are combined using a majority voting scheme. If no base classifier is selected, the entire pool is used for classification.

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

k-Nearest Oracles Union (KNORA-U)
------------------------ 

.. code-block:: python  

  class deslib.dcs.knorau.KNORAU(self, pool_classifiers=None, feature_subsets=None, k=7, DFP=False, knn_metric='minkowski',
                                 dimensionality_reduction=False, reduction_technique='pca', n_components = 5, cbr_features = None, 
                                 colors=None) 
                        
The KNORA-U method chooses all classifiers that correctly classify at least one sample in the region of competence of the test sample. Each chosen classifier is assigned a number of votes equivalent to the number of samples in the region of competence that it correctly predicts. The votes from all base classifiers are combined to determine the final ensemble decision.

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

k-Nearest Oracles Eliminate Weighted (KNORAE-W) 
------------------------ 

.. code-block:: python  

  class deslib.dcs.knorae.KNORAE_W(self, pool_classifiers=None, feature_subsets=None, k=7, DFP=False, knn_metric='minkowski',
                                   dimensionality_reduction=False, reduction_technique='pca', n_components = 5, cbr_features = None, 
                                   colors=None) 
                        
This scheme is the same as KNORA-ELIMINATE, but each vote is weighted by the Euclidean distance between the neighbor pattern xj and the test pattern X. 

Parameters 

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
