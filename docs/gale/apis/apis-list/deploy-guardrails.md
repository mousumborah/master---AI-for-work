# Deploy Guardrails API

This API deploys predefined **guardrails** to enhance security, compliance, and content moderation in AI interactions. These guardrails act as filters or constraints to ensure safe and appropriate AI responses.

Users can deploy a specific guardrail from a predefined set of options, including:

* Anonymization
* Ban Topics
* Prompt Injection Prevention
* Toxicity Detection
* Bias Detection
* Relevance Filtering

Once deployed, the selected guardrail becomes active, regulating interactions within the environment.

The API response includes the **model ID** and the **guardrail deployment status**. After receiving the response, use the <code>dockStatusId</code> to call the [Get Dock Status API](../apis-list/get-dock-status.md){:target="_blank"} and verify the successful deployment of the guardrail.

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
   <td><code>https://{<i>host</i>}/api/public/guardrails/deploy</code>
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
   <td>The environment URL. For example, <code>https://gale.kore.ai</code>.
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
curl --location 'https://dev-axxxxt-plxxxxxxm.kore.ai/api/public/guardrails/deploy' \ 
--header 'x-api-key: kg-axxxxxxx-5xx3-5xx8-bxxxxxx-5xxb-4xxb-9xx5-cxxxxxxxxx3' \ 
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
   <td><b>name</b>
   </td>
   <td>The name of the guardrail you want to deploy.
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
  "dock-statusId": "ds-d0xxxxxd-bxx9-5xx0-8xx5-5bxxxxxxxxx1",
  "modelId": "cm-77xxxxxb-exx9-5xxc-8xx6-5xxxxxxxxxx1",
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
   <td>The unique identifier to track the status of model deployment.
   </td>
   <td>String
   </td>
  </tr>
  <tr>
   <td><strong>modelId</strong>
   </td>
   <td>The unique identifier for the model.
   </td>
   <td>String
   </td>
  </tr>
  <tr>
   <td><strong>jobType</strong>
   </td>
   <td>Type of job being performed (e.g: "<i>GUARDRAIL</i>").
   </td>
   <td>String
   </td>
  </tr>
  <tr>
   <td><strong>action</strong>
   </td>
   <td>The action performed on the model, i.e. "<i>DEPLOY</i>".
   </td>
   <td>String
   </td>
  </tr>
  <tr>
   <td><strong>status</strong>
   </td>
   <td>The current status of the job ("<i>SUCCESS</i>", "<i>IN_PROGRESS</i>", or "<i>FAILED</i>").
   </td>
   <td>String
   </td>
  </tr>
</table>

