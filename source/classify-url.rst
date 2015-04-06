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

.. code-block:: json
    
    {
        "econtext": {
            "classify": {
                "title": "Parks - topics.info.com",
                "scored_categories": [
                    {
                        "category_id": "ea6ffbcd01035b37ff6ee2520886edb2",
                        "score": 94
                    },
                    {
                        "category_id": "9cce2269280df1735bfb7add016053aa",
                        "score": 18
                    },
                    {
                        "category_id": "73f184234d3663bc38a2c69c5a596f88",
                        "score": 16
                    },
                    {
                        "category_id": "796f7b52fd5700e86550dcb0e3516b37",
                        "score": 14
                    },
                    {
                        "category_id": "9f42639bc209e5045e4a51590cdfa176",
                        "score": 12
                    },
                    {
                        "category_id": "1107001263f3bb50b39e06927cdfe25e",
                        "score": 10
                    },
                    {
                        "category_id": "b7e52fc4fec0604a147b069f88c96b21",
                        "score": 8
                    },
                    {
                        "category_id": "321823741cea94b74c4052353cfd60b5",
                        "score": 8
                    },
                    {
                        "category_id": "74e6481ac198124b100f71cbbdee0f97",
                        "score": 8
                    },
                    {
                        "category_id": "7109ce21fef05dac6712d9a3a04e0bc8",
                        "score": 8
                    },
                    {
                        "category_id": "551640eba8f1a37aef0f8cdf53856dce",
                        "score": 6
                    },
                    {
                        "category_id": "47fdc91255f389f287d234fbdfbd1bdf",
                        "score": 6
                    },
                    {
                        "category_id": "fb9dcbc78dc77f9ad762bbe5ddb8227d",
                        "score": 4
                    },
                    {
                        "category_id": "04839ba22bccf21811c82615576fa29d",
                        "score": 4
                    },
                    {
                        "category_id": "d9b5c51c9dba85c63687be5e7a20f9e3",
                        "score": 4
                    },
                    {
                        "category_id": "a1e0ab985dc13d11cdc971457d08eb09",
                        "score": 4
                    },
                    {
                        "category_id": "3f8171bd811a887e72a346c8074ff4a4",
                        "score": 4
                    },
                    {
                        "category_id": "2e59b740f636f1266c11d8c131d3cf99",
                        "score": 4
                    },
                    {
                        "category_id": "96c6ccdf98424017a9cdd424488d5fb2",
                        "score": 4
                    },
                    {
                        "category_id": "fab214cbdc889d506f4c38c669f04d81",
                        "score": 4
                    },
                    {
                        "category_id": "c21b325e6677b113feaeba808cdb60b8",
                        "score": 4
                    },
                    {
                        "category_id": "8ce4fc6e479203528fee9da65255d6c8",
                        "score": 4
                    },
                    {
                        "category_id": "0cf2772b4005706b980e678da13ca2ad",
                        "score": 4
                    },
                    {
                        "category_id": "9809e8e43f1b8ee6b3cb1d9f5ce40875",
                        "score": 4
                    },
                    {
                        "category_id": "d0eeda292f4bdc0d8bd4c63654c87006",
                        "score": 4
                    },
                    {
                        "category_id": "3b5c33221277d029b473d929bd2bf95d",
                        "score": 4
                    },
                    {
                        "category_id": "669a6c25adde8ba94c543970b0c6c60f",
                        "score": 4
                    },
                    {
                        "category_id": "ddca6e39042ecd2359850018486639b2",
                        "score": 4
                    },
                    {
                        "category_id": "78425310c9d085b9b93261f035a66597",
                        "score": 4
                    },
                    {
                        "category_id": "d556451cf71b9bf1eaea6ed7cef75eb3",
                        "score": 4
                    },
                    {
                        "category_id": "e73adb7d92811d4d8091940a90bd2584",
                        "score": 4
                    },
                    {
                        "category_id": "68fcfb3dea55fba9bcdc3148fa451c3f",
                        "score": 4
                    },
                    {
                        "category_id": "6c6c61694f8d7eda13818e1facf8414c",
                        "score": 4
                    },
                    {
                        "category_id": "8cd451f6f48e5d1c527dc6a09b87b6cf",
                        "score": 4
                    },
                    {
                        "category_id": "60784e92c2d4a29746898a07c67f925e",
                        "score": 4
                    },
                    {
                        "category_id": "847994c2f48c7c9b877e5f70fcf8cdc4",
                        "score": 4
                    },
                    {
                        "category_id": "244dbc7d9cfd0f20af08fb650ca16662",
                        "score": 4
                    },
                    {
                        "category_id": "fb9bf7b28f385841bb5a9c5ffc5e7395",
                        "score": 4
                    },
                    {
                        "category_id": "b6008e08ab19c8d6e5691ad12d30fcdc",
                        "score": 2
                    },
                    {
                        "category_id": "eb8b901faaf65f319b62d7877c99da77",
                        "score": 2
                    },
                    {
                        "category_id": "0899bf4ddb4c3e6cfce37aaf2a0faad0",
                        "score": 2
                    },
                    {
                        "category_id": "1de55b5239dcc10dfb2e400cf235ce87",
                        "score": 2
                    },
                    {
                        "category_id": "69a07de549ffa40efe90a48bb5fec021",
                        "score": 2
                    },
                    {
                        "category_id": "a1c05bb2a32386df75f092f86f698058",
                        "score": 2
                    },
                    {
                        "category_id": "216768c903c4fc2e76643b48b53fa5de",
                        "score": 2
                    },
                    {
                        "category_id": "ee01bbb89527fa494054474f44266069",
                        "score": 2
                    }
                ],
                "scored_keywords": [
                    {
                        "keyword": "parks",
                        "score": 68
                    },
                    {
                        "keyword": "the director",
                        "score": 30
                    },
                    {
                        "keyword": "recreation departments",
                        "score": 22
                    },
                    {
                        "keyword": "state parks",
                        "score": 22
                    },
                    {
                        "keyword": "local parks",
                        "score": 14
                    },
                    {
                        "keyword": "recreation",
                        "score": 14
                    },
                    {
                        "keyword": "california",
                        "score": 14
                    },
                    {
                        "keyword": "the department",
                        "score": 14
                    },
                    {
                        "keyword": "parks management education programs",
                        "score": 12
                    },
                    {
                        "keyword": "topics.info.com",
                        "score": 12
                    },
                    {
                        "keyword": "development",
                        "score": 12
                    },
                    {
                        "keyword": "the chicago park district",
                        "score": 12
                    },
                    {
                        "keyword": "city park district management",
                        "score": 10
                    },
                    {
                        "keyword": "search the web",
                        "score": 10
                    },
                    {
                        "keyword": "related articles",
                        "score": 10
                    },
                    {
                        "keyword": "programs",
                        "score": 10
                    },
                    {
                        "keyword": "state park agencies",
                        "score": 10
                    },
                    {
                        "keyword": "the parks",
                        "score": 10
                    },
                    {
                        "keyword": "the state",
                        "score": 8
                    },
                    {
                        "keyword": "a prime example",
                        "score": 8
                    },
                    {
                        "keyword": "trails",
                        "score": 8
                    },
                    {
                        "keyword": "activities",
                        "score": 8
                    },
                    {
                        "keyword": "state",
                        "score": 8
                    },
                    {
                        "keyword": "a parks",
                        "score": 8
                    },
                    {
                        "keyword": "county",
                        "score": 8
                    },
                    {
                        "keyword": "the city",
                        "score": 8
                    },
                    {
                        "keyword": "stables",
                        "score": 8
                    },
                    {
                        "keyword": "the u.s",
                        "score": 6
                    },
                    {
                        "keyword": "the national association",
                        "score": 6
                    },
                    {
                        "keyword": "the state park system",
                        "score": 6
                    },
                    {
                        "keyword": "management",
                        "score": 6
                    },
                    {
                        "keyword": "aspiring park management professionals",
                        "score": 6
                    },
                    {
                        "keyword": "recreation department director",
                        "score": 6
                    },
                    {
                        "keyword": "recreation department advisory board",
                        "score": 6
                    },
                    {
                        "keyword": "the california department",
                        "score": 6
                    },
                    {
                        "keyword": "investments",
                        "score": 4
                    },
                    {
                        "keyword": "financial decisions",
                        "score": 4
                    },
                    {
                        "keyword": "government",
                        "score": 4
                    },
                    {
                        "keyword": "their state park systems",
                        "score": 4
                    },
                    {
                        "keyword": "its state government",
                        "score": 4
                    },
                    {
                        "keyword": "the safety",
                        "score": 4
                    },
                    {
                        "keyword": "state park management infrastructure",
                        "score": 4
                    },
                    {
                        "keyword": "california office",
                        "score": 4
                    },
                    {
                        "keyword": "marinas",
                        "score": 4
                    },
                    {
                        "keyword": "\u00a9shutterstock",
                        "score": 4
                    },
                    {
                        "keyword": "several colleges",
                        "score": 4
                    },
                    {
                        "keyword": "cash management",
                        "score": 4
                    },
                    {
                        "keyword": "new board members",
                        "score": 4
                    },
                    {
                        "keyword": "the maintenance",
                        "score": 4
                    },
                    {
                        "keyword": "additional state parks",
                        "score": 4
                    },
                    {
                        "keyword": "recreation facilities",
                        "score": 4
                    },
                    {
                        "keyword": "a park",
                        "score": 4
                    },
                    {
                        "keyword": "trees knowledge",
                        "score": 4
                    },
                    {
                        "keyword": "information technology",
                        "score": 4
                    },
                    {
                        "keyword": "assistance",
                        "score": 4
                    },
                    {
                        "keyword": "a municipal",
                        "score": 4
                    },
                    {
                        "keyword": "wildlife recreation management",
                        "score": 4
                    },
                    {
                        "keyword": "parish authority",
                        "score": 4
                    },
                    {
                        "keyword": "the federal parks system",
                        "score": 4
                    },
                    {
                        "keyword": "construction management",
                        "score": 4
                    },
                    {
                        "keyword": "funds",
                        "score": 4
                    },
                    {
                        "keyword": "the state park systems vegetation",
                        "score": 4
                    },
                    {
                        "keyword": "special events",
                        "score": 4
                    },
                    {
                        "keyword": "\u0027s accounting department",
                        "score": 4
                    },
                    {
                        "keyword": "vendor bids",
                        "score": 4
                    },
                    {
                        "keyword": "recreation ecology",
                        "score": 4
                    },
                    {
                        "keyword": "ogals",
                        "score": 4
                    },
                    {
                        "keyword": "director",
                        "score": 4
                    },
                    {
                        "keyword": "\u0027s central park",
                        "score": 4
                    },
                    {
                        "keyword": "general counsel",
                        "score": 4
                    },
                    {
                        "keyword": "commissioners",
                        "score": 4
                    },
                    {
                        "keyword": "california state parks general plans division",
                        "score": 4
                    },
                    {
                        "keyword": "the management",
                        "score": 4
                    },
                    {
                        "keyword": "additional officials",
                        "score": 4
                    },
                    {
                        "keyword": "certain park areas",
                        "score": 4
                    },
                    {
                        "keyword": "the guidance",
                        "score": 4
                    },
                    {
                        "keyword": "a grassy area",
                        "score": 4
                    },
                    {
                        "keyword": "golf courses",
                        "score": 4
                    },
                    {
                        "keyword": "recreational facilities",
                        "score": 4
                    },
                    {
                        "keyword": "facilities",
                        "score": 4
                    },
                    {
                        "keyword": "wildland recreation management",
                        "score": 4
                    },
                    {
                        "keyword": "assessment programs",
                        "score": 4
                    },
                    {
                        "keyword": "local park areas",
                        "score": 4
                    },
                    {
                        "keyword": "a state agency",
                        "score": 4
                    },
                    {
                        "keyword": "park districts",
                        "score": 4
                    },
                    {
                        "keyword": "pools",
                        "score": 4
                    },
                    {
                        "keyword": "human resources",
                        "score": 4
                    },
                    {
                        "keyword": "monitoring",
                        "score": 4
                    },
                    {
                        "keyword": "recreation natural resources division",
                        "score": 4
                    },
                    {
                        "keyword": "administers",
                        "score": 4
                    },
                    {
                        "keyword": "park maintenance standards",
                        "score": 4
                    },
                    {
                        "keyword": "wilderness first-responder training",
                        "score": 4
                    },
                    {
                        "keyword": "management resources",
                        "score": 4
                    },
                    {
                        "keyword": "individual state parks",
                        "score": 4
                    },
                    {
                        "keyword": "the facility management department",
                        "score": 4
                    },
                    {
                        "keyword": "lodges",
                        "score": 4
                    },
                    {
                        "keyword": "forest",
                        "score": 4
                    },
                    {
                        "keyword": "cabins",
                        "score": 4
                    },
                    {
                        "keyword": "recreation area users",
                        "score": 4
                    },
                    {
                        "keyword": "state park government agencies effectively",
                        "score": 4
                    }
                ],
                "categories": {
                    "b6008e08ab19c8d6e5691ad12d30fcdc": {
                        "id": "b6008e08ab19c8d6e5691ad12d30fcdc",
                        "name": "Websites \u0026 Online Content",
                        "path": [
                            "Computers \u0026 Electronics",
                            "Telecommunications",
                            "Internet Access",
                            "Websites \u0026 Online Content"
                        ]
                    },
                    "fb9dcbc78dc77f9ad762bbe5ddb8227d": {
                        "id": "fb9dcbc78dc77f9ad762bbe5ddb8227d",
                        "name": "Construction",
                        "path": [
                            "Business \u0026 Industrial",
                            "Construction"
                        ]
                    },
                    "eb8b901faaf65f319b62d7877c99da77": {
                        "id": "eb8b901faaf65f319b62d7877c99da77",
                        "name": "19th Century Architecture",
                        "path": [
                            "Arts \u0026 Entertainment",
                            "Art \u0026 Architecture",
                            "Architecture \u0026 Urban Planning",
                            "19th Century Architecture"
                        ]
                    },
                    "04839ba22bccf21811c82615576fa29d": {
                        "id": "04839ba22bccf21811c82615576fa29d",
                        "name": "Campgrounds",
                        "path": [
                            "Travel",
                            "Travel Accommodations",
                            "Campgrounds"
                        ]
                    },
                    "9f42639bc209e5045e4a51590cdfa176": {
                        "id": "9f42639bc209e5045e4a51590cdfa176",
                        "name": "Government",
                        "path": [
                            "Government"
                        ]
                    },
                    "b7e52fc4fec0604a147b069f88c96b21": {
                        "id": "b7e52fc4fec0604a147b069f88c96b21",
                        "name": "Information Technology Services",
                        "path": [
                            "Business \u0026 Industrial",
                            "General Business \u0026 Industrial",
                            "General Business \u0026 Industrial Services",
                            "Information Technology Services"
                        ]
                    },
                    "d9b5c51c9dba85c63687be5e7a20f9e3": {
                        "id": "d9b5c51c9dba85c63687be5e7a20f9e3",
                        "name": "Shutterstock",
                        "path": [
                            "Arts \u0026 Entertainment",
                            "Art \u0026 Architecture",
                            "Photographic \u0026 Digital Arts",
                            "Shutterstock"
                        ]
                    },
                    "a1e0ab985dc13d11cdc971457d08eb09": {
                        "id": "a1e0ab985dc13d11cdc971457d08eb09",
                        "name": "Business Auditing Services",
                        "path": [
                            "Business \u0026 Industrial",
                            "General Business \u0026 Industrial",
                            "General Business \u0026 Industrial Services",
                            "Business Auditing Services"
                        ]
                    },
                    "3f8171bd811a887e72a346c8074ff4a4": {
                        "id": "3f8171bd811a887e72a346c8074ff4a4",
                        "name": "Wildlife",
                        "path": [
                            "Pets \u0026 Animals",
                            "Wildlife"
                        ]
                    },
                    "2e59b740f636f1266c11d8c131d3cf99": {
                        "id": "2e59b740f636f1266c11d8c131d3cf99",
                        "name": "Facilities Management",
                        "path": [
                            "Business \u0026 Industrial",
                            "General Business \u0026 Industrial",
                            "General Business \u0026 Industrial Services",
                            "Facilities Management"
                        ]
                    },
                    "96c6ccdf98424017a9cdd424488d5fb2": {
                        "id": "96c6ccdf98424017a9cdd424488d5fb2",
                        "name": "Trees",
                        "path": [
                            "Home \u0026 Garden",
                            "Lawn \u0026 Garden",
                            "Lawn \u0026 Garden Products",
                            "Trees"
                        ]
                    },
                    "fab214cbdc889d506f4c38c669f04d81": {
                        "id": "fab214cbdc889d506f4c38c669f04d81",
                        "name": "Law \u0026 Legal",
                        "path": [
                            "Law \u0026 Legal"
                        ]
                    },
                    "551640eba8f1a37aef0f8cdf53856dce": {
                        "id": "551640eba8f1a37aef0f8cdf53856dce",
                        "name": "Mayors",
                        "path": [
                            "Government",
                            "Government [No Location Specified]",
                            "Governmental Structures",
                            "Mayors"
                        ]
                    },
                    "0899bf4ddb4c3e6cfce37aaf2a0faad0": {
                        "id": "0899bf4ddb4c3e6cfce37aaf2a0faad0",
                        "name": "Outdoor Sports",
                        "path": [
                            "Sports",
                            "Outdoor Sports"
                        ]
                    },
                    "c21b325e6677b113feaeba808cdb60b8": {
                        "id": "c21b325e6677b113feaeba808cdb60b8",
                        "name": "Hunting",
                        "path": [
                            "Sports",
                            "Outdoor Sports",
                            "Hunting"
                        ]
                    },
                    "8ce4fc6e479203528fee9da65255d6c8": {
                        "id": "8ce4fc6e479203528fee9da65255d6c8",
                        "name": "Holidays \u0026 Special Events",
                        "path": [
                            "People \u0026 Society",
                            "Holidays \u0026 Special Events"
                        ]
                    },
                    "0cf2772b4005706b980e678da13ca2ad": {
                        "id": "0cf2772b4005706b980e678da13ca2ad",
                        "name": "Computer Technical Support",
                        "path": [
                            "Computers \u0026 Electronics",
                            "Computers",
                            "Computer Services",
                            "Computer Technical Support"
                        ]
                    },
                    "9809e8e43f1b8ee6b3cb1d9f5ce40875": {
                        "id": "9809e8e43f1b8ee6b3cb1d9f5ce40875",
                        "name": "Golf Courses",
                        "path": [
                            "Sports",
                            "Individual Sports",
                            "Golf",
                            "Golf Courses"
                        ]
                    },
                    "73f184234d3663bc38a2c69c5a596f88": {
                        "id": "73f184234d3663bc38a2c69c5a596f88",
                        "name": "City Parks",
                        "path": [
                            "Travel",
                            "Sightseeing Tours \u0026 Tourist Attractions",
                            "Tourist Attractions",
                            "City Parks"
                        ]
                    },
                    "47fdc91255f389f287d234fbdfbd1bdf": {
                        "id": "47fdc91255f389f287d234fbdfbd1bdf",
                        "name": "Business Management Information",
                        "path": [
                            "Business \u0026 Industrial",
                            "General Business \u0026 Industrial",
                            "General Business \u0026 Industrial Services",
                            "Business Management Information"
                        ]
                    },
                    "8cd451f6f48e5d1c527dc6a09b87b6cf": {
                        "id": "8cd451f6f48e5d1c527dc6a09b87b6cf",
                        "name": "Cash Management",
                        "path": [
                            "Sciences \u0026 Humanities",
                            "Science",
                            "Mathematics \u0026 Computer Sciences",
                            "Cash Management"
                        ]
                    },
                    "1de55b5239dcc10dfb2e400cf235ce87": {
                        "id": "1de55b5239dcc10dfb2e400cf235ce87",
                        "name": "Parks \u0026 Natural Resources Agencies",
                        "path": [
                            "Government",
                            "Government [No Location Specified]",
                            "Parks \u0026 Natural Resources Agencies"
                        ]
                    },
                    "69a07de549ffa40efe90a48bb5fec021": {
                        "id": "69a07de549ffa40efe90a48bb5fec021",
                        "name": "Nonprofit \u0026 Charitable Organizations",
                        "path": [
                            "People \u0026 Society",
                            "Social Groups \u0026 Issues",
                            "Social Issues \u0026 Advocacy",
                            "Nonprofit \u0026 Charitable Organizations"
                        ]
                    },
                    "3b5c33221277d029b473d929bd2bf95d": {
                        "id": "3b5c33221277d029b473d929bd2bf95d",
                        "name": "Urban \u0026 Regional Planning Services",
                        "path": [
                            "Arts \u0026 Entertainment",
                            "Art \u0026 Architecture",
                            "Architecture \u0026 Urban Planning",
                            "Urban \u0026 Regional Planning Services"
                        ]
                    },
                    "669a6c25adde8ba94c543970b0c6c60f": {
                        "id": "669a6c25adde8ba94c543970b0c6c60f",
                        "name": "Swimming Pools",
                        "path": [
                            "Home \u0026 Garden",
                            "Home Spa \u0026 Recreation",
                            "Home Spa \u0026 Recreation Products",
                            "Swimming Pools"
                        ]
                    },
                    "ddca6e39042ecd2359850018486639b2": {
                        "id": "ddca6e39042ecd2359850018486639b2",
                        "name": "Skiing",
                        "path": [
                            "Sports",
                            "Winter Sports",
                            "Skiing"
                        ]
                    },
                    "78425310c9d085b9b93261f035a66597": {
                        "id": "78425310c9d085b9b93261f035a66597",
                        "name": "Investing",
                        "path": [
                            "Finance",
                            "Investing"
                        ]
                    },
                    "d556451cf71b9bf1eaea6ed7cef75eb3": {
                        "id": "d556451cf71b9bf1eaea6ed7cef75eb3",
                        "name": "Playgrounds",
                        "path": [
                            "Games \u0026 Toys",
                            "General Games \u0026 Toys Facilities",
                            "Game Playing Facilities",
                            "Playgrounds"
                        ]
                    },
                    "e73adb7d92811d4d8091940a90bd2584": {
                        "id": "e73adb7d92811d4d8091940a90bd2584",
                        "name": "Ecotourism \u0026 Nature Vacations",
                        "path": [
                            "Travel",
                            "Specialty Vacations",
                            "Ecotourism \u0026 Nature Vacations"
                        ]
                    },
                    "a1c05bb2a32386df75f092f86f698058": {
                        "id": "a1c05bb2a32386df75f092f86f698058",
                        "name": "Nonprofit Corporation Information",
                        "path": [
                            "Law \u0026 Legal",
                            "Corporate \u0026 Business Law",
                            "Corporate Law",
                            "Nonprofit Corporation Information"
                        ]
                    },
                    "74e6481ac198124b100f71cbbdee0f97": {
                        "id": "74e6481ac198124b100f71cbbdee0f97",
                        "name": "Finance",
                        "path": [
                            "Finance"
                        ]
                    },
                    "6c6c61694f8d7eda13818e1facf8414c": {
                        "id": "6c6c61694f8d7eda13818e1facf8414c",
                        "name": "Grants",
                        "path": [
                            "Finance",
                            "Financial Assistance",
                            "Grants"
                        ]
                    },
                    "ea6ffbcd01035b37ff6ee2520886edb2": {
                        "id": "ea6ffbcd01035b37ff6ee2520886edb2",
                        "name": "State \u0026 Regional Parks",
                        "path": [
                            "Travel",
                            "Sightseeing Tours \u0026 Tourist Attractions",
                            "Tourist Attractions",
                            "State \u0026 Regional Parks"
                        ]
                    },
                    "216768c903c4fc2e76643b48b53fa5de": {
                        "id": "216768c903c4fc2e76643b48b53fa5de",
                        "name": "Job Certifications",
                        "path": [
                            "Jobs \u0026 Education",
                            "Jobs",
                            "Jobs [No Industry Specified]",
                            "Job Certifications"
                        ]
                    },
                    "ee01bbb89527fa494054474f44266069": {
                        "id": "ee01bbb89527fa494054474f44266069",
                        "name": "State Governors",
                        "path": [
                            "Government",
                            "Governments of North America",
                            "Government of the US",
                            "State Governors"
                        ]
                    },
                    "68fcfb3dea55fba9bcdc3148fa451c3f": {
                        "id": "68fcfb3dea55fba9bcdc3148fa451c3f",
                        "name": "Commercial Construction Management Services",
                        "path": [
                            "Business \u0026 Industrial",
                            "Construction",
                            "Commercial \u0026 Industrial Construction Services",
                            "Commercial Construction Management Services"
                        ]
                    },
                    "d0eeda292f4bdc0d8bd4c63654c87006": {
                        "id": "d0eeda292f4bdc0d8bd4c63654c87006",
                        "name": "Accounting \u0026 Taxes",
                        "path": [
                            "Finance",
                            "Accounting \u0026 Taxes"
                        ]
                    },
                    "1107001263f3bb50b39e06927cdfe25e": {
                        "id": "1107001263f3bb50b39e06927cdfe25e",
                        "name": "Search Engines \u0026 Web Portals",
                        "path": [
                            "Computers \u0026 Electronics",
                            "Telecommunications",
                            "Internet Access",
                            "Search Engines \u0026 Web Portals"
                        ]
                    },
                    "321823741cea94b74c4052353cfd60b5": {
                        "id": "321823741cea94b74c4052353cfd60b5",
                        "name": "Human Resources",
                        "path": [
                            "Business \u0026 Industrial",
                            "General Business \u0026 Industrial",
                            "General Business \u0026 Industrial Services",
                            "Human Resources"
                        ]
                    },
                    "fb9bf7b28f385841bb5a9c5ffc5e7395": {
                        "id": "fb9bf7b28f385841bb5a9c5ffc5e7395",
                        "name": "Alcohol",
                        "path": [
                            "Food \u0026 Drink",
                            "Drinks",
                            "Alcohol"
                        ]
                    },
                    "60784e92c2d4a29746898a07c67f925e": {
                        "id": "60784e92c2d4a29746898a07c67f925e",
                        "name": "Emergency Preparedness",
                        "path": [
                            "People \u0026 Society",
                            "Social Groups \u0026 Issues",
                            "Social Issues \u0026 Advocacy",
                            "Emergency Preparedness"
                        ]
                    },
                    "9cce2269280df1735bfb7add016053aa": {
                        "id": "9cce2269280df1735bfb7add016053aa",
                        "name": "Recreation Management Services",
                        "path": [
                            "Business \u0026 Industrial",
                            "Sports \u0026 Entertainment Industry",
                            "Sports \u0026 Entertainment Industry Services",
                            "Recreation Management Services"
                        ]
                    },
                    "796f7b52fd5700e86550dcb0e3516b37": {
                        "id": "796f7b52fd5700e86550dcb0e3516b37",
                        "name": "Education \u0026 Reference Software",
                        "path": [
                            "Computers \u0026 Electronics",
                            "Computers",
                            "Computer Products",
                            "Education \u0026 Reference Software"
                        ]
                    },
                    "7109ce21fef05dac6712d9a3a04e0bc8": {
                        "id": "7109ce21fef05dac6712d9a3a04e0bc8",
                        "name": "Undergraduate Education",
                        "path": [
                            "Jobs \u0026 Education",
                            "Education",
                            "Undergraduate Education"
                        ]
                    },
                    "847994c2f48c7c9b877e5f70fcf8cdc4": {
                        "id": "847994c2f48c7c9b877e5f70fcf8cdc4",
                        "name": "Lodges",
                        "path": [
                            "Travel",
                            "Travel Accommodations",
                            "Vacation Rentals",
                            "Lodges"
                        ]
                    },
                    "244dbc7d9cfd0f20af08fb650ca16662": {
                        "id": "244dbc7d9cfd0f20af08fb650ca16662",
                        "name": "Law Enforcement",
                        "path": [
                            "Government",
                            "Government [No Location Specified]",
                            "Law Enforcement \u0026 Public Safety Agencies",
                            "Law Enforcement"
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

.. _robots.txt: http://www.robotstxt.org/robotstxt.html
