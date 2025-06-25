
This document provides detailed instructions on the manual integration process of the Kore.ai Agent AI widget into a Genesys Cloud CX environment when using an **XO 11 App**. It offers step-by-step guidance to ensure a smooth and efficient setup process, covering all necessary aspects of integration from start to finish.

## Prerequisites
* Genesys Cloud account with sufficient admin rights.
* Kore.ai XO 11 Instance with at least one Dialog Task configured for Agent AI (https://platform.kore.ai).

## Manual Steps
After setting up the Genesys Cloud account, you must have proper permission to use the following Genesys components:

* OAuth Credentials
* Interaction Widget (Integration)
* Audiohook (Integration) – optional, if using Kore-managed Transcriptions.
* Data Table

### **Step 1: OAuth Credential**

An OAuth credential with proper permissions is required for the connection between the Kore.ai Agent AI interaction widget and the Kore.ai platform.

A Genesys OAuth ID is required to complete the URL formation for the Genesys interaction widget.

Steps to get Genesys OAuth ID:

1. Sign in to **Genesys Cloud**.
2. Go to **Admin** > **Integrations** > **OAuth**.  
<img src="../images/genesys-oauth-path-1.png" alt="genesys-oauth-path" title="genesys-oauth-path" style="border: 1px solid gray; zoom:80%;">
3. Click **Add Client**.  
<img src="../images/integ-oauth-add-client-2.png" alt="integ-oauth-add-client" title="integ-oauth-add-client" style="border: 1px solid gray; zoom:80%;">
4. Enter the app name, description, and token duration in the **App Name**, **Description**, and **Token Duration** fields.
5. Select **Token Implicit Grant (Browser)** in the **Grant Types** fields.
6. Add [https://agentassist.kore.ai/koreaiaa-genesys/](https://agentassist.kore.ai/koreaiaa-genesys/) in the **_Authorized redirect URIs (one per line)_** section.
7. Add the following list of scopes in the **Scope** section:
    *  architect
    *  conversations
    * conversations:readonly
    * integrations
    * integrations:readonly
    * messaging
    * messaging-platform
    * messaging-platform:readonly
    * messaging:readonly
    * notifications
    * user-basic-info
    * web-chat
    * web-chat:readonly

<img src="../images/oauth-client-details-3.png" alt="oauth-client-details" title="oauth-client-details" style="border: 1px solid gray; zoom:80%;">

<img src="../images/oauth-client-details-second-image-4.png" alt="oauth-client-details-second-image" title="oauth-client-details-second-image" style="border: 1px solid gray; zoom:80%;">

After saving the configuration, you will get the Client Id of the created OAuth client. Copy the ID and have it available for [Step 2](#step-2-interaction-widget).

### **Step 2: Interaction Widget**

Create a new Interaction Widget. This widget is hosted in the Genesys agent desktop and provides the Agent AI solution features to agents.

1. Sign in to **Genesys Cloud**.
2. Click **Admin** > **Integrations**.  
<img src="../images/genesys-admin-integ-path-5.png" alt="genesys-admin-integ-path" title="genesys-admin-integ-path" style="border: 1px solid gray; zoom:80%;">
3. If you have not created an Interaction Widget for Agent AI, install a new Interaction Widget by clicking the **Integrations** tab on the right side of the page.
<img src="../images/new-interaction-widget-6.png" alt="new-interaction-widget" title="new-interaction-widget" style="border: 1px solid gray; zoom:80%;"> 
4. Name the Interaction Widget with a meaningful name, such as **KoreaiAA Interaction Widget**.
5. Open the Interaction Widget by clicking the name.
<img src="../images/open-interaction-widget-7.png" alt="open-interaction-widget" title="open-interaction-widget" style="border: 1px solid gray; zoom:80%;"> 
6. Go to the **Configuration** tab of the Interaction Widget.
<img src="../images/interaction-widget-configuration-tab-8.png" alt="interaction-widget-configuration-tab" title="interaction-widget-configuration-tab" style="border: 1px solid gray; zoom:80%;"> 
7. In the **Application URL** field, enter the following structure; use the **OAuth ID** from [Step 1](#step-1-oauth-credential).

[https://agentassist.kore.ai/koreaiaa-genesys/?conversationid={{gcConversationId}}&lang={{gcLangTag}}&environment={{gcHostOrigin}}&genesysid=](https://agentassist.kore.ai/koreaiaa-genesys/?conversationid=%7B%7BgcConversationId%7D%7D&lang=%7B%7BgcLangTag%7D%7D&environment=%7B%7BgcHostOrigin%7D%7D&genesysid=)&lt;genesys-oauth-Id>

Or

[https://platform.kore.ai/koreaiaa-genesys/](https://platform.kore.ai/koreaiaa-genesys/)
8. Allow all permissions in **iFrame Sandbox Options** and **iFrame Feature/Permission Policy**.

**iFrame Sandbox Options**:
allow-forms,allow-modals,allow-popups,allow-presentation,allow-same-origin,allow-scripts,allow-downloads.

**iFrame Feature/Permission Policy**: camera,microphone,geolocation,clipboard-write,display-capture,fullscreen.

**Communication Type Filtering**: chat, call, callback, email, sms, line, facebook, instagram, twitter, open, webmessaging, whatsapp.

### **Step 3: Agent Access**

To view the Interaction Widget, agents must have the following accesses:

**Group Membership**

An Interaction Widget uses Group Membership to determine who can view it on the agent desktop.

1. Use an existing Group, if your agents are already part of it. Otherwise, create a new Group for Agent AI permission.
2. Name the Group as **KoreAA-Agents** or similar to distinguish it.
3. Add any agent to allow them to use the Agent AI functionality. You can utilize more than one Group, if required.
4. Go back to the **Integrations** section and open the **Interaction Widget** created in [Step 2](https://docs.kore.ai/agentassist/uncategorized/agentassist-integration-in-genesys-manual-steps/#Step_2_Interaction_Widget). 
5. On the **Configuration** tab, add access using the Group you identified or created for Agent AI in the **Group Filtering** option.

You may also utilize **Queue Filtering** (optional).  
<img src="../images/configuration-group-filtering-9.png" alt="configuration-group-filtering-9" title="configuration-group-filtering-9" style="border: 1px solid gray; zoom:80%;">

**Custom Role/Permission**

By default, most agents don’t have access to read from a Data Table. You must grant them explicit permission to read from the Data Table for loading the Interaction Widget.

1. Sign in to **Genesys Cloud**.
2. Go to **Admin** > **People & Permissions** > **Roles / Permissions**.
3. Click **Add Role** to create a new Role.
4. Give a distinctive name to the Role; for example, **KoreaiAA Agent**.
5. On the **Permission** tab, search for the following and add (select the box):

**Architect** > **DataTable** > **View**

**Conversation** > **Transcription** > **View**

**Note**: The Conversation permission is available only in CX3 license.

6. Once finished, the **Assigned Permissions** view should look like this:
<img src="../images/assigned-permissions-10.png" alt="assigned-permissions" title="assigned-permissions" style="border: 1px solid gray; zoom:80%;">
7. Once the role is created, click the three dots at the right end of the **Permission role** and select **Change Membership**.
<img src="../images/change-membership-11.png" alt="change-membership" title="change-membership" style="border: 1px solid gray; zoom:80%;">
8. Add appropriate agents to the role.

### **Step 4: Data Table Configuration**

This step includes creation of a Data Table with Agent AI bot details.

**Note**: The configuration data is stored directly in the Custom Fields of the Data Table, not in a Data Table row. A single Data Table represents a configuration of Agent AI. In other words, the default values of the Custom Fields contain the necessary configuration data to load the Agent AI widget.

1. Sign in to **Genesys Cloud**.
2. Go to **Admin** > **Architect** > **Data Tables**.  
<img src="../images/genesys-architect-data-tables-12.png" alt="genesys-architect-data-tables" title="genesys-architect-data-tables" style="border: 1px solid gray; zoom:80%;">
3. Create a new Data Table by clicking the plus icon, and provide a relevant name such as **KoreaiAA-configuration**.
<img src="../images/new-data-table-13.png" alt="new-data-table" title="new-data-table" style="border: 1px solid gray; zoom:80%;">
4. Click the “three dots,” and select **Edit Table Fields** from the list.
<img src="../images/edit-table-fields-14.png" alt="edit-table-fields" title="edit-table-fields" style="border: 1px solid gray; zoom:80%;">
**Note**: Reference Key label must be set to “agentAssist”. This is the value used by the Interaction Widget to load the configuration data.
5. Click **Add Field** to create five custom fields to provide the Agent AI configuration.
<img src="../images/add-field-15.png" alt="add-field-15" title="add-field-15" style="border: 1px solid gray; zoom:80%;">
6. Click the **Add Field** button under **Custom Fields**.
Set the data type for all custom fields as **String** while adding.  
<img src="../images/custom-field-string-16.png" alt="custom-field-string" title="custom-field-string" style="border: 1px solid gray; zoom:80%;">
7. Add the custom fields with Bot details.  
<img src="../images/custom-field-bot-details-17.png" alt="custom-field-bot-details" title="custom-field-bot-details" style="border: 1px solid gray; zoom:80%;">
8. Follow the below conventions for other custom fields. Use the exact names, including upper/lower case.

These values are found in the **Flow & Channels** > **Channels** > **Digital** > **Configured Channels** > **JWT App Details** section of the **[XO](https://platform.kore.ai/)** application.

<table>
  <tr>
   <td>
<strong>Field Label</strong> 
   </td>
   <td>                    <strong>Default Value</strong>
   </td>
  </tr>
  <tr>
   <td>AgentAssist URL
   </td>
   <td><a href="https://agentassist.kore.ai/">https://agentassist.kore.ai</a>
   </td>
  </tr>
  <tr>
   <td>Bot Id
   </td>
   <td>st-8cb94691-xxxx-xxxx-xxxx-xxxxxxxx
   </td>
  </tr>
  <tr>
   <td>Client Id
   </td>
   <td>cs-b60f544d-xxxx-xxxx-xxxx-xxxxxxxxxxxx
   </td>
  </tr>
  <tr>
   <td>Client Secret
   </td>
   <td>&lt;secret-key from Agent AI>
   </td>
  </tr>
  <tr>
   <td>is Audiohook Enabled
   </td>
   <td>true / false
   </td>
  </tr>
</table>

**Note**:

* All the custom fields should be of the string type.
* If the “is Audiohook Enabled” option is false, the application tries to utilize the Genesys native transcriptions using the Transcriptions API.

To change the values, you must click the gray box surrounding each Custom Field, not directly on the textbox.

### **Step 5 (Optional): Audiohook Integration**

The final step is to install Audiohook for voice streaming, if using Kore-managed Transcriptions.

1. Sign in to **Genesys Cloud**.
2. Go to **Admin** > **Integrations** > **Integrations**.  
<img src="../images/genesys-admin-integrations-18.png" alt="genesys-admin-integrations" title="genesys-admin-integrations" style="border: 1px solid gray; zoom:80%;">
The Audiohook integration requires specific configuration values to support Agent AI configuration.

3. Install a new audiohook app by clicking the **Integrations** button on the top-right corner.  
<img src="../images/add-new-audiohook-19.png" alt="add-new-audiohook" title="add-new-audiohook" style="border: 1px solid gray; zoom:80%;">  

    <img src="../images/locate-audiohook-20.png" alt="locate-audiohook" title="locate-audiohook" style="border: 1px solid gray; zoom:80%;">

4. Open the audiohook, and go to the **Configuration** tab.  
<img src="../images/audiohook-configuration-tab-21.png" alt="audiohook-configuration-tab" title="audiohook-configuration-tab" style="border: 1px solid gray; zoom:80%;">
    
    1. Channel value should be both.

    2. The **Connection URI** format should be similar to the following:
wss://[savg-webserver.kore.ai/audiosocket/genesys/?sipuri=xxx&token=xxx&botId=xxx&accountId=xxx&agentassist=true](http://savg-webserver.kore.ai/audiosocket/genesys/?sipuri=xxx&token=xxx&botId=xxx&accountId=xxx&agentassist=true)

    3. Get **sipuri=sip:&lt;sip-string>** from **UXO**, **Flow & Channels** > **Channels** > **Kore.ai Voice Gateway** > **SIP Numbers** > **Configure SIP Transfer** > **Transfer from IVR** page.  
    <img src="../images/Transfer-from-IVR-page-22.png" alt="Transfer-from-IVR-page" title="Transfer-from-IVR-page" style="border: 1px solid gray; zoom:80%;">

    4. Use the following reference from **Flow & Channels** > **Channels** > **Digital** > **Configured Channels** > **JWT App Details** section of the **[XO](https://platform.kore.ai/)** application to fetch **Bot ID**, **Account ID**, **Client ID**, and **Client Secret** (for token generation).  
    <img src="../images/web-mobile-client-23.png" alt="web-mobile-client" title="web-mobile-client" style="border: 1px solid gray; zoom:80%;">

    5. Follow the steps of [Using XO Platform APIs – Kore.ai Documentation](https://developer.kore.ai/docs/bots/api-guide/apis/#Generating_the_JWT_Token) to generate the token (token= &lt;token>.)

5. Add credentials in the **Credentials** tab.  
<img src="../images/integration-configuration-credentials-tab-24.png" alt="integration-configuration-credentials-tab" title="integration-configuration-credentials-tab" style="border: 1px solid gray; zoom:80%;">
    
    1. Refer to [Step-4](https://docs.kore.ai/agentassist/integration/agentassist-integration-in-genesys-manual-steps/#Step_4_Data_Table_Configuration) and use **Bot Client ID** and **Client Secret** as API Key and Client Secret respectively.

    2. These credentials are used to validate the audiostream signature by Kore.

6. Click **Save**.

### **Step 6: XO 11 Configuration Notes**

For the configured App, ensure at least one Dialog Task has been configured for Agent AI use.
<img src="../images/dialog-settings-page-25.png" alt="dialog-settings-page" title="dialog-settings-page" style="border: 1px solid gray; zoom:80%;">

**Where to find configuration settings**

You can find the necessary information in **Flows & Channels** > **Digital** > **Web/Mobile Client**.
<img src="../images/jwt-app-details-26.png" alt="jwt-app-details" title="jwt-app-details" style="border: 1px solid gray; zoom:80%;">
