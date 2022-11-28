# Exam Practice #2 - Table of contents

    Objectives Percentage (Corrects/Number Questions)
    Configure processes and communications 42.86 % (3/7)
    Design and implement source control 84.62 % (11/13)
    Design and implement build and release pipelines 45 % (9/20)
    Develop a security and compliance plan 40 % (2/5)
    Implement an instrumentation strategy 40 % (2/5)
    Customer Score: 54% - FAIL - 27/50 (1 Unanswered)

- [Exam Practice #2 - Table of contents](#exam-practice-2---table-of-contents)
  - [Configure processes and communications](#configure-processes-and-communications)
    - [Configure activity traceability and flow of work](#configure-activity-traceability-and-flow-of-work)
    - [Configure collaboration and communication](#configure-collaboration-and-communication)
  - [Design and implement source control](#design-and-implement-source-control)
    - [Design and implement a source control strategy](#design-and-implement-a-source-control-strategy)
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

### Configure activity traceability and flow of work

- To analyze code changes to identify potential root of a test failure with RTM
  - use Source traceability

### Configure collaboration and communication

- use URL with HTTPS endpoints to invoke endpoints securely
- the ignore-for-release labels excludes a pull reuqest from appearing in the automatically generated release notes
- use the evaluationTracing diagnostic setting to retrieve details pertaining to event matching

## Design and implement source control

### Design and implement a source control strategy

- To improve performance of execution of git commands by using Scalar:
  - You should **disable** **auto-GC by setting gc.auto=0**. This prevents the Git commands from being blocked by maintenance.
  - You should **disable** writing the commit-graph during get fetch by setting fetch.**writeCommitGraph=false**. This is an important step since Scalar ensures that the fetch step runs git fetch about once an hour only. This saves time since this ensures that the download of new objects happen when you are not waiting for your command to complete execution.
  - You should **disable status.aheadBehind=false** to remove the calculation of how far ahead or behind your branch is compared to the remote-tracking branch
  - You should **use the core.fsmonitor hook to Watchman**. The hooks folder in the Dot Git Folder (.git) has a few script files inside it that are referred to as Git Hook Scripts.

## Design and implement build and release pipelines

### Design and implement pipeline automation

- ```yaml
    coverage:
        status:
            comments: on
            diff:
                target: 50%
    ```

  - the details about coverage for each file changed will be posted as a pull request comment
  - The file provides code coverage only for the lines changed in a pull request
  - 50% **do not** represents the threshold value for a succesful full coverage status to be posted

- If you see the phrase, "You don't have sufficient permission to do XYZ", then this is an issue that is being caused by either incorrect or inadequate permission(s) for a user to perform a specific action.
  - Create releases
  - Manage releases
  - Edit release stage
  - Manage deployments

### Design and implement a package management strategy

- deprecating a feature is a **minor** version change
- add a retention policy to remove old packages version to improve a Nuget client performance while minimizing administrative overhead

### Design and implement pipelines

- Pre-deployment trigger question
  - Qa stage is triggered **after Release**
  - Produciton stage is triggered **after Stage**
  - Development is **Manual Only**

### Design and implement deployments

- To implment a delivery strategy to use feature flags
  1. Design the feature’s functionality.
  2. Create a release strategy.
  3. Build the feature.
  4. Test the feature.
  5. Release the feature

- to implement a release pipeline for a blue-green deployment strategy using deployment slots
  1. Create a new deployment slot named staging in Azure App Service.
  2. Add a staging stage in the Release pipeline.
  3. Create a task to deploy the application to the staging slot.
  4. Add a production stage in the Release pipeline.
  5. Create an App Service Manage task to swap the staging slot to production.

### Design and implement infrastructure as code (IaC)

- To recommend an IaC solution to ensure that Infrastructure as a Service (IaaS) resources have a specific configuration, such as which services are installed in the virtual machine (VM) and to minimize configuration drift
  - You should recommend Chef Infra. Chef Infra is an IaC automation solution that you can use to manage how your infrastructure is configured according to your policies. The Chef server stores all configuration definitions for your infrastructure in cookbooks. Each node managed by this Chef server has a Chef Client agent installed. The agent ensures that the node complies with the configuration stored on the server and corrects or updates the node configuration if necessary

  - You recommend PowerShell DSC. PowerShell DSC is a solution that configures resources based on simple configuration files. You can use DSC configurations in push and pull modes. Both modes create a local configuration state in the target machines called Local Configuration Manager (LCM) that determines which configurations should be applied. In pull mode, the LCM is configured to regularly check a pull service for newer configurations, ensuring that the IaaS resource is up-to-date with the desired configurations. It is recommended to use Azure Automation as a managed pull service

### Maintain pipelines

- use Microsoft hosted agent for public and open source project with less than 10 parallel builds. Use self-hosted for unlimited parallel builds and unlimited build minutes per month
- Flaky testing is a feature available for Azure DevOps Services and it enables to perform automatic detection of flaky tests. Once a test is marked as flaky the data is available for all Azure pipelines for a given branch

## Develop a security and compliance plan

### Design and implement a strategy for managing sensitive information in automation

- to automate the secret rotation for this database while keeping the password available.
  1. Create an Azure function that is triggered by the Key vault Near Expiry event.
  2. Create a new password and set a new secret version in Key Vault.
  3. Update the database with the new passwor

- to use Azure Resource Manager (ARM) templates to create the Azure VM via a build pipeline. These templates will need to reference secrets stored in Azure Key Vault during the
deployment

    ```json
    "resources": [
        {
        "apiVersion": "2020-10-01",
        "name": "dynamicSecret",
        "type": "**Microsoft.Resources/deployments**",
        "properties": {
            "mode": "Incremental",
            "templateLink": {
                "contentVersion": "1.0.0.0",
                "uri": "some-template-link-url"
                },
                "parameters": {
                    "adminPassword": {
                    "reference": {
                        "**keyVault**": {
                            "id": "[parameters('id')]"
                            },
                            "secretName": "[parameters('secretName')]"
                            }
                        }
                    }
            }
        }
    ]
    ```

### Automate security and compliance scanning

- to integrate this new project pipeline with SonarQube
  - You should generate an authentication token in SonarQube. That token will be saved when you create a service endpoint in Azure DevOps and will link the SonarQube server with Azure DevOps.
  - You may also need to install the SonarQube extension in the organization once via the Marketplace to enable SonarQube-related tasks for pipelines.
  - You should not install the SonarQube extension in your project. Marketplace extensions for Azure DevOps are installed at the organization level only

## Implement an instrumentation strategy

### Configure monitoring for a DevOps environment

- use the Log Analytics agent to collect telemetry from Windows and Linux OS and send the data to a Log Analytcs workspace in Azure Monitor. This agent can be deployed in any public cloud and on-premises virtual machine. Also you can enable VM insights

### Analyze metrics

- use static threshold to generate an alert when a given resource utilization is greater\lower than a certain value
