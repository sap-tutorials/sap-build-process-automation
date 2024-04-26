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

# Connect Action Project to Dropdown in Form
<!-- description --> Use and add a data source to the form dropdown field in order to display information from external systems

## Prerequisites
- Complete the tutorial [Create Business Partner Action Project in SAP Build Actions](spa-business-partner-action-create)

## You will learn
- How to use action project to retrieve data from data source and show in dropdown in form

## Intro
In this tutorial, you will create a project using a template from the store and edit the trigger form to create a dropdown and populate it with the values from the action project.

### Import sample process as template

1.  From the **SAP Build** lobby, select the **Store** tab.

    <!-- border -->![Import Project](ImportProject_31.png)

2. On the **Store** page, search for **Sales Order Management (MI01)** and once it loads, click **Create from Template**.

    <!-- border -->![Import Project](ImportProject_32.png)

3. In the **Project Name** field, enter **Sales Order Approvals Project**.
   
    > You can keep the default description or enter the description of your choice

    - Click **Create**.

    <!-- border -->![Import Project](ImportProject_33.png)

4. Open **Lobby** and you will see your project created.
   
5. Click on the **Sales Order Approvals Project** to open it.

    <!-- border -->![Import Project](ImportProject_34.png)


### Create a dropdown in order processing form


1.  Select the **Order Processing Form**.

    <!-- border -->![Action Project](005.png)

2. Select the menu for the **Customer Name** text field and select **Delete**.

    <!-- border -->![Action Project](006.png)

    You will now replace the text field with a dropdown field.

3. Drag and drop a **Dropdown** field in the form and enter the name as **Customer Name**.
   
4. Check the required box on the right side panel.
   
5. Choose **save**.

    <!-- border -->![Action Project](007.png)


### Add environment variable to access destination

1. Select the **Settings** icon at the top-right corner.

    <!-- border -->![Action Project](009.png)

2. In the **Project Properties** pop-up, select **Environment Variables** and choose **+ Create**.

    <!-- border -->![Action Project](010.png)

3. Fill in the information:

    - Enter `S4_Business_Partner` as identifier.
    - Enter **Description** of your choice.
    - Select the **Type** as **Destination**.
    - Choose **Create**.

    <!-- border -->![Action Project](011.png)

4. Once the environment variable is created, close the pop-up.

    <!-- border -->![Action Project](012.png)


### Add action project to dropdown

1. Select the **Customer Name** dropdown.
   
2. As **Data to display**, choose **Data Source**.
   
3. Select the value-help option for **Data Source** field.

    <!-- border -->![Action Project](008.png)

4. In the **Browse Library** pop-up, choose **GET** as **Action Type**. 
   
5. Select the **Add** option for the action project you created earlier.

    <!-- border -->![Action Project](013.png)

    > **CAUTION:** The action project will only be visible in the Browse Library pop-up if the Main Output Array is marked in the action response as described in previous tutorial.

6. Select the `S4_Business_Partner` as the **Destination Variable** and select the value-help option for **Available Data** field.

    <!-- border -->![Action Project](014.png)

7. Choose the **Customer Name** option from the dropdown.

    <!-- border -->![Action Project](015.png)

8. **Save** the form.

    <!-- border -->![Action Project](016.png)

    With this, you have created a form with dropdown as input field and connected your action project to the dropdown.
