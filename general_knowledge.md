# General Knowledge

- A **task group** allows you to encapsulate a sequence of tasks, already defined in a build or a release pipeline, into a single reusable task that can be added to a build or release pipeline, just like any other task.
  - Task groups **are not supported in YAML pipelines**. Instead, in that case you can use templates
- parallel jobs:
  - ds split data in multiple chinks
  - devops: deploy to multiple stages at the same time?

- when would you choose a self hosted agent instead of a microsoft one?
  - <https://www.youtube.com/watch?v=FEK8fZCjlQY>

- given that you have some secrets in azure key vault, when would you use github secrets instead of key\value stored in azure key vault?
  - you always should you use kv for production

- vm vs containers

## Topic 1

- meld vs sonarqube vs owasp zap
  - Mend (formerly WhiteSource) is the leader in continuous open source software security and compliance management.
    - create a build task and use the WhiteSource Bolt service
  - Black Duck helps organizations identify and mitigate open source security, license compliance and code-quality risks across application and container portfolios
  - The Microsoft Test & Feedback extension:
    - *Anyone can now test web apps and give feedback, all directly from the browser on any platform*
    - Assign Stakeholders to users with no license or subscriptions who need access to a limited set of features.
    - Assign Basic to users with a TFS CAL, with a Visual Studio Professional subscription, and to users for whom you are paying for Azure Boards & Repos in an organization
  - Microsoft Visual Studio App Center integration:
    - Collect crash reports for issue analysis.
    - Distribute beta releases to your testers.
    - Get user feedback on the functionality of new apps.
  - OWASP ZAP: automatically find security vulnerability in a web appliction
- azure load testing

- lead time, cycle time:
  <https://docs.microsoft.com/en-us/azure/devops/report/dashboards/cycle-time-and-lead-time?view=vsts>
  - Lead time measures the total time elapsed from the creation of work items to their completion.
  - Cycle time measures the time it takes for your team to complete work items once they begin actively working on them.
- **Static code analysis** tools in the IDE provide the first line of defense to help ensure that security vulnerabilities are not introduced into the CI/CD process.
- Database Import Service in Azure Devops Services to migrate Team Foundation Server 2013 (TFS 2013) to Azure DevOps

- work methodologies:
  - Choose CMMI when your team follows more formal project methods that require a framework for process improvement and an auditable record of
    decisions. With this process, you can track requirements, change requests, risks, and reviews.
  - Choose Basic when your team wants the simplest model that uses Issues, Tasks, and Epics to track work.
  - Choose Agile: This process works great if you want to track user stories and (optionally) bugs on the Kanban board, or track bugs and tasks on
    the taskboard.
  - Choose Scrum: This process works great if you want to track product backlog items (PBIs) and bugs on the Kanban board, or break PBIs and bugs
    down into tasks on the taskboard.

- configuration drift:
  - Register-AzureRmAutomationDscNode with ApplyAndAutocorrect
- version control system:
  - for source code to be stored on a managed Windows server located on the company network use **GitHub Enterprise**

- when npm install you **do not** install dev dependencies unless you specify the **--dev** flag
- blue/green  (or red/black) deployment allow you to roll back in the shortest time
- To deploy an application to a number of Azure virtual machines group them in a **deployment resource group**
  - *When authoring an Azure Pipelines or TFS Release pipeline, you can **specify the deployment targets for a job using a deployment group**.
If the target machines are Azure VMs, you can quickly and easily prepare them by installing the Azure Pipelines Agent Azure VM extension on each of the VMs, or by using the Azure Resource Group Deployment task in your release pipeline to create a deployment group dynamically*

- when using Terraform you may want to use:
  - **Yeoman**: makes it easy to create Terraform modules
  - **Terratest**: provides a collection of helper functions and patterns for common infrastructure testing tasks, like making HTTP requests and using SSH to access a specific virtual machine

- when deploying artifacts use **feed views** to make sure that the release of packages that are in development is restricted

- for a new application that will be deployed to a number of Windows Server 2016 Azure virtual machines use:
  - Azure Resource Manager templates
  - The Custom Script Extension for Windows

- monitoring and alerting:
  - Azure Security Center:
    - has the  Compute & apps which allows to view recommendations with regards to the security of the web apps and functions
  - Azure Application Insights:
    - tell you about any performance issues and exceptions, and help you find and diagnose the root causes
    - three types of Application Insights availability tests:
      - URL ping test: a simple test that you can create in the Azure portal. It sends web requests to your application at regular intervals from points around the world. It can alert you if your application isn't responding, or if it responds too slowly
    - uses Kusto Query Language (KQL)
    - **Smart Detection automatically** warns you of potential performance problems and failure anomalies in your web application. It performs proactive analysis of the telemetry that your app sends to Application Insights. If there is a sudden rise in failure rates, or abnormal patterns in client or server performance, you get an alert
  - Azure SQL Database Intelligent Insights
    - uses Kusto Query Language (KQL)
  - Data analysis in Azure SQL:
    - uses Kusto Query Language (KQL)
  - use Logic Apps to customize your alert notifications.

