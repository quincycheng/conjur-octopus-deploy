# Octopus Deploy Plugin for retrieving secrets from CyberArk Conjur

## Installation

1. Go to `Library` > `Steps Templates` > `Import`
2. Copy the content from the [cyberark-conjur-retrieve-a-secret.json](cyberark-conjur-retrieve-a-secret.json) file in this repo to the text field and click `Import`
3. Click on `Settings` tab, select `Current Logo` under `Logo` and choose the [cyberark-logo.png](cyberark-logo.png) file from this repo 

## Usage

1. In the process, click `Add Step`
2. Choose `Library Step Templates`, hover to `CyberArk Conjur - Retrieve a Secret` and click `Add`
3. Fill in the neccesary info. The following table summarize the usage of each parameters

Variable|Name|Description|Default Value
--------|----|-----------|-------------
CONJUR_ACCOUNT|Conjur Account|Conjur account that you are connecting to. This value is set during Conjur deployment|default
CONJUR_APPLIANCE_URL|Conjur Appliance URL|The URL of the Conjur instance you are connecting to. When connecting to DAP configured for high availability, this should be the URL of the master load balancer (if performing read and write operations) or the URL of a follower load balancer (if performing read-only operations)|
CONJUR_AUTHN_LOGIN|Conjur Authn Login|User/host identity|
CONJUR_AUTHN_API_KEY|Conjur Authn API Key|User/host API key|
VARIABLE_ID|Variable ID of Conjur Secret|Variable ID of Conjur Secret|
OUTPUT_NAME|Output Variable Name|This specifies the output variable.   For more details of output variables, please refer to https://octopus.com/docs/projects/variables/output-variables|Secret
STAY_SENSITIVE|Stay Sensitive|By default, the output variable will be saved as sensitive.   Only disabled this for debug purpose in non-production environment|True
FIX_SLASH_ENCODING|Fix Incorrect Slash Encoding|PowerShell may incorrectly decode slashes in URL.   If error 404 is returned, toggling this option may fix the issue|True

4. To get the secret in subsequent steps, we can make use of output variable.
For example, if your step is called `GetConjurSecret` and the output name is set to `Secret` (by default), the output variable will be `$OctopusParameters["Octopus.Action[GetConjurSecret].Output.Secret"`
