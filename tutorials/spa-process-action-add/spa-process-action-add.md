---
author_name: Archana Shukla
author_profile: https://github.com/ArchanaShukla
keywords: tutorial
auto_validation: true
time: 20
tags: [ tutorial>beginner, software-product>sap-business-technology-platform]
primary_tag: software-product>sap-build-process-automation
parser: v2
---

# Add Action to Business Process
<!-- description --> Add the action in the business process to connect to the backend system

## You will learn
- to import sample process
- to discover action from action library
- to add and configure action to the business process
- to map input fields of the action to the actual process content
- to release and deploy business process with actions

## Intro
Learn how to add the action in the business process to connect to backend system. You can do this by choosing the relevant action from the actions library, and then configuring the action's parameters.

### Import sample process as template

1. From the **SAP Build Lobby**, click on the **Store** tab.

    <!-- border -->![Import Project](ImportProject_31.png)

2. On the **Store** page, search for **Sales Order Approvals - Sample** and once it loads, click **Create from Template**.

    <!-- border -->![Import Project](ImportProject_32.png)

3. In the **Project Name** field, enter **Sales Order Approvals**.
    > You can keep the default description or enter the description of your choice

    - click **Create**.

    <!-- border -->![Import Project](ImportProject_33.png)

4. Open **Lobby** and you will see your project created.

    <!-- border -->![Import Project](ImportProject_34.png)


### Add environment variable to access destination

1. Click to open **Sales Order Approvals** business process project from the **Lobby**.
    > When you open for the first time then you might get an option to Accept.

    <!-- border -->![Import Project](ImportProject_35.png)

1. Click to open **Order Processing** process.
    - From your project overview section,
        - In the process builder, click to open **Project Properties** from top-right corner of the page.

    <!-- border -->![Destination](destination_04.png)

2. In the **Project Properties** pop-up, select **Environment Variables** and choose **Create** to create an environment variable for this business processes.

    <!-- border -->![Destination](destination_05.png)

3. Enter the following to create an environment variable:

    - **S4HANACloud** as **Identifier**.
    - Any **Description** of your choice.
    - **Destination** as variable type.

    <!-- border -->![Destination](destination_05a.png)

    - Click **Create**.

4. Once the environment variable is created, **Close** the project properties' pop-up.

    <!-- border -->![Destination](destination_06.png)

### Add action

1. In the Process Builder canvas, click the **+** in output connector of **Auto Approval Notification**.

    <!-- border -->![Add Artifact](action1.png)

2. In the list, choose **Actions** > **Browse library**.

    <!-- border -->![Browse Action](action2.png)

3. In the action library pop up, enter the action name like Sales Order, to find the list of actions on sales order published by you in the library.

    <!-- border -->![Search Action](action3.png)

4. From the filtered list of actions, click **Add** on the action which is to create sales order.

    > This will add the action to connect process to the backend system in your business process.

    <!-- border -->![Add Action](action4.png)


### Configure action

1. In **General** tab of action parameters, choose the corresponding **Destination variable** that you previously created.

    <!-- border -->![Add Destination Variable](action5.png)

2. Click **Inputs** tab, and map each input to the actual process content.


    |  Input Field         |  Process Content
    |  :-------------------|  :-------------
    |  `DistributionChannel` |  Order Processing Form > Distribution Channel
    |  `OrganizationDivision` |  Order Processing Form > Division
    |  `PurchaseOrderByCustomer` |  Order Processing Form > Order Number
    |  `SalesOrderType` |  Order Processing Form > Sales Order Type
    |  `SalesOrganization` |  Order Processing Form > Sales Organisation
    |  `SoldToParty` |  Order Processing Form > Ship To Party (Customer)


    <!-- border -->![Map Inputs](action6.png)


3. In **Outputs** tab, check to make sure all outputs are same as defined in the action project.

    <!-- border -->![Check Outputs](action7.png)

4. Finally, update the connections of **Order Confirmation Form** activity in the business process such that once the order is confirmed the sales order is created in the backend system.

    - select and delete the output connector from **Order Confirmation Form** to **End** activity.

    <!-- border -->![Select and delete connector](action9.png)

    - Drag and drop the **+** in the output connector of **Order Confirmation Form** to the action activity.

    <!-- border -->![Drag and drop connector](action10.png)

    > You can connect these nodes by simply dragging and dropping the lines. If a connected line can't be moved, simply click and delete the line, then drag and drop the resulting unconnected line to the proper node.

    The final process should be same as shown below. Ensure that you have the right connections such that *Auto Approval Notification Form* and *Order Confirmation Form* connects to *Action* activity.

    <!-- border -->![Deployed](action11.png)

5. Click **Save** to save your work.

### Release business process project

You will now release and deploy your project. The release process allows for semantic version control with format X.Y.Z, where you will be able to increment your project release version based on a major version change (X), minor version change (Y), or bug/patch version change (Z). Deploying your project will allow you to set the proper parameters, if necessary, to allow for project execution.

There are two possible situations:

- When you're releasing a new business process project, enter a brief summary of the changes in the **Release Notes** (optional) then choose **Release**.
- When you're releasing a modified version of a business process project that is already released, in the release **Version Contains dialogue**, select one of the following:
    - Select **Bug Fix** to indicate bug fixes. It updates the third digit of the version number.
    - Select **Minor Changes** to indicate small modifications. It updates the second digit of the version number.
    - Select **Major Changes** to indicate important modifications potentially leading to incompatibility between versions. It updates the first digit of the version number.


1. In the Process Builder, click **Release**.

    <!-- border -->![Release](release1.png)

2. For the first version, add a **Version Comment** if needed and click **Release**.

    <!-- border -->![Release first](release2.png)

    - For the additional version, choose the type of version, add a **Version Annotation** if needed and click **Release**.

    <!-- border -->![Release new](release3.png)

3. The successfully released project is ready to be deployed.

    > If needed, you can refer to the [Documentation](https://help.sap.com/docs/PROCESS_AUTOMATION/a331c4ef0a9d48a89c779fd449c022e7/bcb638ecb98d4e1db8267ecccd8ffdf3.html?version=Cloud).

    <!-- border -->![Released](release4.png)


### Deploy released project

You can deploy business process projects from each released version of the project in the Process Builder or through Lobby.

1. From the released version of the business process project in the Process Builder, click **Deploy**.

    <!-- border -->![Start Deploy](deploy1.png)

2. In the **Deploy Sales Order Approvals version 1.0.0** window, choose **Next**.

    <!-- border -->![Start Deploy](deploy1a.png)

3. Now you will set the runtime variables. From the drop-down select the destination **S4HANACloud** and click **Next**.

    > Variables allow you to reuse certain information for a given business process project deployment.

    > You use variables to pass parameters to automations. You can create variables in the Process Builder for which you can later set values when deploying the business process project. For example, in the current use case, you have created a *Destination* variable. Please use the same destination *S4HANACloud*.

    <!-- border -->![Deploy confirm first](deploy2.png)

4. Click **Deploy**.

    <!-- border -->![Deploy](deploy3.png)

    The successfully deployed project is ready for running and monitoring.

    > If needed, you can refer to the [Documentation](https://help.sap.com/docs/PROCESS_AUTOMATION/a331c4ef0a9d48a89c779fd449c022e7/d1e6a2d496f24ef1be43c2da8716c3b6.html?version=Cloud).

    <!-- border -->![Deployed](deploy4.png)

    You've successfully imported a sample process, added an action to create a sales order and configure the action with the environment variable to get the connection details from destination in SAP BTP cockpit.
