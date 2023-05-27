>The certification validates your basic knowledge of cloud services and how those services are provided with Azure. Candidates should be able to demonstrate a fundamental knowledge of cloud concepts, along with Azure services, workloads, security, privacy, pricing, and support.

- Describe cloud concepts (25–30%)
- Describe Azure architecture and services (35–40%)
- Describe Azure management and governance (30–35%)

## Describe Cloud Concepts

### Cost
**Capital Expenditures** vs **Operating Expenses**.
- CapEx: Capital Expenditures are depreciated (decrease) over the useful life of the asset.
	- You cannot fully deduct the cost from the fiscal year the asset was paid for in.
- OpEx: Operating Expenses are deducted in the same year they are made.

### Types of Cloud Computing Services
- Infrastructure as a Service (IaaS).
	- You manage the OS, data and application.
	- Example: Azure Compute (VM's).
	- Common scenarios: Test and development, storage and backups or high performance computing.
- Platform as a Service (PaaS).
	- You manage the data and application.
	- Example: Azure Functions, Azure Cosmos DB.
	- Common scenarios: Analytics, BI, Development Framework to reduce coding.
- Software as a Service (SaaS).
	- You manage nothing. You use the software as-is.
	- Example: SharePoint.
	- Common scenarios: Gain access to software without maintaining it.

### Cloud Computing deployment models
- **Public Cloud**: Cloud serivce proved by thirt-party provider, hardware can be shared amongst mulitple clients.
- **Private Cloud**: Hardware is only used by a single company, wich often owns the hardware and datacenter.
- **Hybrid Cloud**: Combination between public and private cloud with automation and orchestration between the two.
- **Community Cloud**: Infrastructure is shared between several orgs from a specific community with commen concerns (security, compliance, jurisdiction, etc.)

## Describe Azure architecture and services
### Azure Architecture
- **Geographies**: Each Azure geography contains one or more regions and meets specific data residency and compliance requirements. This lets you keep your business-critical data and apps nearby on fault-tolerant, high-capacity networking infrastructure.
- **Regions**: Each Azure region features datacenters deployed within a latency-defined perimeter. They're connected through a dedicated regional low-latency network. This design ensures that Azure services within any region offer the best possible performance and security.
	- Choosing an Region ([Link: Interactive Map](https://infrastructuremap.microsoft.com/explore)):
		- Proximity to users
		- Service/Feature availability (not all new products are released on each region)
		- Data residency (for regulated industries)
- **Availability zones**: Azure availability zones are connected by a high-performance network with a round-trip latency of less than 2ms. They help your data stay synchronized and accessible when things go wrong. To ensure resiliency, a minimum of three separate availability zones are present in all availability zone-enabled regions.

### Azure Compute
- Azure Virtual Machine
	- Responsible for maintaince and updates.
	- Familiar hosting option for on-premises organisations.
	- For "Custom Of The Self" products.
- Containers in Azure
	- Packages application and dependencies
	- Need a container runtime on server
	- Azure PaaS container hosting options:
		- Azure Container Instances (ACI): host containers without maintaining and patching the enviroment. Single container per image. Intended for smaller applications.
		- Azure Kubernetes Service (AKS) simplifies deploying a managed Kubernetes cluster in Azure by offloading the operational overhead to Azure. As a hosted Kubernetes service, Azure handles critical tasks, like health monitoring and maintenance.
		- Azure Container Apps: serverless container manager for microservices. Powerd by Kubernetes but you have no access to the Kubernetes.
- Azure App Service
	- Platform-as-a-Service.
	- For: Web apps, Mobile apps, API's, WebJobs.
	- Runtimes (such as: .NET, Node.js) pre-installed.
	- Azure manages the underlying virutal machines.
	- Deployment slots for development, testing and production.
	- Automatic scaling.
- Azure [[Functions]]
	- Run code without a full application.
	- Triggers: timer, http, storage events

### Networking
- Virtual Network
	- Azure virtual network enables Azure resources to securely communicate with each other, the internet, and on-premises networks.
	- Diveded into multiple subnets.
		- Deploy (for example a VM) in a Subnet.
		- You control access to a Subnet via Network Security Groups (NSG).
	- VNets cannot communicate with other VNets.
		- Only via VNET peering

- On-premise to Azure:
	- VPN Gateway
		- Azure VPN Gateway is a service that uses a specific type of virtual network gateway to send encrypted traffic between an Azure virtual network and on-premises locations over the public Internet.
	- ExpressRoute
		- Uses a certified providers to connect to the Azure Edge.

- Azure DNS:
	- Azure DNS is a hosting service for DNS domains that provides name resolution by using Microsoft Azure infrastructure. By hosting your domains in Azure, you can manage your DNS records by using the same credentials, APIs, tools, and billing as your other Azure services.
	- Benefits:
		- Role-bases Access control
		- Activity logs
		- Global Network of DNS Servers
		- Support voor Private Domains (VNET)
			- Network interface that uses a private IP adres on your VNET
		- Alias Records to Azure Services

### Data Storage
- Categories of Data
	- Structured (such as; SQL)
	- Unstructured (such as; blob, file)
	- Semi-structured (such as; NoSQL, Cosmos DB)

- Azure Storage Accounts
	- Azure Storage Services
		- Blog Storage (Unstructured data)
		- File Storage (Same as Blob but supports SMB protocol for connecting to VM's)
		- Disk Storage (Stores the VM disks)
		- Table storage (Structured data in the form of NoSQL)
		- Queue Storage (Stores messages)
- Storage Account Types
	- General Purpose V2 (GPv2)
		- Blobs, Files, Tables, Queues
		- Recommended type
		- Most redundancy options
	- Premium Block Blob
		- Blobs only
		- High performance (SSD)
		- Locally-redundant and zone-redundant storage only
	- Premium File Share
		- Files only
		- High performance (SSD)
		- Locally-redundant and zone-redundant storage only
	- Premium Page Blob
		- Page blobs only
		- High performance (SSD)
		- Locally-redundant and zone-redundant storage only
- Redundancy
	- Locally Redundant Storage (LRS): replicated 3 times. Protects against server rack failure.
	- Zone-redundant Storage (ZRS): data in 3 seperate availabilty zones.
	- Geo-redudant Storage (GRS): Copies data to a single location in a seperate region.
	- Geo-zone-redundant Storage (GZRS): combination between zone and geo.
	- Read access (geo-)zone-redudant Storage (RA-GZRS): by default the geo will be manually selected by Azure in case of a disaster. With this type you have read only access to the paired region.
- Blob types
	- Block Blob: composed of blocks
	- Append Blob: can only append blocks, ideal for logs
	- Page blob: 8TB max blob, VM disks and databases
- Access Tiers (can be automated with blob lifecycle management)
	- Hot Tier: For frequent accessing data: (highest storage cost, lowest data access cost)
	- Cool Tier: For infrequent accessing data: (lower storage cost, higher data access cost)
	- Archive Tier: For rarely accessing data: (lowest storage cost, highest data access cost, data offline)
- Data Transfer Options
	- Azure Portal
	- Azure Storage Explorer
	- AzCopy (Command line tool)
	- PowerShell
	- Azure CLI
	- SDK's for multiple programming languages
	- Azure File Sync for on-premise infrastructure

- Databases
	- SQL Server on VM
	- Azure SQL Database (PaaS, managed by Microsoft)
	- Azure SQL Managed Instance
		- Deploy VM into own VNET
	- Managed Database Services
		- MySQL
		- PostreSQL
 
### Management and Monitoring
- Azure Resource Manager (ARM)
	- Azure Resource Manager is the deployment and management service for Azure. It provides a management layer that enables you to create, update, and delete resources in your Azure account. You use management features, like access control, locks, and tags, to secure and organize your resources after deployment.
	- Enables Resource Groups
	- Ability to create Templates for IaC
- ARM Templates
	- Combines IT operations and Development (DevOps)
	- Infrastructure now being managed as code
	- Can be stored an versioned in code repositories
	- Included in CI/CD pipelines
	- Template
		- JSON
		- Declarative syntax (write what you want)
		- Deploy from Azure Pipelines or GitHub Actions

- Azure Service Health
	- Azure Status: service outages across all of Azure.
	- Service Health: personalized service health of services and regions you use.
	- Resource Health: health of your deployed resources
- Azure Monitor
	- Metrics: numeric values, for alerting and detection of issues
	- Logs: records with resource-specific data, for troubelshooting and analysis
	- Application Insights:
		- For web apps
		- Runtime monitoring
- Azure Arc
	- Manage resources outside of Azure
	- Get; tags, searching and indexing, RBAC

## Describe Azure management and governance
### Azure Active Directory
- Authentication
	- The act of proving who or what something is
	- In Azure; Azure Active Directory
- Authoriztion
	- Granting the correct level of access to a resource or service
	- In Azure; Role Based Access Control (RBAC)

### Role Based Access Control
- Most used roles:
	- Owner: let's you manage everything including access to resources.
	- Contributor: lets you manage everything except granting access to resources.
	- Reader: lets you view everything but not make changes.


### Azure Security and Compliance
- Network Security Groups
	- Allow or deny inbound and outbound traffic.
	- Rules are ordered based on a number from 100 (first) tot 4096 (last).
	- Attatch to subnets or NIC.
	- When you create a inbound rule the outbound is automatically allowed.

- Azure Key Vault
	- Centralize the storage of application secrets.
	- Uses Hardware security modules (HSMs).
	- Enable loggin to monitor how an when secrets are being used.
	- Enables centralized administration of secrets.
	- Recomendations:
		- User separate key vault for each application or environment.
		- Take regular backups of your key vault.
		- Turn on loggin and set up alerts.
		- Turn on soft delete and purge protection.

### Azure Pricing and Support Options
- Subscriptions
	- Resource groups belong to a Subscription.
	- Elements:
		- Legel agreement.
		- A billing unit.
		- Logical boundry of scale.
		- First container created and administrative boundary.

- Planning and Managment of Costs:
	- Plans:
		- Free: $200 free used in 30 days.
		- Student: $100 free used in 12 months.
		- Pay-As-You-Go: Charges monthly for the services you used in that billing period.
		- Enterprise Agreement: Purchase Azure services and Microsoft software under a single agreement.
	- Purchase options:
		- Enterprise Agreement (EA):
			- Designed for very large organisations.
			- Premiere support and dadicated Azure resources.
			- Annual Azure spend commit.
			- Customized and deeply discounted Azure pricing.
		- Direct:
			- Bill from Microsoft.
			- Support trough Microsoft support plan.
		- Cloud Solution Provider (CSP):
			- Bill from CSP.
			- Support trough CSP.
	- Pricing calculator
		- Azure Pricing calculator: estimate the costst for Azure products.
		- Total Cost of Ownership (TCO): estimate the cost of migration and Cost of Ownership

- Support Options
	- Plans:
		- Basic (free):
			- 24x7 access to billing and subscription support.
			- Online self-help.
			- Azure products and services documentation/whitepapers.
			- Support forms.
		- Developer:
			- E-mail only
		- Standard.
		- Professional Direct.
		- Premier.

- SLA
	- Commitment between a service provider and its internal or external customers.
	- Azure SLA: uptime and connectivity commitments. Those can be different per service.

- Service Lifecycle
	- Azure Previews: for evaluating products while in development (early access).
