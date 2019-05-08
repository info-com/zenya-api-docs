List of Available Functions
===========================

NLP
----------

Perform Natural Language Processing functions against text strings and documents.

.. csv-table::
    :header: "Method","Resource","Description"
    :stub-columns: 1
    :widths: 10, 30, 100

    "POST","nlp/parse","Performs Part of Speech (POS) tagging, Named Entity Recognition (NER), dependency parsing, tokenization, sentiment analysis, and other core functions of the eContext NLP stack."
    "POST","nlp/lid","Identify the language of some text input."

Categories
----------

Classify single keywords into the eContext Taxonomy.

.. csv-table::
    :header: "Method","Resource","Description"
    :stub-columns: 1
    :widths: 10, 30, 100

    "GET","categories/tiers","Retrieve top tier Categories from the eContext Taxonomy."
    "GET","categories/map/:keyword","Retrieve a best map Category from the provided keyword based on the eContext knowledge set."
    "GET","categories/search/:keyword","Retrieve a set of possible Categories from the provided keyword based on comparing the keyword with pre-classified keywords in the eContext Dataset."

Content Classification
----------------------

Classify long-form text context, short-form text content (including social media), the content from URLs or HTML, or lists of keywords into the eContext Taxonomy.

.. csv-table::
    :header: "Method","Resource","Description"
    :stub-columns: 1
    :widths: 10, 30, 100

    "POST","classify/text","Submit plain text for classification."
    "GET","classify/text/:result_id","Retrieve a classified dataset."
    "POST","classify/social","Submit a list of social posts for classification."
    "GET","classify/social/:result_id","Retrieve a classified dataset."
    "POST","classify/url","Submit a url to be retrieved and classified."
    "GET","classify/url/:result_id","Retrieve a classified dataset."
    "POST","classify/html","Submit HTML code for classification."
    "GET","classify/html/:result_id","Retrieve a classified dataset."
    "POST","classify/keywords","Submit a list of keywords for classification."
    "GET","classify/keywords/:result_id","Retrieve a classified dataset."
  

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

    "GET","user/attributes","Return basic information about the current user."
    "GET","user/usage","Retrieve the usage information for the current billing cycle."
    "GET","user/taxonomies","Retrieve a list of public and privately available taxonomies."
    "POST","user/taxonomy","Create a custom taxonomy for use in classification tasks."
    "GET","user/taxonomy/:dataset_id","Retrieve a customized taxonomy."
    "DELETE","user/taxonomy/:dataset_id","Delete a customized taxonomy."
