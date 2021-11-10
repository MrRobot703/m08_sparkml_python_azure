# Spark Databricks ML

This a simple databricks ML application and is available on . First there are some necessary components that
need to be installed and provisioned:

* Azure account
* Azure Databricks service
* Terraform
* Auzer-cli
* Databricks cli (for providing secrets store, available only for pay-as-you-go subscription)

## Terraform
To initialize terraform backend infrastructure run:
```
terraform init
terraform apply
```
in the terraform/backend folder. 

Then run the same commands in the terraform folder.
Also, if you want to keep .trstate file somewhere private,
I suggest you to check out [terraform official guids](https://www.terraform.io/docs/language/settings/backends/azurerm.html)
for reference. The easiest so far approach is to authenticate via access_key with azure blob storage
and keep state file there.
And don't forget to run:
```
terraform destroy
```
after you finished with application so not to waste resource in the cloud.

## Azure cli and Databricks cli
You can download azure cli with homebrew if you are on mac. For other platforms please refer to
[microsoft guids](https://docs.microsoft.com/en-us/cli/azure/)

```
brew update && brew install azure-cli
az login
```

To download and install databricks cli you need python or pip package manager.
After python installation you can run following commands:

```
pip install databricks-cli
```
For more detailed guid please refer to [databricks docs](https://docs.databricks.com/dev-tools/cli/index.html)

## Start the application
Go into databricks notebook and upload sparksql_jvm_azure.dbc from notebooks folder.

To use databricks key vault for storing secrets there is a brilliant [video](https://www.youtube.com/watch?v=HZ00AznWvKc&list=PLEuWSnkVcdnatmaUOicGa3UJPUTR4bvKc&index=2&t=59s) 
on youtube that perfectly explains how to get started. Unfortunately this feature is only available for pay-as-you-go subscriptions.
