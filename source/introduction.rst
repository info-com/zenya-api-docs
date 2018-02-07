Introduction
============

The eContext API exposes the functionality of the eContext platform to
developers via a RESTful API. The general purpose is to provide access to
eContext's hierarchical category structure, or Taxonomy; to allow for real-time classification of data to the
taxonomy; and to allow for keyword retrieval from the eContext dataset utilizing
rich searching and filtering capabilities.

Taxonomy Overlay
----------------

The eContext API can be used to classify content to 3rd party taxonomies, including industry standard taxonomies like the IAB, or custom client specific taxonomies. Contact our `Client Services Team`_ to learn more about the standard overlays we support, or commission a custom overlay.

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

.. _Client Services Team: hello@econtext.com
