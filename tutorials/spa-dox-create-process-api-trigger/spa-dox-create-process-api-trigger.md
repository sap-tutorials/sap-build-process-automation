---
parser: v2
author_name: Paulina Bujnicka
author_profile: https://github.com/pbujnicka
auto_validation: true
time: 20
tags: [ tutorial>intermediate, software-product>sap-business-technology-platform, tutorial>free-tier]
primary_tag: software-product>sap-build-process-automation
---

# Create an API Trigger for the Business Process
<!-- description --> Trigger business process from other services.

## Prerequisites
 - Complete [Automate to Access Documents from Document Management Repository](spa-dox-create-process-api-automation)

## You will learn
  - How to trigger business process through an API

---

### Configure Inputs for API Trigger


Once you have completed the [Automate to Access Documents from Document Management Repository](spa-dox-create-process-api-automation), your process looks like this:

<!-- border -->![Proces](001.png)

1. From the **Editable** version of the **Invoice Approval** project, choose the three dots of the **Invoice Request Form** and **Remove** to delete the form.

    <!-- border -->![Delete Form](0022.png)

2. Click on the **Canvas** in the background.

    <!-- border -->![Canvas](2001.png)

3. Choose **Configure Inputs** in **Inputs** to configure inputs.

    <!-- border -->![Inputs](033.png)

3. In **Configure Process Inputs** window choose **Add Input** to add parameters.

    <!-- border -->![Add Inputs](1001.png)

4. Configure three inputs. Enter the names and choose types.

    |  **Name**    | **Type**
    |  :------------- | :-------------
    |  `fileName`       | string
    |  `folderName`     | string
    |  `employeeName`   | string

    **Apply** changes.

    <!-- border -->![Add Inputs](1002.png)


### Binding Input and Output Parameters


1. Choose **Download Document DMS** automation.

    <!-- border -->![DMS Automation](044.png)

    - Configure **Inputs** section. Select the text box and map corresponding content.

    |  **Form Input Fields**    | **Process Content Entry**
    |  :------------- | :-------------
    |  `folderName`    | `folderName`
    |  `uploadedFileName`     | `fileName`

    <!-- border -->![Configure Inputs](055.png)

2. Choose **Extract Invoice Data** automation.

    <!-- border -->![Invoice Data](066a.png)

    - Configure **Inputs** section. Select the text box and map corresponding content.

    |  **Form Input Fields**    | **Process Content Entry**
    |  :------------- | :-------------
    |  `FilePath`    | `outputPath`

    <!-- border -->![Configure Inputs 2](077.png)

3. Select **Invoice Approval Form**.

    <!-- border -->![Invoice Approval Form](099a.png)

    - Configure **General** section. Select the text box and map corresponding content.

    |  **Form General Fields**    | **Process Content Entry**
    |  :------------- | :-------------
    |  Recipients > Users  | `eMail`


    <!-- border -->![Configure General ](111.png)

    - Configure **Inputs** section. Select the text box and map corresponding content.

    |  **Form Inputs Fields**    | **Process Content Entry**
    |  :------------- | :-------------
    |  Employee Name  | `employeeName`

    <!-- border -->![Configure Inputs 4 ](112a.png)

4. **Save** your work.






---
