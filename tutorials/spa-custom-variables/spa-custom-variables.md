---
author_name: Paulina Bujnicka
author_profile: https://github.com/pbujnicka
keywords: tutorial
auto_validation: true
time: 60
tags: [ tutorial>beginner, software-product>sap-business-technology-platform]
primary_tag: software-product>sap-build-process-automation
parser: v2
---

# Use Custom Variables for the Global Process
<!-- description --> Add, modify and use custom variables in the process. 


## Prerequisites
  - [Subscribe to SAP Build Process Automation](spa-subscribe-booster)

## You will learn
  - How to create and use simple custom variables 


## Intro

By using custom variables, you can make any information available at the global level at any stage in the process. The outputs of any step that you add to your process can be consumed as inputs for the subsequent steps in a process. In addition, you can create custom variables on a project level that are not bound to a particular step.

---

### Process description

For your company, you need to design the process to submit innovation ideas by the employees. The process should by triggered by the employee who fills out the form. Then CFO would like it to be divided into CAPEX and OPEX categories, so two different councils can process the ideas and decide whether to provide an approval. If the innovation idea requires additional information, the council will send it back to the requester. In case the process will be approved by the council, the CFO will receive the case for the final approval. The requester must receive an email with the council or CFO decision.



### Create the project

1. In the SAP Build **Lobby**, select **Create** button.

    <!-- border -->![CGV](001.png)

2. Select **Build an Automated Process**.

    <!-- border -->![CGV](002a.png)

3. Select **Business Process**.

    <!-- border -->![CGV](003a.png)

4. Name the project: **Innovation Idea Process**, and confirm with **Create** button.

    <!-- border -->![CGV](004.png)

5. Create the process by providing the name: **Innovation Idea Global Process**.

    <!-- border -->![CGV](005.png)

### Create custom variables

1. To create global custom variables for the process, open the **Process Details**.

    <!-- border -->![CGV](006a.png)

2. Choose the **Variables** tab and select **Configure** for the **Custom Variables** section.

    <!-- border -->![CGV](006.png)

3. Configure the following variables:

    | **Name**    | **Type** | 
    | -------- | ------- |
    | rework | Boolean |
    | global cost | Number |
    | global description | String |
    | global idea name | String |
    | global council comments | String |
    | category | String |

4. To do that, select **Add Variable** button and add each variable. Last, select **Apply** to finish.
   
    <!-- border -->![CGV](007.png)
   
5. **Save** the process.

    <!-- border -->![CGV](007a.png)


### Add subprocess

> Due to product limitations, you need to add a subprocess. Please note that this step will not be necessary, once the custom variables will be available as output within the Trigger form.

1. Choose **+** below the **Trigger**.

    <!-- border -->![CGV](008.png)

2. Choose **Subprocess**. 

    <!-- border -->![CGV](009.png)

3. Choose **Blank Subprocess**.
   
    <!-- border -->![CGV](010.png)

4. Name it **Subprocess** and choose **Create**.

    <!-- border -->![CGV](011.png)

5. In the **General** section of the **Subprocess**, choose **Open Editor** to configure inputs and outputs.
   
    <!-- border -->![CGV](012.png)

6. Open the **Process Details**.

    <!-- border -->![CGV](012a.png)
 
7. Choose the **Variables** tab and select **Configure** for the **Process Inputs** section.

    <!-- border -->![CGV](013.png)

8. Select **Add Input** and add inputs below and select **Apply**:

    | **Name**    | **Type** | 
    | -------- | ------- | 
    | Name Subprocess    |  String   | 
    | Description Subprocess | String |
    | Number Subprocess | Number  | 
    | Category Subprocess | String | 

    <!-- border -->![CGV](014.png)

9. Choose **Configure** for the **Process Outputs** section.
   
    <!-- border -->![CGV](015a.png)
   
