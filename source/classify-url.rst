Classify URL
=============

.. contents:: Classify URL Calls
    :local:

POST classify/url
------------------

Classify the submitted URL and return scored categories and keywords.

The Classify URL call honors the robots.txt file from the site of the specified
URL.  In the case that the specified URL is blocked by robots.txt_, a 403 error
will be returned to the user with an error message indicating same.

The Classify URL call also requires that the URL being examined must adhere to a
content-type and content-length standard.  The ``Content-type`` header for the
URL must be one of the following: ``text/plain``, ``text/html``, ``text/xhtml``,
``application/xhtml+xml``, ``text/xml``, ``application/xml``.  The
``Content-length`` header must present a value less than or equal to 256000
bytes.

In typical usage the ``async`` parameter should be set to ``false``.  The POST call will return a 200 HTTP
Status-Code (:rfc:`2616#section-10.2.1`) as well as the classification for the input.

If ``async`` is set to ``true``, the POST call will return a 201 HTTP Status-Code (:rfc:`2616#section-10.2.2`)
as well as a ``result_uri`` pointing to the result set. If the result set is not yet completed,
the GET call will return a 202 HTTP Status-Code (:rfc:`2616#section-10.2.3`).  The result set, once completed, will be
available for retrieval for either 2 days or until it is successfully consumed, whichever comes first.

Resource URL
^^^^^^^^^^^^
:api_url:`classify/url`

Parameters
^^^^^^^^^^

.. csv-table::
    :header: "Parameter","Type","Description"
    :stub-columns: 1
    :widths: 25, 20, 100

    "url (*required*)", "string", "A fully qualified URL to be retrieved and classified."
    "async (*optional, but recommended*)", "boolean", "Set to ``false`` to run a blocking call and return results immediately upon completion. Set to ``true`` to run a non-blocking call and retrieve a result set later (defaults to ``true``)"
    "classification_type (*optional*)", "integer", "Select the classification method: ``1`` for rule-based, ``2`` for model-based, or ``0`` for a rule-based with model-based as a fallback (defaults to ``0``)"
    "entities (*optional*)", "boolean", "Perform Named Entity Recognition (NER) on the content submitted (defaults to ``false``)"
    "taxonomy_timestamp (*optional*)", "integer", "A Unix timestamp instructing the classifier to use categories from the eContext Taxonomy that existed at this point in time.  This will allow recently deleted categories to remain and hides newly created categories"
    "dataset_id (*optional*)", "string", "A :ref:`custom-taxonomies` id to use in lieu of the default eContext Taxonomy"

Return
^^^^^^

The result set includes ``scored_categories`` and ``scored_keywords`` as well as a ``categories`` dictionary. The
``scored_keywords`` object contains a list of high-value phrases that eContext was able to pull out of the submitted text
as well as associated scores for each. The ``scored_categories`` object contains a list of ``category_id`` and ``score``
objects where the ``category_id`` corresponds to an item in the ``categories`` dictionary. Higher values indicate a higher
score.

Example Request
^^^^^^^^^^^^^^^

POST Request
""""""""""""

.. parsed-literal::

    curl -X POST -u username:password --data-binary @classify-url-input.json \\
    --header "Content-type: application/json" \\
    :api_url:`classify/url`

The contents of :download:`classify-url-input.json <_static/classify-url-input.json>`:

.. code-block:: json

    {
        "async": false,
        "url":"http://topics.info.com/Parks_4679"
    }


POST Response
"""""""""""""

.. literalinclude:: _static/classify-url-output.json
   :language: json

.. _robots.txt: http://www.robotstxt.org/robotstxt.html
