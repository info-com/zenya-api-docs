Changelog
=========

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
