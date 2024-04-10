---
parser: v2
author_name: Chaitanya Priya Puvvada
author_profile: https://github.com/chaitanya-priya-puvvada
auto_validation: true
time: 10
tags: [ tutorial>beginner, software-product>sap-business-technology-platform, tutorial>free-tier]
primary_tag: software-product>sap-build-process-automation
---

# Create an API Trigger for the Process
<!-- description --> Create an API trigger for the business process.

## Prerequisites
 - Acquire the template - Sales Order Management (MI01) by referring to tutorial [Acquire a Template Project From the Store](spa-acquire-businessprocess-store) **OR**
 - Complete the mission [Build Your First Business Process with SAP Build Process Automation](mission.sap-process-automation)

## You will learn
  - How to create an API trigger to start an instance of a business process from any service, like SAP Build Apps


## Intro
A business process is started by defining a trigger, an event that indicates to your SAP Build Process Automation tenant to start a process instance.

Process triggers can be a form, such as a request form, an API call, where an external system starts the process or an Event.

You can start an instance of your process using an API call, with the inputs for the call configured from the process builder. These inputs can then be used as input fields in your process.

You may also start the instance with an event trigger which on-boards and listens to back-end events emitted from an external source system and reacts to such events by triggering artifacts such as processes and automations.

### Create a data type

A data type is an artifact describing a data structure that can be used as an input and/or an output parameter in automations or processes. You have two options to create the fields in the data type. You can either import an excel file or define the fields manually.

Once you have acquired the Template Project from the Store, your process looks as below:

<!-- border -->![template](28.png)

[OPTION BEGIN [Import Excel File]]

In this option, you will be importing an excel file to create the data type. Based on the values present in the excel, the type of field is determined automatically and the fields are created accordingly. For example `orderAmount` is maintained as 19000, hence the type of the field `orderAmount` is determined as Number.

