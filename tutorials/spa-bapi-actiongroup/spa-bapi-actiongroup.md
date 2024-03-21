---
author_name: Aviral Agarwal
author_profile: https://github.com/aviral-agarwal-sap
keywords: tutorial
auto_validation: true
time: 20
tags: [ tutorial>beginner, software-product>sap-business-technology-platform, tutorial>free-tier]
primary_tag: software-product>sap-build-process-automation
parser: v2
---

# Connect BAPI using Action Group with SAP Build Process Automation
<!-- description -->Learn how to create BAPI Action Group which uses BAPI  Action and retrieves the data from the backend.

## Prerequisites
- [Desktop agent](https://developers.sap.com/tutorials/spa-setup-desktop-3-0-agent.html) version must be equal to or greater than 2.0.30.
- Install Microsoft Visual C++ 2010 Redistributable Package x86, available on the Microsoft website.
- For using SSO connection system, SSO (SAP Single Sign-On) must be configured on your system.
- BAPI with Remote-enabled Module.

## You will learn
- How to create an Action Group
- How to add BAPI Action in Action Group
- How to configure the Action Group

## Intro

> **IMPORTANT:** Please refer to sample **Connect BAPI using Action Group** in the SAP Build Store if you face any issues while following the tutorial. To retrieve the sample, refer to **step 7** of this tutorial.

BAPI is a standard interface to the business object model in SAP products. BAPIs are the primary methods through which customer code and third-party applications interact with SAP products. An Action Group is collection of actions that once executed, return some response. BAPI is part of an Action Group whose actions help you to construct the parameters to execute the BAPI module and return the BAPI response.

In this tutorial, you will create an Action Group Artifact and connect to `BAPI RFC_GET_TABLE` and query the **MAKT-Material Master** related table.

---

### Execute BAPI module in SAP GUI system

1. Login to SAP GUI application. Run the se37 transaction.

    <!-- border -->![Action Project](037.png)

2. Select the `RFC_READ_TABLE` module as the Function Module.

    <!-- border -->![Action Project](038.png)

3. Review the Import options for this module.

    <!-- border -->![Action Project](039.png)

4. When you execute the module, you get the following output.

    <!-- border -->![Action Project](040.png)

    This is the output we expect at the end of our automation. In the next steps you will be building an automation for the same.


### Create a project

1.  In the **SAP Build** Lobby, select the **Create** button.

    <!-- border -->![Action Project](001.png)

2. In the popup, select **Build an Automated Process**.

    <!-- border -->![Action Project](002.png)

3. Select **Task Automation** option.

    <!-- border -->![Action Project](003.png)

4. Enter your project name and select Create.

    <!-- border -->![Action Project](004.png)

5. In the **Configure Agent Version** popup that appears, select your desktop agent version. Select **Confirm**.

    <!-- border -->![Action Project](005.png)

6. In the **Create Automation** popup, enter the name of the automation and select **Create**.

    <!-- border -->![Action Project](006.png)


### Create BAPI Action Group Artifact

1.	Select the **+** icon in top-left corner. Select **Create** option and choose **Action Group**.

    <!-- border -->![Action Project](007.png)

2. In the **Create Action Group** popup, enter the name of your Action Group and set the Connection type to **Basic**.

    <!-- border -->![Action Project](008.png)

    > There are three types of connections in BAPI Connection System.
    SSO: This connection type allows you to set SSO connection. `SNCName`, `MessageServer`, `InstanceNumber` and Client are commonly used for this connection type. By default, `SNCMode` is set to true for this connection type.
    Basic: This connection type allows you to set Basic connection. User, Password, `MessageServer`, `InstanceNumber` and Client are commonly used for this connection type. By default, `SNCMode` is set to false for this connection type.
    Custom: This connection type allows you to set any other advance connection. You can add connection parameters as per your requirement. By default, `SNCMode` is set to false for this connection type. However, you can change the `SNCMode` value by adding the parameter.
    In the tutorial, you will use **Basic** Connection Type .

3. Open SAP Logon Pad. Select the system, right-click the connection and select **Properties**.

    <!-- border -->![Action Project](009.png)

4. Copy the details for your connection from the **System Entry Properties** to **Create Action Group** popup to let the Action Group connect with your system.

    <!-- border -->![Action Project](010.png)

5. In the **Connection Parameter** popup, enter your Username and Password and select **Create Connection**.

    <!-- border -->![Action Project](011.png)

### Add BAPI Action to the Action Group

Each Action Group artifact can have multiple actions. Each Action corresponds to a single BAPI selection.

1. In the BAPI  Editor, select **Create an action** option.

    <!-- border -->![Action Project](012.png)

2. In the **Create BAPI Action** popup, enter the Action name and select **Create**.

    <!-- border -->![Action Project](013.png)

3. In the next popup,
    - Enter the BAPI module name as `RFC_READ_TABLE`.
    - Select the search icon.
    - Select the BAPI module from the search results.
    - Select **Create**.

    <!-- border -->![Action Project](014.png)

4. In the Input tab, select the `QUERY_TABLE` and **ROWCOUNT** fields.

    <!-- border -->![Action Project](015.png)

5.  Select the **OUTPUT** tab. Select the **Data** field and choose **Save**.

    <!-- border -->![Action Project](016.png)

6. To test your BAPI module select the **Test** tab.
    - Enter the `QUERY_TABLE` as **MAKT**.
    - Enter the **ROWCOUNT** as 10.
    - Select the **Test** option.

    <!-- border -->![Action Project](033.png)

7. You can see the data fetched from the given table is shown in Response Preview.

    <!-- border -->![Action Project](034.png)


8. Select **Release**.

    <!-- border -->![Action Project](017.png)

9. In the Release popup, select **Release**.

    <!-- border -->![Action Project](018.png)

10. After releasing the Action Group you are redirected to the **Overview** page. Here you can see the input and output data types are automatically created according to the fields we selected in previous steps.

    <!-- border -->![Action Project](032.png)

### Edit the Automation

1. Select the **Execute BAPI module** automation.

    <!-- border -->![Action Project](019.png)

2. In the Automation Editor, search for **Try** control. Drag the control to the canvas.

    <!-- border -->![Action Project](020.png)

3. Select the **Try** control and set the **Error to catch** parameter to **Error**.

    <!-- border -->![Action Project](021.png)

4. Now search for your Action Group **BAPI Action Group** and drag and drop the **RFC Read Table Action** in the Try block.

    <!-- border -->![Action Project](022.png)

5. Once you add the **RFC Read Table Action**, the BAPI SDK will be automatically added which can be seen in project dependencies.

    <!-- border -->![Action Project](036.png)


5. Select the Action Group and enter your SAP Logon connection **Username** and **Password**.

    <!-- border -->![Action Project](023.png)

6. For the **BAPI Input**, select **Create Custom Data**.

    <!-- border -->![Action Project](024.png)

7.  For the **Imports** option, select **Create Custom Data**.

    <!-- border -->![Action Project](025.png)

8. Under the `QUERY_TABLE` input, enter the name of the table you want to read. In this use case, we are reading **MAKT** table. Enter the number of rows you want to query in **ROWCOUNT** input parameter.

    <!-- border -->![Action Project](026.png)

9. The parameter **Close Connection** closes the connection to your external system automatically. Hence you don't need to close the connection explicitly.

    <!-- border -->![Action Project](035.png)


10. Search for the **Log Message** process and drag it below step 2 - RFC Read Table Action.

    <!-- border -->![Action Project](027.png)

11. Select the **Log Message** step and in the **message** field, select **BAPI Response**.

    <!-- border -->![Action Project](028.png)

### Test your automation

1. Select the **Test** button in top-left corner.

    <!-- border -->![Action Project](029.png)

2. In the **Test Automation** popup, select **Test**.

    <!-- border -->![Action Project](030.png)

3. In the **Test Console** you can see the number of rows mentioned in row count have been fetched and displayed.

    <!-- border -->![Action Project](031.png)

With this, you have successfully created a BAPI Action Group that uses BAPI Action and retrieves the data from the backend in your automation.

### Retrieve sample project from the store (Optional)

   > The entire project is available in the SAP Build Store as a sample and you can follow the below steps to retrieve the project and use it for reference.
    
1. From the SAP Build Lobby, navigate to Store.
   
2. Search for the sample project: **Connect BAPI using Action Group**.
   
3. Choose **Create from Template** to retrieve the sample and save it as a new project in your lobby.

    <!-- border -->![Store](store.png)

4. Choose **Create**.

    <!-- border -->![Create](create.png)

    Your project gets created in editable version. You may release and deploy it and run the project.
    
5. Navigate back to the lobby by clicking on the SAP logo.
  
    <!-- border -->![Project](lobby.png)

    You can see your project is available in the lobby.
  
    <!-- border -->![Lobby](project.png)