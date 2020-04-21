# ACI - Azure DevOps To GitHub Repository Migrator

Deploys the containerized version of the migrator to __Azure Container Instances__

This script, available as Windows Batch script and as Linux Bash script, uses the public image on Docker Hub: [n3wt0n/azdo2ghrepomigrator](https://hub.docker.com/r/n3wt0n/azdo2ghrepomigrator)

## Usage

Firs step is to __replace the environment variables__ values in the _deploy-aci.yaml_ file with your ones (see below).

Then just invoke:
- Windows: deployToACI.bat
- Linux / MacOS: deployToACI.sh

## Prerequisites

This script requires Azure CLI, which can be found here: [Install the Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest)

## Required Environment Variables

The container needs the following environment variables (and values) to run.  
Remember to change their values in the __deploy-aci.yaml_ file.

- __AZDOPAT__: __PAT__ (Personal Access Token) in Azure DevOps with the _Code > Read_ permissions granted
- __AZDOORG__: name of the Azure DevOps __Organization__ where your source repository resides (_the XXX in dev.azure.com/XXX or XXX.visualstudio.com_)
- __AZDOPRJ__: name of the Azure DevOps __Team Project__ where the source repository resides
- __AZDOREPO__: name of the Azure DevOps __Source Repository__ to migrate
- __GHPAT__: __PAT__ (Personal Access Token) in GitHub with the _repo (Full control)_ permmissions granted
- __GHUSER__: GitHub __Username__ with which you have created the destination repository
- __GHREPO__: name of the GitHub __Destination Repository__

> For instruction on how to generate a PAT in Azure DevOps, take a look at the [official documentation here](https://docs.microsoft.com/en-us/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate?view=azure-devops&tabs=preview-page#create-personal-access-tokens-to-authenticate-access)

> For instruction on how to generate a PAT in GitHub, take a look at the [official documentation here](https://help.github.com/en/github/authenticating-to-github/creating-a-personal-access-token-for-the-command-line#creating-a-token)

> Please note that the Destination Repo ___must be empty and not be initialized___.