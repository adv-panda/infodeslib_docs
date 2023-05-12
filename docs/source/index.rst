=======================================
Infodeslib
=======================================

.. toctree::
   :maxdepth: 1
   :hidden:
   :caption: Getting Started

   Introduction <quickstart/introduction>
   Installation <quickstart/usage>

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: APIs

   Dynamic Classifier Selection <apis/dcs>
   Dynamic Ensemble Selection <apis/des>
   
.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: Examples

   Basic Usage <examples/example1>
   Explainability <examples/example2>
   Pool Evaluation <examples/example3>
   Test instance Evaluation <examples/example4>

========================

**Late Fusion based Dynamic Ensemble Learning library.**

Infodeslib is open source library focusing the implementation of the state-of-the-art techniques for dynamic classifier and ensemble selection with late fusion setting.
This project is under active development. Contributions are welcomed through its GitHub page: https://github.com/adv-panda/infodeslib 

.. image:: images/logo_small.png

:doc:`Install</quickstart/usage>`

:doc:`Quick Start</quickstart/introduction>`


**Example** 

Here we present an example of the KNORA-U techniques using a random forest to generate the pool of classifiers: 

.. code-block:: python 
   
   from infodeslib.des.knorau import KNORAU  
   
   pool_classifiers = [classifier1, ..., classifierN]
   # feature_set1 is a list of columns 
   feature_sets = [feature_set1, ..., feature_setN] 

   # Initialize the DS model
   knorau = KNORAU(pool_classifiers, feature_sets)

   # Fit the dynamic selection model
   knorau.fit(X_dsel, y_dsel) 

   # Predict new examples
   knorau.predict(X_test, plot=True)

   # Check performance (based on accuracy)
   knorau.score(X_test, y_test) 