1.  Download [SalesorderDatatype.xlsx](https://github.com/sap-tutorials/sap-build-process-automation/blob/main/tutorials/spa-create-process-api-trigger/SalesorderDatatype.xlsx) excel file for Sales Order datatype.

    <!-- border -->![Create data type](excelFile.png)

2.  Navigate to your project. Click on the **Project Content** icon on the top left corner > **+** > **Create** > **Data Type** .

    <!-- border -->![Create data type](20.png)

3.  Name the data type **Sales Order**.

    <!-- border -->![SalesOrder](21.png)

4. Click on **Import Excel File**.

    <!-- border -->![Excelfile](22.png)

5. Click on **Browse** to select the excel file.

    <!-- border -->![Excelfile](23.png)

6. Select **Import an Excel File**.

    <!-- border -->![excelFile](24.png)


    Your final data type looks as below.

    <!-- border -->![DataType](25.png)

[OPTION END]

[OPTION BEGIN [Define Fields Manually]]

In this option you will be defining each field with field name and type of field manually.

1.  Click on the **Project Content** icon on the top left corner > **+** > **Create** > **Data Type**.

    <!-- border -->![Create data type](20.png)

2.  Name the data type **Sales Order**.

    <!-- border -->![dataType](21.png)

3. Click on **New Field** to add new fields to the data type **Sales Order**.

    <!-- border -->![dataFields](26.png)


4.  Repeat the process to add all the fields of the type as shown below.

    |  Field Name   | Type
    |  :------------- | :-------------
    |  `customerName`     | String |
    |  `orderNumber`     | String |
    |  `orderAmount`     | Number |
    |  `orderDate`    | Date|
    |  `shippingCountry`    | String|
    |  `expectedDeliveryDate`  | Date|

    >**IMPORTANT:** The spelling and casing of the fields, as well as any extra spaces, is crucial because the API to trigger the process will require the fields exactly as written.

    Your final data type looks as below. Click **Save** to save the data type.

    <!-- border -->![DataType](25.png)


[OPTION END] 

### Create an API trigger for the process


1. Open the process **Order Processing**.

    <!-- border -->![Process](29.png)

2. From the **Editable** version of the project, choose the three dots of the **Order Processing Form** and select **Remove** to delete the form.

    <!-- border -->![Delete Form](30.png)

    A warning message will inform you that the related bindings will be removed. Choose **OK**.

    <!-- border -->![Warning](3.png)

3. **Save** the project.

4.  To add an API trigger for the process, click on the **Add a Trigger** > **Call an API**.
 

    <!-- border -->![New API Trigger](31a.png)
    <!-- border -->![New API Trigger](31b.png)


5.  Enter the name of the trigger as **Sales Order Trigger**. Choose **Create**.

    <!-- border -->![Create API Trigger Pop Up](5.png)

6. **Save** your project.


### Create inputs for the process

1. Open the **Process Details** by clicking on the Canvas.
   
    <!-- border -->![Process Details](45.png)

2. Choose **Variables**. Then choose **Configure** to configure process inputs.
   
    <!-- border -->![Configure](46.png)

3. Delete the existing inputs by clicking on the delete button. 
   
    >The existing inputs were configured from the **Order Processing Form**. Since you have removed it, you will need to configure new input parameters for the **Sales Order Trigger**.

    <!-- border -->![Delete](47.png)

4. Choose **Add Input** and add the following parameter:

    |  **Name**    | **Type**
    |  :------------- | :-------------
    |  `salesOrderDetails`       | `SalesOrder`

    Check the **Required** box and choose **Apply**.

    <!-- border -->![Delete](49.png)

5. **Save** your project.

6. Once the trigger is created successfully, you can view the trigger under the **Triggers**  section in the **Overview** page.

    <!-- border -->![Triggers Overview](32.png)  

    >You can edit, deactivate, or delete the API trigger properties from Triggers tab in the respective process builder overview.
    >
    >- Deactivate means that while the trigger exists in design-time, you cannot consume it in runtime.
    >
    >- Delete will permanently delete the trigger from design-time, but for already deployed processes the trigger will still exist at runtime.
    >
    >In general, any changes in the trigger will be effective only when the process is released and deployed.
    >
    >**Note:** All the API triggers that are created in that project will be shown.

### Modify the process

Since you have created an API trigger, the bindings were lost. Let's adjust the process with the new inputs configured for the API trigger.

1. Choose the condition artifact and click on **Open Condition Editor**.

    <!-- border -->![Condition](33.png)

2. Enter the condition for `orderAmount`.

    <!-- border -->![Condition](8.3.png)

    <!-- border -->![Condition](9.2.png)

3. Enter the condition for `shippingCountry`.
     
    <!-- border -->![Condition](50.png)
    
    <!-- border -->![Condition](51.png)

3. Click on **Apply**.

4. Choose **Approval Form** to adjust the bindings. Modify the **General** section.
  In the Subject field, do the following:

    - Enter **Review and approve order**
    - Select **Order Number** from Process Inputs
    - Enter **from**
    - Select **Customer Name** from Process Inputs
    - Enter **company**

    <!-- border -->![Condition](35a.png)

    Since the process would be started through an API, remove the Users **Process Started by** and enter your `EmailID` that was configured for the tenant.

    <!-- border -->![Condition](35.png)

5. Modify the **Inputs** section.

    <!-- border -->![Condition](36.png)

6. Choose **Order Confirmation Form** to adjust the bindings. Modify the **General** section.
  In the Subject field, do the following:

    - Enter **Your order**
    - Select **Order Number** from Process Inputs
    - Enter **has been successfully received**

    <!-- border -->![Condition](37a.png)

    Since the process would be started through an API, remove the Users **Process Started by** and enter your `EmailID` that was configured for the tenant.

    <!-- border -->![Confirmation](37.png)

1. Modify the **Inputs** section.

    <!-- border -->![Inputs](38b.png)

2. Choose **Order Rejection Notification Form** to adjust the bindings. Modify the **General** section.
  In the Subject field, do the following:

    - Enter **Your order**
    - Select **Order Number** from Process Inputs
    - Enter **is rejected by the supplier**

    <!-- border -->![Condition](39a.png)

    Since the process would be started through an API, remove the Users **Process Stared by** and enter your `EmailID` that was configured for the tenant.

    <!-- border -->![Rejection Form](39.png)

1. Modify **Inputs** section.

    <!-- border -->![Inputs](40b.png)

2.  Choose **Auto Approval Notification Form** to adjust the bindings. Modify the **General** section.
  In the Subject field, do the following:

    - Enter **Your order**
    - Select **Order Number** from Process Inputs
    - Enter **has been successfully received**

    <!-- border -->![Condition](41a.png)

    Since the process would be started through an API, remove the Users **Process Started by** and enter your `EmailID` that was configured for the tenant.

    <!-- border -->![Approval Notification](41.png)

1.  Modify the **Inputs** section.

    <!-- border -->![Inputs](42.png)

2.  **Save** your project.



### Release and deploy the process with an API trigger

1. **Release** the project.

    <!-- border -->![Release](43.png)


2. After successful release of the project, **deploy** the project.

    <!-- border -->![Deploy](44.png)

    You have successfully released and deployed the process and it is ready to consume via APIs.









---
