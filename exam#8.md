## Configure processes and communications

### Configure activity traceability and flow of work

- Your company uses Azure Boards to manage the platform backlog, and the external team uses Trello. You need to add new cards to the external team board when your product team creates new backlog items in Azure Boards. This process should be as automatic as possible. Which two actions should you perform? Each correct answer presents part of the solution.
  - You should **grant access to Azure DevOps in the Trello account**. This will allow Azure DevOps to programmatically create new cards and lists in a Trello board from this account via a token that is used by a service hook subscription
  - You should also **configure a service hook subscription in Azure DevOps**. Service hooks let you run tasks on other services when events occur in your Azure DevOps projects. You can configure the service hook with the generated token to create new cards in Trello when new work items are added to the Azure Boards backlog

### Configure collaboration and communication

- You use Azure Boards as part of Azure DevOps Services to track work. You use the Agile process to create multiple work items including user stories, tasks and bugs, among others. You need to connect your Azure Board work items with GitHub.com so that you can link GitHub commits and pull requests with the work items. Which two authentication methods should you recommend to meet the above requirement? Each correct answer presents a complete solution.
  - You should recommend using a personal access token or a GitHub.com user account. Different authentication methods are used depending on the type of GitHub platform that you want to connect to.
    In this scenario, you need to connect to the GitHub.com platform which supports two types of authentication methods:
    - Personal Access Token (PAT): You need to use the URL for your GitHub.com and the PAT credentials, which are recognized by GitHub.com
    - GitHub.com user account: You should use the GitHub.com user account credentials when you want to connect to GitHub.com. Authentication via GitHub.com user account credentials is the     preferred and recommended method when connecting Azure Boards with the GitHub platform.
- Azure boards Widget:
  - Show a consolidate view of the success rate of a deployment pipeline:
    - You should use the **Deployment status widget** to show a consolidated view of the success rate of a deployment pipeline. This widget shows the deployment status and the test pass rate across multiple

## Design and implement source control

### Configure and manage repositories

- You need to set permissions for a user named UserA so that they can perform the following operations:
  - Create branches.
  - Create tags.
  - Manage notes.
    Which three security groups could you add UserA
    - You should add UserA to the Contributors, Build Administrators, or Project Administrators groups. If UserA was a member of any of these three groups, they would be able to contribute, create branches, create tags, and manage notes

## Design and implement build and release pipelines

### Design and implement pipeline automation

```yaml
    coverage:
        status:
            comments: on
            diff:
                target: 50%

```

Code coverage is an important metric of quality. It helps you to measure the percentage of your project's code that is being tested. There are two kinds of code coverage:

- Full coverage denotes coverage for the entire code within a project.
- Diff coverage denotes specific code coverage in the context of pull requests, which are initiated and executed by code developers in a project and is relevant for developers who are focused on the specific lines of code they have added or changed.

Details about coverage for each file will be posted as a pull request comment. The YAML configuration file contains **the details of code coverage for each file changed, which will be posted as a pull request comment when 'on'**.
The YAML file will provide details related to code coverage only for the lines changed in a pull request, due to the nature of the coverage being diff coverage.
50% does not represent the threshold value for a successful full coverage status to be posted. **50% represents the target threshold value for diff coverage, not full coverage**

### Design and implement a package management strategy

- semantic versioning:
  - Introduce a new backwards compatible feature -> Minor
  - Deprecate a feature -> Minor
  - Remove a deprecated feature -> Major
  - To release a bugfix -> Patch

- to generate automatically version number in a release pipeline based on the commit history:
  - GitVersion
  - Semantic release

### Design and implement pipelines

- Your company moves development to Azure DevOps. The build jobs rely on external devices. You need to build a secure pipeline by monitoring the health signals from the external devices
  - You should enable release gates in the pre-deployment and post-deployment conditions. This option will allow the build process to monitor the health of external devices that may be needed before or Use Azure REST APIs to send email alerts.

- You work as a DevOps Engineer for a gaming company. Your company uses self-hosted build agents with Azure Pipelines for projects across the organization. The self-hosted build agents run in Azure Virtual Machines Scale Sets (Azure VMSS) in Ubuntu-based machines. You need to regularly update the tooling installed in the self-hosted build agents to support new projects and security patches by creating a new virtual machine image. You need to automate the process of building new virtual machine images
  - **You should use Packer**. **Packer** is a tool for creating identical virtual machine images for multiple platforms or cloud providers from a single source configuration. From a configuration source, you can install and update all the required tooling in an updated Ubuntu base image, and automate this process of build and updating the Azure VMSS image with an Azure Pipeline.
