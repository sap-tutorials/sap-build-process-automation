---
parser: v2
author_name: Céline Audin
author_profile: https://github.com/celineaudinsap
auto_validation: true
time: 10
tags: [ tutorial>intermediate, software-product>sap-business-technology-platform, tutorial>free-tier]
primary_tag: software-product>sap-build-process-automation
---

# Release and Deploy the Process to Trigger Technical Events
<!-- description --> Release and deploy the Process to retrieve details on an excel spreadsheet

## Prerequisites
- [Subscribe to SAP Build Process Automation](spa-subscribe-booster)
- Complete [Capture and Declare an Application to Trigger Technical Events](spa-technical-events-capture-declare)
- Complete [Create an Automation to Trigger Technical Events](spa-technical-events-automation-user-task)
- [Install and Setup the Desktop Agent](spa-setup-desktop-3-0-agent)
- [Agent Management Settings to Execute the Process with an Automation](spa-run-agent-settings)

## You will learn
  - How to release and deploy the business process project

---

### Create the project launcher


Since the automation requires human intervention, with a popup dialog, the automation has to be executed in attended mode. This means that the user must be present for the automation to run.

You will trigger the automation using the project launcher.

>The project launcher allows you to launch your automation in attended mode in two different ways:

> - You can launch your automations manually in attended mode from the agent using the Launch manually from the agent section.
- You can configure events to trigger and launch your automations automatically using the Launch automatically by events section.

In this tutorial, you will manually launch your automation from the agent by adding it in the Launch manually from the agent section of the project launcher.

1. In **Build Process Automation** overview page, choose **Create** and **Project Launcher**.

    <!-- border -->![Project Launcher](84-project-launcher.png)

2. In the **Create Project Launcher** window, name the project **Get Order Details** and choose **Create**.

    <!-- border -->![Project Launcher](85-project-launcher.png)

    A project launcher editor opens in the main panel of **Build Process Automation**. On the **Project Launcher details** right-hand side panel, you can see the automations available in your project.

3. In the **Project Launcher Details**, drag the automation and drop it in the **Launch manually from agent** section of the project launcher.

4. Choose **Save**.

    <!-- border -->![Project Launcher](86-project-launcher.png)


### Release and deploy the business process project


Now you may release and deploy it in attended mode. You need to select this trigger type since the user is asked to perform an action, which is to approve or decline retrieving the order details in an excel spreadsheet.

1. In the Process Builder, choose **Release**.

    <!-- border -->![Release Automation](79-release.png)

2. Add a **Version Comment** if needed and choose **Release**.

    <!-- border -->![Release Project](80-release-project.png)

    > ### What's going on?
    > Every time you release, a new version will be created. Versions are incremented automatically based on how you want to store the changes in the repository (that is as major or minor updates or as a patch). Versions use an x.y.z format where x is a major version number, y is minor, and z is the patch number. For instance, if you are releasing your process project for the first time, then the version will start with 1.0.0. The next time you release there will be options to choose from – that is, if the new version is a major, minor, or patch update; version numbers will be automatically updated.

3. The project released successfully and is ready to be deployed.

    <!-- border -->![Released Project](81-released-project.png)

    You can deploy Business Process projects from each released version of the project in the Process Builder or through the Lobby. Deploying the project makes it available for others to use it. Bare in mind that you can only deploy a released version of the project.

4. From the released version of the Business Process project in the Process Builder, choose **Deploy**.
   
5. Select an **Environment** and choose **Deploy**.

    <!-- border -->![Deploy Project](82-deploy-project.png)

    To Deploy will take a couple of seconds/minutes depending upon how big your project is and how many different skills it has. Any errors during the deployment will be shown in the Design Console.

6. The project deployed successfully and is now ready to be executed.

    <!-- border -->![Deployed Project](87-deployed-project.png)

    > You cannot edit released or deployed projects. To continue working on your project, you need to select the Editable option from the list of released versions.

 ### Create an attended trigger 

1. Navigate back to **SAP Build > Control Tower > Environments**.
   
    <!-- border -->![Trigger](87a.png)

2. Select your environment.
 
    <!-- border -->![Environment](87b.png)

3. Go to **Attended Triggers > Create Attended Trigger**.

    <!-- border -->![Project](87c.png)

4. In the **Create Attended Trigger** box, do the following:

    - Select **Get Order Details** project
    - Name the trigger `Attended_Trigger`
    - Enter the **Schedule** details

    <!-- border -->![Create attended trigger](83.png)

5. Choose **Distribution** tab and configure the **Distribution restriction policy** to **Agents matching attributes**.
   
6. Choose **+ Add** and set your attribute and value.
   
7. Choose **Create**.

    <!-- border -->![Distribution](84.png)

8. Your Attended Trigger is created.

    <!-- border -->![Attended Trigger](85.png)

9. Go to your **Desktop Agent > Settings > Mode**  and make sure the agent is in attended mode. If not, activate the Attended Mode.

    <!-- border -->![Attended mode](86.png)

10. Choose **Projects**.
   
11.  Your project is ready to be launched in attended mode. Choose **Activate**. 

    <!-- border -->![Projects](88.png)

12. Choose **Start**.

    <!-- border -->![Start Project](89-start-project.png)

    > **CAUTION:** Please make sure your **Browse Orders** application is open.

---