10. Select **Add Output** and add outputs below and select **Apply**:

    | **Name**    | **Type** | 
    | -------- | ------- | 
    | Name Subprocess    |  String   | 
    | Description Subprocess | String |
    | Number Subprocess | Number  | 
    | Category Subprocess | String | 

    <!-- border -->![CGV](015.png)

11. Go to the **End** and map the **Process Outputs** with the **Process Inputs** as in the screenshot below:
   
    <!-- border -->![CGV](099.png)

12. **Save** changes in the **Subprocess** and close the tab.


### Create the trigger form

1. In the **Innovation Idea Global Process**, choose **Add a Trigger** to create a trigger form for the requester. 

    <!-- border -->![CGV](016.png)

2. Choose **Submit a Form**. 

    <!-- border -->![CGV](016a.png)

3. Choose **Blank Form**.

    <!-- border -->![CGV](016b.png)

4. Name it **Innovation Idea Form**. Select **Create**.

    <!-- border -->![CGV](017.png)

5. Choose **Open Editor** of the form.
   
    <!-- border -->![CGV](098.png)

6. Add form input fields by clicking on the fields or using drag and drop option.

    | **Form Field**    | **Value** | **Option** |
    | -------- | ------- | ------- |
    | Headline 1  | Innovation Ideas Form    |  |
    | Paragraph | Please fill out the form with your innovation ideas. Once the form will be processed, you will be informed about the Council or CFO decision via email.     | |
    | Text    | Name of the Idea     |Required |
    | Text Area | Idea Description | Required |
    | Number | Estimated Cost of the Innovation | Required |
    | Dropdown  | Select the Category | Required |

    <!-- border -->![CGV](018.png)

7. For the drop-down field provide two values: `OPEX` and `CAPEX`. 
   
    <!-- border -->![CGV](018a.png)

8. **Save** the form and close the tab.


### Map subprocess inputs and outputs

1. In the **Innovation Idea Global Process**, select **Subprocess** and go to the **Inputs** section. Map the following from Trigger Form outputs:
     - **Category Subprocess** with **Select the Category**
     - **Description Subprocess** with **Idea Description**
     - **Name Subprocess** with **Name of the Idea**
     - **Number Subprocess** with **Estimated Cost of the Innovation**

    <!-- border -->![CGV](019.png)

2. Go to the **Outputs** section. **Set Custom Variables** by choosing them from the list:
     - **global cost**  
     - **global description**  
     - **global idea name**  
     - **category** 
   
    <!-- border -->![CGV](097.png)


3.  Map with **Subprocess** outputs:
     - **global cost** with **Number Subprocess**
     - **global description** with **Description Subprocess**
     - **global idea name** with **Name Subprocess**
     - **category** with **Category Subprocess**

    <!-- border -->![CGV](020.png)

4. **Save** the process.



### Create the approval forms and conditions

1. Choose **+** to create an approval form after **Subprocess**. 

    <!-- border -->![CGV](021a.png)

2. Choose **Approval**. 

    <!-- border -->![CGV](021.png)

3. Choose **Blank Approval**.
   
    <!-- border -->![CGV](022.png)

4. Name it `CAPEX Council Approval` and make sure to mark the checkbox **Based on a form** and select the trigger form from the list. Choose **Create**.

    <!-- border -->![CGV](023.png)

5. Select the **Approval Form** and choose **Open Editor**.

    <!-- border -->![CGV](023a.png)

6. Make changes in the form:
    - change the **Headline** to `CAPEX Approval for Innovation Idea`

    <!-- border -->![CGV](023b.png)

7. At the end of the form add additional input fields:

    | **Form Field**    | **Value** | **Option** |
    | -------- | ------- | ------- |
    | Paragraph | In case you need more information from the requester, please check the box below to send the form back to the requester and reject the approval.    | |
    | Checkbox    | Rework needed!     |  |
    | Text Area | Council Comment| Required |

    <!-- border -->![CGV](024.png)

8. **Save** the form, and close the tab.

