# List Management

List Management section consist of essential contact details for the campaigns. There are two subsections:

1. **Contact Lists**: Contact lists contain vital information about individuals, enabling targeted and effective communication. It is a collection of names, and contact numbers necessary for running a campaign.
2. **DNC (Do Not Contact) Lists**: These are contacts who have opted for "Do Not Contact" (DNC) or have registered on the national DNC facility, indicating their preference not to receive unsolicited calls. The DNC Lists Contacts count comprises contacts from both uploaded CSV files and contacts added directly through the bot or agent.

You can view the lists by going to **Contact Center** > **Campaigns** > **List Management**.
<img src="../images/contact-lists-main-page.png" alt="List Management Page" title="List Management Page" style="border: 1px solid gray; zoom:80%;">

## Contact Lists

To view the Contact Lists, click the **Contact Lists** tab.

The following details are displayed in Contact Lists:
<img src="../images/contact-lists-table.png" alt="Contact Lists Table" title="Contact Lists Table" style="border: 1px solid gray; zoom:80%;">

* **Contact Lists** - Name of the list. For example, Contact List 1.
* **Actions** - Edit and Delete lists.
* **Status** - Shows the status of the list. For example, Validating, Validated, and Invalid.
* **Contacts** - Shows the total count of contacts in the list. For example, 288.
* **Campaigns** - Name of the Campaign. For example, Post Sales Survey.

### Create a Contact List

Steps to add a contact list:

1. Click **+ New Contact List**.
<img src="../images/new-contact-list-button.png" alt="New Contact List Button" title="New Contact List Button" style="border: 1px solid gray; zoom:80%;">

2. On the **New Contact List** pop-up window, enter the **Name** and **Description** of the list.
<img src="../images/new-contact-list.png" alt="Name and Description of Contact List" title="Name and Description of Contact List" style="border: 1px solid gray; zoom:80%;">

3. Click **Select a CSV file to upload** and upload the CSV file.
<img src="../images/select-csv-for-contact-list.png" alt="Select CSV File" title="Select CSV File" style="border: 1px solid gray; zoom:80%;">

4. The file upload progress is displayed.
<img src="../images/contact-list-upload-progress.png" alt="Contact List Upload" title="Contact List Upload" style="border: 1px solid gray; zoom:80%;">

5. Select the **Mapping Fields** and click **Save**.  
<img src="../images/mapping-fields-contact-list.png" alt="Mapping Fields" title="Mapping Fields" style="border: 1px solid gray; zoom:80%;">

    !!! Note

        Phone Number is mandatory for voice campaigns.

The Contact List is created.

#### Dynamic Retrieval and Reflection of CSV Column Values

Campaign managers can read, fetch, and display column and corresponding field values from a CSV file whenever required. This can be done within the message node in the start flow or by sending the necessary values to the Agent Console during an agent transfer ensuring these values are reflected in the voice campaign call.

* Mapped fields in the uploaded CSV file are readable and can be used within the start flow. These fields can be configured in the message node of the experience flow.
* When a field is configured in the experience flow, the system recognizes it and fetches the corresponding value during outbound campaigns. For example, if the `{{First Name}}` field is configured in a message node, the system retrieves and speaks the relevant value during a voice campaign call.
* The system reads data from the CSV file and transmits necessary information/values to the agent console corresponding to the Customer/Phone number. This applies to both agent transfers in an Agentless Campaign and Auto Dialers on the agent console.
* Non-mapped fields are saved in the data table for additional queries. For example, if there is a column named "Account Num" in the contact, this "Account Num" will be part of the contact data table and can be called as part of the start flow.

To retrieve user information from the context, specifically the user details from the uploaded CSV, we need to extract all the fields present in the CSV. This requires configuring the script node to capture the data from the context and store it in a variable. This allows us to use and modify the data throughout the entire workflow.

Steps to query the CSV fields in the start flow-node:

1. Use the following code to retrieve the data from the context.

    `
let userInfo = context?.campaignUserInfo;
setCallFlowVariable('userInfo', userInfo);
    `  
<img src="../images/script-task.png" alt="MScript Task" title="Script Task" style="border: 1px solid gray; zoom:80%;">  
The user information is stored in the userInfo variable and saved in the `callFlowVariable` for future use.

2. The userInfo data can be used depending on the use case. For example, if we want to create a message to play when calling a customer, we can add the following in a message node:

    `
hi {{context.userInfo.firstName}} {{context.userInfo.lastName}}, your balance on the phoneNumber {{context.userInfo.phoneNumber}} is {{context.userInfo.balance}}, please recharge before the due date {{context.userInfo.dueDate}} {{context.userInfo.month}}
    `
<img src="../images/script-task-customized.png" alt="Customized Script Task" title="Customized script Task" style="border: 1px solid gray; zoom:80%;">  

