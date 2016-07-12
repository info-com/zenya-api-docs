Introduction
============

The eContext API exposes the functionality of the eContext platform to 
developers via a RESTful API. The general purpose is to provide access to the 
eContext Taxonomy structure, to allow for real-time mapping of data to the 
taxonomy, and to allow for keyword retrieval from the eContext dataset utilizing 
rich searching and filtering capabilities.

Taxonomy Overlay
----------------

The eContext API can be used to classify content to your taxonomy as well.  By
connecting with our team, you can create a taxonomy overlay which uses our
technology to map any text content directly to your own taxonomy structure.
Contact our `Overlay Team`_ for more information.

Input Format
------------

The input format to the eContext API is specified using the HTTP Content-Type 
header  (:rfc:`2616#section-14.17`). A Content-Type of ``application/json`` is 
preferred, and there is no guarantee that other Content-Types will be honored.

Output Format
-------------

The output format is generally set by using the HTTP Accept header (:rfc:`2616#section-14.1`).
The default output format for the eContext API is JSON (``application/json``). As the default
output format, all examples in this documentation are displayed using JSON.

The following output formats are currently supported:

* application/json (:rfc:`4627`)

.. _Overlay Team: overlayteam@econtext.com