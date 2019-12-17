Best Practices
===============

Rule-Based vs. Model-Based Classification
-----------------------------------------

eContext offers a unique combination of curated, rule-based classification and machine learned, neural network model-based classification. Users can request classification from one or the other, or use a hybrid ML + rule-based system.

Classification results from the rule-based system can come from any one of eContext's 500,000+ topic categories, across its 20+ levels of the hierarchy. Classification from the model-based system can come from one of approximately 2,000 topic categories at the first 3 levels of depth in the hierarchy.

Users can select the method they wish to use with the ``classification_type`` parameter, and the values below:

.. csv-table::
    :header: "Value", "Description"

    "0","Uses a hybrid ML + rule-based methodology (default for classify/text, classify/html, classify/url, and classify/keywords)"
    "1","Rule-based method, only (default for classify/social)"
    "2","Mode-based method, only"

When machine learning models are being utilized, by default, eContext filters out predictions that fall below a certain probability threshold. This threshold can be adjusted by passing in an ``ml_threshold`` parameter with a float value between 0.0 and 1.0.

.. code-block:: json

   {
     "classification_type": 2,
     "ml_threshold": 0.70,
     "social": [
       "han and luke"
     ]
   }


Fixing Classification Results to a Point in Time
------------------------------------------------

eContext is continually expanding and improving its classification abilities, adding & removing categories in its hierarchy and altering rules that guide classification. New data is available in the eContext service every 24 hours (00:00 UTC).

However, there may be cases where users do not want the classification to change over the course of a long-running job or while processing batches of content across several days.

To ensure this consistency, users may pass in the ``taxonomy_timestamp`` parameter with their request. This parameter accepts a unix timestamp which will instruct the engine to ignore any changes made to the classification system after this date. Any timestamp within the past three weeks is considered valid.  See the below example:

.. code-block:: json

   {
     "async":false,
     "taxonomy_timestamp":1514764800,
     "social":[
       "happy new year!"
     ]
   }
