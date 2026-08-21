---
parser: v2
author_name: Khushi Yadav
author_profile: https://github.com/khushiyadavsap
auto_validation: true
time: 15
tags: [ tutorial>intermediate, software-product>sap-business-technology-platform, tutorial>free-tier ]
primary_tag: software-product>sap-build-process-automation
---

# Integration With SAP Analytics Cloud and SuccessFactor

<!-- description --> Learn how to connect to external systems like SAP Analytics Cloud and SuccessFactor using action in SAP Build Process Automation to customize or extend standard business processes.

## Prerequisites

- SAP SuccessFactors
- SAP Analytics Cloud
- Configure SMTP server destination by referring to [configuring-smtp-mail-destination](https://help.sap.com/docs/build-process-automation/sap-build-process-automation/configuring-smtp-mail-destination)

## You will learn

- How to acquire a template project from the store and customize it
- Use actions in a business process to implement changes in an external dedicated system

## Intro

Action is a feature in SAP Build Process Automation to connect processes with external systems. It allows users to automate or extend their business processes for any available LoB processes like S/4HANA, `Ariba`, SuccessFactors, SAP Analytics Cloud etc. In this tutorial, you will create a request to approve a position in the HR Planning Process. If the request gets approved then a position is created in the dedicated system.

### Retrieve the project from store

1. From the SAP Build Lobby, navigate to the store.
2. Search for the sample project: **SAC HR Position Planning**.
3. Choose **Create from Template** to retrieve the sample and save it as a new project in your lobby.

    ![Store](store1.png)

4. Choose **Create**.

    ![Create](create1.png)

    Your project gets created in editable version.

### Modify the process

1. Choose the process **SAC HR Position Planning**.

    ![Process](process.png)

2. Choose **Mail - Approved** and select **Open Mail Body Editor**.

    ![MailBody](openMail.png)

3. Click on **SuccessFactors** in the mail body and choose **Edit**.

    ![Edit](edit.png)

4. Replace the link and choose **Save**.

    ![save](save.png)

5. Click on **headcount plan** in the mail body and choose **Edit**.

    ![headcount](head.png)

6. Replace the link and choose **Save**.

    ![save](save2.png)

7. Choose **Apply**.

    ![Apply](apply.png)

8. Choose **Mail - Rejected** and select **Open Mail Body Editor**.

    ![MailBody](open.png)

9. Click on **headcount plan** in the mail body and choose **Edit**.

    ![headcount](count.png)

10. Replace the link and choose **Save**.

    ![save](save3.png)

11. Choose **Apply**.

    ![Apply](apply2.png)


### Configure destinations in SAP Build Process Automation

1. In **SAP Build**, navigate to **Control Tower > Destinations**.

    ![Destinations](ctower.png)

2. Choose **Open in BTP Cockpit**.

    > This Button is visible if you have a Process Automation Admin role.

    ![Open BTP Cockpit](openbtp.png)

    You will be navigated to the **Destinations** page of SAP Business Technology Platform.

3. Choose **Create Destination**.

    ![Create Destination](createdestbtp.png)

4. Add details by referring to the following and choose **Save**.

    > - For SAC destination, enter the details: refer to [SAC Base URL](https://help.sap.com/docs/SAP_ANALYTICS_CLOUD/14cac91febef464dbb1efce20e3f1613/3ccfab3348dd407db089accb66cff9a2.html) for URL of the destination.
    - For Success Factor destination, enter the details: refer to [Success Factor URL](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/d599f15995d348a1b45ba5603e2aba9b/af2b8d5437494b12be88fe374eba75b6.html)
    - For URL of the destination: refer to [documentation](https://help.sap.com/docs/build-process-automation/sap-build-process-automation/testing-actions) to add necessary additional properties.

    ![New Destination](successDest.png)

    ![New Destination](sacDest.png)

6. In SAP Build Process Automation, navigate to **Control Tower > Destinations > Add**.

    ![Destinations](ctower.png)

    ![Destinations](add.png)

7. Select the name of the destinations that you created in SAP BTP Cockpit and choose **OK**.

    ![New Destination](sacadd.png)

    ![New Destination](successadd.png)

    The Destinations are successfully added to SAP Build Process Automation tenant.

8. Go to the project to create the environment variables of type destination. 
   
9. Navigate to **Manage the project properties > Environment Variables > Create**.

    ![Environment Variable](settings.png)

    ![Environment Variable](envvar.png)

10. Create Environment Variables of type **Destination**.

    ![Environment Variable](createdest.png)

    ![Environment Variable](created.png)

    The destinations can be accessed successfully in your Business Process project.

### Release and deploy the project

1. Release the project.

    ![Release](release.png)

2. From the released version of the Business Process project in the Process Builder, choose **Deploy**.

    ![Start Deploy](deploy.png)

3. Choose an **Environment** and select **Deploy**.

    ![Choose environment](chooseEnv.png)

4. Choose **Deploy**.

    ![Deploy](00.png)

5. Define the variables by selecting the required destinations created previously and click **Deploy**.

    ![Define Variables](01.png)

   You have successfully released and deployed the process and it is ready to consume via APIs.
   
   ![Deployed version](02.png)


### Retrieve information from API trigger

Once you have successfully deployed the business process with an API trigger, you can view the API trigger in the Overview section under the tab Triggers.

![Trigger](trigger1.png)

1. To view the context of the workflow API, navigate to the Lobby by clicking on the SAP logo.

    ![Lobby](lobby2.png)

2. Choose **Control Tower** > **Environments**.

    ![Environments](env.png)

3. Choose the environment in which the project is deployed.

    ![Environment](public.png)

4. You can view the trigger in the **Unattended Triggers** tab. Click on **View**.

    ![View](view.png)

    ![View](view1.png)

---
