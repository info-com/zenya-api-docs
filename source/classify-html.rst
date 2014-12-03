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

.. code-block:: json
    
    {
	"econtext": {
	    "classify": {
		"title": "Microsoft Stores offer $100 Xbox One discount if you trade in a PS3",
		"scored_categories": [
		    {
			"category_id": "69426ba5f3037acc424187e29a26391d",
			"score": 58
		    },
		    {
			"category_id": "93dadcfdf6f5e16904c5390975df4509",
			"score": 34
		    },
		    {
			"category_id": "2513798803bdfb6216a33be0251c200f",
			"score": 34
		    },
		    {
			"category_id": "2e2a08cf1ae055f11496a2585a254beb",
			"score": 28
		    },
		    {
			"category_id": "9fc965e17d7fa1eddac9938062c71b2d",
			"score": 28
		    },
		    {
			"category_id": "46e2413b704c67d817ce601f4a9e675d",
			"score": 8
		    },
		    {
			"category_id": "e318c16a62207da2f9545ff033f63e4e",
			"score": 6
		    },
		    {
			"category_id": "d79362632d5f0a8886128aa4729359a0",
			"score": 4
		    },
		    {
			"category_id": "c6ca93d64aa02a41ca440a3987ddfb27",
			"score": 2
		    },
		    {
			"category_id": "56410b3fd387574f8da8d2d674089c35",
			"score": 2
		    }
		],
		"scored_keywords": [
		    {
			"keyword": "a ps3",
			"score": 28
		    },
		    {
			"keyword": "you trade",
			"score": 28
		    },
		    {
			"keyword": "xbox one discount",
			"score": 24
		    },
		    {
			"keyword": "microsoft stores offer",
			"score": 24
		    },
		    {
			"keyword": "the ps4",
			"score": 6
		    },
		    {
			"keyword": "microsoft",
			"score": 6
		    },
		    {
			"keyword": "the xbox one",
			"score": 6
		    },
		    {
			"keyword": "order",
			"score": 6
		    },
		    {
			"keyword": "terms",
			"score": 4
		    },
		    {
			"keyword": "xbox 360 e",
			"score": 4
		    },
		    {
			"keyword": "little",
			"score": 4
		    },
		    {
			"keyword": "microsoft stores",
			"score": 4
		    },
		    {
			"keyword": "course",
			"score": 4
		    },
		    {
			"keyword": "the price difference",
			"score": 4
		    },
		    {
			"keyword": "xbox 360 s",
			"score": 4
		    },
		    {
			"keyword": "march 2",
			"score": 4
		    },
		    {
			"keyword": "store credit",
			"score": 4
		    },
		    {
			"keyword": "a number",
			"score": 4
		    },
		    {
			"keyword": "one advantage",
			"score": 4
		    },
		    {
			"keyword": "conditions",
			"score": 4
		    },
		    {
			"keyword": "the same time",
			"score": 2
		    },
		    {
			"keyword": "the console",
			"score": 2
		    },
		    {
			"keyword": "every console",
			"score": 2
		    },
		    {
			"keyword": "a big loss",
			"score": 2
		    },
		    {
			"keyword": "the price",
			"score": 2
		    },
		    {
			"keyword": "you an xbox one",
			"score": 2
		    },
		    {
			"keyword": "an xbox one",
			"score": 2
		    },
		    {
			"keyword": "your old machine",
			"score": 2
		    },
		    {
			"keyword": "its original accessories",
			"score": 2
		    },
		    {
			"keyword": "the power supply",
			"score": 2
		    },
		    {
			"keyword": "a way",
			"score": 2
		    }
		],
		"categories": {
		    "93dadcfdf6f5e16904c5390975df4509": {
			"id": "93dadcfdf6f5e16904c5390975df4509",
			"name": "Microsoft",
			"path": [
			    "Computers & Electronics",
			    "Computers & Electronics Brands [List]",
			    "Microsoft"
			]
		    },
		    "2e2a08cf1ae055f11496a2585a254beb": {
			"id": "2e2a08cf1ae055f11496a2585a254beb",
			"name": "Microsoft Stores",
			"path": [
			    "Computers & Electronics",
			    "General Electronics",
			    "General Electronics Retailers [List]",
			    "Microsoft Stores"
			]
		    },
		    "e318c16a62207da2f9545ff033f63e4e": {
			"id": "e318c16a62207da2f9545ff033f63e4e",
			"name": "PlayStation 4 Game Systems",
			"path": [
			    "Computers & Electronics",
			    "Video Game Electronics",
			    "Video Game Electronics Products",
			    "PlayStation 4 Game Systems"
			]
		    },
		    "46e2413b704c67d817ce601f4a9e675d": {
			"id": "46e2413b704c67d817ce601f4a9e675d",
			"name": "Xbox 360 Game Systems",
			"path": [
			    "Computers & Electronics",
			    "Video Game Electronics",
			    "Video Game Electronics Products",
			    "Xbox 360 Game Systems"
			]
		    },
		    "d79362632d5f0a8886128aa4729359a0": {
			"id": "d79362632d5f0a8886128aa4729359a0",
			"name": "Credit & Lending",
			"path": [
			    "Finance",
			    "Credit & Lending"
			]
		    },
		    "c6ca93d64aa02a41ca440a3987ddfb27": {
			"id": "c6ca93d64aa02a41ca440a3987ddfb27",
			"name": "Accessories",
			"path": [
			    "Apparel",
			    "Accessories"
			]
		    },
		    "2513798803bdfb6216a33be0251c200f": {
			"id": "2513798803bdfb6216a33be0251c200f",
			"name": "Xbox One Game Systems",
			"path": [
			    "Computers & Electronics",
			    "Video Game Electronics",
			    "Video Game Electronics Products",
			    "Xbox One Game Systems"
			]
		    },
		    "9fc965e17d7fa1eddac9938062c71b2d": {
			"id": "9fc965e17d7fa1eddac9938062c71b2d",
			"name": "PlayStation 3 Game Systems",
			"path": [
			    "Computers & Electronics",
			    "Video Game Electronics",
			    "Video Game Electronics Products",
			    "PlayStation 3 Game Systems"
			]
		    },
		    "69426ba5f3037acc424187e29a26391d": {
			"id": "69426ba5f3037acc424187e29a26391d",
			"name": "Original Xbox Game Systems",
			"path": [
			    "Computers & Electronics",
			    "Video Game Electronics",
			    "Video Game Electronics Products",
			    "Original Xbox Game Systems"
			]
		    },
		    "56410b3fd387574f8da8d2d674089c35": {
			"id": "56410b3fd387574f8da8d2d674089c35",
			"name": "Power Supplies",
			"path": [
			    "Computers & Electronics",
			    "General Electronics",
			    "General Electronics Products",
			    "Power Supplies"
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
