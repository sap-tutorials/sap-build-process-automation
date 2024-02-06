---
author_name: Aviral Agarwal
author_profile: https://github.com/aviral-agarwal-sap
keywords: tutorial
auto_validation: true
time: 10
tags: [ tutorial>beginner, software-product>sap-business-technology-platform, tutorial>free-tier]
primary_tag: software-product>sap-build-process-automation
parser: v2
---

# Setup Environment
<!-- description --> Create destination in BTP cockpit and set it in SAP Build Process Automation

## You will learn
  - to add destination in SAP BTP Cockpit to connect to backend system
  - to set destination in SAP Build Process Automation


## Intro
To configure action in business process, you will need to create an environment variable to access the destination that is created in SAP Business Technology Platform. A destination is needed to connect to the S/4HANA system to execute the APIs. The destination-based environment variable will be used to configure the action of the business process.


### Add destination in SAP BTP cockpit

1. To add the destination in your BTP Cockpit, do the following:

    - [Download](https://www.sap.com/registration/trial.f47300f6-63b8-4f22-b189-dbadd3c903d6.html?id=0050000000420272023) the S4 Business Partner destination file.
    - Go to **Connectivity** >> **Destinations** in your **BTP Cockpit**.
    - Click **Import Destination** and select the downloaded destination file.
    - Update the **URL**, **User** and the **Password** based on your **S4HANACloud** setup.
    - **Save** the changes.

    <!-- border -->![Destination](001.png)

    <!-- border -->![Destination](002.png)

    > Note that there is a property **sap.processautomation.enabled** added to the destination. The destinations which have this property set as true can be discovered and added in SAP Build Process Automation.


### Set destination in SAP Build Process Automation

1. Now that your destination is created in SAP BTP cockpit, you may set it in SAP Build Process Automation. To do so:

    - Open **SAP Build** development workbench.
    - Click **Control Tower > Destinations**.
  
    <!-- border -->![Destination](002a.png)

    - Click **New Destination**.
    - From **Add Destination** pop-up, select `S4_Business_Partner` destination.
    - Click **Add** to add a new destination in SAP Build Process Automation.

    <!-- border -->![Destination](003.png)

    A new destination will be added.

    <!-- border -->![Destination](004.png)

    > This destination will then be associated with the environment variable while deploying the business process.

    You have successfully created and configured the destination to be accessed while configuring business process.
