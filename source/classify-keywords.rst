Classify Keywords
=================

.. contents:: Classify Keywords Calls
    :local:

POST classify/keywords
----------------------

Classify a list of keywords and return mapped eContext categories.

*There is a hard limit of 1,000 keywords per call.*

Resource URL
^^^^^^^^^^^^
:api_url:`classify/keywords`

Parameters
^^^^^^^^^^

.. csv-table::
    :header: "Parameter","Type","Description"
    :widths: 25, 20, 100

    "keywords (*required*)", "array", "A list of keyword strings to process (no more than 1,000)."
    "classification_type (*optional*)", "integer", "Select the classification method: ``1`` for rule-based, ``2`` for model-based, or ``0`` for a hybrid rule-based + model-based (defaults to ``0``)"
    "ml_threshold (*optional*)", "float", "Specify a confidence threshold for accepting an ML prediction. A lower value increases recall at the expense of precision (defaults to ``0.75``)"
    "flags (*optional*)", "boolean", "Provide :ref:`objects-flags` to help filter out certain content categories including adult, firearms, gambling, etc (defaults to ``false``)"
    "branches (*optional*)", "array", "A set of eContext category ids. Any classification outside the section/s of the hierarchy described by this set will be removed from the response."
    "entities (*optional*)", "boolean", "Perform Named Entity Recognition (NER) on the content submitted (defaults to ``false``)"
    "taxonomy_timestamp (*optional*)", "integer", "A Unix timestamp instructing the classifier to use categories from the eContext Taxonomy that existed at this point in time.  This will allow recently deleted categories to remain and hides newly created categories"
    "dataset_id (*optional*)", "string", "A :ref:`custom-taxonomies` id to use in lieu of the default eContext Taxonomy"
    "add_last_node (*optional*)", "bool", "Include the last category node, or leave at the parent category"
    "classify_limit (*optional*)", "integer", "Limit the number of categories that may be returned per post"
    "classify_timeout (*optional*)", "float", "The number of seconds to spend on a classification task"

Return
^^^^^^

The result set includes a ``results`` key which provides a list of category id
keys and associated data including :ref:`objects-flags`, if requested and found.
The results in this set are in the same order as the keyword list submitted in
the POST call.

Example Request
^^^^^^^^^^^^^^^

POST Request
""""""""""""

.. parsed-literal::

    curl -X POST -u username:password --data-binary @classify-keywords-input.json \\
    --header "Content-type: application/json" \\
    :api_url:`classify/keywords`

The contents of :download:`classify-keywords-input.json <_static/classify-keywords-input.json>`:

.. literalinclude:: _static/classify-keywords-input.json
    :language: json


POST Response
"""""""""""""

.. literalinclude:: _static/classify-keywords-output.json
   :language: json
