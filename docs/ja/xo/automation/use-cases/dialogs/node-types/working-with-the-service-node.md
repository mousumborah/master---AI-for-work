# Service Node

The Service Node is a component type in a dialog task that you can use to add an API service to make REST or SOAP requests to third-party web services. You can use this node when you have the parameters needed for the API request using an entity or other nodes to capture the user input.

## Add the Node

The setup of a Service node in a dialog task involves the following steps:

1. Open the dialog task to add the Service node.
2. Add a Service node in the designated place. For steps related to adding nodes, [refer here](../../using-the-dialog-builder-tool/#add-nodes){:target="_blank"}.

    !!! note

        You can add a service node within an existing sequence or outside any existing sequence. If you add it outside, a new, untitled sequence will automatically get created containing the new Service node.

3. The Service window is displayed with the **Component Properties** tab selected by default.

    <img src="../images/service-node-img1.png" alt="Service node - Add node" title="Service node - Add node" style="border:1px solid gray;zoom:70%;">


## Configure the Node

### Component Properties

!!! Note

    All changes made to the Component Properties tab will affect all instances of the Service node, across Dialog Tasks. 

To configure the Component Properties tab, please follow the steps below:

1. On the **Component Properties** tab, enter the **Name** and **Display Name** of your Service node. 
2. Choose a **Service Type** from the drop-down list:
    1. **Custom Service** – Define an API request to a third-party web service. This is the default setting.
    2. **HTML to Image** – Define HTML to render as an image using JavaScript. For example, to compose HTML or the value of a key in a web service response that contains HTML markup as a string that you want to convert to an image.
    3. **URL to Image** – Define a web page URL to load to render an image.
    4. **Custom Authentication Service** – Define a URL to a third-party application that provides the authentication services necessary for the task flow. [Learn more](../../implementing-custom-authentication){:target="_blank"}.
    5. **Alert Subscription Service** – Define contextually relevant alerts to be sent proactively to the user as a part of the dialog journey.
    6. **Data Service** – Define CRUD operations to query and manipulate the data for any given data table/table view.

3. Based on the service type selected, select the **Type/Sub Type** from the respective drop-down lists or Auth URL.
4. Define the **Pre-processor Script** to pass the input parameters dynamically for executing an Service Node’s API call. [Learn more](#pre-processor-script).

5. Under the **Request Definition** section, click **Define Request**.

    <img src="../images/service-node-img2-define-request.png" alt="Service node - Define request" title="Service node - Define request" style="border:1px solid gray;zoom:70%;">

    !!! Note
    
        In the case of a **Custom Authentication Service** service type, the Request Definition section does not apply and you can see a Response.
    
6. The **Define Request for &lt; _ServiceXXXX_ >** dialog is displayed, as shown in the following illustration.

    <img src="../images/service-node-img3-define-request-dialog.png" alt="Service node - Define request dialog" title="Service node - Define request dialog" style="border:1px solid gray;zoom:70%;">

7. Click the **Auth** tab to create a new Authorization Profile or select an existing profile. For more information, see the [Bot Authorization Overview](../../../../../app-settings/dev-tools/bot-authorization/bot-authentication/) article.

8. Define the Post-processor Script to fetch the API response parameters using the Service Node and define the dialog flow. [Learn more](#post-processor-script).

9. Add the sample response(s) you want the Service Node to return.

    <img src="../images/service-node-img4-add-sample-response.png" alt="Service node - Sample response" title="Service node - Sample response" style="border:1px solid gray;zoom:70%;">

    Depending on the Service Type selected, refer to one of the following sections in this topic:

    1. [Defining a Custom Service](#custom)
    2. [Defining a URL to Convert to Image](#define-a-url-to-convert-to-image)
    3. [Defining HTML to Convert to Image](#define-html-to-convert-to-image)
    4. [Defining Alert Subscription Service](#define-an-alert-subscription-service)
    5. [Defining Data Service](#define-a-data-service)
  
10. In the **Variable Namespaces** section, associate the variable namespaces to execute this node and its transitions. This option is visible only when the Variable Namespace is enabled for the VA. You can go with the task level settings or customize it for this node. For more information, refer to [Managing Namespace](../../../../../app-settings/managing-namespace){:target="_blank"}.

!!! Note

    Post v11.3 release:  
     1.  **Service Call Timeout** and **Timeout Error Handling Behavior** settings have been moved from Component Properties to Instance Properties within the Service Node.  
     2.  The modifications made are exclusive to the particular dialog task and will not impact any other dialog tasks utilizing the same Service Node.


#### Pre-processor Script

The Pre-processor Script helps execute a custom JavaScript code within the Service Node to manipulate existing values or set new ones within the context and pass the input parameters dynamically for executing an API call using the Service Node. It works similarly to the Script Node. [Learn more](#configure-the-node).

With the Pre-processor Script, the Platform does not have to process additional Script nodes to execute a single service node.

Steps to Configure a Pre-processor Script

1. Open the dialog task.
2. In the dialog builder, click the required Service Node.
3. In the **Component Properties** window, click **Define Script** in the Pre-processor/Post-processor Script section.

    <img src="../images/service-node-img6-define-script-pre-and-post-processor.png" alt="Service node - Pre-processor script" title="Service node - Pre-processor script" style="border:1px solid gray;zoom:70%;">

4. In the Add Script window, add the script you want to execute, and click **Save**.

    <img src="../images/service-node-img7-add-script-to-service-node.png" alt="Service node - Add Pre-processor script" title="Service node - Add Pre-processor script" style="border:1px solid gray;zoom:70%;">

!!! note

    Pre-processor Script is available for all the existing service nodes (treated as an empty script node) and does not have any JavaScript defined.

#### Post-processor Script

The **Post-processor Script** executes the defined JavaScript code following the execution of the service node.

Using this property, developers can fetch and store only the required Service Node API response parameters in the context object and define the dialog execution flow. The Post-processor Script has the same properties as the Script Node. [Learn more](#configure-the-node).

The steps to configure a Post-processor Script are the same as the Pre-processor Script. Click [here](#pre-processor-script) to learn more.

!!! note

    Post-processor is available for all the existing service nodes (treated as an empty script node) and does not have any JavaScript defined.

### Instance Properties

!!! Note

    The settings in the Instance Properties tab are specific to the current dialog task and do not reflect in other dialog tasks that use this node.

Use the Instance Properties to define any user tags that you want to set.

1. On the Service node properties panel, click the **Instance Properties** tab.
2. Under **Advanced Controls**, select the maximum wait time for the **Timeout** for service node calls and decide how the bot can respond or choose an alternate path when timeout occurs. You can configure the following settings:
    1. **Timeout(Seconds)**: Select the maximum wait time from the dropdown list. The timeout range can be any value between **1 Second** to **60 Seconds**. The default value is 20 Seconds.
    2. **Timeout error handling**: Choose how the bot should respond when the timeout occurs.
        * **Close the Task and trigger Task Execution Failure Event**, or
        * **Continue with the task and transition to this node**; select the node to which the service call can transition in the flow.

      

3. Under the **Custom Tags** section, add tags to build custom profiles of your VA’s conversations. [Click here for more](../../../../../analytics/automation/custom-dashboard/custom-meta-tags){:target="_blank"}.

<img src="../images/service-node-img5-timeout-error-handling.png" alt="Service node - Timeout Error handling" title="Service node - Timeout Error handling" style="border:1px solid gray;zoom:70%;">


### Connections Properties

!!! Note
    
    * The conditions configured here are applicable only for this instance and will not affect this node when being used in any other dialog.
    * The connection properties would be present only if this is the bottommost node of a sequence.

To set up node connection conditions, please follow the steps outlined in [Adding IF-Else Conditions to Node Connections. ](../../node-connections/nodes-conditions){:target="_blank"}

<img src="../images/service-node-img9-connection-properties.png" alt="Service node - Connection properties" title="Service node - Connection properties" style="border:1px solid gray;zoom:70%;">


## Service Types

You can define the Service Type as:

* **Custom Service** – Define an API request to a third-party web service. This is the default setting.
* **HTML to Image** – Define HTML to render as an image using JavaScript. For example, to compose HTML or the value of a key in a web service response that contains HTML markup as a string that you want to convert to an image.
* **URL to Image** – Define a web page URL to load to render an image.
* **Custom Authentication Service** – Define a URL to a third-party application that provides the authentication services necessary for the task flow.
* **Alert Subscription Service** – Define contextually relevant alerts to be sent proactively to the user as a part of the dialog journey.
* **Data Table Service** – Define CRUD operations to query and manipulate the data for any given data table/table view assigned to the Virtual Assistant.


### Define a Custom Service

1. When you select **Custom Service** in the **Service Type**, then in the **Sub-Type** field, select one of the options:
    1. **REST** – The API web service is using REST services.
    2. **SOAP** – The API web service is using SOAP services.

2. In the **Request Definition** section, click **Define Request** to specify the settings for the web service type.
3. The **Define Request for &lt; _Service Node Name_ >** dialog is displayed as shown in the following illustration.
4. In the **Request URL** field, in the first field, select the HTTP method used for the request. You can select:
    1. **POST**– Used to send data to the server. For example, customer information, file upload, and so forth using HTML forms.
    2. **PUT**– Replaces the content of the target resource with the content sent.
    3. **PATCH** – Appends the content of an existing target resource with the content sent.
    4. **DELETE** – Deletes the content of an existing target resource.
    5. **GET** – Returns the content of an existing target resource

5. In the second field of the **Request URL**, specify the URL for the dialog task response to process at Kore.ai. For example, http://koremessenger.com/postURL. Add query or path parameters as part of the URL, if required. To use entity node values as parameters, use the following syntax for accessing the `Context` object: https://myDomain.com/{{context.entities.topic}} for the `context.entities.topic`. You must use the double brackets `{{ context.object }}`. For more information, refer to [Context Object](../../../intelligence/context-object.md){:target="_blank"}.
    1. Optionally, click **Show Advanced**, and select  

        1. **Yes** in the **Access Using A Connector** field if access for Kore.ai assistants is using the Kore.ai connector agent. For more information, refer to [Using the Kore.ai Connector](../../../../../administration/kore-ai-connector){:target="_blank"}.  
        2. **Yes** in the **De-Identification of PII Data** to redact any sensitive information types that users share with your assistants. For more information, refer to [Redacting Personally Identifiable Information](../../../../../app-settings/advanced-settings/pii-data-masking){:target="_blank"}
    
    2. In the **Auth** tab, select the type of authorization needed for this service node call, or define a new authorization type if needed. For more information, refer to [Setting Up Authentication](../../../../../app-settings/dev-tools/bot-authorization/bot-authentication){:target="_blank"}.
    3. In the **Headers** tab, specify the headers as key/value pairs if required to access the specified request URL.  Authentication headers are auto-generated based on the authorization type specified on the **Auth** tab. You need to define any other standard headers. For example, Content-type, Accept, or any custom headers. Headers defined here are only applicable to this service node.
    4. In the **Body** tab, select the body content type. You can select:
        * **application/x-www-form-urlencoded** – Also known as Multipart/Form-data, which is an encoding type that allows files to be sent through an HTTP POST request method if you want to allow a user to upload a file from a form. You can add key/value pairs that are encoded by the XO Platform.
        * **application/json** – Use JSON to transmit data between the Kore.ai servers and your VA’s web application. Any JSON is sent with the request without any processing.
        * **application/xml** – For SOAP services, pass XML payload using POST methods. You can pass entity node values as part of the XML, using the following syntax for accessing the `Context` object: https://myDomain.com/{{context.entities.topic}} for the `context.entities.topic`. You must use the double brackets `{{ context.object }}`. For more information, refer to [Context Object](../../../intelligence/context-object.md){:target="_blank"}.
    
    5. In the **Test Request** tab, click **Test** to optionally send your API request URL using the specified Auth type, HTTP headers, and body parameters, if defined. The response is displayed in the text area. Click **Save as Sample Response** to save the test response as the sample response for this node.
    6. Click **Save** to save the request for the service node and close the **Define Request for &lt; _Service Node Name_ >** dialog.

6. In the **Sample Response** section, optionally click **Add Sample Response** to display the **Add Sample Response** dialog that you can use to manually enter or paste a sample response.
7. Optionally, in the **Add Sample Response** drop-down list, you can select:
    1. **JSON** – A list of JSON key/value pairs available in the request URL response used in other nodes as variables.
    2. **RAW** – A list of key/value pairs that are used in other nodes as variables.

8. In the **Component Properties** section, select the maximum wait time for the **Timeout** for service node calls and decide how the bot can respond or choose an alternate path when timeout occurs. You can configure the following settings.
    1. **Timeout(Seconds)**: Select the maximum wait time from the drop-down list. The timeout range can be any value between _1 Second_ to _20 Seconds_. The default value is **5 Seconds**.
    2. **Timeout error handling**: Choose how the bot should respond when the timeout occurs.
        * **Close the Task and trigger Task Execution Failure Event**, or
        * **Continue with the task and transition to this node**; select the node to which the service call can transition in the flow.


### Define a URL to Convert to Image

1. When you select **URL to Image** in the **Service Type**, the **Type** setting is read-only.
2. In the **Request Definition** section, click **Define Request** to specify the settings when the **URL to Image** is selected for **Service Type**. The **Define Request for &lt; _Service Node Name_ >** dialog is displayed as shown in the following illustration.
3. In the **URL to Convert** field, enter the URL for the image. The syntax when using a `Context` object key in a URL is to enclose the object name in double brackets, for example, https://myURLimage.com/{{context.entities.imageName}}.
4. In the **Render Sizes** section, specify a name for the image size. For example, for an iPhone or tablet, enter the **Width** and **Height** in pixels; then click **+Add** to add additional sizes, or click **Add** to save and close the dialog.
5. Click **Save** to save the request for the service node and close the **Define Request for &lt; _Service Node Name_ >** dialog.

!!! Note

    By default, the webpage loading time is configured as 2 seconds. If the page loads within 2 seconds, then a screenshot is captured. Otherwise, a blank page is displayed.


### Define HTML to Convert to Image

1. When you select **HTML to Image** in the **Service Type**, the **Type** setting is read-only.
2. In the **Request Definition** section, click **Define Request** to specify the settings when **HTML to Image** is selected for **Service Type**. The **Define Request for &lt; _Service Node Name_ >** dialog is displayed as shown in the following illustration.
3. In the **HTML to Convert** field, enter the HTML for the image.
4. In the **Render Sizes** section, specify a name for the image size. For example, for an iPhone or tablet, enter the **Width** and **Height** in pixels; then click **+Add** to add additional sizes, or click **Add** to save and close the dialog.

The following is an example for converting HTML to an image:

```
<head>

<link href="../assets/styles.min.css" rel="stylesheet"/>

<title>HTML: Print Wide HTML Tables</title>

<script src="//ajax.googleapis.com/ajax/libs/jquery/1.10.2/jquery.min.js"></script>

<style>

 .style1 {

    border-collapse: collapse;

    }

 .style1 th {

    background-color: #DDDDDD;

    white-space: nowrap;

    }

 .style1 .d {

    white-space: nowrap;

    }

 .style1 .n {

    padding-left: 20px;

    text-align: right;

    }

</style>

</head>

<body>

<table id="table1" class="style1" border="1" cellpadding="4" cellspacing="0">

 ///TODO Add Table Rows here.

</table>

<input type="button" id="print-button" value="Make this table printable contact@ {{context.session.UserContext.emailId}}"/>

<script>

/*

* HTML: Print Wide HTML Tables

* http://salman-w.blogspot.com/2013/04/printing-wide-html-tables.html

*/

$(function() {

$("#print-button").on("click", function() {

  var table = $("#table1"),

      tableWidth = table.outerWidth(),

      pageWidth = 600,

      pageCount = Math.ceil(tableWidth / pageWidth),

      printWrap = $("<div></div>").insertAfter(table),

      i,

      printPage;

  for (i = 0; i < pageCount; i++) {

     printPage = $("<div></div>").css({

         "overflow": "hidden",

         "width": pageWidth,

         "page-break-before": i === 0 ? "auto" : "always"

       }).appendTo(printWrap);

  table.clone().removeAttr("id").appendTo(printPage).css({

     "position": "relative",

     "left": -i * pageWidth

    });

  }

table.hide();

$(this).prop("disabled", true);

});

});

</script>

</body>

</html>
```

The preceding HTML example, when table rows are added into the example, can render the following image to an end-user.

<img src="../images/service-node-img10-html-to-image.png" alt="Service node - HTML to Image" title="Service node - HTML to Image" style="border:1px solid gray;zoom:70%;">


### Define an Alert Subscription Service

You can now automatically subscribe your users to send contextually relevant alerts as part of the dialog journey. For example, a person booking a flight ticket for a specific date is auto-subscribed to get regular updates on the weather forecast for the destination city.

To set up an alert subscription service, follow the below steps:

1. Open the **Component Properties** tab of the service node to which you want to associate the alert.
2. Under the **General Settings** section, select **Auto Subscription Service** from the **Service Type** drop-down list.
3. Click **Define Request**.  
  
    !!! Note
    
        To create an alert subscription service, you must base it on an existing alert task. Users are auto-subscribed to the alert task on reaching the associated service node in the dialog.

4. On the Smart/Automatic Alerts dialog box, select an alert task from the **Choose Alert** drop-down list. The list consists of only the published alert tasks related to your VA.
5. Enter the necessary information as explained below.


#### Alert Subscription (Smart Alert) Configurations

In a typical alert setup, the alert parameters, filters, and other necessary details are entered by the users. Since this is an auto-subscription for alerts, you need to configure those details as a developer.

**Alert Parameters**

These vary according to the alert you select. Provide the default parameter values to use for the Alert Subscription service.

In this example, the parameters defined for the alert are _Topic Name_ and _News Region_. Since the idea is to send weather forecasts to the user for the destination city, you can set the parameter values as _Weather Forecast_ and _context.entity.destinationcity_ respectively.

**Filters**

These vary according to the alert you select. Provide the filter criteria to use for the Alert Subscription service.

**Alert Frequency**

Provide the frequency to send alert notifications. You need to select a Scheme, Frequency, and Time Frame.

1. From the **Select Scheme** drop-down list, select daily, weekday, or weekend, depending on when you want to send the alert.
2. From the **Select Frequency** drop-down list, select _Every_ if you want to send multiple alerts at regular intervals of time in a day or select _at_ to send one alert at a specific time of the day.
3. From the **Select Time** drop-down list, select an interval time value or a time of the day, depending on the frequency value chosen above.

    For example, _Daily At 6 a.m._ means that an alert is sent to the user every day at 6 a.m.

**Smart Alert Expiry**

Configure when to expire sending alerts to the users from one of the following options:

1. **Duration**: Stops sending notification after the entered number of days from the date of subscription.
2. **Number of Notifications**: Stops sending alerts after an entered number of notifications are sent.

**Alert Upgrades**

Define the expected behavior of this alert if an upgraded version of the underlying alert task (the published alert that you have selected at the beginning) is published.

1. **Remove Existing Instances –** All existing subscriptions of this smart alert are removed and users will no longer receive notifications. Users are auto-subscribed to the upgraded alert task only when they execute the dialog and reach the service node in the dialog journey.
2. **Allow Users To Manually Upgrade Subscription –** Users will receive an upgrade notification on the selected channel which is a link that guides them through to upgrade their auto-subscription. If the upgrade is successful, the user will receive a success notification.


### Define a Data Service

1. When you select **Data Service** in the **Service Type**, the **Type** setting provides two options:
    1. Table – choose this option to perform CRUD operations on the data table.
    2. View – choose this option to fetch data from a table view.

        !!! Note
        
            Your VA should have permission to access the table/view. The owner of the table/view has to grant this permission, [click here for how](../../../../../administration/data/data-table/#assignments){:target="_blank"}.

2. In the **Request Definition** section, click **Define Request** to specify the operation you want to perform. [Click here for details.](../../../../../administration/data/data-as-service){:target="_blank"}


## Next Steps

* [Implement Custom Authentication for the Service Node](./../implementing-custom-authentication.md) or
* [Enable 2-way SSL for the Service node](./../enabling-2-way-ssl-for-service-nodes.md)