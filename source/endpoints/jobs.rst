.. _jobs-endpoint:

*************
Jobs
*************

``GET /jobs/{id}``
*******************

Gets an existing transcription :ref:`job <job-model>` by id

**CURL Examples**

.. code:: javascript

  curl -X GET "https://api.rev.ai/revspeech/v1beta/jobs/{id}" -H "Authorization: Bearer <api_key>"

**Parameters**

====================== ===============================================================
Name                   Description
====================== ===============================================================
id ``*required``        Gets an existing transcription job by id
====================== ===============================================================

**Responses**

====================== ===============================================================
Code                   Description
====================== ===============================================================
200                    :ref:`Revspeech API Job <job-model>`

                       ``Example Value``

                       .. code:: javascript

                        {
                          "id": "111111",
                          "status": "in_progress",
                          "created_on": "2018-05-05T23:23:22.29Z"
                        }          
---------------------- ---------------------------------------------------------------
401                    Request Unauthorized

                       ``Example Value``

                       .. code:: javascript

                        {
                          "title": "Authorization has been denied for this request"
                        }    
---------------------- ---------------------------------------------------------------
404                    Job Not Found
====================== ===============================================================


``POST /jobs``
*****************

Submits a transcription job

**CURL Examples**

Submitting via media URL. URL must be publicly accessible and a direct link to media.
.. code:: javascript

    curl -X POST "https://api.rev.ai/revspeech/v1beta/jobs" -H "Authorization: Bearer <api_key>" -H "Content-Type: application/json" -d "{\"media_url\":\"https://support.rev.com/hc/en-us/article_attachments/200043975/FTC_Sample_1_-_Single.mp3\",\"metadata\":\"This is a sample submit jobs option\"}"

Submitting for local uploads. Must include the audio type.
.. code:: javascript

  curl -X POST "https://api.rev.ai/revspeech/v1beta/jobs" -H "Authorization: Bearer <api_key>" -H "Content-Type: multipart/form-data" -F "media=@/path/to/media_file.mp3;type=audio/mp3" -F "options={\"metadata\":\"This is a sample submit jobs option for multipart\"}"

**Request Body (required)**

====================== ===============================================================
Content-Type           Example
====================== ===============================================================
application/json       Submitting via :ref:`Revspeech API Options <options-model>` with a ``media_url``

                       ``Example Value``

                       .. code:: javascript

                        {
                            "media_url": "https://support.rev.com/hc/en-us/article_attachments/200043975/FTC_Sample_1_-_Single.mp3",
                            "metadata": "This is a sample submit jobs option",
                            "callback_url": "https://www.example.com/callback"
                        }     
---------------------- ---------------------------------------------------------------
multipart/form         Uploading Direct Media File

                       ``Example Value``

                       **Key**: *Value*

                       **media**: *any media file with audio*

                       **options**: :ref:`options model <options-model>`
====================== ===============================================================

**Responses**

====================== ===============================================================
Code                   Description
====================== ===============================================================
200                    :ref:`Revspeech API Job <job-model>`

                       ``Example Value``

                       .. code:: javascript

                        {
                          "id": "111111",
                          "status": "in_progress",
                          "created_on": "2018-05-05T23:23:22.29Z"
                        }       
---------------------- ---------------------------------------------------------------
400                    Bad Request

                       ``Example Values``

                       .. code:: javascript

                        {
                          "parameter": {
                             "<invalid_parameter>": [
                                 "The <invalid_parameter> field is required"
                              ],
                          },
                          "type": "https://www.rev.ai/api/v1/errors/invalid-parameters",
                          "title": "Your request parameters didn't validate"
                        }     

                        {
                          "parameter": {
                             "media_url": [
                                 "The media_url field is required"
                              ],
                          },
                          "type": "https://www.rev.ai/api/v1/errors/invalid-parameters",
                          "title": "Your request parameters didn't validate"
                        }   
---------------------- ---------------------------------------------------------------
401                    Request Unauthorized

                       ``Example Value``

                       .. code:: javascript

                        {
                          "title": "Authorization has been denied for this request"
                        }    
---------------------- ---------------------------------------------------------------
403                    Insufficient Credits

                       ``Example Value``

                       .. code:: javascript

                        {
                          "title": "You do not have enough credits",
                          "type": "https://www.rev.ai/api/v1/errors/out-of-credit",
                          "detail": "You have only 60 seconds remaining",
                          "current_balance": 60
                        }    
====================== ===============================================================
