# Deployment Instructions

## Open Repository
Open the repository in Microsoft Edge and use single sign-on:
[PubSec-Info-Assistant](https://github.com/microsoft/PubSec-Info-Assistant)

This will allow you to sign on github where you have access to your connected Organization such as Microsoft. If you dont have this connected then use this link to connect your org.
Without this your codespace use will be limited.[connect Microsoft Org to your Github](https://repos.opensource.microsoft.com/link)

## Deployment Guide
Follow the deployment guide instructions:
[Deployment Guide](https://github.com/microsoft/PubSec-Info-Assistant/blob/main/docs/deployment/deployment.md)

## Setting Up Codespaces
Once you open Github repo, Click on **Code** and select the **Codespaces** tab to create a new codespace. 
For any help with creating codespaces refer to:
[Developing in GitHub Codespaces](https://github.com/microsoft/PubSec-Info-Assistant/blob/main/docs/deployment/developing_in_a_GitHub_Codespaces.md)

## Configure Environment Variables
1. Open `scripts/environments` and copy `local.env.example` to `local.env`.
2. Update `local.env` values as specified in this table:  
   [Configure Environment Files](https://github.com/microsoft/PubSec-Info-Assistant/blob/main/docs/deployment/deployment.md#configure-env-files)
3. Alternatively, copy the environment file example from:
   [BootcampAIArchitect/Session4/local.env](https://github.com/ArpitaisAn0maly/BootcampAIArchitect) and substitute your values.

## Log into Azure using the Azure CLI
### Steps:
1. Open a terminal (bash window) and run:
   ```bash
   az cloud show
   az cloud set --name AzureUSGovernment
   az login --use-device-code
   ```
2. Grab the URL from the terminal output and open it in an **incognito mode browser**.
   - This prevents cross-credential conflicts.
3. Copy the **device code** from the terminal output and paste it into the browser when prompted.
4. Log in using **FedRAMP GCC High subscription**.
5. Verify your account details:
   ```bash
   az account show
   ```
6. If you are part of multiple tenants, use:
   ```bash
   az login --tenant <tenantID>
   az account set --subscription <mysubscriptionID>
   ```

## Continue Deployment Steps
Follow the remaining deployment steps from:
[Azure Resource Provider Registration](https://github.com/microsoft/PubSec-Info-Assistant/blob/main/docs/deployment/deployment.md#azure-resource-provider-registration)
