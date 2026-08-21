# CAIP Technical Workshop-Roadshow: Caldova Production Challenge

## Overview

>**Note:** This workshop is designed as a hands-on technical roadshow exercise. Participants should use the provided Caldova scenario, current-state details, reference architecture, and sandbox environment to complete the activities.

>**Note:** Teams should export their future-state architecture before starting rapid prototyping. The exported image will be used to generate deployment assets with GitHub Copilot.

This CAIP Technical Workshop-Roadshow helps participants solve a real-world pharmaceutical manufacturing transformation scenario for **Caldova**. Participants will use business envisioning, whiteboarding, future-state architecture design, Microsoft Fabric, Microsoft Foundry, and GitHub Copilot to create a rapid prototype that supports manufacturing capacity decisions, data modernization, and governed multi-agent AI.

## Learning Objectives

After completing this workshop, you will be able to:

- Understand Caldova's product launch challenge and the business drivers behind the transformation.
- Use whiteboarding to map business problems to a future-state technical architecture.
- Design a governed intelligence layer that supports trusted AI agents.
- Rapidly prototype deployment assets from a future-state architecture.
- Use GitHub Copilot in VS Code to generate ARM/Bicep templates and supporting deployment guidance.
- Explain how Microsoft Fabric, Fabric IQ, Microsoft Foundry, and multi-agent patterns can address Caldova's operational challenges.

## 1. Caldova Product Launch Challenge

### 1.1 Company Type and Situation

Caldova is a pharmaceutical company racing to launch an accelerated V2 / next-generation pharma product ahead of a competitor's scheduled release. The launch depends on supply chain, manufacturing, procurement, data, application, and compliance teams working from the same trusted context.

The immediate business pressure is a **7% capacity gap across three manufacturing plants**. Caldova needs to determine whether the gap can be closed internally and, if not, which pre-qualified contract manufacturing organizations can fast-track support in a **3-6 month window**.

Caldova also needs a multi-agent AI solution leveraging Microsoft IQ capabilities to recommend and take action on critical operational issues for the COO.

### 1.2 Technical Backdrop

Caldova's existing estate was not originally built for AI workloads:

- The supply chain planning application runs on a legacy system.
- The manufacturing database sits on an on-premises SQL Server estate.
- The broader infrastructure footprint runs on VMware.
- Data is siloed across IoT, supply chain, customer, production, supplier, and manufacturing quality systems.
- Each system has separate definitions, owners, access rules, and governance controls.

Because no single team can see the full picture, no AI agent can be trusted to act without a shared, governed intelligence layer.

### 1.3 Customer Overview

Caldova wants to turn AI from isolated experiments into a durable operating capability for regulated pharmaceutical manufacturing. The desired end state is one governed, context-rich intelligence layer that every agent can trust.

That layer should connect:

- Real-time and historical operational data
- Manufacturing knowledge
- Supplier intelligence
- Internal SOPs
- Escalation paths
- Trusted web context
- Identity, permissions, sensitivity, and compliance controls

## 2. Envisioning Session Using Whiteboarding to Solve Caldova Business Problem

### 2.1 Workshop Exercise

- **Exercise:** Envisioning Session Using Whiteboarding
- **Estimated Time:** 150 minutes team exercise + 15 minutes reporting
- **Team Size:** TBD

### 2.2 Strategic Mandate

**Cloud & AI-First Caldova Manufacturing Ops 2027** connects three transformation motions:

| Pillar | Objective |
|---|---|
| Modernize with Confidence | Migrate the legacy SQL Server estate to Azure SQL Managed Instance while retaining compatibility, availability, and compliance controls. |
| Amplify Your Intelligence | Build a semantic, context-rich intelligence layer with Fabric IQ so manufacturing data speaks the language of the business. |
| Ubiquitous Innovation | Enable teams to rapidly build and deploy governed multi-agent solutions in Microsoft Foundry. |