9. In the **Innovation Idea Global Process**, choose `CAPEX Council Approval` form. In the **General** section:
    - Under **Subject** enter: `CAPEX Council Approval`
    - Under **Recipients** as **Users** enter: email of the `CAPEX` Council

    <!-- border -->![CGV](025.png)

10. In the **Inputs** section map the content with Custom Variables:
    - **Estimated Cost of the Innovation** with **global cost**
    - **Idea Description** with **global description**
    - **Name of the Idea** with **global idea name**
    - **Select the Category** with **category**
  
    <!-- border -->![CGV](026.png)


11. In the **Outputs** section, add the variables:
    - **rework**  
    - **global council comments** 

    <!-- border -->![CGV](027a.png)

12. Now map the custom variables with the process content from `CAPEX Council Approval` form:
    - **rework** with **Rework needed!** 
    - **global council comments** with **Council Comment**

    <!-- border -->![CGV](027.png)

13. Choose **+** above `CAPEX Council Approval` form to add a condition which will distribute the form to `CAPEX` or `OPEX` council. 

    <!-- border -->![CGV](028a.png)

14. Choose **Controls and Events**.

    <!-- border -->![CGV](028.png)

15. Choose **Condition**. 

    <!-- border -->![CGV](029.png)

16. Define and edit the condition:
    - Provide the **Step Name**: `Condition OPEX/CAPEX` 
    - Name the Branch: `If CAPEX`
    - Choose **Open Condition Editor**
  
    <!-- border -->![CGV](030.png)

17.   Define the **Branch Condition**:
    - For **Item** select custom variable **category**
    - For **Value** type **`CAPEX`**
    - Select **Apply** 
    - **Save** the process

    <!-- border -->![CGV](031.png)
    
18.  In the **Overview** tab, duplicate the `CAPEX Council Approval` form.

    <!-- border -->![CGV](032.png)

19. Name it `OPEX Council Approval`. Choose **Duplicate**.
   
    <!-- border -->![CGV](033.png)

20. Change the **Headline** to `OPEX Approval for Innovation Idea` and **Save**. Close the tab.

    <!-- border -->![CGV](034.png)

21. In the Process tab, move `CAPEX Council Approval` under **If CAPEX** Condition.

    <!-- border -->![CGV](035.png)

22. Choose **+** under **Default** branch of the condition 

    <!-- border -->![CGV](036.png)

23. Choose **Approval**.

    <!-- border -->![CGV](036a.png)

24. Choose the `OPEX Council Approval` form.

    <!-- border -->![CGV](036b.png)

25. In the **General** section of the `OPEX Council Approval` form:
    - Under **Subject** enter: `OPEX Council Approval`
    - Under **Recipients** as **Users** enter: email of the `OPEX` Council

    <!-- border -->![CGV](037.png)

26. In the **Inputs** section map the content with Custom Variables:
    - **Estimated Cost of the Innovation** with **global cost**
    - **Idea Description** with **global description**
    - **Name of the Idea** with **global idea name**
    - **Select the Category** with **category**

    <!-- border -->![CGV](038.png)

27. Select the **Outputs** tab and add the following variables:
    - **rework**
    - **global council comments** 

    <!-- border -->![CGV](039a.png)

28. Map the custom variables with the process content from **OPEX Council Approval** form:
    - **rework** with **Rework needed!** 
    - **global council comments** with **Council Comment**

    <!-- border -->![CGV](039.png)

29. **Save** the process.


### Create the CFO approval form

You will now create the **CFO Approval** form after the process would be approved by the `CAPEX` Council. 

1. Choose **+** below **Approve** option of `CAPEX Council Approval` form.

    <!-- border -->![CGV](040a.png)

2. Choose **Approval**.

    <!-- border -->![CGV](040b.png)
   
3. Choose **Blank Approval**.

    <!-- border -->![CGV](040c.png)

4. Name it **CFO Approval**, and make sure to mark the checkbox **Based on a form** and select the `CAPEX Council Approval` form from the list. Choose **Create**.
   
    <!-- border -->![CGV](040d.png)

