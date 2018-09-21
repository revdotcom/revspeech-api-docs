.. _webhooks-model:

*************
Webhooks
*************

It is possible to provide a ``callback_url`` field when :ref:`submitting a job <jobs-endpoint>`. If a ``callback_url`` is provided, the API will POST the following data to the given url when the :ref:`job's <job-model>` ``status`` becomes either ``transcribed`` or ``failed``

``Properties``
***************

====================== ================ ==============================================================================================
Name                   Type             Description
====================== ================ ==============================================================================================
job                    object           :ref:`RevSpeech API Job <job-model>`
====================== ================ ==============================================================================================

``Examples``
*************

.. code:: javascript

    // Transcribed Job
    {
      "job": {
        "id": "111111",
        "status": "transcribed",
        "created_on": "2018-05-05T23:23:22.29Z",
        "callback_url": "https://www.example.com/callback",
        "duration_seconds": 356.24,
        "media_url": "https://support.rev.com/hc/en-us/article_attachments/200043975/FTC_Sample_1_-_Single.mp3"
      }
    }   