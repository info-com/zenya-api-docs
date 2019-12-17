.. _search-filters:

Keyword Search Filters
======================

.. contents:: Contents
    :local:

There are several filters that may be applied to a number of eContext API calls. Each filter should be
represented as an object with at least two attributes.

:filter: An *integer* value that specifies the filter to apply.
:value: A *mixed* value containing the parameters to pass in to the filter.
:operator: An *integer* value that is *sometimes required* specifies the operator to apply on the ``value``.
:invert: An optional *boolean* value which will invert the filter.  If, for example, you wanted to retrieve only keywords that were about "Tobacco and Cigarettes" you could use the Keyword Flags filter and invert the filter.

Available Filters
-----------------

.. csv-table::
    :header: "ID","Filter Name","Description"
    :widths: 10, 30, 100
    
    "1",":ref:`character_count`","Filter results based on the character length of keywords"
    "2",":ref:`word_count`","Filter results based on the number of words in each keyword"
    "3",":ref:`keyword_flags`","Filter results based on various :ref:`keyword-flags`"
    "5",":ref:`search_volume`","Filter results based on monthly search traffic estimates of keywords"
    "6",":ref:`intent_flags`","Filter results based on textual intent of keywords"
    "7",":ref:`exclude_terms`","Filter out results using the provided terms"
    "8",":ref:`language_flags`","Filter out results based on language"

.. _keyword-flags:

Keyword Flags
-------------

.. csv-table::
    :header: "ID","Flag Name","Description"
    :widths: 10, 30, 100
    
    "1","Invalid","Keyword fails punctuation and composition standards"
    "2","General","Keyword fails general banned standards, including obscene language"
    "4","Adult","Keyword contains adult content"
    "8","Alcohol","Keyword contains content referring to alcohol"
    "16","Fireworks","Keyword contains content referring to fireworks"
    "32","Gambling","Keyword contains content referring to gambling"
    "64","Prescription Drugs","Keyword contains content referring to prescription drugs"
    "128","Tobacco and Cigarettes","Keyword contains content referring to smoking, tobacco, or cigarettes"
    "256","Weapons","Keyword contains content referring to weapons"
    "512","Brands (beta)","Keyword contains content referring to a known brand"
    "1024","Location (beta)","Keyword contains content referring to a known location"

Intent Flags
------------

.. csv-table::
    :header: "ID","Flag Name","Description"
    :widths: 10, 30, 100
    
    "1","Purchase","Keywords related to ""buying"" ideas"
    "2","Comparison","Keyword containing comparison ideas"
    "4","Negative","Keyword containing negative terminologies"
    "8","Question","Keywords expressing questions"
    "16","Coupons","Keywords related to ""coupon"" and ""deal"" ideas"

Operators
---------

.. csv-table::
    :header: "ID","Flag Name","Description"
    :widths: 10, 30, 100

    "0","=","Equal to"
    "1","!=","Not equal to"
    "2","<","Less than"
    "3","<=","Less than or equal to"
    "4",">","Greater than"
    "5",">=","Greater than or equal to"
    "10","\|","Bitwise OR"
    "11","&","Bitwise AND"

Filters
-------

.. _character_count:

Character Count
^^^^^^^^^^^^^^^

The character count filter removes keywords that fall outside of the specified range. The value 
attribute of this filter specifies a character length limit.

Multiple instances of this filter may be passed in order to define customized ranges. An example 
of this filter, shown below, limits character length to between 20-30 characters. 

*The operator attribute is required for this filter.*

Example
"""""""

Filter for character count less than or equal to 30 and greater than or equal to 20.

.. code-block:: javascript
    
    {"filter":1, "value":30, "operator":3}, // less than or equal to 30
    {"filter":1, "value":20, "operator":5}  // greater than or equal to 20

.. _word_count:

Word Count
^^^^^^^^^^

The word count filter removes keywords that fall outside of the specified range.  The value
attribute of this filter specifies a word length limit.

Multiple instances of this filter may be passed in order to define customized ranges.  An example of this filter,
shown below, limits word length to between 4-7 words.

Example
"""""""

.. code-block:: javascript
    
    {"filter":2, "value":4, "operator":5}, // greater than or equal to 4
    {"filter":2, "value":7, "operator":3}  // less than or equal to 7


