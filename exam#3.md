# Exam Practice #3 - Table of contents

    Objectives Percentage (Corrects/Number Questions)
    Configure processes and communications 66.67 % (4/6)
    Design and implement source control 83.33 % (10/12)
    Design and implement build and release pipelines 66.67 % (12/18)
    Develop a security and compliance plan 80 % (4/5)
    Implement an instrumentation strategy 55.56 % (5/9)
    Customer Score: 70% - FAIL - 35/50 (0 Unanswered)

- [Exam Practice #3 - Table of contents](#exam-practice-3---table-of-contents)
  - [Configure processes and communications](#configure-processes-and-communications)
    - [Configure activity traceability and flow of work](#configure-activity-traceability-and-flow-of-work)
    - [Configure collaboration and communication](#configure-collaboration-and-communication)
    - [Plan and implement branching strategies for the source code](#plan-and-implement-branching-strategies-for-the-source-code)
  - [Design and implement build and release pipelines](#design-and-implement-build-and-release-pipelines)
    - [Design and implement pipeline automation](#design-and-implement-pipeline-automation)
    - [Design and implement pipelines](#design-and-implement-pipelines)
    - [Design and implement deployments](#design-and-implement-deployments)
    - [Design and implement infrastructure as code (IaC)](#design-and-implement-infrastructure-as-code-iac)
    - [Maintain pipelines](#maintain-pipelines)
  - [Develop a security and compliance plan](#develop-a-security-and-compliance-plan)
    - [Automate security and compliance scanning](#automate-security-and-compliance-scanning)
  - [Implement an instrumentation strategy](#implement-an-instrumentation-strategy)
    - [Configure monitoring for a DevOps environment](#configure-monitoring-for-a-devops-environment)

## Configure processes and communications

### Configure activity traceability and flow of work

- a user should not have more than two items in progress

### Configure collaboration and communication

- evalutionTracing allows you to retrieve details pertaining to event matching

### Plan and implement branching strategies for the source code

- You should perform the following actions in order:
      1. Create a repository.
      2. Create the main branch.
      3. Create a build pipeline.
      4. Enable the continuous integration trigger.
- To ensure that only changes from a reviewed pull requests are added to the main branch:
  - Add the Tech Lead group as automatic reviewers
  - Add a Build validation policy

## Design and implement build and release pipelines

### Design and implement pipeline automation

- To author advanced queries in Kusto Query Language in Azure Devops:
  - Azure Data Explorer

### Design and implement pipelines

- to automate the release note generation process for a Node.js SDK in an Azure DevOps Project
  - You should install the Generate release notes cross-platform extension from the marketplace. This extension can generate release notes using the same APIs as the Azure Pipelines Release UI uses. The release notes are generated in markdown format that you can customize by using a template. You can use a template to retrieve the related work items and customize the release notes summary.
  - Alternatively, you could add a generate release notes task to the release pipeline. You should configure this task to define where the release notes file will be saved and which template you
  will use to generate the release notes.

### Design and implement deployments

- A development team uses an Azure DevOps CI/CD pipeline. The developers finish their work at different times. You need to ensure that the software only allows the features that are fully functional.
  - The developers should create a long-running feature branch and merge changes after the feature is complete. **The developers should use feature flags**. Feature flags allow a developer to turn features off until they are ready for production. This also ensures that code that is merged does not break the build pipeline

### Design and implement infrastructure as code (IaC)

1. Create a PowerShell Workflow runbook and execute it.
2. Import the necessary modules from the modules gallery Create a graphical runbook and execute it. .
3. Create a PowerShell runbook and execute it.
    First, you should create an Azure Automation account. You can use the Azure Automation account to manage your runbooks, configuration management, and compiling DSC configurations.
    Next, you should import the necessary modules from the modules gallery. You need to import the Az.Accounts and the Az.Automation modules from the modules gallery. These modules are required
    by your runbook script, and they are not available by default when you create your Automation account.
    Finally, you should create a PowerShell runbook and execute it. You need to create a PowerShell runbook to execute your script and compile the DSC configuration that should be used for the
    production environment.

### Maintain pipelines

- to find out which tests are intermittently failing more frequently and fix these tests:
  - You should recommend checking the test failures analytics report. This report is available in the build tests analytics tab and includes metrics about how many tests are executed in the
    pipeline, how many unique tests are failing, and some metrics for each test. In the metrics for each test, you can sort by the pass rate and see the intermittent tests with the lowest pass rate

## Develop a security and compliance plan

### Automate security and compliance scanning

- to improve code quality during the continuous integration pipeline in  a Java application that is integrated with Azure Pipelines:
  - You should recommend enabling Run PMD Analysis in a Maven task. PMD is used to perform static code analysis and report common quality issues, like unused variables and empty try/catch
    blocks. PMD supports Java applications and could be integrated in your build process using the Maven task.
  - Another option is to recommend enabling Run SonarQube Analysis in a Maven task. With SonarQube analysis you can analyze your code in multiple languages, including Java, for code quality issues
    and define rules to check for unused variables and try/catch blocks

## Implement an instrumentation strategy

### Configure monitoring for a DevOps environment

- which workspaces can be used as the centralized workspace.

  - You should use workspace2 or workspace3 only. Both workspaces are configured to allow the usage of resource permission or workspace permission. You should use resource permission to
    implement granular role-based access control to allow each team to have access to logs related to their application only. Log Analytics workspaces do not require resources to be in the same
    Azure region to be integrated.
  - You should not use workspace1. This workspace is configured to require workspace permissions. You cannot assign granular role-based access control to resource level in this access mode. With
    workspace permissions, you need to give access to all resources available in the workspace for both teams.

- Which sampling methods are supported for each application
  - You should use Adaptive, Ingestion, or Fixed-rate sampling for Application2. All sampling configurations allow you to reduce the metric traffic to 10% and meet the budget.
  - You should use Adaptive or Ingestion sampling only for Application3. Azure Functions does not support Fixed-rate sampling.
        Fixed-rate sampling is configured in the server-side SDK and only sends to Application Insights the configured sampling of the metrics.
        Ingestion sampling is configured on the Application Insights side, discarding the metrics sent by the application at a sampling rate set by you, which also reduces costs.
        Adaptive sampling is automatically configured in ASP.NET Core SDK and Azure Functions. It automatically discards telemetry data when the volume exceeds the count defined in
        the MaxTelemetryItemsPerSecond setting. The current configuration is exceeding the budget, so you should reduce the MaxTelemetryItemsPerSecond setting accordingly to meet the targeted
        traffic of 1 GB per day

- to enable distributed tracing for a Python microservice
    You should perform the following actions in order:

    1. Install the OpenCensus Python SDK.
    2. Configure the application with an Application Insights instrumentation key.
    3. Define the trace ID, span ID, and sampling flag to the log records.

    You should not define the exceptions and stack traces to log records. This would allow you to see the exception and stack traces of the application in Application Insights. These properties are not
    necessary
- to integrate the platform monitoring tools to centralize the solution's operating system logs in Azure Monitor and also use VM Insights
  - You should use the Log Analytics agent. This agent allows you to collect telemetry from Windows and Linux operating systems and send the data to a Log Analytics workspace in Azure Monitor. You
    can deploy this agent in any public cloud and on-premises virtual machine. With the Log Analytics agent, you can also enable VM Insights.

- to send alerts to the developers when users see errors on the production website. The developers should be able to debug those errors using stack traces:
  - You should recommend Application Insights. Application Insights is an application performance management (APM) service that you can use to monitor your web applications. You can integrate the
    web application with Application Insights with an instrumentation package. All of the exceptions and other metrics will be monitored and sent to the Application Insights servers.
- You should also recommend Logic Apps. Using Logic Apps allows you to connect and run a custom query in Application Insights with a weekly scheduled trigger and post a message in the Microsoft
  Teams channel with the contents of the custom query, without the requirement to write any code.
