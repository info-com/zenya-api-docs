.. _custom-taxonomies:

Custom Taxonomies
=================

.. contents:: Custom Taxonomies
    :local:

You can use our taxonomy engine to run against a much smaller custom taxonomy that you create and control directly.


GET /user/taxonomies
--------------------

Retrieve a list of publicly available taxonomies and private custom taxonomies

Resource URL
^^^^^^^^^^^^

:api_url:`user/taxonomies`

Example Request
^^^^^^^^^^^^^^^

GET Request
"""""""""""

.. parsed-literal::

    curl -X GET -u username:password :api_url:`user/taxonomies`

GET Response
""""""""""""

.. code-block:: json

    {
      "econtext": {
        "user": {
          "private": {
            "Colors": "604962c585d0bbf9724d03110effbe64f6289bd04fa3d65da4b03dfc06d0ddf5"
          },
          "public": []
        },
        "signature": {
          "resource": "GET /user/taxonomies",
          "status": "200 OK - successful",
          "client_ip": "127.0.0.1"
        }
      }
    }


POST /user/taxonomy
-------------------

Create a new taxonomy in the eContext system that can be used to classify content.  The data structure used to create
the taxonomy is a hierarchically organized list of node objects.  Each node object contains a "name"; a "positive_vocabs"
list; a "negative_vocabs" list; and "nodes", a list of node objects that are children of the current node object.

Resource URL
^^^^^^^^^^^^
:api_url:`user/taxonomy`

Parameters
^^^^^^^^^^

.. csv-table::
    :header: "Parameter","Type","Description"
    :widths: 25, 20, 100

    "name (*required*)", "string", "A name used to identify your taxonomy"
    "nodes (*required*)", "array", "A nested array containing the taxonomy structure to create"
    "public", "boolean", "Create a publicly available taxonomy (admin only)"

Return
^^^^^^

The result will return a `dataset_id` which is a globally unique identifier for the new taxonomy.

Example Request
^^^^^^^^^^^^^^^

Create a new "Colors" taxonomy that can then be used in classification tasks.

POST Request
""""""""""""

.. parsed-literal::

    curl -X POST -u username:password --data-binary @user-taxonomy-input.json \\
    --header "Content-type: application/json" \\
    :api_url:`user/taxonomy`

The contents of :download:`user-taxonomy-input.json <_static/user-taxonomy-input.json>`:

.. literalinclude:: _static/user-taxonomy-input.json
    :language: json


POST Response
"""""""""""""

.. literalinclude:: _static/user-taxonomy-output.json
   :language: json


GET /user/taxonomy
------------------

Retrieve a stored taxonomy

Resource URL
^^^^^^^^^^^^

:api_url:`user/taxonomy/:dataset_id`

Parameters
^^^^^^^^^^

.. csv-table::
    :header: "Parameter","Type","Description"
    :widths: 25, 20, 100

    "dataset_id (*required*)", "string", "A globally unique custom taxonomy identifier"

Example Request
^^^^^^^^^^^^^^^

GET Request
"""""""""""

.. parsed-literal::

    curl -X GET -u username:password :api_url:`user/taxonomy/604962c585d0bbf9724d03110effbe64f6289bd04fa3d65da4b03dfc06d0ddf5`

GET Response
""""""""""""

.. literalinclude:: _static/user-taxonomy-dataset_id.json
   :language: json


DELETE /user/taxonomy/:dataset_id
---------------------------------

Remove a custom taxonomy from the eContext API

Resource URL
^^^^^^^^^^^^

:api_url:`user/taxonomy/:dataset_id`

Parameters
^^^^^^^^^^

.. csv-table::
    :header: "Parameter","Type","Description"
    :widths: 25, 20, 100

    "dataset_id (*required*)", "string", "A globally unique custom taxonomy identifier"

Example Request
^^^^^^^^^^^^^^^

DELETE Request
""""""""""""""

.. parsed-literal::

    curl -X DELETE -u username:password :api_url:`user/taxonomy/604962c585d0bbf9724d03110effbe64f6289bd04fa3d65da4b03dfc06d0ddf5`

DELETE Response
"""""""""""""""

.. code-block:: json

    {
      "econtext": {
        "user": {
          "result": true
        },
        "signature": {
          "resource": "DELETE /user/taxonomy/:dataset_id",
          "status": "200 OK - successful",
          "client_ip": "127.0.0.1"
        }
      }
    }
