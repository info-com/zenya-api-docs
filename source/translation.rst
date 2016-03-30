Translation in eContext
=======================

If the content you want to classify is in a language other than English, eContext
can use your existing translation service to perform translation prior to
classification.  Include the credentials for your translation API service
with your eContext API request, and non-English content can be processed the
same as English content.  You may also use eContext's own translation service to
process a smaller number of languages, detailed below.

Adding Translation Parameters To A Call
---------------------------------------

In general, requesting translation is as simple as including a translate parameter
with your API call.  Here is an example using :doc:`/classify/social <classify-social>`:

.. literalinclude:: _static/classify-social-translate-input.json
    :language: json

If making a bulk post of content through the :doc:`/classify/social <classify-social>` 
or :doc:`/classify/keywords <classify-keywords>` calls, we recommend that all posted content
is in the same source language if you are using the Microsoft Translator plugin. 
If you expect that the content may contain a mixture of source languages, include
only one post per call.  Google and eContext do allow you to mix your input content.

The 3rd party services eContext connects through to provide translation services 
generally charge their users by characters processed.  eContext will return the
number of characters that were processed by the translation service to help you
keep track of your usage.  However, since eContext passes through 
your credentials, you are responsible for understanding your usage by querying 
the service directly.  eContext is not responsible for charges that you incur by using a 
translation plugin. eContext will attempt to identify the language of
incoming content and will make a best effort to not pass English content into a translation
service.

If a translation plugin is specified, the return object from eContext will 
include a summary of the translation activity as well as the translated content
retrieved from those services.  For example:

.. literalinclude:: _static/classify-social-translate-output.json
    :language: json


Calls that Accept Translation Parameters
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. toctree::
    :maxdepth: 1
    
    classify-html
    classify-keywords
    classify-social
    classify-text
    classify-url

eContext Translation Service
----------------------------------------

eContext's inhouse translation service provides fast machine translation for the
following languages:
    
    * Spanish
    * French
    * Portuguese
    * Italian
    * Dutch
    * German

Please contact your sales representative at eContext for more information on
signing up for eContext Translation Services.

Available 3rd Party Translation Services
----------------------------------------

You are responsible for all costs associated with any 3rd Party Translation Service
you request eContext to use on your behalf. eContext will not make any changes to your account.

eContext may add, alter or remove integration with 3rd Party Services at its
discretion.

eContext plugin to Microsoft Translator API
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

You can use your Microsoft Translator API account within eContext.  eContext will provide on-the-fly language
identification and translation, allowing you to classify non-English source content.

To sign up for a Micosoft Translator API Account, follow these steps:
    
#. Signup for a basic Microsoft Account at http://login.live.com
#. Signup for a Microsoft Azure Account at https://datamarket.azure.com/home/
#. Subscribe to the Microsoft Translator API
    a. Go to https://datamarket.azure.com/dataset/bing/microsofttranslator
    b. Add a subscription for the appropriate level
#. From your Microsoft Azure Account "Developers" tab, register a new application
    a. Go to https://datamarket.azure.com/developer/applications
    b. Click the "Register" button
    c. Register your new application, taking note of your "Client ID" and "Client secret"

You may now use these credentials to perform translation in the eContext API. 
An example of the POST body that would pass content through to the Microsoft
Translator API for translation before processing in eContext:

.. literalinclude:: _static/classify-social-translate-input-ms.json
    :language: json

eContext plugin to Google Translate API
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

You can use the Google Translate API Keys connected with your Google Developer Console account within eContext. 
eContext will provide on-the-fly language identification and translation, allowing you to classify non-English
source content.

To connect to the Google Translate API, follow these steps from the Google
Developer Console.

#. Open the API Manager from the Google Developer Console menu.
#. Search for the Translate API
#. Enable the Translate API
    a. If you do not have billing set up on your Google Developer Account, click on the "Quotas" tab of the Translate API and select "Enable Billing"
#. Open the Credentials tab under the API Manager
#. From the "Add credentials" menu, select "API Key"
#. Create a new "Browser key"
    a. GIve the key a name
    b. Add "api.econtext.com" the list of domains to accept requests from.  This will ensure that your API key cannot be abused

An example of the POST body that would pass content through to the Google 
Translate API for translation before processing in eContext:

.. literalinclude:: _static/classify-social-translate-input-b.json
    :language: json