### 2.3 The Three Challenges

Your team must address the following three challenges. Document your approach, sequencing, risks, and mitigation plan.

#### Challenge 1: SQL Estate Migration to Azure SQL Managed Instance

You are the migration architect team for Caldova. The CTO has tasked you with designing a migration strategy to move the SQL Server estate from the London and Miami datacenters to Azure SQL Managed Instance ahead of the VMware exit and within the 16-week window.

**Migration Problem:**

- IT believes there are 10 databases, but audit logs show queries against unknown database names on LEGACY01.
- The estate must be fully inventoried and assessed before migration.
- 247 instances of deprecated SQL syntax must be remediated.
- EXTERNAL_ACCESS and UNSAFE CLR assemblies are not supported on Azure SQL Managed Instance.
- Production runs in an availability group between London and Miami.
- BatchManufacturingCore tolerates a maximum of 30 minutes of downtime.
- GxP records must stay in the UK region.

**Questions to Answer:**

- How will you inventory the full estate and assess migration readiness for Azure SQL Managed Instance?
- How will you categorize compatibility issues as blockers vs. warnings?
- What is your remediation plan for deprecated features and non-SAFE CLR assemblies?
- How will you test remediation without affecting production?
- What is your migration and cutover sequence?
- What is your rollback plan if cutover fails?

#### Challenge 2: Unified Data Intelligence Layer with Fabric IQ

You are part of the Caldova data engineering team. The CDO wants one governed, context-rich intelligence layer that every future AI agent can trust, built on Microsoft Fabric with Fabric IQ.

**Unification Problem:**

- Operational data is siloed across six systems: IoT/plant telemetry, supply chain planning, customer/demand, production/MES, supplier/ERP, and quality/LIMS.
- Each system defines concepts such as plant, batch, and capacity differently.
- Agents built directly against raw tables drift, duplicate logic, and cannot be audited.
- Identity, permissions, and sensitivity labels must be honored end-to-end.

**Questions to Answer:**

- How will you land the six sources into OneLake using mirroring, shortcuts, and pipelines without creating another copy-and-drift problem?
- How will you model the manufacturing ontology in Fabric IQ?
- How will agents reason over shared business concepts instead of raw tables?
- How will access controls, sensitivity labels, and auditability be preserved?

#### Challenge 3: Multi-Agent Solution for CMO Recommendation

You are the Caldova data science team. Leadership needs a defensible answer in days, not weeks: can the 7% capacity gap across the three plants be closed internally, and if not, which pre-qualified contract manufacturing organizations can fast-track support within the 3-6 month window?

**Recommendation Problem:**

- Internal headroom analysis requires real-time line, shift, and batch-schedule data from all three plants.
- CMO selection must weigh qualification status, GMP compliance history, available capacity, tech-transfer time, and cost.
- Data is spread across supplier/ERP, quality, and external sources.
- Every recommendation must carry a GxP-compliant audit trail.

**Questions to Answer:**

- How will you decompose the problem into agents?
- How will the orchestrator, current capacity analysis, contract manufacturer analysis, COO recommender, and compliance guardrail agents collaborate in Foundry?
- How does each agent ground reasoning in the Fabric IQ ontology?
- Why does grounding in shared business concepts matter for trust and reuse?

### 2.4 Current and Reference Architecture Activity

1. Open the current and reference architecture in your whiteboard.
2. Fill out the business envisioning sections based on the Caldova case study.
3. Identify business goals, technical constraints, and measurable success criteria.
4. Drag and drop the relevant components from the reference architecture.
5. Build a future-state architecture that addresses all three challenges.
6. Export the future-state architecture as an image.

>**Note:** Save the exported future-state architecture image. You will upload it during the rapid prototyping exercise and use it with GitHub Copilot in VS Code.

### 2.5 Database Inventory

