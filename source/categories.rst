Categories
==========

.. contents:: Categories Calls
    :local:

GET categories/map/:keyword
---------------------------

Use the Zenya Taxonomy to map your keyword to a best match Category.

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
    "use_density (*optional*)", "boolean", "Optional fall back on density match; the same as is used in the ``categories/search`` function.  Defaults to *0*.
      
      Example Value: ``1``"

Example Request
^^^^^^^^^^^^^^^

GET Request
"""""""""""

.. parsed-literal::
    
    curl -X GET -u username:password :api_url:`categories/map/breaking+bad`

GET Response
""""""""""""

.. code-block:: json
    
    {
	"zenya": {
	    "categories": [
		{
		    "id": "218f5840b5c92395b3654a92035016fd",
		    "name": "Hotels in Chicago, Illinois",
		    "path": [
			"Travel",
			"Travel Accommodations",
			"Hotels & Motels",
			"Hotels in Chicago, Illinois"
		    ]
		}
	    ],
	    "signature": {
		"resource": "GET /categories/map/:keyword",
		"status": "200 OK - successful",
		"client_ip": "127.0.0.1"
	    }
	}
    }

GET categories/search/:keyword
------------------------------

Sometimes you might want to use a density search against the Zenya Keyword Dataset to 
provide possible Category matches rather than simply mapping against the Zenya Taxonomy.
This method of matching uses a set of over 500,000,000 categorized keywords to identify
probable category matches for the particular keyword you are interested in.

Resource URL
^^^^^^^^^^^^
:api_url:`categories/search/:keyword`

Parameters
^^^^^^^^^^

.. csv-table::
    :header: "Parameter","Type","Description"
    :stub-columns: 1
    :widths: 25, 20, 100
    
    "keyword (*required*)", "string", "The keyword to match against the Zenya Keyword Dataset for possible categorization. This value should be URL encoded.
      
      Example Value: ``chicago+hotels``."
    "limit (*optional*)", "integer", "The number of category objects to return in the result set. The max number of categories is ``10`` and the default is ``5``.
      
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
	"zenya": {
	    "categories": [
		{
		    "id": "218f5840b5c92395b3654a92035016fd",
		    "name": "Hotels in Chicago, Illinois",
		    "path": [
			"Travel",
			"Travel Accommodations",
			"Hotels & Motels",
			"Hotels in Chicago, Illinois"
		    ]
		},
		{
		    "id": "c915f112a5632b280c894e262828c981",
		    "name": "Hotels & Motels",
		    "path": [
			"Travel",
			"Travel Accommodations",
			"Hotels & Motels"
		    ]
		},
		{
		    "id": "ccae5eac4fd6066ca54b80e2d7538904",
		    "name": "Hotel Discounts",
		    "path": [
			"Travel",
			"Travel Accommodations",
			"Hotels & Motels",
			"Hotel Discounts"
		    ]
		},
		{
		    "id": "279ea6977fd894d2c4f34954dce6c75c",
		    "name": "Budget Hotels in Chicago, Illinois",
		    "path": [
			"Travel",
			"Travel Accommodations",
			"Hotels & Motels",
			"Budget Hotels in Chicago, Illinois"
		    ]
		},
		{
		    "id": "fa7f7c965a104216596faa0d9a6d72fd",
		    "name": "Hotel Suites in Chicago, Illinois",
		    "path": [
			"Travel",
			"Travel Accommodations",
			"Hotels & Motels",
			"Hotel Suites in Chicago, Illinois"
		    ]
		}
	    ],
	    "signature": {
		"resource": "GET /categories/map/:keyword",
		"status": "200 OK - successful",
		"client_ip": "127.0.0.1"
	    }
	}
    }
