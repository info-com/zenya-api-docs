Categories
==========

.. contents:: Categories Calls
    :local:

GET categories/tiers
--------------------

Retrieve the top tier Categories from the eContext Taxonomy.  The categories returned from this call may be used to specify
a branch of the taxonomy that you would like to limit mapping and search to.

Resource URL
^^^^^^^^^^^^

:api_url:`categories/tiers`

Example Request
^^^^^^^^^^^^^^^

GET Request
"""""""""""

.. parsed-literal::
    
    curl -X GET -u username:password :api_url:`categories/tiers`

GET Response
""""""""""""

.. code-block:: json
    
    {
      "econtext": {
        "categories": [
          {
            "id": "719105219f516cdbd3bc846a12df0b44",
            "name": "Adult Content",
            "path": [
              "Adult Content"
            ],
            "idpath": [
              "719105219f516cdbd3bc846a12df0b44"
            ],
            "stats": {
              "social_idf": 296563.6,
              "social_relevance": 0.0000027124
            }
          },
          {
            "id": "922b44e4080760bcd7f30f0a676d3dfd",
            "name": "Apparel",
            "path": [
              "Apparel"
            ],
            "idpath": [
              "922b44e4080760bcd7f30f0a676d3dfd"
            ],
            "stats": {
              "social_idf": 15787.579033579,
              "social_relevance": 0.0000509518
            }
          },
          {
            "id": "0cc9e1516aaa38d4802a2ee5314ac4ab",
            "name": "Arts & Entertainment",
            "path": [
              "Arts & Entertainment"
            ],
            "idpath": [
              "0cc9e1516aaa38d4802a2ee5314ac4ab"
            ],
            "stats": {
              "social_idf": 2143.2770736046,
              "social_relevance": 0.0003753161
            }
          },
          {
            "id": "6cfd0f39559d540094604e7eb3e54098",
            "name": "Beauty",
            "path": [
              "Beauty"
            ],
            "idpath": [
              "6cfd0f39559d540094604e7eb3e54098"
            ],
            "stats": {
              "social_idf": 913.3248365394,
              "social_relevance": 0.0008807451
            }
          },
          {
            "id": "3064c1a4cbbabd7f0ffd45cd40db97ed",
            "name": "Books & Literature",
            "path": [
              "Books & Literature"
            ],
            "idpath": [
              "3064c1a4cbbabd7f0ffd45cd40db97ed"
            ],
            "stats": {
              "social_idf": 17636.444647759,
              "social_relevance": 0.0000456105
            }
          },
          {
            "id": "246045a85ad09438156569ba21b02f5e",
            "name": "Business & Industrial",
            "path": [
              "Business & Industrial"
            ],
            "idpath": [
              "246045a85ad09438156569ba21b02f5e"
            ],
            "stats": {
              "social_idf": 505.1528825996,
              "social_relevance": 0.0015924017
            }
          },
          {
            "id": "f2300bfd81612ac3e8e5c154334057c5",
            "name": "Computers & Electronics",
            "path": [
              "Computers & Electronics"
            ],
            "idpath": [
              "f2300bfd81612ac3e8e5c154334057c5"
            ],
            "stats": {
              "social_idf": 5407.1904628331,
              "social_relevance": 0.000148766
            }
          },
          {
            "id": "27e0bc27298feede36140f281e0dee16",
            "name": "Finance",
            "path": [
              "Finance"
            ],
            "idpath": [
              "27e0bc27298feede36140f281e0dee16"
            ],
            "stats": {
              "social_idf": 1640.1458351059,
              "social_relevance": 0.0004904481
            }
          },
          {
            "id": "10fedce50b97f7006e71901bcdacc0fc",
            "name": "Food & Drink",
            "path": [
              "Food & Drink"
            ],
            "idpath": [
              "10fedce50b97f7006e71901bcdacc0fc"
            ],
            "stats": {
              "social_idf": 2338.8296529969,
              "social_relevance": 0.0003439354
            }
          },
          {
            "id": "132a2327ee287cd11be6d6fd6fb2f276",
            "name": "Games & Toys",
            "path": [
              "Games & Toys"
            ],
            "idpath": [
              "132a2327ee287cd11be6d6fd6fb2f276"
            ],
            "stats": {
              "social_idf": 2772.4196749605,
              "social_relevance": 0.0002901459
            }
          },
          {
            "id": "e205ca26092d0fdb0b7a49354a3fe318",
            "name": "Government",
            "path": [
              "Government"
            ],
            "idpath": [
              "e205ca26092d0fdb0b7a49354a3fe318"
            ],
            "stats": {
              "social_idf": 1167.0077491222,
              "social_relevance": 0.0006892896
            }
          },
          {
            "id": "65a41262de6b6fa72bebc5fb7b84d4dd",
            "name": "Health",
            "path": [
              "Health"
            ],
            "idpath": [
              "65a41262de6b6fa72bebc5fb7b84d4dd"
            ],
            "stats": {
              "social_idf": 563.5454013916,
              "social_relevance": 0.0014274029
            }
          },
          {
            "id": "04265b097615aa97178e3e06d933a31a",
            "name": "Hobbies & Leisure",
            "path": [
              "Hobbies & Leisure"
            ],
            "idpath": [
              "04265b097615aa97178e3e06d933a31a"
            ],
            "stats": {
              "social_idf": 8730.3596014493,
              "social_relevance": 0.000092139
            }
          },
          {
            "id": "0b1cfd1a5102a974a372e9bc3cfffb35",
            "name": "Home & Garden",
            "path": [
              "Home & Garden"
            ],
            "idpath": [
              "0b1cfd1a5102a974a372e9bc3cfffb35"
            ],
            "stats": {
              "social_idf": 10614.886563877,
              "social_relevance": 0.000075781
            }
          },
          {
            "id": "be42e02a03e419e7d31db6b54ef84913",
            "name": "Jobs & Education",
            "path": [
              "Jobs & Education"
            ],
            "idpath": [
              "be42e02a03e419e7d31db6b54ef84913"
            ],
            "stats": {
              "social_idf": 917934.95238095,
              "social_relevance": 0.000001
            }
          },
          {
            "id": "9449388ba0686b2b73d88f6801ae43d3",
            "name": "Law & Legal",
            "path": [
              "Law & Legal"
            ],
            "idpath": [
              "9449388ba0686b2b73d88f6801ae43d3"
            ],
            "stats": {
              "social_idf": 2320.5289514867,
              "social_relevance": 0.0003466478
            }
          },
          {
            "id": "bcfb236bcfc3b0f4f03a3cfeed7253a7",
            "name": "People & Society",
            "path": [
              "People & Society"
            ],
            "idpath": [
              "bcfb236bcfc3b0f4f03a3cfeed7253a7"
            ],
            "stats": {
              "social_idf": 2780.8185227928,
              "social_relevance": 0.0002892696
            }
          },
          {
            "id": "0bd59f073e8d6969764d60d60c8e472a",
            "name": "Pets & Animals",
            "path": [
              "Pets & Animals"
            ],
            "idpath": [
              "0bd59f073e8d6969764d60d60c8e472a"
            ],
            "stats": {
              "social_idf": 154213.072,
              "social_relevance": 0.0000052162
            }
          },
          {
            "id": "1a25b3de350ce8b90adf2488940ac282",
            "name": "Real Estate",
            "path": [
              "Real Estate"
            ],
            "idpath": [
              "1a25b3de350ce8b90adf2488940ac282"
            ],
            "stats": {
              "social_idf": 2770.825643237,
              "social_relevance": 0.0002903129
            }
          },
          {
            "id": "97a2cc1e4f6df353e6eab12cfe9782ef",
            "name": "Sciences & Humanities",
            "path": [
              "Sciences & Humanities"
            ],
            "idpath": [
              "97a2cc1e4f6df353e6eab12cfe9782ef"
            ],
            "stats": {
              "social_idf": 481915.85,
              "social_relevance": 0.0000016692
            }
          },
          {
            "id": "62d92a4437331aae79cd0181b8e3e48d",
            "name": "Shopping",
            "path": [
              "Shopping"
            ],
            "idpath": [
              "62d92a4437331aae79cd0181b8e3e48d"
            ],
            "stats": {
              "social_idf": null,
              "social_relevance": null
            }
          },
          {
            "id": "b00fac5f30dc8dbb660c8d08fe66f487",
            "name": "Sports",
            "path": [
              "Sports"
            ],
            "idpath": [
              "b00fac5f30dc8dbb660c8d08fe66f487"
            ],
            "stats": {
              "social_idf": 976.9719730374,
              "social_relevance": 0.0008233668
            }
          },
          {
            "id": "71d23bae99aff67ee839c60c0c8ba179",
            "name": "Travel",
            "path": [
              "Travel"
            ],
            "idpath": [
              "71d23bae99aff67ee839c60c0c8ba179"
            ],
            "stats": {
              "social_idf": 777.0329732344,
              "social_relevance": 0.001035228
            }
          },
          {
            "id": "8e80758bbe284a4a02ffaad4636f21b2",
            "name": "Vehicles",
            "path": [
              "Vehicles"
            ],
            "idpath": [
              "8e80758bbe284a4a02ffaad4636f21b2"
            ],
            "stats": {
              "social_idf": 3559.8585410896,
              "social_relevance": 0.0002259658
            }
          },
          {
            "id": "dec756dcf0caf002c0b704a1717e1d63",
            "name": "Weapons",
            "path": [
              "Weapons"
            ],
            "idpath": [
              "dec756dcf0caf002c0b704a1717e1d63"
            ],
            "stats": {
              "social_idf": 4606.1252090801,
              "social_relevance": 0.0001746384
            }
          }
        ],
        "signature": {
          "resource": "GET /categories/tiers",
          "status": "200 OK - successful",
          "client_ip": "127.0.0.1"
        }
      }
    }





GET categories/map/:keyword
---------------------------

Use the eContext Taxonomy to return a single best matching Category for the keyword submitted.

Resource URL
^^^^^^^^^^^^

:api_url:`categories/map/:keyword`

Parameters
^^^^^^^^^^

.. csv-table::
    :header: "Parameter","Type","Description"
    :stub-columns: 1
    :widths: 25, 20, 100
    
    "keyword (*required*)", "string", "The keyword to provide a best match Category for.  This should be URL encoded.
      
      Example Value: ``chicago+hotels``."
    "use_density (*optional*)", "boolean", "Optional fall back on matching against pre-classified eContext keywords. Uses the same methodology as the ``categories/search`` function, returning the highest confidence answer, only.  Defaults to *0*.
      
      Example Value: ``1``"
    "branches (*optional*)","string","An array of category/tier ids used to limit classification results.
      
      Example Value: ``922b44e4080760bcd7f30f0a676d3dfd``"

Example Request
^^^^^^^^^^^^^^^

GET Request
"""""""""""