| Database | Size | Purpose | Special Features |
|---|---:|---|---|
| BatchManufacturingCore | 8 TB | Electronic batch records, MES transactions, batch genealogy, equipment and line history across the three plants | TDE encrypted |
| QualityLIMS | 3 TB | QC test results, stability studies, deviations and CAPA, batch release records | TDE encrypted |
| SupplierPayments | 300 GB | Procurement and CMO payment processing, supplier banking details | Always Encrypted |
| 7 smaller databases | ~1 TB | Serialization, track-and-trace, label management, environmental monitoring, warehouse and materials, training records, planning staging, and reporting marts | TBD |
| Total: 10 known databases | ~12 TB | Full known SQL estate | TBD |

### 2.6 Application Downtime Tolerances

| Application | Downtime Tolerance | Peak Load |
|---|---:|---:|
| Supply Chain Planning Portal | 5 minutes | 500 req/sec |
| Batch Release & QA Console | 2 minutes | 200 req/sec |
| MES / Batch Execution Service | 0 minutes, 24/7 | 100 req/sec |

### 2.7 Current Environment

#### London Primary Datacenter

- ZAVA-SQL-PROD01: SQL Server 2019 CU25, 64 cores, 512 GB RAM, 15 TB
- ZAVA-SQL-REPORT01: SQL Server 2017 CU31, reporting workload
- ZAVA-SQL-LEGACY01: SQL Server 2016 SP3, pharmacy gateway

#### Miami DR Datacenter

- ZAVA-SQL-DR01: SQL Server 2019 CU25, 32 cores, 256 GB RAM
- Async availability group replication from London

### 2.8 Non-Negotiable Constraints

| Constraint | Requirement |
|---|---|
| Maximum Downtime | 30 minutes for BatchManufacturingCore; an in-process batch cannot lose its electronic batch record mid-run. |
| Data Residency | GxP batch and quality records for BatchManufacturingCore and QualityLIMS must remain in the UK region. |
| Regulatory Compliance | Migration must preserve data integrity per GMP Annex 11 / 21 CFR Part 11 with full audit trail continuity. |
| Launch Window | Migration must complete within the 16-week window and cannot collide with V2 process validation runs. |

### 2.9 Network Environment Requirements

- No direct internet access from datacenter servers.
- All traffic routes through Zscaler proxy with SSL inspection.
- Firewall change control requires 2-week lead time.
- ExpressRoute exists but bandwidth is limited.
- OT and plant-floor networks are segmented from IT.
- MES and IoT historian data crosses only through approved DMZ brokers.
- CMO, supplier, and 3PL API endpoints are IP-allowlisted on both sides.
- Partner-side firewall changes may take up to 4 weeks.

## 3. Rapid Prototyping Using Cora

### 3.1 Rapid Prototyping Steps (Option 1)

Here are the steps you will follow to create a rapid prototype for Caldova.

1. Leverage the AI assistant **Cora** in the CAIP technical workshop web app.
2. Provide the Caldova business problem statement to Cora.
3. Upload the future-state architecture image created during the whiteboarding exercise.
4. Ask Cora to explain the architecture and recommend the appropriate solution accelerator.
5. Choose the appropriate solution accelerator based on Cora's recommendation.
6. Generate Bicep templates and deployment assets.
7. Validate the generated assets in VS Code.
8. Deploy the solution in the sandbox environment.
9. Review the deployed environment and confirm that all three Caldova challenges are addressed.
10. Test the multi-agent solution.

### 3.2 Multi-Agent Solution to Test

The rapid prototype should include the following agents:

- Orchestrator / Supervisor
- Current capacity analysis agent
- Contract manufacturer analysis agent
- COO recommender agent
- Compliance guardrail agent

### 3.3 Sample Test Prompt

Use a prompt similar to the following:

> Assess the real-time line, shift, and batch-schedule data from all three plants to recommend 7% capacity gap closure. If the entire gap cannot be closed internally, assess all 11 contract manufacturers and weigh their qualification status, GMP compliance history, available capacity, tech-transfer time, and cost to fully close the 7% capacity gap.

