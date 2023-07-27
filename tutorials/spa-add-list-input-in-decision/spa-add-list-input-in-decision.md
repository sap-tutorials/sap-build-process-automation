---
parser: v2
author_name: Djamai Hania
author_profile: https://github.com/Haniadjamai
auto_validation: true
time: 30 
tags: [ tutorial>intermediate, software-product>sap-business-technology-platform, tutorial>free-tier ]
primary_tag: software-product>sap-build-process-automation
---

# Use list as an input for Decision artifact in SAP Build Process Automation.
 
<!-- description --> Use a list as an input to your Decision artifact, process the data and extract the details to a table in a Form.

## Prerequisites
  - Either complete the mission [Create Tables in the Form](https://developers.sap.com/tutorials/spa-forms-table.html).
  - Setup the desktop agent to run automation as explained in [this tutorial](spa-run-agent-settings).
  - Download the [Orders.xlsx](https://github.com/sap-tutorials/sap-build-process-automation-Contribution/blob/main/tutorials/spa-add-list-input-in-decision/Orders%20.xlsx) in your local machine. 

## You will learn
  - How to use a List as an input to your Decision.
  - How to use a reusable text rules. 
  - How to bind List in Decision to Table in Form.

## Intro

In this tutorial, you will automate the process where the Sales executive is notified about the erroneous or error-free Orders through a Task in the Inbox of SAP Build Process Automation.

The process is designed to have the following artifacts:

- A Form where the Sales Executive would provide the path of Sales Orders Excel maintained in his system.
- Automation to read the Sales order details.
- Decision artifact to process the details of a list of orders extracted from Excel. Based on the rules created in Decision, it would determine whether the order details are error-prone or error-free.
- Notification Form to the Sales executive which displays the erroneous or error-free Sales Orders in a Table format.

The process looks as below 

   <!-- border -->![decision](process.png)


---

### Create a new process 

After completing the prerequisites, you will create a new process.

1. Navigate to the **Artifacts** tab, from the editable version of your project, click the **Create** dropdown and choose **Process**.

    <!-- border -->![decision](2.png)

2. In the **Create Process** dialog box, do the following:

    - Enter a **Process Name** such as Order Processing Error Table.
    - Choose **Create**.

    <!-- border -->![decision](2-1.png)

    Your new process opens in the process builder. You will now create a trigger form that will start the process. 

3. Choose **+** in the **Trigger** settings, then select **Forms** and choose **New Form**.

    <!-- border -->![decision](3.png)


4. In the **Create Form** dialog box, do the following:

    - Enter a **Process Name** such as Order File Path Form.
    - Choose **Create**.

    <!-- border -->![decision](4.png)

5. Choose the three dots and select **Open Editor**.

    <!-- border -->![decision](5.png)

6. Now, you will edit the form by using the available layout and input field options. Start by dragging and dropping the form layout fields, then enter the given names and field settings as shown in the example below:

    |  **Form Fields**    | **Field Settings with Label**
    |  :------------- | :-------------
    |  Headline 1         | Order File Path Form
    |  Paragraph          | Please provide the full file path for the Excel file and submit. 
    |  Text               | File Path.

    <!-- border -->![decision](6.png)

7. For the input label **Text** select the **Required** checkbox, and **Save**. 

    <!-- border -->![decision](7.png)

8. **Save** the form.

### Create a new automation

1. Navigate to the **Artifacts** tab, from the editable version of your project, search for **Get Order Automation**. Choose the three dots and select **Duplicate**.

    <!-- border -->![decision](8.png)

2. In the **Duplicate Artifact** dialog box, enter a **Automation Name** such as Get Order Details For Error.

    <!-- border -->![decision](9.png)

    Your new automation opens in the process builder.

3. Now, Select all activities from **Create Sales Order** to **End** as shown in the image below, using Ctrl+Shift to select the requested activities. Right-click and select **Delete** from the context menu.

    <!-- border -->![decision](10.png)
    <!-- border -->![decision](11.png)


4. Click on the Canvas, in the Automation Details section on the right, select **Input/Output**, and in the inputs section rename `OrderNumber` to `FilePath`. Select **List** in the Output parameters.

    <!-- border -->![decision](12.png)

5. Select **Excel Cloud Link**, in the details on the right side, choose the **Edit activity** button.

    <!-- border -->![decision](13.png)

6. In the Workbook Path field enter the Environment Variable as `FilePath`.

    <!-- border -->![decision](16.png)

7. Select **End**, in the configuration screen on the right, under the Output Parameter, in the `SelectedOrderDetails` field enter ` Orders`.

    <!-- border -->![decision](13_2.png)
8. **Save** your automation.

9. Select **Order Processing Error Table** Process. Choose **+**, Select **Automation** and choose **Get Order Details For Error**.

    <!-- border -->![decision](14.png)

10. Choose **Get Order Details For Error** automation in the process and map the input parameter `FilePath` of the automation with the **File Path** of Order File Path Form.

    <!-- border -->![decision](15.png)

11. **Save** your process.


### Create Data Types

1. Go back to the **Overview** tab and Navigate to the **Artifacts** tab, select **Error Output** data.

    <!-- border -->![decision](data1.png)

2. In the **Error Output** data type screen, choose **New Field** to add a new attribute to the data object.

    <!-- border -->![decision](data3.png)

3. In the Field Details section on the right, in the **Name** field enter **Order Number**. Keep the Type as **String**.

    <!-- border -->![decision](data4.png)

4. **Save** your work.

    <!-- border -->![decision](data6.png)

### Create a new decision

1. Navigate to the **Order Processing Error Table** process. Choose **+**, Select **Decision** then **New Decision**.

    <!-- border -->![decision](17.png)

2. In the Create Decision window, enter a **Decision Name** such as **Order Error Checking**. And Choose **Create** button.

    <!-- border -->![decision](18.png)

3. Now you have to model the decision. For that, choose the 3 dots next to **Order Error Checking** decision and choose **Open Editor**.

    <!-- border -->![decision](19.png)


### Configure Input/Output of Decision

1. Go back to **Order Error Checking** decision tab. In the Determine Approver section, select **Add Input Parameter**  button and **Add Output Parameter** button to configure input and output parameters.

    <!-- border -->![decision](20.png)

2. Configure Input Parameter:

    - In Name enter: **Order List Input**,
    - In Description enter: **Order List Input**,
    - In Type choose: **Sales Order Excel**, and select **List**.

    <!-- border -->![decision](21.png)

3. Configure Output Parameter:

    - In Name enter: **Order Error List**,
    - In Description enter: **Order Error List**,
    - In Type choose: **Error Output**, and select **List**.

    <!-- border -->![decision](22.png)

4. **Save** your decision.

    <!-- border -->![decision](22-1.png)

### Configure Variables of Decision

1. Now, we will add intermediate variables that we will use to store the results of the rules. Select **Variables** and choose **Add Variable**.

    <!-- border -->![decision](23.png)

2. In the Decision Variable window:
    
    - In the Name enter **Order Input**.
    - In the Description enter **Intermediate variable to store Order Details**.
    - Under Type select **Sales Order Excel**.

    <!-- border -->![decision](24.png)

    > Here, we will use an intermediate variable to store the inputs, which can be utilized later in reusable text rules, thus avoiding overwriting the original inputs.

3. Similarly, for the second variable select **Add Variable**.

    <!-- border -->![decision](25.png)

4. In the Decision Variable window:
    
    - In the Name enter **Error Output**.
    - In the Description enter **Intermediate variable to store the error details of the Orders**.
    - Under Type select **Error Output**.

    <!-- border -->![decision](26.png)

    > This intermediate variable will serve to temporarily store the outputs of the text rules for each error test, without overwriting the results of the initial tests. Additionally, it allows appending the result of each test to the variable, preserving the information from previous tests.

5. **Save** your decision.

    <!-- border -->![decision](26-1.png)


### Configure Text Rules of Decision

1. Now, we are going to add reusable text rules, which are validation or error detection rules. Therefore, we will create a reusable rule for each error search in the command. Select **Rules** and choose **Add Rule**.

    <!-- border -->![decision](27.png)

2. The first text rule we will create is a test for the delivery date of the order. In the Create Rule window: 

    - In the Rule Type select **Text Rule**.
    - In the Rule Name enter **Date Error test**.
    - In the Rule Description enter **check order delivery date**.
    - Active **Reusable Rule**.
    - Choose **Next Step** button.

    <!-- border -->![decision](28.png)

3. Configure the output or result of the decision table. Under **Result Vocabulary**:

    - Select **Error Output** data type,
    - In the Vocabulary section choose **Error Output** to add the Result Attributes.
    - Choose **Next Step** button.

    <!-- border -->![decision](29.png)
    <!-- border -->![decision](30.png)

4. Review and choose **Create** button to create the rule.

    <!-- border -->![decision](31.png)

5. In the newly created **Text Rule**, add values to condition and result columns:

    - in the If condition: Order Input.expectedDeliveryDate > TODAY( )  
    - In `OrderNumber` enter : Order Input.orderNumber 
    - In `ErrorDescription` enter : 'Delivery date is after current date' 
    - In `ErrorCode` enter : 'ERR1'

    > Do not copy and paste the values, use the Suggestions pop up (Ctrl+Space) as shown in the picture below. When entering the error code and its description, please remember to put two singles quotes first and then type the code and description inside them.

    <!-- border -->![decision](32-1.png)

    Once you have successfully entered the values, your rule looks as below.

    <!-- border -->![decision](32.png)


6. **Save** your work.

    <!-- border -->![decision](32-2.png)

7. Go back to **Rules**, click on **Back Button**.

    <!-- border -->![decision](33-1.png)

8. click on the three dots next to **Date Error Test** rule and choose **Duplicate**.

    <!-- border -->![decision](33.png)

9. The second text rule we will create is a test for the order amount. In the Duplicate Rule window: 

    - In the Rule Name enter **Order Amount Error test**.
    - In the Rule Description enter **Test the order amount**.
    - Choose **OK** button.

    <!-- border -->![decision](34.png)

10. Click on the **Order Amount Error test** rule.

    <!-- border -->![decision](35.png)

11. In the newly created **Rule Text**, add values to condition and result columns:

    - in the If condition: Order Input.orderAmount > 1000000 
    - In `OrderNumber` enter : Order Input.orderNumber 
    - In `ErrorDescription` enter : 'Fraudulent Request'  
    - In `ErrorCode` enter : 'ERR2'

    <!-- border -->![decision](37.png)

12. **Save** your rule.

13. Go back to **Rules**, click on **Back Button**.

    <!-- border -->![decision](33-2.png) 

14. Now, we will create three more text rules to perform three additional tests. To do this, repeat the same step: click on the three dots next to text rule and select **Duplicate** to create the three new text rules.

    <!-- border -->![decision](33-3.png) 

15. The third text rule we will create is a test for shipping country. So similarly **Duplicate** a new text rule and in the Duplicate Rule window: 

    - In the Rule Name enter **Shipping Country Error Test**.
    - In the Rule Description enter **check The Shipping Country**.
    - Choose **OK** button.

    <!-- border -->![decision](38.png)

16. Click on the newly created **Text Rule** and add values to condition and result columns:

    - in the If condition: Order Input.shippingCountry NOTEXISTSIN [ 'India' , 'United Kingdom' ]  
    - In `OrderNumber` enter : Order Input.orderNumber 
    - In `ErrorDescription` enter : 'Delivery not supported in this country'   
    - In `ErrorCode` enter : 'ERR3'
    - **Save** your rule and click on **Back Button**.

    <!-- border -->![decision](41.png)

17. The same goes for the fourth text rule, we will create is a test for the order status. **Duplicate** a new text rule and in the Duplicate Rule window: 

    - In the Rule Name enter **Order Status Error Test**.
    - In the Rule Description enter **test order status**.
    - Choose **OK** button.

    <!-- border -->![decision](42.png)

18. Click on the newly created **Text Rule**, add values to condition and result columns:

    - in the If condition: Order Input.orderStatus = '' 
    - In `OrderNumber` enter : Order Input.orderNumber 
    - In `ErrorDescription` enter : 'Order status is not set'   
    - In `ErrorCode` enter : 'ERR4'
    - **Save** your rule and click on **Back Button**.

    <!-- border -->![decision](45.png)

19. Similarly for the final text rule, we will verify if the order has no errors. In the Duplicate Rule window: 

    - In the Rule Name enter **No Error Test**.
    - In the Rule Description enter **test if the order has no errors**.
    - Choose **OK** button.

    <!-- border -->![decision](46.png) 

20. Click on the newly created **Text Rule**, add values to condition and result columns:

    - in the If condition: Order Input.orderDate <= TODAY( ) AND Order Input.orderAmount < 1000000 AND Order Input.shippingCountry EXISTSIN [ 'India' , 'United Kingdom' ] AND Order Input.orderStatus != '' 
    - In `OrderNumber` enter : Order Input.orderNumber 
    - In `ErrorDescription` enter : 'No Error'   
    - **Save** your rule and click on **Back Button**.

    <!-- border -->![decision](49.png)

### Configure Main Rule of Decision

    Now, we will create a rule that will execute and utilize all the reusable text rules we created before in a loop for each order. The results will be sent to an error table stored in the previously created variable.

1. Go back to **Rules** and click on **Add Rule**.

    <!-- border -->![decision](50-1.png)

2. In the Create Rule window: 

    - In the Rule Type select **Text Rule**.
    - In the Rule Name enter **Main Rule**.
    - In the Rule Description enter **A rule that executes all error-testing rules in a loop for each order**.
    - Choose **Next Step** button.

    <!-- border -->![decision](50.png)

3. In the **Configure Results** step, under **Result Vocabulary** choose `No Result` and click on **Next Step** button.

    <!-- border -->![decision](51.png)
    <!-- border -->![decision](52.png)

4. Review and choose **Create** button to create the rule.

    <!-- border -->![decision](53.png)

5. In the newly created **Text Rule**, In the **If** statement, assign `true` to represent the absence of any specific condition.

    <!-- border -->![decision](54.png)

6. In the **Then** statement, press **Ctrl+Space** on your keyboard and select **Loop Functions**.

    <!-- border -->![decision](55.png)

7. A window for configuring loop functions opens. Configure the function as follows: 

    - In the Vocabulary select **Order List Input**.
    - In the Current Item select **Order Input**. 
    - In the Expression statement enter: APPEND( Order Error List ,  Date Error test )

    <!-- border -->![decision](56.png) 

    > In this function, what we have done is iterate through each element, which represents each order, and perform the delivery date test. Then, we append the test output to the **Order Error List**.  So, the objective is to repeat the same process for each reusable text error rule that we have previously created and gradually add the collected errors for each order to the **Order Error List**.

8. Click on the **+** to add a new expression box and enter : APPEND( Order Error List ,  Order Amount Error Test )

    <!-- border -->![decision](57.png)

9. Similarly, add three more expression box and enter the following in each box: 

    - First box : APPEND( Order Error List ,  Shipping Country Error Test  )
    - Second box : APPEND( Order Error List ,  Order Status Error Test )
    - Third box : APPEND( Order Error List ,  No Error Test )
    - Choose **Apply** button.

    <!-- border -->![decision](58.png)

    > So, here we will iterate through all the reusable text error rules that we have created earlier, one by one, for each order. The result obtained from each rule, whether there is an error or not, will be added to the **Order Error List** list without overwriting the previous results. That's why we have used an intermediate variable.

10. **Save** your work. 

    <!-- border -->![decision](59_1.png)
    <!-- border -->![decision](59.png)

### Configure Decision in Process Builder

1. Navigate to the **Order Processing Error Table** process, choose **Order Error Checking** decision and do the following. Choose **Inputs** tab, under the select list click on the `List SalesOrderDetails`.

    <!-- border -->![decision](60.png)

    Bind the properties for `SalesOrderDetails` list.

    <!-- border -->![decision](60_1.png)

2. **Save** the process.

### Create Order Error Table Form

1. Go back to the **Overview** tab and Navigate to the **Artifacts** tab, search for **Order Rejection Notification With Errors** form. Choose the three dots and select **Duplicate**.

    <!-- border -->![decision](61.png)

2. In the **Duplicate Artifact** dialog box, enter a **Form Name** such as  **Order Error Table Form** and click on **Duplicate**

    <!-- border -->![decision](62.png)

    Your new form opens in the process builder.

    <!-- border -->![decision](63.png)

3. Click on the three buttons next to **Customer Name** and next to **Order Number**, then choose **Delete** to remove them.

    <!-- border -->![decision](64.png)
    <!-- border -->![decision](65.png)

4. Now, change the **Headline** and the **Paragraph** following the table below..

    |  **Form Fields**    | **Field Settings with Label**
    |  :------------- | :-------------
    | Headline 1 | Order Error Summary Table. 
    | Paragraph  | The table below represents your processed order list with details of the errors found. 

    <!-- border -->![decision](66.png)

5. Modify the table to add a cell for the **Order Number**. Click on the **+** icons beside Output Code field and select **Text** and enter **Order Number** as field name

    <!-- border -->![decision](67.png)
    <!-- border -->![decision](68.png)

6. Click on the three dots next to **Order Number** and choose **Move Left** to shift the cell to the left, and repeat the operation to move the cell all the way to the left of the table.

    <!-- border -->![decision](69.png)
    <!-- border -->![decision](70.png)

7. **Save** your form.

    <!-- border -->![decision](71.png)

8. Navigate to the **Order Processing Error Table** process.

    - choose **+** next to the decision.
    - Select **Forms** then **Order Error Table**.

    <!-- border -->![decision](72.png)

10. Configure the **General** information section:

    - In the **Subject** section, enter **Order Error**.
    - In the **Recipients** section, under Users, select **Process Started By** from Process Metadata.

    <!-- border -->![decision](73.png)

11. Now, configure the **Input** information section. In the select list choose `List Order_Error_List`.

    <!-- border -->![decision](74.png)

12. **Save** the process.

    <!-- border -->![decision](75.png)

### Release and deploy

1. In the **Order Processing Error Table** process, choose the **Release** button in the top right corner.

    <!-- border -->![decision](76.png)

2. In the **Release Project** popup, select **Release**.

    <!-- border -->![decision](77.png)

3. In the **Overview** section that appears, choose **Deploy**.

    <!-- border -->![decision](78.png)

4. In the popup that appears, choose **Next**.

    <!-- border -->![decision](78-1.png)

5. In the **Runtime Variables** section, choose **Next**. You will enter the `ordersFilePath` as you would provide the path of excel in the Input form which is explained in **Step 13: Test the process**.

    <!-- border -->![decision](78-2.png)

6. In the **Triggers** section, choose **Deploy**.

    <!-- border -->![decision](78-3.png)

7. After project deployment, a confirmation popup will appear. Choose **Close**.

    <!-- border -->![decision](78-4.png)

### Configure process with Automation.

1. Before executing the process, make sure your desktop agent is in unattended mode.

    <!-- border -->![decision](80-1.png)

   Please complete the two tutorials before you test the automation:

- Execute the Process with an Automation. [Mentioned in Pre-requisites](https://developers.sap.com/tutorials/spa-run-agent-settings.html).
- [Add agent attributes](https://developers.sap.com/tutorials/spa-run-agent-settings.html) to the project.

### Test the process

1. Open the process builder of the deployed version and choose **Order File Path Form**, select the **Copy Link** icon under **Form Link**.

    <!-- border -->![decision](80.png)

2. In a new tab in your browser, enter your file path and select **Submit**.

    <!-- border -->![decision](81.png)

3. Once the form is submitted successfully, the BOT opens the **Sales order Excel** file which is stored in your system reads the data, and passes the data to the Decision. The Business rules are executed and the list of orders with/without errors are displayed in the Tables in the Form. 
    You can notice the steps of execution in the **Monitor** section.

    <!-- border -->![decision](monitor.png)

4. Now, the process indicates that the Task is available in **My Inbox**.

    <!-- border -->![decision](monitor2.png)

5. In the **SAP Build** lobby, choose **My Inbox** icon.

    <!-- border -->![decision](82.png)

6. You will get a notification with the error details in a table.

    <!-- border -->![decision](83.png)

Congrats! You have successfully completed the tutorial . With this process, Sales Executive is notified of erroneous and error free orders.





