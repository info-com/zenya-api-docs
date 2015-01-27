Categories
==========

.. contents:: Categories Calls
    :local:

GET categories/tiers
--------------------

Retrieve the top tier Categories from the Zenya Taxonomy.  The categories returned from this call may be used to specify
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
	"zenya": {
	    "categories": [
		{
		    "id": "719105219f516cdbd3bc846a12df0b44",
		    "name": "Adult Content",
		    "path": ["Adult Content"]
		},
		{
		    "id": "922b44e4080760bcd7f30f0a676d3dfd",
		    "name": "Apparel",
		    "path": ["Apparel"]
		},
		{
		    "id": "0cc9e1516aaa38d4802a2ee5314ac4ab",
		    "name": "Arts & Entertainment",
		    "path": ["Arts & Entertainment"]
		},
		{
		    "id": "6cfd0f39559d540094604e7eb3e54098",
		    "name": "Beauty",
		    "path": ["Beauty"]
		},
		{
		    "id": "3064c1a4cbbabd7f0ffd45cd40db97ed",
		    "name": "Books & Literature",
		    "path": ["Books & Literature"]
		},
		{
		    "id": "246045a85ad09438156569ba21b02f5e",
		    "name": "Business & Industrial",
		    "path": ["Business & Industrial"]
		},
		{
		    "id": "f2300bfd81612ac3e8e5c154334057c5",
		    "name": "Computers & Electronics",
		    "path": ["Computers & Electronics"]
		},
		{
		    "id": "27e0bc27298feede36140f281e0dee16",
		    "name": "Finance",
		    "path": ["Finance"]
		},
		{
		    "id": "10fedce50b97f7006e71901bcdacc0fc",
		    "name": "Food & Drink",
		    "path": ["Food & Drink"]
		},
		{
		    "id": "132a2327ee287cd11be6d6fd6fb2f276",
		    "name": "Games & Toys",
		    "path": ["Games & Toys"]
		},
		{
		    "id": "e205ca26092d0fdb0b7a49354a3fe318",
		    "name": "Government",
		    "path": ["Government"]
		},
		{
		    "id": "65a41262de6b6fa72bebc5fb7b84d4dd",
		    "name": "Health",
		    "path": ["Health"]
		},
		{
		    "id": "04265b097615aa97178e3e06d933a31a",
		    "name": "Hobbies & Leisure",
		    "path": ["Hobbies & Leisure"]
		},
		{
		    "id": "0b1cfd1a5102a974a372e9bc3cfffb35",
		    "name": "Home & Garden",
		    "path": ["Home & Garden"]
		},
		{
		    "id": "be42e02a03e419e7d31db6b54ef84913",
		    "name": "Jobs & Education",
		    "path": ["Jobs & Education"]
		},
		{
		    "id": "9449388ba0686b2b73d88f6801ae43d3",
		    "name": "Law & Legal",
		    "path": ["Law & Legal"]
		},
		{
		    "id": "bcfb236bcfc3b0f4f03a3cfeed7253a7",
		    "name": "People & Society",
		    "path": ["People & Society"]
		},
		{
		    "id": "0bd59f073e8d6969764d60d60c8e472a",
		    "name": "Pets & Animals",
		    "path": ["Pets & Animals"]
		},
		{
		    "id": "1a25b3de350ce8b90adf2488940ac282",
		    "name": "Real Estate",
		    "path": ["Real Estate"]
		},
		{
		    "id": "97a2cc1e4f6df353e6eab12cfe9782ef",
		    "name": "Sciences & Humanities",
		    "path": ["Sciences & Humanities"]
		},
		{
		    "id": "62d92a4437331aae79cd0181b8e3e48d",
		    "name": "Shopping",
		    "path": ["Shopping"]
		},
		{
		    "id": "b00fac5f30dc8dbb660c8d08fe66f487",
		    "name": "Sports",
		    "path": ["Sports"]
		},
		{
		    "id": "71d23bae99aff67ee839c60c0c8ba179",
		    "name": "Travel",
		    "path": ["Travel"]
		},
		{
		    "id": "8e80758bbe284a4a02ffaad4636f21b2",
		    "name": "Vehicles",
		    "path": ["Vehicles"]
		},
		{
		    "id": "dec756dcf0caf002c0b704a1717e1d63",
		    "name": "Weapons",
		    "path": ["Weapons"]
		}
	    ],
	    "signature": {
		"resource": "GET /categories/map/:keyword",
		"status": "200 OK - successful",
		"client_ip": "127.0.0.1"
	    }
	}
    }





GET categories/map/:keyword
---------------------------

Use the eContext Taxonomy to map your keyword to a best match Category.

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
	"econtext": {
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

Sometimes you might want to use a density search against the eContext Keyword Dataset to 
provide possible Category matches rather than simply mapping against the eContext Taxonomy.
This method of matching uses a set of over 500,000,000 categorized keywords to identify
probable category matches for the particular keyword you are interested in, and includes a
confidence score for each category.

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
	"econtext": {
	    "categories": [
		{
		    "id": "218f5840b5c92395b3654a92035016fd",
		    "name": "Hotels in Chicago, Illinois",
		    "path": [
			"Travel",
			"Travel Accommodations",
			"Hotels & Motels",
			"Hotels in Chicago, Illinois"
		    ],
		    "confidence": 0.87564669363183
		},
		{
		    "id": "c915f112a5632b280c894e262828c981",
		    "name": "Hotels & Motels",
		    "path": [
			"Travel",
			"Travel Accommodations",
			"Hotels & Motels"
		    ]
		    "confidence": 0.03306368168564
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
		    "confidence": 0.02067068008654
		}
	    ],
	    "signature": {
		"resource": "GET /categories/map/:keyword",
		"status": "200 OK - successful",
		"client_ip": "127.0.0.1"
	    }
	}
    }
