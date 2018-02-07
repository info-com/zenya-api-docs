Changelog
=========

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