.. _keyword_flags:

Keyword Flags
^^^^^^^^^^^^^

The keyword flags filter allows a user to selectively filter out flagged keywords.  For example,
you could choose to eliminate most banned keywords (but allow keywords relating to alcohol and
location).

Example
"""""""

Filter out all keywords flagged with the specified keyword flags, except for "alcohol" and "location", identified by
flags 8 and 1024, respectively

.. code-block:: javascript

    {"filter":3, "value":[1, 2, 4, 16, 32, 64, 128, 256, 512]}


.. _search_volume:

Search Volume
^^^^^^^^^^^^^

The search volume filter removes keywords that fall outside the specified range. The value 
attribute of this filter specifies a monthly search traffic limit.

Multiple instances of this filter may be passed in order to define customized ranges. An example 
of this filter, shown below, returns keywords with an estimated monthly search volume of 1,000-
100,000.

*The operator attribute is required for this filter.*

Example
"""""""

.. code-block:: javascript
    
    {"filter":5, "value":100000, "operator":3},  // less than or equal to 100000
    {"filter":5, "value":1000, "operator":5}     // greater than or equal to 1000

.. _intent_flags:

Intent Flags
^^^^^^^^^^^^

The intent filter restricts results to those keywords flagged as belonging to certain intent 
groupings, defined above. A single keyword may contain multiple intent flags. 

Multiple instances of this filter may be passed in order to customize the result set. The example, 
provided below, returns keywords containing the "purchase" and "comparison" intent flags, but 
excluding the "negative" intent flag. Keywords that match this explicit criteria and contain the 
"questions" flag will also be included, as they are not explicitly excluded. Keywords containing 
no intent flags would not be included.

Example
"""""""

.. code-block:: javascript
    
    {"filter":6, "value":[1,2], "operator":11},  // require the purchase and comparison flags
    {"filter":6, "value":[4], "invert":true}     // exclude the negative flag

.. _exclude_terms:

Exclude Terms
^^^^^^^^^^^^^

The exclude terms filter removes keywords containing any of the phrases specified in the filter. 
You may surround a phrase with double-quotes in order to search more precisely, as shown in the
example below.

Please note that using this filter can significantly slow down search times. If you need to enter 
more than a few terms, you will experience better performance and results by refining your 
original query term. 

By setting the invert operator to "true", you can filter to show only those terms containing any of 
the specified words.

Example
"""""""

The example filters out keywords containing the phrases "javascript", "c++", and "php" and also 
filters out keywords containing the exact word (unstemmed) "worlds".

.. code-block:: javascript
    
    {"filter":7, "value":["javascript", "c++", "php", "\"worlds\""]}

.. _language_flags:

Language Flags (beta)
^^^^^^^^^^^^^^^^^^^^^

The language filter restricts results to those keywords flagged as belonging to the specified 
language. Keywords may contain multiple language flags, identified using `ISO 639-2 <http://www.loc.gov/standards/iso639-2/php/code_list.php>`_ 
three character language codes. 

Multiple instances of this filter may be passed in order to customize the result set. The example, 
provided below, returns keywords that are flagged as Spanish. 

Currently, keywords may be flagged as either English or Spanish. Other language offerings will 
be available in the future.

Example
"""""""

.. code-block:: javascript
    
    {"filter":8, "value":["spa"]}  // Require Spanish

Example Requests
----------------

No Filters
^^^^^^^^^^

A simple request with no filters passed.

.. parsed-literal::
    
    curl -X POST -u username:password --data-binary @keywords-search-nofilters.json \\
    --header "Content-type: application/json" :api_url:`keywords/search`

The contents of :download:`@keywords-search-nofilters.json <_static/keywords-search-nofilters.json>`:

.. literalinclude:: _static/keywords-search-nofilters.json
    :language: json

Many Filters
^^^^^^^^^^^^

A more complicated keyword search with many filters.

.. parsed-literal::
    
    curl -X POST -u username:password --data-binary @keywords-search-filters.json \\
    --header "Content-type: application/json" :api_url:`keywords/search`

The contents of :download:`@keywords-search-filters.json <_static/keywords-search-filters.json>`:

.. literalinclude:: _static/keywords-search-filters.json
    :language: json

