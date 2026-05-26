---
author_name: Rebecca Yang
author_profile: 
keywords: tutorial
auto_validation: true
time: 20
tags: [ tutorial>beginner, software-product>joule, tutorial>license]
primary_tag: software-product>joule
parser: v2
---


# Use Joule Studio to Create an Assistant to Monitor Supplier Risk

<!-- description -->Use Joule Studio to create and test an Intelligent Procurement Assistant for Spend Management.

## Prerequisites

- Access to Joule Work and Joule Studio in the Agent Lab at SAPPHIRE
- You have been provided with the logon information

## You will learn

- How to use intent-based development to create AI solutions.
- How SAP Domain Models and other resources are levergaed to contextualize the generated solution

## Intro

>**IMPORTANT**
>
>**Welcome to the Agent lab SAPPHIRE 2026!**
>
>You are working with a pre-release version of the Joule Studio. This gives you an early look at our upcoming capabilities. Please keep the following in mind:
>
> - Features are subject to change: The user interface (UI), terminology, and functionalities you see in this lab may differ from the final generally available product (GA).
> - For Educational use only: This environment is designed for learning and experimentation, not for production use.
> - Potential instability: As a preview version, you may encounter occasional instability or minor bugs. The exercises are designed to work with the current state of the platform. If you get stuck, please notify a session instructor.

Using Joule Studio’s intent‑based development, you can create an intelligent agent that continuously monitors supplier performance across critical KPIs in real time. The agent detects early warning patterns, explains the root causes of supplier risk, and proactively recommends pre‑qualified alternative suppliers within the same category. By generating executive‑ready summaries backed by supporting data, it enables teams to address performance issues before they disrupt production while significantly reducing time spent on manual supplier research and reporting.

### Get Started

1. Open **Joule Work** and select the **Develop +** area.

    <!-- border -->
    ![Click + to open the new solution dialog](010-create-solution.png)

2. On the **Agent** tile, choose **Create**.

3. Leave the selected **New Solution** unchanged, and fill in the agent details:

    ```COPY
        Supplier Performance Assistant
    ```

    Intent Statement:

    ```COPY
       Create an AI agent that monitors supplier performance, identifies at-risk suppliers, 
       and recommends approved alternative suppliers using simulated procurement data.
    ```

    Select **Quick create**.

    <!-- border -->
    ![Enter agent name and intent statement](030-define-solution-details.png)

4. Choose **OK**.

### Intent

1. This is where the tool tries to understand your intentions. The tool will attempt to understand your prompt and will likely ask you clarifying questions if you have not chosen quick-create as recommended above. Once it decides it understands enough, it will map the challenge to SAP's Reference Business Architecture and performs a fit-gap analysis. It has access to SAP Knowledge Graph, SAP LeanIX, and SAP Domain Models to help it create the intent document. Intent fit indicates how closely the proposed solution corresponds to your requirement.

   <!-- border -->
   ![intent-tools](040-Intent-tools.png)

    > Answer the questions set by the tool. The questions that the tool asks cannot be predicted, so you have to use your judgement. Bear in mind that some landscapes such as S/4HANA or Success Factors as backends so tailor your responses accordingly. The more complex you make your scenario, the longer it will take to generate and test the solution.

2. Once the intent document is created, proceed to the next phase, which is requirement generation. This might happen automatically if you have selected quick-create at the start. If processesing is waiting for your input to proceed, enter **Create Requirement** or similar.

3. While the requirements are being generated, you can explore the intent on the **Idea Board**.

    <!-- border -->
    ![intent-tools](040-Intent-ready.png)

### Requirements

When the requirement is ready, you have the opprotunity to review and refine it. For this tutorial, you will accept suggested product requirement document without changes. To progress to the next phase, you need to transform the PRD into a technical specification.

Depending on your role in your company, you might be finished at this point and make the PRD available to a different team to take further. However, in this tutorial, you are taking the project forward with the generation of a technical specification. Similar to the previous step, this might happen automatically if you have selected quick-create at the start.

At this stage, you can see the your PDR similar to the one below in markdown format.
If you need to update it manually, you can just proceed clicking on the text in the view or by editing the files in the dedicated code tab.

<!-- border -->
![Technical  overview](060-prd-ready.png)

### Specification

When the specification is complete you could pass it on to another team to do the implementation. However, here you are going to get the tool to implement the agent. This might happen automatically if you have selected quick-create at the start.

<!-- border -->
![Spec creation](070-create-spec.png)

While the solution is being generated, you can explore the specification in the **Code**** tab. You'll find it as **specification/specification.md**

<!-- border -->
![Spec ready](070-spec-ready.png)

If processesing is waiting for your input, enter **Implement the Solution**.

   The tool will work through the tasks defined in the specification. When it is finished, it will update the status in the specification to show the tasks have been done.

### Solution

1. Wait until the implementation is finished successfully.

    ![Solution code](085-solution-ready.png)

2. You can then explore the code if you need to.

    ![Solution code](085-solution-code.png)

3. Go to the **view** tab of your solution and try your agent. What you can do will depend on what has been implemented.

For the Agent Lab at SAPPHIRE, you will not be deploying your agent. However, the code that has been generated follows SAP best practices and would be deployable to the runtime.
