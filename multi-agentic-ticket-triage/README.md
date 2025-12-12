# Use Case: Ticket Triage 

### Prerequisites   
Get a subscription to Microsoft Azure Cloud and create a resource group   

### Key Functions   
Prioritizes user's ticket, assigns team, and estimates efforts based on the content and complexity 

### Code Walkthrough 
* Create Azure AI Foundry project to provision gpt-4o and save its project endpoint   
* Complete authentication with the subscription credentials using Azure CLI   
Create AgentsClient instance to interact with the deployed agent using project endpoint with Azure AI Projects library   
Create three purpose-built agents from AgentsClient based on the ticket content :    
  * Priority Agent: prioritizes ticket into high/medium/low   
  * Team Agent: Assigns ticket into frontend/backend/infra/marketing   
  * Effort Agent: Estimates efforts into small/medium/large    
* Orchestrates the three agents by creating ConnectedAgentTool for each agent  
* Create a triage agent to process the ticket by passing three ConnectedAgentTool as tools   
* Create an agent thread to manage the context and agents  
* Submit the prompt to AgentsClient using thread id   
* Run the thread using the triage agent id and generate the response   

### Installation
Create a Python virtual environment to install the dependencies   
```
pip install python-dotenv azure-identity azure-ai-projects azure-ai-agents
```

### Sample Output
User Input: Users can’t reset their password from the mobile app.
<img width="934" height="462" alt="image" src="https://github.com/user-attachments/assets/7f21d5e5-c648-4f83-871f-b55710008fe8" />

