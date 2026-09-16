---
parser: v2
author_name: Céline Audin
author_profile: https://github.com/celineaudinsap
auto_validation: true
time: 15
tags: [ tutorial>intermediate, software-product>sap-business-technology-platform, tutorial>free-tier]
primary_tag: software-product>sap-build-process-automation
---

# Run a Business Process From the Business Site
<!-- description --> Configure a form trigger in the Business Site to run a Business Process

## Prerequisites
 - Complete [Configure SAP Build Work Zone, standard edition](spa-configure-workzone) tutorial

## You will learn
  - How to configure your form trigger as a tile in the Business Site.

---

### Configure the Process Trigger


You completed [Configure SAP Build Work Zone, standard edition](spa-configure-workzone) tutorial. You assigned **My Inbox**, **Process Workspace**, **Visibility Scenario Dashboard** and **Visibility Scenario Instances** to **Everyone** role and clicked **Save**.

![Assignments to Everyone Role](01.png)

1. Go back to **Content Manager** page.

    ![Back My Content](02.png)

2. Select **Process Trigger**.

    ![Process Trigger](07.png)

3. Choose **Create a Local Copy**.

    ![Create Local Copy](08.png)

4. Choose **Edit** to make changes to the **Process Trigger** app.

    ![Edit](09.png)

5. Change the name of the app to **Sales Order Management**.

    ![Change Name](10.png)

6. Select the tab **Navigation**.

    ![Navigation](11.png)

7. Now you need to fill the **Default Value** of the app's parameters with the **Launchpad Configuration Parameter** of your process' **Trigger Settings**.

    ![Default Value Field](11a.png)

8. Navigate back to your deployed project in **SAP Build Process Automation**.

9. Select the **Order Processing Form**.

10. Copy the **Launchpad Configuration Parameter**.

    ![Copy Parameter](12.png)

    >This is the parameter you need to configure this form trigger as a tile in the Business Site.

11. Now navigate back to the Work Zone.

12. Paste the value in the **Default Value** field of the Sales Order Management app's parameters.

    ![Default Value](13.png)

13. Select the tab **Translation**.

14. Change the name of the **Title** to **Sales Order Management**.

    ![Change Name](13b.png)

15. Choose **Save**.



### Assign Sales Order Management Trigger to SAP Build Process Automation Group


1. Navigate back to **Content Manager**.

    ![My Content](13a.png)

2. Select **SAP Build Process Automation** group.

    ![SAP Process Automation](03.png)

3. Choose **Edit** to make changes to the group.

    ![Edit Group](04.png)

    You will now assign the **Sales Order Management** trigger to your group.

4. Click on the **On/Off Button** to add the **Sales Order Management** item.

5. Choose **Save**.

    ![Save](05.png)


### Assign Sales Order Management Trigger to Everyone Role


1. Go back to **Content Manager**.

    ![My Contact](06.png)

2. Choose **Everyone**.

    ![Everyone](16.png)

3. Choose **Edit**.

4. You will now assign the **Sales Order Management** trigger to Everyone role.

5. Click on the **On/Off Button** to add the **Sales Order Management** item.

6. Choose **Save**.

    ![Everyone](17.png)


### Launch the Business Site


1. Navigate back to the **Site Directory**.

    ![Site Directory](18.png)

2. Go to the site.

    ![Go to site](19.png)

    You will be directed to the **Business Site** where the Sales Order Management tile has been created.

    You can now trigger the process from the **Business Site**.

3. Choose **Sales Order Management** tile.

    ![Tile](20.png)

    > You can also see **My Inbox** and **Process Workspace** tiles added to the **Business Site** which can be used by the business users to access the tasks and monitor the processes respectively.

    You will be redirected to the **Order Approval Request Form**.

    ![Form](21.png)



---
