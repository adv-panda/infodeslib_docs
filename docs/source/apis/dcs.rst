======================
Dynamic Classifier Selection 
======================

Dynamic Classifier Selection (DCS) is a technique used in machine learning ensembles, where the most appropriate classifier or a subset of classifiers is selected for each new sample to be classified. This is done dynamically, based on the characteristics of the input data, with the goal of improving the overall classification performance of the ensemble. DCS algorithms typically use measures of classifier competence, which are estimates of the accuracy of each classifier for the given input data, to decide which classifier or subset of classifiers to use. 


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

.. code-block:: python  

  class deslib.dcs.lca.LCA(self, pool_classifiers=None, feature_subsets=None, k=7, DFP=False, knn_metric='minkowski',
                           dimensionality_reduction=False, reduction_technique='pca', n_components = 5, cbr_features = None, 
                           colors=None) 
                        
The LCA technique measures the competency of each classifier by evaluating its accuracy in predicting the label of a test sample with respect to a particular output class. The classifier's competence level is estimated by the percentage of local training samples, assigned to that output class, which it correctly predicts. The most competent classifier is then chosen to predict the label of the test sample. If more than one classifier has the same level of competence, the first evaluated one is selected. The selection methodology can be adjusted by modifying the hyper-parameter selection_method.

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

Modified Local Accuracy (MLA)
------------------------ 

.. code-block:: python  

  class deslib.dcs.mla.MLA(self, pool_classifiers=None, feature_subsets=None, k=7, DFP=False, knn_metric='minkowski',
                           dimensionality_reduction=False, reduction_technique='pca', n_components = 5, cbr_features = None, 
                           colors=None) 
                        
The MLA approach is similar to LCA but takes into account the distance between the test sample and each pattern in the region of competence to weight the output of each base classifier. The classifier with the highest competence level is selected to predict the label of the test sample, and if multiple classifiers have the same competence level, the first evaluated one is chosen. The selection methodology can be modified by adjusting the hyper-parameter selection_method.

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

Modified Rank (Rank)
------------------------ 

.. code-block:: python  

  class deslib.dcs.rank.Rank(self, pool_classifiers=None, feature_subsets=None, k=7, DFP=False, knn_metric='minkowski',
                            dimensionality_reduction=False, reduction_technique='pca', n_components = 5, cbr_features = None, 
                            colors=None) 
                        
The Modified Classifier Rank method evaluates the competency level of each classifier and selects the most competent one to predict the label of a test sample. Competence is measured by counting the number of correctly classified samples starting from the closest neighbor of the test sample. The classifier with the highest number of correctly classified samples is deemed the most competent and chosen to predict the label. If multiple classifiers have the same level of competence, the first evaluated one is selected. The selection methodology can be adjusted by modifying the hyper-parameter selection_method.

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
