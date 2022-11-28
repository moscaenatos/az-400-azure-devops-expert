# Exam Practice #6 - Table of contents

## Design and implement source control

### Configure collaboration and communication

- Which chart widget should you use for each requirement?
  - You should use the Lead Time widget to determine how long a work item takes from creation to completion. This would give stakeholders an estimation of how long it would take for a recently requested feature to become available.
  - You should use the Sprint capacity widget to estimate the team capacity in a given sprint. The Sprint capacity widget allows you to determine whether the team is currently capable of working on all of the sprint user stories.
  - You should use the Deployment status widget to show a consolidated view of the success rate of a deployment pipeline. This widget shows the deployment status and the test pass rate across multiple environments for a recent set of builds on a deployment pipeline

## Design and implement source control

### Plan and implement branching strategies for the source code

- to define a branching strategy
  - You should use feature branches for features and bug fixes. This is a good practice in a distributed version control environment because it allows you to isolate work that is in progress

## Design and implement build and release pipelines

### Design and implement pipeline automation

- the following YAML configuration file

    ```yaml
        pool:
            vmImage: ubuntu-latest
        jobs:
            - job: waitForValidation
            displayName: Wait for external validation
            pool: server
            timeoutInMinutes: 4320
            steps:
                -   task: ManualValidation@0
                    timeoutInMinutes: 2880
                    inputs:
                            notifyUsers: |
                                jdoe@mycompany.com
                    instructions: 'Please validate the build configuration and resume'
                    onTimeout: 'resume'
    ```

  - jdoe@mycompany.com will be able to approve or deny the pipeline run. The optional parameter notifyUsers denotes the list of email addresses for users that will be notified that the task has been
  activated and in order for them to approve or deny the pipeline run.
  - Only users with the Queue builds permission can act on a manual validation. Users with the View builds and Stop builds permissions **cannot** perform a manual validation.
  - The job **will not** time out in 48 hours. The **job times out in 72 hours**, or three days, which is expressed in minutes as 4320. The timeoutInMinutes parameter under Jobs refer to a job, whereas the timeoutInMinutes parameter under steps refers to a task. In this scenario, **timeoutInMinutes: 4320 refers to the job**, **timeoutInMinutes: 2880 refers to the task**.

### Design and implement a package management strategy

- which version to upate when:
  - create a bugfix -> Patch
  - remove a deprecated feature -> Major
  - deprecate a feature -> Minor
  - introduce a new backwards compatible feature -> Minor

### Design and implement pipelines

- You work as a DevOps Engineer for a gaming company. Your company uses self-hosted build agents with Azure Pipelines for projects across the organization. The self-hosted build agents run in Azure Virtual Machines Scale Sets (Azure VMSS) in Ubuntu-based machines. You need to regularly update the tooling installed in the self-hosted build agents to support new projects and security patches by creating a new virtual machine image.
You need to automate the process of building new virtual machine images.
  - **You should use Packer**. Packer is a tool for creating identical virtual machine images for multiple platforms or cloud providers from a single source configuration. From a configuration source, you can install and update all the required tooling in an updated Ubuntu base image, and automate this process of build and updating the Azure VMSS image with an Azure Pipeline.

## Implement an instrumentation strategy

### Configure monitoring for a DevOps environment

- To prevent a deployment to start when the CPU usage metric in the staging environment is above a certain percentage:
  1. Create an alert rule in Azure Monitor.
  2. Add a Query Azure Monitor alerts task in the staging post-deployment gate.
  3. Configure the task with an alert rule filter type.
  4. Select the alert rule.

- You need to implement a mechanism to allow continuous monitoring of your DevOps release pipeline throughout the software development lifecycle, which will allow you to create appropriate alert mechanisms, and gate or roll back a deployment until an alert is resolved. What should you integrate with your DevOps pipelines?
  - You should integrate **Azure Monitor Application Insights** with your Azure pipelines. This is the required step for implementing a mechanism that allows continuous monitoring of your DevOps release pipeline throughout the software development lifecycle. This will allow you to create appropriate alert mechanisms, and gate or roll back a deployment until an alert is resolved.