## 4. Rapid Prototype Using GitHub Copilot (Option 2)

### 4.1 GitHub Copilot Role in the Workshop

Use GitHub Copilot to accelerate the creation, validation, and refinement of deployment assets. Copilot should help participants:

- Convert architecture decisions into deployable infrastructure definitions.
- Generate ARM/Bicep templates.
- Create supporting parameter files.
- Review dependencies and deployment sequencing.
- Explain template sections and resource relationships.
- Identify missing networking, identity, monitoring, or security configuration.
- Produce deployment instructions for the sandbox environment.

### 4.2 Upload Future State Architecture and Generate ARM/Bicep Template in VS Code

Follow these steps in VS Code:

1. Open the workshop repository or sandbox folder in VS Code.
2. Create a folder named `deployment-assets`.
3. Add the exported future-state architecture image to the folder.
4. Open GitHub Copilot Chat in VS Code.
5. Attach or reference the future-state architecture image.
6. Ask Copilot to analyze the architecture and identify the Azure resources required.
7. Ask Copilot to generate an ARM or Bicep template based on the architecture.
8. Ask Copilot to create a parameter file for the sandbox deployment.
9. Ask Copilot to validate dependencies, naming conventions, and resource group assumptions.
10. Review the generated files before deployment.

#### GitHub Copilot Setup

You will use GitHub Copilot to generate ARM or Bicep templates from the provided natural language business use case/scenario.

1. Click on the **Visual Studio Code** from the VM desktop.

   ![](../main/Sandbox-Environment-Guides/Images/amp14.png)

1. Click on **Continue with GitHub** to sign in to GitHub Copilot.

   ![](../Sandbox-Environment-Guides/Images/amp18.png)

1. On the **Sign in to GitHub** tab, enter the provided **GitHub username** **(1)** in the input field, and click on **Sign in with your identity provider** to continue **(2)**.

    - **Username:** <inject key="GitHub User Name" enableCopy="true"/>

     ![](../Sandbox-Environment-Guides/Images/amp19.png)

1. Click on **Continue** on the **Single sign-on to CloudLabs Organizations** page to proceed.

   ![](../Sandbox-Environment-Guides/Images/amp20.png)

1. Click on **Accept**.

   ![](../Sandbox-Environment-Guides/Images/amp21.png)

1. Select **Continue** to **Authorize Visual Studio Code**.

   ![](../Sandbox-Environment-Guides/Images/amp22.png)

1. Select **Authorize Visual Studio Code**.

   ![](../Sandbox-Environment-Guides/Images/amp23.png)

1. Select **Open**.

   ![](../Sandbox-Environment-Guides/Images/amp24.png)

1. Once the Visual Studio code opens, choose the theme of your wish **(1)** and then click **Get Started (2)**.

   ![](../Sandbox-Environment-Guides/Images/b1.png)

   ![](../Sandbox-Environment-Guides/Images/amp26.png)

   >**Note:** If you get any error pop up, please **Close.**

   ![](../Sandbox-Environment-Guides/Images/b2.png)   

1. Select **File (1)** and then **Open Folder (2)**.

   ![](../Sandbox-Environment-Guides/Images/amp27.png)

1. Navigate to **C:\ (1)**, then click **New folder (2)** to create a new folder.

   ![](../Sandbox-Environment-Guides/Images/b3.png)

1. Name the folder as **miq-project**.

   ![](../Sandbox-Environment-Guides/Images/b4.png)

1. Click on the folder **(1)** and then click on **Select folder (4)**.

   ![](../Sandbox-Environment-Guides/Images/b5.png)

1. From the **GitHub Copilot** Chat, select **Models (1)** and then select **Trust Workspace to enable models (2)**.

   ![](../Sandbox-Environment-Guides/Images/b6.png)

