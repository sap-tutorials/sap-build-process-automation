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

# Add Action to a Dropdown in a Form
<!-- description --> Add action to a dropdown in the trigger form to connect to the backend system

## Prerequisites
- Complete the tutorial [Create Action Project in Lobby](spa-business-partner-action-create)

## You will learn
- to import a sample process from the store
- to implement action in the project
- to create a destination environment variable 
- to create a dropdown in trigger form with action response as the data source
- to add destination based environment variable in trigger form 

## Intro
In this tutorial, you will create a project using a template from the store. You will edit the trigger form and create a dropdown to populate it with action response as options.

### Import sample process as template

1.  In **SAP Build**, select the **Store** tab.

    <!-- border -->![Action Project](001.png)

1.  Search for **Sales Order** in the search bar.

    <!-- border -->![Action Project](002.png)

1.  In the search results, select the **Create From Template** option for the **Sales Order Approvals - Sample** project.

    <!-- border -->![Action Project](003.png)

1.  Enter the name of your choice in the Project Name text box and select **Create**.

    <!-- border -->![Action Project](004.png)

### Create a dropdown in order processing form

1.	Once the project is created, select the **Order Processing Form** from the side menu of artifacts.

    <!-- border -->![Action Project](005.png)

2. Select the menu for the **Customer Name** text field and select **Delete**.

    <!-- border -->![Action Project](006.png)

3. Drag and drop the **Dropdown** artifact in the form and enter the name as **Customer Name**.

    <!-- border -->![Action Project](007.png)

### Add environment variable to access destination

4. Select the **Settings** icon at the top-right corner.

    <!-- border -->![Action Project](009.png)


4. In the **Environment Variables** tab select **Create**.

    <!-- border -->![Action Project](010.png)

4. In the popup that appears, enter the following details.

    - Enter `S4_Business_Partner` as identifier.
    - Enter **Description** of your choice.
    - Select the **Type** as **Destination**.
    - Choose **Create**.

    <!-- border -->![Action Project](011.png)

4. Once the environment variable is created, close the popup.

    <!-- border -->![Action Project](012.png)


### Add action project to dropdown

1. For the **Customer Name** dropdown, choose **From data set** and select the value-helper for the **Data Source**.

    <!-- border -->![Action Project](008.png)

1. In the **Browse Library** popup, choose **GET** as **Action Type**. Select the **Add** option for the action project you created earlier.

    <!-- border -->![Action Project](013.png)

1. Select the `S4_Business_Partner` as the **Destination Variable** and select the value-help option for **Available Data** field.

    <!-- border -->![Action Project](014.png)

1. Choose the **Customer Name** option from the dropdown.

    <!-- border -->![Action Project](015.png)

1. **Save** the form.

    <!-- border -->![Action Project](016.png)