5. Select the **CFO Approval** form and choose **Open Editor**.

    <!-- border -->![CGV](040e.png)

6.  Edit the form as follows:
   
    - Rename the **Headline** to **Final CFO Approval - Innovation Idea**
    - Remove the **Checkbox**: **Rework needed!**
    - Add at the end a **Paragraph**: **Please provide your final decision for the innovation idea:**
    - Add a **Text Area** named **CFO Decision**, and mark it as required 

7.  **Save** the form and close the tab.

    <!-- border -->![CGV](040f.png)

8.  In the **Innovation Idea Global Process**, select **CFO Approval** form and in **General** section enter:
    - Under **Subject** enter: **CFO Approval**
    - Under **Recipients** as **Users** enter: email of the CFO
  
    <!-- border -->![CGV](040g.png)

9.  In the **Inputs** section map the content with Custom Variables:

    - **Council Comment** with **global council comments**
    - **Estimated Cost of the Innovation** with **global cost**
    - **Idea Description** with **global description**
    - **Name of the Idea** with **global idea name**
    - **Select the Category** with **category**

10. **Save** the process.

    <!-- border -->![CGV](040h.png)

### Create the rework form and conditions

Now, you will create a form for a requester, in case the changes will be necessary. 

1. In the **Overview** tab, **duplicate** the **Innovation Idea Form**.

    <!-- border -->![CGV](040.png)

2. Name it **Innovation Idea Form - Rework**. Choose **Duplicate**.

    <!-- border -->![CGV](041.png)

3. Provide changes in the form. At the beginning:
    
    - Change the **Headline** to: **Innovation Ideas Form: Modify your request**
    - Change the **Paragraph** to: **Please make changes to the form based on the comments from the Council below:**
    - Add a **Text Area**, name it **Comments from the Approval Council**, and select **Read only** configuration
    - Add a **Headline 2**, name it **Data from your initial innovation form**
    - For the Inputs: Name of the Idea, Idea Description, Estimated Cost of the Innovation, Select the Category, select **Read only** configuration
  
    <!-- border -->![CGV](042aa.png)

    
4. Add additional inputs at the end:

    | **Form Field**    | **Value** | **Option** |
    | -------- | ------- | ------- |
    | Paragraph | Please modify your request below, based on the comments from the Council and your initial form. After that submit the form.   | |
    | Text    |  Name of the Idea - Edited     | Required |
    | Number | Estimated Cost of the Innovation - Edited | Required |
    | Text Area | Idea Description - Edited | Required |
    | Dropdown | Select the Category - Edited | Required |

    <!-- border -->![CGV](041a.png)

5. In the dropdown list, add `OPEX` and `CAPEX` as Data to display.

6. **Save** the form and close the tab.

    <!-- border -->![CGV](041b.png)
   
7.  In the **Innovation Idea Global Process**, choose **+** after `CAPEX Council Approval` **Reject** branch to add a condition.

    <!-- border -->![CGV](042a.png)

8.  Choose **Controls and Events**.
   
    <!-- border -->![CGV](042b.png)

9.  Choose **Condition**.
   
    <!-- border -->![CGV](042c.png)

10. Customize the **Condition**:
   
    - Step Name: **Rework**
    - Branch Name: **If Rework Required**

    <!-- border -->![CGV](043.png)
   
11.  Select **Open Condition Editor** and define the condition:
    
    - For **Item** select **rework** from Custom Variables
    - For **Value** choose **true**
    - select **Apply**

    <!-- border -->![CGV](044.png)

12.  Choose **+** after the condition branch **If Rework Required**.
    
    <!-- border -->![CGV](045a.png)

13.  Choose **Form**.
    
    <!-- border -->![CGV](045b.png)
    
14.  Add the form **Innovation Idea Form - Rework**.

    <!-- border -->![CGV](045.png)

15.  Select **Innovation Idea Form - Rework** form and in the **General** section define:
    - Under **Subject** enter: **Innovation Idea Form - Rework**
    - Under **Recipients** as **Users** select: **Process Started by**

    <!-- border -->![CGV](046.png)

