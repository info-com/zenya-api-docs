Classify URL
=============

.. contents:: Classify URL Calls
    :local:

POST classify/url
------------------

Classify the submitted URL and return scored categories and keywords. This call creates a new
result resource that will be available for either 2 days or until being successfully consumed in a
GET call.

The Classify URL call honors the robots.txt file from the site of the specified URL.  In the case
that the specified URL is blocked by robots.txt_, a 400 error will be returned to the user with an
error message indicating same.

The Classify URL call also requires that the URL being examined must adhere to a
content-type and content-length standard.  The ``Content-type`` header for the
URL must be one of the following: ``text/plain``, ``text/html``, ``text/xhtml``,
``application/xhtml+xml``, ``text/xml``, ``application/xml``.  The ``Content-length``
header must present a value less than or equal to 256000 bytes.

The response from the POST call should include a 201 HTTP Status-Code (:rfc:`2616#section-10.2.2`)
as well as a "result_uri" pointing to the result set. If the result set is not yet completed, 
the GET call will return a 202 HTTP Status-Code (:rfc:`2616#section-10.2.3`).

An optional ``async`` parameter can be used to create a blocking call 
when set to ``false``.  In this case, the results from the POST will be the same
as the results that would have been retrieved from the GET on a completed result
set.

Resource URL
^^^^^^^^^^^^
:api_url:`classify/url`

Parameters
^^^^^^^^^^

.. csv-table::
    :header: "Parameter","Type","Description"
    :stub-columns: 1
    :widths: 25, 20, 100
    
    "url (*required*)", "string", "URL to be retrieved and classified."
    "async (*optional*)", "boolean", "Optionally run a blocking call and retrieve results immediately (defaults to *true*)"

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
        "url":"http://topics.info.com/Parks_4679"
    }


POST Response
"""""""""""""

.. code-block:: json
    
    {
        "econtext": {
            "classify": {
                "type": "url",
                "result_id": "1476f360a941cf711170493c103e23d373426273df9b79a54faeba81139e9d54",
                "result_uri": "https://api.econtext.com/v2/classify/url/1476f360a941cf711170493c103e23d373426273df9b79a54faeba81139e9d54",
                "status": "working"
            },
            "signature": {
                "resource": "POST /classify/:type/:result_id",
                "status": "201 Created - successful",
                "client_ip": "127.0.0.1"
            }
        }
    }

GET classify/url/:result_id
----------------------------

Retrieve an URL classification result set. If the result set is not yet complete, this 
call will return a 202 HTTP Status-Code (:rfc:`2616#section-10.2.3`). The result set should 
be ready shortly at which point this call will return the appropriate 200 HTTP Status-Code
(:rfc:`2616#section-10.2.1`). After consumption, this resource will be removed.


The result set includes "scored_categories" and "scored_keywords" as well as a "categories"
dictionary. The "scored_keywords" object contains a list of high-value phrases that eContext
was able to pull out of the submitted text as well as associated scores for each. The "scored_categories" object contains a list of "category_id" and "score" objects where the "category_id"
corresponds to an item in the "categories" dictionary. Higher values indicate a higher score.

Resource URL
^^^^^^^^^^^^
:api_url:`classify/url/:result_id`

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
    :api_url:`classify/url/1476f360a941cf711170493c103e23d373426273df9b79a54faeba81139e9d54`

GET Response
""""""""""""

.. literalinclude:: _static/classify-url-output.json
   :language: json

.. _robots.txt: http://www.robotstxt.org/robotstxt.html
