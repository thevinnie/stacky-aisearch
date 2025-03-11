# Stacky AI Search

## Steps

### Azure AI Search
0. This should already be available in your subscription with an Embeddings model deployed. The default in the labs is text-embeddings-ada-002.


### Storage

1. In your Azure subscription, create an ADLS Gen 2 storage account.
2. Create a container called "stackexchange"
3. From this repository, download the posts_json_2024.zip and extract the contents
4. Choose up to three files from the folder and upload to the "stackechange" folder in ADLSGen2

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


