---
parser: v2
author_name: Céline Audin
author_profile: https://github.com/celineaudinsap
auto_validation: true
time: 15
tags: [ tutorial>beginner, sap-conversational-ai>sap-business-technology-platform, tutorial>free-tier]
primary_tag: sap-conversational-ai>sap-build-process-automation

---

# Acquire Orders Management Using UI5 Application Project From the Store
<!-- description --> Acquire Orders Management package from the SAP Build store and reuse the package in SAP Build Process Automation.

## Prerequisites
- [Subscribe to SAP Build Process Automation](spa-subscribe-booster)

## You will learn
  - How to explore content in the SAP Build Store.
  - How to acquire the **Orders Management using UI5 application** package from the SAP Build Store.
  - How to reuse a package from the Store in SAP Build Process Automation.

---
### Explore the store


The Store offers predefined content for your automation. Packages are categorized by catalog which let you choose between Automation SDK, Business Content and Learning Content.

1. Navigate to the store in your SAP Build Process Automation Tenant.

    <!-- border -->![Navigate Store](01.png)

    > **Learning Content** offers learning packages to get started with the Application Development tool. These packages allow you to learn best practices by reusing the most common flows to design your first projects.

    > **Business Content** provides pre-built automations for concrete business problems.

    > **Automation SDK** provides all the Software Developments Kits that can be acquired from the store.

2. Select one or more filters on the left to filter the available Store projects by Project Type (for example Process and Actions), Format Type (for example, Ready to use and Template), Catalog (for example, Business Content), Product (for example, SAP S/4HANA Cloud), Publisher, Line of Business, and Industry.

    <!-- border -->![Store View](02-StoreView.png)


### Acquire the Orders Management using SAPUI5 application package


1. You will acquire the package titled **Orders Management using UI5 application**. Set the following parameters: under **Catalog**, check **Learning Content**.

    <!-- border -->![Learning Catalog](03-Learning.png)

2. In the search bar, type Orders Management, hit enter and click on the project for more information.

    <!-- border -->![Orders Management](04-OrdersManagement.png)

    This sample package presents a way to deal with Excel and a web application using the SAPUI5 framework. Each sample package comes with a description, documents about the sample, artifacts, version history and dependencies.

    <!-- border -->![Explore](05-Explore.png)

3. To add the package, you have two options:

    - From the project information section, choose **Add** and select **Create from Template**.

    <!-- border -->![Add Create Template](06-AddCreateTemplate.png)

    - From the project list, choose **Add** and select **Create from Template**.

    <!-- border -->![Add Create Template](07-AddCreateTemplate2.png)

    You will now create a Business Process Project from this template.

4. Name the project **Orders Management Dev Tutorial** and choose **Create**.

    <!-- border -->![Create Project](08.png)

5. To see the newly created project, navigate back to the **Lobby** from the top menu.

    <!-- border -->![Created Project](09.png)


### Add an automation to the process


1. Choose the project. You will see all the artifacts that are part of the project. The project is **Editable** which means you can modify it.

2. The project can now be edited in **Build Process Automation**.

    <!-- border -->![Application Development](10.png)

    For instance, you can create a process artifact and add an automation to the Business Process.

3. Select **Create** and then **Process**.

    <!-- border -->![Create Process](13-CreateProcess.png)

4. In the **Create Process** window, fill in the fields as shown in the screenshot:

    <!-- border -->![Create Process Window](14-CreateProcessWindow.png)

    The Process builder opens with the just created process.

5. Now click on the **+** below **Trigger**.

    <!-- border -->![Add](Add.png)
   
6. Select **Automation**.

    <!-- border -->![Automation](Automation.png)

    You have a list of all the automations available in the bot you just acquired. For this tutorial, you will use the **Get Processors Details** automation.

    <!-- border -->![Add Automation](15-AddAutomation.png)

    Now your automation is successfully added to the process. You can further continue modifying your process by adding a trigger to the start event and getting rid of the errors by filling in the missing mandatory inputs.

