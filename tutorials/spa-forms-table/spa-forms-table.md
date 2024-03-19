---
parser: v2
author_name: Aviral Agarwal
author_profile: https://github.com/aviral-agarwal-sap
auto_validation: true
time: 25
tags: [ tutorial>beginner , software-product>sap-business-technology-platform, tutorial>free-tier]
primary_tag: software-product>sap-build-process-automation
---

# Create Tables in the Form
<!-- description --> Validate the order details extracted from the automation and display the error details in a table in a form.

## Prerequisites
 - Complete the mission [Boost your Business Process with Automation, Decision and Process Visibility](mission.sap-process-automation-boost).
 - Download the [Orders.xlsx](https://github.com/sap-tutorials/sap-build-process-automation/blob/main/tutorials/spa-forms-table/Orders.xlsx) on your local machine.
 - Setup the desktop agent to run automation as explained in [this tutorial](spa-run-agent-settings)

## You will learn
  - How to create a Table in the Form.
  - How to use List in Decision.
  - How to bind List in Decision to Table in Form.
  - How to retrieve the sample project from the Store.

## Intro
In this tutorial, you will be creating a Decision to validate the Purchase Order Details extracted from excel. If the Purchase Order Details has errors, the errors will be displayed in a table in a form.

---

### Create decision artifact

Once you have completed the prerequisite mission, your process should look something like below. 

<!-- border -->![Automation](001c.png)

1. In the  **Order Processing** process:
    - Choose **+** after the **Get Order Details**.

    <!-- border -->![Automation](001a.png)

    - Select **Decision**.

    <!-- border -->![Automation](001.png)

    - Select **Blank Decision**.

    <!-- border -->![Automation](001b.png)

2. A pop up will appear to configure the decision. Enter **Order Validity Check** as decision name and choose **Create**.

    <!-- border -->![Automation](002.png)

   
### Create data types

1. Go to the **Overview** Tab. Choose the **Create** button. Create an artifact of the type **Data Type**.

    <!-- border -->![Automation](003.png)

2. A new pop-up will appear.
    - Enter **Name** of the data type: **Error Output**.
    - Enter **Description** of your choice.
    - Choose **Create**.

    <!-- border -->![Automation](004.png)

3.  In the Data Type **Error Output** add new fields as following.

    |  Field Name           | Type
    |  :-------------       | :-------------
    |  `ErrorCode`          | String
    |  `ErrorDescription`   | String

    <!-- border -->![Automation](005.png)

    <!-- border -->![Automation](006.png)

4. Choose **Save**.


### Configure decision

1. Navigate to the **Order Processing** process. 
   
2. Select the decision **Order Validity Check** menu option and choose **Open Editor**.

    <!-- border -->![Automation](007.png)

3. Add Input and Output parameters.

    <!-- border -->![Automation](008.png)

4. Edit Input and Output parameters as follows.

    |  Parameter Name       | Data Type        | Parameter Type | Description
    |  :---------------     | :-------------   | :------------- | :---------------
    |  `Input Sales Order`      | Sales Order     | Input          | Input Sales Order
    |  `Validity Check Output`    | Error Output| Output         | Validity Check Output

    > **CAUTION:** Select the **List** checkbox to make the output type as list of Error Output.

    <!-- border -->![Automation](009.png)

5. Select the **Rules** tab. Choose **Add Rule**.

    <!-- border -->![Automation](011.png)

6. Enter **Rule Name** as Error Check and **Rule Description** of your choice.
   
7. For **Hit Policy**, select **All Match**.

    > **What is going on?:** With a **First Match** hit policy, the rule engine fetches the first occurrence that matches the condition and returns it as the result. On the other hand, with a **All Match** hit policy, the rule engine fetches all the occurrences that matches the condition and returns them as the result.
    
8. Choose **Next Step**.

    <!-- border -->![Automation](012.png)

9.  In the **Configure Conditions** section, expand the **Input Sales Order** parameter.

    <!-- border -->![Automation](013.png)

10. For this scenario you will be choosing `expectedDeliveryDate`, `orderAmount`, `shippingCountry` and `orderStatus`. Choose **Next Step**.

    <!-- border -->![Automation](014.png)

11. In the **Configure Results** section, enter Validity Check Output (List) in **Result Vocabulary**. Choose **Validity Check Output** parameter. Choose **Next Step**.

    <!-- border -->![Automation](016.png)

12. In the **Review** section, a summary of the rule to be added is displayed. Choose **Create**.

    <!-- border -->![Automation](017.png)

13. **Enter Full Screen Mode** by clicking on the icon on the top right corner.

    <!-- border -->![Automation](017a.png)
   
14. In the **Decision Table**, add the below mentioned conditions.

    |  Parameter Name       | Condition        | Error Code | Error Description
    |  :---------------     | :-------------   | :------------- | :---------------
    |  `expectedDeliveryDate`      | <TODAY()     | 'ERR01'          | 'Delivery date is before current date'
    |  `orderAmount`    | >100000| 'ERR02'              | 'Fraudulent Request'
    |  `shippingCountry`      | NOTEXISTSIN ['India','United Kingdom']     | 'ERR03'               | 'Delivery not supported in this country'
    |  `orderStatus`    | =''| 'ERR04'              | 'Order status is not set'

15. Click on the first column.

    <!-- border -->![Automation](018a.png)

16. Type `<TODAY`, and choose **TODAY** from Array Operators. When finished, click outside the input field to confirm.

    <!-- border -->![Automation](018.png)

17. Proceed in the same way for Error Code and Error Description (or **Then** section):

    <!-- border -->![Automation](018b.png)

    > Remember that for all String type data object attributes, you must add a single quote (') before and after the text.

18. To add a new row to the decision table:
    - Choose the check-box of the first row
    - Choose **Add Row**
    - From the dropdown options, select **Insert After**

    <!-- border -->![Automation](019.png)

19. Similarly, enter the above values for the next rows.

20. Choose **Save**.

    <!-- border -->![Automation](021.png)


### Bind parameters to decision

1. Navigate back to the **Order Processing** process.
   
2. Select the **Order Validity Check** decision and choose **Inputs** in decision details.

3. Map the input parameters listed in `Input Sales Order` to the `selectedOrder` output variables from **Get Order Details** automation.
   
4. Choose **save**.

    <!-- border -->![Automation](024.png)


### Create rejection notification form with tables

1. In the **Overview** tab, click the **Create** dropdown and choose **Form**.

    <!-- border -->![Automation](025.png)

2. In the **Create Form** popup, enter the form name and choose **Create**.

    <!-- border -->![Automation](026.png)

3. Add a **Headline** and **Paragraph** to provide necessary details. Add two **Text** fields and name them **Customer Name** and **Order Number**.
   
4. Check both **Text** fields as read only.

    <!-- border -->![Automation](027.png)

5. Add a **Table** with **Error Details** as title. Mark it as Read Only.

    <!-- border -->![Automation](028.png)

6. Choose the **+** icon in the table and select **Text**. Enter **Error Code** as field name.

    <!-- border -->![Automation](029.png)
    
7. Choose the **+** icon beside Error Code field and select **Text**.

    <!-- border -->![Automation](030.png)
    
8. Enter **Error Description** as field name and choose **Save**.

    <!-- border -->![Automation](031.png)


### Create condition and add rejection form

1. In the **Order Processing** process choose the **+** sign after the **Order Visibility Check** decision.

    <!-- border -->![Automation](032.png)

2. Choose **Controls and Events**.
   
    <!-- border -->![Automation](032a.png)
  
3. Select **Condition**.

    <!-- border -->![Automation](032b.png)

4. Choose the **Open Condition Editor** for the new condition.

    <!-- border -->![Automation](033.png)

5. In the **Edit Branch Condition** popup select the `list-Validity Check Output` parameter.

    <!-- border -->![Automation](034.png)

6. Put **0** as value and select **Apply**.

    <!-- border -->![Automation](035.png)

7. In the **If** branch of the new condition, choose **+** to add a new artifact.
  
    <!-- border -->![Automation](035a.png)

8. Select **Form**.

    <!-- border -->![Automation](035b.png)

9. Select **Order Rejection Notification With Errors** under **Available Forms**.

    <!-- border -->![Automation](036.png)
    
10. In the **General** section of form details:
    
    - Enter as **Subject**: Order Rejected due to errors
    - Choose **Process Started By** as **users** under **Recipients**.

    <!-- border -->![Automation](037.png)
    
11. Under **Inputs** section, choose **Select list** and bind `list-Validity Check Output` to it.

    <!-- border -->![Automation](038.png)

12. Choose the **Order Number** and **Customer Name** from trigger form to map them with the respective input fields.

    <!-- border -->![Automation](039.png)
    
13. Select the **+** after **Order Rejection Notification with Errors** form.
    
    <!-- border -->![Automation](039a.png)

14. Choose **Controls and Events**.
    
    <!-- border -->![Automation](039b.png)

15. Choose **End**.

    <!-- border -->![Automation](040.png)

    At the end, your process will look like this.
    
16. Save your work.

    <!-- border -->![Automation](042.png)


### Release and deploy

1. In the **Order Processing** process, choose the **Release** button on the top right corner.

    <!-- border -->![Automation](043.png)

2. In the **Release Project** popup, select **Release**.

    <!-- border -->![Automation](044.png)

3. In the **Overview** section that appears, choose **Deploy**.

    <!-- border -->![Automation](045.png)

4. Choose the **Environment** and select **Deploy**.

    <!-- border -->![Automation](environment.png)

5. In the **Define Variables** section, enter the `filePath` for the excel file you downloaded in the prerequisites section. Choose **Deploy**.

    <!-- border -->![Automation](047.png)
    
    Your project is deployed.

    <!-- border -->![Automation](049.png)


### Test the process

1. In the **Order Processing** process, choose the **Order Processing Form** artifact. On the right panel that appears, select the **Copy Link** icon next to **Form Link** field.

    <!-- border -->![Automation](050.png)

2. Before executing the process, make sure your desktop agent is in unattended mode. You can refer the prerequisites to Execute the Process with an Automation.

    <!-- border -->![Automation](054.png)

3. In a new tab in your browser, enter the form link. Enter the details required in the form and select **Submit**.

    <!-- border -->![Automation](051.png)

    When you enter the order number in the form, the automation fetches the order details from excel stored in your machine. The details are validated according to the rules in the decision table and the respective errors are shown in a table in the form.

4. In the SAP Build Lobby, choose the **Inbox** icon on the top right.

    <!-- border -->![Automation](052.png)

5. You will get a notification with the error details in a table.

    <!-- border -->![Automation](053.png)


### Retrieve sample project from the store

This sample project can be downloaded from the SAP Build Store.

To retrieve this sample, please follow these steps:
    
1. From the SAP Build Lobby, navigate to Store.
   
2. Search for the sample project: **Sales Order Management (MI05)**.
   
3. Choose **Create from Template** to retrieve the sample and save it as a new project in your lobby.

    <!-- border -->![Store](store.png)

4. Choose **Create**.

    <!-- border -->![Create](create.png)

    Your project gets created in editable version. You may release and deploy it and run the project.
    
5. Navigate back to the lobby by clicking on the SAP logo.
  
    <!-- border -->![Project](project.png)

    You can see your project is available in the lobby.
  
    <!-- border -->![Lobby](lobby.png)

---
