---
parser: v2
author_name: Samir Hamichi
author_profile: https://github.com/shamichi-repo
auto_validation: true
time: 10
tags: [ tutorial>beginner, software-product>sap-business-technology-platform, tutorial>free-tier ]
primary_tag: software-product>sap-build-process-automation
---

# Create a Process Condition in a Vertical Layout Process Editor
<!-- description --> Create a process condition to route the process based on business criteria

## Prerequisites
- Complete [Create and Configure Forms](spa-vl-create-forms) tutorial


## You will learn
  - How to create and configure a process condition
  - How to define different process flows for each conditional criteria

---

## Intro
In this unit, you will learn how to use process condition in a business process to get rid of unnecessary approvals when the process is routed for auto-approval or one-step-approval flow based on the sales order criteria.

A process condition routes the business process based on certain criteria. These conditions apply an **If or Else** rule to the process content and respond according to the rules defined as settings in the process builder.


### Create process condition

Once the process with forms is designed, define which process flow should run based on if/else condition criteria. 

1. To add a condition to a process open the **Process Builder**. Choose **+** below the Trigger. 

    <!-- border -->![Process Condition](001a.png)

2. Choose **Controls and Events**.

    <!-- border -->![Process Condition](001b.png)
   
3. Choose **Condition**.

    <!-- border -->![Process Condition](001c.png)

4. To configure the condition, choose **Open Condition Editor**.

    <!-- border -->![Process Condition](002.png)

    > Process content will contain a list of attributes that have been defined in previous skills. For example: in the screenshot below, you can see attributes from the trigger form. You will use this process content to configure different skills during business process modelling.

5. Edit your branch condition:
   
    - Set **Order Amount** from the process content
    - Select **is less than**
    - Enter **100000** as the value

    <!-- border -->![Process Condition](003.png)

    You have configured your **if** branch to: **if Order Amount is less than 100000**.

6. Similarly, add one more condition. Select  **Add Group**.

7. In the group section select **Any** to make it **OR** conditional group. Select conditions:

    | **Item** | **Condition** | **Value**
    |  :------------- | :------------- | :-------------
    | Shipping Country | is equal to | India
    | Shipping Country | is equal to| Germany

8. Choose **Apply** to add the condition to the business process.

    > You can expand the **Summary** section to see how the process conditions are designed

    <!-- border -->![Process Condition](004.png)

9. Both **If** and **Default** link branches are connected to the **Approval Form**.

    <!-- border -->![Process Condition](006.png)

    With this process condition, only the sales order above a specific amount will be sent for approval and the rest will be auto-approved. 
    
    You have to add a notification form in the **If** connection to notify the requester of the auto-approval and terminate the process.

10. To create the new form, choose **+** below the **If**.

    <!-- border -->![Process Condition](008a.png)

11.  Choose **Form**.

    <!-- border -->![Process Condition](008b.png)

12. Choose **Blank form**.

    <!-- border -->![Process Condition](008c.png)

13. In the **Create Form** window:

    - Enter the Name: **Auto Approval Notification**
    - Enter a Description: **Notification form to inform auto approval of the sales order**
    - Choose **Create**

    <!-- border -->![Process Condition](009.png)

14. Select **Open Editor** of the form.

    <!-- border -->![Process Condition](009c.png)

15. Design the notification form, the same way as in the previous chapter, to send another notification to the requester about auto-approval. Add **Layout fields**:

    | **Form Fields** | **Field Settings with Label**
    |  :------------- | :-------------
    | Headline 1 | Automatic Order Confirmation
    | Paragraph  | Your order has been received and we will send you the details as soon as the order is shipped. You can find the details of your order below, please review and verify your request:
    | Paragraph  | Your Sales Order Details:

    <!-- border -->![Process Condition](009a.png)

16. For all below **Input Fields**, enter the labels and select the **Read Only** checkbox.

    | **Form Fields**| **Field Settings with Label**
    |  :------------- | :-------------
    | Text | Order Number
    | Number | Order Amount
    | Date | Expected Delivery Date

17. Add **Layout field**:

    | **Form Fields** | **Field Settings with Label**
    |  :------------- | :-------------
    | Paragraph | Please press the SUBMIT button to acknowledge the order status.

18. **Save** your work.

   <!-- border -->![Process Condition](009b.png)


### Configure auto-approval form

1. Go back to the process builder and configure the **Auto Approval Notification**.

2. Select the **Auto Approval Notification** to configure the **General** section.

3. In the **Subject** field, do the following:
   
    - Enter: **Your order**
    - Choose: **Order Number** from Order Processing Form
    - Enter: **has been successfully received**

4. In the **Users** section, under **Recipients** select **Process Started By** from Process Metadata.

    <!-- border -->![Process Condition](011.png)

5. Select **Inputs** section and configure the following inputs:

    | Form Input Fields| Process Content Entry
    |  :------------- | :-------------
    | Order Number | Order Number
    | Order Amount | Order Amount
    | Expected Delivery Date | Expected Delivery Date

6. Choose **Save**.

    <!-- border -->![Process Condition](012.png)

7. Below **Auto Approval Notification**, select **+**.
    
    <!-- border -->![Process Condition](013a.png)

8. Choose **Flow Logic**.

    <!-- border -->![Process Condition](013b.png)

9. Choose **End**.

    <!-- border -->![Process Condition](013c.png)

10.  **Save** your work.

    <!-- border -->![Process Condition](014.png)

    This completes the process design with condition criteria that will decide what process flow is executed and whether there will be an auto-approval or a one-step approval route.

---
