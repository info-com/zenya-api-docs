Objects
=======

.. contents:: Contents
    :local:

Category
--------

A Category is the base classification object in the eContext platform.  A 
typical Category will contain an id, name, and the path (and ids) in the
eContext Taxonomy.

Each Category exists in exactly one location in the eContext Taxonomy and has 
only one parent. Categories may move, periodically, in the eContext Taxonomy, 
and their names and path values may change. A Category will always keep the same
id. A Category may represent a thing, place, person, product, service, or an
abstract concept.

.. code-block:: json
    
    {
      "id": "ac0fb32ea52f2c1228592ad6598c2cc2",
      "name": "Breaking Bad",
      "path": [
        "Arts & Entertainment",
        "Movies & Television",
        "Movie & TV Products",
        "TV",
        "Drama TV Shows",
        "Breaking Bad"
      ],
      "idpath": [
        "0cc9e1516aaa38d4802a2ee5314ac4ab",
        "06b7167107de9cff93e6738da9c044c4",
        "8e4e953b861d4597cb5fae3b7de67ce5",
        "b3728edb10af57dfbd941132f0c932ae",
        "153fd544b9063cfdbe86aaf1b04882b4",
        "ac0fb32ea52f2c1228592ad6598c2cc2"
      ],
      "stats": {
        "social_idf": 21067.359562841,
        "social_relevance": 0.0000381826
      }
    }

.. csv-table::
    :header: "Attribute","Description"
    :stub-columns: 1
    :widths: 25, 100
    
    "id", "A unique identifier for this Category. Please note that ids are encoded to each account, and the ids shown in these examples will not be the same as those received from the service"
    "name", "The name of this Category"
    "path", "The path for this Category in the eContext Taxonomy"
    "idpath", "The path for this Category using ids"
    "stats", "Useful statistics associated with this Category"
    "stats.social_idf", "The Inverse Document Frequency of this Category.  See below for more details"
    "stats.social_relevance", "The percentage of conversations found in eContext's Social Media feeds over the past month that address this specific Category. This statistic only applies to the single category object, and does not aggregate or sum categories deeper in its hierarchical path"


stats.social_idf
^^^^^^^^^^^^^^^^

This statistic provides partial data for computing TF-IDF for categories in the
Social space.  Social IDF is calculated from conversations compiled from eContext's feeds
of Social Media data over the past month.  The provided number is calculated as follows:

.. math::
    {idf}(t, D) =  \log \frac{N}{|\{d \in D: t \in d\}|}

Where:

* :math:`N` = Total number of documents in the corpus
* :math:`|\{d \in D: t \in d\}|` = number of documents where the Category `t` appears

Please note that in this context, a term is a Category, not a lexeme, but can be
useful for removing Category noise from your results.


stats.social_relevance
^^^^^^^^^^^^^^^^^^^^^^

This statistic provides information about the relevance of a particular category
in in eContext's Social Media feeds over the past month and is calculated as follows:

.. math::
    {relevance}(t, D) = \frac{|\{d \in D: t \in d\}|}{C}

Where:

* :math:`|\{d \in D: t \in d\}|` = number of documents where the Category `t` appears
* :math:`C` = Sum of all categories found in each document the corpus

Overlay
-------

An overlay object provides a map from the eContext taxonomy to a client's own
taxonomy, and/or a standard taxonomy overlay, for example, to the IAB taxonomy.
Overlays are only available to select clients at this time.  Please contact
our `Overlay Team`_ for access to standard taxonomy overlays or for 
information about onboarding your own taxonomy overlay.

In general, the overlay object itself will contain a dictionary of eContext
category ids that correspond to the categories dictionary, and then matching
categories inside each subscribed taxonomy overlay.

For example, if a user is subscribed to the IAB taxonomy overlay, the output for
the following `classify/keywords` call might look like this:

.. code-block:: bash

    curl -X POST -H "Authorization: Basic __AUTHENTICATION__" -H "Content-Type: application/json" -d '{
        "async":false,
        "keywords":[
          "baby strollers",
          "chicago bears"
        ]
    }' "https://api.econtext.com/v2/classify/keywords"