## Topic 2

- to increase the logging level when the web app exceeds normal usage patterns use:
  - an Azure Monitor alert that has a dynamic threshold
  - Azure Automation runbooks by using action groups or by using classic alerts to automate tasks based on alerts
- in Azure Kubernetes Service (AKS) pod:
  - livenessProbe: Azure Container Instances supports liveness probes so that you can configure your containers within your container group to restart if critical functionality is not working.
  - readinessProbe: Azure Container Instances supports readiness probes to include configurations so that your container can't be accessed under certain conditions.ons

- Azure Monitor query (Kusto):
  - identify the distinct event IDs of each virtual machine :
  use make_list to pivot data by the order of values in a specific column

      ``` KQL
      | where TimeGenerated > ago(12h)
      | order by TimeGenerated desc
      | summarize make_list(EventID) by Computer
      ```

  - **request** metric reflects the number of incoming server requests that were received by your web application.

      ```KQL
      requests
      | summarize sum(itemCount) by bin(timestamp, 5m)
      | render barchart
      ```

- Azure Pipelines with Microsoft Teams
    1. In Microsoft Teams, go to the Apps store, search for Azure Pipelines, and then select Azure Pipelines.
    2. Select the Open dropdown arrow, and then select Add to a team.
    3. Select or enter your team name, and then choose Set up a bot.
    4. In the Teams conversation pane, enter ```@azurePipelines signin```
    5. Select Sign in and complete authentication to Azure Pipelines.
    6. Use the following commands to monitor all pipelines in a project or only specific pipelines.
       - To start monitoring all pipelines in a project, use the following command inside a channel:
       ```@azure pipelines subscribe [project url]```
       - Subscribe to a pipeline or all pipelines in a project to receive notifications:
       ```@azure pipelines subscribe [pipeline url/ project url]```

- Use the Dependency agent if you need to use the Map feature VM insights or the Service Map solution.
  Note: Consider the following when using the Dependency agent:
  The Dependency agent requires the Log Analytics agent to be installed on the same machine.

- To configure verbose logs for all runs, you can add a variable named **system.debug** and set its value to **true**.

## Topic 3

- to send an SMS alert when scheduled maintenance is planned for the Azure services
  - Create an Azure Service Health alert.
  - Create and configure an action group.

- to ensure that an email alert is generated whenever VMSS1 scales in or out
  - **DO** From Azure Monitor, create an action group
  - **DO NOT** configure the autoscale settings
  - **DO NOT** configure the Notifications settings
  - **DO NOT** configure the Service hooks settings
  
- Smart Detection of failure anomalies takes 24 hours to learn the normal behavior of your app, before it is switched on and can send alerts

- process to choose:
  - Scrum. This process works great if you want to track product backlog items (PBIs) and bugs on the Kanban board, or break PBIs and bugs down into tasks on the taskboard.
  - Agile. This process works great if you want to track user stories and (optionally) bugs on the Kanban board, or track bugs and tasks on the taskboard.
  - CMMI. This process works great when your team follows more formal project methods that require a framework for process improvement and an auditable record of decisions.
    With this process, you can track requirements, change requests, risks, and reviews
  product backlog --> scrum
  user stories --> Agile
  track changes --> CMMI

- to restart an Azure container instance named ACI1 when a containerized app named App1 is build on it:
  - add a readiness probe to the YAML configuration of App1.

- Azure Platform as a Service (PaaS) resources, like Azure SQL and Web Sites (Web Apps), can emit performance metrics data natively to Log Analytics.

- to implement a health check of a web app
  - you can also use health extension to monitor the application health of each instance in your scale set and perform instance repairs using automatic instance repairs

- You can mark or unmark a test as flaky based on analysis or context, by choosing Flaky and Clear Flaky tests included in test pass percentage. This will exclude flaky test (i.e. those who fail because an API timeout) from the test pass percentage

- to prevent the configuration of the project from changing over time
  - implement **Continuous Assurance** for the project

- Azure Security Center:
  - Azure Security Center includes Azure-native, advanced threat protection for Azure Key Vault, providing an additional layer of security intelligence
  - When Security Center discovers a connected VM without a vulnerability assessment solution deployed, it provides the security recommendation "A vulnerability assessment solution should be enabled on your virtual machines

