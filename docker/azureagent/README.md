# Azure docker agent user guide
To be able to run the Azure DevOps pipeline for this docker image needs to be built and run
(See following sections for details).


Make sure 
## Build docker agent image
Run command in directory containing the dockerfile:
```
docker build -t azureagent:latest .
```
## Start docker agent and connect to Azure DevOps

### Prerequisites
The command is dependent on that an access token has been created and that this user has access to add agents to the pool.
Details about what pool it's connected to, the agent name etc. can be found in `./start.sh`

### Start the docker agent
Run command:
```
docker run -e AZP_URL=https://dev.azure.com/hellowallin -e AZP_TOKEN=$(cat ~/.azure_conf/admin-token) -e AZP_AGENT_NAME=mydockeragent azureagent:latest
```
