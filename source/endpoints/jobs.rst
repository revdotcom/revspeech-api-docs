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
200                    :ref:`RevSpeech API Job <job-model>`

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


``GET /jobs``
*******************

Gets a list of transcription :ref:`jobs <job-model>` submitted within the last week in reverse chronological 
order up to ``limit`` jobs per call. Pagination is supported via passing the last job id from a previous call 
into ``starting_after``.

**CURL Examples**

Getting list of jobs with a limit of 10 jobs.

.. code:: javascript

  curl -X GET "https://api.rev.ai/revspeech/v1beta/jobs?limit=10" -H "Authorization: Bearer <api_key>"

Getting list of jobs starting after :ref:`job <job-model>` with id 111111.

.. code:: javascript

  curl -X GET "https://api.rev.ai/revspeech/v1beta/jobs?starting_after=111111" -H "Authorization: Bearer <api_key>"


**Parameters**

============================ ===============================================================
Name                         Description
============================ ===============================================================
limit ``optional``           Limits the number of jobs returned, default is 100, max is 1000
---------------------------- ---------------------------------------------------------------
starting_after ``optional``  Gets jobs listed after this job id, exclusive - job with id not included
============================ ===============================================================

**Responses**

====================== ===============================================================
Code                   Description
====================== ===============================================================
200                    List of :ref:`RevSpeech API Job <job-model>`

                       ``Example Value``

                       .. code:: javascript

                        [{
                          "id": "222222",
                          "created_on": "2018-05-08T23:23:22.29Z",
                          "media_url": "https://example.com",
                          "status": "transcribed",
                          "duration_seconds": 40
                        },
                        {
                          "id": "111111",
                          "status": "in_progress",
                          "created_on": "2018-05-05T23:23:22.29Z"
                        }]         
---------------------- ---------------------------------------------------------------
400                    Bad Request

                       ``Example Value``

                       .. code:: javascript

                        {
                          "parameter": {
                             "limit": [
                                 "The max value for limit is 1000"
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
application/json       Submitting via :ref:`RevSpeech API Options <options-model>` with a ``media_url``

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
200                    :ref:`RevSpeech API Job <job-model>`

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