.. parsed-literal::
    
    curl -X GET -u username:password :api_url:`categories/map/breaking+bad+tshirt?branches[]=922b44e4080760bcd7f30f0a676d3dfd`

GET Response
""""""""""""

.. code-block:: json
    
    {
      "econtext": {
        "categories": [
          {
            "id": "99d39893587ca299b70c4e9cd725c383",
            "name": "T-Shirts",
            "path": [
              "Apparel",
              "Clothing",
              "Shirts & Tops",
              "Shirts & Tops [No Demographic Specified]",
              "Casual Shirts & Tops",
              "T-Shirts"
            ],
            "idpath": [
              "922b44e4080760bcd7f30f0a676d3dfd",
              "3f58d0f311043889059146c7dc765bd3",
              "8f0ea90fa739b596619a75cbfd50ba47",
              "0dac4f87992e3197f964a30aa670dd76",
              "13d1828fbb80571690be3ef2c7971a7b",
              "99d39893587ca299b70c4e9cd725c383"
            ],
            "stats": {
              "social_relevance": 0.0005984496,
              "social_idf": 1349.3014255217
            }
          }
        ],
        "signature": {
          "resource": "GET /categories/map/:keyword",
          "status": "200 OK - successful",
          "client_ip": "54.243.176.220"
        }
      }
    }