.. code-block:: json

    {
      "econtext": {
        "classify": {
          "mappings": [
            "33ffa2f8cae5b84455321ab2575441fe",
            "85edc49558d9373a4a5bcfc6eb0bac90"
          ],
          "categories": {
            "33ffa2f8cae5b84455321ab2575441fe": {
              "id": "33ffa2f8cae5b84455321ab2575441fe",
              "name": "Strollers",
              "path": [
                "Home & Garden",
                "Baby Needs",
                "Baby Products",
                "Baby Travel Products",
                "Baby Strollers & Carriages",
                "Strollers"
              ],
              "idpath": [
                "0b1cfd1a5102a974a372e9bc3cfffb35",
                "5eae0deb470fb00144d9a73160dc81f4",
                "e142965050c94732a5044303907523f6",
                "20b3458f5d86613bd46b967a6832bce5",
                "83b0847bd055decd09c623c6c451014e",
                "33ffa2f8cae5b84455321ab2575441fe"
              ],
              "stats": {
                "social_relevance": 0.0000055254,
                "social_idf": 12.019372309892
              }
            },
            "85edc49558d9373a4a5bcfc6eb0bac90": {
              "id": "85edc49558d9373a4a5bcfc6eb0bac90",
              "name": "Chicago Bears",
              "path": [
                "Sports",
                "Team Sports",
                "Football",
                "Football Leagues & Teams",
                "Professional Football Leagues & Teams",
                "NFL",
                "National Football Conference",
                "National Football Conference - North Division",
                "Chicago Bears"
              ],
              "idpath": [
                "b00fac5f30dc8dbb660c8d08fe66f487",
                "97e2d582fd4e9fe6c9ca51128222e55f",
                "1d86d6fea65150be10232959abc02574",
                "9398300d477069715ad4682b293fb087",
                "04455c6d36d1056a7be0b231e861c0c5",
                "f3fafece413cb4e87975d12457ddb9a1",
                "4f2d7f778d65a60d35cc53fff475e84f",
                "7680bb6c2b3e6babe7bfcc7c44fd752b",
                "85edc49558d9373a4a5bcfc6eb0bac90"
              ],
              "stats": {
                "social_relevance": 0.0000065315,
                "social_idf": 11.852088630462
              }
            }
          },
          "overlay": {
            "33ffa2f8cae5b84455321ab2575441fe": {
              "iab2016": [
                [
                  "Home & Garden"
                ],
                [
                  "Family & Parenting",
                  "Babies & Toddlers"
                ]
              ]
            },
            "85edc49558d9373a4a5bcfc6eb0bac90": {
              "iab2016": [
                [
                  "Sports"
                ],
                [
                  "Sports",
                  "Football"
                ]
              ]
            }
          }
        },
        "signature": {
          "resource": "POST /classify/:type/:result_id",
          "status": "200 OK - successful",
          "client_ip": "127.0.0.1"
        }
      }
    }

In this case, we're returning categories from the eContext 2015 IAB Taxonomy 
Overlay that maps from eContext categories to the IAB.  The eContext "Strollers"
category maps to the IAB "Home & Garden" and "Babies & Toddlers" categories, and
the eContext "Chicago Bears" category maps to the IAB "Sports" and "Football"
categories.

Please note that the overlay object will not appear for categories/map or 
categories/search calls.

Entities
--------

In certain cases, the eContext Taxonomy may not return as many classifications 
as you may like.  For example, eContext may not return many location names or
the names of people mentioned in a social media post or article.  In these cases
you may specifically request additional entities to be returned.  Please note
that the addition of named entity parsing does increase latency.

Entity extraction is provided for the classify/social, classify/html, 
classify/text, and classify/url calls and can be enabled by passing in an 
additional parameter with your request object.  For example, to retrieve extra
entities in a classify/social call you may pass in ``"entities":true`` as shown
in the following example:
    
.. literalinclude:: _static/classify-social-input.json
    :language: json

Available entities types:
^^^^^^^^^^^^^^^^^^^^^^^^^

.. csv-table:: 
    :header: "Entity", "Description"
    :stub-columns: 1
    
    "PERSON","Names of people"
    "NORP","Nationalities or religious and political groups"
    "FAC","Facilities"
    "ORG","Organizations"
    "GPE","Geo-political entities"
    "LOC","Locations that are not GPEs"
    "PRODUCT","Products"
    "EVENT","Events"
    "WORK_OF_ART","Titles of works of art including music, books, paintings, etc"
    "LAW","Laws and legal documents"
    "LANGUAGE","Names of Languages"

.. _objects-flags:

Object Flags
------------

There are many scenarios where you may want to be able to filter content on the
fly.  Along with classification of content, eContext is able to quickly identify
and flag social media posts and keywords for content that may be unsuitable for
your audiences.  Please note that the addition of content flagging does increase
latency.

Social media posts and keywords may be flagged in real-time to the following
categories and can be triggered, as shown above, by passing in ``"flags":true``
in your request object:

.. csv-table::
    :header: "ID","Flag Name","Description"
    :stub-columns: 1
    :widths: 10, 30, 100
    
    "2","General","Keyword fails general banned standards, including obscene language"
    "4","Adult","Keyword contains adult content"
    "8","Alcohol","Keyword contains content referring to alcohol"
    "16","Fireworks","Keyword contains content referring to fireworks"
    "32","Gambling","Keyword contains content referring to gambling"
    "64","Prescription Drugs","Keyword contains content referring to prescription drugs"
    "128","Tobacco and Cigarettes","Keyword contains content referring to smoking, tobacco, or cigarettes"
    "256","Weapons","Keyword contains content referring to weapons"
    "2048","Intent","Keyword contains either a purchase, comparison, question, or negative intent"


.. _Overlay Team: overlayteam@econtext.com

