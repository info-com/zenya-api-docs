Classify Social
===============

.. contents:: Classify Social Calls
    :local:

POST classify/social
--------------------

Classify a list of social posts and return scored categories and keywords.

In typical usage the ``async`` parameter should be set to ``false``.  The POST call will return a 200 HTTP
Status-Code (:rfc:`2616#section-10.2.1`) as well as the classifications for the input.

If ``async`` is set to ``true``, the POST call will return a 201 HTTP Status-Code (:rfc:`2616#section-10.2.2`)
as well as a ``result_uri`` pointing to the result set. If the result set is not yet completed,
the GET call will return a 202 HTTP Status-Code (:rfc:`2616#section-10.2.3`).  The result set, once completed, will be
available for retrieval for either 2 days or until it is successfully consumed, whichever comes first.

*There is a limit of 1,000 posts per call.*

Resource URL
^^^^^^^^^^^^
:api_url:`classify/social`

Parameters
^^^^^^^^^^

.. csv-table::
    :header: "Parameter","Type","Description"
    :stub-columns: 1
    :widths: 25, 20, 100

    "social (*required*)", "array", "A list (no more than 1,000 items) of strings."
    "async (*optional, but recommended*)", "boolean", "Set to ``false`` to run a blocking call and return results immediately upon completion. Set to ``true`` to run a non-blocking call and retrieve a result set later (defaults to ``true``)"
    "classification_type (*optional*)", "integer", "Select the classification method: ``1`` for rule-based, ``2`` for model-based, or ``0`` for a hybrid rule-based + model-based (defaults to ``1``)"
    "flags (*optional*)", "boolean", "Provide :ref:`objects-flags` to help filter out certain content categories including adult, firearms, gambling, etc (defaults to ``false``)"
    "entities (*optional*)", "boolean", "Perform Named Entity Recognition (NER) on the content submitted (defaults to ``false``)"
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
