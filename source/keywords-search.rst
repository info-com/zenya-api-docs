Keyword Search
==============

.. contents:: Keyword Search Calls
    :local:

POST keywords/search
---------------------------

Execute a search of the eContext Keyword Dataset and retrieve matching keywords. Returns a result_id to the GET keywords/search/:result_id call. This call creates a new result resource that will be available for either 2 days or until consumption.

This function accepts two distinct types of queries:

* By Category (``"type":0``): Searches for keywords belonging to a specified category node (category only) or branch (category + descendants).
* By Keyword (``"type":1``): Searches for keywords containing the words (including stemmed variants) of the input query.

See query and type description for formatting details.

Resource URL
^^^^^^^^^^^^
:api_url:`keywords/search`

Parameters
^^^^^^^^^^

.. csv-table::
    :header: "Parameter","Type","Description"
    :stub-columns: 1
    :widths: 25, 20, 100
    
    "query (*required*)", "mixed", "The query string, if search by Keyword, or an array of categories if searching by Category.  If searching by Category, the query should be an array of key->value pairs where the key is the Category id and the value is a boolean, selecting the entire branch if set to ``true``, or just the node, if set to ``false``."
    "type (*required*)", "enum", "What type of search is being performed.  (``0`` = by Category, ``1`` = by Keyword)"
    "filters (*optional*)", "array", "Filters to be applied to this search.  For more information please see section on :ref:`search-filters`"
    "pagesize (*optional*)", "integer", "The number of keywords to show on a single result page. Default value is ``1,000``"
    "limit (*optional*)", "integer", "The maximum number of keywords to return.  There is a system maximum of 500,000.  Default value is ``25,000``"
    

Example Request By Keyword
^^^^^^^^^^^^^^^^^^^^^^^^^^

POST Request
""""""""""""

.. parsed-literal::
    
    curl -X POST -u username:password --data-binary @keywords-search-a-input.json \\
    --header "Content-type: application/json" \\
    :api_url:`keywords/search`

The contents of :download:`keywords-search-a-input.json <_static/keywords-search-a-input.json>`:

.. literalinclude:: _static/keywords-search-a-input.json
    :language: json

POST Response
"""""""""""""

.. code-block:: json
    
    {
	"econtext": {
	    "keywords": {
		"count": 4086,
		"pagesize": 250,
		"pages": 17,
		"limit": 25000,
		"searchid": "7765ebd5f81ee17bd79cf5fbf650fc1379cf5251f4a090006250b796331a668b"
	    },
	    "signature": {
		"resource": "GET /categories/map/:keyword",
		"status": "200 OK - successful",
		"client_ip": "127.0.0.1"
	    }
	}
    }

Example Request By Category
^^^^^^^^^^^^^^^^^^^^^^^^^^^

POST Request
""""""""""""

.. parsed-literal::
    
    curl -X POST -u username:password --data-binary @keywords-search-b-input.json \\
    --header "Content-type: application/json" \\
    :api_url:`keywords/search`

The contents of :download:`keywords-search-b-input.json <_static/keywords-search-b-input.json>`:

.. literalinclude:: _static/keywords-search-b-input.json
    :language: json


POST Response
"""""""""""""

.. code-block:: json
    
    {
	"econtext": {
	    "keywords": {
		"count": 25000,
		"pagesize": 20,
		"pages": 1250,
		"limit": 25000,
		"searchid": "63c48c6eb0e25572fdd0f872a04f60c6377365cb2e9687bbbe39631b258ec289"
	    },
	    "signature": {
		"resource": "GET /categories/map/:keyword",
		"status": "200 OK - successful",
		"client_ip": "127.0.0.1"
	    }
	}
    }

GET keywords/search/:result_id
------------------------------

Return keywords from the specified search. Each keyword contains a category_id that maps to a
Category in the associated "categories" dictionary. A ``null`` value in the ``category_id`` indicates that the keyword is currently unmapped to the eContext Taxonomy.

Resource URL
^^^^^^^^^^^^
:api_url:`keywords/search/:result_id`

Parameters
^^^^^^^^^^

.. csv-table::
    :header: "Parameter","Type","Description"
    :stub-columns: 1
    :widths: 25, 20, 100
    
    "result_id (*required*)", "string", "The identifier specifying which search to return results from. The ``result_id`` is included in the response from a successful **POST** keywords/search call."
    "page (*optional*)", "integer", "Specify which page to retrieve results from.  If no page is specified, a default value of ``1`` is used.  Indexing for pages begins at ``1``."

Example Request
^^^^^^^^^^^^^^^

