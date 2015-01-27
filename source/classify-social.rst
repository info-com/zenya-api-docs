Classify Social
===============

.. contents:: Classify Social Calls
    :local:

POST classify/social
--------------------

Classify a list of social posts and return scored categories and keywords. This call creates a new result
resource that will be available for either 2 days or until being successfully consumed in a GET
call.

The response from the POST call should include a 201 HTTP Status-Code (:rfc:`2616#section-10.2.2`)
as well as a "result_uri" pointing to the result set. If the result set is not yet completed, 
the GET call will return a 202 HTTP Status-Code (:rfc:`2616#section-10.2.3`).

*There is a limit of 1,000 posts per call.*

Resource URL
^^^^^^^^^^^^
:api_url:`classify/social`

Parameters
^^^^^^^^^^

.. csv-table::
    :header: "Parameter","Type","Description"
    :stub-columns: 1
    :widths: 25, 20, 100
    
    "social (*required*)", "array", "A list (no more than 1,000 items) of strings."

Example Request
^^^^^^^^^^^^^^^

POST Request
""""""""""""

.. parsed-literal::
    
    curl -X POST -u username:password --data-binary @classify-social-input.json \\
    --header "Content-type: application/json" \\
    :api_url:`classify/social`

The contents of :download:`classify-social-input.json <_static/classify-social-input.json>`:

.. literalinclude:: _static/classify-social-input.json
    :language: json

POST Response
"""""""""""""

.. code-block:: json
    
    {
	"econtext": {
	    "classify": {
		"type": "social",
		"result_id": "88bdc5e454fba33d73ed35798ece835f17523ba351a82658b5a818ce4190b02f",
		"result_uri": "https://api.econtext.com/v2/classify/social/88bdc5e454fba33d73ed35798ece835f17523ba351a82658b5a818ce4190b02f",
		"status": "working"
	    },
	    "signature": {
		"resource": "POST /classify/:type/:result_id",
		"status": "201 Created - successful",
		"client_ip": "127.0.0.1"
	    }
	}
    }

GET classify/social/:result_id
--------------------------------

Retrieve Social classification results. If the result set is not yet complete, this 
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

:api_url:`classify/social/:result_id`

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
    :api_url:`classify/social/88bdc5e454fba33d73ed35798ece835f17523ba351a82658b5a818ce4190b02f`

GET Response
""""""""""""

