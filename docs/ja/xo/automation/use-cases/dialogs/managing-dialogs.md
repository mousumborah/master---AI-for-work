# Managing Dialogs

Your bot can have many dialog tasks with related components. You can use the Dialog Editor to create, review, and edit a single dialog task for a bot. However, to better visualize and understand relationships and settings for all dialog tasks in a bot, you must use the Manage Components feature.


## Manage Task Components

To manage your dialog tasks, follow the below steps:

1. Open the bot for which you want to manage the dialog task components.
2. Select the **Automation** from the left menu
3. On the **Automation** menu, click **USE CASES > Dialogs**.
4. Click **Manage Components** on the top-right.

    <img src="../images/manage-components-img1.png" alt="Manage Components" title="Manage Components" style="border: 1px solid gray; zoom:60%;">


## Dialog Components

The Dialog Components window shows all the components used in any dialog task of the bot. To view or modify the settings of a component, click its name. The Properties panel of the node opens.

<img src="../images/manage-components-img2.png" alt="Dialog Components" title="Dialog Components" style="border: 1px solid gray; zoom:60%;">

The following table lists the details included in the window for each component type


<table>
  <tr>
   <td><strong>COMPONENT TYPE</strong>
   </td>
   <td><strong>DETAILS</strong>
   </td>
  </tr>
  <tr>
   <td><strong>User Intent</strong>
   </td>
   <td>
<ul>

<li>Name

<li>Display Name

<li>Description

<li>Dialog Tasks used in
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><strong>Entity</strong>
   </td>
   <td>
<ul>

<li>Name

<li>Display Name

<li>Entity Type

<li>Dialog Tasks used in
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><strong>Service</strong>
   </td>
   <td>
<ul>

<li>Name

<li>Display Name

<li>Service Type

<li>Dialog Tasks used in
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><strong>Script</strong>
   </td>
   <td>
<ul>

<li>Name

<li>Display Name

<li>Dialog Tasks used in
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><strong>Message</strong>
   </td>
   <td>
<ul>

<li>Name

<li>Display Name

<li>Dialog Tasks used in
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><strong>Confirmation</strong>
   </td>
   <td>
<ul>

<li>Name

<li>Display Name

<li>Dialog Tasks used in
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><strong>GenAI Node</strong>
   </td>
   <td>
<ul>

<li>Name

<li>Display Name

<li>Dialog Tasks used in
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><strong>GenAI Prompt</strong>
   </td>
   <td>
<ul>

<li>Name

<li>Display Name

<li>Dialog Tasks used in
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><strong>Webhook</strong>
   </td>
   <td>
<ul>

<li>Name

<li>Display Name

<li>Dialog Tasks used in
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><strong>Agent Transfer</strong>
   </td>
   <td>
<ul>

<li>Name

<li>Display Name

<li>Dialog Tasks used in
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><strong>Form</strong>
   </td>
   <td>
<ul>

<li>Name

<li>Display Name

<li>Dialog Tasks used in
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><strong>Logic</strong>
   </td>
   <td>
<ul>

<li>Name

<li>Display Name

<li>Dialog Tasks used in
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><strong>Bot Action</strong>
   </td>
   <td>
<ul>

<li>Name

<li>Display Name

<li>Dialog Tasks used in
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><strong>Process</strong>
   </td>
   <td>
<ul>

<li>Name

<li>Display Name

<li>Dialog Tasks used in
</li>
</ul>
   </td>
  </tr>
</table>

## Upgrade Tasks

After you publish a task, the Bots Admin approves and deploys the task to make changes in the published bot. You must upgrade the bot; then publish the upgrade for Bots Admin approval and deploy it to users.

### Upgrade Tasks

If you need changes to the published task, you must upgrade the task to a new version.

### Upgrade Types

There are two types of upgrades for a task:

* **Mandatory** – A mandatory upgrade generally does not require end-user action, and users are only informed that the task was upgraded with an auto-upgrade. If a mandatory upgrade does require end-user action, for example, new authentication requirements, the end-user is notified to take the action for a manual upgrade, sent reminder notifications, and finally, expiration of the original task after 15 days.
* **Optional** – An optional upgrade is not required and is not auto-upgraded for users. End-user action is required to complete the manual upgrade and the user can choose whether or not to upgrade.


### Task Upgrade Definitions

A **Version Type** is either a major or minor update. Depending on the changes of the bot task, you can specify the version type as a minor or major update for the revision number. All published tasks begin with the **Version** set to **1.0**. A major update is set with the **Version** to **2.0**, while a minor update is set with the **Version** to **1.1**.

As part of the end-user upgrade experience, you must define the messages shown to the user to describe the upgrade and other messages that describe what the upgrade will change.


### Verify Flows

If the upgraded task is mapped in a flow, you must review, update, and confirm existing mapping values defined in the flow. If the flows are not verified, mapped action tasks will not be displayed in the upgraded task for the end-user.

!!! note

    You cannot publish another upgrade to a mandatory published task that requires manual end-user input during the initial 15-day deployment.


### Upgrade a Task

Using the **Upgrade** command, a duplicate of the original task is created where you can make your modifications without affecting the published version. Then, when ready to deploy, you can decide if the upgraded task is mandatory or optional for users that are already using the originally published task.

To upgrade a task, follow the below steps:

1. Open the app to edit the task
2. Select the **Automation** from the left menu
3. On the **Automation** menu, click **USE CASES > Dialogs**..
4. Click the **More** icon of the published task you want to upgrade, and then click **Upgrade**.
5. A duplicate of the published task is created with the **Status** set to **Upgrade In Progress** and the **General** tab is displayed.
6. Modify the task and click **Finish Setup**.

After the modifications to the upgraded task, the task status is set to **Configured** and the version is set to **Draft**.

**Next Steps**

You might want to look into how to work with the Prompt Editor, [refer here for more](../prompt-editor/){:target="_blank"}.