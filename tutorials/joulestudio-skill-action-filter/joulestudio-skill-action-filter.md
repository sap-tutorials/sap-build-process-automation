---
author_name: Martin Plummer
author_profile: https://github.com/mhplum
keywords: tutorial
auto_validation: true
time: 20
tags: [ tutorial>beginner, software-product>sap-business-technology-platform, tutorial>license]
primary_tag: software-product>sap-build
parser: v2
---


# Create a Filter in an Action Project
<!-- description --> Create a filter in an action project to simplify the use of the OData service in Joule Studio.

## Prerequisites

- Access to an SAP BTP tenant configured for Joule and Joule Studio
- You have [configured the destinations to the OData services](joulestudio-skill-environment-setup)
- You have [created and configured the action projects](joulestudio-skill-action-create)


## You will learn
  - How to adjust the input of an action and create a custom filter
  - How to use the filter in a Joule skill
  - How to get Joule to automatically generate the conversation message

### Copy action project for BusinessPartner service

1. Open **SAP Build Lobby**.

    > The lobby is a central page for creating, accessing, and managing your projects in SAP Build.

2. Choose **Connectors**, then choose **Actions**.

    <!-- border -->
    ![Actions save as new project](joulestudio-skill-action1.png)

3. Select your API_BUSINESS_PARTNER action project, then choose **Versions**.

4. Choose **…** by the **Published to Library** version, then choose **Save As New Project**.

    <!-- border -->
    ![Save as new project popup](joulestudio-skill-action2.png)

5. Enter:
    - **`FilterBusinessPartners`** for the **Project Name**.
    - **`This is to give Joule access to information about business partners. An extra input field is added to simplify the use of the filter.`** for the **Description**.

6. Choose **Save As New**.

    <!-- border -->
    ![Actions](joulestudio-skill-action3.png)

7. Choose the new project.

    <!-- border -->
    ![Actions add input](joulestudio-skill-action4.png)

8. Choose the **GET Retrieves business partner general data** action.

9. On the **Input** tab, choose **Add**.

    <!-- border -->
    ![Actions add new field](joulestudio-skill-action5.png)

10. Choose **New Field**.

11. Enter **`FirstName`** as the **Key** and the **Label**, then choose **Add**.

12. Choose the **Value** field of **$filter**.

    <!-- border -->
    ![Filter popup](joulestudio-skill-action7.png)

13. In the side panel **$filter**, choose the **Value** field to open the **Condition Editor**.

     <!-- border -->
     ![Condition Editor](joulestudio-skill-action9.png)

14. For **Column**, **Condition**, and **Criteria**, select **`FirstName`**, **`equal to`**, and **`${FirstName}`** respectively. Then choose choose **OK**.

15. Choose the **Test** tab.

16. Enter **`Jane`** in the **FirstName** field, then choose **Test**.

     <!-- border -->
     ![Actions test](joulestudio-skill-action12.png)

17. Choose **Save**, then **Release**, and finally **Publish**.

     <!-- border -->
     ![Actions published](joulestudio-skill-action13.png)


### Create a Joule Skill 


1. Go to the **SAP Build Lobby**

    <!-- border -->
    ![Lobby](joulestudio-skill-skill1.png)


2. Choose **Create**.

    <!-- border -->
    ![Create Project](joulestudio-skill-skill2.png)

3. Choose **Joule Skill**, then choose **Next**.

4. Enter name **`SearchWithName`** and description **`Uses an Action containing a mapped condition to filter on the FirstName.`**.

    <!-- border -->
    ![Create Project](joulestudio-skill-skill3.png)

5. Choose **Review**, then choose **Create**.

6. In Joule Studio, choose **Create** **>** **Joule Skill**.

    <!-- border -->
    ![Joule Studio](joulestudio-skill-skill6.png)

7. Enter:
    - **`SearchWithFirstName`** for **Name**.
    - **`Retrieve information about employees with a given first name. Usually John or Jane is used`** for **Description**.

    <!-- border -->
    ![Create Joule Skill popup](joulestudio-skill-skill7.png)

8. Choose **Create**.

9. Choose **Trigger** to open the side panel.

10. Enable **Allow Joule to generate a response**.

    <!-- border -->
    ![Joule Studio generate responses](joulestudio-skill-skill10.png)

