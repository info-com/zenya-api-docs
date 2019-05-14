Natural Langauge Processing
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
