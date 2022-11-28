# Exam Practice #4 - Table of contents

    Objectives Percentage (Corrects/Number Questions)
    Configure processes and communications 100 % (6/6)
    Design and implement source control 61.54 % (8/13)
    Design and implement build and release pipelines 65 % (13/20)
    Develop a security and compliance plan 66.67 % (4/6)
    Implement an instrumentation strategy 60 % (3/5)
    Customer Score: 68% - FAIL - 34/50 (0 Unanswered)

- [Exam Practice #4 - Table of contents](#exam-practice-4---table-of-contents)
  - [Design and implement source control](#design-and-implement-source-control)
    - [Design and implement a source control strategy](#design-and-implement-a-source-control-strategy)
    - [Plan and implement branching strategies for the source code](#plan-and-implement-branching-strategies-for-the-source-code)
    - [Configure and manage repositories](#configure-and-manage-repositories)
  - [Design and implement build and release pipelines](#design-and-implement-build-and-release-pipelines)
    - [Design and implement pipeline automation](#design-and-implement-pipeline-automation)
    - [Design and implement a package management strategy](#design-and-implement-a-package-management-strategy)
    - [Design and implement pipelines](#design-and-implement-pipelines)
    - [Design and implement infrastructure as code (IaC)](#design-and-implement-infrastructure-as-code-iac)
  - [Develop a security and compliance plan](#develop-a-security-and-compliance-plan)
    - [Design and implement a strategy for managing sensitive information in automation](#design-and-implement-a-strategy-for-managing-sensitive-information-in-automation)
  - [Implement an instrumentation strategy](#implement-an-instrumentation-strategy)
    - [Configure monitoring for a DevOps environment](#configure-monitoring-for-a-devops-environment)

## Design and implement source control

### Design and implement a source control strategy

- To prevent merge conflicts from concurrent edits of large files on Git Large File Storage (LFS)
  - use the git lfs track command with the --lockable flag. File Locking allows developers to lock their files when they are updating them. This prevents other users from updating them at the same time.

### Plan and implement branching strategies for the source code

- Case study :
  - You should perform the following actions in order:
      1. Create a repository.
      2. Create the main branch.
      3. Create a build pipeline.
      4. Enable the continuous integration trigger.
  - To ensure that only changes from a reviewed pull requests are added to the main branch:
    - Add the Tech Lead group as automatic reviewers
    - Add a Build validation policy

### Configure and manage repositories

- permissions needed to
  - Create branches
  - Create tags
  - Manage notes
    - Project Administrator
    - Build Admnistrator
    - Contributors
- to remove a file from git to keep the repository clean and lightweight
  - git rebase (before the file was committed)
  - git push --force

## Design and implement build and release pipelines

### Design and implement pipeline automation

- For a user to be able to run automated tests from Azure Test Plans, the user needs to be a **Project Contributor** or be assigned the following permissions:
  - Manage deployments
  - Manage releases
  - Create releases
  - Edit release stage

- to perform statiscal analaysis and visualise results in a chart to identify trends while using queries in Kusto:
  - integrate the devops pipeline with **Azure Data Explorer**

### Design and implement a package management strategy

- to automatically generate a version number in the release pipeline based on the commit history:
  - Semantic release
  - GitVersion

### Design and implement pipelines

- to ensure that a deployment wll fail if the approval takes longer than 2 hours:
  - Set a timeout for pre-deployment approvals

### Design and implement infrastructure as code (IaC)

- to configure a VM named server02 used as SMTP server using DSC

    ```Powershell Desired State Configuration (DSC)
        Node server02
        {
            WindowsFeatureSet ConfigureVmServices
                {
                    Name = @("SMTP-Server", "Web-Server")
                    Ensure = "Present"
                    IncludeAllSubFeature = $true
                }
        }
    ```

- to create a list of all non-compliant resources based on existing policies using Powershell in Azure DevOps
  - ```Get-AzPolicyState```
- to maintain VM's desidered configuration using a configuration management tool that do not require to have agents installed or having background jobs running on them:
  - Ansible
  - **NB**: **Chef and Puppet** requires an agent to be installed in the target machine

## Develop a security and compliance plan

### Design and implement a strategy for managing sensitive information in automation

- to securely use a private SSH key stored in a file in a release pipeline without exposing it:
  - Upload hte SSH key in the Azure Pipeline Library as a secure file
  - Use the Download Secure File task to download the SSH key

- to configure a pipeline to deploy an application in a third-party Azure subscription that your credentials do not have access to:
  - use a service connection with manual subscription pipeline (then set a different account that has permission to deploy the app)

## Implement an instrumentation strategy

### Configure monitoring for a DevOps environment

- To prevent a deployment to start when the CPU usage metric in the staging environment is above a certain percentage:
  1. Create an alert rule in Azure Monitor.
  2. Add a Query Azure Monitor alerts task in the staging post-deployment gate.
  3. Configure the task with an alert rule filter type.
  4. Select the alert rule.

- to centralize the operating system logs in azure Monitor and use VM Insights for a solution that runs on VMs deployed in a multi-cloud env that includes Azure, AWS and on-premises machines
  - Log Analytics agent allows you to collect telemetry from Windows and Linux Os. The agent can be installed in any public cloud and on-premises VM. Also you can enable VM Insights
