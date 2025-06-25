# Response Templates

Response Templates are predefined (“canned”) messages that agents can use to speed up their delivery of information during customer interactions: welcome messages, salutations, notifications, and more. Response Templates are organized into groups and may be assigned to agents according to skills or agent groups.

To access this feature, go to **Contact Center AI** > **CONFIGURATIONS** > **Response Templates**.
<img src="../images/response-templates-page.png" alt="
Response Templates Page" title="Response Templates Page" style="border: 1px solid gray; zoom:80%;">

## The Response Templates Live Board

The Response Templates section provides the following high-level features:

* **Add** a new Response Group.
* **Name-Level Search** Response Groups and Response Templates. The search runs for groups and responses at the name level and does not extend to the response message content.
* **Browse** Response Templates and Groups by clicking the name of a group. This action opens up the group and lists the responses included within it.

## Response Groups

Response Templates are organized into _Response Groups_, to which agents need to be mapped for responses to be available to them in the [Agent Console](../../../console/agent-console-introduction.md).

### View an Existing Response Group

Click on a Response Group name to view its contents:
<img src="../images/view-existing-response-group.gif" alt="
View Existing response Group" title="View Existing Response Group" style="border: 1px solid gray; zoom:80%;">

Contact Center comes pre-configured with the following Response Groups:

1. **Greeting**: Welcome message like Hello, How may I assist you?
2. **Conversational**: General conversation like a follow-up on a delay, small talk, etc.
3. **Closing**: Closing statements, feedback, request to fill up a survey, thank you, and chat again, closing the chat because of no response from the customer.
4. **Transfer**: Interaction transfer to a manager, agent, or queue.
5. **Abuse**: Fair (initial) and final warning levels when the customer uses abusive language.
6. **Privacy**: Permission-based service responses that enhance conversational privacy.

### Create a Response Group

To create a **Response Group**, follow these steps:

1. Go to **CONFIGURATION > Response Templates**.
2. In the **Response Templates** section, click **+ Response Group**.
<img src="../images/add-response-group.png" alt="
Add Response Group" title="Add Response Group" style="border: 1px solid gray; zoom:80%;">

3. In the **Add New Response Group** panel, provide the following details:
<img src="../images/add-new-response-group-window.png" alt="
Add New Response Group Window" title="Add New Response Group Window" style="border: 1px solid gray; zoom:80%;">
    1. **Group Name** – The name of your **response group**. For example, _Greetings, Sales Responses_, etc.
    2. **Shortcut Command** – Agents can quickly find the group of responses by typing the shortcut command in their chat response box. This action pulls up a list of available responses within the group.
    <img src="../images/response-template-live-interaction.gif" alt="
Shortcut Command Usage" title="Shortcut Command Usage" style="border: 1px solid gray; zoom:80%;">
    3. **Description** – A brief description of the response group.
    4. **Skill Match** – By default, this feature is disabled. While _Skill Match_ is off at the group level, you can map skills per response. If you enable this feature, all the responses in this group will be mapped to the selected skills and made available to matching agents. Therefore, the group and its responses within it will not be made available to agents who are not assigned the mapped skills. The skill match does not take routing into account, so if an agent matches the skills but, for example, is transferred a conversation from an agent with a different skill set, they will still see the responses.
        1. Configure the **OR/AND** conditional logic by toggling between the tabs.
            1. To add a new AND/OR row to a condition, click the **+Add** button on the right.
            2. To delete a row for the _OR condition_, click the **Delete (x)** icon.
            3. To configure the _AND condition_, click the **+ Add** button underneath the AND/_OR_ section.
            4. You can add additional AND/OR conditions after the AND operator.
            5. To delete an entire AND/OR or AND condition, click the **Delete** (bin) icon on the right. This action removes all rows associated with that condition.

            !!! Note

                You cannot restore deleted conditions.
            6. Below is a short demo of this configuration:
            <img src="../images/add-skills-to-response-group.gif" alt="
Shortcut Command Usage" title="Shortcut Command Usage" style="border: 1px solid gray; zoom:90%;">

        2. **Agent Group Match** – This option is disabled by default. When enabled, all the responses in this group appear only to member agents. The **agent** group matching property at each skill level is not available.
        <img src="../images/agent-group-match.png" alt="
