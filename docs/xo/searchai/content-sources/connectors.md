# Connectors

Using the connectors, you can ingest content into the application from diverse sources, including third-party repositories like ServiceNow, Microsoft SharePoint, Atlassian’s Confluence, IBM Domino, etc., and provide your users with a seamless search experience.

Search AI provides in-built connectors to enable crawling specific third-party content management applications, CRM systems, web database applications,  or cloud-based applications. The application can be configured to connect to multiple systems simultaneously using a connector for each third-party application.


## Understanding Connectors 

Connectors enable the application to establish a connection with the third-party application. After the connection is established and authentication is complete, the data from the third-party application is ingested, indexed, and ready to answer in response to search queries. The access privileges of the content are maintained as per the privileges assigned to the user in the third-party repository. This implies that only the files accessible to the user can appear in the answers. During each synchronization cycle of the connector, Search AI only retrieves newly added or modified data from the application, determined by the timestamp of changes. If data has previously been indexed and remains unchanged, it is not retrieved again. 

Refer to the [Connector Directory](connectors/connector-directory.md) for the complete list of applications supported via connectors. For any specific integration requirements, please [contact us](https://kore.ai/contact-us/). 

## Authorization Support for Connectors

Search AI supports two types of authorization mechanisms. 

1. **Basic**: Basic Authorization involves sending a username and password with each request. These credentials are encoded and sent as a Base64-encoded string in the request header.
To use this type of authorization, provide your **username** and **password**. 

2. **OAuth 2.0**: The OAuth 2.0 framework allows third-party applications to access resources on behalf of a user without sharing the credentials. It involves the exchange of access tokens between the client application and the authorization server. 
To use this type of authorization mechanism, **register Search AI as an Inbound OAuth client in your backend application.**

OAuth 2.0 protocol defines several grant types for different use cases. Each grant type is designed to address specific authorization scenarios. 

Currently, SearchAI supports the following grant types:

1. **Client credentials Grant Type**: In this type, the client application(SearchAI, here) directly accesses the resources from the backend application. The client sends the client ID and client secret and gets an access token to access the resources directly. 
    For this type of authentication, provide the **client ID** and **client secret** generated after registering Search AI as an OAuth client application. 

2. **Authorization Code Grant Type**: In the type, the client application(SearchAI) accesses the resources on behalf of a user. Here’s how it works:
    * The client application (in this case, Search AI) initiates the OAuth flow by redirecting the user to the authorization server's authorization endpoint, where the user is prompted to log in to the authorization server.
    * If the login is successful, the authorization server redirects the user back to the client application's redirect URI, along with an authorization code.
    * Upon receiving the authorization code, the client application makes a POST request to the authorization server's token endpoint.
    * The authorization server verifies the authorization code, client credentials, and a redirect URI and responds with an access token and optionally a refresh token in the body of the response.
    * The client application can now use the access token to make authorized requests to the resources.
    * When an access token expires, the client application can use the refresh token to obtain the new token. 
    
    For this type of authentication, provide the **client credentials,** and on the consent screen, log in with your user credentials to access the resources.

3. **Password Grant Type**: This type of authorization allows the client application to exchange the user's credentials for an access token. Here’s how it works:
    * The client application authenticates itself to the authorization server by sending its client ID and client secret to the token endpoint.
    * The resource owner provides their credentials (username and password) directly to the client application. The client application sends a POST request to the authorization server's token endpoint, including the user's credentials.
    * If the user's credentials are valid and authorized to access the requested resources, the authorization server responds with an access token.
    * The client application can now use the access token to make authorized requests to the resource server on behalf of the user.

    For this type of authorization, provide the **client credentials** as well as **user credentials** with access to the required resources. 

## Managing Connectors
The Connectors are available under the Content Section. There are two tabs that list the configured connectors and the list of all supported connectors. On the UI, supported connectors are organized by the application type for easy navigation. Additionally, configured connectors are marked with a green indicator.
![Connector Home](images/home.png "connector home")



### Adding a content source using Connector

To set up a new connector, choose it from the list of supported connectors and enter the configuration details. For comprehensive instructions on setting up connectors, refer to the [specific connector documentation](connectors/connector-directory.md).


### Enabling RACL 

To enable RACL in supported connectors, go to the **Permissions and Security** tab and select Permission Aware.

* **Permission Aware**: Automatically syncs the permission information for the ingested content from the third-party application.
* **Public Access**: Irrespective of the permissions in the third-party application, the ingested content is accessible to all SearchAI users. 

You can verify the permissions imported in the ingested content in the <code>sys_racl</code></strong> field in the JSON view of the corresponding content.

For more information on RACL implementation in Search AI, refer to [this](./racl-support.md). 


### Ingesting Content

By default when a connector is added, the content is not ingested from the third-party application until a Sync operation is performed. You can either initiate a sync operation manually or schedule an automatic sync. 

!!!note
    Note that any files larger than 15MB in size will be skipped during the ingestion process.  Ensure that the files are within the size limit for proper ingestion. To increase this limit, [reach out to our support team](https://kore.ai/support/). 


To initiate a sync operation manually, go to the **Configurations** tab in the Connector details and click on **Sync Now**. This initiates the sync operation immediately and ingests new or updated content from the application. 

![Manual Sync](../images/connectors/manual-sync.PNG "Manual Sync")

You can also schedule an automatic sync operation for a future time. Automatic Sync ensures that the data stays up-to-date and also reduces the administrative overhead of performing manual sync regularly. 

The automatic sync can be scheduled as a one-time activity or to be performed at regular intervals. To schedule a sync operation, enable the **Schedule Sync** option and provide the date and time of the beginning of the event. 

![Auto Sync](../images/connectors/schedule-sync.PNG "Auto Sync")

To set up a recurring sync schedule, provide the synchronization frequency along with the date and time of the first sync operation.  Once set, the scheduler automatically ingests content using the connector at regular intervals. 

![Recurring Sync](../images/connectors/recurrent-sync.PNG "Recurring Sync")

To disable automatic synchronization at any time, use the **Schedule Sync** slider button. 

![Disable Sync](../images/connectors/disable-sync.PNG "Disable Sync")

**Stopping the Synchronization**

* If you manually stop synchronization using the **Stop Sync** option while the sync job is actively running, it will halt immediately. Any content that has already been ingested at the time of stopping will be available for search.
* If the sync job is queued when you select Stop Sync, the synchronization will be canceled and will not proceed.

**Status of Ingested Content**

Upon initiating the synchronization operation, the ingestion of the content from the connector begins. You can monitor the progress of this operation by navigating to the **Jobs** tab. The ingested content is displayed under the **Content** tab, which features three separate tabs based on the ingestion status of the content.

* Successful: This section lists content that has been successfully ingested.
* Failed: Here, you will find content that failed to ingest.
* Skipped: This section includes content that was bypassed during the ingestion process.

![Ingestion Logs](images/connectors/ingestion-logs/tabs.png "Ingestion Logs")

For both **failed** and **skipped** content, the application provides detailed logs that can be useful for troubleshooting. These logs include potential reasons for the failure and actionable steps to facilitate successful ingestion in the future. By reviewing these logs, users can gain insights into the issues encountered and take informed actions to resolve them, ensuring a smoother ingestion process moving forward.
![Ingestion Logs](images/connectors/ingestion-logs/errors.png "Error Messages")


### Enabling/Disabling Connectors

After the connector is configured and the source is connected, you can enable or disable the connection temporarily. When a connector is disabled, sync operation is temporarily disabled. This may be useful for testing, particularly when there is more than one connector configured with your Search AIst application. 

!!!Note
    Disabling a connector does not delete the ingested content. It disables any future data synchronization operation with the third-party application. The sync is resumed based on the configuration after the connector is enabled again.

To enable or disable a connector, use the corresponding Action buttons.
![Disable Connector](../images/connectors/disable-connector.png "Disable Connector")

### View and Edit Connector Details

To view or edit the connector configuration, i.e., connection settings, sync schedule, etc.,  click the corresponding connector from the list. The configuration details and content from the connector are shown under different tabs.
![Connector Details](../images/connectors/connector-details.png "Connector Details")

Click on any of the content items to view the details of the ingested content. It provides an overview of the ingested content like file type, URL, preview of the content of the file, etc. Click on **View JSON** to see the details of the ingested content. 
![Content Details](../images/connectors/content-details.png "Content Details")

The JSON view provides detailed information of the ingested content. The ingested content and its metadata are captured in standard fields in the Search AI application. For instance, the description or text of the ingested content is set in the content field, the access information is stored in the sys_racl field, sourceType suggests the source of the content, and the meta_data field captures the meta information of the ingested content. 
![Content Details](../images/connectors/content-details-json.png "Content Details")


**Content**

The **Content** tab lists all the pages crawled from the connector source along with their URL and timestamp of the last update. 

**Jobs**

This tab lists the synchronization-related tasks initiated by Search AI on the connector. 
![Connector Details](../images/connectors/jobs-tab.png "Connector Details")

### Removing the content source integrated using Connector 

To permanently remove a content source and corresponding connector from Search AI, go to the **Authorization tab** and click the **Remove Source** button. This will also **delete any data in Search AI indexed from the content source**.
![Delete Connector](../images/connectors/delete-connector.png "Delete Connector")
