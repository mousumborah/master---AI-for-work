# DocSearch Node

The **DocSearch Node** in GALE's Agent Flow improves how information is found and processed. It uses advanced searching called Retrieval Augmented Generation (RAG). 

By connecting to your **Search AI** App, the DocSearch Node provides high-quality search results that are relevant to the current context. These results are delivered right inside the agent workflow.

## Key Features

* **RAG Searching Framework**:

    RAG blends traditional retrieval systems (e.g., search, databases) with generative LLM capabilities, ensuring more accurate, relevant, and up-to-date results tailored to your needs.

    RAG enhances generative AI outputs through these key steps:

    <ul><li><b>Retrieval & Pre-processing</b>: Powerful search algorithms query external data (e.g., web pages, databases). Retrieved data is pre-processed through tokenization, stemming, and stop-word removal.</li>
    <li><b>Grounded Generation</b>: Pre-processed data integrates with the LLM, enriching its context for more accurate, informative, and engaging responses.</li></ul>
<ul><li><b>Integration with SearchAI</b>     
    <ul><li>The DocSearch Node connects to a configured <b>Search AI App</b> via GALE’s integration page.</li>
    <li>It accesses indexed resources from the <b>Sources</b> repository within Search AI to retrieve relevant information.</li></ul></li>
    <li><b>Dynamic Input Queries</b></li>
    <ul><li>Accepts search input either as a variable or static text.</li>
    <li>Facilitates seamless query processing by <b>Search AI</b>, which identifies and extracts/retrieves contextually relevant chunks from the available resources using SearchAI’s <a href="https://docs.kore.ai/xo/searchai/answer-generation/" target="_blank">Answer Generation</a>, corresponding to the input query and the meta filters provided via the <b>Advanced Search API</b>. <a href="https://docs.kore.ai/xo/apis/searchai/answer-generation/" target="_blank">Learn more</a>.</li></ul></ul>

