## Use Case: Ticket Triage   

### Learning Objective    
Create a multi-agentic workflow with purpose-built agents for prioritizing user's ticket, assigning team, and estimating efforts based on the ticket content      

### Prerequisites   
* Create a [free account on Azure](https://azure.microsoft.com/en-us/pricing/purchase-options/azure-account) to build AI solutions using Azure AI services
* Install [Azure CLI](https://learn.microsoft.com/en-us/cli/azure/?view=azure-cli-latest) to enable secured access to Azure resources   

### Code Walkthrough 
* Create Azure AI Foundry project on [Microsoft Foundry](https://ai.azure.com/) to provision a LLM (gpt-4o)     
* Create AgentsClient instance to interact with the deployed agent using project endpoint with Azure AI Projects library   
* Create three purpose-built agents from AgentsClient based on the ticket content :    
  * Priority Agent: prioritizes ticket into high/medium/low   
  * Team Agent: Assigns ticket into frontend/backend/infra/marketing   
  * Effort Agent: Estimates efforts into small/medium/large    
* Orchestrates the three agents by creating ConnectedAgentTool for each agent  
* Create a triage agent to process the ticket by passing three ConnectedAgentTool as tools   
* Create an agent thread to manage the context and agents  
* Submit the prompt to AgentsClient using thread id   
* Run the thread using the triage agent id and generate the response   

Refer to this [link](https://learn.microsoft.com/en-in/training/modules/develop-multi-agent-azure-ai-foundry/) for more information on creating collaborative agentic workflow using Foundry Agent Services   

### Installation
Create a Python virtual environment to install the dependencies   
```
pip install python-dotenv azure-identity azure-ai-projects azure-ai-agents
```

### Running Application   
* Open a Windows command-line interface or Linux terminal and run the following command to complete authentication with the subscription credentials   
```
az login
```
* Run the application
```
python triage_agent.py
```
### Sample Output
User Input: Users can’t reset their password from the mobile app.
<img width="934" height="462" alt="image" src="https://github.com/user-attachments/assets/7f21d5e5-c648-4f83-871f-b55710008fe8" />

