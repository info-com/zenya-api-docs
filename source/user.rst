User
==========

.. contents:: User Calls
    :local:

GET user/attributes
---------------------------

Return Zenya user information including tier depth visibility and user roles.

Resource URL
^^^^^^^^^^^^
:api_url:`user/attributes`

Example Request
^^^^^^^^^^^^^^^

GET Request
"""""""""""

.. parsed-literal::

    curl -X GET -u username:password :api_url:`user/attributes`

GET Response
""""""""""""

.. code-block:: json
    
    {
	"zenya": {
	    "user": {
		"attributes": {
		    "username": "31bc9229f61ebfa4782036bda7bd6acb",
		    "group": "regular",
		    "tier_depth": 4
		}
	    },
	    "signature": {
		"resource": "GET /categories/map/:keyword",
		"status": "200 OK - successful",
		"client_ip": "127.0.0.1"
	    }
	}
    }

GET user/usage
--------------

Return API credit usage for the current billing cycle.  The data returned by this call is not "live" but updated daily.

Resource URL
^^^^^^^^^^^^
:api_url:`user/usage`

Example Request
^^^^^^^^^^^^^^^

GET Request
"""""""""""

.. parsed-literal::

    curl -X GET -u username:password :api_url:`user/usage`

GET Response
""""""""""""

.. code-block:: json
    
    {
	"zenya": {
	    "user": {
		"usage": {
		    "currency_spent": 1.31,
		    "credits_used": 5224,
		    "date_start": "2014-03-12",
		    "date_end": "2014-04-12"
		}
	    },
	    "signature": {
		"resource": "GET /categories/map/:keyword",
		"status": "200 OK - successful",
		"client_ip": "127.0.0.1"
	    }
	}
    }
