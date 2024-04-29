---
parser: v2
author_name: Djamai Hania
author_profile: https://github.com/Haniadjamai
auto_validation: true
time: 40
tags: [ tutorial>beginner, software-product>sap-business-technology-platform, tutorial>free-tier ]
primary_tag: software-product>sap-build-process-automation
---

# Add a Subprocess to an Automation
<!-- description --> Learn how to use a subprocess in SAP Build Process Automation.

## Prerequisites
- Complete [Add Links to Forms](spa-add-links-forms)
- Complete [Agent Management Settings to Execute the Process with an Automation](spa-run-agent-settings)

## You will learn
  - How to add a subprocess in a process.
  - How to add a subprocess in an automation.
  - How to send tasks to multiple participants.

---

## Intro
Using subprocess in your automation enables you to easily reuse existing code segments in various processes. This re-usability eliminates the need for duplicating the same code multiple times, saving you valuable time and development efforts.

Furthermore, incorporating subprocess in your automation allows you to divide your tasks into smaller and more manageable units. This simplifies the comprehension and maintenance of your automated system.

---
### Create a subprocess in a process project

You will incorporate a subprocess within a primary process.

After completing the [prerequisites](spa-add-links-forms), your process will look like this:
    
<!-- border -->![subprocess](1a.png)

1. Navigate to the **Overview** tab. From the editable version of your project, click the **Create** dropdown and choose **Process**.

    <!-- border -->![subprocess](2a.png)

2. In the **Create Process** dialog box, do the following:

    - Enter a **Process Name** such as Manage Trainees Learning Journey.
    - Choose **Create**.

    <!-- border -->![subprocess](3.png)

    Your new process opens in the process builder. You will now create a trigger form that will start the process. 

    <!-- border -->![subprocess](4a.png)

3. Choose **Add a Trigger** in the **Trigger** settings.
   
    <!-- border -->![subprocess](4b.png)

4. Select **Submit a Form**.

    <!-- border -->![subprocess](4c.png)

5. Choose **Registration Form**.

    <!-- border -->![subprocess](4d.png)

6. Choose **Save**.

    <!-- border -->![subprocess](5a.png)

7. Navigate back to the **Overview** tab. Select the **Learning Path** process.

    <!-- border -->![subprocess](sub1a.png)

8. Choose the three dots of the Trigger form and select **Remove**.

9.  Choose **Save**.

    <!-- border -->![subprocess](30a.png)

10. Go back to **Manage Trainees Learning Journey** process, select **+** under **Registration Form**.

    <!-- border -->![subprocess](sub2a.png)

11. Choose **Subprocess**.

    <!-- border -->![subprocess](sub2b.png)

12. Choose **Learning Path**.

    <!-- border -->![subprocess](sub2c.png)

13. **Save** the process.

    Now you have an optimized process that incorporates a subprocess, making it more efficient and streamlined.

    <!-- border -->![subprocess](sub3a.png)


### Release, deploy and run the process project

1. To release and deploy a process, please refer to step 1 and 2 of the tutorial on how to release and deploy a process [Run the Business Process](spa-run-process).

2. In the **Overview** section, open the process **Manage Trainees Learning Journey** process of the deployed version, choose **Registration Form** and select the **Copy Link** icon next to the **Form Link** field.

    <!-- border -->![subprocess](sub4a.png)

3. Now paste the **Form Link** into a browser. When the form opens in the browser, you will have the course presentation fields that you defined in the Registration Form. Click on **Start**.    

    <!-- border -->![subprocess](sub5.png)

    Now, you will receive the training materials directly in your inbox, just like you did in the [Add Links to Forms](spa-add-links-forms) tutorial.

    >In the next steps, you will cover the usage of a subprocess within an automation and also demonstrate how to distribute the learning path to multiple learners simultaneously.


### Add a table to the registration form

After completing the steps above, your process will look like this:
    
   <!-- border -->![subprocess](sub3b.png)

1. From the editable version of your project, select the **Registration Form**, choose the three dots and select **Open Editor**.

     <!-- border -->![subprocess](6a.png)

2. Add a **Table** with **Learners** as title.

     <!-- border -->![subprocess](7a.png)

3. Choose the **+** icon in the table and select **Text**. 

    <!-- border -->![subprocess](8a.png)

4. Enter **First Name** as the field name.

    <!-- border -->![subprocess](8_1a.png)

