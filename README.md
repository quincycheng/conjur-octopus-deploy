# Octopus Deploy Step Template for retrieving secrets from CyberArk Conjur

This step template can now be installed directly from Octopus Deploy, both Cloud & Server version!

Octopus Library: https://library.octopus.com/step-templates/eafe9740-1008-4375-9e82-0d193109b669/actiontemplate-cyberark-conjur-retrieve-a-secret 

![install_small](https://user-images.githubusercontent.com/4685314/111723010-e0efff80-889d-11eb-80cb-fd5f9f3df038.gif)


## Usage

1. In the process or runbook, click `Add Step`
2. Search for `CyberArk` or `Conjur`
3. If you haven't installed the template, hover to `CyberArk Conjur - Retrieve a Secret` under `Community Contributed Step Templates` and click `Add`.   If you have installed the step template, hover to `CyberArk Conjur - Retrieve a Secret` under `Installed Step Template` and click `Add`
5. Fill in the neccesary info. The following table summarize the usage of each parameters

Variable|Name|Description|Default Value
--------|----|-----------|-------------
CONJUR_ACCOUNT|Conjur Account|Conjur account that you are connecting to. This value is set during Conjur deployment|default
CONJUR_APPLIANCE_URL|Conjur Appliance URL|The URL of the Conjur instance you are connecting to. When connecting to DAP configured for high availability, this should be the URL of the master load balancer (if performing read and write operations) or the URL of a follower load balancer (if performing read-only operations)|
CONJUR_AUTHN_LOGIN|Conjur Authn Login|User/host identity|
CONJUR_AUTHN_API_KEY|Conjur Authn API Key|User/host API key|
CONJUR_VARIABLE_ID|Variable ID of Conjur Secret|Variable ID of Conjur Secret|
CONJUR_OUTPUT_NAME|Output Variable Name|This specifies the output variable.   For more details of output variables, please refer to https://octopus.com/docs/projects/variables/output-variables|Secret
CONJUR_STAY_SENSITIVE|Stay Sensitive|By default, the output variable will be saved as sensitive.   Only disabled this for debug purpose in non-production environment|True
CONJUR_FIX_SLASH_ENCODING|Fix Incorrect Slash Encoding|PowerShell may incorrectly decode slashes in URL.   If error 404 is returned, toggling this option may fix the issue|True

4. To get the secret in subsequent steps, we can make use of output variable.
For example, if your step is called `GetConjurSecret` and the output name is set to `Secret` (by default), the output variable will be `$OctopusParameters["Octopus.Action[GetConjurSecret].Output.Secret`
