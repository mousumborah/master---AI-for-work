# Retrieval 

This section allows you to configure the chunk retrieval strategy and the corresponding thresholds.

## Retrieval Strategy

Choose the preferred chunk retrieval strategy for retrieving answer chunks from the answer index for a given query. Search AI supports **Vector retrieval**, which uses cosine similarity scores, and **Hybrid retrieval**, which considers patterns and structures in the text. The choice between using vector retrieval and hybrid retrieval depends on various factors, including the nature of the data, the specific requirements of the application, and the available resources.

1. **Vector Retrieval**: In this type of retrieval, at the time of query, we compute the cosine similarity between the query vector and each chunk vector, and the resulting scores are used to filter and sort the results. The score ranges from 0 to 1, where 0 indicates no match, and 1 represents a complete match.
2. **Hybrid Retrieval**: This retrieval method combines multiple approaches to identify the most relevant content in response to a query. It primarily merges keyword-based matching with vector-based scoring, leveraging the strengths of both to improve accuracy and relevance in search results.

## Qualification Criteria

* **Similarity Score Threshold**: This setting allows users to specify the minimum similarity score required for an answer chunk to be considered relevant. Chunks with scores below this threshold are discarded. This parameter can take any value between 0 and 100. The greater the value of this field, the more similarity score is required.
* **Proximity Threshold:** This parameter can be used to determine how closely retrieved chunks should be located to the highest-ranking chunk. Chunks beyond this threshold are discarded. This parameter can take any value between 0 and 50. The lower the value of the proximity threshold, the closer the chunks are.
* **Top Chunks**: This field specifies the maximum number of qualified answer chunks to be considered for generating answers. In the case of generative answers, these number of top chunks are sent to the LLM as the context for generating an answer to the user query. 

**By default, the Hybrid Retrieval mechanism is used, and the Top Chunks number is set to 10.**
