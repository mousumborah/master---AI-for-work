# Configure Agent Node

By default, the Agent Node is disabled. Enable the node from **Generative AI Tools** > **GenAI Features** > **Dynamic Conversations**. [Learn more](../../../../generative-ai-tools/dynamic-conversations-features.md/#agent-node).

Add the node to a dialog task and configure the node's properties and tool calling capabilities.  

## Add Agent Node to a Dialog Task

Steps to add an Agent node to a Dialog Task:

1. Go to **Automation** > **Dialogs** and select the task that you are working with. 

2. You can add the Agent Node just like any other node. You can find it in the main list of nodes. 

    <img src="../images/canvas-GenAI Node.png" alt="image_tooltip" title="image_tooltip" style="border: 1px solid gray; zoom:70%;">


## Configure Agent Node

### Component Properties

The component properties empower you to configure the following settings. The changes made within this section affect this node across all instances and dialog tasks.

It allows you to provide a **Name** and **Display Name** for the node. The node name cannot contain spaces.


<img src="../images/gennodecp1n.png" alt="Component Properties" title="Component Properties" style="border: 1px solid gray; zoom:70%;">


#### Model Configuration

Adjusting the settings allows you to fine-tune the model’s behavior to meet your needs. The default settings work fine for most cases. You can tweak the settings and find the right balance for your use case. A few settings are common in the features, and a few are feature-specific:


* **Model**: The selected model for which the settings are displayed.
* **Prompt/Instructions or Context**: Add feature/use case-specific instructions or context to guide the model.
* **Conversation History Length**: This setting allows you to specify the number of recent messages sent to the LLM as context. These messages include both user messages and virtual assistant (VA) messages. The default value is 10. This conversation history can be seen from the debug logs. 
**Note**: Applicable only if you are using a custom prompt. 
* **Temperature**: The setting controls the randomness of the model’s output. A higher temperature, like 0.8 or above, can result in unexpected, creative, and less relevant responses. On the other hand, a lower temperature, like 0.5 or below, makes the output more focused and relevant.
* **Max Tokens**: It indicates the total number of tokens used in the API call to the model. It affects the cost and the time taken to receive a response. A token can be as short as one character or as long as one word, depending on the text.
* **Fallback Behavior**: Fallback behavior lets the system determine the optimal course of action on LLM call failure or the Guardrails are violated. You can select fallback behavior as:
    * Trigger the Task Execution Failure Event
    * Skip the current node and jump to a particular node. The system skips the node and transitions to the node the user selects. By default, ‘End of Dialog’ is selected.


#### Pre-Processor Script


This property helps execute a script as the first step when the Agent Node is reached. Use the script to manipulate data and incorporate it into rules or exit scenarios as required. The Pre-processor Script has the same properties as the Script Node. [Learn more](../working-with-the-script-node/#configure-the-node){:target="_blank"}.

To define a pre-processor script, click **Define Script**, add the script you want to execute, and click **Save**. Enable **Auto Save** to save your work automatically after one second of inactivity. It must be re-enabled each time you open the editor.

<img src="../images/pre_prosessor.png" alt="Pre prosessor Script" title="Pre prosessor Script" style="border: 1px solid gray; zoom:70%;">


#### Entities

Specify the entities to be collected by LLM during runtime. In the Entities section, click **+ Add**, enter an **Entity Name,** and select the **Entity Type** from the drop-down list.

Most entity types are supported. Here are the exceptions: custom, composite, list of items (enumerated and lookup), and attachment. See [Entity Types](../../entity-types){:target="_blank"} for more information.

<img src="../images/entitiesv2.png" alt="image_tooltip" title="image_tooltip" style="border: 1px solid gray; zoom:70%;">

#### System Context

Add a brief description of the use case context to guide the model.

#### Tools

Tools allow the Agent Node to interact with external services, fetching or posting data as needed. When called, they let language models perform tasks or obtain information by executing actions linked to Script, Service, or Search AI nodes. Users can add a maximum of 5 tools to each node.

!!! note

    The Agent Node supports tool-calling with custom JavaScript prompts in non-streaming mode.

Click **+ Add** to open the **New Tool** creation window.  

<img src="../images/genai-node(18).png" alt="Tools" title="Tools" style="border: 1px solid gray; zoom:70%;">

Define the following details for tool configuration:

* **Name**: Add a meaningful name that helps the language model identify the tool to call during the conversation. 
* **Description**: Provide a detailed explanation of what the tool does to help the language model understand when to call it.
* **Parameters**:Specify the inputs the tool needs to collect from the user. Define up to 10 parameters for each tool and mark them as mandatory or optional.  
    * **Name**: Enter the parameter name.
    * **Description**: Enter an appropriate description of the parameter.
    * **Type**: Select the parameter type (String, Boolean, or Integer). 
* **Actions**: These are the nodes that the XO Platform executes when the language model requests a tool call with the required parameters. Users can add up to 5 actions for each tool. These actions are chained and executed sequentially, where the output of one action becomes the input for the next.
    * **Node Type**: Select the node type (Service Node, Script Node, Search AI Node) from the dropdown.
    * **Node Name**: Select a new or existing node from the dropdown.
* **Response Path**: The final output from the action nodes is required to be added as a Response Path for the Platform to understand where to look for the actual response in the payload. Choose the specific key or path that defines the output.
* **Choose transition**: Define the behavior after tool execution:
    * **Default**: Send the response back to the LLM. It is mandatory to have a Response Path in this case.
    * **Exit Node**: Follow the transitions defined for the Agent Node.
    * **Jump to a Node**: You can jump to any node defined in the dialog. 


**Jump to a Node Transition**

The Jump-to-Node transition option enables the creation of sophisticated dialog workflows. It allows for dynamic branching based on tool execution results, significantly streamlining the design of complex conversation flows.

**Key Updates**:

* Added "Jump-to-Node" transition option for tools within the Agent node.
* Enables seamless navigation to specified target nodes following tool execution.
* Maintains complete session-level conversation history across all transitions.
* Supports transitions to both orphan nodes and sub-dialogs.
* Ensures full backward compatibility with existing tool configurations.

#### Rules

Add the business rules that the collected entities should respect. In the rules section, click **+ Add**, then enter a short and to-the-point sentence, such as:

* _The airport name should include the IATA Airport Code;_
* _The passenger’s name should include the last name._

There is a 250-character limit to the Rules field, and you can add a maximum of 5 rules.

<img src="../images/rulesv2.png" alt="Rules" title="Rules" style="border: 1px solid gray; zoom:70%;">



#### Exit Scenarios

Specify the scenarios that should terminate entity collection and return to the dialog task. This means the node ends interaction with the generative AI model and returns to the dialog flow within the XO Platform.

Click **Add Scenario**, then enter short, clear, and to-the-point phrases that specifically tell the generative AI model when to exit and return to the dialog flow. For example, Exit when the user wants to book more than 5 tickets in a single booking and return `"max limit reached"`.

There is a 250-character limit to the Scenarios field, and you can add a maximum of 5 scenarios.

<img src="../images/exitv2.png" alt="Exit Scenarios" title="Exit Scenarios" style="border: 1px solid gray; zoom:70%;">

#### Post-Processor Script

This property initiates the post-processor script after processing every user input as part of the Agent Node. Use the script to manipulate the response captured in the context variables just before exiting the Agent Node for both the success and exit scenarios. The Post-processor Script has the same properties as the Script Node. [Learn more](../working-with-the-script-node/#configure-the-node){:target="_blank"}.

**Important Considerations**

If the Agent Node requires multiple user inputs, the post-processor is executed for every user input received.

To define a post-processor script, click **Define Script** and add the script you want to execute. 


### Instance Properties

Configure the instance-specific fields for this node. These apply only for this instance and will not affect this adaptive dialog node when used in other tasks. You must configure Instance Properties for each task where this node is used.

<img src="../images/instancev2.png" alt="Instance Properties" title="Instance Properties" style="border: 1px solid gray; zoom:70%;">


#### User Input

Define how user input validation occurs for this node:

* **Mandatory**: This entity is required and must be provided before proceeding.
* **Allowed Retries**: Configure the maximum number of times a user is prompted for a valid input. You can choose between 5-25 retries in 5-retries increments. The default value is 10 retries. 
* **Behavior on Exceeding Retries**: Define what happens when the user exceeds the allowed retries. You can choose to either _End the Dialog_ or _Transition to a Node_ – in which case you can select the node to transition to.


#### Auto Correct

Toggle enable/disable the Auto Correct for spelling and other common errors.


#### Advanced Controls

Configure advanced controls for this node instance as follows:

**Intent Detection**

This applies only to String and Description entities: Select one of these options to determine the course of action if the VA encounters an entity as a part of the user utterance:

* **Accept input as entity value and discard the detected intent**: The VA captures the user entry as a string or description and ignores the intent.
* **Prefer user input as intent and proceed with Hold & Resume settings**: The user input is considered for intent detection, and the VA proceeds according to the Hold & Resume settings.
* **Ask the user how to proceed**: Allow the user to specify if they meant intent or entity.

**Interruptions Behavior**

To define the interruption handling at this node. You can select from the below options:

* **Use the task level ‘Interruptions Behavior’ setting**: The VA refers to the **Interruptions Behavior** settings set at the dialog task level.
* **Customize for this node**: You can customize the **Interruptions Behavior** settings by selecting this option and configuring it. You can choose whether to allow interruptions or not, or to allow the end user to select the behavior. You can further customize Hold and Resume behavior. Read the [Interruption Handling and Context Switching](../../../intelligence/conversation-management/manage-interruptions.md){:target="_blank"} article for more information.

**Custom Tags**

Add Custom Meta Tags to the conversation flow to profile VA-user conversations and derive business-critical insights from usage and execution metrics. You can define tags to be attached to messages, users, and sessions.  See [Custom Meta Tags](../../../../../analytics/automation/custom-dashboard/custom-meta-tags){:target="_blank"} for details.

<img src="../images/instancev2.png" alt="Instance Properties" title="Instance Properties" style="border: 1px solid gray; zoom:70%;">


### Connections Properties

!!! note

    If the node is at the bottom of the sequence, then only the connection property is visible.

Define the transition conditions from this node. These conditions apply only to this instance and will not affect this node’s use in any other dialog. For a detailed setup guide, See [Adding IF-Else Conditions to Node Connections](../../node-connections/nodes-conditions){:target="_blank"} for a detailed setup guide.

The Connection Path property offers three default variants:

1. Not Connected - No specific next node is defined
2. End of Dialog - Explicitly ends the current dialog
3. Return to Flow - Terminates the Dialog Task and returns control to the Flow Builder. The Flow Builder resumes from the next node.
    * Enable the **Deflect to Chat** option to create conversation flows that transition from voice to chat-based interactions within the same context.
    It has two deflection types - ‘ Automation’ and ‘Agent Transfer’.  
    <img src="../images/deflect-to-chat1.png" alt="Deflect to Chat" title="Deflect to Chat" style="border:1px solid gray;zoom:70%;">


!!! Note

    Deflect to Chat works only with Kore Voice Gateway Channels (Phone number or SIP Transfer).

## Custom Prompt for Agent Node

Custom prompts are required to work with the Agent Node for tool-calling functionality. Platform users can create custom prompts using JavaScript to tailor the AI model's behavior and generate outputs aligned with their specific use case. By leveraging the Prompts and Requests Library, the users can access, modify, and reuse prompts across different Agent Nodes.
The custom prompt feature enables users to process the prompt and variables to generate a JSON object, which is then sent to the configured language model. Users can preview and validate the generated JSON object to ensure the desired structure is achieved.

Agent Node with custom prompt supports configuring pre and post-processor scripts at both node and prompt levels. This enables platform users to reuse the same custom prompt across multiple nodes while customizing the processing logic, input variables, and output keys for each specific use case. 

When you configure pre and post-processor scripts at both node and prompt levels, the execution order is: Node Pre-processor → Prompt Pre-processor → Prompt Execution → Prompt Post-processor → Node Post-processor.

!!! warning

    Configuring pre and post-processor scripts at both node and prompt levels may increase latency.

!!! note

    Node-level pre and post-processor scripts support [App Functions](../../../../app-settings/dev-tools/reusing-bot-functions-custom-script-file.md) in addition to content, context, and environment variables.



Let’s review a sample prompt written in Javascript and follow the step-by-step instructions to create a custom prompt. 

Sample JavaScript

```

let payloadFields = {
  model: "claude-3-5-sonnet-20241022",
  max_tokens: 8192,
  system:`${System_Context}.

                    ${Required_Entities && Required_Entities.length ?
                    `**Entities Required for the Use Case*: You are instructed to collect the from the List: ${Required_Entities}
                     **Entity Collection Rules**:
                        - Do not Prompt the user if the any of entities data is already captured or available in the context`: ''}
                    **Instructions To be Followed**:: ${Business_Rules}
                    **Tone and Language**::  
                       - Maintain a professional, helpful, and polite tone.  
                       - Support multiple languages if applicable to cater to diverse users.

                    **Output Format**::
                        - You Should Always STRICTLY respond in a **STRINGIFIED JSON format** to ensure compatibility with downstream systems.
                        - The response JSON must include the following keys:  
                          - "bot": A string containing either:
                            - A prompt to collect missing required information
                            - A final response
                          - "entities": An array of objects containing collected entities in format:
                            [
                              {
                                "key1": "value1",
                                "key2": "value2"
                              }
                            ]
                          - **conv_status**: String indicating conversation status:
                            - "ongoing": When conversation requires more information
                            - "ended": When one of these conditions is met:
                              - All required entities are collected
                              - All required functions/tools executed successfully
                              - Final response provided to user
                              - when one of the Scenarios Met from ${Exit_Scenarios}.`,
  messages: []
};

// Check if List_of_Tools exists and has length
if (Tools_Definition && Tools_Definition.length) {
  payloadFields.tools = Tools_Definition.map(tool_info => {
      return {
          name: tool_info.name,
          description: tool_info.description,
          input_schema: tool_info.parameters
      };
  });
}

// Map conversation history to context chat history
let contextChatHistory = [];
if (Conversation_History && Conversation_History.length) {
    contextChatHistory = Conversation_History.map(function(entry) {
      return {
          role: entry.role === "tool" ? "user" : entry.role,
          content: (typeof entry.content === "string") ? entry.content : entry.content.map(content => {
              if (content.type === "tool-call") {
                  return  {
                        "type": "tool_use",
                        "id": content.toolCallId,
                        "name": content.toolName,
                        "input": content.args
                    }
              }
              else {
                    return {
                        "type": "tool_result",
                        "tool_use_id": content.toolCallId,
                        "content": content.result
                    }
              }
          })
      };
    });
}
// Push context chat history into messages
payloadFields.messages.push(...contextChatHistory);

 Add user input to messages
 let lastMessage;
 if (contextChatHistory && contextChatHistory.length) {
     lastMessage = contextChatHistory[contextChatHistory.length-1];
 }

 if (!lastMessage || (lastMessage && lastMessage.role !== "tool")) {
     payloadFields.messages.push({
       role: "user",
      content: `${User_Input}`
     });
 }

// Assign payloadFields to context
context.payloadFields = payloadFields;



```

### Add Custom Prompt
The process involves creating a new prompt in the Prompts Library and writing the JavaScript code to generate the desired JSON object. Users can preview and test the prompt to ensure it generates the expected JSON object. Once the custom prompt is created, users can select it in the Agent Node configuration to leverage its functionality.


For more information on Custom Prompt, see [Prompts and Requests Library](../../../../generative-ai-tools/prompts-library.md).

To add an Agent node prompt using JavaScript, follow the steps:

1. Go to **Generative AI Tools** > **Prompts Library**.
2. On the top right corner of the **Prompts Library** section, click **+ New Prompt**.
3. Enter the **prompt name**. In the **feature** dropdown, select **Agent Node** and select the **model**. 
4. The Configuration section consists of End-point URLs, Authentication, and Header values required to connect to a large language model. These are auto-populated based on the input provided while model integration and are not editable. 
5. In the Request section, click **Start from Scratch**. [Learn more](#dynamic-variables).  
<img src="../images/toolcall1.png" alt="Start from Scratch" title="Start from Scratch" style="border: 1px solid gray; zoom:70%;">

6. Ensure the Stream Response is disabled, as the Agent Node supports tool-calling with custom JavaScript prompts in non-streaming mode.

7. Click **JavaScript**. The Switch Mode pop-up is displayed. Click **Continue**.  
<img src="../images/switch.png" alt="ISwitch Mode" title="Switch Mode" style="border: 1px solid gray; zoom:70%;">

    !!! note

        The Agent Node supports tool-calling with custom JavaScript prompts in non-streaming mode.
    
8. Enter the **JavaScript**. The Sample Context Values are displayed. To know more about context values, see [Dynamic Variables](#dynamic-variables).  
<img src="../images/toolcall2.png" alt="Script Preview" title="Script Preview" style="border: 1px solid gray; zoom:70%;">


9. Enter the Variable **Value** and click **Test**. This will convert the JavaScript to a JSON object and send it to the LLM.  
<img src="../images/values.png" alt="Script Preview" title="Script Preview" style="border: 1px solid gray; zoom:70%;">

    You can open a Preview pop-up to enter the variable value, test the payload, and view the JSON response.  
<img src="../images/valuepopup.png" alt="Preview pop-up" title="Preview pop-up" style="border: 1px solid gray; zoom:70%;">  
<img src="../images/jsonpreview.png" alt="JSON Preview" title="JSON Preview" style="border: 1px solid gray; zoom:70%;">

10. The LLM's response is displayed.  
<img src="../images/content-key.png" alt="Response" title="Response" style="border: 1px solid gray; zoom:70%;">

11. In the Actual Response section, double-click the **Key** that should be used to generate the text response path. For example, double-click the **Content** key and click **Save**.
12. Enter the **Exit Scenario Key-Value fields**, **Virtual Assistance Response Key**, and **Collected Entities**. The Exit Scenario Key-Value fields help identify when to end the interaction with the Agent model and return to the dialog flow. A Virtual Assistance Response Key is available in the response payload to display the VA’s response to the user. The Collected Entities is an object within the LLM response that contains the key-value of pairs of entities to be captured.  
<img src="../images/essentialkeys.png" alt="Essential keys" title="Essential keys" style="border: 1px solid gray; zoom:70%;">

13. Enter the **Tool Call Request key**. The tool-call request key in the LLM response payload enables the Platform to execute the tool-calling functionality.
14. Click **Test**. The Key Mapping pop-up appears.
    1. If all the key mapping is correct, close the pop-up and go to step 15.  
    <img src="../images/keymappingright.png" alt="Essential keys" title="Essential keys" style="border: 1px solid gray; zoom:70%;">

    2. If the key mapping, actual response, and expected response structures are mismatched, click **Configure** to write the post-processor script.  
    <img src="../images/key-map.png" alt="Essential keys" title="Essential keys" style="border: 1px solid gray; zoom:70%;">
    
        !!! note
            
            When you add the post-processor script, the system does not honor the text response and sets all child keys under the text and tool keys to match those in the post-processor script. 

        1. On the Post-Processor Script pop-up, enter the Post-Processor Script and click **Save & Test**. The response path keys are updated based on the post-processor script.  
        <img src="../images/postprocessor.png" alt="Post-Processor Script" title="Post-Processor Script" style="border: 1px solid gray; zoom:70%;">     
        2. The expected LLM response structure is displayed. If the LLM response is not aligned with the expected response structure, the runtime response might be affected. Click **Save**.

15. Click **Save**. The request is added and displayed in the **Prompts and Requests Library** section.  
<img src="../images/promptinlibrary.png" alt="Prompt Library" title="Prompt Library" style="border: 1px solid gray; zoom:70%;">

16. Go to the Agent Node in the dialog. Select the Model and Custom Prompt for the tooling calling.  
<img src="../images/selectprompt.png" alt="Custom Prompt" title="Custom Prompt" style="border: 1px solid gray; zoom:70%;">

    If the default prompt is selected, the system will display a warning that “Tools calling functionality requires custom prompts with streaming disabled.  
<img src="../images/errornote.png" alt="Custom Prompt" title="Custom Prompt" style="border: 1px solid gray; zoom:70%;">


### Expected Output Structure

Defines the standardized format required by the XO Platform to process LLM responses effectively.


<table border="1">
  <thead>
    <tr>
      <th>Format Type</th>
      <th>Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Text Response Format</td>
      <td>
        <pre>
{
  "bot": "Sure, I can help you with that. Can I have your name please?",
  "analysis": "Initiating appointment scheduling.",
  "entities": [],
  "conv_status": "ongoing"
}
        </pre>
      </td>
    </tr>
    <tr>
      <td>Conversation Status Format</td>
      <td>
        <pre>
{
  "bot": "Sure, I can help you with that. Can I have your name please?",
  "analysis": "Initiating appointment scheduling.",
  "entities": [],
  {=="conv_status": "ongoing"==}
}
        </pre>
      </td>
    </tr>
    <tr>
      <td>Virtual Assistant Response Format</td>
      <td>
        <pre>
{
  {=="bot": "Sure, I can help you with that. Can I have your name please?"==},
  "analysis": "Initiating appointment scheduling.",
  "entities": [],
  "conv_status": "ongoing"
}
        </pre>
      </td>
    </tr>
    <tr>
      <td>Collected Entities Format</td>
      <td>
        <pre>
{
  "bot": "Sure, I can help you with that. Can I have your name please?",
  "analysis": "Initiating appointment scheduling.",
  {== "entities": []==},
  "conv_status": "ongoing"
}
        </pre>
      </td>
    </tr>
    <tr>
      <td>Tool Response Format</td>
      <td>
        <pre>
{
  "toolCallId": "call_q5yiBbnXPhEPqkpzsLv2isho",
  "toolName": "get_delivery_date",
  "result": {
    "delivery_date": "2024-11-20"
  }
}
        </pre>
      </td>
    </tr>
    <tr>
      <td>Post-Processor Script Format</td>
      <td>
        <pre>
{
  "bot": "I'll help you check the delivery date for order ID 123.",
  "entities": [{"order_id": "123"}],
  "conv_status": "ongoing",
  "tools": [
    {
      "toolCallId": "toolu_016FWtdANisgqDLu3SjhAXJV",
      "toolName": "get_delivery_date",
      "args": { "order_id": "123" }
    }
  ]
}
      </pre>
      </td>
    </tr>
  </tbody>
</table>





### Context Object

The context object is used to get the entities and the parameters of tools.


<table>
  <tr>
   <td>Entities
   </td>
   <td>{context.AI_Assisted_Dialogs.GenAINodeName.entities[x].{entityName}}
   </td>
  </tr>
  <tr>
   <td>Parameters
   </td>
   <td>{context.AI_Assisted_Dialogs.GenAINodeName.active_tool_args.{parameterName}}
   </td>
   <tr>
   <td>Bot Response Path
   </td>
   <td>{{context.AI_Assisted_Dialogs.bot_response.bot}}
   </td>
  </tr>
</table>


### Dynamic Variables

The Dynamic Variables like Context, Environment, and Content variables can now be used in pre-processor scripts, post-processor scripts, and custom prompts.

[Learn more](../../../../app-settings/variables/using-bot-variables.md).

<table>
  <tr>
   <td>
Keys
   </td>
   <td>Description
   </td>
  </tr>
  <tr>
   <td>{{User_Input}}
   </td>
   <td>The latest input by the end-user.
   </td>
  </tr>
  <tr>
   <td>{{Model}} Optional
   </td>
   <td>This specifies the LLM tagged to the Agent Node in the Dialog Task.
   </td>
  </tr>
  <tr>
   <td>{{System_Context}} Optional
   </td>
   <td>This contains the initial instructions provided in the Agent Node that guide how the LLM should respond.
   </td>
  </tr>
  <tr>
   <td>{{Language}} Optional
   </td>
   <td>The language in which the LLM will respond to the users
   </td>
  </tr>
  <tr>
   <td>{{Business_Rules}} Optional
   </td>
   <td>Rules mentioned in the Agent Node are used to understand the user input and identify the required entity values.
   </td>
  </tr>
  <tr>
   <td>{{Exit_Scenarios}} Optional
   </td>
   <td>Scenarios mentioned in the Agent Node should terminate entity collection and transition to the next node based on Connection Rules.
   </td>
  </tr>
  <tr>
   <td>{{Conversation_History_String}} Optional
   </td>
   <td>This contains the messages exchanged between the end-user and the virtual assistant. It can used only in the JSON prompt.
   </td>
  </tr>
  <tr>
   <td>{{Conversation_History_Length}} Optional
   </td>
   <td>This contains a maximum number of messages that the conversation history variable can hold.
   </td>
  </tr>
  <tr>
   <td>{{Required_Entities}} Optional
   </td>
   <td>This contains the list of entities (comma-separated values) mentioned in the Agent Node to be captured by the LLM.
   </td>
  </tr>
  <tr>
   <td>{{Conversation_History}} Optional
   </td>
   <td>Past messages in the conversation are exchanged between the end-user and the virtual assistant. This is an array of objects with role and content as keys. It can used only in the JavaScript prompt
   </td>
  </tr>
  <tr>
   <td>{{Collected_Entities}} Optional
   </td>
   <td>List of entities and their values collected by the LLM. This is an object with an entity name as the key and the value as LLM collected value.
   </td>
  </tr>
  <tr>
   <td>{{Tools_Definition}} Optional
   </td>
   <td>List of tools that will enable the language model to retrieve data, perform calculations, interact with APIs, or execute custom code.
   </td>
  </tr>
</table>


## Tool Calling in Debug Logs

The debug logs capture the entire execution flow, including the conversation history array and the tools being called. The conversation history array tracks the interaction between the user and the assistant, while the tool calls (`FundsTransfer`, `PayeesAvailableCheck`) represent the specific actions or functions invoked by the assistant to fulfill the user's request.

By examining the debug logs, users can trace the steps taken by the assistant, understand how it processes the user's input, and see how it interacts with different tools to complete the requested task. The logs provide crucial visibility into the underlying execution and are invaluable for debugging, monitoring, and gaining a deeper understanding of the assistant's behavior.

The debug logs on the left side of the screenshot below provide a comprehensive view of the execution flow and the interactions between the user, the assistant (Finance Buddy), and the underlying system. This detailed view ensures that you are fully informed about the process.

<img src="../images/tooldebug.png" alt="Essential keys" title="Essential keys" style="border: 1px solid gray; zoom:70%;">

Here's a step-by-step explanation of the execution captured in the debug logs:

1. The user initiates the conversation with Finance Buddy, requesting to transfer funds to the user.
2. Finance Buddy responds, asking how it can help the user.
3. The user expresses their intent to transfer funds to a person.
4. The Agent Node is initiated (`Agent node initiated`).
5. The Agent Node Request Response Details are captured in JSON format and contain the conversation history up to this point.
6. The tool execution (`FundsTransfer`) is initiated. This indicates that the assistant has determined that the tool needs to be called based on the user's request.
7. The assistant checks if the person (Raj Kumar) is already registered as a payee in the user's account. To verify this, it calls the `PayeesAvailableCheck` tool.
8. The `PayeesAvailableCheck` tool completes execution, and the result is captured in the debug logs. The assistant determines that the person is registered as a payee.
9. The assistant informs the user that the person is registered as a payee and requests additional details to proceed with the fund transfer. It asks the user to select the transfer type (NEFT/IMPS/RTGS), provide the transfer amount, and confirm their account ID.
10. The user provides the requested information.
11. The assistant calls the `FundsTransfer` tool with the provided details to initiate the fund transfer.
12. The `FundsTransfer` tool completes execution, and the Agent Node captures the updated conversation history array in the request-response details.
13. The XO Platform exits the Agent node.