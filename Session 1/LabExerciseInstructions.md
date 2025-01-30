# Azure OpenAI Setup and API Calls Guide

## How to Set Up Environment

Follow the steps in the [Azure OpenAI Quick Start](https://github.com/Azure/azure-openai-samples/tree/main/quick_start) to set up your environment.

## Make Azure Open AI API Calls using Python SDK

To make API calls, you can refer to the [ChatCompletion API notebook](https://github.com/Azure/azure-openai-samples/blob/main/quick_start/v1/02_ChatCompletion_api.ipynb). 

Make sure to use the API version: **2024-05-01-preview** for the exercises.

### Environment File for Lab

Use the provided `.env.sample` file for your environment setup:

[Sample `.env` file](https://github.com/Azure/azure-openai-samples/blob/main/quick_start/v1/.env.sample)

Here is an example of the required environment variables:

```plaintext
AZURE_OPENAI_ENDPOINT=https://<your service name>.openai.azure.com/
AZURE_OPENAI_KEY=xxxxxxxxxxxxxxxxxxxxxxxx
AZURE_OPENAI_DEPLOYMENT_NAME=gpt4o
EMBEDDING_MODEL_NAME=text-embedding-ada-002