5. Choose the **+** icon next to the First Name field and select **Text**. 

    <!-- border -->![subprocess](9a.png)

6. Enter **Last Name** as a field name.
   
    <!-- border -->![subprocess](9_1a.png)

7. Similarly choose the **+** icon next to the Last Name field and select **Text**. 

    <!-- border -->![subprocess](10a.png)

8. Enter **Emails** as a field name.
   
    <!-- border -->![subprocess](10_1a.png)

9.  **Save** the form.


### Create the automation

1. Navigate back to the **Manage Trainees Learning Journey** process.

2. Select the three dots next to the **Learning Path** subprocess and choose **Remove**.
    
    <!-- border -->![subprocess](11_0a.png)

    > ### What's going on?
    >
    > You will remove the subprocess from the main process. Our objective is to create an automation that utilizes the **Learning Path** subprocess to send the learning path to multiple users at once.

1. Now choose **+**.
  
    <!-- border -->![subprocess](11_0b.png)

2. Select **Automation**.

    <!-- border -->![subprocess](11_0c.png)

3. Select **Blank Automation**.

    <!-- border -->![subprocess](11a.png)

4. A pop up will appear to configure the Desktop Agent version. Do the following in the pop up:

    - From the dropdown, select the version of the Desktop Agent installed on your machine. It would be displayed with suffix as **Registered**.
    - Select your platform.
    - Choose the **Confirm** button.

    <!-- border -->![subprocess](12a.png)

5. A new pop-up will appear to create the automation. Do the following in the pop-up:

    -  Under Name enter: **Assign Learning Journey**.
    -  Choose the **Create** button.
    
    <!-- border -->![subprocess](13.png)

    An automation **Assign Learning Journey** will be created successfully.

6. Choose **Save**.
  
    <!-- border -->![subprocess](13_1a.png)


### Create data types

1. Go to the **Overview** Tab. Choose the **Create** button. Create an artifact of the type **Data Type**.

    <!-- border -->![subprocess](14a.png)

2. A new pop-up will appear.
    - Enter **Name** of the data type: **Learner**.
    - Choose **Create**.

    <!-- border -->![subprocess](15.png)

3.  In the Data Type **Learner** add 3 new fields as such:.

    |  Field Name           | Type
    |  :-------------       | :-------------
    |  `email`              | String
    |  `firstname`          | String
    |  `lastname`           | String

    <!-- border -->![subprocess](16.png)

    <!-- border -->![subprocess](17.png)

4. Choose **Save**.

    <!-- border -->![subprocess](17_1.png)

    Your data type gets created and you can view it in the list of artifacts in the **Overview** page.

    Now you will create a second data type.

5. Similarly, go to the **Overview** tab. Choose the **Create** button. Create an artifact of the type **Data Type**.

    <!-- border -->![subprocess](18a.png)

6. A new pop-up will appear.
    - Enter **Name** of the data type: **dataset**.
    - Choose **Create**.

    <!-- border -->![subprocess](19.png)

7.  In the Data Type **dataset** add a new field such as:

    |  Field Name           | Type
    |  :-------------       | :-------------
    |  `Learner`            | Learner

    <!-- border -->![subprocess](19_1.png)

8. Check List. 

9. Choose **Save**.

    <!-- border -->![subprocess](20.png)


### Configure the automation

1. Navigate back to the **Manage Trainees Learning Journey** process and select the three dots next to **Assign Learning Journey** automation, choose **Open Editor**.

    <!-- border -->![subprocess](21a.png)

2. In the Automation Details section on the right, search for the **For Each** activity and drag and drop the activity into the automation flow.

    <!-- border -->![subprocess](22.png)

3. Select the **Input/Output** section in Automation Details. 

    <!-- border -->![subprocess](23a.png)

4. Add an input parameter as following:

    - In Parameter Name enter: `learners`.
    - In Data Type choose: **Learner**.
    - Check **List**.

    <!-- border -->![subprocess](24.png)

5. Click on the **For Each**, enter the value of Set looping List as `learners`.

    <!-- border -->![subprocess](25.png)

6. Click on the canvas and select the **Processes** section in Automation Details. 

    <!-- border -->![subprocess](26.png)

7. Select **Learning Path** and drag and drop the activity into the automation flow inside the **For Each** loop.

    <!-- border -->![subprocess](27.png)

8. **Save** your work.


### Configure the subprocess

1. Go to the **Overview** tab. Select the **Learning Path** process.

    <!-- border -->![subprocess](29.png)

