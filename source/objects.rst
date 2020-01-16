Objects
=======

.. contents:: Contents
    :local:

Category
--------

A Category is the base classification object in the eContext platform.  A
typical Category will contain an id, a name, a path where the Category resides in the eContext Taxonomy, and the ids of each element in that path.

Each Category exists in exactly one location in the eContext Taxonomy and has
only one parent. Categories may be altered over time, the content classified to them may differ, and their name, path, and idpath values may change. However, a Category will always keep the same id. A Category may represent a thing, place, person, product, service, or an abstract concept.

.. code-block:: json

    {
      "id": "d974b27c85b666e371d1a2f5d50d5d48",
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
         "90a7a21c5fe42569fb5bb0d28ce9f77a",
         "7dde2749bbff96f9c111a50d8dd12fd8",
         "c4d86afd19597a9bd040fee32df9b318",
         "74c4ca4f7550a6267e1c0d1b5552465c",
         "fe88b63f0fdb129d97fe996c05d3ebf1",
         "d974b27c85b666e371d1a2f5d50d5d48"
      ],
      "stats": {
         "social_relevance": 0.0000432244,
         "social_idf": 9.8314479757,
         "commercial_score": 0.3
      },
      "facets": [
         [
             "domain",
             "product"
         ],
         [
             "brand",
             "breaking bad"
         ]
      ]
    }

.. csv-table::
    :header: "Attribute","Description"
    :widths: 25, 100

    "id", "A unique identifier for this Category. Please note that ids are encoded to each account, and the ids shown in these examples will not be the same as those received from the service"
    "name", "The name of this Category"
    "path", "The path for this Category in the eContext Taxonomy"
    "idpath", "The path for this Category using ids"
    "stats", "Useful statistics associated with this Category"
    "stats.social_relevance", "The percentage of conversations found in eContext's Social Media feeds over the past month that address this specific Category. This statistic only applies to the single Category object, and does not aggregate or sum categories deeper in its hierarchical path"
    "stats.social_idf", "The Inverse Document Frequency of this Category.  See below for more details"
    "commercial_score", "A value (0.0 - 1.0) representing the competition and cost of digital advertising around the category topic"
    "facets", "A list of values describing aspects of the category. See below for examples of response values"


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

This statistic provides information about the relevance of a particular Category
in in eContext's Social Media feeds over the past month and is calculated as follows:

.. math::
    {relevance}(t, D) = \frac{|\{d \in D: t \in d\}|}{C}

Where:

* :math:`|\{d \in D: t \in d\}|` = number of documents where the Category `t` appears
* :math:`C` = Sum of all categories found in each document the corpus

Facets
^^^^^^

Facets add detail to the nature of a category topic, and can be useful for organizing classifications across different paths and verticals. 

For example, linking categories for the Brand "Honda", whether they appear in "Home & Garden" (Honda Lawn Mowers) or "Vehicles" (Honda Accord).

Below are some examples of possible values pairs returned in the Facets list. Additional Facet Types will be released in future versions.

.. csv-table::
    :header: "Facet Type","Example Facet Value/s","Description"
    :widths: 30, 40, 70

    "Domain","Product, Service, Facility, Information","A broad class describing if a category is a commercial item or piece of IP; an action or practice; a place; or an abstract concept"
    "Brand","Apple, Honda, et al","The brand name associated with a category. May also be the name of a Person or piece of intellectual property (like a film series or TV show)"
    "Product Line", "iPhone, Accord, et al", "A distinguishing name given to a set of items or services offered by a Brand"
    

Overlay
-------

An overlay object provides a map from the eContext taxonomy to a client's own
taxonomy, and/or an industry standard taxonomy, like the IAB Content Taxonomy.
Overlays are only available to select clients at this time.  Please contact
our `Client Services Team`_ to learn more about the standard overlays we support, or commission a custom overlay.

In general, the overlay object itself will contain a dictionary of eContext
Category ids that correspond to the categories dictionary, and then matching
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
              "IAB_v2.0_2018": [
                [
                  [
                    "274",
                    "Home & Garden"
                  ]
                ],
                [
                  [
                    "196",
                    "Family and Relationships::Parenting::Parenting Babies and Toddlers"
                  ]
                ]
              ]
            },
            "85edc49558d9373a4a5bcfc6eb0bac90": {
              "IAB_v2.0_2018": [
                [
                  [
                    "483",
                    "Sports"
                  ],
                ],
                [
                  [
                    "484",
                    "Sports::American Football"
                  ]
                ]
              ],
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

In this case, we're returning categories from the eContext 2018 IAB Taxonomy
Overlay that maps from eContext categories to the IAB.  The eContext "Strollers"
Category maps to the IAB "Home & Garden" and "Parenting Babies and Toddlers" categories, and the eContext "Chicago Bears" Category maps to the IAB "Sports" and "American Football" categories.

Please note that the overlay object will not appear for categories/map or
categories/search calls.

Entities
--------

In addition to topics from its curated hierarchy, eContext can also use Named Entity Recognition (NER) to return additional information on a document.

Please note that the addition of Named Entity Recognition does increase latency.

Entity recognition is provided for the classify/social, classify/html,
classify/text, and classify/url calls and can be enabled by passing in an
additional parameter with your request object.  For example, to retrieve
Entities in a classify/social call you may pass in ``"entities":true`` as shown
in the following example:

.. literalinclude:: _static/classify-social-input.json
    :language: json

For each item classified, its recognized ``entities`` will be returned in a separate list from ``scored_categories``. Entity ids can be referenced in the ``categories`` dictionary to lookup their names, paths, and idpaths. In some cases, one or more of the recognized entities may be synonymous with a Category, and the id for the category will be included in the ``entities`` list, along with an Entity type.

Available Entity types:
^^^^^^^^^^^^^^^^^^^^^^^^^

.. csv-table::
    :header: "Entity","Description"
    :widths: 40, 100

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

eContext's Entity recognition should resolve multiple occurances or references of the same Entity in a document into a single entry. For some location Entities, eContext may provide additional levels of detail by referencing the Entity against a custom gazetteer.

.. _objects-flags:

Object Flags
------------

Along with classification of content, eContext is able to identify
and flag social media posts and keywords for content that may be unsuitable for
your audiences.  Please note that the addition of content flagging does increase
latency.

Social media posts and keywords may be flagged in real-time to the following
categories and can be triggered by passing in ``"flags":true``
in your request object.

eContext offers the following flagging categories. Be advised that these flags are optimized for keyword search & display, and are engineered to over-flag in cases of ambiguity.

.. csv-table::
    :header: "ID","Flag Name","Description"
    :widths: 10, 30, 100

    "2","General","Text fails general standards, including obscene language"
    "4","Adult","Text contains adult content"
    "8","Alcohol","Text contains content referring to alcohol"
    "16","Fireworks","Text contains content referring to fireworks"
    "32","Gambling","Text contains content referring to gambling"
    "64","Prescription Drugs","Text contains content referring to prescription drugs"
    "128","Tobacco and Cigarettes","Text contains content referring to smoking, tobacco, or cigarettes"
    "256","Weapons","Text contains content referring to weapons"
    "2048","Intent","Text contains either a purchase, comparison, question, or negative intent"


.. _Client Services Team: hello@econtext.ai
