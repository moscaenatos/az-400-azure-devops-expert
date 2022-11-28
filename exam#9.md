# Exam Practice #9 - Table of contents

    Objectives Percentage (Corrects/Number Questions)
    Configure processes and communications 100 % (7/7)
    Design and implement source control 75 % (6/8)
    Design and implement build and release pipelines 80.95 % (17/21)
    Develop a security and compliance plan 100 % (6/6)
    Implement an instrumentation strategy 50 % (4/8)
    Customer Score: 80% - PASS - 40/50 (0 Unanswered)

- [Exam Practice #9 - Table of contents](#exam-practice-9---table-of-contents)
  - [Design and implement source control](#design-and-implement-source-control)
    - [Design and implement a source control strategy](#design-and-implement-a-source-control-strategy)
    - [Configure and manage repositories](#configure-and-manage-repositories)
  - [Design and implement build and release pipelines](#design-and-implement-build-and-release-pipelines)
    - [Design and implement deployments](#design-and-implement-deployments)
  - [Implement an instrumentation strategy](#implement-an-instrumentation-strategy)
    - [Configure monitoring for a DevOps environment](#configure-monitoring-for-a-devops-environment)

## Design and implement source control

### Design and implement a source control strategy

- You need to improve the performance of execution of git commands by using Scalar
  - You can use Scalar to accelerate the Git workflow, irrespective of the size or shape of your Git repository. You can modify Git config settings to overcome the issue, and solve the associated performance bottlenecks as well.
  - You should disable auto-GC by setting gc.auto=0. This prevents the Git commands from being blocked by maintenance.
  - You should disable writing the commit-graph during get fetch by setting fetch.writeCommitGraph=false. This is an important step since Scalar ensures that the fetch step runs git fetch about once an hour only. This saves time since this ensures that the download of new objects happen when you are not waiting for your command to complete execution.
  - You should disable status.aheadBehind=false to remove the calculation of how far ahead or behind your branch is compared to the remote-tracking branch. This can save seconds when you just want to see your unstaged changes.
  - You should use the core.fsmonitor hook to Watchman. The hooks folder in the Dot Git Folder (.git) has a few script files inside it that are referred to as Git Hook Scripts. Git hooks are the scripts that are executed before or after the events. Watchman watches files and records when they actually change. It can also trigger actions, such as rebuilding assets, when matching files change. This assumes that you are using Watchman. In Scalar configuration, in case you are not using Watchman, this config is skipped.

### Configure and manage repositories

- You need to set permissions for a user named UserA so that they can perform the following operations:
  - Create branches.
  - Create tags.
  - Manage notes.
    Which three security groups could you add UserA
    - You should add UserA to the **Contributors**, **Build Administrators**, or **Project Administrators** groups. If UserA was a member of any of these three groups, they would be able to contribute, create branches, create tags, and manage notes

## Design and implement build and release pipelines

### Design and implement deployments

- to implement feature toggles to test canary features with a  specific group of users
  - Use **LaunchDarkly**. It can be installed in Python applications and instantly enable feature toggles through the **LaunchDarkly** portal

- to implement a release pipeline for a blue-green deployment strategy using deployment slots

  1. Create a new deployment slot named staging in Azure App Service.
  2. Add a staging stage in the Release pipeline.
  3. Create a task to deploy the application to the staging slot.
  4. Add a production stage in the Release pipeline.
  5. Create an App Service Manage task to swap the staging slot to production.

- to gradually release a feature to support canary deployment
  - Deployment Slots
  - Traffic Manager

## Implement an instrumentation strategy

### Configure monitoring for a DevOps environment

- You need to reduce Application2 and Application3 telemetry volume to approximately 1 GB per day, per application.
    Which sampling methods are supported for each application?
  - You should use Adaptive, Ingestion, or Fixed-rate sampling for Application2. All sampling configurations allow you to reduce the metric traffic to 10% and meet the budget.
  - You should use Adaptive or Ingestion sampling only for Application3. **Azure Functions does not support Fixed-rate sampling**

- Next, you should configure the application with an Application Insights instrumentation key. **The instrumentation key allows the Python application to send logs to Application Insights**
- You should not configure the application with an Application Insights API key.**The API key is used to programmatically read Application Insights telemetry, and not to integrate with applications**.

- Category='Administrative' Signal name = 'All Administrative operations', Status='failed'
  - it was triggered by a **failed attempt to restart a web app in plan01**

- use **Azure Monitor Application Inights** to implement a mechanism that allows continuous monitoring of the DevOps release pipelines throught the software development lifecycle. With this, you can create appropriate alert mechanism, and gate or roll back a deployment until an alert is resolved
