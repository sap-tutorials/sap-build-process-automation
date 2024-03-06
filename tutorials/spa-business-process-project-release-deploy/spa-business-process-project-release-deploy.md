---
parser: v2
author_name: Céline Audin
author_profile: https://github.com/celineaudinsap
auto_validation: true
time: 5
tags: [ tutorial>beginner, software-product>sap-business-technology-platform, tutorial>free-tier]
primary_tag: software-product>sap-build-process-automation
---

# Release, Deploy and Run a Business Process Project
<!-- description --> Release, deploy and run a business process project to run and monitor your project

## Prerequisites
- A Business Process Project saved and with no errors.

## You will learn
  - How to release, deploy and run a process

---

### Release business process project
Before you run the process, ensure that the process is saved and that there are no errors showing in the Design Console. To run the process, you must first release and then deploy the Business Process project. Releasing a project creates a version or snapshot of the changes.

1. In the Process Builder, choose **Release**.

    <!-- border -->![Release](01_Process_final.png)

2. Add a **Version Comment** if needed and choose **Release**.

    <!-- border -->![Release first](02_Release_first_version.png)

3. If it is an additional version, choose the type of version, add a **Version Comment** if needed and choose **Release**.

    <!-- border -->![Release new](02_Release_second_version.png)

    > Every time you release, a new version will be created. Versions are incremented automatically based on how you want to store the changes in the repository (that is as major or minor updates or as a patch). Versions use an x.y.z format where x is a major version number, y is minor, and z is the patch number. For instance, if you are releasing your process project for the first time, then the version will start with 1.0.0. The next time you release there will be options to choose from – that is, if the new version is a major, minor, or patch update; version numbers will be automatically updated.

4. The project released successfully and is ready to be deployed.

    > If needed, you can refer to the [Documentation](https://help.sap.com/docs/build-process-automation/sap-build-process-automation/releasing-project?version=Cloud).

    <!-- border -->![Released](03_Released_first_version.png)


### Deploy the released process

    You can deploy Business Process projects from each released version of the project in the Process Builder or through the Lobby. Deploying the project makes it available for others to use it. Bare in mind that you can only deploy a released version of the project.

1. From the released version of the Business Process project in the Process Builder, choose **Deploy**.

    <!-- border -->![Start Deploy](01_Released_first_version.png)

2. Choose an **Environment** and select **Deploy**.

    <!-- border -->![Deploy](environment.png)

    The Deploy action will take a couple of seconds/minutes, depending upon how big your project is and how many different skills it has. Any errors during the deployment will be shown in the Design Console.

3. The project deployed successfully and is now ready for running and monitoring.

    > If needed, you can refer to the [Documentation](https://help.sap.com/docs/build-process-automation/sap-build-process-automation/deploy-project?version=Cloud).

    <!-- border -->![Deployed](03_Deployed_first_version.png)

    Once the deployment is successful, you will see a changed status. You can also see all your deployed and/or released project versions from the project status list next to the project name.

    <!-- border -->![Deploy successful](01_Deployed_process.png)

    > You cannot edit released or deployed projects. To continue working on your project, you need to select the Editable option from the list of released versions.

### Run the business process


   Now that you have successfully deployed your project, it is time to run the process and see the results.

1. From the deployed version of the Business Process project in the Process Builder, open the process **Get Invoice Details**.

    <!-- border -->![Run](01_Open_Order_Processing.png)

2. Select **Invoice Request Form**.

3. Choose the **Copy** icon aside the **Form Link** in the **Invoice Request Form**.

    <!-- border -->![Run copy the form link](02_Process_Start.png)

4. Open the Form pasting the **Form Link** in a browser window.

    <!-- border -->![Run open the form](03_Order_Processing_Form.png)

5. Fill the **Invoice Request Form** and choose **Submit**.

    > Do not enter any random value or else the Automation will not give any results.

    <!-- border -->![Run open the form](Form_Inputs.png)

6. The process is triggered. You can now work on the tasks and monitor the process.

    <!-- border -->![Run form successfully submitted](Run_inputs_2.png)


---
