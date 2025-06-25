# Agent AI Updates

This document provides information on the feature updates and enhancements introduced in **Agent AI** of XO v11.x releases.

## v11.11.1 March 15, 2025

<u>Patch Release</u>

This update includes only bug fixes.

<hr>

## v11.11.0 March 4, 2025

<u>Minor Release</u>

### Widget Enhancements

#### More Accurate Intent Extraction from Landing Summary

This update has introduced a service node and a new tag-based approach to generate the landing summary (a concise summary) of the conversation. This summary is used internally to improve intent identification accuracy. It is generated after the Welcome Dialog task ends and is not visible to agents. However, the detailed summary from the message node continues to be visible to the agents. [Learn more:octicons-arrow-right-24:](./../../agentai/agent-experience/faq/agentai-faq.md).

#### Search AI Timeout Configuration and Runtime Error

The Search tab in the Agent AI widget now displays a timeout error message for searches exceeding 10 seconds. [Learn more:octicons-arrow-right-24:](./../../agentai/agent-experience/agent-assist-widget-v3.md/#timeout-and-server-errors)

#### API Call Notification for Dialog Tasks

Agents now receive notifications when a dialog task makes an API call, indicating a waiting period. The notification disappears once a response is received. While the waiting message is displayed, agents can close the dialog task.

#### Automatic Upgrade from Agent AI V2 to V3

The legacy Agent AI V2 is automatically upgraded to the enhanced and backward-compatible V3, which offers improved functionality and continued compatibility with previous configurations.

### UI Enhancement

#### Introducing the Dialog Task Layout feature

To enhance the management and customization of dialog tasks within the widget, Kore has introduced the **Dialog Task Layout** subsection under the **Widget Theming** section. The key features of this update are:

* **Dialog Task Search**: Easily search for dialog task names, like searching a word within a web page.
* **Dialog Task Grouping**: Group dialog tasks to better organize them.
* **Dialog Task Sorting**: Sort dialog tasks in alphabetical order for better accessibility.

!!! note

    Dialog tasks not added to a group don’t appear at runtime. 
[Learn more:octicons-arrow-right-24:](./../../agentai/configuration/widget-theming-layout-customization.md/#dialog-task-layout)

#### Interactive Language (App Language) option for Widget

Kore has included a new option, **Interactive Language**, in the **Default Language for Agent AI Widget** drop-down list. Selecting this option adjusts the widget's localized text language to match the app's language. [Learn more:octicons-arrow-right-24:](./../../agentai/configuration/widget-settings.md/#steps-to-set-agent-ai-general-settings) 

### Integrations

#### Support for associating a Single Bot with Multiple Queues in Genesys Cloud CX

To streamline bot management, improve efficiency, and reduce maintenance cost, Kore now provides the ability to associate a single bot with multiple Genesys Cloud CX queues.

#### Agent AI Voice integration with CX Cloud from Genesys and Salesforce

Kore Agent AI is now integrated with CX Cloud from Genesys and Salesforce.

#### Agent AI Voice Integration with Salesforce Voice

Agent AI Voice is now integrated with Salesforce default telephony, Amazon Connect.

<hr>

## v11.10.0 February 12, 2025

<u>Minor Release</u>

### UI Enhancements

#### Language Dropdown Automatically Adjusts to the App's Language

The language dropdown in Welcome Events, Widget Settings, and Feedback Settings now automatically adjusts to match the app's language.

### Widget Enhancements

#### Load Time Reduction of Agent AI Widget

The Agent AI widget’s load time has been optimized by removing synchronous API calls for settings and preferences before establishing the socket connection. These configurations are now received asynchronously using a socket event, significantly improving initial load performance.

#### Ability to Pause or Resume Transcription

Agent AI widget is now capable of honoring the pause and resume events transmitted from agent desktops to control the visibility of transcripts to agents within the Widget. [Learn more:octicons-arrow-right-24:](./../../agentai/agent-experience/agent-assist-widget-v3.md)

#### Enhanced Input Box for Override, List View, Restart, and Search Bar fields

For improved navigation of longer entries, input text boxes of Override, List View, Restart, and Search Bar are now expanded to display up to three lines with a scroll bar.

#### On-demand Summary Generation

Agents can now generate on-demand conversation summaries at any point during a conversation, up to 2 times per agent per conversation. This functionality is available even during agent transfers, allowing the receiving agent to regenerate a new summary and view the previous summary with timestamps. [Learn more:octicons-arrow-right-24:](./../../agentai/agent-experience/agent-assist-widget-v3.md#generate-summary)

### Integrations

#### Enhanced Genesys Middleware to Support Base64 Encoded Value

Genesys Middleware has been enhanced to support Base64-encoded values when passing the *x_passthru_metadata* parameter to Agent AI. This enhancement resolves the issues with SSO token decryption. [Learn more:octicons-arrow-right-24:](./../../agentai/integration/genesys/manual-integration-of-agent-ai-voice-with-genesys-cloud.md)

#### Enhanced Salesforce Package includes Language Parameter

The Salesforce package now includes a language parameter to support AgentAssist's multi-language capability. During installation, users select a language that sets the *interactive_language* parameter (e.g., interactive_language=Spanish), which is sent to AgentAssist to conduct all interactions (for example, welcome messages, task running, sentiment analysis) in the selected language. [Learn more:octicons-arrow-right-24:](https://docs.kore.ai/xo/agentai/integration/salesforce-nice-cx-cti/kore-agent-ai-with-salesforce-nice-cx-cti/#set-up-agentassist-configuration)

#### Multi-bot Support for Agent AI Integration with ServiceNow

Multiple bots can be mapped to a queue, region, or other defined criteria within a workspace, enabling agents to manage cases across bots without manual intervention or limitations. [Learn more:octicons-arrow-right-24:](./../../agentai/integration/servicenow/chat-integration-with-servicenow.md/#multibot-solution-with-servicenow)

<hr>

## v11.9.1 January 25, 2025

<u>Patch Release</u>

This update includes bug fixes.

<hr>

## v11.9.0 January 05, 2025

<u>Minor Release</u>

This update includes enhancement and bug fixes. The key enhancement included in this release is summarized below.

### Search AI Configuration

#### Inbuilt and External Search AI App

This update introduced flexible Search AI configuration to choose built-in functionality or custom Search AI apps:

* None: No Search AI functionality.
* Use Search AI Configurations from the current app: Uses the in-built Search AI app that comes with the current XO11 app.
* Link Search AI Configurations from a different app: Users can configure up to three customized Search AI apps.

### Widget Settings

#### Auto-corrections for the Search tab

The new auto-correct feature for the Search tab allows admins to control spelling corrections through Widget Settings, including custom dictionary management. While admins can enable/disable it globally, agents can toggle it individually in Settings, with agent preferences taking priority. [Learn more :octicons-arrow-right-24:](../../agentai/configuration/widget-settings.md#auto-corrections-for-the-search-tab)

#### Enhanced Dialog Task Entity Extraction

The Proactive Mode toggle has been enhanced to include the “Automatic Dialog Task Entity Extraction” option. This option automatically extracts entities from user messages during dialog task execution. [Learn more :octicons-arrow-right-24:](../../agentai/configuration/widget-settings.md#agent-ai-channel-specific-settings)

### Integration

#### ServiceNow Chat Integration

Agent AI is now integrated with ServiceNow Chat. [Learn more :octicons-arrow-right-24:](../../agentai/integration/servicenow/chat-integration-with-servicenow.md){:target="_blank"}

<hr>

## v11.8.1 December 19, 2024

<u> Patch Release </u>

This update includes minor enhancements and bug fixes. Key enhancements included in this release are summarized below.

### Multi-lingual Support
The Agent AI integration with ServiceNow now supports multiple languages. Agents can interact with the widget, Welcome Events, and bots in their preferred language.

<hr>

## v11.8.0 December 11, 2024

<u> Minor Release </u>

This update includes enhancements and bug fixes. Key enhancements included in this release are summarized below.

### Widget Enhancements

#### Auto-Scroll for Transcript Tab
The Transcript tab is now updated with the "auto-scroll" functionality, wherein the system automatically navigates to the last message for new utterances. Agents can manually scroll up and down to read through the content.  
<img src="../images/auto-scroll-transcript-tab.png" alt="auto-scroll-transcript-tab" title="auto-scroll-transcript-tab" style="border: 1px solid gray; zoom:80%;">

#### Enhanced Language Support for Localization
The Greeting Messages, Widget Content, Layout Customization, and Negative Feedback Reasons now support the following additional languages:

* HT - Haitian Creole
* TL - Tagalog
* FI - Finnish
* UK - Ukrainian
* SV - Swedish
* CA - Catalan
* AZ - Azerbaijani
* DA - Danish
* MS - Malay
* MY - Myanmar (Burmese)
* TH - Thai
* PT_PT - Portuguese (European)

#### Clickable Spyglass icon on the Search bar

The **Spyglass** icon on the Agent AI widget’s **Search** bar is now clickable. Users can search by pressing the **Enter** key or clicking the **Spyglass** icon.  
<img src="../images/spy-glass-icon-search-tab.png" alt="spy-glass-icon" title="spy-glass-icon" style="border: 1px solid gray; zoom:80%;">

#### Run Dialog Task Enhancement
In the Agent AI widget, Dialog Tasks now display the **Run with Agent Input** button as an icon next to the Run button. Agents can click this icon to customize the Dialog Task content and decide whether to send the dialog.

#### Rate Limit on Socket Connections from Agent AI
To prevent system overload, crashes, or slowdowns and ensure optimal performance, Kore.ai has implemented a rate limit on sockets. The rate limit on sockets are:

* Message Limit: This limit is 500 messages per socket per minute. If exceeded, a 1-minute cooldown will be activated, during which no messages can be sent. A rate_limit event will notify users of the retry time.
* Conversation Limit: Each conversation is limited to 10 parallel socket connections. If this limit is surpassed, additional connections are disconnected until one of the existing connections is closed.
* Agent Conversation Socket Limit: No specific limit on socket connections per agent exists.

#### Summarization Support for Japanese
The Agent AI widget now supports conversation summarization in Japanese.

### Integration Enhancements

#### Genesys Agent AI integration with Genesys Desktop Application
The Genesys Agent AI solution (Agent AI widget) now works with the Genesys Desktop Application. [Learn more :octicons-arrow-right-24:](https://docs.kore.ai/agentassist/integration/agent-ai-integration-with-genesys-cloud-cx/){:target="_blank"}.

#### Enhanced Language Support for NICE MAX Desktop
The Agent AI integration with NICE MAX Desktop now supports multiple languages, allowing agents to interact with the Agent AI widget in their preferred language.

#### Support for passing Custom Data
Agent AI integration with NICE CTI on Salesforce allows agents to pass custom data (such as name and department) into the Agent AI widget via the NICE CTI scripts. This integration enhances personalization and context-awareness in customer interactions, improving customer satisfaction and operational efficiency.

#### Security Enhancement to Prevent Agent Impersonation
Kore.ai has implemented a security enhancement for the Agent AI widget to prevent data breaches and unauthorized actions. The widget’s URL, which previously accepted a modifiable **conversationID** query parameter, now prevents the impersonation of legitimate agents. This update mitigates the risk of unauthorized access via **JWT token** misuse and **iframe link** inspection.

#### AgentAssist Chat Integration with ServiceNow
AgentAssist is now integrated with ServiceNow, allowing agents to access the features for a seamless chat experience within the ServiceNow environment.

### API Enhancements

#### Raw Data API Enhancements
The Raw Data API is updated to include the following:

* Queue Details: This parameter, “queueInfo,” contains the “queueId” and “queueName” information.
* Scroll Up and Scroll Down counts: The “countScrollUp” and “countScrollDn” parameters show the number of times an agent clicks the “up” and “down” arrows to scroll up or down in the widget.
* Links Clicked / Redirects: The “linksClicked” parameter shows the URL and the timestamp when a link was clicked.

#### Chat History API Includes Agent Messages
The Chat or [Conversation Details and Summary API](https://developer.kore.ai/docs/bots/api-guide/conversation-details-summary-api/){:target="_blank"} now includes Agent messages to help generate the complete conversation summary for those who use the Chat History API to access conversations.

### UI Enhancement

#### Enhanced Language Support for XO v11
For localization, the XO v11 App now supports Japanese and Korean languages.

<hr>

## v11.7.1 November 18, 2024

<u> Patch Release </u>

This update includes minor enhancements and bug fixes. Key enhancements included in this release are summarized below.

### Widget Enhancement
#### Agent AI for Outbound Calls

Agent AI is now available for both inbound and outbound calls.

### Integration Enhancement
#### Default Kore Agent AI Interaction Widget for Genesys

To streamline call handling and improve efficiency, the Agent AI widget now supports Genesys' default pop-up window. The widget automatically opens upon receiving a call or message.

<hr>

## v11.7.0 November 3, 2024

<u> Minor Release </u>

This update includes enhancements and bug fixes. Key enhancements included in this release are summarized below.

### Widget Enhancements

#### Extended Language Support for Localization

The Greeting Messages, Widget Content, Layout Customization, and Negative Feedback Reasons now support the following additional languages:

* HE - Hebrew
* ZH_TW - Traditional Chinese
* PT - Portuguese (Brazil)
* ID - Indonesian
* RU - Russian
* TR - Turkish
* VI - Vietnamese
* PL - Polish
* FA - Persian
* UR - Urdu

#### Enhanced Access Control for Search AI

Agent AI now allows restricted access for targeted users by configuring up to three Search AI apps with the following scopes: 

* Internal Answers: Access to internal sources only.
* External Answers: Access to external sources only.
* Auto-Suggestions: Access to auto-suggestions (prompts) only.

**Configuration rules**:

* Choose either Internal Answers or External Answers with Auto-Suggestions.
* Internal and External Answers cannot be combined in one app.
* Auto-Suggestions can be configured for only one Search AI app.
* Knowledge AI settings are available only when selecting either Internal or External Answers.

#### Decommissioning of Agent AI Widget v2

The widget v2 will be decommissioned by the end of November 2024. A banner has been added in the Voice and Chat channels to notify users that Agent AI widget v2 will be decommissioned. Please upgrade to v3 for continued support.

### Integration Enhancements

#### Summary Support for NICE MAX Desktop

Agents using NICE MAX Desktop now receive a concise summary at the end of a chat or voice session. This summary highlights key points and identifies action items, allowing agents to review important information quickly. [Learn more :octicons-arrow-right-24:](../../agentai/integration/nice-max/nice-max-desktop-chat-and-voice.md){:target="_blank"}.

#### Multibot Support for Agent AI Voice in Genesys

Previously limited to a single bot and a department-specific approach, the solution has now been upgraded to support multiple bots and a queue-based functionality. This enhancement enables Genesys Cloud CX to offer a more flexible and scalable solution for businesses seeking to leverage AI to improve agent efficiency and customer satisfaction across multiple departments.

<hr>

## v11.6.1 October 21, 2024

<u> Patch Release </u>
This update includes enhancements and bug fixes. Key enhancements included in this release are summarized below.

### Enhanced NICE MAX Desktop Integration

The Agent AI integration with NICE CX MAX Desktop now supports passing custom data to the Agent AI Widget and is compatible with XO v11. [Learn more :octicons-arrow-right-24:](../../agentai/integration/nice-max/nice-max-desktop-chat-and-voice.md){:target="_blank"}

### Enhanced Salesforce-NICE CTI Integration

The Agent AI integration with Salesforce-NICE CTI now supports all Agent AI features, including automation, transcription, intent identification, Agent Coaching, Agent Playbooks, Sentiment Analysis, and end-of-call summaries. This results in improved personalization and operational efficiency.

<hr>

## v11.6.0 September 28, 2024
<u> Minor Release </u>

This update includes enhancements and bug fixes. Key enhancements included in this release are summarized below.

### “Thumbs-down”/Negative Feedback Reasons Comment Box Updated

The placeholder text in the comment box is now labeled “Tell us more…” instead of “Add additional comments here.”  
<img src="../images/negative-feedback-reason-comment-box.png" alt="negative-feedback-reason-comment-box" title="negative-feedback-reason-comment-box" style="border: 1px solid gray; zoom:80%;">

### Summarization in Spanish

For Spanish conversations, auto-summarization is now available in the Spanish language.

### Error Message Configuration

The error message display pattern in the Agent AI widget has been updated to help agents view and understand issues without unnecessary redundancy.

You can configure error messages during [Use Case creation](https://docs.kore.ai/agentassist/use-cases/dialogues-creation/){:target="_blank"} at the bot level. These messages are displayed in the Agent AI widget for invalid user input. The runtime display varies based on whether a single or multiple error messages are triggered.

**Single Error Message**

When a single error message is triggered during dialog task execution, the **Assist** tab displays the error message and the number of occurrences. If the same error message is triggered again, the message does not repeat, but the number of occurrences increases.  
<img src="../images/single-error-message.png" alt="single-error-message" title="single-error-message" style="border: 1px solid gray; zoom:80%;">

**Multiple Error MessageS**

When multiple (different) error messages are triggered, they are all displayed in the **Assist** tab, with a count indicating the total number of error messages.  
<img src="../images/multiple-error-messages.png" alt="multiple-error-messages" title="multiple-error-messages" style="border: 1px solid gray; zoom:80%;">

### Enhanced Raw Data API

The [Raw Data API](https://docs.kore.ai/agentassist/api/raw-data-api-v2/){:target="_blank"} is enhanced to retrieve and store summary feedback, reasons, and comments.

<hr>

## v11.5.1 September 14, 2024
<u> Patch Release </u>

This update includes bug fixes.

<hr>

## v11.5.0 September 01, 2024
<u> Patch Release </u>

This update includes enhancements and bug fixes. Key enhancements included in this release are summarized below.

### Agent AI Conversation Logs

This update introduces a comprehensive Conversation Logs feature for reviewing past agent-customer interactions. It provides a powerful tool for managers and quality assurance teams to review, analyze, and improve agent-customer interactions over time.

[Learn more :octicons-arrow-right-24:](../../analytics/contact-center/agentai-conversation-logs.md){:target="_blank"}

Key updates:

* **Detailed Interaction Records**: Date and time of conversations, Channel used, and Duration of interaction.

* **Conversation Content**: Auto-generated summaries, Edited summaries (if any), and Original conversation transcripts.

* **Flexible Filtering Options**: Today, Yesterday, Past 7 days, Past 28 days, Past 90 days, and Custom date range.

### Expandable and Collapsible Table Templates in the Widget

This update allows agents to manage their workspace more efficiently by controlling the display of table templates, leading to a more organized and personalized view of information.

Key updates:

* **Expand/Collapse Functionality**: Icons added to toggle table view.
* **Default View**: Tables appear expanded by default.
* **User Control**: Agents can adjust table visibility as needed.  
<img src="../images/expandable-collapsible-content.png" alt="expandable-collapsible-content" title="expandable-collapsible-content" style="border: 1px solid gray; zoom:80%;">

### Enabling Server-Side Triggering of Conversation Summary in Agent AI

Third-party applications can now trigger a conversation summary by sending the “agentAssist.endOfConversation” event to Agent AI with the help of a new API.

[Learn more :octicons-arrow-right-24:](../../apis/agent-ai/conversation-summary-trigger-api.md){:target="_blank"}

### Introduction of Additional languages for Agent AI

For localization, feedback, and greetings, Agent AI now supports 33 languages, including Indian, Dutch, and other major languages. It significantly broadens Agent AI’s accessibility and user-friendliness across different linguistic markets, enabling more effective communication and interaction with a global user base.

Key updates:

* **Expanded Language Options**: Added Indian, Dutch, and other major languages, a total of 33 supported languages.
* **Comprehensive Integration**: Widget Settings, Feedback Settings, and Widget Theming.
* **Specific Application Areas**: Auto Summarization, Default Widget Language, Various Feedback Types (Dialog Task, Answers, FAQ, Summary), and Widget Personalization Settings.

<hr>

## v11.4.1 August 11, 2024
<u> Patch Release </u>

This update includes feature enhancements and bug fixes. Key features and enhancements included in this release are summarized below.

### Widget Landing Tab

The location of the Widget Landing Tab settings is changed in this update:

* Old location: Widget Settings > Agent AI Channel Specific Settings. 
* New location: Widget Theming > Layout Customization > Widget Menu Layout.

This change consolidates widget customization options, making it easier for users to configure the landing tab along with other layout settings.

### OAuth Credential Update for Genesys

The **Authorized Redirect URI** in the Genesys Middleman App is updated to ensure seamless integration of Agent AI with XO v11:

* Previous URI: https://agentassist.kore.ai/koreaiaa-genesys/
* New URI: https://platform.kore.ai/koreaiaa-genesys/

<hr>

## v11.4 July 27, 2024
<u> Patch Release </u>

This update includes feature enhancements and bug fixes. Key features and enhancements included in this release are summarized below.

### Search AI Configuration Moved from Account to Bot Level

The Search AI Configuration data is now saved at the bot level instead of the account level.

### Enhanced Scroll Functionality in the Widget

In the Agent AI widget, the **Assist** and the **My Bot** tabs now contain “up” and “down” arrow buttons at the top and the bottom to let you scroll to the first and last messages. These buttons appear after the messages in the **Assist** tab are large enough to require a scroll bar.  
<img src="../images/enhanced-scroll-functionality-1.png" alt="enhanced-scroll-functionality" title="enhanced-scroll-functionality" style="border: 1px solid gray; zoom:80%;">

### Agent AI Enabled Dialog Tasks for Playbook Step Adherence and Triggers

To improve the usability and relevance of the Playbooks module, Agent AI now restricts the selection of dialog tasks specified only for the Playbook’s designated channel. This dialog task selection applies during trigger point creation for Dynamic Playbooks and Step Adherence within Primary Playbooks.  
<img src="../images/agent-ai-enabled-dialog-tasks-2.png" alt="agent-ai-enabled-dialog-tasks" title="agent-ai-enabled-dialog-tasks" style="border: 1px solid gray; zoom:80%;">

### Feedback Reason and Comment on Summarization

The Agent AI widget's Summary feature now offers enhanced feedback capabilities for auto-generated summaries. Agents can provide more specific and actionable feedback by selecting a reason from up to five customizable messages and adding optional comments. Administrators can edit these messages, turn the comment box on or off, and choose the feedback language. This improved feedback system allows agents to pinpoint issues with summaries more accurately, contributing to the continuous improvement of the auto-summarization feature's accuracy and relevance over time. [Learn More :octicons-arrow-right-24:](../../agentai/configuration/feedback-settings.md){:target="_blank"} 
<img src="../images/feedback-reason-3.png" alt="feedback-reason" title="feedback-reason" style="border: 1px solid gray; zoom:80%;">

### Language-specific Summarization

The Agent AI widget now supports language-specific summarization for third-party agent desktops. Admins can customize the language of automatically generated conversation summaries by selecting the **Custom Dialog Task** option in the **Auto Summarization Model** section. After choosing a preferred language, the system displays a configured dialog task for that language. The summary is then generated based on this language-specific task, allowing for more accurate and culturally appropriate summaries across different languages.  
<img src="../images/language-specific-summarization-4.png" alt="language-specific-summarization" title="language-specific-summarization" style="border: 1px solid gray; zoom:80%;">

### View Summary from Any Active Tab

The Agent AI widget now displays summaries more flexibly across all active tabs. When an agent closes a conversation, the summary appears on whichever tab they're currently viewing, not just the Assist tab. This change supports the widget's customizable layout feature, allowing agents to see summaries even if they've rearranged or removed certain tabs. For example, a summary can now pop up on the Search tab, enhancing the widget's versatility and ensuring agents always have access to important conversation summaries regardless of their current view.

### Widget Layout Customization (Beta)

The Agent AI widget now offers channel-specific layout customization in beta. Users can adjust language settings, menu labels, visibility controls for messages, dialog task timelines, and assist message types. The feature also allows customization of widget menu layout, assist action menu, landing tab settings, and "More" menu behavior. This flexibility enables tailoring the widget to specific channel needs and preferences. While the preview function is still in beta and may not fully reflect the final widget experience, it provides a close reference for customization options. [Learn More :octicons-arrow-right-24:](../../agentai/configuration/widget-theming-layout-customization.md){:target="_blank"}  
<img src="../images/widget-layout-customization-5.png" alt="widget-layout-customization" title="widget-layout-customization" style="border: 1px solid gray; zoom:80%;">

### Entry/Exit Event Support in Third-Party Integration

Integration with third-party applications lets Agent AI capture and process events like entry, exit, and internalTransfer between agents to ensure smooth transition and improved user experience. Currently, these events are only supported by Genesys. 

<hr>

## v11.3.1 July 13, 2024

<u> Patch Release </u>

This update includes bug fixes.

<hr>

## v11.3.0 June 29, 2024

<u>Patch Release</u>

This update includes feature enhancements and bug fixes. Key features and enhancements included in this release are summarized below.

### Summarization Service Optimization

The Conversation Summary generation process has been updated to handle short, long, and abrupt endings of conversations. For long conversations, the maximum limit is set to 8000 tokens (approximately 6000 words).

### Improved Widget Search Experience

The widget search bar has been improved for a better user experience. It now shows "Ask a question" as placeholder text with a search icon on the right. As users type in the bar, the placeholder disappears, and the search icon changes to a close (X) icon, which makes it easy to clear the text.

### Dashboard Updates

Agent AI dashboard is enhanced with new suggestion relevance metrics and reorganized customer inquiry insights.

* A new **Relevant Suggestions** tab is added, showing the percentage of suggestions used by agents.
* The **What are your customers looking for** section is revised:
    * "Articles" is renamed to "Answers", displaying SearchAssist results.
    * A new "Others" tab is added for web suggestions and additional data sources.

<img src="../images/updated-dashboard.png" alt="updated-dashboard" title="updated-dashboard" style="border: 1px solid gray; zoom:80%;">

### Attachment Support in Widget

Agent AI now accepts file or image attachments during live conversations. 

If the file or image is not automatically detected, you can override and manually attach the file. To maintain system efficiency, attachments are limited to one file at a time and must not exceed 25 MB in size.

### Dark Theme for Agent AI Widget

Agents can now customize the widget appearance by selecting a theme. To select it, go to the widget’s **Settings** section and select **Dark** or **Light**.

### In-line Digital Form

Agent AI has introduced in-line digital forms in the **Assist** tab, making it easier to collect customer information during live conversations. Configure the forms with dialog tasks to use this feature and select "Open inline form" in the **Web/Mobile SDK Form Behavior** setting.

<img src="../images/inline-digital-form.png" alt="inline-digital-form" title="inline-digital-form" style="border: 1px solid gray; zoom:80%;">

**In-line form**:

<img src="../images/inline-form.png" alt="inline-form" title="inline-form" style="border: 1px solid gray; zoom:80%;">

### Streamlined Conversation Summary Management

Conversation Summary management has been improved to enhance usability and tracking.

* When agents submit a summary, it's automatically saved and linked to its **Conversation ID**, making it easily accessible in the **Conversation Logs** screen.  
<img src="../images/conversation-logs.png" alt="conversation-logs" title="conversation-logs" style="border: 1px solid gray; zoom:80%;">

* For easy identification and comparison, the modified Conversation Summary before submission is marked as “Edited Summary” with an “eye” icon to view the original summary.  
<img src="../images/edited-summary.png" alt="edited-summary" title="edited-summary" style="border: 1px solid gray; zoom:80%;">

* Each displayed Conversation Summary indicates whether it has been modified.
* If summary generation fails, the following message is displayed to inform the user: "Error occurred while generating summary".  
<img src="../images/summary-generation-error.png" alt="summary-generation-error" title="summary-generation-error" style="border: 1px solid gray; zoom:80%;">

### Enabling Channel-Specific Automations and Managing Appearance in the Widget Library

Agent AI lets you configure channel-specific dialog tasks across all communication channels - Chat, Voice, and Email. You can also specify whether these dialog tasks appear in the list or only when searched in the widget’s library (**Search** tab). These preferences can be set while creating or editing a dialog task and are available under the **Triggers & Permissions** tab.
<img src="../images/triggers-and-permissions.png" alt="triggers-and-permissions" title="free text" style="border: 1px solid gray; zoom:80%;">

**When Enabled**: When a dialog task is enabled for a specific channel, it is triggered automatically or manually by the agent during interaction with customers on that specific channel.

**Launch Through Library**: 

**Enabled**: The dialog task is listed under all available dialog tasks in the **Search** tab of triggers-and-permissions widget.

**Disabled**: The dialog task doesn’t appear on the list but remains searchable via the “Ask a question” search bar in the **Search** tab.

### Agent AI Raw Data API v2

This updated version of the Raw Data API offers the following additional conversation data for deeper insights into Agent AI interactions and conversation flows:

* Feedback (reason code and feedback text in addition to like/dislike) from the agent.
* Complete generated answers with feedback
* Comprehensive agent activity tracking
* Full end-user utterances
* Dialog task execution details
* Agent search bar activity timing


## v11.2.1 June 15, 2024

<u>Patch Release</u>

This update includes bug fixes.

<hr>

## v11.2 June 01, 2024

<u>Patch Release</u>

This update includes feature enhancements and bug fixes. Key features and enhancements included in this release are summarized below.

### Auto-scroll Agent AI Widget Content

The **Auto-Scroll Assist Tab Content toggle** lets you manage the scrolling functionality of content in the Assist tab. Agents can enable/disable this toggle in the **AgentAssist widget** > **Settings** tab.
<img src="../images/autoscroll-settings-tab.png" alt="autoscroll-settings-tab" title="autoscroll-settings-tab" style="border: 1px solid gray; zoom:80%;">

<img src="../images/autoscroll-enabled-disabled-1.png" alt="autoscroll-enabled-disabled" title="autoscroll-enabled-disabled" style="border: 1px solid gray; zoom:80%;">

### Entity-Based Summarization

Dialog tasks having “message nodes” didn’t let users customize the Conversation Summary. Hence, to let users customize the Conversation Summary, “message nodes” are replaced with “entity nodes”. To utilize this capability, admins must create dialog tasks with entity nodes and select these dialog tasks in the **Agent AI** > **Configuration** > **Widget Settings** > **AgentAssist Channel Specific Settings** > **Auto Summarization** > **Auto Summarization Model** > **Custom Dialog Task** section.

<img src="../images/entity-based-summarization-2.png" alt="entity-based-summarization" title="entity-based-summarization" style="border: 1px solid gray; zoom:80%;">

For Conversation Summary customization, select a dialog task with “entity node” in the **Custom Dialog Task** field.

### Warm Transfer

Agent AI has introduced the **Warm Transfer** feature to customize the transfer functionality of the Agent AI widget. This feature specifically caters to third-party configurations, where appropriate transfer events are transmitted.

The **Warm Transfer** feature can be defined as a conference call between two agents and applies to both Voice and Chat channels. During this process, Agent-2 has the ability to modify the Summary Feedback, but the **Run**, **Override, Send, Copy, Terminate, Restart,** and **List View** buttons remain disabled until Agent-1 disconnects from the call. It has the following options to choose from:

* **Scroll up to the First Message**

* **Continue from the Last Message**

* **Configure Dialog Task**

### Negative Feedback Settings

For better processing and accurate identification of reasons for receiving a “thumbs down”, Admins can now configure a list of negative feedback messages for agents to select. They can also include a comment box for agents to add additional comments. Admins decide whether these two options appear in the widget after agents select the “thumbs down” icon at the end of a Dialog Task and after each answer and FAQ. Additionally, Admins can change the language of the feedback messages by selecting one from the available language list.

**Feedback Settings in the AgentAssist UI**:

<img src="../images/feedback-settings-ui-3.png" alt="feedback-settings-ui" title="feedback-settings-ui" style="border: 1px solid gray; zoom:80%;">

**Feedback Messages and Comment Box in the Widget**:

<img src="../images/feedback-settings-widget-4.png" alt="feedback-settings-widget" title="feedback-settings-widget" style="border: 1px solid gray; zoom:80%;">

<hr>

## v11.1.1 May 11, 2024

<u>Patch Release</u>

This update includes bug fixes.

<hr>

## v11.1.0 April 27, 2024

<u>Minor Release</u>

Key features and enhancements included in this release are summarized below.

### Agent AI Widget Updates

#### No Results Found and No Dialog Tasks Enabled Messages

The Agent AI widget now shows the “No Search Result Found. Could you rephrase your question or ask something else?” message when an agent’s search query on the search bar doesn’t show any results.
If no dialog tasks are configured for an account, the message “No dialog tasks enabled for library” appears in the Library/Search tab.

#### Updates to the Override Mode of the Agent AI widget

**Override Mode Off**
        
* When the customer's input is expected, the field remains grayed out and displays the entity name followed by “waiting….”
* The “Override” call-to-action (CTA) appears, and agents can click it to override the customer's utterance and manually populate the entity field.

**Override Mode On**
        
* The green “tick” mark that appeared after receiving the customer’s input is removed.
* The Entity Display Name appears with a cursor to indicate editing mode.
* Introduced the Cross and Check icons.
* The “keyboard” icon is replaced with the “agent” icon to indicate agent input.

### Agent AI Configuration with OpenAI GPT-3.5

For enhanced Real-time Coaching and Playbooks performance, the AgentAI configuration is now upgraded from OpenAI GPT 3.0 to OpenAI GPT 3.5. OpenAI GPT 3.5 delivers more accurate and context-aware responses, thereby enhancing Real-time Coaching effectiveness and Playbooks quality.

### Feedback Mechanism for Answers
In an effort to constantly improve the accuracy and helpfulness of answers displayed on the AgentAI widget, Kore has introduced a feedback mechanism for agents. Agents can now click the “thumbs up” or “thumbs down” icon displayed with every answer to indicate positive or negative feedback. This feedback data will help train Agent AI to provide more accurate answers.

### SearchAssist Configuration Page Updates

The SearchAssist Configuration page inside Agent AI has been updated with the following changes:

* Stream ID has been replaced with App ID.
* A warning is displayed when a user enters incorrect values in the configuration fields -  “Could not establish connection with SearchAssist. Check all parameters and try again. Hint: Ensure that the domain URL does not contain "https://" and does not have a forward slash "/" at the end.”
* As soon as a user lands on the configuration page, the following hint is displayed: “Ensure that the domain URL does not contain "https://" and does not have a forward slash "/" at the end.” 
* If a user enters incorrect values in the configuration page, the following error message is displayed: “Error establishing connection.

### Conversation Transfer Experience (Third-Party Agent Desktop)

Agent AI has introduced the Conversation Transfer feature to customize the transfer functionality of the Agent AI widget. This feature is applicable only to the third-party configurations where appropriate transfer events are transmitted. The Cold Transfer type applies to all three channels - Chat, Voice, and Email and has the following options to choose from:
* Scroll up to the First Message
* Continue from the Last Message
* Configure Dialog Task

### Configure your own Auto Summarization Model (Third-Party Agent Desktop)

Agent AI has introduced the **Auto Summarization Model** widget to customize the automatic summarization process. You can now select Kore’s default automatic summarization or the “Custom Dialog Task“ option, which lets you select a “dialog task with a single message node” to automatically generate the conversation summary. This is applicable only to third-party agent desktops.

After enabling the **Auto Summarization** toggle, select one of the following options:

* **OOTB Kore Summarization**: For Kore’s default auto summarization
* **Custom Dialog Task**: To generate customized auto summarization, you must select a dialog task with a single message node. These message nodes call APIs.

The **Custom Dialog Task** field displays a list of dialog tasks or child bots based on bot selection at the app level. 

The Agent AI widget's Assist tab now displays an updated Summary that includes the following:

* A **.ai Suggested** logo.
* The summary textbox has a cross icon for clearing the text.
* Ability to freely edit the summary within the text box.

After submission, the summary appears under the “.ai CONVERSATION SUMMARY” title with a **Copy** button at the bottom-right corner.

### Updated Summarization Feature

Agent AI has improved the Summarization feature of its widget. The latest version comes up with improved summary accuracy and advanced handling of various scenarios in conversations between agents and users. Currently, this update is available only for the US PROD environment and supports English. It is not yet available for DE, JP, EU, AU, and IND environments.  

**Key Highlights**
    
* Improved Summary Accuracy: The summary accuracy has been significantly improved through the implementation of a new model, and Agent AI is fine tuning it for specific use cases.
* Summary for Small Conversations: Agent AI has effectively addressed issues related to agent transfer scenarios between bots and users, ensuring seamless communication and comprehension.
* Handling Incomplete Summaries: The new model handles incomplete summaries more effectively, providing more comprehensive and useful insights even when the conversation is not fully concluded.
* Handling Longer Calls: The new model handles longer calls extending up to 20 minutes. The previous model would generate incomplete summaries for such extended conversations.

### Agent Coaching Updates

In Agent Coaching > Utterance Trigger section, **Anytime in conversation** is now a default selection for the “in conversation” field.

### Dashboard Updates

#### Enhanced Agent Feedback Functionality

The AgentAI dashboard has been updated to include a detailed summary of Agent Feedback for dialog tasks, including "Not Helpful" feedback and additional comments. Users can now get a detailed view of the “Not Helpful” feedback with Responses, Additional Comments, and Counts.

#### Average Widget Usage (Third-Party Agent Desktop)

The Dashboard has been updated to include the Average Widget Usage feature. This feature gives a graphical representation of the average amount of time agents spend on the AgentAI widget.
