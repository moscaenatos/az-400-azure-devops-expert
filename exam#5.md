# Exam Practice #5 - Table of contents

    Objectives Percentage (Corrects/Number Questions)
    Configure processes and communications 100 % (6/6)
    Design and implement source control 61.54 % (8/13)
    Design and implement build and release pipelines 65 % (13/20)
    Develop a security and compliance plan 66.67 % (4/6)
    Implement an instrumentation strategy 60 % (3/5)
    Customer Score: 68% - FAIL - 34/50 (0 Unanswered)

## Design and implement source control

### Design and implement a source control strategy

- use Oauth to make sure that the connection between Github and Azure DevOps server is preferred. OAuth is the preferred authentication method when connecting Github and Azure Devops

### Configure and manage repositories

- use **Azure policy** to make sure that every resource in a subscription contains a tag that identifies the team that is responsible for each resource

## Design and implement build and release pipelines

### Design and implement pipeline automation

- to enstablish authenticaiton to enable Azure CLI in a github Actions workflow:
  - Use Azure login action with OpenID Connect (OIDC) (based on OAUTH 2.0). You'll need:
    - an Azure Active Directory with a service principal that has contributor role access to the subscription
    - Azure Ad application which is configured with a federated credential to trust tokens issued by GitHub Actions to your GitHub repository
    - a GitHub Actions workflow that requests GitHub issue tokens to the workfwo and uses the Azure login action
  - Use Azure login actions with a service principal secret

### Design and implement a package management strategy

- which version to upate when:
  - create a bugfix -> Patch
  - remove a deprecated feature -> Major
  - deprecate a feature -> Minor
  - introduce a new backwards compatible feature -> Minor

### Design and implement deployments

- to implement a delivery streategy to use a feature flags
  1. Design the feature's functionality
  2. Create a release strategy
  3. Build the feature
  4. Test the feature
  5. Release the feature

### Maintain pipelines

- to understand why the top failing tasks are failing:
  - use the Pipeline pass rate report
    - The report provides in-depth view of the pipeline passa rate and how it has trended over time. Additionally it provides an insight into which specific tasks have failed.

## Develop a security and compliance plan

### Automate security and compliance scanning

- to run web app scanning before deployment to prevent security breaches:
  - use OWASP ZAP

## Implement an instrumentation strategy

### Analyze metrics

- to send traces and all application metricts to Azure Monitor Application Insights using a sw projects with a multi language stack:
  - use Azure Monitor OpenTelemetry Exporter
