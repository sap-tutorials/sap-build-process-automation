---
parser: v2
author_name: Samir Hamichi
author_profile: https://github.com/shamichi-repo
auto_validation: true
time: 15
tags: [ tutorial>intermediate, software-product>sap-business-technology-platform,products>sap-business-application-studio, tutorial>free-tier ]
primary_tag: software-product>sap-build-process-automation
---

# Integrate an SAP UI5 Task in a Business Process
<!-- description -->Integrate an Existing Workflow SAP UI Task in a sales order approval business process.

## Prerequisites
 - Complete [Create an SAP UI5 Task in for a Business Process](spa-create-sapui5-task-orderapproval) tutorial
 - Complete [Subscribe to SAP Build Process Automation](spa-subscribe-booster) tutorial
 - Complete [Build Your First Business Process with SAP Build Process Automation](mission.sap-process-automation) mission

## You will learn
  - How to integrate your SAP UI5 Approval Form in an SAP Build Process Automation project.

---

### Import your SAP UI5 form in your SAP Build Process Automation

1. Open your Sales Order Management project you created as a prerequisite.

    > **CAUTION**: If you are using a SAP BTP Free Trial account, you are limited to a quota of 5 forms within your project. Please delete the **Approval Form** before you import your SAP UI5 form.

    <!-- border -->![Process](001.png)

2. Perform the following steps:

    - under the **Editable** version of your project
    - choose the **Import** button.
    - select **Form** from the contextual menu

    <!-- border -->![Process](022a.png)

3. Fill the Import Form details:

    - set the **Application ID**, the name of your SAP UI5 application you get from the *manifest.json* file
    - set the **Version**, the application version you get from the *manifest.json* file
    - provide a **Name**, an identifier and a description for your approval form
    - choose the **Import** button

    <!-- border -->![Process](022.png)

4. The form should open in the **Forms Editor**:

    - if you want to open the *manifest.json*, choose the **hyper link** button
    - close the **Forms Editor**

    <!-- border -->![Process](023.png)

### Update your Business Process

1. Open your **Order Processing** business process

    <!-- border -->![Process](024.png)

2. Remove the current **Approval Form** designed by with **Forms Builder**

    <!-- border -->![Process](025.png)

3. Add your imported **Order Approval UI Task** as approval into your business process

    <!-- border -->![Process](026.png)

4. Connect the **reject** branch into the **Order Rejection Notification** form

    <!-- border -->![Process](026a.png)

5. Select the Oder Approval UI Task, fill and map the required fields:

    - in the **Subject** field, enter **Review and approve order**, select **Order Number** from Order Processing Form, enter **and**, select **Ship To Party** from Order Processing Form
    - set the **Users** under **Recipients** with **Process Started By** from Process Metadata
    - choose the **Inputs** tab

    <!-- border -->![Process](027.png)

6. Map the required form **Inputs** accordingly

    <!-- border -->![Process](028.png)

7. Select the **Order Confirmation Form** and map the required missing input accordingly

    <!-- border -->![Process](029.png)

8. Select the **Order Rejection Notification** form

    - map the required missing input accordingly

    <!-- border -->![Process](030a.png)

9. Save your project

10. Release your project


### Deploy your project

1. Deploy your **Project** and retrieve the **Form Trigger** link for testing

    <!-- border -->![Process](037.png)

2. Provide **Sales Order** data and test your process going through the approval process branch

    <!-- border -->![Process](038.png)


### Check task in Inbox

[OPTION BEGIN [SAP Build Process Automation]]       
1. Open your **Inbox**

    <!-- border -->![Process](14.png)

2. Review your approval task and take a decision.

    <!-- border -->![Process](15.png)

3. Complete your process:

    - Refresh your tasks
    - Check that the decision is reflected with the right notification task

    <!-- border -->![Process](16b.png)
[OPTION END]

[OPTION BEGIN [SAP Build Work Zone(Standard Edition)]]        
>Pre-requisite: Complete [Configure SAP Build Work Zone, Standard Edition ](spa-configure-workzone)tutorial

1. Once you have subscribed to SAP Build Work Zone, Standard Edition navigate to **Site Directory** and go to the site.

    <!-- border -->![Process](43.png)

2. Choose the **Inbox** tile.

    <!-- border -->![Process](44.png) 

3. Review your approval task and take a decision.

    <!-- border -->![Process](45b.png)

4. Complete your process:
    - Refresh your tasks
    - Check that the decision is reflected with the right notification task
    <!-- border -->![Process](46b.png)

[OPTION END]

### Process monitoring

1. Monitor the business process

    <!-- border -->![Process](17.png)

You have successfully completed the tutorial, integrating an SAP UI5 application in the order approval business process.

