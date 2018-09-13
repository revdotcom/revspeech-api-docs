Revspeech API Documentation
===========================

This Revspeech API aims to deliver quality speech-text recognition via an API. All public methods and 
objects are documented here for developer reference.

*This documentation is a work in progress and subject to change*

Base Endpoint
**************

The base url for this version of the api is

 ``https://api.rev.com/revspeech/v1beta``

All endpoints described in this documentation are relative to this base url

.. toctree::
    :maxdepth: 2
    :caption: Authorization:

    authorization/api-key

.. toctree::
    :maxdepth: 2
    :caption: Endpoints:

    endpoints/jobs
    endpoints/transcript
    endpoints/account

.. toctree::
    :maxdepth: 2
    :caption: Models:

    models/job
    models/options
    models/transcript
    models/account