16. Choose the **Inputs** tab and map the form **Inputs** with the custom variables:
    - **Comments from the Approval Council** with **global council comments**
    - **Estimated Cost of the Innovation** with **global cost**
    - **Idea Description** with **global description**
    - **Name of the Idea** with **global idea name**
    - **Select the Category** with **category**

    <!-- border -->![CGV](048.png)

17.  Set Custom Variables with the form **Outputs**:

    <!-- border -->![CGV](096.png)

18. Choose **+** after the **Default branch**. 

    <!-- border -->![CGV](047a.png)

19. Choose **Controls and Events**.

    <!-- border -->![CGV](047b.png)

20. Choose **Go to Step**.

    <!-- border -->![CGV](047c.png)

21. Choose **End** from the proposed steps.

    <!-- border -->![CGV](047d.png)

22. Choose **+** after **Innovation Idea Form - Rework**.

    <!-- border -->![CGV](049a.png)

23. Choose **Controls and Events**.

    <!-- border -->![CGV](049b.png)

24. Choose **Go to Step**.

    <!-- border -->![CGV](049c.png)

25. Choose `Condition OPEX/CAPEX` from the proposed steps.

    <!-- border -->![CGV](049d.png)

26. Choose **+** in the **Reject** branch of `OPEX Council Approval`.

    <!-- border -->![CGV](050a.png)

27. Choose **Controls and Events**. 

    <!-- border -->![CGV](050b.png)

28. Choose **Go to Step**.

    <!-- border -->![CGV](050c.png)
    
29. Choose **Rework Condition** from the proposed steps.

    <!-- border -->![CGV](050d.png)

30. Choose **+** in the **Approve** branch of `OPEX Council Approval`.

    <!-- border -->![CGV](050e.png)

31. Choose **Controls and Events**. 

    <!-- border -->![CGV](050f.png)

32. Choose **Go to Step**.

    <!-- border -->![CGV](050g.png)
    
33. Choose **CFO Approval** form from the proposed steps.

    <!-- border -->![CGV](050h.png)


29. **Save** the process. 


### Add mail artifacts

1. After the **CFO Approval** form, under the **Approve** branch, select **+**.
   
    <!-- border -->![CGV](052a.png)   

2. Choose **Email**. 
   
    <!-- border -->![CGV](052b.png)   
   
3. Edit the Artifact details:
    - Change the **Step Name** to **Approval Email**
    - Under **Mail Header** as **To** select: **Process Started by** from the Process Content
    - Under **Mail Header** as **Subject** enter: **Innovation Idea was approved**

4. Select **Open Mail Body Editor**. 
    
    <!-- border -->![CGV](052.png)    
   
5. In the **Edit Mail Body** window, enter the following body:

    - Enter: **Dear**
    - Select **Process Started by** from the the Process Metadata 
    - Enter: **Thank you for your idea. We have carefully evaluated it.**
    - Enter: **The CFO decision is to proceed with the idea.**
    - Enter: **Please find the CFO's comment below:**
    - Select **CFO Decision** from the CFO Approval form

6. Select **Apply**.

    <!-- border -->![CGV](053.png)    

    Now, you will add in the same way the rejection email.

7. After the **CFO Approval** form, under the **Reject** branch, select **+** and **Email**. Edit the Artifact details:
    - Change the **Step Name** to **Rejection Email**
    - Under **Mail Header** as **To** select: **Process Started by** from the Process Content
    - Under **Mail Header** as **Subject** enter: **Innovation Idea was rejected**
  
8.  Select **Open Mail Body Editor**.

    <!-- border -->![CGV](055.png)   
   
9.  In the **Edit Mail Body** window, do the following:
   
    - Enter: **Dear**
    - Select **Process Started by** from the Process Metadata
    - Enter: **Thank you for your idea. We have carefully evaluated it.**
    - Enter: **The CFO decision is to not proceed with the idea.**
    - Enter: **Please find the CFO's comment below:**
    - Select **CFO Decision** from the CFO Approval form

