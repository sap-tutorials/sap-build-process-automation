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

    ![Process](01.png)

2. Perform the following steps:

    - under the **Editable** version of your project
    - choose the **Import** button
    - select **Form** from the contextual menu

    ![Process](02.png)

3. Fill the Import Form details:

    - set the **Application ID**, the name of your SAP UI5 application you get from the *manifest.json* file
    - set the **Version**, the application version you get from the *manifest.json* file
    - provide a **Name**, an identifier and a description for your approval form
    - choose the **Import** button

    ![Process](03.png)

4. The form should open in the **Forms Editor**:

    - if you want to open the *manifest.json*, choose the **hyper link** button
    - close the **Forms Editor**

    ![Process](04.png)

### Update your Business Process

1. Open your **Order Processing** business process.

    ![Process](05.png)

2. Remove the current **Approval Form** designed by with **Forms Builder**.

    ![Process](06.png)

3. Add your imported **Order Approval UI Task** as approval into your business process.

    ![Process](07.png)

4. Connect the **reject** branch into the **Order Rejection Notification** form.

    ![Process](08.png)

5. Select the Order Approval UI Task, fill and map the required fields:

    - in the **Subject** field, enter **Review and approve order**, select **Order Number** from Order Processing Form, enter **and**, select **Ship To Party** from Order Processing Form
    - set the **Users** under **Recipients** with **Process Started By** from Process Metadata
    - choose the **Inputs** tab

    ![Process](09.png)

6. Map the required form **Inputs** accordingly.

    ![Process](10.png)

7. Select the **Order Confirmation Form** and map the required missing input accordingly.

    ![Process](11.png)

8. Select the **Order Rejection Notification** form.

    - map the required missing input accordingly

    ![Process](18.png)

9. Save your project.

10. Release your project.


### Deploy your project

1. Deploy your **Project** and retrieve the **Form Trigger** link for testing.

    ![Process](12.png)

2. Provide **Sales Order** data and test your process going through the approval process branch.

    ![Process](13.png)


### Check task in Inbox

[OPTION BEGIN [SAP Build Process Automation]]       
1. Open your **Inbox**.

    ![Process](14.png)

2. Review your approval task and take a decision.

    ![Process](15.png)

3. Complete your process:

    - Refresh your tasks
    - Check that the decision is reflected with the right notification task

    ![Process](16b.png)
[OPTION END]

[OPTION BEGIN [SAP Build Work Zone (Standard Edition)]]        
>Pre-requisite: Complete [Configure SAP Build Work Zone, Standard Edition ](spa-configure-workzone)tutorial

1. Once you have subscribed to SAP Build Work Zone, Standard Edition navigate to **Site Directory** and go to the site.

    ![Process](43.png)

2. Choose the **Inbox** tile.

    ![Process](44.png) 

3. Review your approval task and take a decision.

    ![Process](45b.png)

4. Complete your process:
   
    - Refresh your tasks
    - Check that the decision is reflected with the right notification task
  
    ![Process](46b.png)

[OPTION END]

### Process monitoring

1. Monitor the business process.

![Process](17.png)

You have successfully completed the tutorial, integrating an SAP UI5 application in the order approval business process.

### Retrieve sample project from the store (Optional)

> The entire project is available in the SAP Build Store as a sample and you can follow the below steps to retrieve the project and use it for reference.

To retrieve this sample, please follow these steps:
    
1. From the SAP Build Lobby, navigate to Store.
   
2. Search for the sample project: **Sales Order Management (MI08)**.
   
3. Choose **Create from Template** to retrieve the sample and save it as a new project in your lobby.

    ![Office](store.png)

4. Choose **Create**.

    ![Office](create.png)

    Your project gets created in editable version. You may release and deploy it and run the project.
    
5. Navigate back to the lobby by clicking on the SAP logo.
  
    ![Office](project.png)

    You can see your project is available in the lobby.
  
    ![Office](lobby.png)
