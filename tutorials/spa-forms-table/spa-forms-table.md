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
<!-- description --> Validate the order details extracted from the automation and display the error details in table in a form.

## Prerequisites
 - Complete the mission [Boost your Business Process with Automation, Decision and Process Visibility](mission.sap-process-automation-boost).
 - Download the [Orders.xlsx](https://github.com/sap-tutorials/sap-build-process-automation/blob/main/tutorials/spa-forms-table/Orders.xlsx) on your local machine.
 - Setup the desktop agent to run automation as explained in [this tutorial](spa-run-agent-settings)

## You will learn
  - How to create Table in the Form.
  - How to use List in Decision.
  - How to bind List in Decision to Table in Form.
  - How to retrieve the sample project from the Store.

## Intro
In this tutorial, you will be creating a Decision to validate the Purchase Order Details extracted from excel. If the Purchase Order Details has errors, the errors will be displayed in a table in a form.

---

### Create decision artifact

Once you have completed the prerequisite mission, your process should look something like below. 

<!-- border -->![Automation](042.png)

1. Select the process **Order Processing**.
    - Choose **+**.
    - Select **Decision**,  **New Decision**.

    <!-- border -->![Automation](001.png)

2. A pop up will appear to configure the decision. Enter **Order Validity Check** as decision name and choose **Create**.

    <!-- > It would be with suffix as **Registered**. -->

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


1. Navigate to the **Order Processing** process.Select the decision **Order Validity Check** menu option and choose **Open Editor**.

    <!-- border -->![Automation](007.png)

2. Add Input and Output parameters.

    <!-- border -->![Automation](008.png)

3. Edit Input and Output parameters as follows.

    |  Parameter Name       | Data type        | Parameter Type | Description
    |  :---------------     | :-------------   | :------------- | :---------------
    |  `Input Sales Order`      | Sales Order     | Input          | Input Sales Order
    |  `Validity Check Output`    | Error Output| Output         | Validity Check Output

    Select the **List** checkbox to make the output type as list of Error Outputs.

    <!-- border -->![Automation](009.png)

4. Select the **Rules** tab. Choose **Add Rule**.


    <!-- border -->![Automation](011.png)



5. Enter **Rule Name** as Error Check and **Rule Description** of your choice.

6. Choose **Next Step**.

    <!-- border -->![Automation](012.png)

7. In the **Configure Conditions** section, expand the **Input Sales Order** parameter.

    <!-- border -->![Automation](013.png)

8. For this scenario you will be choosing `expectedDeliveryDate`, `orderAmount`, `shippingCountry` and `orderStatus`. Choose **Next Step**.

    <!-- border -->![Automation](014.png)
    <!-- border -->![Automation](015.png)

9. In the **Configure Results** section, enter Validity Check Output in **Result Vocabulary**. Choose **Validity Check Output** parameter. Choose **Next Step**.

    <!-- border -->![Automation](016.png)

10. In the **Review** section, a summary of the rule to be added is displayed. Choose **Create**.

    <!-- border -->![Automation](017.png)

11. In the **Decision Table**, add the below mentioned conditions. Choose **Save**.

    |  Parameter Name       | Condition        | Error Code | Error Description
    |  :---------------     | :-------------   | :------------- | :---------------
    |  `expectedDeliveryDate`      | >TODAY()     | 'ERR01'          | 'Delivery date is after current date'
    |  `orderAmount`    | >10000000| 'ERR02'              | 'Fraudulent Request'
    |  `shippingCountry`      | NOTEXISTSIN ['India','United Kingdom']     | 'ERR03'               | 'Delivery not supported in this country'
    |  `orderStatus`    | =''| 'ERR04'              | 'Order status is not set'



    <!-- border -->![Automation](018.png)

    <!-- border -->![Automation](019.png)

    <!-- border -->![Automation](021.png)

    <!-- border -->![Automation](022.png)


### Bind parameters to decision


1. Go to the **Order Processing** process.Select the **Order Validity Check** decision and choose **Inputs** in decision details.

    <!-- border -->![Automation](023.png)

2. Map the input parameters listed in `Input_Sales_Order` to the `selectedSalesOrder` output variables from **Get Sales Order Details** automation.

    <!-- border -->![Automation](024.png)

### Create rejection notification form with tables

1. In the **Overview** tab, click the **Create** dropdown and choose **Form** under **Process** section.

    <!-- border -->![Automation](025.png)

2. In the **Create Form** popup, enter the form name and choose **Create**.

    <!-- border -->![Automation](026.png)

3. Add a **Headline** and **Paragraph** to provide necessary details. Add the **Customer Name** and **Order Number** as read only fields.

    <!-- border -->![Automation](027.png)

4. Add a **Table** with **Error Details** as title. Mark it as Read Only.

    <!-- border -->![Automation](028.png)


5. Choose the **+** icon in table and select **Text**. Enter **Error Code** as field name.

    <!-- border -->![Automation](029.png)
    
6. Choose the **+** icons beside Error Code field and select **Text**.

    <!-- border -->![Automation](030.png)
    
7. Enter **Error Description** as field name and choose **Save**.

    <!-- border -->![Automation](031.png)


### Create condition and add rejection form

1. In the **Order Processing** process choose the **+** sign and select **Condition** under **Controls**.

    <!-- border -->![Automation](032.png)

2. Choose the **Open Condition Editor** for the new condition.

    <!-- border -->![Automation](033.png)

3. In the **Edit Branch Condition** popup select the `list-Valicity_Check_Output` parameter.

    <!-- border -->![Automation](034.png)

4. Put **0** as value and select **Apply**.

    <!-- border -->![Automation](035.png)


5. After the new condition
    - Choose **+** to add a new artifact.
    - Select **Order Rejection Notification With Errors** under **Forms**.

    <!-- border -->![Automation](036.png)
    
6. In the **General** section of form details, add **Process Started By** as **Recipient**.

    <!-- border -->![Automation](037.png)
    
7. Under **Inputs** section, choose **Select list** and bind `list Validity_Check_Output` to it.

    <!-- border -->![Automation](038.png)

8. Choose the **Order Number** and **Customer Name** from trigger form to map them with the respective input fields.

    <!-- border -->![Automation](039.png)
    
9. Select the arrow after **Order Rejection Notification with Errors** form and drag it to connect with the **END** of the process.

    <!-- border -->![Automation](040.png)

10. Select the **+** symbol after the **Default** branch and drag it to connect with the previous condition.

    <!-- border -->![Automation](041.png)

11. At the end, your process will look like this.

    <!-- border -->![Automation](042.png)

### Release and deploy

1. In the **Order Processing** process, choose the **Release** button in the top right corner.

    <!-- border -->![Automation](043.png)

2. In the **Release Project** popup, select **Release**.

    <!-- border -->![Automation](044.png)

3. In the **Overview** section that appears, choose **Deploy**.

    <!-- border -->![Automation](045.png)

4. In the popup that appears, choose **Next**.

    <!-- border -->![Automation](046.png)


5. In the **Runtime Variables** section, enter the `filePath` for the excel file you downloaded in the prerequisites section. Choose **Next**

    <!-- border -->![Automation](047.png)
    
6. In the **Triggers** section, choose **Deploy**.

    <!-- border -->![Automation](048.png)
    
7. After project deployment, a confirmation popup will appear. Choose **Close**.

    <!-- border -->![Automation](049.png)

### Test the process

1. In the **Order Processing** process, choose the **Order Processing Form** artifact. In the right panel that appears, select the **Copy Link** icon under **Form Link** field.

    <!-- border -->![Automation](050.png)

2. Before executing the process, make sure your desktop agent is in unattended mode. You can refer the prerequisites to Execute the Process with an Automation.

    <!-- border -->![Automation](054.png)

3. In a new tab in your browser, enter the form link. Enter the details required in form and select **Submit**.

    <!-- border -->![Automation](051.png)

    When you enter the order number in the form, the automation fetches the order details from excel stored in your machine. The details are the validated according to the rules in the decision table and the respective errors are shown in a table in the form.

4. In the SAP Build Lobby, choose the **Inbox** icon on the top right.

    <!-- border -->![Automation](052.png)

5. You will get a notification with the error details in a table.

    <!-- border -->![Automation](053.png)

### Retrieve sample project from the store

This sample project can be downloaded from the SAP Build Store.

To retrieve this sample, please follow these steps:
    
1. From the SAP Build Lobby, navigate to Store.
   
2. Search for the sample project: **Sales Order Management (TU05)**.
   
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
