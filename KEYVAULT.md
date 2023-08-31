
# Create the Service principal


 az ad sp create-for-rbac -n "api://<spName>" --role owner --scopes subscriptions/<subscriptionId>/resourceGroups/<resourceGroup>

  az ad sp create-for-rbac -n "api://spcv" --role owner --scopes subscriptions/6ea869be-bab3-4204-94c3-1fc677f7d2de/resourceGroups/democv

  {
  "appId": "5d7a08f6-30ff-43a4-86b1-e902c50fe0a0",
  "displayName": "api://spcv",
  "password": "O~Y8Q~PEux6ww-CisqpyJRcqcrSXUTZwxFBeYaC3",
  "tenant": "0f942ca0-ebef-4f26-80f8-f501d599ba90"
}

######################################################################

# Query the Object ID of the service principal
 az ad sp show --id <appId> --query id --out tsv

 az ad sp show --id 5d7a08f6-30ff-43a4-86b1-e902c50fe0a0 --query id --out tsv

2dca8a1b-c860-4e09-b0ec-b737051224c9

# Set permissions [ GET and LIST ] for the KEYVAULT   
 az keyvault set-policy -n <keyVaultName> --object-id <objectId> --secret-permissions get list

 az keyvault set-policy -n beescv01  --object-id 2dca8a1b-c860-4e09-b0ec-b737051224c9 --secret-permissions get list

 