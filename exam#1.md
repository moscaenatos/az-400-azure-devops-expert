# Exam Practice #1 - Table of contents

    Objectives Percentage (Corrects/Number Questions)
    Configure processes and communications 28.57 % (2/7)
    Design and implement source control 27.27 % (3/11)
    Design and implement build and release pipelines 55 % (11/20)
    Develop a security and compliance plan 71.43 % (5/7)
    Implement an instrumentation strategy 20 % (1/5)
    Customer Score: 44% - FAIL - 22/50 (0 Unanswered)

- [Exam Practice #1 - Table of contents](#exam-practice-1---table-of-contents)
  - [Configure processes and communications](#configure-processes-and-communications)
    - [Configure activity traceability and flow of work](#configure-activity-traceability-and-flow-of-work)
    - [Configure collaboration and communication](#configure-collaboration-and-communication)
  - [Design and implement source control](#design-and-implement-source-control)
    - [Design and implement a source control strategy](#design-and-implement-a-source-control-strategy)
    - [Plan and implement branching strategies for the source code](#plan-and-implement-branching-strategies-for-the-source-code)
    - [Configure and manage repositories](#configure-and-manage-repositories)
  - [Design and implement build and release pipelines](#design-and-implement-build-and-release-pipelines)
    - [Design and implement pipeline automation](#design-and-implement-pipeline-automation)
    - [Design and implement a package management strategy](#design-and-implement-a-package-management-strategy)
    - [Design and implement pipelines](#design-and-implement-pipelines)
    - [Design and implement deployments](#design-and-implement-deployments)
    - [Design and implement infrastructure as code (IaC)](#design-and-implement-infrastructure-as-code-iac)
    - [Maintain pipelines](#maintain-pipelines)
  - [Develop a security and compliance plan](#develop-a-security-and-compliance-plan)
    - [Design and implement a strategy for managing sensitive information in automation](#design-and-implement-a-strategy-for-managing-sensitive-information-in-automation)
    - [Automate security and compliance scanning](#automate-security-and-compliance-scanning)
  - [Implement an instrumentation strategy](#implement-an-instrumentation-strategy)
    - [Configure monitoring for a DevOps environment](#configure-monitoring-for-a-devops-environment)
    - [Analyze metrics](#analyze-metrics)

## Configure processes and communications

- To link commits with the work items:
  - Include AB# followed by the work item id in every commit message
- Lead time of a work item is defined as the time taken to close a work item after it was created
- Personal access token and Github.com user acconuts are authentication methods that allows to link Github comits and pull request with Azure Board

### Configure activity traceability and flow of work

- Deployment status widget shows the deployment status and the test pass rate across multiple enviroments for a recent set of builds on a deployment pipeline
- Project Administrator secuirty group allows to edit or create a team project wiki

### Configure collaboration and communication

## Design and implement source control

### Design and implement a source control strategy

- Use git to allow each devleoper to have a local copy of the source repository. This allows them to work offline
- if you get git@github.com: Permission denied it means you do not have a valid SSH key set up

### Plan and implement branching strategies for the source code

- set the minimum number of reviewers to three
- Case study :
  - You should perform the following actions in order:
      1. Create a repository.
      2. Create the main branch.
      3. Create a build pipeline.
      4. Enable the continuous integration trigger.
  - To ensure that only changes from a reviewed pull requests are added to the main branch:
    - Add the Tech Lead group as automatic reviewers
    - Add a Build validation policy
  - Rebase and fast-forward:
    - This merge type creates a linera history by replacing the source branch commits to the target without a merge commit
  - To publish the tags for commits:
    1. git tag
    2. git push origin

### Configure and manage repositories

- acceptable name for git tags are:
  - name which consists of less tha 40 hexadecimal characters
  - A name withouth ASCII control characters
  - A name length which does not exceed 250 ASCII characters

## Design and implement build and release pipelines

### Design and implement pipeline automation

- to enstablish an authentication method that enables you to use Azure CLI in a GitHub Actions workflow:
  - Azure login action with OpenId Connect (OIDC)
  - Azure login action with a service principal secret

- To author advanced queries in Kusto Query Language in Azure Devops:
  - Azure Data Explorer

### Design and implement a package management strategy

- A valid artifact management tool for a private Maven library are:
  - Azure Artifacts
  - Nexus repository
  - Artifactory

- To integrate a release pipeline with an Azure Artifacts feed managed by another team which sent you a settings.xml file with Maven credentials
    You should perform the following actions:

    1. Upload the settings.xml file in Azure Pipelines library
    1. Add the credentials in the package pom.xml file.
    1. Commit the settings.xml file in the package code repository.
    1. Include the feed repository configuration in the package pom.xml file
    1. Add a Download secure file task in the pipeline
    1. Copy the settings.xml file to the ~/.m2 directory in the pipeline.

- To publish a private SDK in a Node.js package registry:
    1. Create a new feed in Azure Artifacts to store builds
    2. Configure a .npmrc file in the root of the Git repo.
    3. Run npm publish during the build pipeline

### Design and implement pipelines

### Design and implement deployments

- To support gradual availability of each stage to users during deployment:
  - Traffic Manager
  - Deployment slots

- To deploy an application using progressive exposure deployments:
  - Deployment rings
  - Feature flags

- To configure a release pipeline to deploy an application that runs 20 VM instances through a deployment group

  1. Create a deployment group in Azure DevOps.
  2. Install the deployment group agent extension in the scale set.
  3. Configure the agent extension with a PAT.

### Design and implement infrastructure as code (IaC)

### Maintain pipelines

- To analyze and understand why tasks in a pipeline are failing while using Pipeline Analytics:
  - The Pipeline pass rate report

## Develop a security and compliance plan

### Design and implement a strategy for managing sensitive information in automation

- You should use an Azure Key Vault secret for ProjectA.
  A secure parameter value in ARM templates contains the reference to a Key Vault secret read by ARM during the template deployment time inside Azure.
- You should use a GitHub Actions secret for ProjectB. You can store secrets for a GitHub repository under the Environment secrets settings.
  You can use these secrets directly from GitHub Actions using the ${{ secrets.SECRET_NAME }} syntax in your pipeline, without needing to include extra steps.
- You should use an Azure Pipeline secret variable for ProjectC. You can set variables in Azure Pipelines containing secret values that are encrypted at rest.
  After you set a secret variable, you can access this secret in your pipeline tasks without including extra steps.

### Automate security and compliance scanning

- to make sure that the company is using software with approved terms and conditions using Mend:
  - Define a white list of licenses to approve
  - Define a black list of licenses to reject

## Implement an instrumentation strategy

### Configure monitoring for a DevOps environment

- To prevent a deployment to start when the CPU usage metric in the staging environment is above a certain percentage:
  1. Create an alert rule in Azure Monitor.
  2. Add a Query Azure Monitor alerts task in the staging post-deployment gate.
  3. Configure the task with an alert rule filter type.
  4. Select the alert rule.

- to integrate the platform monitoring tools to centralize the solution's operating system logs in Azure Monitor and also use VM Insights:
  - You should use the Log Analytics agent.
  - This agent allows you to collect telemetry from Windows and Linux operating systems and send the data to a Log Analytics workspace in Azure Monitor. You can deploy this agent in any public cloud and on-premises virtual machine. With the Log Analytics agent, you can also enable VM Insights

- Restart Web Apps is one of the possible administrative activities in an App Service plan, but the alert condition is configured for failed events only.

### Analyze metrics

- To send traces and eventually all application metrics to Azure Monitor Application Insights for analysis while using perform continuous monitoring of your DevOps release pipeline throughout the software development lifecycle.

  - You should implement the Azure Monitor OpenTelemetry Exporter component as this sends traces, metrics and logs to Azure Monitor Application Insights. Azure Monitor OpenTelemetry Exporter allows distributed tracing for Azure DevOps release pipelines. These traces are then sent to Azure App Insights for further review and analysis. At the time of writing, OpenTelemetry Exporter is in preview
