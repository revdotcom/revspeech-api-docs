*************
Transcript
*************

``GET /jobs/{id}/transcript``
******************************

Gets an :ref:`transcript <transcript-model>` by :ref:`job <job-model>` id

Note: all GET transcript requests must include an ``Accept`` header that specifies the desired output format. Either plain text or revs special json format

**CURL Examples**

.. code:: javascript

  curl -X GET "https://api.rev.ai/revspeech/v1beta/jobs/{id}/transcript" -H "Authorization: Bearer <api_key>" -H "Accept: application/vnd.rev.transcript.v1.0+json"

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
200                    :ref:`Rev.ai Transcript <transcript-model>`

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
                                  "end_ts": 1.5,
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

                        | When the submitted job has :ref:`skip_diarization <options-model>` either set to ``false`` or not set, 
                        | the transcript will appear as follows:
                        
                        | `Speaker 0    00:01     What is your name?`
                        | `Speaker 1    00:03     Sir Lancelot of Camelot!`
                        | `Speaker 0    00:05     What is your quest?`
                        | `Speaker 1    00:08     To seek the Holy Grail!`
                        | `Speaker 0    00:11     What is your favorite colour?`
                        | `Speaker 1    00:14     Red! I mean blue!`

                        When the submitted job has :ref:`skip_diarization <options-model>` set to ``true``, the same audio would appear as:

                        | `Speaker 0    00:01     What is your name? Sir Lancelot of Camelot! What is your`
                        | `quest? To seek the Holy Grail! What is your favorite colour? Red! I mean blue!`

---------------------- ---------------------------------------------------------------
401                    Request Unauthorized

                       ``Example Value``

                       .. code:: javascript

                        {
                          "title": "Authorization has been denied for this request"
                        }    

                        Caused by an old or invalid API Token, try regenerating your token on your `settings page`_. 
---------------------- ---------------------------------------------------------------
404                    Job Not Found
---------------------- ---------------------------------------------------------------
406                    Not Acceptable

                       ``Example Value``

                       .. code:: javascript

                        {
                          "allowed_values": [
                            "text/plain",
                            "application/vnd.rev.transcript.v1.0+json"
                          ],
                          "type": "https://www.rev.ai/api/speech/v1/errors/unsupported-transcript-format",
                          "title": "Transcript format is not supported",
                          "detail": "Unsupported value */*"
                        }  
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

                        In case of failure, more details can be found at :ref: `GET jobs/{id}`
====================== ===============================================================