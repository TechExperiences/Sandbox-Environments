# Post deployment Guide - Work IQ

The third component of the accelerator — Work IQ (the Copilot Studio email-triggered agent that orchestrates Fabric IQ and Foundry IQ from a single conversational ingress)

### Steps need to be performed:

- **Import the solution:** Import the Power Platform zip solution file inside the solution file folder into your Power Platform environment
- **Configure connections:** Sign in to and authorize the Work IQ, Microsoft Teams, Copilot Studio, Office 365 Outlook, Fabric Data Agent, and Foundry Agent connections. 
- **Configure the email trigger** in the Power Automate flow — select the target inbox/folder to monitor and (optionally) add a subject filter such as IQ Request.
- **Publish the agent** in Copilot Studio and enable the Microsoft Teams channel.

## Step 0: Create a Power Platoform Environment with Dataverse enabled

1. Right click on the [make.powerapps.com](https://make.powerapps.com) link then **Copy link** and then paste it on your VM browser tab.

1. On the **Welcome to Power Apps** page, click **Get started**.

   ![](../Sandbox-Environment-Guides/Images/a41.png)

1. Click on the **Settings (1)** from the top left and then select **Admin center**.

   ![](../Sandbox-Environment-Guides/Images/a42.png)

1. On the **Power Platform admin center**, click on **Manage (1)** then **Environments (2)** and then click **+ New (3)**.

   ![](../Sandbox-Environment-Guides/Images/a43.png)

1. On the **New environment** page, provide the following details to create a new environment.

    - **Type:** Choose **Production (1)**
    - **Region:** Leave default
    - **Name:** Enter **Amplify Environment<inject key="DeploymentID" enableCopy="false"/>** **(3)**
    - Then Scroll down to **Change default settings**

      ![](../Sandbox-Environment-Guides/Images/a44.png)

1. Expand **Change default settings (1)** and then **Turn On (2)** setting **Add a Dataverse data  store?** and then click on **Save (3)**.

   ![](../Sandbox-Environment-Guides/Images/a45.png)

1. Under **Security group**, click **+ Select**.

   ![](../Sandbox-Environment-Guides/Images/a46.png)

1. Select **None (1)** and then **Done (2)**.

   ![](../Sandbox-Environment-Guides/Images/a47.png)

1. Then select **Save**.

   ![](../Sandbox-Environment-Guides/Images/a48.png)

1. Please wait until your **Amplify Environment<inject key="DeploymentID" enableCopy="false"/>** environment is **Ready** before proceeding.

   ![](../Sandbox-Environment-Guides/Images/a49.png)


## Step 1: Import the Solution

In this step, you will import the Power Platform zip solution file into your Power Platform environment.
