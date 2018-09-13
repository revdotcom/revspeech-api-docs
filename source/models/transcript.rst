*************
Transcript
*************

Revspeech API Transcript Model

Note: properties are not displayed in the returned object if they are ``null``

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
type                   string           type of transcript element. "text", "punct", or "unknown"
---------------------- ---------------- ----------------------------------------------------------------------------------------------
value                  string           value of the transcript element
---------------------- ---------------- ----------------------------------------------------------------------------------------------
ts                     double           the timestamp of the beginning of the element in fractional seconds relative to the beginning of the audio
---------------------- ---------------- ----------------------------------------------------------------------------------------------
ts_end                 double           the timestamp of the end of the element in fractional seconds relative to the beginning of the audio
---------------------- ---------------- ----------------------------------------------------------------------------------------------
confidence             double           confidence score of the provided value. ranges from 0.00 to 1.00
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
              "ts_end": 1.5,
              "confidence": 1.00
            },
            {
              "type": "text",
              "value": "World",
              "ts": 1.75,
              "ts_end": 2.85,
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
              "ts_end": 3.5,
              "confidence": 1.00
            },
            {
              "type": "text",
              "value": "are",
              "ts": 3.6,
              "ts_end": 3.9,
              "confidence": 1.00
            },
            {
              "type": "text",
              "value": "a",
              "ts": 4.0,
              "ts_end": 4.3,
              "confidence": 1.00
            },
            {
              "type": "text",
              "value": "block",
              "ts": 4.5,
              "ts_end": 5.5,
              "confidence": 1.00
            },
            {
              "type": "text",
              "value": "of",
              "ts": 5.75,
              "ts_end": 6.14,
              "confidence": 1.00
            },
            {
              "type": "text",
              "value": "text",
              "ts": 6.5,
              "ts_end": 7.78,
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