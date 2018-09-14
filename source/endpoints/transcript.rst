*************
Transcript
*************

``GET /jobs/{id}/transcript``
******************************

Gets an :ref:`transcript <transcript-model>` by :ref:`job <job-model>` id

Note: all GET transcript requests must include an ``Accept`` header that specifies the desired output format. 

**CURL Examples**

.. code:: javascript

  curl -X GET "https://api.rev.ai/revspeech/v1beta/jobs/{id}" -H "Authorization: Bearer <api_key>"

**Parameters**

====================== ===============================================================
Name                   Description
====================== ===============================================================
id ``(required)``      Gets an existing transcription by job id
====================== ===============================================================

**Responses**

====================== ===============================================================
Code                   Description
====================== ===============================================================
200                    :ref:`Revspeech API Transcript <transcript-model>`

                       ``Example Value``

                       **Accept: application/vnd.rev.transcript.v1.0+json**

                       .. code:: javascript

                        {
                          "monologues": [
                            {
                              "speaker": 1,
                              "elements": [
                                {
                                  "type": "text",
                                  "value": "Hello",
                                  "ts": 0.5,
                                  "ts_end": 1.5,
                                  "confidence": 0.99                                 
                                },
                                {
                                  "type": "punct",
                                  "value": "."
                                }
                              ]
                            }                           
                          ]
                        }       
---------------------- ---------------------------------------------------------------
 200                    ``Example Value``

                        **Accept: text/plain**

                        `Speaker 1:    00:00    Hello there, this is a sample transcript in plain text`

                        `Speaker 1:    00:43    It is in the format of <Speaker> <Timestamp> <Text>`
---------------------- ---------------------------------------------------------------
400                    Bad Request

                       ``Example Value``

                       .. code:: javascript

                        {
                          "allowed_values": [
                            "text/plain",
                            "application/vnd.rev.transcript.v1.0+json"
                          ],
                          "current_value": "*/*",
                          "type": "https://www.rev.ai/api/speech/v1/errors/unsupported-transcript-format",
                          "title": "Transcript format is not supported",
                          "detail": "Unsupported value */*"
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
---------------------- ---------------------------------------------------------------
409                    Incorrect Transcript State

                       ``Example Value``

                       .. code:: javascript

                        {
                          "allowed_values": [
                            "transcribed"
                          ],
                          "current_value": "in_progress",
                          "type": "https://www.rev.ai/api/speech/v1/errors/invalid-job-state",
                          "title": "Job is in invalid state",
                          "detail": "Job is in invalid state to obtain the transcript"
                        }                        
====================== ===============================================================