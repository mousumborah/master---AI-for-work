# Queue Size

To get the queueDetails by giving queueId and filters with the given stream Id.

| **Method**       | POST                                                           |
|--------------|----------------------------------------------------------------|
| **Endpoint**     | `https://{host}/agentassist/api/v1/public/{{:streamId}}/monitor/queueStatsById/{{:queueId}}` |
| **Content Type** | `application/json`                                             |
| **Authorization**| `auth: {{JWT}}` <br>See [How to generate the JWT Token](../automation/api-introduction.md#generating-the-jwt-token)|
| **API Scope**    | SmartAssist Analytics                                          |

## Query Parameters

| **PARAMETER** | **DESCRIPTION**                                                       | **TYPE**          |
|-----------|-------------------------------------------------------------------|---------------|
| Host      | The Environment URL. For example, https://platform.kore.ai     | string, required |
| queueId   | You can get the queueId in the /queues GET API.                   | string, required |
| BotId     | BotId or StreamId. You can access it from the General Settings page of the bot. | string, required |

## Sample Request

```
curl --location 'https://{{host}}/agentassist/api/v1/public/st-3bf09bef-f979-5489-b337-f465bd5xxxx/monitor/queueStatsById/qu-895dc0c-a83e-4d25-9517-dbb2ccdaxxxx/' \
--header 'auth: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhcHBJZCI6ImNzLTNmYzQwYTcyLThiNGUtNWNlMy1iY2E3LThjYTcwZTQxYTQwZCJ9.ssiizteAJB0pdV2BYhILSRp12TAJ2V4cHWzpjp3SU8I' \
--header 'accountId: 637368b4a1d031234ba6xxxx' \
--header 'Content-Type: application/json' \
--data '{
"languages": ["en", "es"],
"channels": ["rtm", "msteams"]
}'
```
## Request Parameters

| PARAMETER | DESCRIPTION | REQUIRED/OPTIONAL | TYPE |
|-----------|-------------|-------------------|------|
| Channels  | To filter the results based on the channel. Only Contact Center AI supported channels can be given and should be selected from the following: <br> ["rtm", "ivr", "sms", "slack", "facebook", "kore", "spark", "skype", "msteams", "twitter", "telegram", "wfacebook", "ringcentral", "skypeforbusiness", "jabber", "yammer", "whatsapp", "line", "liveperson", "mattermost", "wechat", "web-sdk", "rcs", "skypeonprem", "unblu", "audiocodes", "alexa", "twiliovoice", "ivrVoice", "korevg", "email", "emailConnect"] <br> "rtm" : Web/Mobile Client channel <br> "ivr" : agent ai channel | optional | array of strings |
| Languages | To filter the results based on the bot language, that is, interaction language with the bot. Only Contact Center AI supported languages can be selected and should be selected from the following: <br> ["en", "de", "es", "fr", "pt", "it", "zh_cn", "zh_tw", "id", "ko", "nl", "ja", "ar", "fi", "ru", 'pl", "uk", "sv", "kk", "nb", "hi", "te", "ta", "mr", "ca", "sl", "ge" ] Here "en" : English "de" : German "es" : spanish "fr" : french "pt" : Portuguese "it" : Indonesian "zh_cn" : Chinese "zh_tw" : "id" : Indonesian "ko" : Korean "nl" : Dutch "ja" : Japanese "ar" : Arabic "fi" : Finnish "ru" : Russian "pl" : Polish "uk" : Ukrainian "sv" : Swedish "kk" : Kazakh "nb" : Norwegian "hi" : Hindi "te" : Telugu "ta" : Tamil "mr" : Marathi "ca" : Catalan "sl" : Slovenian "ge" : Georgia | 0ptional | array of strings |

## Sample Response

```
[
    {
        "queueId": "qu-aa16c29-08b2-4948-aa00-a6a3547exxxx",
        "queueName": "Default Queue",
        "skills": [],
        "waiting": 0,
        "engaged": 0,
        "dropOff": 44,
        "agentStatus": {
            "available": 1,
            "offline": 0,
            "busy": 0,
            "away": 0
        },
        "noOfAgents": 1,
        "queueSummary": {
            "avgWait": 0,
            "maxWait": 0,
            "ASA": 0  // ASA - Average Speed to Answer
        }
    }
]
```