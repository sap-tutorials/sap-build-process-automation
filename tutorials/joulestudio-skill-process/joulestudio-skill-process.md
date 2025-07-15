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


# Consume an Automated Process in a Joule Skill
<!-- description --> Create a automated process and consume it in a Joule Skill.

## Prerequisites

- Access to an SAP BTP tenant with Joule and Joule Studio
- Email has been configured for Process Automation



## You will learn
  - How to create an automated process
  - How to publish the process to the library 
  - How to use the process in a Joule skill
  

## Details
You will create an automated process but existing content for SAP Build Process Automation can also be used within Joule skills. In the current release,  you can pass values to the input parameters of a process triggered from a Joule skill but you cannot use the output parameters of the process to return values to the Joule skill - it is "fire and forget".

In order for a process to be visible in Joule Studio, the process must have been published to the library - you need to remember to release, deploy, and then publish. You publish from within the Lobby.

In this tutorial, you will create a simple automated process for sending an email. The example extends the badge scenario used in the previous tutorials but the Joule skill is not dependent on the other skills.


### Create a Project for the Automated Process

1. Open the **SAP Build Lobby**.

    > The lobby is a central page for creating, accessing, and managing your projects in SAP Build.

    <!-- border -->
    ![Lobby](joulestudio-skill-process-create1.png)

2. Choose **Create**.
    <!-- border -->
    ![Create automated process](joulestudio-skill-process-create2.png)

3. Choose **Automated Process** then choose **Next**.

    <!-- border -->
    ![Create process](joulestudio-skill-process-create3.png)

4. Choose **Process**, then choose **Next**.

    <!-- border -->
    ![Name and description](joulestudio-skill-process-create4.png)

5. Enter **`InitiateSecurityChecksViaEmail`** for the **Name**, and **`When a badge is reported as lost or stolen, contact security via email`** for the **Description**. Choose **Review**.

    <!-- border -->
    ![Create project](joulestudio-skill-process-create5.png)

6. Choose **Create**.

### Create an Automated Process

1. In the Process Automation editor, choose **Create**.

    <!-- border -->
    ![Process Automation create process](joulestudio-skill-process-create6.png)


2. Enter **`SendEmailToSecurity`** and **`Report stolen or lost badge to security via email`**. Then choose **Create**.

    <!-- border -->
    ![Process Automation open side panel](joulestudio-skill-process-create7.png)

3. Choose **<<** to open the side panel.

    <!-- border -->
    ![Process Automation variables](joulestudio-skill-process-create8.png)

4. Choose the **Variables** tab and then choose **Configure** beside **Process Inputs**.

5. Choose **Add Input** four times and then enter:

    |  Name               | Description        | Required
    |  :-------------     | :-------------     | :-------------
    |  **`EmployeeID`**   | **`Employee ID`**  | select
    |  **`BadgeStatus`**  | **`Badge status`** | select
    |  **`FirstName`**    | **`First name`**   | select
    |  **`LastName`**     | **`Last name`**    | select



     <!-- border -->
     ![Configure Process Inputs](joulestudio-skill-process-create9.png)


6. Choose **Apply**.

    <!-- border -->
    ![Process Automation save](joulestudio-skill-process-create10.png)

7. Close the side panel and choose **Save**.

8. Choose the **+** before the **End** element.

    <!-- border -->
    ![Select Email](joulestudio-skill-process-create11.png)

9. Choose **Email**.

10. Enter an email address in the **To** field and **`Lost Badge`** in the **Subject** field.

    <!-- border -->
    ![Configure Email](joulestudio-skill-process-create13.png)

11. Choose **Open Mail Body Editor**.

12. Expand the **Process Inputs** in **Value Binding**. Use these to construct an email text.

    <!-- border -->
    ![Email Editor](joulestudio-skill-process-create14b.png)

13. Choose **Apply**.

    <!-- border -->
    ![Process Automation finished](joulestudio-skill-process-create15.png)

14. Close the side panel and choose **Save**.

### Release, Deploy and Publish the Process

1. Choose **Release**.

    <!-- border -->
    ![Process Automation release](joulestudio-skill-process-release1.png)

2. Choose **Release**.

3. Choose **Show project version** to change to the released version.

    <!-- border -->
    ![Process Automation deploy](joulestudio-skill-process-release3.png)

4. Choose **Deploy**. Then select your environment and choose **Deploy**.


    <!-- border -->
    ![Process Automation deployed](joulestudio-skill-process-release4.png)


6. Go to the **Lobby** and choose the **Versions** tab for the project.

    <!-- border -->
    ![Lobby publish to library](joulestudio-skill-process-publish1.png)

7. Choose **…** beside **Deployed**, then choose **Publish to Library**.

8. In the popup, choose **Publish**.

    <!-- border -->
    ![Lobby published](joulestudio-skill-process-publish3.png)

### Create a Joule Studio Project

1. Open the **SAP Build Lobby**.

    <!-- border -->
    ![Lobby](joulestudio-skill-process-skill1.png)

2. Choose **Create**.

    <!-- border -->
    ![Create Project joule skill](joulestudio-skill-process-skill2.png)

3. Choose **Joule Skill** then choose **Next**.

    <!-- border -->
    ![Create Project name and description](joulestudio-skill-process-skill3.png)


