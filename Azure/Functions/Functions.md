[[Azure]] Functions is a serverless solution that allows you to write less code, maintain less infrastructure, and save on costs. Instead of worrying about deploying and maintaining servers, the cloud infrastructure provides all the up-to-date resources needed to keep your applications running. Azure functions are grouped in a Azure Function App, that are developed, deployed and hosted as a group.

Serverless:
- Delegate server managment responsibility to the cloud provider.
- Automatic scaling to meet demand.
- Billed only while your code is running.

Choice of programming languages:
- C#
- Java
- JavaScript
- Python
- PowerShell

Hosting Choices (Functions usually run in a "Service plan" on Azure [[App Service]]):
- Consumption Plan
	- Serverless
	- Automatic scale
	- 5 minute time limit
- App Service Plan
	- Traditional pricing model
- Premium Plan
	- Speed
	- Security
	- Reserved instances
- Docker container
	- On premise
	- In any cloud
- Locally
	- Development
	- Testing

## Triggers
Azure Functions has exactly one trigger. The trigger is the event that causes the function to run. The following triggers are available:
- HTTP Request Trigger: use for APIs and webhooks.
- Timer Trigger: use for scheduled tasks.
- Queue Trigger: run in response to a message on a queue.
- Cosmos DB Trigger: run when a document is created or updated.
- Blog Trigger: run when a new file is uploaded to Blob Storage.

#### HTTP Request
- Implement APIs or respond to webhooks.
- Customization:
	- HTTP Methods: e.g. GET or POST.
	- Route: determine the call URL.
- Secured via authorization key:
	- Anonymous: no key required.
	- Function: key per function.
	- Admin: key per function app.

## Input and output bindings
Text