1. Select **Trust Folder and Continue**.

   ![](../Sandbox-Environment-Guides/Images/amp30.png)

1. Click **Auto (1)** and then set the model to **Claude Sonnet 5 (2)**.

   ![](../Sandbox-Environment-Guides/Images/b7.png)

1. Click on **Default permission (1)** and then set it to **Allow all (2)**.

   ![](../Sandbox-Environment-Guides/Images/b8.png)

1. Select **Enable**.

   ![](../Sandbox-Environment-Guides/Images/amp33.png)


### Caldova IQ Deployment Prompts

#### **Prompt 1: SQL Server MI**

**Step 1:** Copy the prompts below into **GitHub Copilot** and attach the **Future State Architecture**.

```
You are my smart agent. Review the problem statement and planned solution architecture design below to help Caldova overcome its challenges. Then prepare Bicep/ARM templates and deploy the resources in the respective environment.

Problem Statement
Caldova is accelerating the launch of its next-generation pharma product ahead of a competitor, requiring supply chain, manufacturing, procurement, data, application, and compliance teams to work from a single trusted context.

With a 7% capacity gap across three manufacturing plants, Caldova must determine whether the gap can be closed internally or through pre-qualified contract manufacturers within 3-6 months, while leveraging a multi-agent AI solution powered by Microsoft IQ capabilities to provide the COO with trusted recommendations and enable timely action on critical operational issues.

### Planned Solution Architecture Design

Attached.

### Scope

First, build the **"1-Modernize with Confidence"** section from the planned solution architecture design using **Azure SQL Server Managed Instance**.

### Instructions

1. Create a new Resource Group in Azure and proceed further.
2. Create Azure SQL Managed Instance with one database.
3. Generate sample data files based on the problem statement: a 7% capacity gap across three manufacturing plants.
4. Create tables for the sample data in the Azure SQL MI database.

> **Note:** Ensure the data is properly relational so it can support Fabric Ontology and Data Agent creation in the future.
```
---

#### **Prompt 2: Fabric IQ**

**Step 2:** Copy the prompts below into **GitHub Copilot**.

```
Great, you have created Azure SQL MI. Now follow the instructions below to build **Fabric IQ**.

### Instructions

1. List all Azure resources from the architecture diagram.
2. Create a new Fabric Workspace using **SKU F16** in the **West US 3** region.
3. Create a Lakehouse and load tables from the Azure SQL MI using Fabric mirroring.
4. Create a Fabric Ontology using the Lakehouse tables with proper relationships and generate the Ontology Graph view.
5. Create a Data Agent using the Ontology as a data source,and prepare proper Agent Instructions based on the Ontology entities to support the business problem.

### Completion Requirement

After completing the steps successfully, create a Markdown file with:

- Deployment instructions
- Post-deployment configurations
- Deployment startup steps for:
  - Creating the workspace
  - Creating the Lakehouse
  - Loading data from SQL MI into Lakehouse using mirroring
  - Creating the Ontology
  - Creating the Data Agent

Then start deployment.

### Supporting Prompts

#### Mirroring Issue

If mirroring is not loading data into the Lakehouse, use this prompt:

> Please load data from SQL MI to Lakehouse using Mirroring.

#### Data Agent Data Source Issue

If the Lakehouse is attached to the Data Agent instead of the Ontology, remove it manually and attach the Ontology manually.

> **Note:** Copilot may not perform this step automatically.

```

If all components are created successfully, proceed to Prompt 3.

---

#### **Prompt 3: Foundry IQ**

