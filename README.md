[![Board Status](https://dev.azure.com/moscaen/e8ee78c4-e8b8-4bb9-b319-3ba4b2ad6720/7a1a78cd-7c77-4109-b00c-87aa69a84884/_apis/work/boardbadge/6250eb75-9c1c-4572-bb30-9aeb2185af4e)](https://dev.azure.com/moscaen/e8ee78c4-e8b8-4bb9-b319-3ba4b2ad6720/_boards/board/t/7a1a78cd-7c77-4109-b00c-87aa69a84884/Microsoft.RequirementCategory)
# AZ-400-DEVOPS-EXPERT guide - Table of contents

- [AZ-400-DEVOPS-EXPERT guide - Table of contents](#az-400-devops-expert-guide---table-of-contents)
  - [Skills measured](#skills-measured)
  - [Functional groups](#functional-groups)
    - [Configure processes and communications (10–15%)](#configure-processes-and-communications-1015)
      - [Configure activity traceability and flow of work](#configure-activity-traceability-and-flow-of-work)
      - [Configure collaboration and communication](#configure-collaboration-and-communication)
    - [Design and implement source control (15–20%)](#design-and-implement-source-control-1520)
      - [Design and implement a source control strategy](#design-and-implement-a-source-control-strategy)
      - [Plan and implement branching strategies for the source code](#plan-and-implement-branching-strategies-for-the-source-code)
      - [Configure and manage repositories](#configure-and-manage-repositories)
    - [Design and implement build and release pipelines (40–45%)](#design-and-implement-build-and-release-pipelines-4045)
      - [Design and implement pipeline automation](#design-and-implement-pipeline-automation)
      - [Design and implement a package management strategy](#design-and-implement-a-package-management-strategy)
      - [Design and implement pipelines](#design-and-implement-pipelines)
      - [Design and implement deployments](#design-and-implement-deployments)
      - [Design and implement infrastructure as code (IaC)](#design-and-implement-infrastructure-as-code-iac)
      - [Maintain pipelines](#maintain-pipelines)
    - [Develop a security and compliance plan (10–15%)](#develop-a-security-and-compliance-plan-1015)
      - [Design and implement a strategy for managing sensitive information in automation](#design-and-implement-a-strategy-for-managing-sensitive-information-in-automation)
      - [Automate security and compliance scanning](#automate-security-and-compliance-scanning)
    - [Implement an instrumentation strategy (10–15%)](#implement-an-instrumentation-strategy-1015)
      - [Configure monitoring for a DevOps environment](#configure-monitoring-for-a-devops-environment)
      - [Analyze metrics](#analyze-metrics)

## Skills measured

1. Configure processes and communications (10–15%)
1. Design and implement source control (15–20%)
1. Design and implement build and release pipelines (40–45%)
1. Develop a security and compliance plan (10–15%)
1. Implement an instrumentation strategy (10–15%)
1. [link](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE3VP8d)

## Functional groups

### Configure processes and communications (10–15%)

#### Configure activity traceability and flow of work

- Plan and implement a structure for the flow of work and feedback cycles
- Identify appropriate metrics related to flow of work, such as cycle times, time to recovery, and
lead time
- Integrate pipelines with work item tracking tools, such as Azure DevOps and GitHub
- Implement traceability policies decided by development
- Integrate a repository with Azure Boards

#### Configure collaboration and communication

- Communicate actionable information by using custom dashboards in Azure DevOps
- Document a project by using tools, such as wikis and process diagrams
- Configure release documentation, including release notes and API documentation
- Automate creation of documentation from Git history
- Configure notifications by using webhooks

### Design and implement source control (15–20%)

#### Design and implement a source control strategy

- Design and implement an authentication strategy
- Design a strategy for managing large files, including Git LFS and git-fat
- Design a strategy for scaling and optimizing a Git repository, including Scalar and crossrepository sharing
- Implement workflow hooks

#### Plan and implement branching strategies for the source code

- Design a branch strategy, including trunk-based, feature branch, and release branch
- Design and implement a pull request workflow by using branch policies and branch protections
- Implement branch merging restrictions by using branch policies and branch protections

#### Configure and manage repositories

- Integrate GitHub repositories with Azure Pipelines, one of the services in Azure DevOps
- Configure permissions in the source control repository
- Configure tags to organize the source control repository
- Recover data by using Git commands
- Purge data from source control

### Design and implement build and release pipelines (40–45%)

#### Design and implement pipeline automation

- Integrate pipelines with external tools, including dependency scanning, security scanning, and
code coverage
- Design and implement quality and release gates, including security and governance
- Design integration of automated tests into a pipeline
- Design and implement a comprehensive testing strategy
- Implement orchestration of tools, such as GitHub Actions and Azure Pipelines

#### Design and implement a package management strategy

- Design a package management implementation that uses Azure Artifacts, GitHub Packages,
NuGet, and npm
- Design and implement package feeds, including upstream sources
- Design and implement a dependency versioning strategy for code assets and packages,
including semantic versioning and date-based
- Design and implement a versioning strategy for pipeline artifacts

#### Design and implement pipelines

- Select a deployment automation solution, including GitHub Actions and Azure Pipelines
- Design and implement an agent infrastructure, including cost, tool selection, licenses,
connectivity, and maintainability
- Develop and implement pipeline trigger rules
- Develop pipelines, including classic and YAML
- Design and implement a strategy for job execution order, including parallelism and multi-stage
- Develop complex pipeline scenarios, such as containerized agents and hybrid
- Configure and manage self-hosted agents, including virtual machine (VM) templates and
containerization
- Create reusable pipeline elements, including YAML templates, task groups, variables, and
variable groups
- Design and implement checks and approvals by using YAML environments

#### Design and implement deployments

- Design a deployment strategy, including blue/green, canary, ring, progressive exposure, feature
flags, and A/B testing
- Design a pipeline to ensure reliable order of dependency deployments
- Plan for minimizing downtime during deployments by using VIP swap, load balancer, and rolling
deployments
- Design a hotfix path plan for responding to high-priority code fixes
- Implement load balancing for deployment, including Azure Traffic Manager and the Web Apps
feature of Azure App Service
- Implement feature flags by using Azure App Configuration Feature Manager
- Implement application deployment by using containers, binary, and scripts

#### Design and implement infrastructure as code (IaC)

- Recommend a configuration management technology for application infrastructure
- Implement a configuration management strategy for application infrastructure, including IaC
- Define an IaC strategy, including source control and automation of testing and deployment
- Design and implement desired state configuration for environments, including Azure
Automation State Configuration, Azure Resource Manager, Bicep, and Azure Policy guest
configuration

#### Maintain pipelines

- Monitor pipeline health, including failure rate, duration, and flaky tests
- Optimize pipelines for cost, time, performance, and reliability
- Analyze pipeline load to determine agent configuration and capacity
- Design and implement a retention strategy for pipeline artifacts and dependencies

### Develop a security and compliance plan (10–15%)

#### Design and implement a strategy for managing sensitive information in automation

- Implement and manage service connections
- Implement and manage personal access tokens
- Implement and manage secrets, keys, and certificates by using Azure Key Vault, GitHub secrets,
and Azure Pipelines secrets
- Design and implement a strategy for managing sensitive files during deployment
- Design pipelines to prevent leakage of sensitive information

#### Automate security and compliance scanning

- Automate analysis of source code by using GitHub code scanning, GitHub secrets scanning,
pipeline-based scans, and SonarQube
- Automate security scanning, including container scanning and OWASP ZAP
- Automate analysis of licensing, vulnerabilities, and versioning of open-source components by
using WhiteSource Bolt and GitHub Dependency Scanning

### Implement an instrumentation strategy (10–15%)

#### Configure monitoring for a DevOps environment

- Configure and integrate monitoring by using Azure Monitor
- Configure and integrate with monitoring tools, such as Azure Monitor and Application Insights
- Manage access control to the monitoring platform
- Configure alerts for pipeline events

#### Analyze metrics

- Inspect distributed tracing by using Application Insights
- Inspect application performance indicators
- Inspect infrastructure performance indicators, including CPU, memory, disk, and network
- Identify and monitor metrics for business value
- Analyze usage metrics by using Application Insight
- Interrogate logs using basic Kusto Query Language (KQL) queries
