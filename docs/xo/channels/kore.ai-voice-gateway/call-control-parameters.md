# Call Control Parameters

Call control parameters are general-purpose parameters that can modify a call's behavior, including ASR/STT & TTS configurations.

!!! note

    Automatic Speech Recognition (ASR) and Speech-to-Text (STT) are two terms that refer to the same technology. Both involve converting spoken language into written text by analyzing and interpreting audio input. The terms are used interchangeably, describing the same function—transforming speech into readable, actionable text.

There are two ways to define the Call Control Parameters - Node Level and Channel Level.

You can apply Call Control Parameters at either the Session or Node level, offering more flexibility in managing call behavior.

* **Session-Level Parameters**: Add the prefix `session.` to apply parameters throughout the session (for example, `session.ttsprovider`).
* **Node-Level Parameters**: Add the prefix node. to apply parameters only at a specific node (for example, `node.ttsprovider`).
* **Default Behavior**: Parameters without a prefix are considered session-level by default.
* Node-level parameters take precedence over session-level parameters. If no node-level parameters are defined, session-level properties will be applied.

## Node Level Call Control

The call control section is Available In [Entity Node](../../automation/use-cases/dialogs/node-types/working-with-the-entity-node.md)/[Message Node](../../automation/use-cases/dialogs/node-types/working-with-the-message-nodes.md#ivr-properties)/[Confirmation Node](../../automation/use-cases/dialogs/node-types/working-with-the-confirmation-nodes.md#ivr-properties) > IVR Properties > Advanced Controls. [Learn more](../../automation/use-cases/dialogs/node-types/voice-call-properties.md#configuring-grammar).  
<img src="../images/node-level-call-control-parameters.png" alt="Node Level Call Control" title="Node Level Call Control" style="border: 1px solid gray; zoom:80%;">

## Channel Level Call Control

For information on configuring the Call Control Parameters at the channel level, refer to [Define the Call Control Parameters](../smart-assist-gateway.md#step-4-define-the-call-control-parameters).

## Update/Modify Parameters
When updating language settings or modifying Automatic Speech Recognition (ASR) and Text-to-Speech (TTS) parameters in Call Control Parameters, users can specify the updated field along with a minimal set of required parameters.

For example, if a user has already configured the STT provider and language in the call control parameters and wants to add a new language, the system appends the new parameter while retaining the existing values. Users only need to provide the additional sttLanguage parameter without redefining the previously set values.

This behavior applies to Session-Level Call Control Parameters.

**Example**

**Existing Parameters:**

```
{
  "sttProvider": "microsoft",
  "sttLanguage": "en-IN"
}
```

**Adding a New Language:**

```
{
  "sttLanguage": "en-ES"
}
```

In this scenario, the system retains the existing **sttProvider** and previously set **sttLanguage**, ensuring that only the new parameter is added without requiring users to re-enter unchanged values.

### Supported Speech Engines

Kore.ai supports the following third-party service providers for ASR/TTS. [Learn more](https://docs.kore.ai/smartassist/configuration/support-for-third-party-asr-tts-and-voice-biometrics/).

<table>
  <tr>
   <td><strong>Speech Engine</strong>
   </td>
   <td><strong>ASR Name</strong>
   </td>
   <td><strong>TTS Name</strong>
   </td>
   <td><strong>Supported Environment</strong>
   </td>
  </tr>
  <tr>
   <td>Microsoft Azure
   </td>
   <td>microsoft
   </td>
   <td>microsoft
   </td>
   <td>On Premise<br>
Cloud
   </td>
  </tr>
  <tr>
   <td>Google
   </td>
   <td>google
   </td>
   <td>google
   </td>
   <td>On-Premise<br>
Cloud
   </td>
  </tr>
  <tr>
   <td>Nvidia (Riva)
   </td>
   <td>nvidia
   </td>
   <td>nvidia
   </td>
   <td>On-Premise
   </td>
  </tr>
  <tr>
   <td>Amazon (AWS)
   </td>
   <td>aws
   </td>
   <td>polly
   </td>
   <td>Cloud
   </td>
  </tr>
  <tr>
   <td>Deepgram
   </td>
   <td>deepgram
   </td>
   <td>deepgram
   </td>
   <td>Cloud
   </td>
  </tr>
  <tr>
   <td>Elevenlabs
   </td>
   <td>Not Supported
   </td>
   <td>elevenlabs
   </td>
   <td>Cloud
   </td>
  </tr>
  <tr>
   <td>Whisper
   </td>
   <td>Not Supported
   </td>
   <td>whisper
   </td>
   <td>Cloud
   </td>
  </tr>
  <tr>
   <td>Ami voice
   </td>
   <td>amivoice
   </td>
   <td>
   </td>
   <td>Cloud
   </td>
  </tr>
</table>

### Common ASR Parameters

<table>
  <tr>
   <td><strong>Parameter</strong>
   </td>
   <td><strong>Type</strong>
   </td>
   <td><strong>Supporting STT/ TTS</strong>
   </td>
   <td><strong>Description</strong>
   </td>
   <td><strong>Examples</strong>
   </td>
  </tr>
  <tr>
   <td>alternativeLanguages
   </td>
   <td>Array of Objects
   </td>
   <td>Google
Microsoft
Deepgram
   </td>
   <td>An array of alternative languages that the speaker may be using
Based on user utterance, the transcript will come from either of the selected languages.
   </td>
   <td>alternativeLanguages =
[
    {
   
   "language": "de-DE",
      "voiceName": "de-DE-KatjaNeural"
    },
    {
      "language": "fr-FR",
      "voiceName": "fr-FR-DeniseNeural"
    }
  ]
   </td>
  </tr>
  <tr>
   <td>sttMinConfidence
   </td>
   <td>Number
Range-
<strong>(0.1 to 0.9)</strong>
   </td>
   <td>ALL
   </td>
   <td>If the <code>minConfidence</code> parameter is set, and the transcript generated by the ASR falls below this confidence threshold, the Voice Gateway will disregard the input and trigger the timeout prompt to play. This ensures that only highly accurate speech recognition results are captured, improving the quality of the interaction.
   </td>
   <td>Example
 <code>sttMinConfidence = 0.5</code>,
Any ASR transcript with a confidence score below 0.5 will be ignored, and the system will play the timeout prompt. This ensures that only inputs with sufficient accuracy are processed, improving reliability in voice interactions.
   </td>
  </tr>
  <tr>
   <td>Hints with Phrase level hintsboost
This is an additional feature present in allowing a boost factor to be specified at the phrase level
Kore VG
Key = hints
   </td>
   <td> Array Of Objects
   </td>
   <td>:
Google
Nvidia
   </td>
   <td>The parameter can list phrases or words that are passed to the speech-to-text service as "hints" for improving the accuracy of speech recognition.
For example - weather and whether have the same pronunciation, for more accuracy we gave hints to the bot.  
Hints : [‘weather’] It will take weather as input
Put this array in the Grammar section of the bot builder.
   </td>
   <td><code>"hints" = [</code>
<code>  {"phrase": "benign", "boost": 50},</code>
<code>  {"phrase": "malignant", "boost": 10},</code>
<code>  {"phrase": "biopsy", "boost": 20},</code>
<code>]</code>
   </td>
  </tr>
  <tr>
   <td>Hints with Separate HintBoost
   </td>
   <td>

   </td>
   <td>Google
Microsoft
Nvidia
   </td>
   <td>
   </td>
   <td><code>"hints": ["benign", "malignant", "biopsy"],</code>
<code>"hintsBoost": 50</code>
   </td>
  </tr>
  <tr>
   <td>sttDisablePunctuation
   </td>
   <td>Boolean
   </td>
   <td>
 Google
 Microsoft
   </td>
   <td>Prevents or Includes the ASR to add punctuation in response.
By default, ASR will add punctuation in the User Transcript
(for example, periods, commas, and question marks).
   </td>
   <td>sttDisablePunctuation : true
True: means remove the punctuation.
False: Add the punctuation
   </td>
  </tr>
  <tr>
   <td>vadEnable
   </td>
   <td>Boolean
   </td>
   <td>ALL
   </td>
   <td>If true, delay connecting to the cloud recognizer until the speech is detected
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>vadVoiceMS
   </td>
   <td>Number in MS
   </td>
   <td>ALL
   </td>
   <td>If vad is enabled, the number of milliseconds of speech is required before connecting to the cloud recognizer.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>vadMode
   </td>
   <td>Number between (0-3)
   </td>
   <td>ALL
   </td>
   <td>If vad is enabled, this setting governs the sensitivity of the voice activity detector; the value must be between 0 to 3 inclusive, lower numbers mean more sensitive
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td colspan="5" >
<h4><strong>Microsoft ASR</strong></h4>

   </td>
  </tr>
  <tr>
   <td>azureSpeechSegmentationSilenceTimeoutMs
   </td>
   <td>Number
   </td>
   <td>
   </td>
   <td>Speech_SegmentationSilenceTimeoutMs is a timeout that can be set in between the phrases
It is similar to Continuous ASR, the Only Difference is  Continuous ASR is handled by vocieGateway but Azure speech segmentation is handled by AZURE ASR, So accuracy will be higher as compared to Continios ASR.
   </td>
   <td><a href="https://learn.microsoft.com/en-us/azure/ai-services/speech-service/how-to-recognize-speech?pivots=programming-language-csharp#change-how-silence-is-handled">More Info</a>
   </td>
  </tr>
  <tr>
   <td>sttEndpointID
   </td>
   <td>String
   </td>
   <td>
   </td>
   <td>Custom service endpoint to connect to, instead of hosted Microsoft regional endpoint.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>azurePostProcessing
   </td>
   <td>String
   </td>
   <td>
   </td>
   <td>improve the final transcript, such as text normalization (adjusting punctuation, casing, etc.) or specific custom handling based on the needs of the application.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>        azureSpeechRecognitionMode
   </td>
   <td>String (Enum)
It can be either
1) AtStart,
2) Continuous
   </td>
   <td>
   </td>
   <td>"<strong>AtStart</strong>": Starts recognizing speech as soon as it detects audio input and stops when the speaker finishes. Suitable for short, one-time speech recognition tasks
"<strong>Continuous</strong>": Continuously listens and transcribes speech, ideal for longer audio streams or uninterrupted speech sessions like meetings or dictation.
   </td>
   <td>azureSpeechRecognitionMode = Continuous“”
   </td>
  </tr>
  <tr>
   <td>profanityOption
   </td>
   <td>String(enum)
   </td>
   <td>
   </td>
   <td>It is used to mask profane words in the transcript. It has three values masked, removed, or raw.
Default: raw
   </td>
   <td>Example:
profanityOption = “masked”
   </td>
  </tr>
  <tr>
   <td>initialSpeechTimeoutMs
   </td>
   <td>Number in Ms
   </td>
   <td>
   </td>
   <td>Initial speech timeout in milliseconds.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>requestSnr
   </td>
   <td>Boolean
   </td>
   <td>
   </td>
   <td>Request signal-to-noise information.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>outputFormat
   </td>
   <td>String
   </td>
   <td>
   </td>
   <td>simple or detailed. Default: simple.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td colspan="5" >
<h4><strong>Google ASR</strong></h4>
   </td>
  </tr>
  <tr>
   <td>sttProfanityFilter
   </td>
   <td>Boolean
   </td>
   <td>
   </td>
   <td>A profanity filter provides a few options for dealing with profane words in the transcription.
Default: false
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>singleUtterance
   </td>
   <td>Boolean
   </td>
   <td>
   </td>
   <td>If true, return only a single utterance/transcript.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>sttModel
   </td>
   <td>String
   </td>
   <td>
   </td>
   <td>speech recognition model to use (default: phone_call)
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>sttEnhancedModel
   </td>
   <td>Boolean
   </td>
   <td>
   </td>
   <td>Use enhanced model
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>words
   </td>
   <td>Boolean
   </td>
   <td>
   </td>
   <td>Enable word offsets
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>diarization
   </td>
   <td>Boolean
   </td>
   <td>
   </td>
   <td>Enable speaker diarization
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>diarizationMinSpeakers
   </td>
   <td>Number
   </td>
   <td>
   </td>
   <td>Set the minimum speaker count.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>diarizationMaxSpeakers
   </td>
   <td>Number
   </td>
   <td>
   </td>
   <td>Set the maximum speaker count.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>interactionType
   </td>
   <td>String
   </td>
   <td>
   </td>
   <td>Set the interaction type: discussion, presentation, phone_call, voicemail, professionally_produced, voice_search, voice_command, dictation
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>naicsCode
   </td>
   <td>Number
   </td>
   <td>
   </td>
   <td>Set an industry NAICS code that is relevant to the speech.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>googleServiceVersion
   </td>
   <td>String
v1  or v2
   </td>
   <td>
   </td>
   <td>Specifies the version of Google's ASR API in use to ensure compatibility.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>googleRecognizerId
   </td>
   <td>String
   </td>
   <td>
   </td>
   <td>Identifies the specific speech recognition model for processing the input.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>googleSpeechStartTimeoutMs
   </td>
   <td>Number
   </td>
   <td>
   </td>
   <td>Set the time (in milliseconds) to wait for the speaker to start speaking before timing out.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>googleSpeechEndTimeoutMs
   </td>
   <td>Number
   </td>
   <td>
   </td>
   <td>Defines how long to wait (in milliseconds) for silence before determining the end of speech.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>googleEnableVoiceActivityEvents
   </td>
   <td>Boolean
   </td>
   <td>
   </td>
   <td>Enables detection of when the user starts or stops speaking during recognition.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>googleTranscriptNormalization
   </td>
   <td>Array
   </td>
   <td>
   </td>
   <td>Adjusts the transcript to make it more readable, applying corrections like punctuation and caseing.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td colspan="5" >
<h4><strong>AWS ASR</strong></h4>

   </td>
  </tr>
  <tr>
   <td>awsAccessKey
   </td>
   <td>String
   </td>
   <td>
   </td>
   <td>The AWS access key for authenticating requests.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>awsSecretKey
   </td>
   <td>String
   </td>
   <td>
   </td>
   <td>The corresponding secret key is used with the access key for AWS service authentication.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>awsSecurityToken
   </td>
   <td>String
   </td>
   <td>
   </td>
   <td>A temporary security token (optional) for requests that use AWS Security Token Service (STS).
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>awsRegion
   </td>
   <td>String
   </td>
   <td>
   </td>
   <td>Specifies the AWS region where the service requests will be sent (for example, us-west-2, eu-central-1).
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>String
   </td>
   <td>String
   </td>
   <td>
   </td>
   <td>The name of the vocabulary filter is used to filter certain words or phrases during transcription.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>awsVocabularyFilterName
   </td>
   <td>String
   </td>
   <td>
   </td>
   <td>The name of the vocabulary filter is used to filter certain words or phrases during transcription.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>awsVocabularyFilterMethod
   </td>
   <td>String/enum
  "remove",
   “mask",
   “tag”
   </td>
   <td>
   </td>
   <td>Specifies how words in the vocabulary filter are handled. It can take one of three values:
<ul>

<li><code>"remove"</code>: Completely remove the word from the transcription.</li>

<li><code>"mask"</code>: Mask the word (for example, replace it with asterisks).</li>

<li><code>"tag"</code>: Add tags to identify the filtered word.</li>
</ul>
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>awsLanguageModelName
   </td>
   <td>String
   </td>
   <td>
   </td>
   <td>The name of a custom language model is to be applied during transcription for better accuracy in a domain-specific language.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>awsPiiEntityTypes
   </td>
   <td>Array
   </td>
   <td>
   </td>
   <td>A list of PII (Personally Identifiable Information) entity types to be detected (for example, ["NAME", "EMAIL", "SSN"]). This helps the system identify and protect sensitive information during transcription.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>awsPiiIdentifyEntities
   </td>
   <td>Boolean
   </td>
   <td>
   </td>
   <td>A flag that indicates whether or not to identify and highlight PII entities within the transcribed text. If true, PII entities will be detected and processed according to the configuration.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td colspan="5" >
<h4><strong>Nvidia ASR</strong></h4>

   </td>
  </tr>
  <tr>
   <td>nvidiaRivaUri
   </td>
   <td>String
   </td>
   <td>
   </td>
   <td>grcp endpoint (ip:port) that Nvidia Riva is listening.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>nvidiaMaxAlternatives
   </td>
   <td>Number
   </td>
   <td>
   </td>
   <td>The number of alternatives to return.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>nvidiaProfanityFilter
   </td>
   <td>Boolean
   </td>
   <td>
   </td>
   <td>Indicates whether to remove profanity from the transcript.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>nvidiaWordTimeOffsets
   </td>
   <td>Boolean
   </td>
   <td>
   </td>
   <td>indicates whether to provide word-level detail.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>nvidiaVerbatimTranscripts
   </td>
   <td>Boolean
   </td>
   <td>
   </td>
   <td>Indicates whether to provide verbatim transcripts.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>nvidiaCustomConfiguration
   </td>
   <td>Object
   </td>
   <td>
   </td>
   <td>An object of key-value pairs that can be sent to Nvidia for custom configuration.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>nvidiaPunctuation
   </td>
   <td>Boolean
   </td>
   <td>
   </td>
   <td>Indicates whether to provide punctuation in the transcripts.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td colspan="5" >
<h4><strong>Deepgram ASR</strong></h4>

   </td>
  </tr>
  <tr>
   <td>deepgramApiKey
   </td>
   <td>String
   </td>
   <td>
   </td>
   <td>Deepgram API key to authenticate with (overrides setting in Kore VG portal).
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>deepgramTier
   </td>
   <td>String
   </td>
   <td>
   </td>
   <td>Deepgram tier you would like to use ('enhanced', 'base').
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>sttModel
   </td>
   <td>String
   </td>
   <td>
   </td>
   <td>Deepgram model used to process submitted audio ('general', 'meeting', 'phonecall', 'voicemail', 'finance', 'conversationalai', 'video', 'custom').
   </td>
   <td>nova-2-phonecall
   </td>
  </tr>
  <tr>
   <td>deepgramCustomModel
   </td>
   <td>String
   </td>
   <td>
   </td>
   <td>Id of the custom model.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>deepgramVersion
   </td>
   <td>String
   </td>
   <td>
   </td>
   <td>Deepgram version of the model used.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>deepgramPunctuate
   </td>
   <td>Boolean
   </td>
   <td>
   </td>
   <td>Indicates whether to add punctuation and capitalization to the transcript.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>deepgramProfanityFilter
   </td>
   <td>Boolean
   </td>
   <td>
   </td>
   <td>Indicates whether to remove profanity from the transcript.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>deepgramRedact
   </td>
   <td>Object
<code>{
        "type": "string",
        "enum": [
          "pci",
          "numbers",
          "true",
          "ssn"
        ]
      },</code>
   </td>
   <td>
   </td>
   <td>Whether to redact information from transcripts ('pci', 'numbers', 'true', 'ssn')
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>deepgramDiarize
   </td>
   <td>Boolean
   </td>
   <td>
   </td>
   <td>Whether to assign a speaker to each word in the transcript.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>deepgramDiarizeVersion
   </td>
   <td>String
   </td>
   <td>
   </td>
   <td>If set to '2021-07-14.0' the legacy diarization feature will be used.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>deepgramNer
   </td>
   <td>Boolean
   </td>
   <td>
   </td>
   <td>
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>deepgramMultichannel
   </td>
   <td>Boolean
   </td>
   <td>
   </td>
   <td>Indicates whether to transcribe each audio channel independently.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>deepgramAlternatives
   </td>
   <td>Number
   </td>
   <td>
   </td>
   <td>The number of alternative transcripts to return.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>deepgramNumerals
   </td>
   <td>Boolean
   </td>
   <td>
   </td>
   <td>Indicates whether to convert numbers from written format (for example, one) to numerical format (for example, 1).
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>deepgramSearch
   </td>
   <td>Array
   </td>
   <td>
   </td>
   <td>An array of terms or phrases to search for in the submitted audio.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>deepgramReplace
   </td>
   <td>Array
   </td>
   <td>
   </td>
   <td>An array of terms or phrases to search for in the submitted audio and replace.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>deepgramKeywords
   </td>
   <td>Array
   </td>
   <td>
   </td>
   <td>An array of keywords to which the model should pay particular attention to boosting or suppressing to help it understand the context.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>deepgramEndpointing
   </td>
   <td>Boolean | Number
   </td>
   <td>
   </td>
   <td>Indicates the number of milliseconds of silence Deepgram will use to determine whether a speaker has finished saying a word or phrase. The value provided must be either several milliseconds or 'false' to disable the feature entirely. <strong>Note</strong>: The default endpoint value that Deepgram uses is 10 milliseconds. You can set this value higher to allow to require more silence before a final transcript is returned but we suggest a value of 1000 (one second) or less, as we have observed strange behaviors with higher values. If you wish to allow more time for pauses during a conversation before returning a transcript, we suggest using the utteranceEndMs feature instead.	
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>deepgramVadTurnoff
   </td>
   <td>Number
   </td>
   <td>
   </td>
   <td>
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>deepgramTag
   </td>
   <td>String
   </td>
   <td>
   </td>
   <td>A tag to associate with the request. Tags appear in usage reports.	
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>deepgramUtteranceEndMs
   </td>
   <td>Number
   </td>
   <td>
   </td>
   <td>This parameter is used to configure ASR to detect the end of speech in live-streaming audio.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>deepgramShortUtterance
   </td>
   <td>Boolean
   </td>
   <td>
   </td>
   <td>This causes a transcript to be returned as soon as the Deepgram is_final property is set. This should only be used in scenarios where you are expecting a very short confirmation or directed command and you want minimal latency.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>deepgramSmartFormatting
   </td>
   <td>Boolean
   </td>
   <td>
   </td>
   <td>Indicates whether to enable Deepgram's Smart Formatting feature.
Deepgram's Smart Format feature applies additional formatting to transcripts to optimize them for human readability.

Smart Format capabilities vary between models. When Smart Format is turned on, Deepgram will always apply the best-available formatting for your chosen combination of model, model option, and language.
   </td>
   <td>
   </td>
  </tr>
</table>

### Common TTS Parameters

<table>
  <tr>
   <td><strong>Parameter</strong>
   </td>
   <td><strong>Type</strong>
   </td>
   <td><strong>Supporting STT/ TTS</strong>
   </td>
   <td><strong>Description</strong>
   </td>
   <td><strong>Examples</strong>
   </td>
  </tr>
  <tr>
   <td>disableTtsCache
   </td>
   <td>Boolean
   </td>
   <td>ALL
   </td>
   <td>Using cache for calling TTS engine if same statement or word found.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>ttsEnhancedVoice
   </td>
   <td>String
   </td>
   <td>AWS
   </td>
   <td>Amazon Polly has four voice engines that convert input text into life-like speech. These include Generative, Long-form, Neural, and Standard. To use an Amazon Polly voice
   </td>
   <td>Examples
    standard" , 
"   neural",
   "generative",
 "  long-form"
   </td>
  </tr>
  <tr>
   <td>ttsGender
   </td>
   <td>String
MALE, FEMALE, NEUTRAL
   </td>
   <td> Google
   </td>
   <td>
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>ttsLoop
   </td>
   <td>Number / String
   </td>
   <td>ALL
   </td>
   <td>The <strong>ttsLoop</strong> parameter is used in Text-to-Speech (TTS) systems to control the repeated playback of a TTS-generated message. When <strong>ttsLoop</strong> is enabled, the specified TTS message will be played multiple times in a loop, which is useful in scenarios where you want to ensure the message is heard clearly, or when the user might need more time to process the information.
   </td>
   <td>Example - ttsLoop = 2
Text will be played twice
   </td>
  </tr>
  <tr>
   <td>earlyMedia
   </td>
   <td>Boolean
   </td>
   <td>ALL
   </td>
   <td>The <strong>Early Media</strong> parameter in TTS (Text-to-Speech) is used to control the playback of audio prompts or messages before a call is fully connected. This feature is typically employed in telecommunication systems, allowing messages to be played while the call is still in the "early" phase, meaning before the recipient answers the call.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>ttsOptions
   </td>
   <td>Object
   </td>
   <td>PlayHt, Deepgram, ElevenLabs, Whisper
   </td>
   <td>It is used to tune the TTS.
   </td>
   <td>
   </td>
  </tr>
</table>

## TTS Options in Kore VG

Kore VG now supports a `ttsOptions` parameter that allows bot developers to customize Text-to-Speech (TTS) messages by passing dynamic objects tailored to the specific TTS provider. Depending on the provider, these options can be used to fine-tune aspects like voice settings, speed, and other properties.

!!! Note

    Each TTS provider will have its own set of customizable parameters. For more detailed information on the parameters they support, refer to their official websites.

### Structure of `ttsOptions`

The `ttsOptions` object contains provider-specific settings in a key-value format. Below are examples of different TTS providers:

#### ElevenLabs

* `optimize_streaming_latency`: Adjusts the latency during streaming.
* `voice_settings`: Includes various voice customization options like `stability`, `similarity_boost`, and `use_speaker_boost`. [Learn more](https://elevenlabs.io/docs/speech-synthesis/voice-settings).

#### PlayHT

* `quality`: Sets the quality of the audio output.
* `speed`: Controls the playback speed.
* `emotion`, `voice_guidance`, `style_guidance`, and `text_guidance`: Allow further customization of the voice's emotional tone and style. [Learn more](https://docs.play.ht/reference/api-generate-tts-audio-stream).

#### Deepgram

Apart from generic parameters like `ttsLanguage` and `voiceName`, which are common across most TTS engines, Deepgram offers a few additional parameters that enhance customization:

* **encoding (string)**: You can specify the desired encoding format for the output audio file, such as `mp3` or `wav`.
* **model (enum)**: Defines the AI model to be used for synthesizing the text into speech. The default model is `aura-asteria-en`, optimized for natural-sounding English voice output.
* **sample_rate (string)**: This enables you to set the sample rate of the audio output, offering control over the quality and clarity of the sound produced.
* **Container**: The Container feature allows users to specify the desired file format wrapper for the output audio generated through text-to-speech synthesis.

These parameters provide additional flexibility for developers to fine-tune the audio output to meet their specific needs. All these parameters will be set inside ttsOptions. [Learn more](https://developers.deepgram.com/docs/tts-rest).

#### AWS

Apart from generic parameters like `ttsLanguage` and `voiceName`, which are common across most TTS engines, Aws offers a few additional parameters that enhance customization, like ttsEnhanceVoice, also known as an engine.

Amazon Polly has four voice engines that convert input text into lifelike speech. These include “standard," "neural," "generative," and "long-form." 

`ttsEnhancedVoice = “neural”`

#### Open AI (Whisper)

Apart from generic parameters like `ttsLanguage` and `voiceName`, which are common across most TTS engines, Whisper offers a few additional parameters that enhance customization, like a model.

For real-time applications, the standard tts-1 model provides the lowest latency but at a lower quality than the tts-1-hd model. Due to how the audio is generated, tts-1 is likely to generate more static content in certain situations than tts-1-hd. In some cases, the audio may not have noticeable differences depending on your listening device and the person.

```
ttsOptions = {
   model = "tts-1"
}
```
### Primary and Fallback ASR/TTS

ASR/TTS Fallback functionality can be implemented at various levels within the system, such as the application level, experience flow level, or even the call control parameter level. This mechanism ensures that if there is an error or failure with the primary ASR (Automatic Speech Recognition) or TTS (Text-to-Speech) service, the system will automatically switch to a secondary, or fallback, ASR/TTS configuration. By doing this, the fallback prevents interruptions in the service and ensures a seamless user experience, regardless of issues with the primary configuration.
* For optimal performance, it’s advised to configure the fallback with the same vendor in a different region/label.

### Configure Primary and Fallback ASR/TTS

**Location 1 - Global Setting**

In SmartAssist: **Configurations** > **System Setup** > **Language & Speech** > **Voice Preferences** > **Show Advanced Settings**.  
<img src="../images/show-advanced-settings.png" alt="Show Advanced Settings" title="Show Advanced Settings" style="border: 1px solid gray; zoom:80%;">

**Location 2 - Call Control Parameters**

In SmartAssist: **Automation** > **Select bot** > **Conversational Skills** > **Dialog Tasks** > **Select Dialog Task** > **Select the Node you want to configure** > **IVR Properties** > **Advance Controls** > **Call Control Parameters**.  
<img src="../images/call-control-parameters.png" alt="Call Control Parameters" title="Call Control Parameters" style="border: 1px solid gray; zoom:80%;">

**Location 3 - Experience Flows**

In SmartAssist: **Configurations** > **Experience Flows** > **Update/New Experience Flow** > **Speech Recognition Engine (ASR/TTS)** > **Show Advanced Settings**.  
<img src="../images/experience-flows-advanced-settings.png" alt="Experience Flows" title="Experience flows" style="border: 1px solid gray; zoom:80%;">  

<img src="../images/edit-experience-flows.png" alt="Edit Experience Flows" title="Edit Experience Flows" style="border: 1px solid gray; zoom:80%;">

**Location 4 - Start Node in Experience Flow**  
<img src="../images/start-node.png" alt="Start Node" title="Start Node" style="border: 1px solid gray; zoom:80%;">  
<img src="../images/start-node-experience-flow.png" alt="Start Node - Experience Flow" title="Start Node - Experience Flow" style="border: 1px solid gray; zoom:80%;">

!!! Note
      
      * This feature is available only in ‘SmartAssist’ and not implemented in ‘XO11’. We will implement it in the next releases. 
      * For now, you can add Primary & Fallback ASR/TTS from the same vendor only.
         * Example: If you have selected the ‘Microsoft Azure Speech Services’ vendor as the ASR, you can enter a label name from the Microsoft vendor itself, such as ‘my_azure-US’.
         * You can configure the label name in Primary ASR/TTS configuration and Fallback ASR/TTS configuration under Show Advanced Settings.
         * The fallback ASR/TTS configuration should not be the same as the Primary ASR/TTS configuration.
         * Both Primary and Fallback ASR/TTS configurations should be available in SAVG Speech Services otherwise you will not be able to configure in SmartAssist.
         * The Credential Status of the Speech services configured in SAVG should be verified. If credential status is failed then ASR/TTS conversations will fail.
      * In Call control parameters, 
         * You can configure the fallback for different vendors. But for optimal performance, it’s advised to configure the fallback with the same vendor in a different region.
         * In-call control parameters don’t have any validation of duplicate values for Primary and Fallback configurations, so you have to pay closer attention to spelling mistakes. [Learn more](#call-control-parameters).

## Voice Gateway Properties

<table>
  <tr>
   <td><strong>Parameter</strong>
   </td>
   <td><strong>Type</strong>
   </td>
   <td><strong>Supporting STT/ TTS</strong>
   </td>
   <td><strong>Description</strong>
   </td>
   <td><strong>Examples</strong>
   </td>
  </tr>
  <tr>
   <td colspan="5" >
<h4><strong>Provider related parameters</strong></h4>

<strong>Speech-to-text and text-to-speech services interface with the user using a selected language (for example, English US, English UK, or German). Text-to-speech services also use a selected voice to speak to the user (for example, female or male).</strong><br>
<strong>For Recognizer, Speech-to-text is used, and for synthesizer, Text to Speech</strong><br>
<strong>sttProvider => google,microsoft  => Recognizer</strong><br>
<strong>ttsProvider => google,microsoft,aws => Synthesizer</strong><br>
<strong>JSON example:</strong><br>
<code>{</code><br>
<code>sttProvider : “google”,</code><br>
<code>sttLangauge:”en-IN”</code><br>
<code>ttsProvider : “google”</code><br>
<code>Language : “en-IN”,</code><br>
<code>voiceName :”‘en-IN-Wavenet-A”</code><br>
<code>}</code><br>
<strong>For applying the below parameters we always have to use the STT engine as Recognizer otherwise the default is applied that was set as bot level or koreVG/SmartAssist application</strong><br>
<strong>Note: Provider Properties will be Applied at the Session Level</strong>
   </td>
  </tr>
  <tr>
   <td>sttProvider
   </td>
   <td>String
   </td>
   <td>ALL
   </td>
   <td>To Set the Speech to Text Engine
At any stage of the call, the bot can dynamically change the speech provider (speech-to-text or text-to-speech) of the call. The provider change can be done for the entire call duration (the current text/audio that is played by the bot).
   </td>
   <td>sttProvider : “google”
   </td>
  </tr>
  <tr>
   <td>sttLanguage
   </td>
   <td>String
   </td>
   <td>ALL
   </td>
   <td>	
To set STT Language in for recognizing user's voice
Note:  Transcript will come according to sttLanguage
sttLangauge = “zh-CN”
All transcripts will come in Chinese
Defines the language (for example, "en-ZA" for South African English) of the bot conversation and is used for the speech-to-text service.
   </td>
   <td>sttLanguage = “en-US”
   </td>
  </tr>
  <tr>
   <td>ttsProvider
   </td>
   <td>String
   </td>
   <td>ALL
   </td>
   <td>Silimar to STT Provider
   </td>
   <td>ttsProvider:”microsoft”
   </td>
  </tr>
  <tr>
   <td>ttsLanguage
   </td>
   <td>String
   </td>
   <td>ALL 
   </td>
   <td>Similar To sttLanguage
The parameter is required to set TTS  languages.
   </td>
   <td>Ex ttsLanguage = “en-US”
   </td>
  </tr>
  <tr>
   <td>voiceName
   </td>
   <td>String
sttLanguage : ‘en-AU’,
   </td>
   <td>ALL
   </td>
   <td>voiceName is mandatory to text to speech conversion.
Voice name should be correctly aligned to ttsLanguage.
VoiceName is used in TTS only for bot response.
   </td>
   <td>voiceName : ‘en
-AU-NatashaNeural’
For example - 
<code>{
ttsPrrovider : ‘microsoft’,
sttLanguage : ‘en-AU’,
voiceName : ‘en-AU-NatashaNeural’
}</code>
   </td>
  </tr>
  <tr>
   <td>enableSpeechInput
   </td>
   <td>Boolean
   </td>
   <td> All
   </td>
   <td>If False, Allow only DTMF Input, By default It is always true and can be used in entity nodes
Do not use this in Channel Over-rider Script. It is meant to be used only through the Call Control Parameter.
   </td>
   <td>Example - enableSpeechInput: false
   </td>
  </tr>
  <tr>
   <td colspan="5" >
<h4><strong>Labels and Fallback Providers</strong></h4>

<strong>Label - Assign/Create a label only if you need to create multiple speech services from the same vendor. Then, use the label in your application to specify which service to use.</strong>
<strong>How to Configure Label</strong><br>
<strong>(1) Add a speech service Inside the speech tab. </strong><br>
<strong>(2) Select a provider and add a label with a unique name.</strong><br>
<strong>(3) Use the same label in the call control parameter.</strong><br>
<strong>(4) The NODE at which you use FallBack Call control parameters at the Same node Primary Recognizer and Synthesizer is NECESSARY to pass.</strong><br>
<strong>  Examples:</strong><br>
<strong>  sttProvider = “google”,</strong><br>
<strong>  sttLanguage = “en-US”,</strong><br>
<strong>  sttLabel = “google-stt-2”</strong><br>
<strong>Examples:</strong><br>
<strong>STT</strong><br>
<strong>  “sttProvider”: “microsoft”,</strong><br>
<strong>  “sttLabel”: “my_azure-US”,</strong><br>
<strong>  “sttLanguage: “en-US”</strong><br>
<strong> TTS </strong><br>
<strong>   “ttsProvider” : “microsoft”,</strong><br>
<strong>   “ttsLanguage”: “en-US”,</strong><br>
<strong>   “voiceName”: “en-US-AmberNeural”</strong><br>
<strong>   “ttsLabel” : “my_azure-US”</strong><br>
<strong>FallBack Examples</strong><br>
<strong>  “sttProvider” : “microsoft”,</strong><br>
<strong>  “sttLabel” : “my_azure-US”,</strong><br>
<strong>  “sttLanguage: “en-US”</strong><br>
<strong>   “ttsProvider” : “microsoft”,</strong><br>
<strong>   “ttsLanguage”: “en-US”,</strong><br>
<strong>   “voiceName”: “en-US-AmberNeural”</strong><br>
<strong>   “ttsLabel” : “my_azure-US”</strong><br>
<strong>  “sttFallbackProvider” : “microsoft”,</strong><br>
<strong>   “sttFallbackLanguage: “en-US”,</strong><br>
<strong>   “sttFallbackLabel”:”my_azure_Europe”</strong><br>
<strong>   “ttsFallbackProvider” : “microsoft”,</strong><br>
<strong>   “ttsFallbackLanguage” : “en-US”</strong><br>
<strong>   “ttsFallbackLabel” : “my_azure_Europe”</strong><br>
<strong>   “ttsFallbackVoiceName”: “en-US-AmberNeural”</strong><br>
<strong>Notes: <br>The NODE at which you use FallBack call control parameters, at the same node Primary Recognizer and Synthesizer is NECESSARY to pass.</strong>
<strong>The best practice is to keep the same ASR Engine in Fallback with a different Label.</strong>
<strong>If the current provider fails, Kore VG will pick a fallback provider. Similarly, we can add a Fallback for the TTS Provider.</strong><br>
<strong>Fallback properties will be applied at the session level.</strong>
   </td>
  </tr>
  <tr>
   <td>sttLabel
   </td>
   <td>String
   </td>
   <td>
   </td>
   <td>Uniquely identify ASR engine in Kore VG.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>sttFallbackLabel
   </td>
   <td>String
   </td>
   <td>
   </td>
   <td>If fallback is enabled in Kore VG at the application level, then in case of any error the switch will happen of ASR to fallback configuration, it is recommended to have a fallback to the same vendor with a different region. 
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>sttFallbackProvider
   </td>
   <td>String
   </td>
   <td>
   </td>
   <td>Fallback provider details 
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>sttFallbackLanguage
   </td>
   <td>String
   </td>
   <td>
   </td>
   <td>Fallback language details 
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>ttsLabel
   </td>
   <td>String
   </td>
   <td>
   </td>
   <td>Uniquely identify TTS engine in Kore VG
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>ttsFallbackLabel
   </td>
   <td>String
   </td>
   <td>
   </td>
   <td>Fallback Label details 
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>ttsFallbackProvider
   </td>
   <td>String
   </td>
   <td>
   </td>
   <td>Fallback provider details 
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>ttsFallbackLanguage
   </td>
   <td>String
   </td>
   <td>
   </td>
   <td>Fallback language details 
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>ttsFallbackVoice
   </td>
   <td>String
   </td>
   <td>
   </td>
   <td>Fallback voice details
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td colspan="5" >
<h4><strong>Continuous ASR</strong></h4>

Continuous ASR (automatic speech recognition) is a feature that allows speech-to-text (STT) recognition to be tuned for the collection of things like phone numbers, customer identifiers, and other strings of digits or characters, which, when spoken, often have pauses between utterances.<br> 
<strong>Note: For Only Microsoft </strong>
Microsoft Azure Introduces one ASR Property that works the same way as Continuous ASR, <strong>AzureSegmentationSilenceTimeout</strong>. Since Silence is detected by ASR Engine Directly Instead of Voice Gateway, detect and merge the response. AzureSegmentationSilenceTimeout is more accurate than continuous ASR. <a href="https://learn.microsoft.com/en-us/azure/ai-services/speech-service/how-to-recognize-speech?pivots=programming-language-csharp#change-how-silence-is-handled">Learn more</a>.<br>
<strong>Note</strong>: Continuous ASR/AzureSegmentationSilenceTimeout is applied at the session level. Throughout the Call, it will be active, and the developer can adjust the value at different nodes based on the requirement.
   </td>
  </tr>
  <tr>
   <td>continuousASRTimeoutInMS
   </td>
   <td>Number in millisecond 
   </td>
   <td>ALL
   </td>
   <td>This is a duration of silence, in seconds, to wait after a transcript is received from the STT vendor before returning the result. If another transcript is received before this timeout elapses, then the transcripts are combined and recognition continues. The combined transcripts are returned once a timeout between utterances exceeds this value
   </td>
   <td>For example - 5000 for  5 sec
   </td>
  </tr>
  <tr>
   <td>continuousASRDigits
   </td>
   <td>Any digit  For example - *,%,&,#
   </td>
   <td>ALL
   </td>
   <td>a DTMF key which, if entered, will also terminate the gather operation and immediately return the collected results
   </td>
   <td>continuousASRDigits : &
   </td>
  </tr>
  <tr>
   <td colspan="5" >
<h4><strong>Barge-IN</strong></h4>

The Barge-In feature controls Kore VG behavior in scenarios where the user starts speaking or dials DTMF digits while the bot is playing its response to the user. In other words, the user interrupts ("barges-in") the bot.<br>
<strong>Note: </strong>Barge-in Will be applied at the Node level. 
   </td>
  </tr>
  <tr>
   <td>listenDuringPrompt
   </td>
   <td>Boolean - True or False
   </td>
   <td>ALL 
   </td>
   <td>If false, do not listen for user speech until the bot has finished playing its response to the user. Defaults to true
Similar to Barge-in.	
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>bargeInMinWordCount
   </td>
   <td>Number
   </td>
   <td>ALL
   </td>
   <td>If barge-in is true, only kill speech when this many words are spoken. Defaults to 1.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>bargeInOnDTMF
   </td>
   <td>Boolean
   </td>
   <td>ALL
   </td>
   <td>Press any key to enable DTMF, and kill audio playback if the caller enters DTMF then you can tell your utterance or speech.
   </td>

  </tr>
  <tr>
   <td colspan="5" >
<h4><strong>Timeout related parameters</strong></h4>

<strong>Note: </strong>All Timeout Parameters will be applied at the Node level.
   </td>
  </tr>
  <tr>
   <td>userNoInputTimeoutMS
   </td>
   <td>Number in millisecond
1 sec - 1000
   </td>
   <td>ALL
   </td>
   <td>Define the maximum wait time to receive user input
If userNoInputTimeoutMS = 0
Kore VG will wait for an infinite time for User Input.
Defines the maximum time (in milliseconds) that VoiceAI Connect waits for input from the user.
   </td>
   <td>userNoInputTimeoutMS = 20000
   </td>
  </tr>
  <tr>
   <td>dtmfCollectInterDigitTimeoutMS
   </td>
   <td>Number - Time in milliseconds
   </td>
   <td>ALL
   </td>
   <td>Defines the timeout that Kore VG waits for the user to press another digit before it sends all the digits to the bot.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>dtmfCollectSubmitDigit
   </td>
   <td>Number
   </td>
   <td>ALL
   </td>
   <td>Defines a special DTMF "submit" digit that when received from the user, KoreVg immediately sends all the collected digits to the bot (as a DTMF message), without waiting for the timeout to expire or for the maximum number of expected digits.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>dtmfCollectMaxDigits
   </td>
   <td>Number
   </td>
   <td>ALL
   </td>
   <td>Maximum number of DTMF digits expected to gather
Example If maxDigit = 5 
So Bot will take only a maximum of 5 digits Input 1234567 bot takes only 12345.
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>dtmfCollectminDigits
   </td>
   <td>Number
   </td>
   <td>ALL
   </td>
   <td>Minimum number of DTMF digits expected to gather. Defaults to 1
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>dtmfCollectnumDigits
   </td>
   <td>Number
   </td>
   <td>ALL
   </td>
   <td>The exact number of DTMF digits is expected to be gathered.
   </td>
   <td>
   </td>
  </tr>
</table>