GET Request
"""""""""""

.. parsed-literal::

    curl -X GET -u username:password \\
    :api_url:`keywords/search/63c48c6eb0e25572fdd0f872a04f60c6377365cb2e9687bbbe39631b258ec289?page=1`

GET Response
""""""""""""

.. code-block:: json
    
    {
	"econtext": {
	    "keywords": {
		"cursor": {
		    "pages": 1250,
		    "current": 1,
		    "next": 2
		},
		"keywords": [
		    {
			"keyword": "breaking bad",
			"volume": 1680000,
			"category_id": "ac0fb32ea52f2c1228592ad6598c2cc2"
		    },
		    {
			"keyword": "breaking bad season 5",
			"volume": 337500,
			"category_id": "ac0fb32ea52f2c1228592ad6598c2cc2"
		    },
		    {
			"keyword": "breaking bad season 6",
			"volume": 123750,
			"category_id": "ac0fb32ea52f2c1228592ad6598c2cc2"
		    },
		    {
			"keyword": "breaking bad finale",
			"volume": 45375,
			"category_id": "ac0fb32ea52f2c1228592ad6598c2cc2"
		    },
		    {
			"keyword": "breaking bad season 5 episode 1",
			"volume": 45375,
			"category_id": "ac0fb32ea52f2c1228592ad6598c2cc2"
		    },
		    {
			"keyword": "breaking bad wiki",
			"volume": 37125,
			"category_id": "ac0fb32ea52f2c1228592ad6598c2cc2"
		    },
		    {
			"keyword": "watch breaking bad online",
			"volume": 30805,
			"category_id": "ac0fb32ea52f2c1228592ad6598c2cc2"
		    },
		    {
			"keyword": "breaking bad season 4",
			"volume": 30580,
			"category_id": "ac0fb32ea52f2c1228592ad6598c2cc2"
		    },
		    {
			"keyword": "breaking bad season 3",
			"volume": 25400,
			"category_id": "ac0fb32ea52f2c1228592ad6598c2cc2"
		    },
		    {
			"keyword": "breaking bad cast",
			"volume": 24825,
			"category_id": "ac0fb32ea52f2c1228592ad6598c2cc2"
		    },
		    {
			"keyword": "breaking bad recap",
			"volume": 24825,
			"category_id": "ac0fb32ea52f2c1228592ad6598c2cc2"
		    },
		    {
			"keyword": "breaking bad season 1",
			"volume": 24825,
			"category_id": "ac0fb32ea52f2c1228592ad6598c2cc2"
		    },
		    {
			"keyword": "breaking bad season 5 episode 9",
			"volume": 24825,
			"category_id": "ac0fb32ea52f2c1228592ad6598c2cc2"
		    },
		    {
			"keyword": "project free tv breaking bad",
			"volume": 20325,
			"category_id": "ac0fb32ea52f2c1228592ad6598c2cc2"
		    },
		    {
			"keyword": "watch breaking bad season 5",
			"volume": 20325,
			"category_id": "ac0fb32ea52f2c1228592ad6598c2cc2"
		    },
		    {
			"keyword": "breaking bad review",
			"volume": 16650,
			"category_id": "ac0fb32ea52f2c1228592ad6598c2cc2"
		    },
		    {
			"keyword": "breaking bad season 2",
			"volume": 16650,
			"category_id": "ac0fb32ea52f2c1228592ad6598c2cc2"
		    },
		    {
			"keyword": "breaking bad season 5 episode 10",
			"volume": 16650,
			"category_id": "ac0fb32ea52f2c1228592ad6598c2cc2"
		    },
		    {
			"keyword": "chi hair products",
			"volume": 15125,
			"category_id": "23d817c419aa783121d39d6a0b3ab7f6"
		    },
		    {
			"keyword": "breaking bad episodes",
			"volume": 13575,
			"category_id": "ac0fb32ea52f2c1228592ad6598c2cc2"
		    }
		],
		"categories": {
		    "23d817c419aa783121d39d6a0b3ab7f6": {
			"id": "23d817c419aa783121d39d6a0b3ab7f6",
			"name": "Chi Hair Care Products",
			"path": [
			    "Beauty",
			    "Hair Care",
			    "Hair Care Products",
			    "Chi Hair Care Products"
			]
		    },
		    "ac0fb32ea52f2c1228592ad6598c2cc2": {
			"id": "ac0fb32ea52f2c1228592ad6598c2cc2",
			"name": "Breaking Bad",
			"path": [
			    "Arts & Entertainment",
			    "Movies & Television",
			    "Movie & TV Products",
			    "Breaking Bad"
			]
		    }
		}
	    },
	    "signature": {
		"resource": "GET /categories/map/:keyword",
		"status": "200 OK - successful",
		"client_ip": "127.0.0.1"
	    }
	}
    }


