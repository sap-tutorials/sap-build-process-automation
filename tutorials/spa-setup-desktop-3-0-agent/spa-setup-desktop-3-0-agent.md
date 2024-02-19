---
author_name: Paulina Bujnicka
author_profile: https://github.com/pbujnicka
keywords: tutorial
auto_validation: true
time: 15
tags: [ tutorial>beginner, software-product>sap-business-technology-platform]
primary_tag: software-product>sap-build-process-automation
parser: v2
---

# Install and Set Up the Desktop Agent 3
<!-- description --> Install and set up the Desktop Agent 3 to run your automations


## Prerequisites
 - A Windows PC
 - If you are using a MAC, please install a VDI
 - Access to a [SAP BTP tenant with SAP Build Process Automation](spa-subscribe-booster)

## You will learn
  - How to install the Desktop Agent 3
  - How to register a tenant in the Desktop Agent 3

---

### About the Desktop Agent 3


The Desktop Agent 3 is an on-premise component of SAP Build Process Automation that is installed locally on user desktops. It executes automation projects that launch and run applications of various kinds, read information from screens, enter data, click options, and process data.

The very first time you launch the Desktop Agent 3 on your workstations, you will be prompted to log in. If you are unsure of your login details, please ask an administrator.


### Download the Desktop Agent 3

>**CAUTION**: If you are a **P user**, you will have to download the Desktop Agent 3 from the SAP Development Tools. Please choose option **Manually**.

[OPTION BEGIN [Automatically]]

Follow these steps once and your Desktop Agent 3 will be regularly updated to the latest version.

1. You can install the Desktop Agent 3 from SAP Build. Navigate to the **Control Tower** in **SAP Build** lobby, choose **Agent Update** under **Agent Configuration**. 

    <!-- border -->![Agent Update](agent3-031a.png)

    >The following steps are required if you have not set up your Secret ID yet. 

2. Select **Go to RBSC Portal**.

    <!-- border -->![RBSC Portal](agent3-031.png)

3. Select **Add User**.

    <!-- border -->![Add User](agent3-023.png)

    > Please make sure you assign the `ProcessAutomationAdmin` role when you subscribe to SAP Build Process Automation in your BTP account. If you do not do so you will not be able to add a user.

4. Set the name of the user and choose **Add user**.

    <!-- border -->![Set username](agent3-024.png)

5. Confirm with **OK** button.

    <!-- border -->![Create user](agent3-025.png)

6. To generate a new Secret ID, choose **Generate** and then select **OK**.

    > Note the full username as it will be needed later.

    <!-- border -->![Generate a new key](agent3-026.png)

7. When the Secret ID is generated, copy its value and click **OK**.

    <!-- border -->![Generate a new key](agent3-028.png)

8. Go back to SAP Build, and select the **Enter Secret ID** button.

    <!-- border -->![Enter Secret ID](agent3-029a.png)

9.  Set the Name and the Secret ID.
    
10. Choose **Confirm**.

    <!-- border -->![Set the secret id](agent3-030.png)

11. Choose the **Go to Download Page** button.

    <!-- border -->![Go to Download Page](agent3-032.png)

12. Download the file.

    <!-- border -->![Download file](agent3-004.png)

[OPTION END]

[OPTION BEGIN [Manually]]

