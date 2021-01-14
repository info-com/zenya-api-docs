Changelog
=========


Version 1.2.17 - 2021-01-14
---------------------------
* Added a POST /categories/categories call to retrieve category and overlay information given a list of category ids


Version 1.2.16 - 2020-08-04
---------------------------
* Added an `add_last_node` parameter to classification calls
* Added a `classify_limit` parameter to classification calls to limit the number of category responses


Version 1.2.15 - 2020-06-16
---------------------------
* Minor bug fixes and performance improvements


Version 1.2.14 - 2020-03-26
---------------------------
* Added a `classify_timeout` parameter to classifiation calls. We can limit the amount of time we'll spend on a single call. When the timeout is reached, results computed up to that point will be returned.
* Performance tuning


Version 1.2.13 - 2020-02-04
---------------------------
* Minor bug fixes and performance improvements


Version 1.2.12 - 2020-01-23
---------------------------
* Minor bug fixes and performance improvements


Version 1.2.11 - 2019-12-12
---------------------------
*  Add an ``ml_threshold`` parameter to control machine learning results during classification. Setting this value lower will result in higher recall, but lower precision.
*  ``async`` is dropped as an option during classification calls. All classification calls will now return results in the body of the response object rather than allowing for retrieval later.


Version 1.2.10 - 2019-08-14
---------------------------
*  Cache the HTML from URL classification to prevent recrawling the same URL if it is seen within a certain period of time. You can force a recrawl by passing in ``cache_skip: true`` in your POST data.


Version 1.2.9 - 2019-07-01
--------------------------
*  Bug fixes
*  Performance enhancements


Version 1.2.8 - 2019-04-10
--------------------------
*  Bug fix for URL classification - all non-200 responses for individually submitted URLs to the API will return a 400.
*  Specify a min_tags parameter in classify/url to fallback to a different extraction engine if not enough content is retrieved
*  Expose a `user/allotments` call to show usage limits if applicable
*  Bug fix where sometimes overlay output format was incorrect

Version 1.2.7 - 2019-03-05
--------------------------
*  Introduction of Facets to Category objects.  Facets can be used to help identify things like brands and products and makes our Categories a little bit richer.


Version 1.2.6 - 2019-01-08
--------------------------
*   Significant changes to the eContext sentiment models as well as significant performance enhancement.  Quickly retrieve sentiment on classification calls.
*   New NLP features - language identification for URLs and other input text.  Available now at ``/v2/nlp/lid``


Version 1.2.5 - 2018-10-25
--------------------------
*   Added Sentiment to most classification calls.  Generally, simply add a ``"sentiment": true`` parameter to the request body.
*   Added NLP parsing functions to the API at ``/v2/nlp/parse`` which performs POS tagging, NER, dependency parsing, entity extraction, etc.  Parsing is currently limited to select users.  Please contact eContext.ai if you're interested in accessing these functions.


Version 1.2.0 - 2018-05-10
--------------------------
*   Include new multi-lingual support :ref:`language-support`
*   Improved the efficiency for :ref:`custom-taxonomies`
*   Increased performance of the classification engine to provide greater detail and insight into classifications

Version 1.1.6 - 2017-03-16
--------------------------
*   Several performance enhancements and bug fixes
*   Changed error handling on ``classify/url`` to be a bit more robust
*   Add client-controlled :ref:`custom-taxonomies` that can be used by the classification engine in lieu of the default eContext taxonomy

Version 1.1.5 - 2017-02-02
--------------------------
*   Specify a ``taxonomy_timestamp`` parameter to freeze the eContext Taxonomy for long-running classification tasks
*   Return more useful errors for invalid filters in ``keywords/search`` calls

Version 1.1.4 - 2017-01-16
--------------------------
*   Added ``scored_keywords`` entries for items classified in ML Classification results
*   Fixed bug where ``classify/url`` would fail if there was a new-line character in the input
*   Significant expansion and updates to internal keyword models

Version 1.1.3 - 2016-11-11
--------------------------
*   Better recognition of duplicate entity categories, particularly names in ML Classification results

Version 1.1.2 - 2016-09-29
--------------------------
*   Added usage limits to assist users in keeping to API usage quotas
*   Integrated entity categories into the main ``categories`` object in response objects

Version 1.1.1 - 2016-08-16
--------------------------
*   Specify a ``branches`` parameter when classifying keywords to restrict to a particular vertical
*   Specify a ``best_match`` parameter (defaults to ``true``) to classify/social, classify/html, classify/url, and classify/text calls which will force the engine to retain submatches instead of removing them from results
*   Added the ability to create custom taxonomies that users may use for specific classification tasks

Version 1.1.0 - 2016-07-11
--------------------------
*   Added fallback NLP Entity extraction options in cases where the eContext Taxonomy does not provide coverage
*   Added keyword flagging to identify keywords that may be sensitive to particular audiences
*   Added social content flagging to identify social media posts that may be sensitive to particular audiences
*   Changed classify/url to return a 403 Status Code if a requested URL is blocked by that domains robots.txt

Version 1.0.24
--------------
*   New eContext translation service provides fast translation for incoming content.  Supports Spanish, French, Portuguese, Italian, Dutch, German content
*   Translated content is now passed through to your classification results

Version 1.0.23
--------------
*   Added the Twitter Interest Taxonomy overlay as an available client add-on
*   Changed format of overlays to be more descriptive - each taxonomy map now returns as a list with Tier 1 and Tier 2, when available

Version 1.0.22
--------------
*   Internal improvements

Version 1.0.21
--------------
*   Added client taxonomy overlay capabilities
*   Added `IAB Taxonomy`_ overlay as an available client addon

Version 1.0.20
--------------
*   Improved performance of demo limits for new accounts
*   Internal improvements in dataset migration and publication including

Version 1.0.19
--------------

*   Added an "async" parameter to classify/ calls to block on classification.  The result of the POST will
    be the actual classification results rather than a link to the result URI.
*   Reject classify/url POSTs where the url being classified doesn't provide an apporpriate content-type ('text/html', 'text/xhtml', 'application/xhtml+xml', 'text/xml', 'application/xml')
*   Reject classify/url POSTs where the url being classified is too large (content-length >= 256000 bytes)
*   Fixed an issue with classify/* results being lost occasionally

Version 1.0.18
--------------

*   Added an eContext Plugin to Google Translate API
*   Added a check to avoid translation of content if it is determined to be in English

Version 1.0.17
--------------

*   Added /categories/tiers to show all top-tier categories in the eContext Taxonomy
*   Added ability to perform automatic content translation prior to classification
    using a bring-your-own translation service - currently only Microsoft Translator API
*   Added general Category statistics including Social IDF (Inverse Document Frequency) and Social Relevance
*   Deprecated /classify/twitter - these calls should be handled by /classify/social

.. _`IAB Taxonomy`: http://www.iab.com/guidelines/iab-quality-assurance-guidelines-qag-taxonomy/
