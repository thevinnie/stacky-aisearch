# Stacky AI Search

## Steps

### Azure AI Search
0. This should already be available in your subscription with an Embeddings model deployed. The default in the labs is text-embeddings-ada-002.


### Storage

1. In your Azure subscription, create an ADLS Gen 2 storage account.
2. Create a container called "stackexchange"
3. From this repository, choose 1 file from a site of your interest from the /data/ folder
4. Upload to the "stackechange" folder in ADLSGen2.  
( The zip file contains other data which may be useful to you after this lab, uploading more than 1 file will take up to two hours (or more) to index. )

### Azure AI Search

5. Create an Azure AI Search resource, if you don't have one already
6. On the Overview blade of Azure AI Search, choose the option to "Import and vectorize your data".

### Import and vectorize data 

#### Connect to your data 

7. Choose Azure Data Lake Storage Gen2
8. Select your Subscription, Storage account, and Blob container where thet JSON files are located.
9. Leave the Blob Folder option empty as you uploaded directly to the root folder
10. Parsing mode - choose "JSON array", then leave the Document root option blank
11. Click Next which will initiate schema validation

#### Vectorize your text 
12. Column to vectorize, select Body, which contains the test from the posts
13. Leave Kind and Subscription with the defaults, which should be Azure OpenAI and your Subscription
14. Select your Azure OpenAI Service
15. Select the embeddings model which was already deployed, text-embedding-ada-002
16. Leave the option for API Key selected, and check the box for acknowledgement of costs associated with using Azure OpenAI

#### Advanced Settings
17. Leave the defaults for these settings

#### Review and Create
18. Review the settings then click Create, which will deploy the Index, Indexer, and configuration profiles to Azure AI Search. It will also initiate the indexing process.

20. Back in Azure AI Search, observe the Indexer progress. When complete, continue back in Azure AI Foundry

### Azure AI Foundry Chat Playground

20. Inside the Azure AI Foundry portal, click on the Chat option under Playground
21. Enter the instructions from grounding.txt in "Give the model instructions and context", then click Apply Changes
22. Expand the "Add your data" section and click the "Add a data source"

### Add data

#### Data Source

23. From the drop down, select Azure AI Search
24. The subscription should already be populated, then select the existing Azure AI Search instance and the Index you just created
25. Check the box for "Add vector search to this search resource" and select the already deployed embeddings model used earlier.
26. Leave the Use custom field mapping unchecked

#### Data management

27. Leave the Search type as the default option
28. Select the existing vector search configuration from your Azure AI Search resource

#### Data connection 

29. Select the API Key option
30. After validation, click Save and Close



## Licensing
StackExchange Datadump Licensing  
https://meta.stackexchange.com/questions/401324/announcing-a-change-to-the-data-dump-process

This data is prepared and used by individuals for use _with_ an LLM, not to train an LLM. Think of it this way: training an LLM is like teaching it new skills and knowledge, while accessing your own data with an LLM is like asking a trained expert to interpret or respond based on specific information you provide.

Training an LLM: 
* Purpose: The data is used to improve or refine the model's ability to understand and generate human-like text.
* Method: The data is fed into the model during its training phase. This phase involves updating the model's parameters based on the patterns and information found in the data.
* Scale: Typically involves large volumes of diverse data to ensure the model learns a wide range of language patterns.

Accessing Your Own Data with an LLM: 
* Purpose: The model is used to process, analyze, or generate responses based on your own specific data.
* Method: The data is input to the model at runtime (i.e., when the model is already trained), and the model uses its existing knowledge to interpret or generate responses related to that data.
* Scale: Usually involves a specific subset of data relevant to your needs, rather than the vast and diverse data used for training.
