---
license needed: BDC Core, AI units, Joule Studio, SAC composable
author_name: Fenja Schulz, Anirban Banerjee
author_profile: https://github.tools.sap/D060476
---

# FAQ for BDC Scenario: Data Product Creation Agent and Insight Generation Agent

<!-- description -->Use Joule Studio to Create an AI Assistant for Financial Analysis on Overdue Receivables.

## Prerequisites

- Design time: MCP server unified-bdc-mcp is installed and the corresponding skill data-product-generation is executed
- Predeployed agent in a separate tab

## The scenario
- link to Git
- how the two play together

## Data Product Creation Agent
- Role during design time
- role during runtime
- questions from the chat
- architecture diagram

**Q: What is the Data Product Creation Agent?**  
**A:** The *Data Product Creation Agent* is an SAP **AI-powered assistant** that helps users of **SAP Business Data Cloud (BDC)** quickly create *data products* – curated datasets ready for analytics or AI. It can both **discover existing data products** and **generate new ones** (including combining multiple sources and performing transformations) based on a user’s **natural-language instructions**. In essence, it serves as a **“co-pilot”** for data engineers and analytics teams to streamline data preparation and **automate the technical work** of building data products.

**Q: What business problem does it solve?**  
**A:** The Data Product Creation Agent addresses the **time-consuming, manual effort** traditionally required to create integrated datasets. It **eliminates the need for writing complex data integration code or switching between multiple tools**, thereby reducing reliance on specialized IT resources. By making data product creation more **self-service and efficient**, it significantly **speeds up time-to-value** – allowing organizations to derive insights and build analytics faster with less manual handoff. 

**Q: How do users interact with the Data Product Creation Agent?**  
**A:** Users interact with the agent through a **conversational interface**. For example, within **SAP’s Joule** (the generative AI assistant in SAP’s platform), a user simply **types a request** describing the data product they need (e.g. *“Create a customer sales pipeline data product combining ERP and CRM data.”*). The agent then engages in an **interactive dialogue**, possibly asking clarifying questions or showing previews, and ultimately produces the requested data product – ready for use in **Business Data Cloud** and accessible to analytics tools or other AI agents. 

**Q: How does the Data Product Creation Agent work behind the scenes?**  
**A:** Behind the scenes, the agent employs **AI and metadata intelligence** to interpret the user’s business request. It uses SAP’s **Knowledge Graph** (which contains metadata about enterprise data sources and existing data products) to **identify relevant source data and existing products**. Then it automatically **proposes and builds the necessary join and transformation logic** to create a new data product if needed. The agent runs through an **“agent loop”** – iteratively refining the solution based on the user’s intent – and **persists the resulting data product** (with its transformation pipeline) in BDC. This means the final output is a properly defined data product, **registered in the Knowledge Graph** for others to discover and reuse across the SAP landscape. 

**Q: How much of the process is automated by AI, and what is the user’s role?**  
**A:** The Data Product Creation Agent automates **most of the technical steps** of data product creation. **The user’s role is to provide high-level guidance** (via natural language) and to validate or refine as needed – the agent does the heavy lifting by generating the data product definition and transformation logic automatically. This high degree of automation means **little to no coding is required** from the user. However, **human-in-the-loop control** is still possible: for complex scenarios, users can adjust or review the generated data product (for example, through a design interface like Data Product Studio) before finalizing or deploying it.

**Q: How does it integrate with SAP’s data and analytics landscape?**  
**A:** The agent is **natively embedded in SAP’s Business Data Cloud**, which is part of SAP’s **Business AI platform** for enterprise data. It leverages **BDC’s Knowledge Graph** and data catalog, so any data product it creates is automatically part of your **governed data fabric** and can be consumed by **SAP Analytics Cloud** or **other BDC AI agents** (including **SAP Joule** and domain-specific agents). It works with data sources and **primary data products** from across SAP systems (e.g. SAP S/4HANA, SAP SuccessFactors, SAP Ariba, etc.), and potentially other integrated sources, to produce **new derived data products** that can bridge multiple **data silos** in one go **without manual integration effort**. 

**Q: Does the Data Product Creation Agent ensure data quality and governance?**  
**A:** Yes. Since it operates within **SAP’s Business Data Cloud**, the agent adheres to the same **data governance, security, and quality frameworks** that govern all data products. The new data products it creates are fully tracked and **documented in the Knowledge Graph**, providing lineage and metadata for transparency. Additionally, organizations can incorporate a **review step** (human-in-the-loop) using Data Product Studio or other governance tools to ensure the generated data product meets quality standards before it’s officially activated. The agent essentially accelerates creation **without compromising on governance or trust**, since it builds on top of **managed, authorized data sources**. 

**Q: Who is the Data Product Creation Agent intended for?**  
**A:** This agent is designed for **technical and data-savvy professionals** who work with enterprise data and need to accelerate data preparation for analytics or AI. Typical users include **data engineers, data architects, solution designers, and advanced business analysts** who use SAP’s Business Data Cloud as their data foundation. By simplifying the process of assembling and preparing data, the agent helps these users (and the organizations they support) be more **productive and innovative** – focusing on *business insights and solutions* rather than on manual data-wrangling tasks.


## Insight Generation Agent
- Role during design time
- role during runtime
- questions from the chat


