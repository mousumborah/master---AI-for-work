# Undeploy a Tool API

This API undeploys a tool that is deployed in an environment. 

The API response includes the **tool ID** and the **tool undeployment status**. After receiving the response, use the <code>dockStatusId</code> to call the [Get Dock Status API](../apis-list/get-dock-status.md){:target="_blank"} and verify the tool undeployment status.


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
   <td><code>https://{<em>host</em>}/api/public/tools/:{<em>toolId</em>}/undeploy</code>
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
  </tr>
  <tr>
   <td><strong>host</strong>
   </td>
   <td>The environment URL. For example, <code>https://gale.kore.ai</code>
   </td>
   <td>String
   </td>
   <td>Required
   </td>
  </tr>
  <tr>
   <td><strong>toolId</strong>
   </td>
   <td>The unique identifier of the tool being undeployed.
   </td>
   <td>String
   </td>
   <td>Required
   </td>
  </tr>
</table>

## Sample Request

```js
curl --location --request POST 'https://dev-axxxt-plxxxxxm.kore.ai/api/public/tools/a-0xxxxxxxxxxxxxxxxxxe/undeploy' \
--header 'x-api-key: kg-axxxxxxx-5xx3-5xx8-bxxb-9xxxxxxxxxx-ebxxxxxxxxxxx3'
```

## Body Parameters

No parameters are passed.

## Sample Response

```js
{
   "dockStatusId": "ds-exxxxxx7-2xx8-5xxc-axx7-cxx73xxxxxx1",
   "toolId": "a-4xxxxxx9-fxx9-5xx7-axx7-9xxfdxxxxxxb",
   "jobType": "TOOLS",
   "action": "UNDEPLOY",
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
   <td>The unique identifier for tracking the tool undeployment status.
   </td>
   <td>String
   </td>
  </tr>
  <tr>
   <td><strong>toolId</strong>
   </td>
   <td>The unique identifier of the tool being undeployed.
   </td>
   <td>String
   </td>
  </tr>
  <tr>
   <td><strong>jobType</strong>
   </td>
   <td>The type of job being performed (“<em>TOOLS</em>”).
   </td>
   <td>String
   </td>
  </tr>
  <tr>
   <td><strong>action</strong>
   </td>
   <td>The action being performed ("<em>UNDEPLOY</em>").
   </td>
   <td>String
   </td>
  </tr>
  <tr>
   <td><strong>status</strong>
   </td>
   <td>The undeployment status ("<em>SUCCESS</em>", "<i>IN_PROGRESS</i>", or <em>"FAILED</em>").
   </td>
   <td>String
   </td>
  </tr>
</table>