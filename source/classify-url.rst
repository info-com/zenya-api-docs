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

Resource URL
^^^^^^^^^^^^
:api_url:`classify/url`

Parameters
^^^^^^^^^^

.. csv-table::
    :header: "Parameter","Type","Description"
    :widths: 25, 20, 100

    "url (*required*)", "string", "A fully qualified URL to be retrieved and classified."
    "classification_type (*optional*)", "integer", "Select the classification method: ``1`` for rule-based, ``2`` for model-based, or ``0`` for a hybrid rule-based + model-based (defaults to ``0``)"
    "ml_threshold (*optional*)", "float", "Specify a confidence threshold for accepting an ML prediction. A lower value increases recall at the expense of precision (defaults to ``0.75``)"
    "cache_skip (*optional*)", "boolean", "Rescrape a URL for HTML content rather than using a possibly cached scrape (defaults to ``false``)"
    "entities (*optional*)", "boolean", "Perform Named Entity Recognition (NER) on the content submitted (defaults to ``false``)"
    "sentiment (*optional*)", "boolean", "Perform sentiment analysis on the content submitted (defaults to ``false``)"
    "min_tags (*optional*)", "integer", "eContext uses a smart parsing library to extract only the most relevant content from a webpage, and ignore areas likely to be less relevant (navigation, footers, etc). However, for some pages this may result in less content extracted than expected. Use this parameter to set a minimum number of HTML tags the smart library must extract; if the result is less than this minimum, eContext will extract content from all HTML tags (eg, a full-page parse)."
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
