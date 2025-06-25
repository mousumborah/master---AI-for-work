# Search AI Updates

This document provides information on the feature updates and enhancements introduced in **Search AI** of XO v11.x releases.

## v11.11.1 March 15, 2025

<u>Patch Release</u>

This update include only bug fixes.

<hr>

## v11.11.0 March 04, 2025

<u> Minor Release </u>

### Salesforce Connector Enhancements

The Salesforce Connector has been enhanced to support custom object ingestion in addition to the capability of ingesting default objects like Knowledge Articles, Cases, Documents, Opportunities, Leads, Contacts, Accounts, and Tasks. During configuration, users can select the type of content to be ingested, providing greater flexibility. Additionally, the filtering feature has been enhanced, allowing users to refine document ingestion based on specific fields. [Learn more :octicons-arrow-right-24:](./../../searchai/content-sources/connectors/salesforce.md)

### New Search AI Connectors (Beta)

Search AI extends support for five new connectors, enabling seamless content ingestion and retrieval from Guru, Miro, Help Scout, Wrike, and Zulip. These connectors enhance enterprise search by integrating knowledge from various collaboration and productivity platforms. The connectors also enable access control for the content that is ingested from the applications.

* [Guru](./../../searchai/content-sources/connectors/guru.md) – Ingests knowledge cards for centralized access to organizational information.
* [Miro](./../../searchai/content-sources/connectors/miro.md) – Enables searching the Miro boards.
* [HelpScout](./../../searchai/content-sources/connectors/helpscout.md) – Enables search across knowledge base articles.
* [Wrike](./../../searchai/content-sources/connectors/wrike.md) – Provides access and searchability for tasks.
* [Zulip](./../../searchai/content-sources/connectors/zulip.md) – Integrates messages from channels into search results and answers.

<hr>

## v11.10.0 February 12, 2025

<u> Minor Release </u>

### Custom Embeddings Support for Enhanced Vector Generation

The Custom LLM feature now supports Vector Generation in Search AI, allowing users to leverage custom embedding models for improved accuracy and relevance. Users can define custom requests, pre-processors, and post-processors, specify input and output keys, and seamlessly integrate with existing features. Search AI triggers vector generation during indexing and user query processing, while the document browser displays embedding status and allows filtering. This enhancement provides greater control, customization, and monitoring capabilities for delivering tailored search experiences.

### Custom Extraction (Beta)

The new Custom Extraction feature in Search AI enables a tailored approach to extracting content from sources. It sends ingested content to a third-party service, which processes and returns the extracted data in a structured chunk format. This enhances flexibility in handling diverse content extraction needs and ensures improved data retrieval and indexing within Search AI.

