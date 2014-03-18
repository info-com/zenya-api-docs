List of Available Functions
===========================

Categories
----------

Classify single keywords into the Zenya Taxonomy.

.. csv-table::
    :header: "Method","Resource","Description"
    :stub-columns: 1
    :widths: 10, 30, 100
    
    "GET","categories/map/:keyword","Retrieve a best map Category from the provided keyword."
    "GET","categories/search/:keyword","Retrieve Categories based on a density search of the Zenya Dataset."

Content Classification (beta)
-----------------------------

Classify groups of keywords, HTML, or Tweets into the Zenya Taxonomy.

.. csv-table::
    :header: "Method","Resource","Description"
    :stub-columns: 1
    :widths: 10, 30, 100
    
    "POST","classify/html","Submit HTML code for classification."
    "GET","classify/html/:result_id","Retrieve a classified dataset."
    "POST","classify/keywords","Submit a list of keywords for classification."
    "GET","classify/keywords/:result_id","Retrieve a classified dataset."
    "POST","classify/text","Submit plain text for classification."
    "GET","classify/text/:result_id","Retrieve a classified dataset."
    "POST","classify/tweets","Submit a list of tweets for classification."
    "GET","classify/tweets/:result_id","Retrieve a classified dataset."

Keywords
--------

Retrieve collections of keywords based on executed searches.

.. csv-table::
    :header: "Method","Resource","Description"
    :stub-columns: 1
    :widths: 10, 30, 100
    
    "POST","keywords/search","Execute a search based on provided parameters."
    "GET","keywords/search/:result_id","Retrieve keywords from the specified search."

User Information
----------------

Retrieve basic user and billing cycle information.

.. csv-table::
    :header: "Method","Resource","Description"
    :stub-columns: 1
    :widths: 10, 30, 100
    
    "POST","user/attributes","Return basic information about the current user."
    "GET","user/usage","Retrieve the usage information for the current billing cycle."


