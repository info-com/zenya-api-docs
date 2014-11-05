Classify Tweets
===============

.. contents:: Classify Tweets Calls
    :local:

POST classify/tweets
--------------------

Classify a list of tweets and return scored categories and keywords. This call creates a new result
resource that will be available for either 2 days or until being successfully consumed in a GET
call.

The response from the POST call should include a 201 HTTP Status-Code (:rfc:`2616#section-10.2.2`)
as well as a "result_uri" pointing to the result set. If the result set is not yet completed, 
the GET call will return a 202 HTTP Status-Code (:rfc:`2616#section-10.2.3`).

*There is a limit of 1,000 tweets per call.*

Resource URL
^^^^^^^^^^^^
:api_url:`classify/tweets`

Parameters
^^^^^^^^^^

.. csv-table::
    :header: "Parameter","Type","Description"
    :stub-columns: 1
    :widths: 25, 20, 100
    
    "tweets (*required*)", "array", "A list of tweet objects (no more than 1,000)."
..    "sentiment (*optional*)", "boolean", "Include sentiment analysis for each tweet."

Tweet objects are the same as those returned from the Twitter API.  For example:

.. code-block:: json
  
  {
      "statuses": [
	  tweeta,
	  tweetb,
	  tweetc
      ]
  }

In that case, you would take the list of tweets and use them as your value for ``tweets``.  Read the
`Twitter API documentation <https://dev.twitter.com/docs/platform-objects/tweets>`_ for more information about the structure of tweets.  The only *required* information from each tweet object is the ``"text"``
attribute.

Example Request
^^^^^^^^^^^^^^^

POST Request
""""""""""""

.. parsed-literal::
    
    curl -X POST -u username:password --data-binary @classify-tweets-input.json \\
    --header "Content-type: application/json" \\
    :api_url:`classify/tweets`

The contents of :download:`classify-tweets-input.json <_static/classify-tweets-input.json>`:

.. literalinclude:: _static/classify-tweets-input.json
    :language: json

POST Response
"""""""""""""

.. code-block:: json
    
    {
	"econtext": {
	    "classify": {
		"type": "tweets",
		"result_id": "3a0c09171d596d0b2b5cdea8e2c064334de1285130a1fe7a9fa1a113d731de4b",
		"result_uri": "https://api.econtext.com/v2/classify/tweets/3a0c09171d596d0b2b5cdea8e2c064334de1285130a1fe7a9fa1a113d731de4b",
		"status": "working"
	    },
	    "signature": {
		"resource": "POST /classify/:type/:result_id",
		"status": "201 Created - successful",
		"client_ip": "127.0.0.1"
	    }
	}
    }

GET classify/tweets/:result_id
--------------------------------

Retrieve Twitter classification results. If the result set is not yet complete, this 
call will return a 202 HTTP Status-Code (:rfc:`2616#section-10.2.3`). The result set 
should be ready shortly at which point this call will return the appropriate 200 HTTP 
Status-Code (:rfc:`2616#section-10.2.1`). After consumption, this resource will be removed.

The result set includes "scored_categories" and "scored_keywords" as well as a "categories"
dictionary. The "scored_keywords" object contains a list of high-value phrases that eContext
was able to pull out of the submitted text as well as associated scores for each. The "scored_categories" object contains a list of "category_id" and "score" objects where the 
"category_id" corresponds to an item in the "categories" dictionary. Higher values indicate 
a higher score.

Resource URL
^^^^^^^^^^^^

:api_url:`classify/tweets/:result_id`

Parameters
^^^^^^^^^^

.. csv-table::
    :header: "Parameter","Type","Description"
    :stub-columns: 1
    :widths: 25, 20, 100
    
    "result_id (*required*)", "string", "A result_id string obtained as a result in the response from the ``POST``."

.. The sentiment score that is returned (if the sentiment flag is turned on) is an integer between  ``0`` and ``10``.  A value of ``0`` indicates severe negative sentiment.  A value of ``5`` indicates neutrality, and a value of ``10`` indicates extremely positive sentiment.

Example Request
^^^^^^^^^^^^^^^

GET Request
"""""""""""

.. parsed-literal::

    curl -X GET -u username:password \\
    :api_url:`classify/tweets/3786eba19540a9d595a6a410218e49dbf08eb4de9f50ec25674c2cf51d92158c`

GET Response
""""""""""""

.. code-block:: json
    
    {
	"econtext": {
	    "classify": {
		"tweets": [
		    {
			"scored_categories": [
			    {
				"category_id": "0a13e7ea736a720e6b5cf35b50e33ec2",
				"score": 1
			    }
			],
			"scored_keywords": [
			    {
				"keyword": "my first status",
				"score": 1
			    },
			    {
				"keyword": "twitter",
				"score": 1
			    }
			]
		    },
		    {
			"scored_categories": [
			    {
				"category_id": "189d0824d6c8d5e2466f3a3c14f9795f",
				"score": 4
			    },
			    {
				"category_id": "ca53bc93257b514dfb55e2a88a0d001d",
				"score": 2
			    }
			],
			"scored_keywords": [
			    {
				"keyword": "check",
				"score": 1
			    },
			    {
				"keyword": "the loop",
				"score": 1
			    },
			    {
				"keyword": "new # chicago hotels",
				"score": 1
			    },
			    {
				"keyword": "# chicago hotel",
				"score": 1
			    }
			]
		    }
		],
		"categories": {
		    "189d0824d6c8d5e2466f3a3c14f9795f": {
			"id": "189d0824d6c8d5e2466f3a3c14f9795f",
			"name": "Hotels in Chicago, Illinois",
			"path": [
			    "Travel",
			    "Travel Accommodations",
			    "Hotels & Motels",
			    "Hotels in Chicago, Illinois"
			]
		    },
		    "ca53bc93257b514dfb55e2a88a0d001d": {
			"id": "ca53bc93257b514dfb55e2a88a0d001d",
			"name": "Hotels & Motels",
			"path": [
			    "Travel",
			    "Travel Accommodations",
			    "Hotels & Motels"
			]
		    },
		    "0a13e7ea736a720e6b5cf35b50e33ec2": {
			"id": "0a13e7ea736a720e6b5cf35b50e33ec2",
			"name": "Twitter",
			"path": [
			    "Computers & Electronics",
			    "Internet",
			    "Websites & Online Content",
			    "Twitter"
			]
		    }
		}
	    },
	    "signature": {
		"resource": "GET /classify/:type/:result_id",
		"status": "200 OK - successful",
		"client_ip": "127.0.0.1"
	    }
	}
    }
