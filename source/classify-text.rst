Classify Text
=============

.. contents:: Classify Text Calls
    :local:

POST classify/text
------------------

Classify the submitted plain text and return scored categories and keywords. This call creates a new
result resource that will be available for either 2 days or until being successfully consumed in a 
GET call.

The response from the POST call should include a 201 HTTP Status-Code (:rfc:`2616#section-10.2.2`) 
as well as a "result_uri" pointing to the result set. If the result set is not yet completed, the 
GET call will return a 202 HTTP Status-Code (:rfc:`2616#section-10.2.3`).

An optional ``async`` parameter can be used to create a blocking call 
when set to ``false``.  In this case, the results from the POST will be the same
as the results that would have been retrieved from the GET on a completed result
set.

Resource URL
^^^^^^^^^^^^
:api_url:`classify/text`

Parameters
^^^^^^^^^^

.. csv-table::
    :header: "Parameter","Type","Description"
    :stub-columns: 1
    :widths: 25, 20, 100
    
    "text (*required*)", "string", "A plaintext string to be classified."
    "async (*optional*)", "boolean", "Optionally run a blocking call and retrieve results immediately (defaults to *true*)"

Example Request
^^^^^^^^^^^^^^^

POST Request
""""""""""""

.. parsed-literal::
    
    curl -X POST -u username:password --data-binary @classify-text-input.json \\
    --header "Content-type: application/json" \\
    :api_url:`classify/text`

The contents of :download:`classify-text-input.json <_static/classify-text-input.json>`:

.. literalinclude:: _static/classify-text-input.json
    :language: json

POST Response
"""""""""""""

.. code-block:: json
    
    {
	"econtext": {
	    "classify": {
		"type": "text",
		"result_id": "7c9587da07731a185369271b773cf9d3449084b1c19edabf0ea5999953168a25",
		"result_uri": "https://api.econtext.com/v2/classify/text/7c9587da07731a185369271b773cf9d3449084b1c19edabf0ea5999953168a25",
		"status": "working"
	    },
	    "signature": {
		"resource": "POST /classify/:type/:result_id",
		"status": "201 Created - successful",
		"client_ip": "127.0.0.1"
	    }
	}
    }

GET classify/text/:result_id
----------------------------

Retrieve a plain text classification result set. If the classification result set is not yet complete,
this call will return a 202 HTTP Status-Code (:rfc:`2616#section-10.2.3`). The result set should be 
ready shortly at which point this call will return the appropriate 200 HTTP Status-Code
(:rfc:`2616#section-10.2.1`). After consumption, this resource will be removed.

The result set includes "scored_categories" and "scored_keywords" as well as a "categories" 
dictionary. The "scored_keywords" object contains a list of high-value phrases that eContext 
was able to pull out of the submitted text as well as associated scores for each. The "scored_categories" object contains a list of "category_id" and "score" objects where the 
"category_id" corresponds to an item in the "categories" dictionary. Higher values indicate 
a higher score.

Resource URL
^^^^^^^^^^^^
:api_url:`classify/text/:result_id`

Parameters
^^^^^^^^^^

.. csv-table::
    :header: "Parameter","Type","Description"
    :stub-columns: 1
    :widths: 25, 20, 100
    
    "result_id (*required*)", "string", "A result_id string obtained as a result in the response from the ``POST``."

Example Request
^^^^^^^^^^^^^^^

GET Request
"""""""""""

.. parsed-literal::

    curl -X GET -u username:password \\
    :api_url:`classify/html/7c9587da07731a185369271b773cf9d3449084b1c19edabf0ea5999953168a25`

GET Response
""""""""""""

.. literalinclude:: _static/classify-text-output.json
   :language: json