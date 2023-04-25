---
parser: v2
author_name: Djamai Hania
author_profile: https://github.com/Haniadjamai
auto_validation: true
time: 25
tags: [ tutorial>beginner, software-product>sap-business-technology-platform, tutorial>free-tier ]
primary_tag: software-product>sap-build-process-automation
---

# Add Links to Forms
<!-- description --> Learn how to links in the Forms of SAP Build Process Automation.

## Prerequisites
- Complete [Subscribe to SAP Build Process Automation using Booster in SAP BTP Free Tier](https://developers.sap.com/tutorials/spa-subscribe-booster.html)

## You will learn
  - How to add interactive forms to the process.
  - How to design a form with a layout and add links using a drag-and-drop approach.

---

## Intro
Interactive forms with links can be used as a training and learning tool. These kind of forms offer several benefits, including easy access to relevant training information and the ability to organize links to guide users through various job-related topics, thereby speeding up the training process.

---

### Create a business process project

After completing the prerequisites, you will create a project.

1. In **SAP Build** lobby, choose **Create**.

    <!-- border -->![create](create.png)

2. Pick **Build an Automated Process**.

    <!-- border -->![Create](create2.png)

3. Select **Business Process**.

    <!-- border -->![Create](create3.png)

4. In the **Create a Business Process** dialog box, do the following:
    - Enter a **Project Name** such as Tutorials Learning Path.
    - Choose **Create**.

    <!-- border -->![create](create4.png)

5. In the **Create Process** dialog box, provide the following:
    - Enter a **Name** such as Learning Path.
    - Choose **Create**.

    <!-- border -->![create](create5.png)

### Create a form to trigger the business process

    You will create a trigger form that will start the process. Open your process in the process builder:

   <!-- border -->![Form](1.png)

1. Choose **+** in the **Trigger** settings, then select **Forms** and **New Form**.

    <!-- border -->![Form](2.png)

2. In the **Create Form** pop-up window, enter:
    - **Name**: Training Form.
    - A description to describe the task of the form.
    - Choose **Create**.

     <!-- border -->![Form](3.png)

3. Choose the three dots and select **Open Editor**.

     <!-- border -->![Form](4.png)

4. Now, you will edit the form by using the available layout and input field options. Start by dragging and dropping the form layout fields, then enter the given names and field settings as shown in the example below:

    |  **Form Fields**    | **Field Settings with Label**
    |  :------------- | :-------------
    |  Headline 1         | Training Form
    |  Paragraph          | *Enter the description of your project here*. 
    
    For the purpose of this tutorial, you may use the following description:

    Welcome to our training document. This document has been designed to assist you in completing specific training courses that are necessary for your job. 
    
    This document contains links to online training tutorials that will guide you through the different steps of the automation process using SAP Build Process Automation. 
    
    We hope that this training document will be useful for you in understanding the benefits of SAP Build Process Automation and how to use it to improve the efficiency of our company.

    <!-- border -->![Form](5.png)

5. Save the form using the **Save** button on the top-right corner of the screen.

    <!-- border -->![Form](5_1.png)

    > To configure the form buttons, you can follow the tutorial [Customize the Titles of Buttons in Forms](https://developers.sap.com/tutorials/spa-customize-title-button-form.html). For example, here the button of the trigger form has been set to **Start**.

    <!-- border -->![Form](button.png)
### Create the first mission form

1. Go to your **Learning Path** process. Select **+** next to the Trigger and add a **New Form** to the process.

    <!-- border -->![Form](5_2.png)

2. In the pop-up window for **Create form**: 
    - Enter the name of your mission: **Build Your First Business Process**.
    - Enter a description to describe the task of the form.
    - Choose **Create**.

    <!-- border -->![Form](6.png)

3. A new form is added to the process. Choose the three dots of the new form and select **Open Editor**. 

    <!-- border -->![Form](7.png)

4. Design the **Build Your First Business Process** form in the form builder by dragging-and-dropping fields into the form editor and configuring respective field settings, as shown in the example below:

    |  **Form Fields**    | **Field Settings with Label**
    |  :------------- | :-------------
    | Headline 1 | First mission 
    | Headline 2 | Time :  1 hr. 15 min
    | Paragraph  | *Enter the description of your mission here*. 
    
    For the purpose of this tutorial, you may use: 

    In this training, you will learn how to use SAP Build Process Automation's intuitive low-code and no-code capabilities to create, develop, deploy, and run your first business process. You will discover how this tool can help you build the apps you need at the speed demanded by your business, using visual drag-and-drop tools for application development. 
    
    You will also learn: 
    
     - How to enable SAP Build Process Automation in SAP BTP Free Tier account.                                                                               
     - How to create interactive forms that can be used as triggers for processes or as approval steps within a business process.

    <!-- border -->![Form](8.png)

5. Now, you will add a **Link** field and configure the field settings. For example, in this tutorial, you will link the form to the **Build Your First Business Process** tutorial.

    |  :------------- | :------------- 
    | Link | <https://developers.sap.com/mission.sap-process-automation.html>
    | Link Text | Build Your First Business Process with SAP Build Process Automation

    <!-- border -->![Form](9.png)

    > You can choose any link and put it here, depending on your project.

6. **Save** the form.

    > To configure the form buttons, you can follow the tutorial [Customize the Titles of Buttons in Forms](https://developers.sap.com/tutorials/spa-customize-title-button-form.html). Here, the button has been set to **Next**.

    <!-- border -->![Form](button2.png)

### Configure the first mission form

1. Go back to the process builder to map the process content with the form input fields. Select the **Build Your First Business Process** form.

2. Configure the **General** information section:
    - In the **Subject** section, enter **First Learning Mission**.
    - In the **Recipients** section, under **Users**, select **Process Started By** from Process Metadata.

    <!-- border -->![Form](10.png)

    > The subject configuration will be displayed when the form appears as a task in the recipient's `MyInbox`.
    
3. In the **Due Date** section:
    - Select **Static Duration** as **type of due date**.
    - Enter **3 Days** as the duration.

    <!-- border -->![Form](13_2.png)

4. **Save** the process.


### Create and configure the second mission form

1. To add the second mission form to the process, select **+** next to the **Build Your First Business Process** form. Choose **Forms** and then **New Form**.

    <!-- border -->![Form](11.png)

2. In the **Create Form** dialog box, do the following.  
    - Enter the name of your mission: **Boost your Business Process with Automation**.
    - Enter a description to describe the task of the form.
    - Choose **Create**.
 
    <!-- border -->![Form](12.png)

3. Choose the three dots of the new form and select **Open Editor**. 

    <!-- border -->![Form](13.png)

4. Design the **Boost your Business Process with Automation** form in the form builder.

    |  **Form Fields**    | **Field Settings with Label**
    |  :------------- | :-------------
    | Headline 1 | Second mission 
    | Headline 2 | Time :  2 hr. 5 min
    | Paragraph  | *Enter the description of your second mission here*. 
    
    For the purpose of this tutorial, you may use: 

    In this training, you will learn how to automate repetitive processes by integrating decision logic with business rules and configuring SAP Process Visibility. You will go through several stages of learning, which include:  

     - Creating an automation to extract and read sales order details from an Excel file "25min"                                                                                 
     - Creating a decision to determine authorized approvers. "20 min"                     
     - Creating a visibility scenario for your business process. "15 min"                  
     - Configuring SAP Build Workzone, standard edition for the visibility scenario. "30 min"                                                                                      
     - Configuring a form trigger in the SAP Launchpad to run a business process. "35min"

    <!-- border -->![Form](14.png)

5. Now, you will add a **Link** field and configure the field settings.

    |  :------------- | :-------------
    | Link | <https://developers.sap.com/mission.sap-process-automation-boost.html>
    | Link Text | Boost your Business Process with Automation, Decision and Process Visibility 

    <!-- border -->![Form](15.png)

6. **Save** the form.

    > To configure the form buttons, you can follow the tutorial [Customize the Titles of Buttons in Forms](https://developers.sap.com/tutorials/spa-customize-title-button-form.html). Similarly, here for the second mission, the button has been set to **Next**.

    <!-- border -->![Form](button3.png)

7. Go back to the process builder to map the process content with the form input fields. Select the **Boost your Business Process with Automation** form.

8. Configure the **General** information section. 
    - In the **Subject** section, enter **Second Learning Mission**.
    - In the **Recipients** section, under **Users**, select **Process Started By** from Process Metadata.

9. In the **Due Date** section:
    - Select **Static Duration** as **type of due date**.
    - Enter **3 Days** as the duration.

    <!-- border -->![Form](16.png)

10. **Save** the process.


### Create and configure the third mission form

1. Similarly, select **+** next to the **Boost your Business Process with Automation** form. Choose **Forms** and **New Form**.

    <!-- border -->![Form](17.png)

2. In the **Create Form** dialog box, do the following: 
    - Enter the name of your mission: **Create Tables in The Form**.
    - Enter a description to describe the task of the form.
    - Choose **Create**.

    <!-- border -->![Form](18.png)

3. Choose the three dots of the new form and select **Open Editor**. 

    <!-- border -->![Form](19.png)

4. Design the **Create Tables in The Form** form in the form builder.

    |  **Form Fields**    | **Field Settings with Label**
    |  :------------- | :-------------
    | Headline 1 | Third mission 
    | Headline 2 | Time :  2 hr. 5 min
    | Paragraph  | *Enter the description of your third mission here*. 
       
    For the purpose of this tutorial, you may use:

    In this training, you will learn how to create a table in a form, validate the order details extracted from the automation, and display any error details in the table.

    Similarly add a **Link** field: 

    |  :------------- | :-------------
    | Link | <https://developers.sap.com/tutorials/spa-forms-table.html>
    | Link Text | Create Tables in the Form

    <!-- border -->![Form](20.png)

5. **Save** the form.

    > To configure the form buttons, you can follow the tutorial [Customize the Titles of Buttons in Forms](https://developers.sap.com/tutorials/spa-customize-title-button-form.html). Here for the last mission, the button has been set to **Done**.

    <!-- border -->![Form](button4.png)

6. Go back to the process builder to map the process content with the form input fields. Select the **Create tables in the Form** form.

7. Configure the **General** information section:
    - In the **Subject** section, enter **Third Learning Mission**.
    - In the **Recipients** section, under **Users**, select **Process Started By** from Process Metadata.

8. In the **Due Date** section:
    - Select **Static Duration** as **type of due date**.
    - Enter **3 Days** as the duration.

    <!-- border -->![Form](21.png)

9. **Save** the process.


### Release and deploy
    
   - Please refer to step 1 and 2 of the tutorial on how to release and deploy a process [Run the Business Process](https://developers.sap.com/tutorials/spa-run-process.html). 


### Test the process 

1. Open the process builder of the deployed version and choose **Training Form**, select the **Copy Link** icon under **Form Link**.

    <!-- border -->![Form](22.png)

2. When you open the form in the browser, you will have the course presentation fields that you defined in the process trigger form. Click on **Start**.    

    <!-- border -->![Form](23.png)

3. In the **SAP Build** lobby, choose **My Inbox** icon.

    <!-- border -->![Form](24.png)

4. You will see the first task **First Learning Mission** appear in the My Inbox application that ships with SAP Build. The task will have the description of the training to be followed and the link to the tutorial. After finishing the mission, click on **Next**.

    <!-- border -->![Form](25.png)

5. Refresh the inbox again to get the second notification for the second mission. Now you can see task **Second Learning Mission** appear in My Inbox. After finishing the mission, click on **Next**.

    <!-- border -->![Form](26.png)

6. Similarly, refresh the inbox again to get the third mission. Once the mission is completed, click on **Done**.

    <!-- border -->![Form](27.png)