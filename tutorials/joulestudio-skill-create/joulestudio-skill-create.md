---
author_name: Martin Plummer
author_profile: https://github.com/mhplum
keywords: tutorial
auto_validation: true
time: 30
tags: [ tutorial>beginner, software-product>sap-business-technology-platform, tutorial>license]
primary_tag: software-product>sap-build
parser: v2
---


# Use Joule Studio to Create and Deploy a Joule Skill
<!-- description --> Use Joule Studio to create and deploy a Joule skill that consumes services from two different systems.

## Prerequisites

- Access to an SAP BTP tenant with Joule and Joule Studio
- You have [configured the destinations to the OData services](joulestudio-skill-environment-setup)
- You have [created and configured the action projects](joulestudio-skill-action-create)


## You will learn
  - How to consume action projects in a Joule skill
  - How to release and deploy the project containing the Joule skill
  - How to test the Joule skill in the standalone assistant


## Intro
Joule Studio in SAP Build is the new design time focused on developing AI capabilities. Joule studio gives SAP customers and partners the possibility to develop AI capabilities, such as custom Joule skills and custom AI agents, to extend the capabilities of Joule co-pilot and optimize organization-specific automation. 


### Create a Joule Skill

1. Open the **SAP Build Lobby**.

    > The lobby is a central page for creating, accessing, and managing your projects in SAP Build.

    <!-- border -->
    ![Lobby](joulestudio-skill-lobby.png)

2. Choose **Create**.

    <!-- border -->
    ![Select Joule Skill](joulestudio-skill-lobby-create.png)

3. Select the **Joule Skill** tile, then choose **Next**.

    <!-- border -->
    ![Enter name and description](joulestudio-skill-create-project.png)

4. Enter name **`CreateBadge`** and description **`Create a badge for an employee given the employee's ID`**, then choose **Review**.

5. On the following screen choose **Create**.

    <!-- border -->
    ![Joule Studio create](joulestudio-skill-create-skill.png)

6. Choose **Create** **>** **Joule Skill**.

    <!-- border -->
    ![Joule Studio create popup](joulestudio-skill-create-skill-2.png)

7. Enter name **`CreateBadge`** and description **`Create a badge for an employee given the employee's ID`**, then choose **Create**.

    > The description is important because Joule will use it to identify the correct skill to select during a conversation.

    <!-- border -->
    ![Joule Studio fresh project](joulestudio-skill-create-new.png)


### Define the Input and Output Parameters

1. Choose **Trigger** (or **<<**) to open the side panel.

    <!-- border -->
    ![Open side panel for trigger](joulestudio-skill-trigger.png)

2. Disable **Allow Joule to generate a response**.

    <!-- border -->
    ![Open side panel for trigger](joulestudio-skill-parameters.png)

3. Choose **Parameters**, then choose **Configure** beside **Skill Inputs**.

    <!-- border -->
    ![Configure inputs](joulestudio-skill-inputs-configure.png)

4. Choose **Add Input** three times and enter:

    |  Name               | Description         | Required
    |  :-------------     | :-------------      | :-------------
    |  **`EmployeeID`**   | **`Employee ID`**   | select
    |  **`Status`**       | **`Status`**        | 
    |  **`CommunityID`**    | **`Community ID`** | 

7. Choose **Apply**.

8. Choose **Configure** beside **Skill Outputs**.

9. Choose **Add Output** three times and then enter:

    |  Name                | Description         | Type           | Required
    |  :-------------      | :-------------      | :------------- | :-------------
    |  **`Badge`**         | **`Badge`**         | **Number**     | select
    |  **`Employee ID`**   | **`Employee ID`**   | **String**     | select
    |  **`Employee Name`** | **`Employee name`** | **String**     | select



     <!-- border -->
     ![Configure outputs](joulestudio-skill-outputs-configure.png)

11. Choose **Apply**.

12. Expand **Skill Outputs**.

     <!-- border -->
     ![Output parameters](joulestudio-skill-outputs-configured.png)

13. Close the side panel.

14. Choose **Save**.

15. Choose **Design Console**. You should see errors.

     <!-- border -->
     ![Design console errors](joulestudio-skill-errors.png)

16. Close the **Design Console**.


### Add First Action

1. Choose the **+** between **Trigger** and **End**.

    <!-- border -->
    ![Joule Studio add action](joulestudio-skill-firstaction1.png)

2. Choose **Call Action**.

    <!-- border -->
    ![Joule Studio browse all actions](joulestudio-skill-firstaction2.png)

3. Choose **Browse All Actions**.

    <!-- border -->
    ![Joule Studio add action](joulestudio-skill-firstaction3.png)

4. Select the action **GET Retrieves business partner data by using business partner number** and then choose **Add**.

     <!-- border -->
     ![Joule Studio create variable](joulestudio-skill-firstaction4.png)

5. Choose **Select a Destination**, then choose **+ Create a Destination Variable**.

    <!-- border -->
    ![Joule Studio create variable](joulestudio-skill-firstaction5.png)

6. Enter **`S4HANA_MOCK`** and a description, then choose **Create**.