You will download the setup program from the SAP Development Tools. It is provided in the form of an industry standard Windows MSI installer.

   
1. Download the **latest version**  of the [MSI file extension](https://tools.hana.ondemand.com/#cloud).

    > MSI version will be updated for every new release. Always download the latest version.

2. Scroll down to **SAP Process Automation: Desktop Agent 3 for Trial**.
   
3. Select the desktop agent available for your operating system.

    <!-- border -->![Desktop Agent 3 Trial download](tools.png)

[OPTION END]

### Install the Desktop Agent 3


When you install the Desktop Agent 3, it will automatically set up the SAP Build Process Automation web browser extension for Google Chrome and Edge.

>To prevent issues during the installation, please close all the Chrome or Edge tabs opened on your machine.

>The minimum version of the Desktop Agent supported by SAP Build Process Automation is **3.7.41**.

1. Open the downloaded file. Select **Next** to begin the installation process.

    <!-- border -->![Desktop Agent 3 Installation](agent3-002.png)

    > You can open the file with **administrator rights**, and install the service, only if your use case requires it. For example, using the agent in unattended mode in production. It is not required for following the tutorials.

2. Wait for the installation process to complete.

    <!-- border -->![Desktop Agent 3 Installation](agent3-034.png)

3. Once the installation is successfully completed, choose **Finish** and launch the Desktop Agent 3.

    >A Google Chrome extension and an Edge add-on are installed when you install the Desktop Agent but you have to enable them (at least the Google Chrome extension).

4. On Google Chrome select the manage extensions under Extensions.

    <!-- border -->![Manage extensions](agent3-005.png)

5. Enable SAP Build Process Automation extension.

    <!-- border -->![Enable extension](agent3-006.png)

6. Do the same for the Edge extension.

    <!-- border -->![Enable extension](agent3-006a.png)


### Register the Desktop Agent on your tenant


Once the installation steps of the SAP Build Process Automation setup wizard are completed, you need to register your agent and connect it to a SAP Build Process Automation tenant in order to execute automations.

> The Agent icon will be available on your System Tray, when the Desktop Agent 3 is installed.


[OPTION BEGIN [Automatically]]

1. After installation is completed and browser extension allowed, open the **Download Page** and choose **Refresh Page**.

2. Once the extension is enabled, you may register your agent to your tenant. Choose **Register Agent**.

    <!-- border -->![Register Agent](agent3-037.png)

3. The Agent is registered:
   
    <!-- border -->![Refresh Page](agent3-037a.png)

3. Once the process is completed, open the **Desktop Agent 3**.

    <!-- border -->![Desktop Agent 3 Installation](agent3-008.png)

4.  Confirm the tenant configuration.

    <!-- border -->![Configure Tenant](agent3-038.png)

    The tenant is active.

    <!-- border -->![Tenant Activate](agent3-039.png)

5. Once you completed the previous actions, log in to your tenant with your user name or e-mail and password.

    <!-- border -->![Activate Tenant](agent3-014.png)

6.  The Agent should be in **Idle** state, waiting to start a project. To check, go to **Control Tower**, and select **Agents**.

    <!-- border -->![Agent](agent3-013.png)

    <!-- border -->![Agent Idle](agent3-013a.png)


[OPTION END]

[OPTION BEGIN [Manually]]



1. Navigate to **SAP Build** lobby. Select **Control Tower > Agents**.
   
    <!-- border -->![Agents](agent3-013.png)

2. Select **Register new agent**.

    <!-- border -->![Register new agent](agent3-007a.png)  

3. In the **Register New Agent** window, select **Copy and Close**.

    <!-- border -->![Register agent](agent3-010.png)

4. Select the **Desktop Agent 3** icon.

    <!-- border -->![Desktop Agent 3 Installation](agent3-008.png)

5. Choose **Tenants**, select **Add Tenant** button.

6. In **Add Tenant** window, do the following:
   
    - In the **Name** field, enter a name for your Tenant,
    - In the **Domain** field paste the URL you copied previously,
    - Choose **Save**.

    <!-- border -->![Tenant data](agent3-011.png)

7. Select the tenant, choose the three dots and select **Activate**.

    <!-- border -->![Activate Tenant](agent3-012.png)

8.  Once you completed the previous actions, log in to your tenant with your user name or e-mail and password.

    <!-- border -->![Activate Tenant](agent3-014.png)

9.  The Agent should be in **Idle** state, waiting to start a project. To check, go to **Control Tower**, and select **Agents**.

    <!-- border -->![Activate Tenant](agent3-013a.png)

[OPTION END]


### Create an environment to add your agent


1. Navigate back to **Control Tower**. Select **Environments** under **Tenant Configuration**.
    
    <!-- border -->![Environment](agent3-020b.png)
   
2. Choose **Create Environment**.
   
3. In the **Create Environment** window do the following:

    - Give your environment a name
    - Select a color
    - You may enter a short description
    - Choose **Create**

    <!-- border -->![Create Environment](agent3-020.png)

4. Select the created environment to add your agent in it.

    <!-- border -->![Select environment](agent3-020a.png)

5. Select **Agent Management > Add Agent**.

6. In the **Add Agent** window, select your agent and choose **Add agent**.

    <!-- border -->![Agent Management Add](agent3-021.png)

7.  Your agent is now added and ready to run.

    <!-- border -->![Agent Management List](agent3-022.png)


---
