User
==========

.. contents:: User Calls
    :local:

GET user/attributes
---------------------------

Return eContext user information including tier depth visibility and user roles.

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
	"econtext": {
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

Return API usage for the current billing cycle.

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

.. literalinclude:: _static/user-usage.json
   :language: json
