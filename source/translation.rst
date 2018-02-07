Non-English Content in eContext
=======================

eContext accepts content in selected non-english languages, as described in this section. When submitting content in one of these supported languages, no additional parameters or declarations are required.

For functions that support multiple records per post, users may submit some records in one language and some records in another language and have each of language recognized individually. However, a mixture of languages in the same record may not be recognized correctly.

eContext uses a variety of additional technology to support this capability, including machine translation, so latency will increase compared to processing content in English. Content in some non-english languages, including those with more diverse character sets or right-to-left script, may take longer to process than others.

All eContext Category information is returned in English; however, certain other response objects may be in English or may be in the source language. See the list of supported languages for more details.


Calls that Accept Non-English Content
-------------------------------------

* :doc:`classify-html`
* :doc:`classify-keywords`
* :doc:`classify-social`
* :doc:`classify-text`
* :doc:`classify-url`

Supported Languages
-------------------

eContext provides rich language responses for the following languages:

    * Arabic
    * Chinese (Simplified & Traditional)
    * Japanese
    * Portuguese
    * Russian
    * Spanish

API responses for content submitted in one of these languages will include ``scored_keywords`` in the original source language.

eContext also supports content in the following languages:

    * French
    * German
    * Italian

API responses for content submitted in one of these languages will be entirely in English.

Additional Languages
^^^^^^^^^^^^^^^^^^^^

If you need to submit content in a language not included in the list of supported languages, please contact our `Client Services Team`_. eContext is always soliciting feedback on new languages to support, and can iterate quickly if your data demands it.

.. _Client Services Team: hello@econtext.com
