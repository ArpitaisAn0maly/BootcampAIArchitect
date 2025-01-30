# Deploying Azure OpenAI with AI Search and Storage

## Step 1: Sign into Azure Portal
Sign into the Azure portal at [Azure Portal](https://portal.azure.us)

## Step 2: Create an Azure OpenAI Resource
Create an Azure OpenAI resource with the following settings:

- **Subscription**: Select an Azure subscription that has been approved for access to the Azure OpenAI service
- **Resource group**: Choose or create a resource group
- **Region**: `usgovarizona`
- **Name**: A unique name of your choice
- **Pricing tier**: `Standard S0`
 

## Step 3: Create an Azure AI Search Resource
While the Azure OpenAI resource is being provisioned, create an Azure AI Search resource with the following settings:

- **Subscription**: The same subscription where you provisioned your Azure OpenAI resource
- **Resource group**: The same resource group where you provisioned your Azure OpenAI resource
- **Service name**: A unique name of your choice
- **Location**: The same region where you provisioned your Azure OpenAI resource
- **Pricing tier**: `Basic`

## Step 4: Create a Storage Account
While the Azure AI Search resource is being provisioned, create a Storage account with the following settings:

- **Subscription**: The same subscription where you provisioned your Azure OpenAI resource
- **Resource group**: The same resource group where you provisioned your Azure OpenAI resource
- **Storage account name**: A unique name of your choice
- **Region**: The same region where you provisioned your Azure OpenAI resource
- **Performance**: `Standard`
- **Redundancy**: `Locally redundant storage (LRS)`

## Step 5: Gather Resource Information
After all three resources have been successfully deployed, collect the following information from the Azure portal:

- The **endpoint** and **key** from the Azure OpenAI resource (available on the *Keys and Endpoint* page)

## Step 6: Upload Your Data
You will use a collection of travel brochures to ground your prompts.

1. Download an archive of brochure data from [this link](https://aka.ms/own-data-brochures) and extract the files to a folder on your PC.
2. In the Azure portal, navigate to your **Storage account**.
3. Go to **Storage browser** → **Blob containers** → **Add new container** and name it `travel`.
4. Open the `travel` container and upload the extracted `.pdf` brochures to the root folder.

## Step 7: Deploy AI Models
You will deploy two AI models: a text embedding model and a GPT model.

### Deploy Text Embedding Model
1. Navigate to your Azure OpenAI resource in the Azure portal.
2. Open **Azure OpenAI Studio**.
3. In **Deployments**, create a new base model deployment with:
   - **Deployment name**: `ada`
   - **Model**: `text-embedding-ada-002`
   - **Model version**: Default
   - **Deployment type**: `Standard`
   - **Tokens per minute rate limit**: Maximum
   - **Content filter**: Default
   - **Enable dynamic quota**: Enabled

### Deploy GPT Model
1. Return to **Deployments** and create another deployment:
   - **Deployment name**: `gpt4o` or `gpt4omini`
   - **Model**: `gpt-4o` or `gpt-4o-mini`
   - **Model version**: Default
   - **Deployment type**: `Standard`
   - **Tokens per minute rate limit**: Maximum
   - **Content filter**: Default
   - **Enable dynamic quota**: Enabled

## Step 8: Add Your Data
1. Select **Chat** under **Playgrounds** in the left menu and choose your model deployment.
2. In the **Chat playground**, select **Add your data** → **Add a data source**.
   ![Azure OpenAI Studio Screenshot](/Session%201/AOAIStudio.png)
3. In the pane that appears:
   - Select **Upload files (preview)** under *Select data source*.
   - Enable **Cross-origin resource sharing (CORS)** for your **Azure Blob Storage** if it is not already enabled.
   - Select your **Azure AI Search** resource and acknowledge usage costs.
   - Click **Next**.
4. On the **Upload files** pane:
   - Browse and upload the `.pdf` brochures you downloaded.
   - Click **Next**.
5. On the **Data management** pane:
   - Choose to enable **semantic search** or **vector search** for indexing.
   ![Add your data](/Session%201/BYOD.png)     
6. Review the details and click **Save and close**.
7. Now, you can chat with the model, and it will use the uploaded data to construct responses.
