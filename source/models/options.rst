.. _options-model:

*************
Options
*************

Rev.ai Job Options Object Model

``Properties``
***************

====================== ================ ==============================================================================================
Name                   Type             Description
====================== ================ ==============================================================================================
media_url              string           **direct download** media url. ignored if submitting job from file
---------------------- ---------------- ----------------------------------------------------------------------------------------------
metadata               string           **optional** metadata to associate with the job. 256 maximum char limit
---------------------- ---------------- ----------------------------------------------------------------------------------------------
callback_url           string           **optional** callback url to invoke on job completion as a :ref:`webhook <webhooks-model>`
---------------------- ---------------- ----------------------------------------------------------------------------------------------
skip_diarization       boolean           **optional** If true then speaker diarization will be skipped, otherwise speech engine will perform speaker diarization. If value is not provided then the value defaults to false.
---------------------- ---------------- ----------------------------------------------------------------------------------------------
language_model         n/a              *CURRENTLY UNSUPPORTED* language model type to use in processing
---------------------- ---------------- ----------------------------------------------------------------------------------------------
recognition_context    n/a              *CURRENTLY UNSUPPORTED* text to be used to give context to the recognition
---------------------- ---------------- ----------------------------------------------------------------------------------------------
locales                n/a              *CURRENTLY UNSUPPORTED* array of locale codes that are expected in the audio
---------------------- ---------------- ----------------------------------------------------------------------------------------------
custom_vocabulary      n/a              *CURRENTLY UNSUPPORTED* array of expressions that must be added/biased during recognition
---------------------- ---------------- ----------------------------------------------------------------------------------------------
desired_processing     n/a              *CURRENTLY UNSUPPORTED* list of speech-recognition steps to be performed
====================== ================ ==============================================================================================

``Examples``
*************

**From Media Url**

.. code:: javascript

    {
      "media_url": "https://support.rev.com/hc/en-us/article_attachments/200043975/FTC_Sample_1_-_Single.mp3",
      "metadata": "sample metadata",
      "callback_url": "https://www.example.com/callback",
      "skip_diarization": "false"
    }       

**From Local File**

.. code:: javascript

    {
      "metadata": "sample metadata",
      "callback_url": "https://www.example.com/callback",
      "skip_diarization": "false"
    }    