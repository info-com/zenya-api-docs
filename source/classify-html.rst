Classify HTML
=============

.. contents:: Classify HTML Calls
    :local:

POST classify/html
------------------

Classify the submitted HTML and return scored categories and keywords.

In typical usage the ``async`` parameter should be set to ``false``.  The POST call will return a 200 HTTP
Status-Code (:rfc:`2616#section-10.2.1`) as well as the classification for the input.

If ``async`` is set to ``true``, the POST call will return a 201 HTTP Status-Code (:rfc:`2616#section-10.2.2`)
as well as a ``result_uri`` pointing to the result set. If the result set is not yet completed,
the GET call will return a 202 HTTP Status-Code (:rfc:`2616#section-10.2.3`).  The result set, once completed, will be
available for retrieval for either 2 days or until it is successfully consumed, whichever comes first.


Resource URL
^^^^^^^^^^^^
:api_url:`classify/html`

Parameters
^^^^^^^^^^

.. csv-table::
    :header: "Parameter","Type","Description"
    :stub-columns: 1
    :widths: 25, 20, 100

    "html (*required*)", "string", "HTML content to be classified."
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

    curl -X POST -u username:password --data-binary @classify-html-input.json \\
    --header "Content-type: application/json" \\
    :api_url:`classify/html`

The contents of :download:`classify-html-input.json <_static/classify-html-input.json>`:

.. code-block:: json

    {
        "async": false,
        "html": "<!DOCTYPE html><html><head><title>Microsoft Stores offer $100 Xbox One discount
        if you trade in a PS3</title></head><body><h1>Microsoft Stores offer $100 Xbox One discount
        if you trade in a PS3</h1><p>Currently there’s one advantage the PS4 has over the Xbox One
        that Microsoft can do little about: the price difference.</p><p>Sure, they
        could cut the price of the Xbox One by $100 and match the PS4 at $399, but then Microsoft
        would be making a big loss on every console sold. However, they have come up with a way to
        offer you an Xbox One for $399.</p><p>From now until March 2, Microsoft Stores will offer
        you $100 of store credit if you trade in a PS3, Xbox 360 S, or Xbox 360 E. Of course,
        there’s a number of terms and conditions in order to get that $100. The console must be in
        fully working order and have its original accessories including the power supply. You will
        also only be guaranteed to get $100 for your old machine if you agree to purchase an Xbox
        One at the same time.</p></body></html>"
    }


POST Response
"""""""""""""

.. literalinclude:: _static/classify-html-output.json
   :language: json
