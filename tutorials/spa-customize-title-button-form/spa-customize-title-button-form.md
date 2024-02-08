---
parser: v2
author_name: Djamai Hania
author_profile: https://github.com/Haniadjamai
auto_validation: true
time: 10
tags: [ tutorial>beginner, software-product>sap-business-technology-platform, tutorial>free-tier ]
primary_tag: software-product>sap-build-process-automation
---

# Customize the Titles of Buttons in Forms 
<!-- description --> Customize and change the labels of buttons within forms in your business process.

## Prerequisites
  - Either complete the mission [Build Your First Business Process with SAP Build Process Automation](https://developers.sap.com/mission.sap-process-automation.html) or
  - Acquire the needed package/project from the Store using this tutorial [Acquire a Template Project from the Store](https://developers.sap.com/tutorials/spa-acquire-businessprocess-store.html).

## You will learn
  - How to customize the title of your form button.

---

## Intro
In this tutorial, you will learn how to customize the titles of buttons in your forms. You can choose from an existing list of options or create a custom title according to your preferences.

---

### Change the button title

After completing the prerequisites, your process will look like this:

<!-- border -->![Button](1.png)

1. In the Order Processing process, select the **Order Processing Form**.

2. Click on the three dots and select **Open Editor**.

    <!-- border -->![Button](2.png)

3. In the form builder scroll down the page. You can see the button is initially configured to **Submit**.

4. Choose **Settings Button Title**.

    <!-- border -->![Button](3.png)

4. In the **Setting Button Title**, you can choose a different title for your Button. Select the title **Send**.

    <!-- border -->![Button](4.png)

    Now your button is configured to **Send**.

    <!-- border -->![Button](5.png)

5. Save the form.

### Customize the titles of the buttons

1. Navigate back to the Order Processing process, select the **Approval Form**. 

2. Choose **Open Editor** to edit your Approval Form.

    <!-- border -->![Button](7.png)

2. In the form builder, scroll down the page and choose **Settings Button Title**.

    <!-- border -->![Button](8.png)

3. In the **Settings Button Title**, you can choose a different title for your buttons.

    <!-- border -->![Button](9.png)

4. To customise your button, select the list of buttons and choose **Custom**.

    <!-- border -->![Button](10.png)

5. In the **Custom Button Title** section, enter your custom title, for example **Validate**.

    <!-- border -->![Button](11.png)

6. Similarly, for your second button, select the list of buttons and choose **Custom**.

    <!-- border -->![Button](12.png)

7. In the **Custom Button Title** section, enter your custom title, for example **Refuse**.

    <!-- border -->![Button](13.png)

8. Save the form.

    > You may configure all form buttons as per your requirements.

    <!-- border -->![Button](14.png)

### Release and deploy
    
   - Refer to the tutorial on how to release and deploy the Process [Run the Business Process](https://developers.sap.com/tutorials/spa-run-process.html).

### Test the process 

1. Open the process builder of the deployed version and choose **Order Processing Form**, select the **Copy Link** icon under **Form Link** field.

    <!-- border -->![Button](21.png)

2. When you open the form in the browser, you will have all the input fields as you have defined in the process trigger form and the new **Send** button. 
   Enter the details required in the form and choose **Send**.

    <!-- border -->![Button](22.png)

3. In the **SAP Build** Lobby, choose **My Inbox** icon.

    <!-- border -->![Button](23.png)

4. You can see tasks appear in the My Inbox application that ships with SAP Build. With the new buttons you can  either **Validate** or **Refuse** the approval task.

    <!-- border -->![Button](24.png)

5. Once you **Validate/Refuse** the approval task, you may refresh the inbox again to get the final notification.

    <!-- border -->![Button](25.png)


