Introduction
============

The Zenya API exposes the functionality of the Zenya platform to developers via a RESTful API. The general
purpose is to provide access to the Zenya Taxonomy structure, to allow for real-time mapping of keywords 
to the Taxonomy, and to allow for keyword retrieval from the Zenya dataset utilizing rich searching and 
filtering capabilities.

Input Format
------------

The input format to the Zenya API is specified using the HTTP Content-Type header  (:rfc:`2616#section-14.17`).
A Content-Type of ``application/x-www-form-urlencoded`` may also be accepted although 
``multipart/form-data`` is currently not accepted.  All examples in this documentation 
assume that **POST** data is in JSON format and that a header 
``Content-type: application/json`` is sent.

Output Format
-------------

The output format is generally set by using the HTTP Accept header (:rfc:`2616#section-14.1`).
The default output format for the Zenya API is JSON (``application/json``).  As the default
output format, all examples in this documentation are displayed using JSON.

The following output formats are currently supported:

* application/xml (:rfc:`3023`)
* application/json (:rfc:`4627`)
* text/html (:rfc:`2854`)

