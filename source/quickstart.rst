**************
Getting Started
**************

Use your API Key generated above to make calls to our API. 

To **transcribe an audio** file to Rev.ai:

.. code:: javascript

  curl -X POST "https://api.rev.ai/revspeech/v1beta/jobs" -H "Authorization: Bearer <api_key>" -H "Content-Type: application/json" -d "{\"media_url\":\"https://support.rev.com/hc/en-us/article_attachments/200043975/FTC_Sample_1_-_Single.mp3\",\"metadata\":\"This is a sample submit jobs option\"}"

You’ll receive a response like this:

.. code:: javascript

  {"id":"2028247","created_on":"2018-09-15T05:14:38.13","name":"sample.mp3","metadata":"This is a sample submit jobs option for multipart","status":"in_progress"}

This id (in this case 2028247) will allow you to retrieve your transcript. To **retrieve your transcript** from RevSpeech run:

.. code:: javascript

  curl -X GET "https://api.rev.ai/revspeech/v1beta/jobs/{id}/transcript" -H "Authorization: Bearer <api_key>" -H "Accept: application/vnd.rev.transcript.v1.0+json"

Alternatively you can get plain text by running:

.. code:: javascript

  curl -X GET "https://api.rev.ai/revspeech/v1beta/jobs/{id}/transcript" -H "Authorization: Bearer <api_key>" -H "Accept: text/plain"

If you have any further questions, contact us at support@rev.ai