2. Open the **Process Details** side panel.
   
    <!-- border -->![subprocess](29a.png)
   
3. Select the **Variables** tab in Process Details.

4. For **Process Inputs**, select **Configure**.

    <!-- border -->![subprocess](31_1a.png)

5. Click on **add input**.

    <!-- border -->![subprocess](31_2.png)

6. Configure the **Process Input** as such: 

    - In Inputs Name enter: `learner`.
    - In Inputs Type choose: **Learner**. 

7. Select **Apply**.

    <!-- border -->![subprocess](32.png)

8. Now, click on **Build Your First Business Process** form and configure the **General** section.

9.  In the **Recipients** section, under **Users** select **email** from Process Inputs.

    <!-- border -->![subprocess](36a.png)

10.  Select the **Boost Your Business Process with Automation** form to configure the **General** section. In the **Recipients** section, under **Users** select **email**.

    <!-- border -->![subprocess](37a.png)

11. Similarly, select the **Create Tables in the Form** form to configure the **General** section. In the **Recipients** section, under **Users** select **email**.

    <!-- border -->![subprocess](38a.png)

12. **Save** your work.

13. Go to the **Overview** tab. Click on the **Assign Learning Journey** automation.

    <!-- border -->![subprocess](38_1.png)

14. Select **Learning Path** and enter the value of learner as `currentMember`.

    <!-- border -->![subprocess](38_2.png)

15. **Save** your work.

16. Navigate back to **Manage Trainees Learning Journey**, select **Assign Learning Journey** automation to configure the **Inputs** parameters.

17. In the **Inputs** section, in **Select list** field, choose **Learners**.

    <!-- border -->![subprocess](38_4a.png)

18. **Save** your work.


### Release and deploy the project

After completing [Agent Management Settings to Execute the Process with an Automation](spa-run-agent-settings) tutorial, you may release and deploy the process.

1. In the **Manage Trainees Learning Journey** process, choose the **Release** button on the top right corner.

    <!-- border -->![subprocess](39a.png)

2. In the **Release Project** popup, select **Release**.

    <!-- border -->![subprocess](40.png)

3. In the **Overview** section that appears, choose **Deploy**.

    <!-- border -->![subprocess](41a.png)

4. Choose an Environment and click on **Upgrade**.
   
    <!-- border -->![subprocess](41b.png)

    Your project is deployed.

    <!-- border -->![subprocess](45a.png)


### Run the process

1. In the **Overview** section, open the process **Manage Trainees Learning Journey** of the deployed version, select **Registration Form** and choose the **Copy Link** icon next to **Form Link** field.

    <!-- border -->![subprocess](46a.png)

2. In a new tab in your browser, paste the form link. Enter the information of the learners in the table for whom you intend to send the learning path and choose **Start**.

    <!-- border -->![subprocess](47a.png)
   
    > After clicking on **Start**, all the learners you have added to the table will receive the project tasks in their Inbox.

3. Navigate to **SAP Build** lobby, choose **My Inbox** icon.

    <!-- border -->![subprocess](48.png)

4. You will see the first task **First Learning Mission** appear in the My Inbox application that ships with SAP Build. The task will have the description of the training to be followed and the link to the tutorial. After finishing the mission, select **I have completed the first mission** and click on **Next**.

    <!-- border -->![subprocess](49.png)

5. Refresh the inbox again to get the second notification to the second mission. Now you can see task **Second Learning Mission** appear in My Inbox. After finishing the mission, click on **Next**.

    <!-- border -->![subprocess](50.png)

6. Similarly, refresh the inbox again to get the third mission. Once the mission is completed, click on **Done**.

    <!-- border -->![subprocess](51.png)


### Retrieve sample project from the store

This sample project can be downloaded from the SAP Build Store.

To retrieve this sample, please follow these steps:
    
1. From the SAP Build Lobby, navigate to Store.
   
2. Search for the sample project: **Learning Journey**.
   
3. Choose **Create from Template** to retrieve the sample and save it as a new project in your lobby.

    <!-- border -->![Store](store.png)

4. Give your project a name and choose **Create**.

    <!-- border -->![Create](create.png)

    Your project gets created in editable version. You may release and deploy it and run the project.
    
5. Navigate back to the lobby by clicking on the SAP logo.
  
    <!-- border -->![Project](project.png)

    You can see your project is available in the lobby.
  
    <!-- border -->![Lobby](lobby.png)

