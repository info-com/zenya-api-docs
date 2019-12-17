Classify HTML
=============

.. contents:: Classify HTML Calls
    :local:

POST classify/html
------------------

Classify the submitted HTML and return scored categories and keywords.

Resource URL
^^^^^^^^^^^^
:api_url:`classify/html`

Parameters
^^^^^^^^^^

.. csv-table::
    :header: "Parameter","Type","Description"
    :widths: 25, 20, 100

    "html (*required*)", "string", "HTML content to be classified."
    "classification_type (*optional*)", "integer", "Select the classification method: ``1`` for rule-based, ``2`` for model-based, or ``0`` for a hybrid rule-based + model-based (defaults to ``0``)"
    "ml_threshold (*optional*)", "float", "Specify a confidence threshold for accepting an ML prediction. A lower value increases recall at the expense of precision (defaults to ``0.75``)"
    "entities (*optional*)", "boolean", "Perform Named Entity Recognition (NER) on the content submitted (defaults to ``false``)"
    "sentiment (*optional*)", "boolean", "Perform sentiment analysis on the content submitted (defaults to ``false``)"
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
