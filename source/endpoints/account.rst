.. _settings page: http://www.rev.ai/settings

*************
Account
*************

``GET /account``
******************************

Gets the developer's :ref:`account <account-model>` information

**CURL Examples**

.. code:: javascript

  curl -X GET "https://api.rev.ai/revspeech/v1beta/account" -H "Authorization: Bearer <api_key>" 

**Responses**

====================== ===============================================================
Code                   Description
====================== ===============================================================
200                    :ref:`Rev.ai Account <account-model>`

                       ``Example Value``

                       **application/json**

                       .. code:: javascript

                        {
                          "email": "jay@rev.ai",
                          "balance_seconds": 1500
                        }    
---------------------- ---------------------------------------------------------------
401                    Request Unauthorized

                       ``Example Value``

                       .. code:: javascript

                        {
                          "title": "Authorization has been denied for this request"
                        }  

                       Caused by an old or invalid API Token, try regenerating your token on your `settings page`_.
====================== ===============================================================