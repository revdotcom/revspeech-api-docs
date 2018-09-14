Revspeech API Documentation
===========================

**Go to Rev.ai Home**: https://www.rev.ai

This Revspeech API aims to deliver quality speech-text recognition via an API. All public methods and 
objects are documented here for developer reference.

*This documentation is a work in progress and subject to change*

Base Endpoint
**************

The base url for this version of the API is

 ``https://api.rev.com/revspeech/v1beta``

All endpoints described in this documentation are relative to this base url

API Key
*************

All API requests must be authorized with an ``"Authorization: Bearer"`` header

.. _settings page: http://www.rev.ai/settings

Developers can obtain their API Key from their `settings page`_.

**Example**

``curl -H "Authorization: Bearer <api_key>"``


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
    models/webhooks