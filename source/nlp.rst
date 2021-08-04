Natural Language Processing
===========================

.. contents:: NLP Calls
    :local:

POST nlp/parse
--------------

Performs Part of Speech (POS) tagging, Named Entity Recognition (NER), dependency parsing, tokenization, sentiment analysis, and other core functions of the eContext NLP stack. Connections to this endpoint are currently limited to select users. Please contact us if you're interested in accessing these functions.

Resource URL
^^^^^^^^^^^^

:api_url:`nlp/parse`

Example Request
^^^^^^^^^^^^^^^

POST Request
""""""""""""

.. parsed-literal::

    curl -X POST -u username:password --data-binary @nlp-parse-input.json \\
    --header "Content-type: application/json" \\
    :api_url:`nlp/parse`
    
The contents of :download:`nlp-parse-input.json.json <_static/nlp-parse-input.json>`:

.. literalinclude:: _static/nlp-parse-input.json
    :language: json
    
POST Response
"""""""""""""

.. literalinclude:: _static/nlp-parse-output.json
   :language: json



POST nlp/lid
------------

Identify the language of some text input. Results are returned indicating an ISO 639-1 Code. 

Resource URL
^^^^^^^^^^^^

:api_url:`nlp/lid`

Example Request
^^^^^^^^^^^^^^^

POST Request
""""""""""""
.. parsed-literal::

    curl -X POST -u username:password --data-binary @nlp-lid-input.json \\
    --header "Content-type: application/json" \\
    :api_url:`nlp/lid`
    
The contents of :download:`nlp-lid-input.json <_static/nlp-lid-input.json>`:

.. literalinclude:: _static/nlp-lid-input.json
    :language: json
    
POST Response
"""""""""""""

.. literalinclude:: _static/nlp-lid-output.json
   :language: json



POST nlp/summarize
------------------

Resource URL
^^^^^^^^^^^^

:api_url:`nlp/summarize`

Parameters
^^^^^^^^^^

.. csv-table::
    :header: "Parameter","Type","Description"
    :widths: 25, 20, 100

    "input_type (*required*)", "string", "What type of input is being provided. Available options include ``text``, ``html``, or ``url``"
    "input (*required*)", "string", "The input content to be classified"
    "topn (*optional*)", "int", "The number of categories to focus on when performing summarization. Defaults to ``2`` top verticals present in the input text."
    "category_ids (*optional*)", "[int]", "A list of category_ids to focus on when performing summarization. This will override ``topn``."
    "validate (*optional*)", "bool", "Perform some soft validation on summarized content. This returns high quality summarized content but often at the expense of length. Defaults to ``true``"


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

    curl -X POST -u username:password --data-binary @nlp-summarize-input.json \\
    --header "Content-type: application/json" \\
    :api_url:`nlp/summarize`

The contents of :download:`nlp-summarize-input.json <_static/nlp-summarize-input.json>`:

.. literalinclude:: _static/nlp-summarize-input.json
    :language: json

POST Response
"""""""""""""

.. literalinclude:: _static/nlp-summarize-output.json
   :language: json