11. Choose **Parameters**, then choose **Configure** beside **Skill Inputs**.

    <!-- border -->
    ![Joule Studio parameters](joulestudio-skill-skill10c.png)

12. Choose **Add Input**. Enter **`FirstName`** for **Name**, **`First name of employee`** for **Description**, and select **Required**.

    <!-- border -->
    ![Joule Studio configure skill inputs](joulestudio-skill-skill12.png)

13. Choose **Apply**

14. Choose **Configure** beside **Skill Outputs**.

    <!-- border -->
    ![Joule Studio parameters](joulestudio-skill-skill12c.png)

15. Choose **Add Output**

16. Enter: 
    - **Name** **`Employees`** 
    - **Description** **`Employees`** 
    - **Type** **`Any`**
    - **List** **`Select`**

    <!-- border -->
    ![Joule Studio configure skill outputs](joulestudio-skill-skill12b.png)

17. Choose **Apply**.

15. Close the side pane and choose **Save**.

### Add Action to Joule Skill 

1. Choose the **+**.

    <!-- border -->
    ![Joule Studio select action](joulestudio-skill-skill14.png)

2. Choose **Action**.

    <!-- border -->
    ![Joule Studio browse actions](joulestudio-skill-skill15.png)

3. Choose **Browse All Actions**.

    <!-- border -->
    ![Joule Studio add action](joulestudio-skill-skill16.png)

4. Select the **GET Retrieves business partner general data** action of the project **FilterBusinessPartners** and choose **Add** beside it. 

5. Choose **Select a Destination Variable**, then **+ Create Destination Variable**.

6. Enter **`S4HANA_MOCK`** and **`BusinessPartner API`**, followed by **Create**.

    <!-- border -->
    ![Joule Studio destination variable](joulestudio-skill-skill17.png)

7. Select the destination variable.

8. Choose the **Inputs** tab.

9. Choose the **FirstName** field to open the **Skill Content** pane.

10. Choose **FirstName** in the **Skill Content** pane to map to the selected **FirstName** field.

    <!-- border -->
    ![Joule Studio map input](joulestudio-skill-skill20.png)

11. Choose the **Outputs** tab just to see the output.

    <!-- border -->
    ![Joule Studio outputs](joulestudio-skill-skill21.png)

12. Close the pane and choose **Save**.

### Configure End

1. Choose the **End** element.

2. Choose the **Employees** field to open the **Skill Content** pane.

22. Choose **{..} list - results**.

    <!-- border -->
    ![Joule Studio configure end](joulestudio-skill-skill22.png)

23. Choose **Save**.



### Release and Deploy

1. Choose **Release**.

    <!-- border -->
    ![Joule Studio release](joulestudio-skill-release2.png)

2. Choose **Release**.

    <!-- border -->
    ![Joule Studio show project version](joulestudio-skill-release3.png)

3. Choose **Show project version**, to change to the released version.

4. Choose **Deploy**.

    <!-- border -->
    ![Joule Studio deploy](joulestudio-skill-deploy1.png)

5. Select your environment and choose **Deploy**.

6. Select your **S4HANA_MOCK** destination and choose **Deploy**.

    <!-- border -->
    ![Joule Studio deployed](joulestudio-skill-deploy2.png)


### Test Joule Skill
1. Open the **SAP Build Lobby**

2. Choose **Control Tower**, then choose the **Environments** tile.

3. Choose your environment.

4. Choose the **Joule** tab.

    <!-- border -->
    ![Environment](joulestudio-skill-test5.png)

5. Choose **Launch**.

    <!-- border -->
    ![Joule conversation](joulestudio-skill-test6.png)

6. Choose **New Conversation**.

7. Enter **`I am at the front desk in the reception area. A person claiming to be an employee is here. Can you check if Jane is in the system?`** 

    <!-- border -->
    ![Joule conversation prompt](joulestudio-skill-test8.png)


8. Choose **Send**.

    <!-- border -->
    ![Joule conversation message](joulestudio-skill-test9.png)

9. Enter **`Thanks, I meant you to check if John is in the system.`**, then choose **Send**.

    <!-- border -->
    ![Joule conversation](joulestudio-skill-test10.png)

10. You can select any of the employees in the list to see their details.

### Test yourself




















