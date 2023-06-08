---
parser: v2
author_name: Djamai Hania
author_profile: https://github.com/Haniadjamai
auto_validation: true
time: 40
tags: [ tutorial>beginner, software-product>sap-business-technology-platform, tutorial>free-tier ]
primary_tag: software-product>sap-build-process-automation
---

# Add a Sub-Process to an Automation
<!-- description --> Learn how to use a sub-process in SAP Build Process Automation.

## Prerequisites
- Complete [Add Links to Forms](spa-add-links-forms)
- Complete [Agent Management Settings to Execute the Process with an Automation](spa-run-agent-settings)

## You will learn
  - How to add a sub-process in a process.
  - How to add a sub-process in an automation.
  - How to send tasks to multiple participants.

---

## Intro
Using sub-processes in your automation enables you to easily reuse existing code segments in various processes. This re-usability eliminates the need for duplicating the same code multiple times, saving you valuable time and development efforts.

Furthermore, incorporating sub-processes in your automation allows you to divide your tasks into smaller and more manageable units. This simplifies the comprehension and maintenance of your automated system.

---
### Create a sub-process in a process project

You will incorporate a sub-process within a primary process.

After completing the [prerequisites](https://developers.sap.com/tutorials/spa-add-links-forms.html), your process will look like this:
    
<!-- border -->![sub-process](1.png)

1. Navigate to the **Overview** tab, from the editable version of your project, click the **Create** dropdown and choose **Process**.

    <!-- border -->![sub-process](2.png)

2. In the **Create Process** dialog box, do the following:

    - Enter a **Process Name** such as Manage Trainees Learning Journey.
    - Choose **Create**.

    <!-- border -->![sub-process](3.png)

    Your new process opens in the process builder. You will now create a trigger form that will start the process. 

    <!-- border -->![sub-process](4.png)

3. Choose **+** in the **Trigger** settings, then select **Forms** and choose **Registration Form**.

4. Choose **Save**.

    <!-- border -->![sub-process](5.png)

5. Navigate back to the **Overview** tab. Select the **Learning Path** process.

    <!-- border -->![sub-process](sub1.png)

6. Choose the three dots of the Trigger form and select **Remove**.

7. Choose **Save**.

    <!-- border -->![sub-process](30.png)

8. Go back to **Manage Trainees Learning Journey** process, select **+** and choose **Subprocesses>Learning Path**.

9. **Save** the process.

    <!-- border -->![sub-process](sub2.png)

    Now you have an optimized process that incorporates a sub-process, making it more efficient and streamlined.

    <!-- border -->![sub-process](sub3.png)


### Release, deploy and run the process project

1. To release and deploy a process, please refer to step 1 and 2 of the tutorial on how to release and deploy a process [Run the Business Process](https://developers.sap.com/tutorials/spa-run-process.html).

2. In the **Overview** section, open the process **Manage Trainees Learning Journey** process of the deployed version, choose **Registration Form** and select the **Copy Link** icon under the **Form Link** field.

    <!-- border -->![sub-process](sub4.png)

3. Now paste the **Form Link** into a browser. When the form opens in the browser, you will have the course presentation fields that you defined in the Registration Form. Click on **Start**.    

    <!-- border -->![sub-process](sub5.png)

    Now, you will receive the training materials directly in your inbox, just like you did in the [Add Links to Forms](https://developers.sap.com/tutorials/spa-add-links-forms.html) tutorial.

    >In the next steps, you will cover the usage of a sub-process within an automation and also demonstrate how to distribute the learning path to multiple learners simultaneously.


### Add a table to the Registration Form

After completing the steps above, your process will look like this:
    
   <!-- border -->![sub-process](sub3.png)

1. From the editable version of your project, choose the three dots and select **Open Editor**.

     <!-- border -->![sub-process](6.png)

2. Add a **Table** with **Learners** as title.

     <!-- border -->![sub-process](7.png)

3. Choose the **+** icon in the table and select **Text**. Enter **First Name** as the field name.

    <!-- border -->![sub-process](8.png)

    <!-- border -->![sub-process](8_1.png)

4. Choose the **+** icon next to the First Name field and select **Text**. Enter **Last Name** as a field name.

    <!-- border -->![sub-process](9.png)
    <!-- border -->![sub-process](9_1.png)


5. Similarly choose the **+** icon next to the Last Name field and select **Text**. Enter **Emails** as a field name.

    <!-- border -->![sub-process](10.png)
    <!-- border -->![sub-process](10_1.png)

6. **Save** the form.


### Create the automation

1. Navigate back to the **Manage Trainees Learning Journey** process and do the following:

    - Select the three dots next to the **Learning Path** sub-process and choose **Remove**.
    
    <!-- border -->![sub-process](11_0.png)

    > ### What's going on?
    >
    > You will remove the sub-process from the main process. Our objective is to create an automation that utilizes the **Learning Path** sub-process to send the learning path to multiple users at once.

    - Now choose **+**.
    - Select **Automation**, **New Automation**.

    <!-- border -->![sub-process](11.png)

2. A pop up will appear to configure the Desktop Agent version. Do the following in the pop up:

    - From the dropdown, select the version of the Desktop Agent installed on your machine. It would be displayed with suffix as **Registered**.
    - Choose the **Confirm** button.

    <!-- border -->![sub-process](12.png)

3. A new pop-up will appear to create the automation. Do the following in the pop-up:

    -  Under Name enter: **Assign Learning Journey**.
    -  Choose the **Create** button.
    
    <!-- border -->![sub-process](13.png)

    An automation **Assign Learning Journey** will be created successfully.

4. Choose **Save**.
  
    <!-- border -->![sub-process](13_1.png)


### Create data types

1. Go to the **Overview** Tab. Choose the **Create** button. Create an artifact of the type **Data Type**.

    <!-- border -->![sub-process](14.png)

2. A new pop-up will appear.
    - Enter **Name** of the data type: **Learner**.
    - Choose **Create**.

    <!-- border -->![sub-process](15.png)

3.  In the Data Type **Learner** add 3 new fields as such:.

    |  Field Name           | Type
    |  :-------------       | :-------------
    |  `email`              | String
    |  `firstname`          | String
    |  `lastname`           | String

    <!-- border -->![sub-process](16.png)

    <!-- border -->![sub-process](17.png)

4. Choose **Save**.

    <!-- border -->![sub-process](17_1.png)

    Now you will create a second data type.

5. Similarly, go to the **Overview** tab. Choose the **Create** button. Create an artifact of the type **Data Type**.

    <!-- border -->![sub-process](18.png)

6. A new pop-up will appear.
    - Enter **Name** of the data type: **dataset**.
    - Choose **Create**.

    <!-- border -->![sub-process](19.png)

7.  In the Data Type **dataset** add a new field such as:

    |  Field Name           | Type
    |  :-------------       | :-------------
    |  `Learner`            | Learner

    <!-- border -->![sub-process](19_1.png)

8. Check List. 

9. Choose **Save**.

    <!-- border -->![sub-process](20.png)


### Configure the automation

1. Navigate back to the **Manage Trainees Learning Journey** process and select the three dots next to **Assign Learning Journey** automation, choose **Open Editor**.

    <!-- border -->![sub-process](21.png)

2. In the Automation Details section on the right, search for the **For Each** activity and drag and drop the activity into the automation flow.

    <!-- border -->![sub-process](22.png)

3. Click on the canvas and select the **Input/Output** section in Automation Details. 

    <!-- border -->![sub-process](23.png)

4. Add Input parameters as following:

    - In Parameter Name enter: `learner`.
    - In Data Type choose: **Learner**.
    - Check **List**.

    <!-- border -->![sub-process](24.png)

5. Click on the **For Each**, enter the value of Set looping List as `learner`.

    <!-- border -->![sub-process](25.png)

6. Click on the canvas and select the **Processes** section in Automation Details. 

    <!-- border -->![sub-process](26.png)

7. Select **Learning Path** and drag and drop the activity into the automation flow inside the **For Each** loop.

    <!-- border -->![sub-process](27.png)

8. **Save** your work.


### Configure the sub-process

1. Go to the **Overview** tab. Select the **Learning Path** process.

    <!-- border -->![sub-process](29.png)

2. Select the **Input/Output** section in Process Details.

    <!-- border -->![sub-process](31.png)

3. Select **Configure** and click on **add input**.

    <!-- border -->![sub-process](31_1.png)

    <!-- border -->![sub-process](31_2.png)

4. Configure the **Process Input** as such: 

    - In Inputs Name enter: `learners`.
    - In Inputs Type choose: **Learner**. 

5. Select **Apply**.

    <!-- border -->![sub-process](32.png)

6. Now, click on **Build Your First Business Process** form and configure the **General** section.

    <!-- border -->![sub-process](35.png)

7. In the **Recipients** section, under **Users** select **email**.

    <!-- border -->![sub-process](36.png)

8. Select the **Boost your Business Process with Automation** form to configure the **General** section. In the **Recipients** section, under **Users** select **email**.

    <!-- border -->![sub-process](37.png)

9. Similarly, select the **Create Tables in the Form** form to configure the **General** section. In the **Recipients** section, under **Users** select **email**.

    <!-- border -->![sub-process](38.png)

10. **Save** your work.

11. Go to the **Overview** tab. Click on the **Assign Learning Journey** automation.

    <!-- border -->![sub-process](38_1.png)

12. Select **Learning Path** and enter the value of learners as `currentMember`.

    <!-- border -->![sub-process](38_2.png)

13. **Save** your work.

14. Navigate back to **Manage Trainees Learning Journey**, select **Assign Learning Journey** automation to configure the **Inputs** parameters.

    <!-- border -->![sub-process](38_3.png)

15. In the **Inputs** section, in **Select list** field, choose **Learners**.

    <!-- border -->![sub-process](38_4.png)

16. **Save** your work.


### Release and deploy the project

After completing [Agent Management Settings to Execute the Process with an Automation](spa-run-agent-settings) tutorial, you may release and deploy the process.

1. In the **Manage Trainees Learning Journey** process, choose the **Release** button on the top right corner.

    <!-- border -->![sub-process](39.png)

2. In the **Release Project** popup, select **Release**.

    <!-- border -->![sub-process](40.png)

3. On the **Overview** section that appears, choose **Deploy**.

    <!-- border -->![sub-process](41.png)

4. In the popup that appears, run the deployment.

    <!-- border -->![sub-process](42.png)
    <!-- border -->![sub-process](43.png)
    <!-- border -->![sub-process](44.png)

5. After project deployment, a confirmation popup will appear. Choose **Close**.

    <!-- border -->![sub-process](45.png)


### Run the process

1. In the **Overview** section, open the process **Manage Trainees Learning Journey** of the deployed version, choose **Registration Form** and select the **Copy Link** icon under **Form Link** field.

    <!-- border -->![sub-process](46.png)

2. In a new tab in your browser, paste the form link. Enter the information of the learners in the table for whom you intend to send the learning path and choose **Submit**.

    <!-- border -->![sub-process](47.png)
   
    > After clicking on **Submit**, all the learners you have added to the table will receive the project tasks in their Inbox.

3. Navigate to **SAP Build** lobby, choose **My Inbox** icon.

    <!-- border -->![sub-process](48.png)

4. You will see the first task **First Learning Mission** appear in the My Inbox application that ships with SAP Build. The task will have the description of the training to be followed and the link to the tutorial. After finishing the mission, select **I have completed the first mission** and click on **Next**.

    <!-- border -->![sub-process](49.png)

5. Refresh the inbox again to get the second notification for the second mission. Now you can see task **Second Learning Mission** appear in My Inbox. After finishing the mission, click on **Next**.

    <!-- border -->![sub-process](50.png)

6. Similarly, refresh the inbox again to get the third mission. Once the mission is completed, click on **Done**.

    <!-- border -->![sub-process](51.png)



