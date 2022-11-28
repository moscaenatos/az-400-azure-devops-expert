# Exam Practice #7 - Table of contents

    Objectives Percentage (Corrects/Number Questions)
    Configure processes and communications 85.71 % (6/7)
    Design and implement source control 84.62 % (11/13)
    Design and implement build and release pipelines 94.44 % (17/18)
    Develop a security and compliance plan 100 % (5/5)
    Implement an instrumentation strategy 57.14 % (4/7)
    Customer Score: 86% - PASS - 43/50 (0 Unanswered)

- [Exam Practice #7 - Table of contents](#exam-practice-7---table-of-contents)
  - [Configure processes and communications](#configure-processes-and-communications)
    - [Configure collaboration and communication](#configure-collaboration-and-communication)
  - [Design and implement build and release pipelines](#design-and-implement-build-and-release-pipelines)
    - [Design and implement deployments](#design-and-implement-deployments)
  - [Implement an instrumentation strategy](#implement-an-instrumentation-strategy)
    - [Configure monitoring for a DevOps environment](#configure-monitoring-for-a-devops-environment)

## Configure processes and communications

### Configure collaboration and communication

- Your organization uses Azure DevOps Services team project Wikis to enhance developer communication. You need to assign default permissions to a user named UserA so that they can edit the team project wiki page. Which security groups should you add UserA to as a team member?
  - The **Project Administrator security group** grants other permissions, such as setting project-level notifications or alerts and creating a wiki.

## Design and implement build and release pipelines

### Design and implement deployments

- A development team uses an Azure DevOps CI/CD pipeline. The developers finish their work at different times. You need to ensure that the software only allows the features that are fully functional. What strategy should you use?
  - **The developers should use feature flags**. Feature flags allow a developer to turn features off until they are ready for production. This also ensures that code that is merged does not break the build pipeline

## Implement an instrumentation strategy

### Configure monitoring for a DevOps environment

- case study AZ-400_86699
  - You need to reduce Application2 and Application3 telemetry volume to approximately 1 GB per day, per application. Which sampling methods are supported for each application?
    - You should use Adaptive, Ingestion, or Fixed-rate sampling for Application2. All sampling configurations allow you to reduce the metric traffic to 10% and meet the budget.
    - You should use Adaptive or Ingestion sampling only for Application3. Azure Functions does not support Fixed-rate sampling
