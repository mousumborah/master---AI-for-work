# Multi-bot Agent AI Integration with Genesys

Multi-bot Integration of Agent AI in Genesys is a significant enhancement to our solution. Previously limited to a single bot and a department-specific approach, the solution has now been upgraded to support multiple bots and a queue-based functionality. This enhancement enables Genesys Cloud CX to offer a more flexible and scalable solution for businesses seeking to leverage AI to improve agent efficiency and customer satisfaction across multiple departments.

This document provides detailed, step-by-step instructions for setting up the multi-bot integration of the AgentAssist widget in the Genesys environment.

* [Step 1: Create and configure a Data Table on the XO Platform](#step-1-create-and-configure-a-data-table-on-the-xo-platform)

* [Step 2: Get Genesys Oauth ID](#step-2-get-genesys-oauth-id)

* [Step 3: Create an Interaction Widget in Genesys for AgentAssist](#step-3-create-an-interaction-widget-in-genesys-for-agentassist)

* [Step 4: Provide Interaction Widget access to agents](#step-4-provide-interaction-widget-access-to-agents)

* [Step 5: (Optional) Install Audiohook for voice streaming](#step-5-optional-install-audiohook-for-voice-streaming)

* [Step 6: Create an architect flow in Genesy for the queue](#step-6-create-an-architect-flow-in-genesys-for-the-queue)

## **Prerequisites**

1. Genesys Cloud account with Admin rights.
2. [Kore.ai](https://agentassist.kore.ai/) Agent AI instance.
3. Familiarity with creating a Group in Genesys.

## **Step 1: Create and configure a Data Table on the XO Platform**

Kore.ai matches the third-party queue name with the "QueueIdentifier" credential name in its bot credentials to render the appropriate bot.

Kore.ai uses Data Tables to store bot credentials, including:

* **BotId**: A unique identifier assigned to a bot.
* **ClientId**: An identifier provided to a client application.
* **ClientSecret**: A secret key or password associated with the ClientId.
* **AgentAssistWidgetURL**: URL that points to the AgentAssist widget.
* **AudiohookEnabled**: A setting or flag indicating whether audio processing is enabled for the bot.
* **QueueIdentifier**: Third-party identifier (company/department) name. It’s a unique identifier to fetch bot details at run time.

Bot credentials are fetched based on Genesys desktop queue names. If the Genesys queue name is of the “&lt;QUEUEIDENTIFIER>&lt;QDELIMITER>XXXXX” format, for example “ALPHAINC_CUSTOMERSERVICE_16092024,” then:

* QueueIdentifier = **ALPHAINC** and qDelimiter = “**_**”.
* Update the QueueIdentifier in the Kore datatable.
* Update the qDelimiter in the “[Create an Interaction Widget in Genesys for AgentAssist](#step-3-create-an-interaction-widget-in-genesys-for-agentassist)” section.

### Creating a New Data Table

Create a Data Table to store bot credentials on the XO Platform.

1. Sign in to Kore.ai [botbuilder](http://bots.kore.ai/botbuilder).
2. Click **Data** > **Data Tables**.
3. Click **New Table**.  
<img src="../images/data-table-new-table-1.png" alt="new-table" title="new-table" style="border: 1px solid gray; zoom:80%;">

4. Enter the following details in the **New Table** page:

    4.1. **Name** of the Data Table.

    4.2. **Description** of the Data Table.

    4.3. **Columns** to be included in the data table. Click the “tick” mark to add multiple columns.  
    <img src="../images/adding-columns-2.png" alt="adding-columns" title="adding-columns" style="border: 1px solid gray; zoom:80%;">

    Add the following **case-sensitive** columns:

      4.3.1. AudiohookEnabled

      4.3.2. AgentAssistWidgetURL
        
      4.3.3. ClientSecret
        
      4.3.4. ClientId
        
      4.3.5. BotId
        
      4.3.6. QueueIdentifier: Enter your company/department name.
    
    4.4. **Indexes** for the table.
    
    4.5. **Bot Assignments** to let virtual assistants access data in this table.
    
    4.6. **App Assignments** to let apps access data in this table.
    
     4.6.1. Select any app from the displayed list, or click **Create New App** and enter your app name:  
     <img src="../images/create-new-app-3.png" alt="create-new-app" title="create-new-app" style="border: 1px solid gray; zoom:80%;">

     4.6.2. Select the **Read**, **Write**, and **Delete** permissions, as required.  

    !!! note
        
        You can also create new apps by clicking **Data** > **Apps** > **New App** in the home page:  
     <img src="../images/new-app-4.png" alt="new-app" title="new-app" style="border: 1px solid gray; zoom:80%;">

    4.7. **Process Assignments** to let a process app access data in this table.
5. Click **Create** to create the new data table.  
<img src="../images/creating-new-data-table-5.png" alt="creating-new-data-table" title="creating-new-data-table" style="border: 1px solid gray; zoom:80%;">

### Insert data into Data Table

Set up necessary permissions and app assignments and insert bot-specific data into the Data Table.

1. Sign in to Kore.ai [botbuilder](http://bots.kore.ai/botbuilder).
2. Click **Data** > **Apps**.
3. Select the **App** with write access to the Data Table where you want to add information.  
<img src="../images/copying-client-id-and-secret-6.png" alt="copying-client-id-and-secret" title="copying-client-id-and-secret" style="border: 1px solid gray; zoom:80%;">

4. Copy **Client ID** and **Client Secret** of the App.
5. Create a JWT Token using the **Client ID** and **Client Secret** by following this [doc](https://developer.kore.ai/docs/bots/api-guide/apis/#Generating_the_JWT_Token).
6. Insert data into the Data Table by following this [doc](https://developer.kore.ai/docs/bots/api-guide/data-insert-api/). Use the JWT Token created in the previous step.

    **API Body Payload Structure:**

    ```
    {
        "data": {
            "QueueIdentifier": <Unique QueueIdentifier>,
            "BotId": <Kore BotId>,
            "ClientId": <Kore ClientId>,
            "ClientSecret": <Kore ClientSecret>,
            "AudiohookEnabled": "true" / "false",
            "AgentAssistWidgetURL": <Kore AgentAssist Widget URL>
        }
    }
    ```  
    <img src="../images/api-body-payload-structure-7.png" alt="api-body-payload-structure" title="api-body-payload-structure" style="border: 1px solid gray; zoom:80%;">

## **Step 2: Get Genesys Oauth ID**

An OAuth credential with proper permissions is required for the connection between the Kore.ai Agent AI interaction widget and the Kore.ai platform. 

A Genesys OAuth ID is required to complete the URL formation for the Genesys interaction widget.

**Steps to get Genesys OAuth ID**:

1. Sign in to **Genesys Cloud**.
2. Go to **Admin** > **Integrations** > **OAuth**.  
<img src="../images/genesys-integration-oauth-8.png" alt="genesys-integration-oauth" title="genesys-integration-oauth" style="border: 1px solid gray; zoom:80%;">

3. Click **Add Client**.  
<img src="../images/oauth-add-client-9.png" alt="oauth-add-client" title="oauth-add-client" style="border: 1px solid gray; zoom:80%;">

4. Enter the **app name**, **description**, and **token duration** in the **App Name**, **Description**, and **Token Duration** fields.
5. Select **Token Implicit Grant (Browser)** in the **Grant Types** section.  
<img src="../images/client-details-section-10.png" alt="client-details-section" title="client-details-section" style="border: 1px solid gray; zoom:80%;">

6. Add [https://agentassist.kore.ai/koreaiaa-genesys/](https://agentassist.kore.ai/koreaiaa-genesys/) in the _Authorized redirect URIs (one per line)_ section. Replace “agentassist.kore.ai” with the domain where your AgentAssist is hosted.
7. Add the following list of scopes in the **Scope** section:

    * conversations
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

    <img src="../images/redirect-uri-and-scope-11.png" alt="redirect-uri-and-scope" title="redirect-uri-and-scope" style="border: 1px solid gray; zoom:80%;">

After saving the configuration, you will get the **Client Id** of the created OAuth client. Copy the ID and have it available for [Step 3](#step-3-create-an-interaction-widget-in-genesys-for-agentassist).

## **Step 3: Create an Interaction Widget in Genesys for AgentAssist**

Create a new Interaction Widget. This widget is hosted in the Genesys agent desktop and provides the AgentAssist solution features to agents.

**Steps to create an Interaction Widget**

1. Sign in to **Genesys Cloud**.
2. Click **Admin** > **Integrations**.  
<img src="../images/genesys-admin-integrations-12.png" alt="genesys-admin-integrations" title="genesys-admin-integrations" style="border: 1px solid gray; zoom:80%;">

3. If you have not created an Interaction Widget for AgentAssist, install a new Interaction Widget by clicking the **Integrations** tab on the right side of the page.  
<img src="../images/install-an-interaction-widget-13.png" alt="install-an-interaction-widget" title="install-an-interaction-widget" style="border: 1px solid gray; zoom:80%;">   
<img src="../images/new-interaction-widget-14.png" alt="new-interaction-widget" title="new-interaction-widget" style="border: 1px solid gray; zoom:80%;">
 
4. Name the **Interaction Widget** with a meaningful name, such as KoreaiAA Interaction Widget.

5. Open the **Interaction Widget** by clicking the name.  
<img src="../images/open-interaction-widget-15.png" alt="open-interaction-widget" title="open-interaction-widget" style="border: 1px solid gray; zoom:80%;">

6. Go to the **Configuration** tab of the Interaction Widget.  
<img src="../images/interaction-widget-configuration-tab-16.png" alt="interaction-widget-configuration-tab" title="interaction-widget-configuration-tab" style="border: 1px solid gray; zoom:80%;">

7. In the **Application URL** field, enter the following structure:  
<code>https://agentassist.kore.ai/koreaiaa-genesys/?conversationid={{gcConversationId}}&lang={{gcLangTag}}&environment={{gcHostOrigin}}&genesysid=<strong>&lt;genesys-oauth-Id>&multibot=true&x_metadata=&lt;?x=%7B%22datatable%22%xxxxx></strong></code>.  
Replace “agentassist.kore.ai” with the domain where your AgentAssist is hosted. The “<code>x_metadata</code>” value equals the url<code>-encoded string</code> of JSON object.  

    7.1. For the **oauthId** value, use the **OAuth ID** from [Step 2](#step-2-get-genesys-oauth-id).

    7.2. For the <strong>x_metadata</strong> value:

    7.2.1. Sign in to [Kore botbuilder](https://bots.kore.ai/botbuilder/login).
    
    7.2.2. Click <strong>Data</strong> > <strong>Data Tables,</strong> and copy the <strong>Data Table</strong> name:  
        <img src="../images/copying-data-table-name-17.png" alt="copying-data-table-name" title="copying-data-table-name" style="border: 1px solid gray; zoom:80%;">

    7.2.3. Click <strong>Apps,</strong> and click one of the app names that has “read” access:  
        <img src="../images/click-an-app-name-18.png" alt="click-an-app-name" title="click-an-app-name" style="border: 1px solid gray; zoom:80%;">

    7.2.4. Copy the <strong>Client ID</strong> and <strong>Client Secret</strong> values.  
        <img src="../images/copying-client-id-and-secret-values-19.png" alt="copying-client-id-and-secret-values" title="copying-client-id-and-secret-values" style="border: 1px solid gray; zoom:80%;">
    
    7.2.5. Create a JWT Token using the <strong>Client ID</strong> and <strong>Client Secret</strong> by following this [doc](https://developer.kore.ai/docs/bots/api-guide/apis/#Generating_the_JWT_Token).

    7.2.6. Generate a JSON object with the specified structure and then convert it into a url-encoded string:

            {

            “datatable”:{

            “name”: <paste the datatable name>

            “token”: <paste token created in the previous step>

            “qDelimiter”: <Paste the special character used in the queue name to distinguish the QueueIdentifier from the remaining part of the queue name>

            }

            }

    Reference:  
    <img src="../images/java-script-mode-20.png" alt="java-script-mode" title="java-script-mode" style="border: 1px solid gray; zoom:80%;">

    7.2.7. Copy the url-encoded string and paste it against the **x_metadata** value.

8. Allow all permissions in **iFrame Sandbox Options** **and iFrame Feature/Permission Policy**.  

**iFrame Sandbox Options**: allow-forms,allow-modals,allow-popups,allow-presentation,allow-same-origin,allow-scripts,allow-downloads.  

**iFrame Feature/Permission Policy**: camera,microphone,geolocation,clipboard-write,display-capture,fullscreen.  

**Communication Type Filtering**: chat and call.

## **Step 4: Provide Interaction Widget access to agents**

To view the Interaction Widget, agents must have the following accesses:

### Group Membership

An Interaction Widget uses Group Membership to determine who can view it on the agent desktop.

1. Use an existing Group, if your agents are already part of it. Otherwise, create a new Group for AgentAssist permission.
2. Name the Group as **KoreAA-Agents** or similar to distinguish it.
3. Add any agent to allow them to use the AgentAssist functionality. You can utilize more than one Group, if required.
4. Go back to the **Integrations** section and open the **Interaction Widget** created in [Step 2](https://docs.kore.ai/agentassist/uncategorized/agentassist-integration-in-genesys-manual-steps/#Step_2_Interaction_Widget). 
5. On the **Configuration** tab, add access using the Group you identified or created for AgentAssist in the Group Filtering option.  

You may also utilize Queue Filtering (optional).  
<img src="../images/group-filtering-21.png" alt="group-filtering" title="group-filtering" style="border: 1px solid gray; zoom:80%;">

### Custom Role/Permission

In addition to the basic agent role, add a new role as given below:

1. Sign in to **Genesys Cloud**.
2. Go to **Admin** > **People & Permissions** > **Roles / Permissions**.
3. Click **Add Role** to create a new role.
4. Give a distinctive name to the role; for example, KoreaiAA Agent.
5. On the **Permission** tab, search for **Conversation** > **Transcription** > **View**, and add (select the box):  

    !!! note

        The Conversation permission is available only in the CX3 license.

6. Once finished, the **Assigned Permissions** view should look like this:  
<img src="../images/assigned-permissions-22.png" alt="assigned-permissions" title="assigned-permissions" style="border: 1px solid gray; zoom:80%;">

7. Once the role is created, click the **three dots** at the right end of the **Permission role,** and select **Change Membership**. Add the appropriate agents to the role.

## **Step 5: (Optional) Install Audiohook for Voice Streaming**

The final step is to install Audiohook for voice streaming, if using Kore-managed Transcriptions.

1. Sign in to **Genesys Cloud**.
2. Go to **Admin** > **Integrations** > **Integrations**.
3. Enter “audiohook” in the search bar.  
<img src="../images/search-audiohook-23.png" alt="search-audiohook" title="search-audiohook" style="border: 1px solid gray; zoom:80%;">  
Audiohook integration requires specific configuration values to support AgentAssist configuration.

4. Install a new audiohook app by clicking the **Integrations** button on the top-right corner.  
<img src="../images/install-new-audiohook-24.png" alt="install-new-audiohook" title="install-new-audiohook" style="border: 1px solid gray; zoom:80%;">  
<img src="../images/new-audiohook-25.png" alt="new-audiohook" title="new-audiohook" style="border: 1px solid gray; zoom:80%;">

5. Open the **Audiohook,** and go to the **Configuration** tab.  
<img src="../images/audiohook-configuration-26.png" alt="audiohook-configuration" title="audiohook-configuration" style="border: 1px solid gray; zoom:80%;">

    5.1. **Channel** value should be both.

    5.2. The **Connection URI** format should be similar to  
    wss://[savg-webserver.kore.ai/audiosocket/genesys/?sipuri=xxx&token=xxx&botId=xxx&accountId=xxx&agentassist=true](http://savg-webserver.kore.ai/audiosocket/genesys/?sipuri=xxx&token=xxx&botId=xxx&accountId=xxx&agentassist=true), but add “multiBot=true” parameter to it. 

    !!! note

        This configuration can be done for a single bot present in Kore.ai Data Table.

6. Get **sipuri=sip:&lt;sip-string>** from **AgentAssist** > **Voice** channel.  
<img src="../images/sip-identifier-27.png" alt="sip-identifier" title="sip-identifier" style="border: 1px solid gray; zoom:80%;">

7. Use the following reference from **AgentAssist.kore.ai**, **Bot Channel** configuration page to fetch **Bot ID**, **Account ID**, **Client ID**, and **Client Secret** (for token generation).  
<img src="../images/for-token-generation-28.png" alt="for-token-generation" title="for-token-generation" style="border: 1px solid gray; zoom:80%;">

    7.1. Follow the steps of [Using XO Platform APIs – Kore.ai Documentation](https://developer.kore.ai/docs/bots/api-guide/apis/#Generating_the_JWT_Token) to generate the token (token= &lt;token>.)

8. Add credentials in the **Credentials** tab. Use the **ClientID** and **ClientSecret** of the bot you have used while configuring the Audiohook. These credentials are used to validate the audiostream signature by Kore.  
<img src="../images/credential-tab-29.png" alt="credential-tab" title="credential-tab" style="border: 1px solid gray; zoom:80%;">

9. Click **Save**.

## **Step 6: Create an Architect Flow in Genesys for the Queue**

When a call comes to a Genesys number, it passes through an architect flow. If you do not have an ACD architect flow for the queue, create one by following this section.

#### Steps to create an architect flow

1. Sign in to **Genesys Cloud**.
2. Go to **Admin** > **Architect** > **Architect**.  
<img src="../images/genesys-architect-30.png" alt="genesys-architect" title="genesys-architect" style="border: 1px solid gray; zoom:80%;">  
<img src="../images/genesys-architect-31.png" alt="genesys-architect" title="genesys-architect" style="border: 1px solid gray; zoom:80%;">

3. Click the **+Add** button to create an **Inbound Call** **Flow**.  
<img src="../images/inbound-call-flow-32.png" alt="inbound-call-flow" title="inbound-call-flow" style="border: 1px solid gray; zoom:80%;">

4. Click **Create Flow**. The final architect flow looks like the following screenshot:  
<img src="../images/create-flow-33.png" alt="create-flow" title="create-flow" style="border: 1px solid gray; zoom:80%;">

    !!! notes

        * Inside the **Transfer to ACD** node, select the **queue name** where you want to transfer the call.
        * The **Transcription node** is optional, if you have already enabled Voice Transcription and Audio Monitoring in the queue level voice configuration.
        * Architect flow is required as a mandatory step, as it directs the incoming call to the Genesys agent desktop.