4. Enter name **`BadgeSecurity`** and description **`Contact security when a badge is reported lost or stolen.`** 

5. Choose **Review**.

    <!-- border -->
    ![Create Project review](joulestudio-skill-process-skill4.png)

6. Choose **Create**.

### Create a Joule Skill and Configure Inputs

1. In Joule Studio, choose **Create** **>** **Joule Skill**.

    <!-- border -->
    ![Joule Studio create joule skill](joulestudio-skill-process-skill5.png)

    <!-- border -->
    ![Joule Studio create joule skill popup](joulestudio-skill-process-skill6.png)

2. Enter name **`BadgeSecurity`** and description **`Contact security when a badge is lost or stolen`**, then choose **Create**.

    <!-- border -->
    ![Joule Studio parameters](joulestudio-skill-process-skill7.png)

3. Choose the **Trigger** element to open the side panel and there disable **Allow Joule to generate a response**.

4. Choose **Parameters**, then choose **Configure** beside **Skill Inputs**.

    <!-- border -->
    ![Joule Studio parameters](joulestudio-skill-process-skill7b.png)

5. Choose **Add Input** four times and enter the following parameters:

    |  Name               | Description        | Required
    |  :-------------     | :-------------     | :-------------
    |  **`Employee ID`**  | **`Employee ID`**  | select
    |  **`BadgeStatus`**  | **`Badge status`** | select
    |  **`First Name`**   | **`First name`**   | select
    |  **`Last Name`**    | **`Last name`**    | 


    <!-- border -->
    ![Joule Studio configure skill inputs](joulestudio-skill-process-skill8.png)

6. Choose **Apply**.

    <!-- border -->
    ![Joule Studio skill inputs](joulestudio-skill-process-skill9.png)

7. Expand **Skill Outputs** to see that there are no outputs configured.

    <!-- border -->
    ![Joule Studio skill outputs](joulestudio-skill-process-skill10.png)

8. Close the side panel and choose **Save**.

### Configure Email Process

1. Choose the **+** between **Trigger** and **End**.

    <!-- border -->
    ![Joule Studio select process](joulestudio-skill-process-skill11.png)

2. Choose **Run Process**.

    <!-- border -->
    ![Joule Studio browse processes](joulestudio-skill-process-skill12.png)


3. Choose **Browse All Processes**.

    <!-- border -->
    ![Joule Studio add process](joulestudio-skill-process-skill13.png)


4. Select your **SendEmailToSecurity** process and choose **Add**.

    <!-- border -->
    ![Joule Studio inputs](joulestudio-skill-process-skill14.png)

5. Choose the **Inputs** tab and choose the **BadgeStatus** field to open the **Skill Content** panel.

6. Select **BadgeStatus** in the **Skill Content** panel to map to the input parameter.

7. Similarly map the rest of the fields with the corresponding inputs.

    <!-- border -->
    ![Joule Studio map inputs](joulestudio-skill-process-skill15.png)

8. Close the side panel and choose **Save**.

### Configure Send Message

1. Choose the **+** before **End**.

    <!-- border -->
    ![Joule Studio send message](joulestudio-skill-process-skill16.png)

2. Choose **Send Message**.

    <!-- border -->
    ![Joule Studio open message editor](joulestudio-skill-process-skill17.png)

3. Choose **Open Message Editor**.

    <!-- border -->
    ![Joule Studio message configuration](joulestudio-skill-process-skill18.png)

4. Enter:
    - **`Security has been Informed`** for the **Title**.
    - **`Badge status ${parameter} for employee ${parameter} has been reported to security`** for the **Text**. Replace parameter with the relevant parameter - use data mapping, **<>**, for entering the parameters.

    <!-- border -->
    ![Joule Studio message configured](joulestudio-skill-process-skill19.png)

5. Choose **Save**.

6. Close the side panel and choose **Save**.

7. Choose **End** element and see that you have not defined any skill outputs.



### Release and Deploy the Joule Skill

1. Choose **Release**.

    <!-- border -->
    ![Joule Studio release](joulestudio-skill-process-skill20.png)

2. In the **Release Project** popup, choose **Release**.

    <!-- border -->
    ![Joule Studio show project version](joulestudio-skill-process-skill21.png)

3. Choose **Show project version** to change to the **Released** version.

    <!-- border -->
    ![Joule Studio deploy](joulestudio-skill-process-skill22.png)

4. Choose **Deploy**.

5. Select your environment and then choose **Deploy**.


### Test Joule Skill
1. Open the **SAP Build Lobby**

2. Choose **Control Tower**, then choose the **Environments** tile.

3. Choose your environment.

4. Choose the **Joule** tab.

    <!-- border -->
    ![Environment](joulestudio-skill-process-test3.png)

5. Choose **Launch**.

6. Choose **New Conversation**.

    <!-- border -->
    ![Joule new conversation](joulestudio-skill-process-test4.png)

7. Enter **`Please report to security that the old badge of John Doe 1003764 has the status LOST`** 

8. Choose **Send**.

    <!-- border -->
    ![Joule conversation](joulestudio-skill-process-test5.png)

9. You can check if the process has been called by going to **Monitoring** **>** **Process and Workflow Instances**.

    <!-- border -->
    ![Monitoring](joulestudio-skill-process-test6.png)


### Test yourself


