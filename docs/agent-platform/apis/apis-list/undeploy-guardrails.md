# Undeploy Guardrails API

This API removes the previously deployed guardrails that regulate AI interactions.

Once undeployed, the guardrails become inactive. The API response includes the **model ID** and the **guardrail undeployment status**. After receiving the response, use the <code>dockStatusId</code> to call the [Get Dock Status API](../apis-list/get-dock-status.md){:target="_blank"} and verify the guardrail undeployment status.


<table>
  <tr>
   <td><strong>Method</strong>
   </td>
   <td>POST
   </td>
  </tr>
  <tr>
   <td><strong>Endpoint</strong>
   </td>
   <td><code>https://{host}/api/public/guardrails/undeploy</code>
   </td>
  </tr>
  <tr>
   <td><strong>Content Type</strong>
   </td>
   <td>application/json
   </td>
  </tr>
  <tr>
   <td><strong>Authorization</strong>
   </td>
   <td><strong><code>X-api-key</code></strong> - The API key used for authentication.
   </td>
  </tr>
</table>

**Where can I find the API key?** [Learn more](../overview.md/#how-to-find-the-api-key){:target="_blank"}.

## Path Parameters

<table>
  <tr>
   <td><strong>PARAMETER</strong>
   </td>
   <td><strong>DESCRIPTION</strong>
   </td>
   <td><strong>TYPE</strong>
   </td>
   <td><strong>REQUIRED/OPTIONAL</strong>
   </td>
   <td><strong>ENUM VALUES</strong>
   </td>
  </tr>
  <tr>
   <td><strong>host</strong>
   </td>
   <td>The environment URL. For example, <code>https://agent-platform.kore.ai</code>
   </td>
   <td>String
   </td>
   <td>Required
   </td>
   <td>
    The allowed guardrails include:
<ul>

<li><strong>Anonymize</strong> – Ensures sensitive information is anonymized.</li>

<li><strong>Ban topics</strong> – Restricts discussions on specific topics.</li>

<li><strong>Prompt injection</strong> – Prevents unauthorized prompt manipulation.</li>

<li><strong>Toxicity</strong> – Detects and filters toxic language.</li>

<li><strong>Bias detection</strong> – Identifies and mitigates biased responses.</li>

<li><strong>Relevance </strong>– Ensures responses stay relevant to the conversation</li>
</ul>
   </td>
  </tr>
</table>


## Sample Request

```js
curl --location 'https://agent-platform.kore.ai/api/public/guardrails/undeploy' \
--header 'x-api-key: kg-axxxxxxx-xxxx-5xx8-bxxb-9xxxxxxxxxx-ebxxxxxx-5xxb-4xxb-9xx5-cxxxxxxxxx3' \
--header 'Content-Type: application/json' \
--data '{"name": "Ban topics"}'
```

## Body Parameters

<table>
  <tr>
   <td><strong>PARAMETER</strong>
   </td>
   <td><strong>DESCRIPTION</strong>
   </td>
   <td><strong>TYPE</strong>
   </td>
   <td><strong>REQUIRED/OPTIONAL</strong>
   </td>
  </tr>
  <tr>
   <td><strong>name</strong>
   </td>
   <td>Name of the guardrail you want to undeploy.
   </td>
   <td>Enum
   </td>
   <td>Required
   </td>
  </tr>
</table>

## Sample Response

```js
{
   "dockStatusId": "ds-exxxxxx7-2xx8-5xxc-axx7-caxxxxxxxxx1",
   "toolId": "a-4xxxxxx9-fxx9-5xx7-axx7-9xxxxxxxxxxb",
   "jobType": "GUARDRAILS",
   "action": "DEPLOY",
   "status": "SUCCESS"
}
```

## Response Parameters

<table>
  <tr>
   <td><strong>PARAMETER</strong>
   </td>
   <td><strong>DESCRIPTION</strong>
   </td>
   <td><strong>TYPE</strong>
   </td>
  </tr>
  <tr>
   <td><strong>dockStatusId</strong>
   </td>
   <td>The unique identifier to track the process status.
   </td>
   <td>String
   </td>
  </tr>
  <tr>
   <td><strong>guardrail</strong>
   </td>
   <td>The guardrail you want to undeploy.
   </td>
   <td>String
   </td>
  </tr>
  <tr>
   <td><strong>jobType</strong>
   </td>
   <td>Type of job being performed. (e.g., "<em>GUARDRAIL</em>").
   </td>
   <td>String
   </td>
  </tr>
  <tr>
   <td><strong>action</strong>
   </td>
   <td>The action performed on the guardrail, i.e. “<em>UNDEPLOY</em>.”.
   </td>
   <td>String
   </td>
  </tr>
  <tr>
   <td><strong>status</strong>
   </td>
   <td>The current status of the job ("<em>SUCCESS</em>", "<em>IN_PROGRESS</em>", or "<em>FAILED</em>").
   </td>
   <td>String
   </td>
  </tr>
</table>