.. code-block:: json
    
    {
        "econtext": {
            "classify": {
                "results": [
                    {
                        "scored_categories": [],
                        "scored_keywords": []
                    },
                    {
                        "scored_categories": [
                            {
                                "category_id": "60f935c5d2086d522ecae202e30223d7",
                                "score": 1
                            },
                            {
                                "category_id": "67e81bc4b914768b754502d66324e7c6",
                                "score": 1
                            }
                        ],
                        "scored_keywords": [
                            {
                                "keyword": "mit institute",
                                "score": 2
                            },
                            {
                                "keyword": "birthday",
                                "score": 1
                            }
                        ]
                    },
                    {
                        "scored_categories": [],
                        "scored_keywords": []
                    },
                    {
                        "scored_categories": [
                            {
                                "category_id": "c9c90dd47f31e4cdc83ebdc54d8e9c3f",
                                "score": 1
                            },
                            {
                                "category_id": "1dfd3698fb5c948621b1c20599436614",
                                "score": 1
                            }
                        ],
                        "scored_keywords": [
                            {
                                "keyword": "science fiction",
                                "score": 1
                            },
                            {
                                "keyword": "car",
                                "score": 1
                            }
                        ]
                    },
                    {
                        "scored_categories": [
                            {
                                "category_id": "ce1e59f1e5287842b8db88264c7eca47",
                                "score": 1
                            }
                        ],
                        "scored_keywords": [
                            {
                                "keyword": "time lapse video",
                                "score": 1
                            }
                        ]
                    },
                    {
                        "scored_categories": [],
                        "scored_keywords": []
                    },
                    {
                        "scored_categories": [],
                        "scored_keywords": []
                    },
                    {
                        "scored_categories": [
                            {
                                "category_id": "00ed9cdb658bf548656eddb00c341da8",
                                "score": 1
                            }
                        ],
                        "scored_keywords": [
                            {
                                "keyword": "tetri",
                                "score": 1
                            }
                        ]
                    },
                    {
                        "scored_categories": [
                            {
                                "category_id": "d0a8833955a9ca0b71171cd83b96c679",
                                "score": 1
                            }
                        ],
                        "scored_keywords": [
                            {
                                "keyword": "large earthquake",
                                "score": 2
                            }
                        ]
                    },
                    {
                        "scored_categories": [
                            {
                                "category_id": "d72d2a2af682d75e452a84c966a7f3de",
                                "score": 1
                            }
                        ],
                        "scored_keywords": [
                            {
                                "keyword": "robotic",
                                "score": 2
                            }
                        ]
                    },
                    {
                        "scored_categories": [
                            {
                                "category_id": "7c3738446505a52dd8534e23e440355a",
                                "score": 1
                            },
                            {
                                "category_id": "d1c457d94bcfc09752c8c819d6ec7dd1",
                                "score": 1
                            },
                            {
                                "category_id": "ea60bd58bd5a5d850aee8ac966081cfb",
                                "score": 1
                            }
                        ],
                        "scored_keywords": [
                            {
                                "keyword": "spacesuit",
                                "score": 1
                            },
                            {
                                "keyword": "astronaut",
                                "score": 1
                            },
                            {
                                "keyword": "shrink wrap",
                                "score": 1
                            }
                        ]
                    }
                ],
                "categories": {
                    "d0a8833955a9ca0b71171cd83b96c679": {
                        "id": "d0a8833955a9ca0b71171cd83b96c679",
                        "name": "Largest Earthquakes",
                        "path": [
                            "Sciences \u0026 Humanities",
                            "Weather",
                            "Earthquakes",
                            "Largest Earthquakes"
                        ]
                    },
                    "1dfd3698fb5c948621b1c20599436614": {
                        "id": "1dfd3698fb5c948621b1c20599436614",
                        "name": "Cars",
                        "path": [
                            "Vehicles",
                            "Automotive",
                            "Automotive Vehicles",
                            "Cars"
                        ]
                    },
                    "d72d2a2af682d75e452a84c966a7f3de": {
                        "id": "d72d2a2af682d75e452a84c966a7f3de",
                        "name": "Robotics Engineering",
                        "path": [
                            "Sciences \u0026 Humanities",
                            "Science",
                            "Natural \u0026 Applied Sciences",
                            "Robotics Engineering"
                        ]
                    },
                    "67e81bc4b914768b754502d66324e7c6": {
                        "id": "67e81bc4b914768b754502d66324e7c6",
                        "name": "Birthdays",
                        "path": [
                            "People \u0026 Society",
                            "Holidays \u0026 Special Events",
                            "Personal Events",
                            "Birthdays"
                        ]
                    },
                    "ce1e59f1e5287842b8db88264c7eca47": {
                        "id": "ce1e59f1e5287842b8db88264c7eca47",
                        "name": "Time Lapse Photography",
                        "path": [
                            "Arts \u0026 Entertainment",
                            "Art \u0026 Architecture",
                            "Photographic \u0026 Digital Arts",
                            "Time Lapse Photography"
                        ]
                    },
                    "60f935c5d2086d522ecae202e30223d7": {
                        "id": "60f935c5d2086d522ecae202e30223d7",
                        "name": "Massachusetts Institute of Technology",
                        "path": [
                            "Jobs \u0026 Education",
                            "Education",
                            "Undergraduate Education",
                            "Massachusetts Institute of Technology"
                        ]
                    },
                    "7c3738446505a52dd8534e23e440355a": {
                        "id": "7c3738446505a52dd8534e23e440355a",
                        "name": "Space Suits",
                        "path": [
                            "Business \u0026 Industrial",
                            "Transportation \u0026 Logistics",
                            "Aerospace \u0026 Defense",
                            "Space Suits"
                        ]
                    },
                    "d1c457d94bcfc09752c8c819d6ec7dd1": {
                        "id": "d1c457d94bcfc09752c8c819d6ec7dd1",
                        "name": "NASA Astronauts",
                        "path": [
                            "Government",
                            "Governments of North America",
                            "Government of the US",
                            "NASA Astronauts"
                        ]
                    },
                    "c9c90dd47f31e4cdc83ebdc54d8e9c3f": {
                        "id": "c9c90dd47f31e4cdc83ebdc54d8e9c3f",
                        "name": "Science Fiction \u0026 Fantasy Books",
                        "path": [
                            "Books \u0026 Literature",
                            "Books \u0026 Literature Products",
                            "Fiction Books",
                            "Science Fiction \u0026 Fantasy Books"
                        ]
                    },
                    "00ed9cdb658bf548656eddb00c341da8": {
                        "id": "00ed9cdb658bf548656eddb00c341da8",
                        "name": "Tetris",
                        "path": [
                            "Computers \u0026 Electronics",
                            "Video Games",
                            "Video Game Products",
                            "Tetris"
                        ]
                    },
                    "ea60bd58bd5a5d850aee8ac966081cfb": {
                        "id": "ea60bd58bd5a5d850aee8ac966081cfb",
                        "name": "Shrink Wrap",
                        "path": [
                            "Business \u0026 Industrial",
                            "General Business \u0026 Industrial",
                            "General Business \u0026 Industrial Equipment \u0026 Supplies",
                            "Shrink Wrap"
                        ]
                    }
                }
            },
            "signature": {
                "resource": "GET \/classify\/:type\/:result_id",
                "status": "200 OK - successful",
                "client_ip": "127.0.0.1"
            }
        }
    }
