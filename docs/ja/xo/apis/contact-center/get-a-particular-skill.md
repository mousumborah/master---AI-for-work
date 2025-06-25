# Get a Particular Skill

To retrieve the details of a particular skill with the given Stream Id, Skill Group Id, and Skill Id.

| **Method**       | GET                                                                             |
|--------------|---------------------------------------------------------------------------------|
| **Endpoint**     | `https://{{host}}/agentassist/api/v1/public/{{streamId}}/skill-groups/{{skillGroupId}}/skills/{{skillId}}` |
| **Content Type** | `application/json`                                                             |
| **Authorization**| `auth: {{JWT}}` <br>See [How to generate the JWT Token](../automation/api-introduction.md#generating-the-jwt-token) |
| **API Scope**    | SmartAssist Analytics                                                          |

## Path Parameters

| **PARAMETER**     | **DESCRIPTION**                                                                      | **TYPE**           |
|---------------|----------------------------------------------------------------------------------|----------------|
| host          | Environment URL, for example, https://platform.kore.ai                        | string, required |
| BotId         | BotId or StreamId. You can access it from the General Settings page of the bot. | String, Required |
| skillGroupId  | Id of the Skill Group.                                                           | string, required |
| skillId       | Id of the Skill.                                                                 | string, required |

## Sample Request

```
curl --location --request GET \
     'https://{{host}}/agentassist/api/v1/public/{{streamId}}/skill-groups/{{skillGroupId}}/skills/{{skillId}}' \
      --header 'auth: {jwt-code}' \
      --header 'Content-Type: application/json' \
```

## Sample Response

```
{
    "status": "ACTIVE",
    "name": "Account Management23",
    "description\"": "Manage Account",
    "skillGroupId": "606ac00ad75b272c78a15a07",
    "agents": [
        {
            "userId": "u-c7b23565-7e83-5099-8f26-f0a41a969f1a",
            "skillId": "607046a3630c9f077af51802",
            "createdBy": "u-c7b23565-7e83-5099-8f26-f0a41a969f1a",
            "orgId": "o-da05dbea-6573-5399-ba58-22035a3122f3",
            "proficiencyLevel": "high",
            "createdAt": "2021-04-09T12:20:51.246Z",
            "updatedAt": "2021-04-09T12:20:51.246Z",
            "id": "607046a3630c9f077af51803",
            "firstName": "Ravi",
            "lastName": "Kumar",
            "emailId": "ravi2@domain.com"
        }
    ],
    "createdBy": "u-c7b23565-7e83-5099-8f26-f0a41a969f1a",
    "createdAt": "2021-04-09T12:20:51.216Z",
    "updatedAt": "2021-04-09T12:20:51.216Z",
    "id": "607046a3630c9f077af51802"
}
```