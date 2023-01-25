---
parser: v2
author_name: Chaitanya Priya Puvvada
author_profile: https://github.com/chaitanya-priya-puvvada
auto_validation: true
time: 10
tags: [ tutorial>beginner, software-product>sap-business-technology-platform, tutorial>free-tier]
primary_tag: software-product>sap-build-process-automation
---

# Acquire A Template Project From The Store
<!-- description --> Import a sample Business process from the SAP Build store

## Prerequisites
- Account with [SAP BTP Free Tier](spa-subscribe-booster) service plan for SAP Build Process Automation

## You will learn
  - How to explore content in the SAP Build Store
  - How to acquire any business process from the SAP Build Store
  - How to reuse a package from the Store in SAP Build Process Automation

---
### Explore the store

The Store is available for everyone and can be accessed directly from the home page. The store offers prebuilt content created and curated by SAP, which can be used free of charge with SAP Build Process Automation.

Packages are categorized by catalog, which let you choose between Business Content, Learning Content and Automation SDK. It also offers a variety of filters, a search feature, and content descriptions to help users find what they are looking for quickly.

1. Navigate to the store in your SAP Build Process Automation Tenant.

    &nbsp;

    > **Learning Content** offers learning packages to get started with the Application Development tool. These packages allow you to learn best practices by reusing the most common flows to design your first projects.

    > **Business Content** provides pre-built Business Process for concrete business problems.

    > **Automation SDK** provides all the Software Developments Kits that can be acquired from the store.

    <!-- border -->![Navigate Store](1.Store.png)

    You can select one or more filters on the left to filter the available Store projects by Project Type (for example Live Process and Business Process), Format Type (for example, Ready to use and Template), Catalog (for example, Business Content), Product (for example, SAP S/4HANA Cloud), Publisher, Line of Business, and Industry.


### Import sales order approvals business process

You will import the Business Process titled **Sales Order Approvals - Sample**.

1. Set the following parameters: under **Catalog**, check **Learning Content** and type **Sales Order Approvals - Sample**  in the search bar and hit enter.

    > This sample content is designed to help users to get started in streamlining and digitalizing the processing of approvals for sales orders and can be managed and customized directly by the departments depending on their needs.

    <!-- border -->![Import Business Process](2.ImportBusinessProcess.png)

2. To add the package,  select **Create from Template**.

    Name the project **Sales Order Approvals Dev Tutorial** and choose **Create**.

    <!-- border -->![Create Project](3.Createfromtemplate.png)


3. Once the project is imported successfully, to see the newly created project, navigate back to the **Lobby** from the top menu.

    <!-- border -->![Lobby](4.Lobby.png)

    You have now imported a sample process and are ready to test/modify it.
