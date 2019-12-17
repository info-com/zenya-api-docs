Classify Social
===============

.. contents:: Classify Social Calls
    :local:

POST classify/social
--------------------

Classify a list of social posts and return scored categories and keywords.

*There is a hard limit of 1,000 posts per call.*

Resource URL
^^^^^^^^^^^^
:api_url:`classify/social`

Parameters
^^^^^^^^^^

.. csv-table::
    :header: "Parameter","Type","Description"
    :widths: 25, 20, 100

    "social (*required*)", "array", "A list (no more than 1,000 items) of strings."
    "classification_type (*optional*)", "integer", "Select the classification method: ``1`` for rule-based, ``2`` for model-based, or ``0`` for a hybrid rule-based + model-based (defaults to ``1``)"
    "ml_threshold (*optional*)", "float", "Specify a confidence threshold for accepting an ML prediction. A lower value increases recall at the expense of precision (defaults to ``0.75``)"
    "flags (*optional*)", "boolean", "Provide :ref:`objects-flags` to help filter out certain content categories including adult, firearms, gambling, etc (defaults to ``false``)"
    "entities (*optional*)", "boolean", "Perform Named Entity Recognition (NER) on the content submitted (defaults to ``false``)"
    "sentiment (*optional*)", "boolean", "Perform sentiment analysis on the content submitted (defaults to ``false``)"
    "taxonomy_timestamp (*optional*)", "integer", "A Unix timestamp instructing the classifier to use categories from the eContext Taxonomy that existed at this point in time.  This will allow recently deleted categories to remain and hides newly created categories"
    "dataset_id (*optional*)", "string", "A :ref:`custom-taxonomies` id to use in lieu of the default eContext Taxonomy"

Return
^^^^^^

The result set includes ``scored_categories`` and ``scored_keywords`` as well as a ``categories`` dictionary. The
``scored_keywords`` object contains a list of high-value phrases that eContext was able to pull out of the submitted
text as well as associated scores for each. The ``scored_categories`` object contains a list of ``category_id`` and
``score`` objects where the ``category_id`` corresponds to an item in the ``categories`` dictionary. Higher values
indicate a higher score.

Example Request
^^^^^^^^^^^^^^^

POST Request
""""""""""""

.. parsed-literal::

    curl -X POST -u username:password --data-binary @classify-social-input.json \\
    --header "Content-type: application/json" \\
    :api_url:`classify/social`

The contents of :download:`classify-social-input.json <_static/classify-social-input.json>`:

.. literalinclude:: _static/classify-social-input.json
    :language: json

POST Response
"""""""""""""

.. literalinclude:: _static/classify-social-output.json
   :language: json