* **Configurable Meta filters**

    * You can configure optional meta filters to narrow the search field with the query.
    * If meta filters are not provided, the query is applied to all the documents uploaded to that connection. [Learn more](./docsearch-node.md/#step-2-link-the-search-ai-app-in-gale){:target="_blank"}.

* **Redirection Capability**

    * Includes an option to redirect users to the **Search AI App** directly from the node.

* **Enhanced Search Relevance**

    * By prioritizing results using RAG criteria, the node provides precise, complete, and context-aware answers.
    * Improves search relevance by focusing on delivering responses tailored to user intent.

* **Contextual Personalization**

    * Ensures results are personalized to the query context, enhancing user experience and satisfaction.

* **Connectivity with Other Nodes**

    * Connect the DocSearch Node inputs and outputs to other nodes for seamless integration and data flow within the Agent Flow Canvas.

## Configuration Overview

Configuring the DocSearch Node consists of the following steps:

1. [Set up a Search AI application and the information source for GALE integration](./docsearch-node.md/#step-1-set-up-search-ai-app){:target="_blank"}.
2. [Link the Search AI application in GALE](./docsearch-node.md/#step-2-link-the-search-ai-app-in-gale){:target="_blank"}.
3. [Add and configure the DocSearch node](./docsearch-node.md/#step-3-add-and-configure-a-docsearch-node){:target="_blank"}.

## Step 1: Set up Search AI App

The integration of Search AI with GALE involves setting up a Search AI application, configuring it for integration, and modifying GALE to interact with Search AI in response to specific conditions or events. Search AI provides REST APIs that enable seamless interaction with any application.

Follow the detailed steps [here](https://docs.kore.ai/xo/apis/automation/api-introduction/#creating-and-managing-jwt-apps-in-xo-platform){:target="_blank"} to complete the configuration.

<div class="admonition note">
<p class="admonition-title">Note</p>
<p>To receive answers from Search AI, you must enable the <b><i>Answer Generation</i></b> option under the <b>API scopes</b> section.</p></div>


## Step 2: Link the Search AI App in GALE

After fetching the Search AI application credentials, configuring the source, and enabling the channel communication via API, you must link the app in GALE. 

**Steps to integrate Search AI in GALE**

1. [Sign in](../../../getting-started/sign-up-sign-in.md/#sign-in-to-gale){:target="_blank"} to your GALE account.
2. [Navigate](../../../settings/settings-overview.md/#access-settings-console){:target="_blank"} to the **Settings** console.
3. Click **Integrations** on the left navigation menu.
4. Scroll down to **Search AI** and click **Link an App**.
<img src="../images/link-an-app.png" alt="link an app" title="link an app" style="border: 1px solid gray; zoom:75%;">

5. In the **Search AI** window, provide the required information that you copied from the SearchAI application in 
[Step 1](./docsearch-node.md/#step-1-set-up-search-ai-app){:target="_blank"}.
6. Click **Test** to test the connection.
7. If the connection is successful, click **Confirm**.
<img src="../images/searchai-connection-form.png" alt="searchai connection form" title="searchai connection form" style="border: 1px solid gray; zoom:75%;">

A success message is displayed and the connection is listed for SearchAI.
<img src="../images/listed-connection.png" alt="listed connection" title="listed connection" style="border: 1px solid gray; zoom:75%;">

If the connection fails with the following message, check and re-enter the correct Search AI app credentials.

<img src="../images/connection-failure.png" alt="connection failure" title="connection failure" style="border: 1px solid gray; zoom:75%;">

<div class="admonition note">
<p class="admonition-title">Note</p>
<p>Currently, we support connections through Search AI. You must provide "<code>https://platform.kore.ai</code>" for the <b>Search AI URL</b> field.</p></div>

## Step 3: Add and Configure a DocSearch Node

Setting up a DocSearch node in an agent flow involves adding the node at the appropriate location in the flow and configuring various node properties.

**Steps to add and configure the node**

1. On the **Agents** tab, click the name of the agent to which you want to add the node. The **Agent Flow** page is displayed.
<img src="../images/access-agents-menu.png" alt="access agents menu" title="access agents menu" style="border: 1px solid gray; zoom:75%;">

2. Click **Go to flow** to edit the in-development version of the flow.
<img src="../images/go-to-flow-doc-search.png" alt="go to agent flow" title="go to agent flow" style="border: 1px solid gray; zoom:75%;">

3. In the flow builder, click **DocSearch** -> **+ New DocSearch** on the **Assets** panel. Alternatively, click **DocSearch** in the bottom panel.
<img src="../images/add-docsearch-node.png" alt="add doc search node" title="add doc search node" style="border: 1px solid gray; zoom:75%;">

4. To provide a unique name, right-click the node and click **Rename** since the node is provided a default name.

    <img src="../images/rename-docsearch-node.png" alt="rename node" title="rename node" style="border: 1px solid gray; zoom:75%;">

Alternatively, click the node and change the value for **Node Name** in the configuration panel.
<img src="../images/node-name.png" alt="node name" title="node name" style="border: 1px solid gray; zoom:75%;">

<ol start="5"><li>Enter an input variable for dynamic inputs or plaintext for hard-coded inputs in the <b>Query</b> field. This field captures the user’s search query.
<img src="../images/context-input.png" alt="query field" title="query field" style="border: 1px solid gray; zoom:75%;"></li>
<li>Select the <b>Search AI connection</b> you set up in <a href="https://docs.kore.ai/gale/agents/agents-flows/types-of-nodes/docsearch-node/#step-2-link-the-search-ai-app-in-gale" target="_blank">Step 2</a> on the GALE integration page.
<img src="../images/searchai-connection.png" alt="search ai connection" title="search ai connection" style="border: 1px solid gray; zoom:75%;"></li></ol>

<div class="admonition note">
<p class="admonition-title">Note</p>
<p>Use search to look up and select the required connection.</p></div>

To set up a new connection, click **+ New Connection**. This will redirect you to the GALE Integrations page. Follow the steps mentioned [here](./docsearch-node.md/#step-2-link-the-search-ai-app-in-gale){:target="_blank"} to complete the integration.

<ol start="7"><li>(Optional) Set <b>Meta filters</b> (click the expansion arrow to access the editor) to define rules that will narrow down the search results. For example, if the sources have multiple files, you can define the specific file names to look up in the meta filters code. <a href="https://docs.kore.ai/xo/apis/searchai/answer-generation/#body-parameters" target="_blank">Learn more</a>.
<img src="../images/set-meta-filters.png" alt="set meta filters" title="set meta filters" style="border: 1px solid gray; zoom:75%;"></li></ol>

<div class="admonition note">
<p class="admonition-title">Note</p>
<p><ul><li>If you do not provide any meta filters, the query is applied to all the documents uploaded to that connection.</li>
<li>The filters can be a context variable in the flow depending on the builder’s requirement.</li></ul></p></div> 

<ol start="8"><li>Enter the search query in the text field.
<img src="../images/enter-search-query.png" alt="enter the search query" title="enter the search query" style="border: 1px solid gray; zoom:75%;"></li>
<li>Click the <b>Response</b> tab and define the JSON structure for the agent's response to the user's query.
<img src="../images/click-response-tab.png" alt="click response tab" title="click response tab" style="border: 1px solid gray; zoom:75%;"></li>
<li>Click <b>Test</b> to test the response.</li>
<img src="../images/test-response.png" alt="test response" title="test response" style="border: 1px solid gray; zoom:75%;"></ol>

The request and response are displayed in the **Run** window.
<img src="../images/run-window.png" alt="run window" title="run window" style="border: 1px solid gray; zoom:75%;">

Use the extracted chunks (shown in the example below), as required to build the agent flow.
<img src="../images/chunks-example.png" alt="extracted chunks" title="extracted chunks" style="border: 1px solid gray; zoom:75%;">

## Related Links

* [Manage Nodes in Agent Flow](../manage-flow-nodes.md){:target="_blank"} - Add and manage nodes on the canvas.
* [Run Agent Flow](../perform-other-actions-on-the-flow-builder/run-the-flow.md){:target="_blank"} - Run and test an agent flow in real time.


