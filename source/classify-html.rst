Classify HTML
=============

.. contents:: Classify HTML Calls
    :local:

POST classify/html
------------------

Classify the submitted HTML and return scored categories and keywords. This call creates a new
result resource that will be available for either 2 days or until being successfully consumed in a
GET call.

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
        "html":"<!DOCTYPE html><html><head><title>Microsoft Stores offer $100 Xbox One discount
        if you trade in a PS3</title></head><body><h1>Microsoft Stores offer $100 Xbox One discount
        if you trade in a PS3</h1><p>Currently there’s one advantage the PS4 has over the Xbox One
        that Microsoft can do little about: the price difference.</p></body></html> Sure, they
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

.. code-block:: json
    
    {
	"econtext": {
	    "classify": {
		"type": "html",
		"result_id": "6cea12b177b8d2005fc2ae5ecf3261075c1301c5204a902112f81344e0ad7200",
		"result_uri": "https://api.econtext.com/v2/classify/html/6cea12b177b8d2005fc2ae5ecf3261075c1301c5204a902112f81344e0ad7200",
		"status": "working"
	    },
	    "signature": {
		"resource": "POST /classify/:type/:result_id",
		"status": "201 Created - successful",
		"client_ip": "127.0.0.1"
	    }
	}
    }

GET classify/html/:result_id
----------------------------

Retrieve an HTML classification result set. If the result set is not yet complete, this 
call will return a 202 HTTP Status-Code (:rfc:`2616#section-10.2.3`). The result set should 
be ready shortly at which point this call will return the appropriate 200 HTTP Status-Code
(:rfc:`2616#section-10.2.1`). After consumption, this resource will be removed.


The result set includes "scored_categories" and "scored_keywords" as well as a "categories"
dictionary. The "scored_keywords" object contains a list of high-value phrases that eContext
was able to pull out of the submitted text as well as associated scores for each. The "scored_categories" object contains a list of "category_id" and "score" objects where the "category_id"
corresponds to an item in the "categories" dictionary. Higher values indicate a higher score.

Resource URL
^^^^^^^^^^^^
:api_url:`classify/html/:result_id`

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
    :api_url:`classify/html/6cea12b177b8d2005fc2ae5ecf3261075c1301c5204a902112f81344e0ad7200`

GET Response
""""""""""""

.. literalinclude:: _static/classify-html-output.json
   :language: json
