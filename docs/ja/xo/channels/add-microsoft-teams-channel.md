# Adding the Microsoft Teams Channel

You can add Microsoft Teams as a delivery channel to your Kore.ai Virtual Assistant to allow it to interact with end-users using Microsoft Teams.


## Prerequisites


* Ensure you have an account with the [Microsoft Bot Framework](https://dev.botframework.com/).
* Create a Bot Channel Service and register it in Azure.
* Enable a webhook for the platform to receive messages.
* Purchase an active subscription to Azure services with Admin access; required to subscribe to a new Azure service.


## Step 1: Create an Azure Bot

Create an Azure Bot and configure it on the Kore.ai XO Platform to establish a communication channel between Microsoft Teams and the platform.


1. Log in to the [Azure portal](https://portal.azure.com/), and click **+ Create a resource** from the portal menu.
2. Search and select **Azure Bot** on the page, and click **Create**.
<img src="../images/MS_Team1.png" alt="Azure bot" title="Azure bot" style="border: 1px solid gray; zoom:70%;">

3. Fill in the required details, select the **Multi Tenant** option in the **Type of App field** then click **Review + Create**.
<img src="../images/MS_Team2.png" alt="review create" title="review create" style="border: 1px solid gray; zoom:70%;">
4. On the next page, review the details and check for the **Validation** status. Click **Create** to proceed.
<img src="../images/MS_Team3.png" alt="app validation" title="app validation" style="border: 1px solid gray; zoom:70%;">

5. Associate the Azure Bot with a **Microsoft App ID** and **Password**. You can choose the default option: **Auto create App Id and password**. You can also choose to **Create a new Microsoft App ID** or **Use existing app registration**. For more information, see [Microsoft Bot Framework documentation](https://docs.microsoft.com/en-gb/azure/bot-service/bot-service-resources-bot-framework-faq?view=azure-bot-service-4.0#app-registration).  <img src="../images/MS_Team4.png" alt="create app ID" title="create app ID" style="border: 1px solid gray; zoom:70%;">

6. Once the deployment is completed, click **Go to resource** to view details of your resource.
<img src="../images/MS_Team5.png" alt="view resource" title="view resource" style="border: 1px solid gray; zoom:70%;">


!!! note

    The platform supports both Single-Tenant and Multi-Tenant apps.

## Step 2: Configure the Resource App Id and Password

Generate a new App Password and Client Secret to configure the Azure Bot on the Kore.ai XO Platform.


1. On the **Configurations** tab, click the **Manage**  option next to the **Microsoft App ID** field.
<img src="../images/MS_Team6.png" alt="Microsoft App ID" title="Microsoft App ID" style="border: 1px solid gray; zoom:70%;">

2. Choose **Certificates & secrets** in the left navigation bar, and create a new client secret on the page:
    * Click the **+ New client secret** option.
    * Provide the necessary details, and then click the **Add** option.
3. Copy the **Value** of the new client secret and provide it in the **App Password** field present on the **Configurations** tab of the Kore.ai XO Platform. [Refer Step 3: Enable Microsoft Teams Channel.](#step-3-enable-microsoft-teams-channel) 
<img src="../images/MS_Team7.png" alt="enable channel" title="enable channel" style="border: 1px solid gray; zoom:70%;">

4. Close the **Certificates and secrets** section to return the **Configuration** section of the resource using the breadcrumbs.

!!! note

    Make a note of the Microsoft App Id in the Azure Bot configurations page and provide it in the Configuration tab of this window.

## Step 3: Enable Microsoft Teams Channel

Configure the MS Teams credentials on the Kore.ai XO Platform to establish communication between both.


1. On the platform, select the assistant, and then go to the **Channels & Flows** > **Channels** > **Digital** > **All** menu.
2. Select the **Microsoft Teams** channel, click the **Configuration** tab, and then enter the following details: **Multi-Tenant Apps Configuration**
    * **Microsoft App ID** – The app ID of your Azure Bot resource.
    * **App Password** – The App password value that you find in the Certificates & Secrets page of the Azure bot.
    * **Enable Proactive Notifications (optional)** – Toggle to enable the Proactive Notification.
    * **Enable Modal Dialogs (optional)** - Toggle to enable the Modal Dialogs. [Learn more](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/how-to/action-commands/create-task-module?tabs=dotnet).
        * Enter the Custom URL to which the platform forwards Modal Dialog messages for processing.

            !!! note

                The platform maintains the conversation context when handling Modal Dialog messages. It forwards these messages with pre-context to the Custom URL for processing, then relays responses back to the user, maintaining a seamless interaction.

    * **Application (Client) ID** – The app ID of your Azure Bot resource.
    * **Client Secret** – The client secret value that you find on the Certificates & Secrets page of the Azure bot.
    * **Delivery (tenant) ID** – The subscription ID that you can find on the Overview page of the Azure bot.
    * Select **Yes** for the **Enable Channel** option.
    <img src="../images/MS_Team8.png" alt="Multi tenant app" title="Multi tenant app" style="border: 1px solid gray; zoom:70%;">


**Single-Tenant App Configuration**


1. Select the **Single-Tenant** option and enter the **App Tenant ID** value.
<img src="../images/MS_Team9.png" alt="Single tenant app" title="Single tenant app" style="border: 1px solid gray; zoom:70%;">


2. Click **Save**.
3. Copy the **Webhook URL** from the tab and paste it in the **Messaging endpoint** field on the **Configurations** module in Azure bot.
4. Click **Apply** to save the entered value.
5. Once the **Configuration** is completed, select the **Channels** option from the left menu and then select the **Microsoft Teams** channel.
<img src="../images/MS_Team10.png" alt="configure tenant" title="configure tenant" style="border: 1px solid gray; zoom:70%;">

6. Select the **I Agree** checkbox on the **Terms of Service** dialog and then click **Agree**.
<img src="../images/MS_Team11.png" alt="Agree Terms" title="Agree Terms" style="border: 1px solid gray; zoom:70%;">

7. Select the **Microsoft Teams Commercial (most common)** option to enable the Teams as per your commercial business requirements. If you want to enable the Azure bot for Government Community Cloud (GCC) organizations, select the **Microsoft Teams Government** option. Click the [Learn more ](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/deploy-and-publish/apps-publish-overview)link next to the option on the screen for more information.
<img src="../images/MS_Team12.png" alt="GCC organizations" title="GCC organizations" style="border: 1px solid gray; zoom:70%;">

8. Click **Apply** to complete the channel setup.

!!! note

    The Web Chat option of Bot Framework is not supported.

## Step 4: Publish Your Bot in Teams

You can now publish the Azure bot on your MS Teams account so that your users can discover and converse with the bot.

To do so, create an MS Teams app, associate the bot with it, and then publish the app.


1. [Log in](https://teams.microsoft.com/) to the MS Teams account with admin credentials.

2. Click **Ellipsis […]** in the left navigation bar and then select the **Developer Portal** icon to launch the Apps builder.  
<img src="../images/MS_Team13.png" alt="developer portal" title="developer portal" style="border: 1px solid gray; zoom:70%;">

3. On the **Developer Portal** page, select the **Apps** tab and then click the **New App** button.
<img src="../images/MS_Team14.png" alt="new app" title="new app" style="border: 1px solid gray; zoom:70%;">

4. On the **New App** dialog, enter a name for the app, copy and paste the App ID of your Azure Bot in the **App ID** field, and then click **Publish**.
<img src="../images/MS_Team15.png" alt="app ID" title="app ID" style="border: 1px solid gray; zoom:70%;">

5. On the **Publish** dialog, select the **Publish to your org** option.
<img src="../images/MS_Team16.png" alt="publish app" title="publish app" style="border: 1px solid gray; zoom:70%;">

6. Grant the desired permissions to your MS Teams app.
<img src="../images/MS_Team17.png" alt="grant permissions" title="grant permissions" style="border: 1px solid gray; zoom:70%;">

7. Click **Publish your App** and complete the publishing process.
<img src="../images/MS_Team18.png" alt="complete process" title="complete process" style="border: 1px solid gray; zoom:70%;">

!!! note

    The Developer Portal view is only available on the **Microsoft Teams Desktop** client.

## Step 5: Approve the MS Teams App Publish Request

The request to publish the MS Teams App must be approved by an MS Teams Admin. Log in to the [MS Teams Admin Portal](https://admin.teams.microsoft.com/) and proceed to **Teams apps > Manage apps**. Search for the app that you published in the earlier step. Select the app and change the Publishing status to **Published**. This completes the process for publishing your bot for your Teams users.


## Step 6: Configure Proactive Notifications [Optional]

If you want to send Proactive Notifications to your users, you need to perform a few more actions.

!!! note

    You can skip the following sections and proceed to the Configurations tab if you do not intend to send Proactive Notifications.

To enable Proactive Notifications, follow these steps:

1. Capture the **App ID** associated with the MS Teams App that is approved in Step 3. You can find this information on the details page of the app.
2. Provide this **App Id** in the channel **Configurations** tab.
<img src="../images/MS_Team19.png" alt="associate app" title="associate app" style="border: 1px solid gray; zoom:70%;">
3. The bot requires additional app credentials for sending the Proactive Notifications. Go to the [Azure](https://portal.azure.com/) portal, and click the **More Services** link.
<img src="../images/MS_Team20.png" alt="more services " title="more services" style="border: 1px solid gray; zoom:70%;">

4. On the More Services page, search and select the **App registrations**.
<img src="../images/MS_Team21.png" alt="app registrations" title="app registrations" style="border: 1px solid gray; zoom:70%;">


5. On the App registrations page, click **New registration**.
<img src="../images/MS_Team21_dup.png" alt="new registration" title="new registration" style="border: 1px solid gray; zoom:70%;">

6. Provide the required information and click **Register**.
<img src="../images/ms_app_registration.png" alt="register app" title="register app" style="border: 1px solid gray; zoom:70%;">

7. You are redirected to the details page of the newly registered app.
8. From the Manage menu, select the **API permissions** section and then click the **Add a permission** option. From the **Request API permissions**, select **Microsoft Graph** and choose **Application Permissions**.
<img src="../images/MS_Team23.png" alt=" app" title="app permissions" style="border: 1px solid gray; zoom:70%;">

9. From the permissions list, select the following permissions and click **Add permissions**.
    * TeamsAppInstallation.ReadForUser.All
    * TeamsAppInstallation.ReadWriteSelfForUser.All
    * TeamsAppInstallation.ReadWriteForUser.All
    * User.Read.All

    ![add permissions](../images/MS_Team24.png "add permissions")

10. Click on the **Grant admin consent** for > domain name> option to complete the granting of the permissions.
11. Proceed to the **Certificates & secrets** section and select the **New client secret** option.
12. Copy the **Value** of the newly created certificate and provide it on the **Configurations** tab of MS Teams Channel on the Kore.ai XO Platform.
13. Overview section of the app and capture **Application (client) ID**, **Directory (tenant) Id** and provide them on the **Configurations** tab of this page.
14. Navigate to the **Configurations** tab to review and enable the Microsoft Teams channel for your bot.

## MS Teams Chat Features

### Ability to Update or Delete Delivered Bot Messages

Developers now can update or delete bot messages in Microsoft Teams even after they have been delivered to users. This feature provides greater flexibility and control, allowing developers to disable or remove template messages after a user has taken action on them.

New Channel Metadata Object: <code>channelActionMetadata</code>

The platform has introduced a new metadata object called `channelActionMetadata`, which captures the necessary metadata for bot messages on the MS Teams channel. This metadata is essential for performing update or deletion actions on the messages.

Captured Meta Fields in <code>channelActionMetadata</code>:

* MsTeams ActivityID
* MsTeams ConversationID
* KoreMessageID

!!! note

    The above fields are captured exclusively for bot messages. These values are refreshed with each new bot message, and it is the developer’s responsibility to capture and manage the metadata for any bot messages that need to be updated or deleted.

Why Only the Latest Bot Message Metadata is Tracked

To prevent an increase in the size of the context object, only the metadata for the most recent bot message is retained. This approach ensures efficiency, even in sessions with a large number of exchanged messages.

#### Channel Utility Function

We have introduced two new channel utility functions: one for retrieving metadata from the channelActionMetadata object and another for updating or deleting delivered bot messages. Currently, these functions are supported for the MS Teams channel and will be extended to other third-party channels as needed.

**channelUtil.getActionMetadata()**

This function allows you to retrieve the metadata stored in the channelActionMetadata object.

Example Script: Fetching and Saving Metadata for Future Actions
```
let channelActionMetadata = channelUtil.getActionMetadata();

if(channelActionMetadata){

    let actionMetadata = {

        activityId : channelActionMetadata.activityId,

        conversationId : channelActionMetadata.conversationId,

        koreMessageId : channelActionMetadata.koreMessageId

    }

}
```

**channelUtil.executeAction()**

This function enables you to execute actions on bot messages that have been delivered in the MS Teams channel. With this function, developers can update or delete messages that have already been sent to the MS Teams channel.

Example Script: Updating the bot message
```
let channelActionMetadata = channelUtil.getActionMetadata();

if(channelActionMetadata){

    let actionMetadata = {

        activityId : channelActionMetadata.activityId,

        conversationId : channelActionMetadata.conversationId,

        koreMessageId : channelActionMetadata.koreMessageId,

        message : "Showing update message"

    }

    channelUtil.executeAction("update_message", actionMetadata);

}
```

Example Script: Deleting the bot message
```
let channelActionMetadata = channelUtil.getActionMetadata();

if(channelActionMetadata){

    let actionMetadata = {

        activityId : channelActionMetadata.activityId,

        conversationId : channelActionMetadata.conversationId,

        koreMessageId : channelActionMetadata.koreMessageId

    }

    channelUtil.executeAction("delete_message", actionMetadata);

}
```

!!! note

    * When an existing bot message is updated using this function, the platform will automatically update the message in the chat history.
    * By default, the platform will emit message tags for any messages that are updated or deleted using this function.

**Tag Values**


* For updated messages: `<Key>`:`<Value>`
    
    channel_action: update_message

* For deleted messages: `<Key>`:`<Value>`

    channel_action: delete_message



<img src="../images/update-delete5.png" alt="Update or Delete Message" title="Update or Delete Message" style="border: 1px solid gray; zoom:70%;">


<img src="../images/update-delete6.png" alt="Update or Delete Message" title="Update or Delete Message" style="border: 1px solid gray; zoom:70%;">


<img src="../images/update-delete2.png" alt="Update or Delete Message" title="Update or Delete Message" style="border: 1px solid gray; zoom:70%;">


<img src="../images/update-delete1.png" alt="Update or Delete Message" title="Update or Delete Message" style="border: 1px solid gray; zoom:70%;">


<img src="../images/update-delete3.png" alt="Update or Delete Message" title="Update or Delete Message" style="border: 1px solid gray; zoom:70%;">


<img src="../images/update-delete4.png" alt="Update or Delete Message" title="Update or Delete Message" style="border: 1px solid gray; zoom:70%;">






### Related Links

After enabling the channel and verifying all the configurations, you can optionally publish the assistant for the new channel. Learn more about[ Publishing your Virtual Assistant](../deploy/publishing-bot.md).

To learn more about working with Channels within the Kore.ai XO Platform, please see [Channel Enablement.](../channels/adding-channels-to-your-bot.md)