**Step 3:** Copy the prompts below into **GitHub Copilot**.
```
Great, you have created both Azure SQL MI and Fabric IQ. Now follow the instructions below to build **Foundry IQ**.

### Instructions

1. List all Azure Foundry-related resources from the architecture diagram.
2. Create Foundry resources in Azure.
3. In the Foundry Project, create one standard model: **gpt-5-mini**.
4. In the Foundry Project, create an agent named **Capacity-Planning-Agent** and attach the Fabric Data Agent, **<<your Data Agent Name>>**, by tool calling.
5. Create proper instructions for the agent so it provides useful responses.
6. Once **Capacity-Planning-Agent** is created, validate that the prompt works and returns valid results, then provide confirmation.
7. Ensure the agent instruction, prompt, and response fulfill the problem statement.

### Additional Requirements

In the Foundry Project, create relevant knowledge bases using Azure AI Search so responses can be retrieved from the Fabric Data Agent when sending prompts in the Foundry Agent.

Also provide relevant Foundry access to the Fabric Workspace.

### Completion Requirement

After completing all steps successfully, create a Markdown file with:

- Deployment instructions
- Post-deployment configurations

Then start deployment.

```

### Supporting Prompt

If the agent is not visible, use this prompt:

> Not able to see agent, please refresh and load it.

---

### Validation Prompts

Once all resources are deployed and the agent is ready, use the prompts below in both the Fabric Data Agent and Microsoft Foundry to validate the Caldova production issue.

#### Validation Prompt 1

```
List down products per plan wise.
```

#### Validation Prompt 2

```
Assess the real-time line, shift, and batch-schedule data from all three plants to recommend 7% capacity gap closure. If the entire gap cannot be closed internally, assess all 11 contract manufacturers and weigh their qualification status, GMP compliance history, available capacity, tech-transfer time, and cost to fully close the 7% capacity gap.
```



>**Note:** Treat generated templates as a rapid prototype starting point. Teams must validate resource availability, region support, security settings, and workshop sandbox constraints before deployment.

## 5. Multi-Agent Solution with Agentic Loop (Option 3)

If the customer already has unified data in the cloud, the key challenge is to build a governed multi-agent solution.

Use an **agentic loop** where agents can plan, reason, act, validate, and improve recommendations using trusted cloud data.

### Steps to Access

1. Open your preferred web browser.
2. Navigate to the Agentic Loop application:
[Agentic Loop - Build with Copilot, Run with Foundry](https://agentic-loop-geguehdxa0c0h4bx.b02.azurefd.net/)
3. Sign in if prompted.
4. Once the application loads, explore the available features and agent experiences.
5. Begin interacting with the application by selecting a scenario or entering a prompt.


Challenge:
Build a Microsoft Foundry multi-agent solution that analyzes the 7% capacity gap, evaluates internal capacity and qualified CMOs, and provides auditable COO-ready recommendations through an agentic loop.

## 6. Deliverables

Your team should produce:

1. Answers to all questions in the three challenges.
2. A completed future-state architecture created through whiteboarding.
3. An exported image of the future-state architecture.
4. Generated ARM/Bicep deployment assets.
5. A validation checklist for the sandbox deployment.
6. A short explanation of how the prototype addresses Caldova's capacity gap decision.

## 7. Report Back to Everyone

Two teams will be selected to present their solution in 10 minutes each:

- **2 minutes:** Approach overview
- **7 minutes:** Solution and answers to challenges
- **1 minute:** Biggest risk and mitigation

## 8. Workshop Recap & Next Steps

By the end of this workshop, you will have learned how to:

- Perform business and technical envisioning.
- Use whiteboarding to solve a customer business problem.
- Create a future-state architecture that addresses customer challenges.
- Use the future-state architecture to create a rapid prototype.
- Collaborate with customers using architecture visuals and AI-assisted prompts.
- Generate GitHub Copilot-assisted ARM/Bicep deployment assets.
- Validate a multi-agent solution that recommends how Caldova can close the 7% capacity gap.

### Next Step

Once deployed, the multi-agent solution should be able to provide a recommendation to close the 7% capacity gap for Caldova. If the gap cannot be fully closed internally, the solution should recommend the most suitable contract manufacturers based on qualification status, GMP compliance history, available capacity, tech-transfer time, cost, and auditability.
