====================
Introduction
====================

Infodeslib is open source library focusing the implementation of the state-of-the-art techniques for dynamic classifier and ensemble selection with late fusion setting. This project is under active development.

There has been a notable increase in research focusing on dynamic selection (DS) techniques within the field of ensemble learning. This leads to the development of various techniques for ensembling of multiple classifiers for a specific instance or set of instances during the prediction phase. Despite this progress, the designing and developing of DS approaches with late fusion settings and their explainability remain unexplored. This work proposes an open-source Python library, Infodeslib, that aims to address this gap. The library provides an implementation of several DS techniques, including four dynamic classifier selections and seven dynamic ensemble selection techniques, all of which are integrated with late data fusion settings and novel explainability features. Infodeslib offers flexibility and customization options, making it a versatile tool for various complex applications that require the fusion of multimodal data and various explainability features. 

Features & Uses
====================

Infodeslib has the following features:
----------------------------------------------

⭐️ **Support for late fusion on DS technques**. Infodeslib supports late fusion of multiple modalities on DS techniques. 

⭐️ **Support for diverse DS technques**. Infodeslib supports 4 dynamic classifier selection and 7 dynamic ensemble selection techniques. 

⭐️ **Explainable AI**. Infodeslib provides deep and suitable XAI for dynamic selection techniques: Case-Based Reasoning, deep-based classifiers contributions, and local feature importance.



Infodeslib has a wide range of uses, including:
-------------------------------------------------------------

✅ Providing various handy **diversity metrics**; 

✅ Providing various handy **new metrics** for evaluation pool of classifiers: coverage score, pool diversity, average accuracy of pool; 

✅ New **hyperparameters** to DS techniques: dimentionality reduction, customizible distance metrics for estimating Region of competence. 

✅ Providing various handy **metric** for evaluating test sample: rareness score; 


Dynamic Classifier Selection 
======================

Dynamic Classifier Selection (DCS) is a technique used in machine learning ensembles, where the most appropriate classifier or a subset of classifiers is selected for each new sample to be classified. This is done dynamically, based on the characteristics of the input data, with the goal of improving the overall classification performance of the ensemble. DCS algorithms typically use measures of classifier competence, which are estimates of the accuracy of each classifier for the given input data, to decide which classifier or subset of classifiers to use. 

.. image:: https://raw.githubusercontent.com/adv-panda/infodeslib_docs/main/docs/source/images/dcs_diagram.png


Dynamic Ensemble Selection 
======================

Dynamic Ensemble Selection (DES) is a method for improving the performance of ensemble learning by dynamically selecting a subset of base classifiers that are most competent in classifying a given test sample. The selection is based on the performance of each classifier in the region of competence, which is determined using k-NN algorithm. The DES approach aims to balance the accuracy and diversity of the selected ensemble of classifiers to improve the overall prediction performance. 

.. image:: https://raw.githubusercontent.com/adv-panda/infodeslib_docs/main/docs/source/images/des_diagram.png
