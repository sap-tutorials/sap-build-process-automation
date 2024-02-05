---
parser: v2
auto_validation: true
time: 15
tags: [ tutorial>beginner, software-product>sap-business-technology-platform, tutorial>free-tier]
primary_tag: software-product>sap-build-process-automation

---

# Agent Management Settings to Execute the Process with an Automation
<!-- description --> Create an agent attribute in the tenant to add it to your agent and project

## Prerequisites
 - Access to a [SAP BTP tenant with SAP Build Process Automation](spa-subscribe-booster)
 - Install and set up the [Desktop Agent 3](spa-setup-desktop-3-0-agent) to run the automation

## You will learn
  - How to create an Agent Attribute in the tenant.
  - How to add the attribute to your agent.
  - How to add the attribute to your project.

## Intro
Agent attributes allow you to sort agents registered within the same tenant and make sure that a specific agent executes the job of your choice.

---


### Create an environment to add your agent

After you have installed the desktop agent, you need to add your agent so that it is able to run an automation.

1. Navigate to **SAP Build** lobby. Select **Control Tower** and **Environments** under **Tenant Configuration**.
    
    <!-- border -->![Environment](agent3-020b.png)
   
2. Choose **Create Environment**.
   
3. In the **Create Environment** window do the following:

    - Give your environment a name
    - Select a color
    - You may enter a short description
    - Choose **Create**

    <!-- border -->![Create Environment](agent3-020.png)

4. Select the created environment to add your agent in it.

    <!-- border -->![Select environment](agent3-020a.png)

5. Select **Agent Management > Add Agent**.

6. In the **Add Agent** window, select your agent and choose **Add agent**.

    <!-- border -->![Agent Management Add](agent3-021.png)

7.  Your agent is now added and ready to run.

    <!-- border -->![Agent Management List](agent3-022.png)


### Create an agent attribute in the tenant


Now that you have your project free of errors, ready to be released, you need to add an **Attribute** to your project. But first, you need to create an Agent Attribute.

To do so, please follow these steps:

1. In **SAP Build** lobby, select **Control Tower > Agent Attributes**.

    <!-- border -->![Agent Attribute](02.png)  

2. Choose **Create Attribute**.

3. In the **Create Agent Attribute** dialog box, please enter **My Agent Attribute** in the **Name** field.

4. From the **Type** dropdown list, select **Predefined** if you wish to add values or else leave **Free** as **Type**.

    > - **Free** – With this type of attribute, you won't be able to add any predefined value. Whenever you want to use this attribute, you will be able to parametrize the value of this attribute.
    > - **Predefined** – With this type of attribute, you will be able to populate values for any specific attribute.

5. In the **Values** field, you may enter any value you wish (i.e. employee ID).

6. Choose **Create**.

    <!-- border -->![Create Agent Attribute](01-Settings-create-agent-attribute.png)  


### Add the attribute to your agent


1. Navigate back to **Control Tower** and choose **Agents** under **Agent Configuration**.

    <!-- border -->![Agents](03.png)
   
2. Search for your agent.

    <!-- border -->![Settings Agents List](01-Settings.png)

3. Verify that it is idle or ready and connected in unattended mode.

    > If your agent is not in unattended mode, you will be able to set it to unattended mode at step 5.
   
4. Select the three dots and choose **Manage Attributes**.

    <!-- border -->![Manage attributes](04.png)

5. In the **Manage Matching Attributes** dialog box, add your attribute:

    - From the drop-down list, select **My Agent Attribute**
    - Enter the value you selected previously in the **Values** field and press **ENTER**
    - Choose **Confirm**

    <!-- border -->![Settings Add Attribute](01-Settings-agent-attributes-add.png)


### Add the attribute to your project


1. Navigate back to your project in the Process Builder.

2. Choose **Settings**.

3. Select **Attributes**.

4. From the dropdown list, select **My Agent Attribute**.

5. Enter your value in the **Values** field and press **ENTER**.

6. Choose **Save**.

7. Choose **Close**.   

      <!-- border -->![Release](00-adding-attribute-value.png)



### Desktop agent in unattended mode


When you are running the process make sure to have the Desktop Agent in unattended mode.

1. Open the Desktop Agent 3 from the `systray`.

    <!-- border -->![Release](04-open-agent.png)

2. Select **Settings** in the Menu and choose **Mode**.

    <!-- border -->![Release](04-open-settings-mode.png)
    
3. Set the Desktop Agent 3 to Unattended mode by selecting **Activate**.

    <!-- border -->![Release](04-unattended-mode.png)

  






---