7. Select the destination variable.

    <!-- border -->
    ![Joule Studio select variable](joulestudio-skill-firstaction6.png)

8. Choose **Inputs**, then choose the **`BusinessPartner`** field to open the **Skill Content** pane.

    <!-- border -->
    ![Joule Studio map input](joulestudio-skill-firstaction7.png)

9. Choose **EmployeeID**.

10. Choose **Outputs** and expand the tree to see it.

     <!-- border -->
     ![Joule Studio inspect output](joulestudio-skill-firstaction8.png)

11. Close the pane and then choose **Save**.

### Add Second Action

1. Choose the **+** between the first action and **End**.

    <!-- border -->
    ![Joule Studio action](joulestudio-skill-secondaction2.png)

2. Choose **Call Action**.

    <!-- border -->
    ![Joule Studio browse actions](joulestudio-skill-secondaction3.png)

3. Choose **Browse All Actions**.

    <!-- border -->
    ![Joule Studio select action](joulestudio-skill-secondaction3b.png)

4. Select the action **POST Invoke action createBadge**, then choose **Add** beside it.

    <!-- border -->
    ![Joule Studio create variable](joulestudio-skill-secondaction4.png)

5. **Choose Select a Destination**, then choose **+ Create a Destination Variable**.

    <!-- border -->
    ![Joule Studio create variable](joulestudio-skill-secondaction5.png)

6. Enter **`Badge_Service`** and a description, then choose **Create**.

7. Select the **Badge_Service** destination variable.

8. Choose **Inputs**, then choose the **`businesspartnerId`** field to open the **Skill Content** pane.

9. Expand the tree in the **Skill Content** pane and map the fields as shown.

    <!-- border -->
    ![Joule Studio map inputs](joulestudio-skill-secondaction6.png)

10. Choose **Outputs** and then expand the tree to see the **result**.

    <!-- border -->
    ![Joule Studio inspect outputs](joulestudio-skill-secondaction7.png)

11. Close the pane and then choose **Save**.

### Define the Send Message

1. Choose the **+** between the second action and the **End** element.

    <!-- border -->
    ![Add send message](joulestudio-skill-sendmessage.png)

2. Choose **Send Message**.

    <!-- border -->
    ![Open message editor](joulestudio-skill-sendmessage-2.png)

3. Choose **Open Message Editor**.

    <!-- border -->
    ![Message editor](joulestudio-skill-messageeditor.png)

4. Enter **`Badge Request`** in the **Title** field.

5. In the **Text** field, enter **`Badge has been created for`**. Then use **<>** to open Data Mapping and add the **`badgeId`** and **`firstname`** parameters. 

    <!-- border -->
    ![Data mapping in message editor](joulestudio-skill-message-firstname.png)

6. In the **Illustration** field, choose an appropriate illustration.

7. Choose **Add Button**.

8. Enter **`Go to Badge System`**.

9. Enter **`https://dev-advocates-sap-build-full-66wu1vlc.launchpad.cfapps.us10.hana.ondemand.com/buildapps237846.buildapps237846/index.html`**

    <!-- border -->
    ![Edited and previewed message](joulestudio-skill-message-finished.png)

10. Check the preview and then choose **Save**.

11. Close the side pane and choose **Save**.

### End Configuration

1. Choose **End**.

    <!-- border -->
    ![Mapped data to skill outputs](joulestudio-skill-end-configuration.png)

2. Map the fields as shown.

3. Close the side pane and choose **Save**.

### Release and Deploy

1. Choose **Release**.

    <!-- border -->
    ![Release](joulestudio-skill-project-release.png)

2. Choose **Release**.

    <!-- border -->
    ![Released](joulestudio-skill-project-released.png)

3. Choose **Show Project Version** to change to the released version.

4. Choose **Deploy**.

    <!-- border -->
    ![Deploy](joulestudio-skill-project-deploy-environment.png)

5. Select your environment and choose **Deploy**.

6. Select the respective destinations

    <!-- border -->
    ![Destinations](joulestudio-skill-project-deploy-variables.png)

7. Choose **Deploy**.

    <!-- border -->
    ![Deployed](joulestudio-skill-project-deployed.png)

### Test in Standalone Assistant

1. Go to the **SAP Build Lobby**.

2. Choose **Control Tower** -> **Environments**.

3. Choose your environment.

4. Choose **Joule**.

    <!-- border -->
    ![Joule tab in environment](joulestudio-skill-assistant-launch.png)

5. Choose **Launch**.

    <!-- border -->
    ![New conversation](joulestudio-skill-conversation-start.png)

6. Enter **`Please create a badge for the employee with the ID 1003764. The badge status is NEW and his community ID is john.doe@bestrunsap.com`**

7. Choose **Send**.

    <!-- border -->
    ![Conversation result](joulestudio-skill-conversation-end.png)

8. Choose the **Go to Badge System** button.

9. Enter **User Name**: **`code`**, **Password**: **`me??Jam7`**, then choose **Continue**.

10. Find your Badge ID in the list of requests.

    <!-- border -->
    ![Badge system list of badges](joulestudio-skill-accessprosystems.png)


### Test yourself