10. Select **Apply**.

    <!-- border -->![CGV](054.png)    
    
11. Add CAPEX/OPEX rejection Email. Go to the condition **Rework**, after **default** add an email:
    - Change the **Step Name** to `Rejection email OPEX/CAPEX`
    - Under **Mail Header** as **To** select: **Process Started by** from the Process Content
    - Under **Mail Header** as **Subject** enter: **Innovation Idea was rejected**

12. Select **Open Mail Body Editor**.
  
    <!-- border -->![CGV](056.png)     

13. In the **Edit Mail Body** window, enter the following body:
    
    - Enter: **Dear** 
    - Select **Process Started by** from the Process Metadata
    - Enter: **Thank you for your idea. We have carefully evaluated it.**
    - Enter: **The Council decision is to not proceed with the idea.**
    - Enter: **Please find the Council's comment below:**
    - Select **Global council comments** from the Custom Variables
  
14. Select Apply.

    <!-- border -->![CGV](057.png)    

15. **Save** the process.

    

### Release and deploy the business process


1. To release the process, choose the **Release** button
   
    <!-- border -->![CGV](059.png)    

2. To deploy the process, choose **Deploy** button.
   
3. Choose an Environment and select **Deploy**.

    <!-- border -->![CGV](060.png)   


### Run the business process 

1. From the deployed version of your business process project in the **Overview** section, open the **Innovation Idea Global Process**.
   
       <!-- border -->![CGV](060a.png)  
   
2. Select the **Innovation Idea Form**. 
   
3. Choose the **Copy** icon aside the **Form Link**.

    <!-- border -->![CGV](061.png)   

4. Open the form pasting the **Form Link** in a browser window.

5. Fill in the form by providing values in the **Innovation Ideas Form**.

    Let's run the process as such:

    <!-- border -->![CGV](062.png)   

    After you choose the **Submit** button, you will be notified that the form has been successfully submitted.

6. The workflow has been triggered and the approval process has started. You can now work on the tasks and monitor the process.


### Work on the tasks

1. Navigate to the **Lobby** and open **My Inbox**.

    <!-- border -->![CGV](100.png)   

    > In this use case, forms will be received in the same inbox since the recipient configured is the same.

2. After opening the **My Inbox** application, you will see on the left-hand side all the tasks listed. Choose the `OPEX Council Approval` form, select **Rework needed!**, add a **Council Comment** and choose **Reject**.

    <!-- border -->![CGV](101.png) 

3. Once you have rejected the approval task, refresh the inbox again to get the **Innovation Idea Form - Rework**.
   
4. You can see the **Comments from the Approval Council** and the data you entered in the **Innovation Idea Form**.
   
5. Now modify your form with a new innovation idea, select `CAPEX` as category and choose **Submit**.
   
    <!-- border -->![CGV](102.png) 

6. Refresh your inbox. As you selected `CAPEX` as category when you filled out your Rework form, you will now receive the `CAPEX Council Approval` form.
   
7. Enter a **Council Comment** but this time choose **Approve**.

    <!-- border -->![CGV](103.png) 

8. Refresh the inbox again to receive the **CFO Approval** form.
   
9. Enter a **CFO decision** and choose **Approve**.
    
    <!-- border -->![CGV](104.png) 

10. You will receive the **Approval Mail** in your inbox. This completes the process.
 
    <!-- border -->![CGV](105.png) 


### Monitor the business process

1. To monitor all the running instances of the process, navigate to **Monitoring > Monitor > Process and Workflow Instances**.

       <!-- border -->![CGV](106.png) 
   
2. Under **Status**, select **Completed**.

    <!-- border -->![CGV](107.png) 

3. Select the **Innovation Idea Global Process** instance.

4. You may check the status of the **Logs** and **Context**. The instance has completed successfully.

    <!-- border -->![CGV](108.png) 
    
---