7. Choose **Add a Trigger**.

    <!-- border -->![Trigger](Trigger.png)
   
8. Select **Submit a Form**.

    <!-- border -->![Form](Form.png)

9. Choose **Blank Form**.

    <!-- border -->![Blank Form](BlankForm.png)

10. In the **Create Form** pop-up, choose **Order Processing Form** for **Name**.

11. Choose **Create**.

    <!-- border -->![Create Form](17-createForm.png)

12. Select the three dots and choose **Open Editor**.

    <!-- border -->![Order Processing](18-orderProcessing.png)

    You will be navigated to the Order Processing Form.

13. Drag and drop the **Text** input. Enter **Order Number** as name and check **Required**.

14. Choose **Save**.

    <!-- border -->![Order Processing Form](19-orderProcessing2.png)

    You will now map the Inputs of the **Get Processors Details** automation.

15. Navigate back to the Order Processing process.

16. Select the **Get Processors Details** automation. Choose `orderReference` input and select **Order Number > Order Processing Form**.

    <!-- border -->![Input Mapping](20-InputMapping.png)

17. Choose **Save**.

18. You may now add forms, approvals, decisions, conditions, etc... to design your process based on your needs.

    <!-- border -->![Process Final](21-process.png)

    Let's test the automation.

19. Double click on **Get Processors Details** automation.

20. The automation opens in a new tab.

21. Select the test icon.

    <!-- border -->![Test Automation](22-testAutomation.png)

22. In the **Test Automation** window, enter **order 7991** as `orderReference`. No need to fill the Environment Variables.

    <!-- border -->![Test Automation2](23-testAuto2.png)

23. This is the final result.

    <!-- border -->![Test Automation3](24-testAuto3.png)

    Once you are done designing your process, you may release and deploy your project.


### Release and deploy the business process project


Now you may release and deploy it in unattended mode.

1. Choose **Release** and again **Release**.

    <!-- border -->![Release](11-Release.png)

2. Now your project is released and you can deploy it. You can choose **Deploy**.

    <!-- border -->![Deploy](12-Deploy.png)

3. Choose the environment and select **Deploy**.

    <!-- border -->![Deploy](02.png)

4. No need to **Define variables**, choose **Deploy**.

    <!-- border -->![Deploy](03.png)  

    To Deploy will take a couple of seconds/minutes depending upon how big your project is and how many different skills it has. Any errors during the deployment will be shown in the Design Console.

5.  The project deployed successfully and is now ready to be executed.

    <!-- border -->![Deployed Project](17-deployed-project.png)

    > You cannot edit released or deployed projects. To continue working on your project, you need to select the Editable option from the list of released versions.


### Set the agent in unattended mode


You need to create a matching agent attribute at this step. Please follow these steps to create an agent attribute in the tenant to add it to your agent and project: [Agent Management Settings to Execute the Process with an Automation](spa-run-agent-settings)


### Run the business process


1. In the **Overview** page, select the **Order Processing** process.

    >Make sure you select the deployed version of the project.

    <!-- border -->![Order 7991](22-order-processing.png)

2. Select the **Order Processing Form** and copy the link.

    <!-- border -->![Order Processing Form](23.png)

3. Paste the link in your browser.

4. Enter **order 7991** in the Order Number field.

5. Choose **Submit**.

    <!-- border -->![Link](24-link-submit.png)

6. The form has been successfully submitted.

    <!-- border -->![Form submitted](25-form-submitted.png)

7. Navigate to **SAP Build > Monitoring > Process and Workflow Instances**.

    <!-- border -->![Monitoring](24.png)

8. Select Status as Completed and choose **Order Processing**.

    <!-- border -->![Monitoring](25.png)

9. Check the **Logs**. 

    The process has successfully ended.

    <!-- border -->![Monitoring](26.png)

---
