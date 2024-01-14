# aml
Azure Machine Learning

1001  brew update && brew install azure-cli
 1002  az version
 1003  az extension add -n ml -y
 1004  az login
 1005  az account set --subscription xxxxxxxxxxxxxxxxxxxxx
 1006  az group create --name aml-dev-rg --location eastus2
 1007  az ml workspace create -n aml-ws -g aml-dev-rg -l eastus2
 


1. An ARM template can be downloaded from GitHub and is found here: https://github.
com/Azure/azure-quickstart-templates/blob/master/quickstarts/
microsoft.machinelearningservices/machine-learning-workspace/
azuredeploy.json.
This template creates the following Azure services:
 Azure Storage Account
 Azure Key Vault
 Azure Application Insights
 Azure Container Registry
 An AML workspace
The example template has three required parameters:
 environment, where the resources will be created
 name, which is the name that we are giving to the AMLS workspace
 location, the Azure Region the resource will be deployed to
2. To deploy your template, you have to create a resource group first as follows:
az group create --name rg_name --location eastus2
3. Make sure your command prompt is opened to the location to which you downloaded the
azuredeploy.json file, and run the following command:
az deployment group create --name "exampledeployment"
--resource-group "rg_name" --template-file "azuredeploy.
json" --parameters name="uniquename" environment="dev"
location="eastus2"
It will take a few minutes for the workspace to be created.


Create a compute
az ml compute create --name computeinstance01 --size STANDARD_
D3_V2 --type ComputeInstance--resource-group aml-dev-rg
--workspace-name aml-ws

az ml compute create --name amlcomputeinstance01 --size STANDARD_D3_V2 --type ComputeInstance --resource-group aml-dev-rg --workspace-name aml-ws