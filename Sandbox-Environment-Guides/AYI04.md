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

1. Navigate back to **Power Apps** portal.

1. Click on the **default Environment (1)** and then select your **Amplify Environment<inject key="DeploymentID" enableCopy="false"/> (2)** Environment.

   ![](../Sandbox-Environment-Guides/Images/a50.png)

1. Make sure your in your **Amplify Environment<inject key="DeploymentID" enableCopy="false"/>** Environment.

   ![](../Sandbox-Environment-Guides/Images/a51.png)

1. Go to **Solutions (1)** and then select **Import solution (2)**.

   ![](../Sandbox-Environment-Guides/Images/a52.png)

1. Click on **Browse** to select the solution file to import.

   ![](../Sandbox-Environment-Guides/Images/a53.png)

1. Navigate to **C:\Files (1)**, then select **MicrosoftIQAccelerator (2)** zip file and then **Open (3)**.

   ![](../Sandbox-Environment-Guides/Images/a54.png)

1. Once the Solution file is imported, click on **Next**.

   ![](../Sandbox-Environment-Guides/Images/a55.png)

1. Click on **Next** again.

   ![](../Sandbox-Environment-Guides/Images/a56.png)

1. Make sure you signed in / green check mark is showing up for all the services **(1)** and then **Import (2)**.

   ![](../Sandbox-Environment-Guides/Images/a57.png)

1. Wait for the Solution to import successfully.

   ![](../Sandbox-Environment-Guides/Images/a58.png)

1. After importing has completed, click **Publish all customizations** in the top menu.    

   ![](../Sandbox-Environment-Guides/Images/a59.png)

1. Wait for publishing to complete. 

   ![](../Sandbox-Environment-Guides/Images/a60.png)

1. When the import is complete, the solution will be available in the environment.

### Step 3: Configure the Email Trigger

Once connections are set, configure the Power Automate flow to monitor the correct inbox:

1. Navigate to **Solutions (1)** then select the imported **Microsoft IQ Accelerator (2)** solution.

   ![](../Sandbox-Environment-Guides/Images/a61.png)

1. Select the **When a new email arrives (V3)** trigger.

   ![](../Sandbox-Environment-Guides/Images/a62.png)

1. Click on **Edit**.

   ![](../Sandbox-Environment-Guides/Images/a63.png)

1. Click on **When a new email arrives (V3)** trigger.

   ![](../Sandbox-Environment-Guides/Images/a64.png)

1. Delete the **Inbox** folder.

   ![](../Sandbox-Environment-Guides/Images/a65.png)

1. Once it is deleted, click on the **folder (1)** icon and then select the **Inbox (2)** again. We deleted and selected the folder again because `Even though the Folder field shows 'Inbox,' this solution was imported from a different environment, so it may still be pointing at the wrong mailbox behind the scenes. Delete the value and re-select 'Inbox' from the picker to force it to re-link to your own mailbox.`

   ![](../Sandbox-Environment-Guides/Images/a66.png)

1. Expand the **Show advanced options** drop down.

   ![](../Sandbox-Environment-Guides/Images/a67.png)

1. Click the **X **next to that email address to remove it entirely, it is a stale leftover from wherever this solution was originally built/tested. 

   ![](../Sandbox-Environment-Guides/Images/a68.png)

1. Optionally add a `Subject Filter` to limit which emails trigger the flow (e.g., **IQ Request (1)**) and then **Save (2)** the flow.   

   ![](../Sandbox-Environment-Guides/Images/a69.png)

1. dd

   ![](../Sandbox-Environment-Guides/Images/a70.png)