- Azure Container Instances:
  - For containerized applications that serve traffic, you might want to verify that your container is ready to handle incoming requests. supports **readiness probes** to include configurations so that your container can't be accessed under certain condition

- configure an Azure Monitor alert that is triggered when WebApp1 generates an error. You need to configure the alert to forward details of the error to a third-party system:
  1. Create an Azure logic app.
  2. Select the HTTP request trigger.
  3. Updated the action group in Azure Monitor.

- Dependency Tracker
  - You generate a risk graph for the project
    - in the risk graph to identify the number of dependencies and the risk level of the project
      - Number of dependencies: Link Width
      - Risk Level: Link Color

## Topic 4

- to configure password stored in Azure Key Vault from Azure Data Factory to connect to a Azure SQL Database, while using the principle of least privilege:
  - Permision type: Secret
  - Access method: Access Policy

- to setup MFA in Azure AD
  - set up conditional access

- to register a self hosted linux agent:
  - provide a personal access token (PAT)

- to authenticate users of a asp.net app by using Azure AD:
  - create an app registration in Azure AD
  
- to connect to an Azure DevOps organization while supporting authentication from Git
  - use a PAT in Azure DevOps

- to assess the security of the web apps and the functions:
  - use Compute & apps in Azure Security Center

- a solution to minimize the likelihood that infrastructure credentials will be leaked
  - Add a PowerShell task to the pipeline and run Set-AzureKeyVaultSecret.

- to bypass policy requirements so you can push changes to the branch directly or complete a pull request even if branch policies are not satisfied
  - From the Security settings of the branch, modify the access control for the user.

- to provision an Azure Kubernetes Services (AKS) cluster in Subscription1 and set the permissions for the cluster by using RBAC roles that reference the identities to an Azure Active Directory tenant named contoso.com
  1. Create an AKS cluster
  2. a system-assigned managed identity
  3. a RBAC binding

- to configure a service endpoint for accessing Azure Key Vault secrets. The solution must meet the following requirements:
  - Ensure that the secrets are retrieved by Azure DevOps.
  - Avoid persisting credentials and tokens in Azure DevOps.
    - Azure Pipelines service connection
    - Managed Service Identity Authentication

- to link GitHub commits, pull requests, and issues to the work items of Project1 while using OAuth-based authentication
  1. From Developer settings in GitHub Enterprise Server, register a new OAuth app.
  2. From Organization settings in Azure DevOps, add an OAuth configuration
  3. From Project Settings in Azure DevOps, add a GitHub connection.

- You are configuring an Azure DevOps deployment pipeline. The deployed application will authenticate to a web service by using a secret stored in an Azure key vault. You need to use the secret in the deployment pipeline.
  1. Create a service principal in Azure Active Directory (Azure AD).
  2. Configure an access policy in the key vault.
  3. Add an Azure Resource Manager service connection to the pipeline

- You can check **policy compliance** with **gates**.
  You can extend the approval process for the release by adding a gate. Gates allow you to configure automated calls to external services, where the results are used to approve or reject a deployment.

- provisioning and connecting to AKS so that RBAC is enabled and uses a custom service principal
  1. az acr create
  2. az ad sp create-for-rbac
  3. kubectl create

- to distribute an app for iOS from App Center
  - you must have a .p12 certificate

- given an Azure DevOps project1 with two pipelines. To make sure that only pipeline1 can deploy to webapp1
  - Create a service principal in Azure Active Directory
  - create a service connection in project1
  - in pipeline1 authorize the service connection

- The NuGet package is in a feed that requires authentication. You need to ensure that the project can restore the NuGet package automatically
  - an Azure Artifacts Credential Provider

- to configure Azure Monitor to use the key to encrypt log data while having an encryption key
  - Step 1: Create an Azure Key vault and store the key.
  - Step 2: Create an Azure Monitor Logs dedicate cluster that has a system-assigned managed identity
  - Step 3: Grant the system-assigned managed Identity Key permissions for the key vault.
  - Step 4: Configure the key vault properties for the cluster.
  - Step 5: Link the Log Analytics workspace to the cluster

- You have an Azure Key Vault that contains an encryption key named key1. You plan to create a Log Analytics workspace that will store logging data. You need to encrypt the workspace by using key1.
  - Step 1: Enable soft delete for the key vault.
  - Step 2: Create a Log Analytics cluster.
  - Step 3: Grant permissions to the key vault.
  - Step 4: Link workspace

## Topic 5