3. The user details provided in the CSV are fetched as `context.userInfo.firstName` (where `firstName` is the header in the CSV). Similarly, all the other fields can be accessed.

    <img src="../images/insights-to-logs.png" alt="Insights to Logs" title="Insights to Logs" style="border: 1px solid gray; zoom:80%;">  

    <img src="../images/csv.png" alt="CSV Fields" title="CSV Fields" style="border: 1px solid gray; zoom:80%;">  

#### Time Zone
* The "**Timezone**" field of the CSV is validated against the Calling Hours Timezone.
* The time zone mentioned against a contact in the CSV is given preference over Calling Hours.
* When setting up the time zones for an Outbound campaign's contact list or specifying callable times, use the Tz database notation. This notation, also known as tzdata, zoneinfo database, or IANA Time Zone Database, provides a standardized naming convention for time zones across the globe.
* Each location is identified in the Tz database by its continent or ocean, followed by the largest city in that area. For example,
    * America/Phoenix
    * Asia/Hong_Kong
    * Pacific/Fiji
* If a contact has a timezone mentioned, the timezone will be validated or converted before dialing. If the contact’s timezone doesn’t fall under calling hours then the contact will be skipped.
* If a contact is skipped then it is considered a check and the Campaign is "**Completed**" once all other contacts are dialed successfully.
* Contacts skipped due to timezone mismatch will appear as "**Unconnected Calls**" on the Campaign Dashboard.

### Edit a Contact List

Steps to edit a contact list:

1. Click the **Edit** icon beside the contact list name.
<img src="../images/edit-call-list-button.png" alt="Edit Contact List Button" title="Edit Contact List Button" style="border: 1px solid gray; zoom:80%;">

2. Upload the call list and click **Save** when the list is appended.
<img src="../images/append-contact-list.png" alt="Append Contact List" title="Append Contact List" style="border: 1px solid gray; zoom:80%;">

    !!! Note

        You can only append a contact list, you cannot edit an existing contact list.

### Delete a Contact List

Steps to delete a contact list:

1. Click the **Edit** icon beside the contact list name and click the **Delete** icon at the bottom left corner of the edit window.
<img src="../images/delete-call-list.png" alt="Delete Contact List" title="Delete Contact List" style="border: 1px solid gray; zoom:80%;">

    !!! Note

        You cannot delete a contact list if it is associated with any campaign.

2. A confirmation message is displayed. Click **Delete**.
<img src="../images/delete-list-confirmation.png" alt="Delete Contact List Confirmation" title="Delete Contact List Confirmation" style="border: 1px solid gray; zoom:80%;">

The contact list is deleted.

## DNC Lists

### Create a DNC List

To create a DNC List, click the **DNC Lists** tab.

Steps to create a new DNC list:

1. Click **+ New DNC List**.
<img src="../images/new-dnc-list.png" alt="New DNC List" title="New DNC List" style="border: 1px solid gray; zoom:80%;">

2. On the **New DNC List** pop-up window, enter the **Name** and **Description** of the list.
<img src="../images/dnc-list-name-description.png" alt="Name and Description DNC List" title="Name and Description DNC List" style="border: 1px solid gray; zoom:80%;">

    !!! Note

        As of now, the default DNC List Type is Internal.

3. Click **Select a CSV file to upload** a CSV file.
<img src="../images/upload-dnc-call-list.png" alt="Upload DNC List" title="DeUpload DNC List" style="border: 1px solid gray; zoom:80%;">

    !!! Note

        You can download the template for the CSV file by clicking the CSV Template.

4. The file upload progress is displayed.
<img src="../images/dnc-list-progress.png" alt="DNC List Upload Progress" title="DNC List Upload Progress" style="border: 1px solid gray; zoom:80%;">

5. Select the **Mapping Fields** and click **Next**.
<img src="../images/dnc-list-mapping-fields.png" alt="DNC List Mapping Fields" title="DNC List Mapping Fields" style="border: 1px solid gray; zoom:80%;">

The DNC List is created.

### Edit a DNC List

Steps to edit a DNC list:

1. Click the **Edit** button.
<img src="../images/edit-dnc-list-button.png" alt="Edit DNC List Button" title="Edit DNC List Button" style="border: 1px solid gray; zoom:80%;">

    !!! Note

        You cannot delete a DNC list when it is "In use".

2. Upload the DNC list and click **Save** when the list is appended.
<img src="../images/edit-dnc-list.png" alt="Edit DNC List" title="Edit DNC List" style="border: 1px solid gray; zoom:80%;">

### Delete a DNC List

Steps to delete a DNC list:

1. Click the **Edit** icon beside the DNC list name and click the **Delete** icon at the bottom left corner of the edit window.
<img src="../images/delete-dnc-list.png" alt="Delete DNC List" title="Delete DNC List" style="border: 1px solid gray; zoom:80%;">

    !!! Note

        You cannot delete a DNC list when it is "In use".

2. A confirmation message is displayed. Click **Delete**.
<img src="../images/delete-dnc-list-confirmation.png" alt="Delete DNC List Confirmation" title="Delete DNC List Confirmation" style="border: 1px solid gray; zoom:80%;">

The DNC list is deleted.