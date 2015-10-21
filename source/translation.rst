Translation in eContext
=======================

Is the content you want to classify in a language other than English?  eContext
can use your existing translation service to perform translation prior to
classification.  Simply add the credentials for your translation API service
to your eContext API request, and we'll do it for you.'

Adding Translation Paramters To A Call
--------------------------------------

In general, requesting translation is as simple as including a translate parameter
to your API call.  Here is an example using :doc:`/classify/social <classify-social>`:

.. literalinclude:: _static/classify-social-translate-input.json
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

Available 3rd Party Translation Services
----------------------------------------

Microsoft Translation API
^^^^^^^^^^^^^^^^^^^^^^^^^

You can bring your Microsoft Translation API account along with you into eContext.  eContext will
use your Microsoft Azure Application credentials to provide on-the-fly translation
of certain content, allowing you to classify non-english source content.

To sign up for a Micosoft Translation API Account follow these steps:
    
#. Signup for a basic Microsoft Account at http://login.live.com
#. Signup for a Microsoft Azure Account at https://datamarket.azure.com/home/
#. Subscribe to the Microsoft Translator API
    a. Go to https://datamarket.azure.com/dataset/bing/microsofttranslator
    b. Add a subscription for the appropriate level
#. From your Microsoft Azure Account "Developers" tag, register a new application
    a. Go to https://datamarket.azure.com/developer/applications
    b. Click the "Register" button
    c. Register your new application, taking note of your "Client ID" and "Client secret"

You may now use these credentials to perform translation in the eContext API
