Classify Keywords
=================

.. contents:: Classify Keywords Calls
    :local:

POST classify/keywords
----------------------

Classify a list of keywords and return mapped eContext categories.

In typical usage the ``async`` parameter should be set to ``false``.  The POST call will return a 200 HTTP
Status-Code (:rfc:`2616#section-10.2.1`) as well as the classifications for the input.

If ``async`` is set to ``true``, the POST call will return a 201 HTTP Status-Code (:rfc:`2616#section-10.2.2`)
as well as a ``result_uri`` pointing to the result set. If the result set is not yet completed,
the GET call will return a 202 HTTP Status-Code (:rfc:`2616#section-10.2.3`).  The result set, once completed, will be
available for retrieval for either 2 days or until it is successfully consumed, whichever comes first.

*There is a limit of 1,000 keywords per call.*

Resource URL
^^^^^^^^^^^^
:api_url:`classify/keywords`

Parameters
^^^^^^^^^^

.. csv-table::
    :header: "Parameter","Type","Description"
    :stub-columns: 1
    :widths: 25, 20, 100

    "keywords (*required*)", "array", "A list of keyword strings to process (no more than 1,000)."
    "async (*optional, but recommended*)", "boolean", "Set to ``false`` to run a blocking call and return results immediately upon completion. Set to ``true`` to run a non-blocking call and retrieve a result set later (defaults to ``true``)"
    "classification_type (*optional*)", "integer", "Select the classification method: ``1`` for rule-based, ``2`` for model-based, or ``0`` for a rule-based with model-based as a fallback (defaults to ``0``)"
    "flags (*optional*)", "boolean", "Provide :ref:`objects-flags` to help filter out certain content categories including adult, firearms, gambling, etc (defaults to ``false``)"
    "branches (*optional*)", "array", "A set of eContext category ids. Any classification outside the section/s of the hierarchy described by this set will be removed from the response."
    "entities (*optional*)", "boolean", "Perform Named Entity Recognition (NER) on the content submitted (defaults to ``false``)"
    "taxonomy_timestamp (*optional*)", "integer", "A Unix timestamp instructing the classifier to use categories from the eContext Taxonomy that existed at this point in time.  This will allow recently deleted categories to remain and hides newly created categories"
    "dataset_id (*optional*)", "string", "A :ref:`custom-taxonomies` id to use in lieu of the default eContext Taxonomy"

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
