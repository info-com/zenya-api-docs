Best Practices
==============

Synchronous vs. Asyncronous calls
---------------------------------

The eContext API allows for both syncronous and asyncronous calls for all of the
general classification calls.  There are various scenarious where synchronous
calls are beneficial, but asynchronous calls may be used to allow you to scale
throughput in certain situations.

Although no official rate-limits are generally enforced against calls to the API,
eContext reserves the right to throttle users sending through excessive calls.

Asynchronous calls
^^^^^^^^^^^^^^^^^^

When using an asynchronous call (the default for classify/*), a request is 
submitted via the API and is queued in the eContext Classification Engine.  A
result object is created immediately and returned to the user to check on
progress, and, when completed, also contains the classification result.  In
general, the workflow looks like this:

.. image:: _static/asynchronous-flow.png
   :alt: Asynchronous Workflow

As you can see, there is a bit more work involved in this method, including the
introduction of a storage backend to allow storage and retrieval of a result set.

However, if your environment is single-threaded and running pool processes,
threads, or multiple processes is difficult, it can be quite simple to implement
an algorithm to run quickly through a large dataset.  In this case, please be
respectful of your usage.  For example, don't simply submit 100,000 keywords
before begining to retrieve results.  Performance will generally be more stable
if you run several asynchronous calls in a queue, checking for results 
periodically so before you submit new keywords.

Synchronous Calls
^^^^^^^^^^^^^^^^^

On the other hand synchronous calls block and return a result from the eContext
Classification Engine as soon as is completed.  Depending on your programming
environment and capabilities, synchronous calls can be parallelized and allow
for very high throughput, and less load on the eContext Classification Engine.
A typical workflow for synchronous calls would make use of process pools, threads,
queues, etc, in order to run several synchronous calls at the same time.

The synchronous workflow is illustrated below, and eliminates a storage backend,
allowing for slightly increased performance:

.. image:: _static/synchronous-flow.png
   :alt: Synchronous Workflow

