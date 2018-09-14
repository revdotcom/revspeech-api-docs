.. _options-model:

*************
Options
*************

Revspeech API Job Options Object Model

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
language_model         n/a              *CURRENTLY UNSUPPORTED* language model type to use in procressing
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

.. code:: javascript

    // From Media Url
    {
      "media_url": "https://support.rev.com/hc/en-us/article_attachments/200043975/FTC_Sample_1_-_Single.mp3",
      "metadata": "sample metadata",
      "callback_url": "https://www.example.com/callback"
    }       
    
    // From Local File
    {
      "metadata": "sample metadata",
      "callback_url": "https://www.example.com/callback"
    }    