GET categories/search/:keyword
------------------------------

Sometimes you might want to retrieve a set of possible Categories from the provided keyword rather than 
mapping against the rules of the eContext Taxonomy. This method of matching uses a set of over 
600,000,000 pre-classified keywords to identify probable Category matches for the particular keyword 
you are interested in, and includes a confidence score for each category.

Resource URL
^^^^^^^^^^^^

:api_url:`categories/search/:keyword`

Parameters
^^^^^^^^^^

.. csv-table::
    :header: "Parameter","Type","Description"
    :stub-columns: 1
    :widths: 25, 20, 100
    
    "keyword (*required*)", "string", "The keyword to match against the eContext Keyword Dataset for possible categorization. This value should be URL encoded.
      
      Example Value: ``chicago+hotels``."
    "limit (*optional*)", "integer", "The number of Category objects to return in the result set. The max number of Categories is ``10`` and the default is ``5``.
      
      Example Value: ``3``"

Example Request
^^^^^^^^^^^^^^^

GET Request
"""""""""""

.. parsed-literal::
    
    curl -X GET -u username:password :api_url:`categories/search/chicago+hotels?limit=3`

GET Response
""""""""""""

.. code-block:: json
    
    {
      "econtext": {
        "categories": [
          {
            "id": "218f5840b5c92395b3654a92035016fd",
            "name": "Hotels in Chicago, Illinois",
            "path": [
              "Travel",
              "Travel Accommodations",
              "Hotels & Motels",
              "North America Hotels",
              "Hotels in the US",
              "Hotels in Illinois",
              "Hotels in Chicago, Illinois"
            ],
            "idpath": [
              "71d23bae99aff67ee839c60c0c8ba179",
              "c41e1ed41cebef0eb241fd192c0e604e",
              "c915f112a5632b280c894e262828c981",
              "8aa4ecfd7cd7a17dcab56a9a37f610fd",
              "435b6bdfab0bf365e5e6887a1b7b3171",
              "06702a0bf4ff694903c44455487c3e1b",
              "218f5840b5c92395b3654a92035016fd"
            ],
            "stats": {
              "social_idf": 713949.40740741,
              "social_relevance": 0.0000011267
            },
            "confidence": 0.87356944379033
          },
          {
            "id": "c915f112a5632b280c894e262828c981",
            "name": "Hotels & Motels",
            "path": [
              "Travel",
              "Travel Accommodations",
              "Hotels & Motels"
            ],
            "idpath": [
              "71d23bae99aff67ee839c60c0c8ba179",
              "c41e1ed41cebef0eb241fd192c0e604e",
              "c915f112a5632b280c894e262828c981"
            ],
            "stats": {
              "social_idf": 1752.8993361826,
              "social_relevance": 0.0004589005
            },
            "confidence": 0.032166909998587
          },
          {
            "id": "ccae5eac4fd6066ca54b80e2d7538904",
            "name": "Hotel Discounts",
            "path": [
              "Travel",
              "Travel Accommodations",
              "Hotels & Motels",
              "Hotels & Motels [No Location Specified]",
              "Hotels & Motels [No Feature Specified]",
              "Hotel Rates",
              "Hotel Deals",
              "Hotel Discounts"
            ],
            "idpath": [
              "71d23bae99aff67ee839c60c0c8ba179",
              "c41e1ed41cebef0eb241fd192c0e604e",
              "c915f112a5632b280c894e262828c981",
              "9ed0129c3d0fe8e16471e4e2af8e7200",
              "a6a8e75c2d32b800bbf7616d802fb4c8",
              "417588c97968aa8aac068f636824479c",
              "c46743267fe34858a80f2bd11dffe25a",
              "ccae5eac4fd6066ca54b80e2d7538904"
            ],
            "stats": {
              "social_idf": 92232.698564593,
              "social_relevance": 0.0000087215
            },
            "confidence": 0.020746008571563
          }
        ],
        "signature": {
          "resource": "GET /categories/search/:keyword",
          "status": "200 OK - successful",
          "client_ip": "127.0.0.1"
        }
      }
    }


