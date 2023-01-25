---
parser: v2
author_name: Chaitanya Priya Puvvada
author_profile: https://github.com/chaitanya-priya-puvvada
auto_validation: true
time: 15
tags: [ tutorial>beginner, software-product>sap-business-technology-platform, tutorial>free-tier]
primary_tag: software-product>sap-build-process-automation
---

# Test an API Trigger for a Business Process
<!-- description --> Run API trigger for the Business Process.

## Prerequisites
 - Complete [Create an API trigger for Business Process ](spa-create-process-api-trigger)
 - Complete [Create Service Key for Build Process Automation](spa-create-service-instance-destination)

## You will learn
- How to discover APIs in SAP API Business Hub
- How to test APIs in SAP API Business Hub
- How to test an API trigger of a business process
- How to start the business process from other services

---

### View an API trigger for the process

Once you have successfully deployed the business process with an API trigger, you can view the API trigger in the **Overview** section under the tab **Triggers**.

1. Click **View** to see context of the workflow API.

    <!-- border -->![Triggers](1.png)

    Copy the payload which would be used in the later steps .

2. You can view the API URL and the payload to start the process.

    <!-- border -->![Trigger Payload](2.png)  

    Details of the payload:

    |  **Name**    | **Details**
    |  :------------- | :-------------
    |  `definitionId`       | ID of the process after it is deployed
    |  `salesorderdetails`       | Input parameter for the API trigger

  You can even get the process `definitionId` from the **Monitor** section as shown below.

  <!-- border -->![Workflow DefinitionID](3.png)

### Create demo environment to test API trigger

All Process Automation APIs (except Inbox APIs which are OData v2 API) are REST APIs that are based on OAuth 2.0 and other methods like API keys.

1. Login to [SAP API Business Hub](https://api.sap.com/package/SAPProcessAutomation/all) to explore them.

    <!-- border -->![API Business Hub](4.png)


2. To trigger the process with an API Trigger, click on **Process and Workflow instances**.

    <!-- border -->![Process and Workflow](5.1.png)

3. Click on **View API Reference**, and then navigate to **Workflow Instances** --> **POST** --> **Try out**.

    <!-- border -->![Try out API](6.png)

4. Let's create a Demo Environment to test the API. Click **Select Environment**.

    <!-- border -->![Select Environment](7.png)

    Map the credentials of the service key that you have created  for SAP Build Process Automation as mentioned in **pre-requisites**.

    <!-- border -->![Credentials](credentials.png)

    | Field|Value
    | --- | :---
    | Client ID | Client ID from the Service key credentials
    | Client Secret | Client Secret from the Service key credentials
    | Token Service URL|  url/oauth/token, where url is noted from Service key credentials


    <!-- border -->![Credentials in Demo Environment](11.png)

5. After successful creation of demo environment, the token for the API call would be added to the header section.

    <!-- border -->![Try out API](12.png)  


### Test API trigger for the process

1. Copy the payload that you copied in Step 1 of section **View an API trigger for the process** and paste it as shown below.

    <!-- border -->![Copy Payload](13.png)  

    The payload looks as below before execution of the API. Click **Run** to trigger the API, which would start your process.

    <!-- border -->![Run](14.png)

2.  You can see the status code of the API as **201**, which is Success, meaning the process was triggered.

    <!-- border -->![Success](15.png)


### Monitor the triggered process in Home Page.

In the home page of SAP Build Process Automation tenant, navigate to **Monitor**-->**Process and Workflow instances** to view the running instance of your process that was triggered from API call.

  <!-- border -->![Success](16.png)













---
