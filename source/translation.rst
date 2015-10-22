Translation in eContext
=======================

If the content you want to classify in a language other than English, eContext
can use your existing translation service to perform translation prior to
classification.  Include the credentials for your translation API service
with your eContext API request, and non-English content can be processed the
same as English content.

Adding Translation Parameters To A Call
--------------------------------------

In general, requesting translation is as simple as including a translate parameter
with your API call.  Here is an example using :doc:`/classify/social <classify-social>`:

.. literalinclude:: _static/classify-social-translate-input.json
    :language: json

If making a bulk post of content through the :doc:`/classify/social <classify-social>` 
or :doc:`/classify/keywords <classify-keywords>` calls, ensure that all posted content
is in the same source language. If you expect that the content may contain a mixture of
source languages, include only one post per call.  

Calls that Accept Translation Parameters
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. toctree::
    :maxdepth: 1
    
    classify-html
    classify-keywords
    classify-social
    classify-text
    classify-url

Available 3rd Party Translation Services
----------------------------------------

You are responsible for all costs associated with any 3rd Party Translation Service
you request eContext to use on your behalf. eContext will not save or store your 3rd
Party Service credentials or make any changes to your account. 

eContext may add, alter or remove integration with 3rd Party Services at its
discretion.

Microsoft Translator API
^^^^^^^^^^^^^^^^^^^^^^^^^

You can use your Microsoft Translator API account within eContext.  eContext will
use your Microsoft Azure Application credentials to provide on-the-fly language
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

You may now use these credentials to perform translation in the eContext API
