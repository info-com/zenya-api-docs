Non-English Content in eContext
===============================

eContext accepts content in selected non-english languages, as described in this section.

eContext uses a variety of additional technology to support this capability so latency may increase compared to processing content in English. Content in some languages may take longer to process than others.

All eContext Category information is currently returned in English.  However, certain other response objects, namely keyword hints and entities, may be in English or may be in the source language. See the list of supported languages for more details.


Calls that Accept Non-English Content
-------------------------------------

* :doc:`classify-html`
* :doc:`classify-keywords`
* :doc:`classify-social`
* :doc:`classify-text`
* :doc:`classify-url`

In supported calls, please identify the source language using an ISO 639-1 Code.  For example, in a classify/social call you might use the following:

.. literalinclude:: _static/classify-social-translate-input.json
    :language: json

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
