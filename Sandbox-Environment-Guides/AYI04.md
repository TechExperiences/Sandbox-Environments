# Post deployment Guide - Work IQ

The third component of the accelerator — Work IQ (the Copilot Studio email-triggered agent that orchestrates Fabric IQ and Foundry IQ from a single conversational ingress)

## Steps need to be performed:

- **Import the solution:** Import the Power Platform zip solution file inside the solution file folder into your Power Platform environment
- **Configure connections:** Sign in to and authorize the Work IQ, Microsoft Teams, Copilot Studio, Office 365 Outlook, Fabric Data Agent, and Foundry Agent connections. 
- **Configure the email trigger** in the Power Automate flow — select the target inbox/folder to monitor and (optionally) add a subject filter such as IQ Request.
- **Publish the agent** in Copilot Studio and enable the Microsoft Teams channel.