[Learn more :octicons-arrow-right-24:](./../../searchai/content-extraction/extraction.md#custom-extractionbeta)

### Answer Insights

The new Answer Insights feature provides comprehensive data about each query-response interaction, enabling a better understanding of system performance and easier troubleshooting.

Key features

* View a list of all answers for a grouped query.
* Search logs by answer and channel.
* Filter logs based on channel
* A detailed view of each answer, including query overview, answer debug information, and LLM request-response details (if available).

[Learn more :octicons-arrow-right-24:](./../../analytics/searchai/answer-insights.md)

### Search Results and Facets

The new Search Results feature, along with faceted search capabilities, allows retrieving and displaying multiple search results ranked by relevance for each query. 

Key changes

* Search Results now use the same pipeline as Answers for improved accuracy and consistency.
* Search Results Configuration - Enable/disable the feature and set the number of search results to display.
* Faceted search offers default filters, customizable filter creation, and static and dynamic filter types.

[Learn more :octicons-arrow-right-24:](./../../searchai/search-results.md)

### Introducing Connector Ingestion Logs for Greater Visibility

Search AI now provides Connector Ingestion Logs, providing file-level status information (successful, failed, or skipped) and pop-ups with error details. Users can now easily identify and troubleshoot issues, understand the actual content available, and re-sync connectors to ensure up-to-date content. The update also improves tracking capabilities and record document sizes in Search AI. 

[Learn more :octicons-arrow-right-24:](./../../searchai/content-sources/connectors.md)

### New Connector Experience: Discover and Configure with Ease

The revamped connector experience makes it easier to discover and configure integrations. The new Configured and All Connectors tabs provide a more informative and intuitive interface, with improved search functionality for quick access to connector configuration. These enhancements streamline the process of connecting data sources and leveraging the unified search capabilities.

[Learn more :octicons-arrow-right-24:](./../../searchai/content-sources/connectors.md)

<hr>

## v11.9.1 January 25, 2025

<u>Patch Release</u>

This update include only bug fixes.

<hr>

## v11.9.0 January 05, 2025

<u>Minor Release</u>

This update include only bug fixes.

<hr>

## v11.8.1 December 19, 2024

<u>Patch Release</u>

This update include enhancement and bug fixes. The key enhancement included in this release is summarized below.

### Content Transformation

Search AI introduces an ETL tool, empowering users to enrich content immediately after extraction and before vectorization. This feature enhances data quality by enabling users to fix errors and enrich data while preserving essential relationships and context between sections of the original document during enrichment.

This tool offers flexibility and control through enrichment stages that can be applied based on the document's extraction strategy. Currently, the following enrichment stages are supported:

* Field Mapping: Map extracted data fields to desired fields.
* Custom Script: Apply custom transformations using custom scripts.

This enrichment process ensures high-quality input for improved answers.

### Change Logs

SearchAI introduces a comprehensive **Change Logs** feature to track and manage application updates made by all team members. Users can search logs by user, export them in CSV format, and access them through public APIs. This feature ensures transparency and simplifies auditing and troubleshooting by providing a centralized view of all changes.

### Chunk Size Configuration

To leverage the potential of the LLM capabilities, Search AI has now increased the chunk size and the maximum number of tokens sent to the LLM. This update ensures that the LLM receives sufficient context for more accurate and comprehensive answer generation.

* The **default chunk** size has been updated to **1000**, with a maximum limit of **5000** tokens per chunk.
* The value of the maximum number of tokens for **Chunk Overlap** is also increased to **100**.
* A new configuration, **Max Tokens for Chunks**, has been introduced that specifies the total number of tokens that can be included in the chunks sent to the LLM for processing. This allows users to fully utilize the LLM’s context-handling capabilities. This has a default value of 20,000 and can take a maximum value of 10,00,000. 

<hr>


## v11.8.0 December 11, 2024

<u> Minor Release </u>

This update include enhancement and bug fixes. The key enhancement included in this release is summarized below.

### Comprehensive Analytics Logs

The new Answer Insights feature provides enhanced visibility into query-response interactions, aiding developers and analysts in debugging, performance improvement, and response quality assessment. 

### Enhanced API Support

Search AI now provides expanded API functionality, enabling users to manage content, retrieve chunks, Ingest new content, and Train the application. This enhancement provides greater control and flexibility for application developers.

### Enhancement for Hybrid Retrieval Search

Search AI now automates query optimization by removing stop words from user queries when using the Hybrid retrieval strategy. This enhancement improves retrieval accuracy, delivering more relevant and precise search results without requiring manual adjustments.

### Public API to fetch the List of Connectors

Search AI now includes a Public API that allows users to retrieve a list of all connectors configured in the application. This addition allows developers to manage connectors programmatically, enhancing productivity.

<hr>

## v11.7.1 November 18, 2024

<u> Patch Release </u>

This update includes enhancements and bug fixes. Key enhancements included in this release are summarized below.

### Advanced Search API Enhancement 
The Answer Generation API has been enhanced to support passing permission entity IDs, enabling refined and secure search responses. This update provides control over content access and ensures that users receive answers tailored to their permissions.

### Introduction of Get Content API
Search AI introduces a new API that enables users to retrieve a document's content, metadata, or both using its ID. This enhancement simplifies access to document data and improves the overall content retrieval experience. 

### Permission Entity API Enhancement
The Get Permission Entity API has been enhanced to provide more comprehensive information. The update adds the entity type and source type to the existing permission entity details in the response. This enhancement helps developers gain deeper insights into permission entities, streamlining integration efforts.


<hr>

## v11.7 November 03, 2024

<u> Minor Release </u>

This update include enhancement and bug fixes. The key enhancement included in this release is summarized below.

### Support for Custom Connector

Search AI now supports content ingestion from any application using the Custom Content Connector. This connector utilizes the application's REST APIs to ingest content facilitated through the Custom Connector Service. Additionally, Search AI enables access control for content ingested via the Custom Connector, ensuring secure access. This feature enhances flexibility by seamlessly integrating various applications, even without pre-built connectors.

### Advanced Filters for ServiceNow and SharePoint Connector

Search AI now supports advanced content filtering within the ServiceNow and SharePoint connectors, enabling users to refine the scope of ingested data from the repositories. This functionality allows administrators to apply specific criteria to select only relevant records or knowledge articles to make searchable. By filtering content based on attributes like status, category, and custom fields, organizations can tailor search responses to meet specific user needs, improving search accuracy.

### Ingesting Documents with Attachments in the Confluence Server

Search AI now supports ingesting Confluence Server documents with attachments, streamlining content indexing and retrieval. Users can include documents as attachments with Confluence knowledge articles. The primary content and its attachments are searchable and accessible, enhancing content discoverability and maximizing the accessibility of embedded knowledge. 

### Enhanced Multi-Modal Content Preview

End-users and developers can now seamlessly preview content within answers and the chunk browser. This enhanced viewing experience includes zoom functionality for tables and images, allowing users to thoroughly examine complex data and visual content. When content contains multiple images, a new carousel interface presents them in an elegant slideshow format, enabling effortless navigation through all visual assets. This integrated preview system streamlines the user experience by making all content immediately accessible and interactive within the natural workflow.


<hr>

## v11.6.1 October 21, 2024

<u> Patch Release </u>

This update include enhancement and bug fixes. The key enhancement included in this release is summarized below.

### Public APIs for Ingesting Structured Data

Search AI introduces public APIs to automate the ingestion and indexing of structured data within the application. Structured data, organized in predefined formats, enables more accurate and relevant search outcomes. This enhancement provides seamless integration for structured data, improving search accuracy and content accessibility.

<hr>

## v11.6.0 September 28, 2024

<u> Minor Release </u>

This update includes enhancements and bug fixes.

### Structured Data as a Source Type

SearchAI now enables the ingestion and indexing of structured data in JSON format using the JSON connector, providing greater flexibility in handling complex data. This feature allows users to seamlessly process and search through structured datasets for more efficient and accurate results.

### Retrieve Chunk Metadata through Advanced Search API

This enhancement to the Advanced Search API allows users to specify and include custom metadata fields in the generated answers. The API response can now be customized to fetch user-defined metadata fields for each chunk in addition to the default fields, providing a more customized and detailed output.

<hr>

## v11.5.1 September 14, 2024

<u> Patch Release </u>

### Advanced Content Extraction from Web Pages

With this release, Search AI introduces advanced support for extracting content from images and tables embedded in web pages. Using advanced extraction technologies, Search AI can now analyze and extract text from image files and complex, structured tables, providing a more comprehensive approach to processing web-based content. This enhancement significantly enhances the application’s ability to index and search diverse content formats.

<hr>

## v11.5.0 September 01, 2024

<u> Patch Release </u>

This update includes enhancements and bug fixes. Key enhancements included in this release are summarized below.

### Content Browser

Search AI chunk browser is now enhanced to make it more user-friendly, providing a detailed view of the extracted content and making it easier to edit. Additionally, you can now view tables directly in the browser. 

### Extraction of Complex Tables from HTML

Search AI can now extract content from complex HTML tables using the Layout-Aware Extraction Strategy, enhancing its ability to accurately capture and process data from table structures. This improvement ensures more reliable data extraction and accurate information retrieval from tabular content.

### Support for New Connectors (Beta)

SearchAI now extends support for data ingestion from a broader range of knowledge bases and enterprise applications through connectors, including Airtable, HubSpot, GitLab, GitHub, Jira, Monday, Notion, and Slack. This expansion allows users to seamlessly integrate and ingest content from these platforms, enhancing the versatility of the data sources.

### Sharepoint Site Support Enhancement

SearchAI now supports ingesting content from up to 6,000 sites from Sharepoint using the connector. This enhancement allows users to seamlessly access and search through a large volume of data, ensuring better search capabilities and improving the information retrieval process across the organization.

### Support for Re-Rankers 

Search AI now offers advanced re-ranking capabilities to improve the quality and relevance of retrieved content significantly. Re-ranking is a crucial second step in the search process that refines initial results for greater accuracy. Enable and configure re-ranking models, like Cross Encoder, BGE, or MixedBread re-rankers, to reorder the chunks provided by the first-stage retriever, ensuring more relevant and accurate answers. 

### Enhanced Search AI Navigation 

The latest version of Search AI offers a simplified interface that is easy to use and intuitive to navigate. The newer design enhances usability and productivity. 

<hr>

## v11.4.1 August 11, 2024

<u> Patch Release </u>

This update includes bug fixes and minor enhancements.

### Search AI Menu Update

The "Answers" menu is renamed "Search Configurations" across the product, aligning with the revised product naming convention. 

Key updates:

* “Search AI > Answers” is now "Search AI > Search Configurations".
* The header in the side navigation for this section now reads "Search Configurations".
* In Automation AI, "Answers" is replaced with "Search Configurations".

<hr>

## v11.4 July 27, 2024

<u> Patch Release </u>

This update includes feature enhancements and bug fixes. Key features and enhancements included in this release are summarized below.

### Source Ingestion Logs

Search AI now maintains comprehensive logs for the content ingested through web crawling. These logs include status codes, sizes, and other necessary details for each page ingested or skipped during the crawling process. Detailed logs help the administrators monitor the ingestion process and promptly identify and resolve issues. 

### Detailed Error Messages for Web Crawl Failures

Search AI now provides detailed error messages for web crawl failures, along with recommended actions to take. This enhancement aids in quick troubleshooting and rectification of issues.

### Answer Generation API Enhancement

The Answer Generation API now allows for more details about the answer in the response. You can get detailed information about the qualified chunks for the query in response, along with the answer to the query. This can be particularly useful to orchestrate complex use cases.

### Answer Generation Errors

Search AI now displays error messages to users when the answer generation process fails. These errors may occur for various reasons, such as an invalid OpenAI key or the absence of relevant chunks. This feature ensures users are promptly informed of any issues, facilitating quicker resolution.

### Layout Aware Content Extraction Strategy (Beta)

Search AI introduces an advanced way of extracting content from documents (PDF and DOCX) by detecting the objects in the document using a combination of OCR technology, layout detection models, and layout awareness rules. This advanced strategy can accurately extract content from tables, graphs, and charts in the documents.

<hr>

## v11.3.1 July 13, 2024

<u> Patch Release </u>

This update includes bug fixes.

<hr>

## v11.3.0 June 29, 2024

<u> Patch Release </u>

Key features and enhancements included in this release are summarized below.

### Support for Filtered Content Ingestion from third-party applications

Search AI now extends support for content ingestion from a wider variety of third-party applications, including Confluence Cloud, Azure Storage, Salesforce, Oracle Knowledge, and dotCMS, in addition to the existing connectors. The connectors now offer customizable filters that give platform users the flexibility to selectively ingest data, allowing for precise and targeted indexing and enhancing the search index's efficiency and accuracy.

### Advanced Web Crawl Configurations

Search AI now offers advanced web crawl capabilities that allow platform users to remove redundant sections of a web page while indexing. Also, for JavaScript-rendered pages, the users can now introduce a delay after which the crawler starts indexing the page, allowing all dynamic content to load properly. These enhancements provide greater control and precision in web crawling, leading to a more efficient and accurate search experience.

<hr>

## v11.2.1 June 15, 2024

<u>Patch Release</u>

Key features and enhancements included in this release are summarized below.

###  Automated Content Syncing and Training with Connectors

Search AI now offers the capability to schedule automatic content syncing from third-party applications using connectors. The data is automatically ingested, and the application is trained with the new data, ensuring that the content is always up to date.

###  Enhanced Web Crawl Error Reporting

The enhanced web crawl error reporting feature in Search AI provides detailed information about crawl failures, enabling quick identification and resolution of issues. 


<hr>

## v11.2 June 01, 2024

<u>Patch Release</u>

Key features and enhancements included in this release are summarized below.

###  Support for Hybrid Chunk Retrieval Strategy

Search AI now supports the Hybrid Chunk Retrieval strategy, which leverages both keyword-based and semantic search techniques to deliver more precise and contextually appropriate answers. This improvement ensures that users receive high-quality responses tailored to their queries, enhancing the overall search experience.

###  Chunk Order Configuration 

Search AI now allows adding relevant chunks in your preferred order within the prompt. The order of the chunks in the prompt can affect the performance depending upon the LLM limitations of context retention, prompt lengths, and attention mechanism. By allowing users to configure the chunk order, SearchAI ensures that relevant data is prioritized, improving the generated responses' quality and reliability.

<hr>

## v11.1.1 May 11, 2024

<u>Patch Release</u>

This update includes feature enhancements and bug fixes. Key enhancement included in this release is summarized below.

### Extended Connector Support

In addition to the existing ServiceNow connector, Search AI now supports more knowledge base connectors, including Zendesk, Confluence Server, Google Drive, and Dropbox. The new connectors make it easier to integrate Search AI with these platforms, helping users quickly find and access information to boost productivity. [Learn more :octicons-arrow-right-24:](../../searchai/content-sources/connectors.md)

<hr>

## v11.1.0 April 27, 2024

<u>Minor Release</u>

This update includes feature enhancements and bug fixes. Key feature included in this release is summarized below.

### Business Rules Support

Business Rules Support allows users to define custom rules that modify the answers provided by the AI search system. By using contextual data specific to their needs, users can create tailored rules to refine the AI's responses. The system also suggests relevant context variables dynamically to assist in defining these rules. [Learn more :octicons-arrow-right-24:](../../searchai/business-rules.md)
