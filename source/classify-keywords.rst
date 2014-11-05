Classify Keywords
=================

.. contents:: Classify Keywords Calls
    :local:

POST classify/keywords
----------------------

Classify a list of keywords and return mappings and associated Categories. This call creates a
new result resource that will be available for either 2 days or until being successfully consumed in
a GET call.

The response from the POST call should include a 201 HTTP Status-Code (:rfc:`2616#section-10.2.2`) as
well as a "result_uri" pointing to the result set. If the result set is not yet completed, the 
GET call will return a 202 HTTP Status-Code (:rfc:`2616#section-10.2.3`).

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

.. code-block:: json
    
    {
	"econtext": {
	    "classify": {
		"type": "keywords",
		"result_id": "fec8af0a4482fe1c72a114e15dc1affbed3a59bc5a4a39887cc052921b1a3739",
		"result_uri": "https://api.econtext.com/v2/classify/keywords/fec8af0a4482fe1c72a114e15dc1affbed3a59bc5a4a39887cc052921b1a3739",
		"status": "working"
	    },
	    "signature": {
		"resource": "POST /classify/:type/:result_id",
		"status": "201 Created - successful",
		"client_ip": "127.0.0.1"
	    }
	}
    }

GET classify/keywords/:result_id
--------------------------------

Retreive the keyword classification result set. If the result set is not yet complete, this call will
return a 202 HTTP Status-Code (:rfc:`2616#section-10.2.3`). The result set should be ready shortly at which point this call will
return the appropriate 200 HTTP Status-Code (:rfc:`2616#section-10.2.1`). After successful consumption, this resource will
be removed.

The result set includes "mappings" which is a list of category id keys that correspond to the
"categories" dictionary. The mappings are in the same order as the keyword list submitted in the
POST call. A ``null`` value in the id indicates that the keyword is currently unmapped to the eContext
Taxonomy.

Resource URL
^^^^^^^^^^^^
:api_url:`classify/keywords/:result_id`

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
    :api_url:`classify/keywords/fec8af0a4482fe1c72a114e15dc1affbed3a59bc5a4a39887cc052921b1a3739`

GET Response
""""""""""""

.. code-block:: json
    
    {
        "econtext": {
            "classify": {
                "categories": {
                    "2feb560c79517929c435dcfdb299d281": {
                        "id": "2feb560c79517929c435dcfdb299d281",
                        "name": "Chicago Bears",
                        "path": [
                            "Sports",
                            "Team Sports",
                            "Football",
                            "Football Leagues & Teams",
                            "Professional Football Leagues & Teams",
                            "National Football League",
                            "National Football Conference",
                            "National Football Conference - North Division",
                            "Chicago Bears"
                        ]
                    },
                    "319f702352ebab8f89f1576fff712525": {
                        "id": "319f702352ebab8f89f1576fff712525",
                        "name": "Museums",
                        "path": [
                            "Travel",
                            "Sightseeing Tours & Tourist Attractions",
                            "Tourist Attractions",
                            "Arts & Culture Attractions",
                            "Museums"
                        ]
                    }
                },
                "mappings": [
                    null,
                    "2feb560c79517929c435dcfdb299d281",
                    "319f702352ebab8f89f1576fff712525"
                ]
            },
            "signature": {
                "client_ip": "209.41.117.158",
                "resource": "GET /classify/:type/:result_id",
                "status": "200 OK - successful"
            }
        }
    }
