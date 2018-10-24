.. _transcript-model:

*************
Transcript
*************

RevSpeech API Transcript Model

Note: properties are not displayed in the returned object if they are ``null``

Jobs with `skip_diarization` set to true will only show a single speaker for the entire duration of the transcript.

``Monologue``
***************

====================== ================ ==============================================================================================
Name                   Type             Description
====================== ================ ==============================================================================================
speaker                int              id of the speaker of the monologue
---------------------- ---------------- ----------------------------------------------------------------------------------------------
elements               array            array of transcript elements
====================== ================ ==============================================================================================

``Element``
***************

====================== ================ ==============================================================================================
Name                   Type             Description
====================== ================ ==============================================================================================
type                   string           type of transcript element. ``"text"``, ``"punct"``, or ``"unknown"``
---------------------- ---------------- ----------------------------------------------------------------------------------------------
value                  string           value of the transcript element
---------------------- ---------------- ----------------------------------------------------------------------------------------------
ts                     double           the timestamp of the beginning of the element in fractional seconds relative to the beginning of the audio
---------------------- ---------------- ----------------------------------------------------------------------------------------------
end_ts                 double           the timestamp of the end of the element in fractional seconds relative to the beginning of the audio
---------------------- ---------------- ----------------------------------------------------------------------------------------------
confidence             double           confidence score of the provided value. ranges from ``0.00`` to ``1.00``
====================== ================ ==============================================================================================

``Examples``
*************

.. code:: javascript

    // Transcript Object
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
              "confidence": 1.00
            },
            {
              "type": "text",
              "value": "World",
              "ts": 1.75,
              "end_ts": 2.85,
              "confidence": .80
            },
            {
              "type": "punct",
              "value": "."
            }
          ]
        },
        {
          "speaker": 2,
          "elements": [
            {
              "type": "text",
              "value": "monologues",
              "ts": 3.0,
              "end_ts": 3.5,
              "confidence": 1.00
            },
            {
              "type": "text",
              "value": "are",
              "ts": 3.6,
              "end_ts": 3.9,
              "confidence": 1.00
            },
            {
              "type": "text",
              "value": "a",
              "ts": 4.0,
              "end_ts": 4.3,
              "confidence": 1.00
            },
            {
              "type": "text",
              "value": "block",
              "ts": 4.5,
              "end_ts": 5.5,
              "confidence": 1.00
            },
            {
              "type": "text",
              "value": "of",
              "ts": 5.75,
              "end_ts": 6.14,
              "confidence": 1.00
            },
            {
              "type": "text",
              "value": "text",
              "ts": 6.5,
              "end_ts": 7.78,
              "confidence": 1.00
            },
            {
              "type": "punct",
              "value": ".",
            },
          ]
        }
      ]
    }         