*************
Job
*************

Revspeech API Job Object Model

Note: properties are not displayed in the returned object if they are ``null``

``Properties``
***************

====================== ================ ==============================================================================================
Name                   Type             Description
====================== ================ ==============================================================================================
id                     string           id of the job 
---------------------- ---------------- ----------------------------------------------------------------------------------------------
status                 string           current status of the job. 'in_progress', 'transcribed', or 'failed'
---------------------- ---------------- ----------------------------------------------------------------------------------------------
created_on             string(date)     the date and time the transcription job was created in ISO-8601 UTC form
---------------------- ---------------- ----------------------------------------------------------------------------------------------
metadata               string           metadata that was provided during job submission. 256 maximum char limit
---------------------- ---------------- ----------------------------------------------------------------------------------------------
callback_url           string           callback url to invoke on job completion
---------------------- ---------------- ----------------------------------------------------------------------------------------------
duration_seconds       double           duration of the file in seconds, null when not available
---------------------- ---------------- ----------------------------------------------------------------------------------------------
media_url              string           media url provided by the job submission
---------------------- ---------------- ----------------------------------------------------------------------------------------------
failure                string           failure reason. 'unspecified', 'download_failure', 'invalid_media', 'insufficient_balance'
---------------------- ---------------- ----------------------------------------------------------------------------------------------
failure_detail         string           human-readable reason why the job failed
====================== ================ ==============================================================================================

``Examples``
*************

.. code:: javascript

    // New Job
    {
      "id": "111111",
      "status": "in_progress",
      "created_on": "2018-05-05T23:23:22.29Z",
      "metadata": "this is sample metadata"
    }       
    
    // Transcribed Job
    {
      "id": "111111",
      "status": "transcribed",
      "created_on": "2018-05-05T23:23:22.29Z",
      "callback_url": "https://www.example.com/callback",
      "duration_seconds": 356.24,
      "media_url": "https://support.rev.com/hc/en-us/article_attachments/200043975/FTC_Sample_1_-_Single.mp3"
    }     
    
    // Failed Job
    {
      "id": "111111",
      "status": "failed",
      "created_on": "2018-05-05T23:23:22.29Z",
      "failure": "download_failure",
      "failure_detail": "Failed to download media file. Please check your url and file type"
    }       
 