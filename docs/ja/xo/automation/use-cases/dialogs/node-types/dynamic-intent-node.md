# Dynamic Intent Node

The Dynamic Intent node lets you dynamically trigger any of the flows in the bot by defining the intent's display name using variables. The target intent can be either a Dialog Task or a FAQ. You can use this node to proactively disambiguate an intent and choose different intents based on the user or conversation context.

In the case of linked bots associated with Universal Bots, you can also use this node to trigger flows present in any other linked bots of the corresponding Universal Bot. This feature allows you to invoke reusable or utility flows in one linked bot from another, for example, user authentication, OTP verification, etc. It simplifies switching between tasks in different linked bots of a Universal Bot.


## Key Points

* The target task can be within the current bot, or if connected to a Universal Bot, it can be in any of the other linked bots of the Universal Bot.
* You can define the display name of the target intent using Context or Environment variables.
* The platform resolves the context or environment variable during runtime to identify the target intent.
* If the variable fails to provide a valid Dialog Task or FAQ Name, the current task will be discarded, and the Task Failure Event will be triggered.

Setting up a Dynamic Intent node in a dialog task involves adding the node at the appropriate location in the dialog flow and configuring various properties of the node, as explained below.


## Add the Node

1. Open the dialog task to which you want to add the dynamic intent node.
2. Use the **“+”** button next to the node after which you want to add the dynamic intent node, choose **+ New Node > Dynamic Intent**.

The Dynamic Intent window is displayed with the **Component Properties** tab selected by default.  

<img src="../images/dynamic-intent-node-img1.png" alt="Dynamic intent node" title="Dynamic intent node" style="border:1px solid gray;zoom:70%;">


## Configure the Node

### Component Properties

The settings made within this section affect this node across all instances in all dialog tasks.  

<img src="../images/dynamic-intent-node-img2.png" alt="Dynamic intent node - Component properties" title="Dynamic intent node - Component properties" style="border:1px solid gray;zoom:70%;">


1. Enter **Name**, **Display Name**, and **Description** for the node. The node name cannot contain spaces.


2. **Target Intent Name**  
    
    In this section, you can define the display name of the intent (Dialog Task or FAQ) that you want to switch to. Use context variable or environment variable to define the display name as follows:

    * Context Variable – `{{context.targetTaskName}}`
    * Environment Variable – `{{env.targetTaskName}}  
    `Where `targetTaskName` is a variable that contains the target intent's display name as the value.

    Example Scenarios:

    * **If the target intent is present within the same bot**: The variable must use a valid display name of an intent within the bot. The target intent can be associated with a Dialog Task or FAQ. Consider the following intent display names – `reset_password`, `apply_paid_leave`, or `how often should I reset my password`. In the **Target Intent Name** field, you can use either the display name `reset_password` as static text or the context variable `{{context.targetTaskName}}` where the variable `targetTaskName` contains the display name `reset_password` as the value.
    * **If the target intent is present in a different linked bot** (the target bot and the current bot are linked to a common Universal Bot): The variable must refer to the target linked bot name and the display name of the intent within the target bot, separated by a ‘dot’. Consider the following intent names – `HRBot.apply_paid_leave`, `ITBot.reset_password`, or `ITBot.how often should I reset my password`. In the **Target Intent Name** field, you can use either the display name `ITBot.reset_password` as static text or the context variable `{{context.targetTaskName}}` where the variable `targetTaskName` contains the display name `ITBot.reset_password` as the value.


3. **Target Intent Error Transition**

    In this section, you can select the flow of execution to be followed in case the Platform fails to resolve the defined target intent:

    * Ignore this node and continue with the execution of the following node in the transition; this option is selected by default.
    * Trigger Task failure event


### Instance Properties

Under the Instance Properties tab, you can configure the instance-specific fields for this Dynamic Intent intent node. These settings are applicable only for this instance and will not affect any other instances of this node.  

<img src="../images/dynamic-intent-node-img3.png" alt="Dynamic intent node - Instance properties" title="Dynamic intent node - Instance properties" style="border:1px solid gray;zoom:70%;">


#### Entity Pre-Assignments

In this section, you can assign values for the entities or context variables of the target dialog task. Provide the name of the entity or context variable of the target intent and define the value to be assigned from the current task’s context.

Key/Value should prefix with context for getting values from the context object.  
Key: `Entity name`  
Value: `context.path of the value which needs to be assigned to the entity`

!!! Note

    This setting is ignored if the target intent is FAQ.


#### Entity Post-Assignments

In this section, you can assign values for the entities and context variables of the current task after returning from the target task. Provide the name of the entity or context variable of the current task and define the value to be assigned from the target task’s context.

Key/Value should prefix with context for getting values from the context object.  
Key: `Entity name`  
Value: `context.path of the value which needs to be assigned to the entity`


#### Transition Options

In this section, you can select the flow to be followed once the task completes. You can choose from two options:

* Initiate the target intent execution from within the current context
* End the current task and initiate the target task


#### Advanced Controls

In this section, you can add Custom Meta Tags to the conversation flow to profile VA-user conversations and derive business-critical insights from usage and execution metrics. You can add tags for the following:

* Message – Define custom tags to be added to the current message in the conversation.
* User – Define custom tags to be added to the user’s profile information.
* Session – Define custom tags to be added to the current conversation session.

For more information on custom tags, see [Custom Meta Tags](../../../../../analytics/automation/custom-dashboard/custom-meta-tags){:target="_blank"}.


### Connections Properties

!!! Note

    Connection properties can be seen and accessed only if this is the bottommost node of a sequence.

Click the Connections tab and set the transition properties to determine the node in the dialog task to execute next. You can write conditional statements based on the values of any Entity or Context Objects in the dialog task, or you can use intents for transitions. See [Adding IF-Else Conditions to Node Connections](../../node-connections/nodes-conditions/){:target="_blank"} for a detailed setup guide.  

<img src="../images/dynamic-intent-node-img4.png" alt="Dynamic intent node - Connection properties" title="Dynamic intent node - Connection properties" style="border:1px solid gray;zoom:70%;">

!!! Note

    These conditions apply only for this instance and will not affect this node when used in any other dialog.