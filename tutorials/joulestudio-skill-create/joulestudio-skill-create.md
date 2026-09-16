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


# Use Joule Studio, Classic Edition to Create and Deploy a Joule Skill
<!-- description --> Use Joule Studio, classic edition to create and deploy a Joule skill that consumes services from two different systems.

## Prerequisites

- Access to an SAP BTP tenant configured for Joule and Joule Studio, classic edition. See [Set Up Joule Studio, classic edition](https://help.sap.com/docs/Joule_Studio/45f9d2b8914b4f0ba731570ff9a85313/04b323352fa645238211ce017f634d34.html) or the [Discovery Center mission](https://discovery-center.cloud.sap/missiondetail/4651/4940/).
- You have [configured the destinations to the OData services](joulestudio-skill-environment-setup)
- You have [created and configured the action projects](joulestudio-skill-action-create)


## You will learn
  - How to consume action projects in a Joule skill
  - How to release and deploy the project containing the Joule skill
  - How to test the Joule skill in the standalone assistant


## Intro
Joule Studio classic in SAP Build is the design time focused on developing AI capabilities. Joule Studio classic gives SAP customers and partners the possibility to develop AI capabilities, such as custom Joule skills and custom AI agents, to extend the capabilities of Joule co-pilot and optimize organization-specific automation. 


### Create a Joule Skill

1. Open the **SAP Build Lobby**.

    > The lobby is a central page for creating, accessing, and managing your projects in SAP Build.

2. Choose **Create**.

    ![Lobby](joulestudio-skill-lobby.png)

3. Select the **Joule Skill** tile, then choose **Next**.

    ![Select Joule Skill](joulestudio-skill-lobby-create.png)

4. Enter name **`CreateBadge`** and description **`Create a badge for an employee given the employee's ID`**, then choose **Review**.

    ![Enter name and description](joulestudio-skill-create-project.png)

5. On the following screen choose **Create**.

6. Choose **Create** **>** **Joule Skill**.

    ![Joule Studio classic create](joulestudio-skill-create-skill.png)

7. Enter name **`CreateBadge`** and description **`Create a badge for an employee given the employee's ID`**, then choose **Create**.

    ![Joule Studio classic create popup](joulestudio-skill-create-skill-2.png)


    > The description is important because Joule will use it to identify the correct skill to select during a conversation.

    ![Joule Studio classic fresh project](joulestudio-skill-create-new.png)


### Define the Input and Output Parameters

1. Choose **Trigger** (or **<<**) to open the side panel.

2. Disable **Allow Joule to generate a response**.

    ![Open side panel for trigger](joulestudio-skill-trigger.png)

3. Choose **Parameters**, then choose **Configure** beside **Skill Inputs**.

    ![Open side panel for trigger](joulestudio-skill-parameters.png)


4. Choose **Add Input** three times and enter:

    |  Name               | Description         | Required
    |  :-------------     | :-------------      | :-------------
    |  **`EmployeeID`**   | **`Employee ID`**   | select
    |  **`Status`**       | **`Status`**        | 
    |  **`CommunityID`**    | **`Community ID`** | 


    ![Configure inputs](joulestudio-skill-inputs-configure.png)

7. Choose **Apply**.

8. Choose **Configure** beside **Skill Outputs**.

9. Choose **Add Output** three times and then enter:

    |  Name                | Description         | Type           | Required
    |  :-------------      | :-------------      | :------------- | :-------------
    |  **`Badge`**         | **`Badge`**         | **Number**     | select
    |  **`Employee ID`**   | **`Employee ID`**   | **String**     | select
    |  **`Employee Name`** | **`Employee name`** | **String**     | select



     ![Configure outputs](joulestudio-skill-outputs-configure.png)

11. Choose **Apply**.

12. Expand **Skill Outputs**.

     ![Output parameters](joulestudio-skill-outputs-configured.png)

13. Close the side panel.

14. Choose **Save**.

15. Choose **Design Console**. You should see errors.

     ![Design console errors](joulestudio-skill-errors.png)

16. Close the **Design Console**.


### Add First Action

1. Choose the **+** between **Trigger** and **End**.

    ![Joule Studio classic add action](joulestudio-skill-firstaction1.png)

2. Choose **Call Action**.

    ![Joule Studio classic browse all actions](joulestudio-skill-firstaction2.png)

3. Choose **Browse All Actions**.

    ![Joule Studio classic add action](joulestudio-skill-firstaction3.png)

4. Select the action **GET Retrieves business partner data by using business partner number** and then choose **Add**.

     ![Joule Studio classic create variable](joulestudio-skill-firstaction4.png)

5. Choose **Select a Destination**, then choose **+ Create a Destination Variable**.

    ![Joule Studio classic create variable](joulestudio-skill-firstaction5.png)

6. Enter **`S4HANA_MOCK`** and a description, then choose **Create**.

7. Select the destination variable.

    ![Joule Studio classic select variable](joulestudio-skill-firstaction6.png)

8. Choose **Inputs**, then choose the **`BusinessPartner`** field to open the **Skill Content** pane.

    ![Joule Studio classic map input](joulestudio-skill-firstaction7.png)

9. Choose **EmployeeID**.

10. Choose **Outputs** and expand the tree to see it.

     ![Joule Studio classic inspect output](joulestudio-skill-firstaction8.png)

11. Close the pane and then choose **Save**.

### Add Second Action

1. Choose the **+** between the first action and **End**.

    ![Joule Studio classic action](joulestudio-skill-secondaction2.png)

2. Choose **Call Action**.

    ![Joule Studio classic browse actions](joulestudio-skill-secondaction3.png)

3. Choose **Browse All Actions**.

    ![Joule Studio classic select action](joulestudio-skill-secondaction3b.png)

4. Select the action **POST Invoke action createBadge**, then choose **Add** beside it.

    ![Joule Studio classic create variable](joulestudio-skill-secondaction4.png)

5. **Choose Select a Destination**, then choose **+ Create a Destination Variable**.

    ![Joule Studio classic create variable](joulestudio-skill-secondaction5.png)

6. Enter **`Badge_Service`** and a description, then choose **Create**.

7. Select the **Badge_Service** destination variable.

8. Choose **Inputs**, then choose the **`businesspartnerId`** field to open the **Skill Content** pane.

9. Expand the tree in the **Skill Content** pane and map the fields as shown.

    ![Joule Studio classic map inputs](joulestudio-skill-secondaction6.png)

10. Choose **Outputs** and then expand the tree to see the **result**.

    ![Joule Studio classic inspect outputs](joulestudio-skill-secondaction7.png)

11. Close the pane and then choose **Save**.

### Define the Send Message

1. Choose the **+** between the second action and the **End** element.

    ![Add send message](joulestudio-skill-sendmessage.png)

2. Choose **Send Message**.

    ![Open message editor](joulestudio-skill-sendmessage-2.png)

3. Choose **Open Message Editor**.

    ![Message editor](joulestudio-skill-messageeditor.png)

4. Enter **`Badge Request`** in the **Title** field.

5. In the **Text** field, enter **`Badge has been created for`**. Then use **<>** to open Data Mapping and add the **`badgeId`** and **`firstname`** parameters. 

    ![Data mapping in message editor](joulestudio-skill-message-firstname.png)

6. In the **Illustration** field, choose an appropriate illustration.

7. Choose **Add Button**.

8. Enter **`Go to Badge System`**.

9. Enter **`https://dev-advocates-sap-build-full-66wu1vlc.launchpad.cfapps.us10.hana.ondemand.com/buildapps237846.buildapps237846/index.html`**

    ![Edited and previewed message](joulestudio-skill-message-finished.png)

10. Check the preview and then choose **Save**.

11. Close the side pane and choose **Save**.

### End Configuration

1. Choose **End**.

    ![Mapped data to skill outputs](joulestudio-skill-end-configuration.png)

2. Map the fields as shown.

3. Close the side pane and choose **Save**.

### Release and Deploy

1. Choose **Release**.

    ![Release](joulestudio-skill-project-release.png)

2. Choose **Release**.

    ![Released](joulestudio-skill-project-released.png)

3. Choose **Show Project Version** to change to the released version.

4. Choose **Deploy**.

    ![Deploy](joulestudio-skill-project-deploy-environment.png)

5. Select your environment and choose **Deploy**.

6. Select the respective destinations

    ![Destinations](joulestudio-skill-project-deploy-variables.png)

7. Choose **Deploy**.

    ![Deployed](joulestudio-skill-project-deployed.png)

### Test in Standalone Assistant

1. Go to the **SAP Build Lobby**.

2. Choose **Control Tower** -> **Environments**.

3. Choose your environment.

4. Choose **Joule**.

    ![Joule tab in environment](joulestudio-skill-assistant-launch.png)

5. Choose **Launch**.

    ![New conversation](joulestudio-skill-conversation-start.png)

6. Enter **`Please create a badge for the employee with the ID 1003764. The badge status is NEW and his community ID is john.doe@bestrunsap.com`**

7. Choose **Send**.

    ![Conversation result](joulestudio-skill-conversation-end.png)

8. Choose the **Go to Badge System** button.

    The logon screen for the application will appear.

9. Enter **User Name**: **`code`**, **Password**: **`me??Jam7`**, then choose **Continue**.

    >**CREDENTIALS LOCKED?:** Please note that the credentials are used by multiple people, and can lead to the credentials being locked. If they are locked, you can skip the rest of the step for viewing the creation of the badge within the UI.
    >
    >You can view the newly created badge in the OData service manually, by opening a browser and entering the following URL and replacing with your badge ID:
    >
    >`https://badges.cfapps.eu10.hana.ondemand.com/service/BadgeRequests/Badges?$filter=badgeId%20eq%2034`
    >
    >You will see the details about the badge.
    >
    >![Badge in Odata service](CheckBadgeOdata.png)
 
10. Find your Badge ID in the list of requests.

    ![Badge system list of badges](joulestudio-skill-accessprosystems.png)


### Test yourself


