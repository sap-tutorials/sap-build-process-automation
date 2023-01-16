---
author_name: Archana Shukla
author_profile: https://github.com/ArchanaShukla
title: Setup Environment
description: Create destination and environment variables for action configuration
keywords: tutorial
auto_validation: true
time: 10
tags: [ tutorial>beginner, software-product>sap-business-technology-platform]
primary_tag: software-product>sap-build-process-automation
parser: v2
---

## Setup Environment
To configure action in business process, you will need to create an environment variable to access the destination that is created in SAP Business Technology Platform. A destination is needed to connect to the S/4HANA system to execute the APIs. The destination-based environment variable will be used to configure the Action of the business process.

## You will learn
  - Create destination in SAP BTP Cockpit to connect to backend system
  - Add destination based environment variable in business process for action configuration


### Add Destination in SAP Build Process Automation

1. To add the destination in your BTP Cockpit, do the following:

    - [Download](S4HANACloud) the S4HANACloud destination file
    - Go to **Connectivity** >> **Destinations** in your **BTP Cockpit**
    - Click **Import Destination** and select the downloaded destination file.
    - Update the **URL**, **User** and the **Password** based on your **S4HANACloud** setup.
    - **Save** the changed

        ![](destination_01a.png)

        > Note that there is a property **sap.processautomation.enabled** added to the destination. The destinations which have this property set as true can be discovered and added in SAP Build Process Automation.

2. Set this destination, created in BTP cockpit, in SAP Build Process Automation. To do so:

    - Open **SAP Build** development workbench
    - Click **Settings**
    - Goto **Destinations** section, and click **New Destination**
    - From **Add Destination** pop-up, select *S4HANACloud* destination
    - Click **Add** to add a new destination in SAP Build Process Automation

        ![](destination_02.png)

    A new destination will be added

      ![](destination_03.png)

    > This destination will be associated with the environment variable while deploying the business process.


### Add Environment Variable to Access Destination

1. Click to go back to **Lobby** and open your business project.
    - From your project overview section,
        - click to open **Order Processing** process.
        - In the process builder, click to open **Project Properties** from top-right corner of the page

            ![](destination_04.png)

2. In the **Project Properties** pop-up, select **Environment Variables** and click **Create** to create an environment variable for this business processes.

      ![](destination_05.png)

3. Enter the following to create an environment variable:

    - **S4HANACloud** as **Identifier**
    - Any **Description** of your choice
    - **Destination** as variable type

      ![](destination_05a.png)

    - Click **Create**

4. Once the environment variable is created, **Close** the project properties pop-up.

    ![](destination_06.png)

You have successfully created and configured the destination to be accessed while configuring business process.
