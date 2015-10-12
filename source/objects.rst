Objects
=======

.. contents:: Category
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
        "social_df": 0.0000381826
      }
    }

.. csv-table::
    :header: "Attribute","Description"
    :stub-columns: 1
    :widths: 25, 100
    
    "id", "A unique identifier for this Category"
    "name", "The name of this Category"
    "path", "The path for this Category in the eContext Taxonomy"
    "idpath", "The path for this Category using ids"
    "stats", "Useful statistics associated with this Category"
    "stats.social_idf", "The Inverse Document Frequency of this Category.  See below for more details."
    "stats.social_df", "The percentage of conversations in Social over the past month that address this specific Category"


stats.social_df
^^^^^^^^^^^^^^^

This statistic provides information about the relevance of a particular category
in Social over the past month and is calculated as follows:

.. math::
    {df}(t, D) = \frac{|\{d \in D: t \in d\}|}{N}

Where:

* :math:`N` = Total number of documents in the corpus
* :math:`|\{d \in D: t \in d\}|` = number of documents where the Category `t` appears


stats.social_idf
^^^^^^^^^^^^^^^^

This statistic provides partial data for computing TF-IDF for categories in the
Social space.  Social IDF is calculated from conversations compiled from
Social Data over the past month.  The provided number is calculated as follows:

.. math::
    {idf}(t, D) =  \log \frac{N}{|\{d \in D: t \in d\}|}

Where:

* :math:`N` = Total number of documents in the corpus
* :math:`|\{d \in D: t \in d\}|` = number of documents where the Category `t` appears

Please note that in this context, a term is a Category, not a lexeme, but can be
useful for removing Category noise from your results.
