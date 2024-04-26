---
author_name: Aviral Agarwal
author_profile: https://github.com/aviral-agarwal-sap
keywords: tutorial
auto_validation: true
time: 20
tags: [ tutorial>beginner, sap-conversational-ai>sap-business-technology-platform, tutorial>free-tier]
primary_tag: sap-conversational-ai>sap-build-process-automation
parser: v2
---

# Deploy and Test the Project
<!-- description --> Deploy the project and test the dropdown filtering

## Prerequisites
- Complete the tutorial [Connect Action Project to Dropdown in Form](spa-dropdown-value-help-filtering)

## You will learn
- to release and deploy the project
- to filter data in a dropdown
- to retrieve sample project from the Store

## Intro
In this tutorial, you will release and deploy the project created in the previous tutorial and test the dropdown filtering in the form.

### Release and deploy the business process project

1. In the project overview tab, select the **Release** option.

    <!-- border -->![Action Project](001.png)

2.  In the **Release Project** popup, select **Release**.

    <!-- border -->![Action Project](002.png)

3.  Select the **Deploy** option in the top-right corner.

    <!-- border -->![Action Project](003.png)

4. Choose an **Environment** and select **Deploy**.

    <!-- border -->![Action Project](environment.png)

5.  In the **Define Variables** section, select the destination variable `S4_Business_Partner` and select **Deploy**.

    <!-- border -->![Action Project](005.png)

    Your project is deployed.

    <!-- border -->![Action Project](006.png)

### Test the dropdown filtering in the form

1. Select the **Order Processing** process.

    <!-- border -->![Action Project](007.png)

2. Select the **Order Processing Form** artifact and copy the deployed form link.

    <!-- border -->![Action Project](008.png)

3. Paste the link into a new browser tab/window to open it.

4. Select the dropdown button for the **Customer Name** field. You can see all the customer names fetched by the action project from the S4/HANA database.

    <!-- border -->![Action Project](009.png)

5. In the **Customer Name** field, if you enter anything, the records will get filtered accordingly.

    <!-- border -->![Action Project](010.png)

    > The filtering is implemented only on the number of records mentioned in **$top** parameter of action project, since only those records are fetched and shown. 

    You have successfully completed releasing and deploying your project and tested the dropdown filtering in the Order Processing Form.

    
### Retrieve sample project from the store (Optional)

   > The entire project is available in the SAP Build Store as a sample and you can follow the below steps to retrieve the project and use it for reference.

This sample project can be downloaded from the SAP Build Store.

To retrieve this sample, please follow these steps:
    
1. From the SAP Build Lobby, navigate to Store.
   
2. Search for the sample project: **Sales Order Management (MI07)**.
   
3. Choose **Create from Template** to retrieve the sample and save it as a new project in your lobby.

    <!-- border -->![Store](store.png)

4. Choose **Create**.

    <!-- border -->![Create](create.png)

    Your project gets created in editable version. You may release and deploy it and run the project.
    
5. Navigate back to the lobby by clicking on the SAP logo.
  
    <!-- border -->![Project](project.png)

    You can see your project is available in the lobby.
  
    <!-- border -->![Lobby](lobby.png)

---

