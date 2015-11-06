Changelog
=========

Version 1.0.18
--------------

*   Added an eContext Plugin to Google Translate API
*   Added a check to avoid tranlsation of content if it is determined to be in English

Version 1.0.17
-------------

*   Added /categories/tiers to show all top-tier categories in the eContext Taxonomy
*   Added ability to perform automatic content translation prior to classification 
    using a bring-your-own translation service - currently only Microsoft Translator API
*   Added general Category statistics including Social IDF (Inverse Document Frequency) and Social Relevance
*   Deprecated /classify/twitter - these calls should be handled by /classify/social
