# AZ-400: Implement CI with Azure Pipelines and GitHub Actions - Table of Contents

- [AZ-400: Implement CI with Azure Pipelines and GitHub Actions - Table of Contents](#az-400-implement-ci-with-azure-pipelines-and-github-actions---table-of-contents)
  - [Explore Azure Pipelines](#explore-azure-pipelines)
    - [Explore the concept of pipelines in DevOps](#explore-the-concept-of-pipelines-in-devops)
    - [Describe Azure Pipelines](#describe-azure-pipelines)
      - [Understand Azure Pipelines key terms](#understand-azure-pipelines-key-terms)
    - [Manage Azure Pipeline agents and pools](#manage-azure-pipeline-agents-and-pools)
      - [Choose between Microsoft-hosted versus self-hosted agents](#choose-between-microsoft-hosted-versus-self-hosted-agents)
      - [Do self-hosted agents have any performance advantages over Microsoft-hosted agents?](#do-self-hosted-agents-have-any-performance-advantages-over-microsoft-hosted-agents)
    - [Introduction to agent pools](#introduction-to-agent-pools)
  - [Explore continuous integration](#explore-continuous-integration)

## Explore Azure Pipelines

### Explore the concept of pipelines in DevOps

A typical pipeline will include the following stages: build automation and continuous integration, test automation, and deployment automation.

### Describe Azure Pipelines

Azure Pipelines is a cloud service that automatically builds and tests your code project and makes it available to other users. It works with just about any language or project type.
Azure Pipelines combines continuous integration (CI) and continuous delivery (CD) to test and build your code and ship it to any target constantly and consistently.

| Continuous integration (CI)                      | Continuous delivery (CD)                        |
| ------------------------------------------------ | ----------------------------------------------- |
| Increase code coverage.                          | Automatically deploy code to production.        |
| Build faster by splitting test and build runs.   | Ensure deployment targets have the latest code. |
| Automatically ensure you don't ship broken code. | Use tested code from the CI process.            |
| Run tests continually.                           |                                                 |

#### Understand Azure Pipelines key terms

![azure-pipeline-components](https://learn.microsoft.com/en-us/training/wwl-azure/explore-azure-pipelines/media/key-pipeline-concepts-overview-ca80c85c.png)

- **Agent**
    When your build or deployment runs, the system begins one or more jobs. An agent is installable software that runs a build or deployment job.
- **Artifact**
    An artifact is a collection of files or packages published by a build. Artifacts are made available for the tasks, such as distribution or deployment.
- **Build**
    A build represents one execution of a pipeline. It collects the logs associated with running the steps and the test results.
- **Continuous delivery**
    Continuous delivery (CD) (also known as Continuous Deployment) is a process by which code is built, tested, and deployed to one or more test and production stages. Deploying and testing in multiple stages helps drive quality. Continuous integration systems produce deployable artifacts, which include infrastructure and apps. Automated release pipelines consume these artifacts to release new versions and fix existing systems. Monitoring and alerting systems constantly run to drive visibility into the entire CD process. This process ensures that errors are caught often and early.
- **Continuous integration**
    Continuous integration (CI) is the practice used by development teams to simplify the testing and building of code. CI helps to catch bugs or problems early in the development cycle, making them more accessible and faster to fix. Automated tests and builds are run as part of the CI process. The process can run on a schedule, whenever code is pushed, or both. Items known as artifacts are produced from CI systems. The continuous delivery release pipelines use them to drive automatic deployments.
- **Deployment target**
    A deployment target is a virtual machine, container, web app, or any service used to host the developed application. A pipeline might deploy the app to one or more deployment targets after the build is completed and tests are run.
- **Job**
    A build contains one or more jobs. Most jobs run on an agent. A job represents an execution boundary of a set of steps. All the steps run together on the same agent. For example, you might build two configurations - x86 and x64. In this case, you have one build and two jobs.
- **Pipeline**
    A pipeline defines the continuous integration and deployment process for your app. It's made up of steps called tasks. It can be thought of as a script that describes how your test, build, and deployment steps are run.
- **Release**
    When you use the visual designer, you can create a release or a build pipeline. A release is a term used to describe one execution of a release pipeline. It's made up of deployments to multiple stages.
- **Stage**
    Stages are the primary divisions in a pipeline: "build the app," "run integration tests," and "deploy to user acceptance testing" are good examples of stages.
- **Task**
    A task is the building block of a pipeline. For example, a build pipeline might consist of build and test tasks. A release pipeline consists of deployment tasks. Each task runs a specific job in the pipeline.
- **Trigger**
    A trigger is set up to tell the pipeline when to run. You can configure a pipeline to run upon a push to a repository at scheduled times or upon completing another build. All these actions are known as triggers.

### Manage Azure Pipeline agents and pools

#### Choose between Microsoft-hosted versus self-hosted agents

- Microsoft-hosted agent
    With a Microsoft-hosted agent, maintenance and upgrades are automatically done. Each time a pipeline is run, a new virtual machine (instance) is provided. The virtual machine is discarded after one use.
- Self-hosted agent

    A self-hosted agent gives you more control to install dependent software needed for your builds and deployments.
    After you've installed the agent on a machine, you can install any other software on that machine as required by your build or deployment jobs.
    A self-hosted agent doesn't have job time limits.

#### Do self-hosted agents have any performance advantages over Microsoft-hosted agents?

**In many cases, yes**. Specifically:

- If you use a self-hosted agent, you can run incremental builds. For example, you define a CI build pipeline that doesn't clean the repo or do a clean build. Your builds will typically run faster
  You don't get these benefits when using a Microsoft-hosted agent. The agent is destroyed after the build or release pipeline is completed.
- A Microsoft-hosted agent can take longer to start your build. While it often takes just a few seconds for your job to be assigned to a Microsoft-hosted agent, it can sometimes take several
  minutes for an agent to be allocated, depending on the load on our system.

### Introduction to agent pools

Instead of managing each agent individually, you organize agents into agent pools. An agent pool defines the sharing boundary for all agents in that pool.

- Pools are scoped to the entire organization so that you can share the agent machines across projects.
- Pools scoped to a project can only use them across build and release pipelines within a project.

## Explore continuous integration

Continuous integration relies on four key elements for successful implementation: a

1. Version Control System
2. Package Management System
3. Continuous Integration System  
4. Automated Build Process.

![anatomy-of-pipeline](https://learn.microsoft.com/en-us/training/modules/integrate-azure-pipelines/2-describe-anatomy-of-pipeline)
