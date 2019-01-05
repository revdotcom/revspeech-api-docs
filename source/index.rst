Welcome to the Rev.ai Documentation
========================================

**Go to Rev.ai Home**: https://www.rev.ai

Rev.ai aims to deliver quality speech-text recognition via an API. All public methods and 
objects are documented here for developer reference.

*This documentation is a work in progress and subject to change*

Base Endpoint
**************

The base url for this version of the API is

 ``https://api.rev.ai/revspeech/v1beta``

All endpoints described in this documentation are relative to this base url

API Key
*************

All API requests must be authorized with an ``"Authorization: Bearer"`` header

``-H "Authorization: Bearer <api_key>"``

.. _settings page: http://www.rev.ai/settings

Developers can obtain their API Key from their `settings page`_. This API need only be generated once and never expires.

Python SDK
**************
Check out our Python SDK here:
https://pypi.org/project/rev-ai/

You can install it using 

.. code:: javascript

  pip install rev_ai

.. toctree::
    :maxdepth: 1
    :caption: Get Started:

    quickstart

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

Errors:
*************

.. _RFC7807: https://tools.ietf.org/html/rfc7807

All errors returned in endpoints follow standard `RFC7807`_ spec