Shortcut Command Usage" title="Shortcut Command Usage" style="border: 1px solid gray; zoom:80%;">

!!! Note

    You can enable Skill Match and Agent Group Match, and the responses within the Response Group will display to agents within the selected Groups who match selected skills.

### Edit a Response Group

To update an existing response group, follow these steps:

1. Under **Response Templates**, click the desired _response group name_. This action displays a detailed view of the response group.
2. Click the **Edit** icon next to the group name.
<img src="../images/edit-response.png" alt="
Edit a Response" title="Edit a Response" style="border: 1px solid gray; zoom:100%;">

3. Make the necessary changes in the **Edit Response Group** panel and click **Save**.

### Delete a Response Group

To delete a response group, follow these steps:

1. Under **Response Templates**, click the desired _response group name_.
2. In the detailed view panel, click the **Edit** icon next to the group name.
3. In the **Edit Response Group** panel, click the **Delete Response Group** icon.
4. Click **Delete** on the delete confirmation dialog. This action removes the group and the responses it contains.
<img src="../images/delete-response.png" alt="
Delete a Response" title="Delete a Response" style="border: 1px solid gray; zoom:100%;">

!!! Note

    You cannot restore deleted standard response groups or any responses it contains. Agents will no longer see responses associated with the deleted group within the console. Please proceed with caution.

## Response Management

### Create a Response

To create a new response within a response group, follow these steps:

1. Under **Response Templates**, click the desired response group entry in the list to view the mapped responses.
2. Click **+ New Response**.
<img src="../images/add-new-response.png" alt="Add New Response" title="Add New Response" style="border: 1px solid gray; zoom:80%;">

3. In the **Add New Response** panel, set the title (name) and the auto-expire values.
    1. **Title**: The name to identify the response.
    2. **Auto Expire**: Select **Never** if you don’t want the response to expire. Otherwise, select a **Custom Date** to set the end date and time from the calendar when the response automatically stops appearing.
4. Set the following options under **Chat Response** and **Email Response**:
    3. **Response shown to agents**: To set the response message for agents, enter the message text in the editor, select any required **Variables** from the list to auto-insert into the message (optional), and click **Done**.
    4. **Skill Match and Agent Group Match**: The agent skill or group match configured for the response group applies here and is uneditable if you have matched skills or groups to the response group. If skills, groups, or both have been left disabled at the group level, then you can set them at the response level (for email and chat). The process is the same for the group-level skill and group match, explained above.
    <img src="../images/response-template-variables.png" alt="Response Template Variables" title="Response Template Variables" style="border: 1px solid gray; zoom:80%;">

5. Click **Create** when ready.

### List of Variables within Response Templates

You can use variables to pull customer-specific information from the [context object](../../../automation/intelligence/context-object.md).

You can add the following variables to Response Templates (chat and email):

* `Customer First Name,`
* `Customer Last Name,`
* `Customer Email,`
* `Customer Phone Number,`
* `Agent First Name,`
* `Agent Last Name,`
* `Agent Nick Name,`
* `Agent Email.`

You can find this list in the message editor whenever you add or edit a Response Template.
<img src="../images/response-variables.gif" alt="Response Variables" title="Response Variables" style="border: 1px solid gray; zoom:80%;">

## Edit a Response

To edit the details of an existing response, follow these steps:

1. Under **Response Templates**,  click the desired _response group name_.
2. Find the response you want to update, and click the corresponding **Edit** icon under _Actions_.
<img src="../images/edit-button.png" alt="Edit Response" title="Edit Response" style="border: 1px solid gray; zoom:80%;">

3. Make the required changes in the _Edit Response_ window, then **Save**.

## Delete a Response

To delete a response, follow these steps:

1. Under **Response Templates**, click the desired _response group name._ This action displays an expanded view of the responses mapped to the group.
2. Find the response you want to delete, then click the corresponding **Edit** icon under _Actions_.
3. Click the **Delete (bin)** button on the bottom toolbar in the _Edit Response_ window.
<img src="../images/delete-button.png" alt="Delete Response" title="Delete Response" style="border: 1px solid gray; zoom:80%;">

4. Click **Delete** on the delete confirmation dialog to remove the selected response.

!!! Note

    You cannot restore deleted Response Templates. Agents will no longer see deleted responses in the console. Please proceed with caution.