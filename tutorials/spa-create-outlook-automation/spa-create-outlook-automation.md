---
parser: v2
author_name: Ramakrishnan Raghuraman
author_profile: https://github.com/r3ksk
auto_validation: true
time: 20
tags: [ tutorial>beginner, software-product>sap-business-technology-platform, tutorial>free-tier]
primary_tag: software-product>sap-build-process-automation
---

# Build Your First Automation Using Outlook SDK of SAP Build Process Automation
<!-- description --> In this tutorial, you will be developing a basic automation using Outlook SDK of SAP Build Process Automation. In the end, by using the activities in Outlook SDK, you will learn how to search outlook inbox or a specific email folder and download any attachments found in the email to a specific local folder.

## Prerequisites
- [Subscribe to SAP Build Process Automation](spa-subscribe-booster)
- [Install and Setup the Desktop Agent](spa-setup-desktop-3-0-agent)
- Basic understanding of SAP Process Automation. You may review the below missions:
    - [Build Your First Business Process with SAP Build Process Automation](mission.sap-process-automation)
    - [Boost your Business Process with Automation, Decision and Process Visibility](mission.sap-process-automation-boost)

## You will learn
  - How to use Outlook SDK of SAP Build Process Automation to search the given email

## Intro
SAP Build Process Automation has native integration to several Microsoft Office products including Outlook and Excel SDK. In this Tutorial, you will explore how to use Outlook SDK to your automations.


---

### About Outlook SDK in SAP Build Process Automation


The Outlook SDK in SAP Build Process Automation, is a collection of activities allowing you to create automations using Microsoft Outlook. It comes with a rich set of functionality. For example:

- Search an email
- Read an email
- Download attachments from an email to your local folder
- Reply to an email
- Administrative operations like move or copy email from one outlook folder to another and many more


### Create an automation project


1.  To create an automation project from **SAP Build** lobby, choose **Create**.

    <!-- border -->![Create an automation Project](01-CreateNewProject.png)

2. Select **Build an Automated Process**.

    <!-- border -->![Build an Automated Process](01-BuildAutomatedProcess.png)

3. You can get started with a **Business Process** and include automation within that.

    For this tutorial, please select **Task Automation** option.

    <!-- border -->![Task Automation](01-TaskAutomation.png)

4. In the **Create a Task Automation project** window, name the project: **Outlook Sample**.

5. Fill in the description as follows: **A demo to create outlook SDK integration using SAP Build Process Automation**.

    > Feel free to name your project and give a description as per your convenience.

    <!-- border -->![Name your project appropriately](02-CreateAutomationProject.png)

6.  Subsequently it will ask you to select your desktop agent. You can pick your active, preferably latest desktop agent version.

    > By the time you follow these scripts, newer Desktop agent versions may have been introduced. Install the latest version of desktop components and select the latest version of agent in this step.

    <!-- border -->![Link to your active desktop agent version](03-SelectAgentVersion.png)

7.  A dialog box is displayed to create a new automation. You can give a name to your automation, for example `searchInOutlook`. You can follow your own naming convention and name for your automation.

    <!-- border -->![Add an automation to your project](04-CreateNewAutomation.png)

    If you had taken the route of creating a new business process project, you can add a new automation by following the given menu options.

    <!-- border -->![Add a new automation to case of business process project](05-AddNewAutomationToTheProject.png)

    A new tab will open and display an empty automation for you to get started.

8.  It adds mandatory core dependencies as part of automation addition to your project.

    <!-- border -->![Core SDK and Excel SDK are standard core dependencies added](06-CoreDependencies.png)

9.  Once an empty project is created, you need to include Outlook SDK dependency to this project. Locate the settings wheel icon in your project.

    <!-- border -->![Locate the settings Icon in your projects](07-SettingsIcon.png)

10. From the dependency section, locate Outlook SDK and include it as a dependency to your project. At the time of this tutorial creation, Outlook SDK `Version 1.32.41` was used.

    > Always update Outlook SDK to the latest version.

    <!-- border -->![Add Outlook SDK to your project](08-AddOutlookSDK.png)

    At this point, you are ready to work with Outlook SDK.


### Search using Outlook SDK


1.  From the **Tools** panel on the right side, search for the activity **Open Outlook Instance**.

2.  Drag and drop it into your automation flow.

    <!-- border -->![Drag Open Outlook Instance on to your automation](10-AddOpenOutlookInstance.png)

3.  Your task will be to do a simple folder search. Locate **Search Email** activity and add it to the flow.

    <!-- border -->![Add Search Email Activity to the automation](11-AddSearchEmailActivity.png)

4.  Select the newly added activity and **Create Custom Data** as search criteria under **Parameters** section.

    <!-- border -->![Add a custom search criteria](12-SearchEmailCustomCriteria.png)

5.  Provide a folder name and a `storeName` as per the input form. Here `storeName` refers to the email inbox, where you wanted the SDK to search.
    - `folderName` : it is an optional input. You need to provide one if you wanted automation to search a specific outlook folder
    - `storeName` : You may have additional mailbox configured within your outlook application. This field could be handy to search specific folder in your inbox. If you wanted to search the default inbox, you can leave the `storeName` empty.


    | Name         | Value                     | Example
    | :------------| :------------------------ | :---------------------
    | `folderName` | Outlook sub folder name | Invoices/ToCreate
    | `storeName`  | Email id               | mymail@bestrunsap.com

    <!-- border -->![Give your search criteria](13-EnterCustomSearchCriteria.png)

    > Review the option `SearchCriterionList`. You can include additional search criteria like emails with specific subject or from specific sender. You can refer to the [documentation](https://help.sap.com/doc/e57d7b179db649e6b5f2d26d9894f9d9/Cloud/en-US/datatypes/emailSearchCriterion.html) for additional information

6.  Add **Get Emails Number (Context)** activity to the flow. The previous step creates a context which is what you are going to use in the next steps.

    <!-- border -->![Add Get Email In Context Activity](14-AddGetEmailsInContext.png)

7.  As this is your first automation using Outlook SDK, you can do a simple check to find out if there is a result in the search. For example, you can find out how many emails are present in that outlook folder. For this, add a **Log Message** activity.

    <!-- border -->![Add Log Message](15-LogTotalEmailsInSearchResult.png)

8.  If you wanted, you can include a custom message using the expression editor.

    <!-- border -->![Open Expression Editor](16-OpenExpressionEditor.png)

9.  Add a custom message to log the total emails in your search results.

    <!-- border -->![Add A Custom Log Message](17-LogTotalEmailsAsCustomMessage.png)

10. Add **Close Outlook Instance** and **Release Outlook Instance** to your flow. This is always required with an **Open Outlook Instance** call to release resources used by you.

    <!-- border -->![Close and Release Outlook Instance](18-ReleaseOutlookInstance.png)

11. Save the project, test run the project, you should see your expected result.

    <!-- border -->![Test & Validate Result](19-SearchResultInTest.png)

    > Review the resources:
    >    
    - Microsoft Outlook Best Practices from the SAP Build Process Automation [documentation](https://help.sap.com/docs/IRPA/8e71b41b9ea043c8bccee01a10d6ba72/5a48c81502db40b08e4aac866e04592a.html)
    >- Outlook Email Best Practices Automation from the [SAP Build Process Automation Store](https://irpa.store.sap.com/#/package/a4c61c62-356e-4165-bdcb-bef08e236cf5)
