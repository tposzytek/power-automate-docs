---
title: Learn how to create UI flows with WinAutomation | Microsoft Docs
description: Learn how to create UI flows with WinAutomation.
services: ''
suite: flow
documentationcenter: na
author: msftman
manager: kvivek
editor: ''
tags: ''
ms.service: flow
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 06/19/2020
ms.author: DeonHe
search.app: 
  - Flow
search.audienceType: 
  - flowmaker
  - enduser
---

# Use Softomotive's WinAutomation with UI flows


Here are some tips before you start using WinAutomation with UI flows.

1.  Your Power Automate Attended RPA license (paid or trial) gives you full access to [WinAutomation](https://www.winautomation.com/). This document will guide you through getting WinAutomation Processes running with Power Automate.

1.  Automation scripts in WinAutomation are called **Processes**. In Power Automate, automation scripts are called *flows* or *UI flows*.

1.  Before you create a WinAutomation Process, check the [list of connectors](https://flow.microsoft.com/connectors/) to see if the application you want to automate already has a connector. If it does, consider creating a flow instead of a UI flow. You might also [build your own connector](https://docs.microsoft.com/connectors/custom-connectors/). In general, API-based connectors provide a better overall experience than UI
    automation in terms of scalability, reliability, and lower cost.

1.  Existing WinAutomation licensed users can learn more at [Softomotive's support page](https://support.softomotive.com/support/home)

## Prerequisites

To run WinAutomation as part of Power Automate, you will need to:

1.  Ensure your machine meets the [requirements for UI flows](https://docs.microsoft.com/power-automate/ui-flows/setup#prerequisites).

2.  Install the [UI flows](https://docs.microsoft.com/power-automate/ui-flows/setup) app, and then install and configure the on-premises data gateway.

>[!IMPORTANT]
>You must have the latest version of WinAutomation and UI flows to record, test, or run UI automation.

## Licensing

You need to have a Power Automate *Per user plan with attended RPA* to use UI flows and WinAutomation. If you don't have a paid plan, you can start a trial by going to Power Automate.

 
## Install WinAutomation

1.  Download the [WinAutomation installer](https://aka.ms/rpaDesktopAutomationInstallPage).

1.  Run the **WinAutomationSetup.exe** file. This file is likely in your **Downloads** folder.

1.  Follow the instructions in the WinAutomation installer to complete the installation. During installation, ensure the **License Type** is set to **Microsoft Power Automate**.

## Sign-in to WinAutomation

1.  After the installation completes, start the WinAutomation Console from the Windows start menu.

1.  The application will start and prompt you to login. Enter the user
    credentials you use for [Power Automate](https://flow.microsoft.com/). If
    you don’t have a valid license, you will see this error message. You can
    also visit the [pricing page](https://flow.microsoft.com/pricing/) to learn
    more about this license or to get a trial license.

      ![License error](../media/create-processes/2d995d2d01844482458c06541d1c4b30.png)

      >[!IMPORTANT]
      > You will need your tenant administrator to grant consent to use
    your Power Automate Work or School account with WinAutomation. For that,
    your admin needs to install WinAutomation, sign in with their tenant
    administrator account, and then grant consent.

      ![Request for permissions](../media/create-processes/7e2c7feb5fa79f570599bffaff3e9887.png)

1.  When you asked to create a Master key during sign in, create one.

1.  Once signed in, you will see the WinAutomation console with a few example
    Processes. To get started, go to **Options** \> **Help** \> **Getting Started**, and then go through a few
    examples of creating simple Processes or check out information from [here](https://docs.winautomation.com/en/building-a-simple-process.html). You can learn more from [WinAutomation getting started tutorials](https://www.winautomation.com/support/tutorials/).

You can now create your own WinAutomation Processes and test them locally.

## Run WinAutomation Processes from Power Automate

1.  Once you have created your automation Process in WinAutomation, you can run
    it from a flow in Power Automate through UI flows (desktop) attended or
    unattended. (**Note**: to learn more about creating and running UI flows,
    please
    go [here](https://docs.microsoft.com/power-automate/ui-flows/create-desktop).)

1.  Create a new desktop UI flow. Delete the default first step of “Record app”.

      ![Delete record app step](../media/create-processes/8060b3deb4dc6c1adb3d2bf6623a5b05.png)

1.  Select **New step**, select **WinAutomation**, and then select the **Run WinAutomation (preview)** action.

      ![Select run WinAutomation](../media/create-processes/067208afe7d9326a0b3b95d3581ffe6d.png)

1.  In the **Run WinAutomation (preview)** card, fill in the Process Path and any optional command line arguments for the WinAutomation Process that you want to run. Surround arguments with quotes if you expect they will contain spaces. Otherwise WinAutomation will treat each word as a separate argument.

      ![WinAutomation card](../media/create-processes/cc73d6d455358810b1866df97e9a95e4.png)

   >[!NOTE]
   >You must create and store WinAutomation Processes locally. *Process Path* is a case-sensitive path in the WinAutomation Console for the Process, from a base directory of My Processes in the Folders Pane on the left side. If you have put the Process in a subfolder, you will need to include that information in the ProcessPath. Don’t put quotes around the Process Path.

   >[!TIP]
   >You can use UI flows inputs and Dynamic content in the target WinAutomation Process path and arguments from Power Automate flow.

1.  You can now save and test your UI flow to see how it launches the WinAutomation Process.

1.  You can then add the UI flow into a flow. You can even connect to other Power Automate connectors and triggers.

1.  You can then select *attended* or *unattended* as the run type.

    >[!TIP]
    >In your WinAutomation Process, you can use the *Get Command Line Arguments* action to retrieve the command line arguments. The arguments are in an array. Use their index to reference each argument.

    >[!IMPORTANT]
    >Do not pass sensitive text such as passwords through the command line arguments.

    >[!IMPORTANT]
    >If you’re running UI flows on an unattended cluster, ensure that WinAutomation is installed on all machines on which the target Process is copied. For more information on attended and unattended UI flows, click [here](https://docs.microsoft.com/power-automate/ui-flows/run-ui-flow).

1.  You can save and then run the flow and see it launch the WinAutomation Process. The UI flow will return after the WinAutomation Process run completes. You can view the run results from Power Automate. If the Process fails, you can see the error messages as well.

    >[!TIP]
    >If you get exceptions, you may not have the latest UI flows installed. Install the [latest UI flows](https://docs.microsoft.com/power-automate/ui-flows/upgrade).

1.  If you want WinAutomation to capture a screenshot when a Process fails, do the following:

1.  From the WinAutomation Console, right click on a Process, select "Edit Process's Properties". Go to the "Error Handling" tab and choose "Override Default Options". Click "Add screenshot to logs" and save. Now if a Process     fails, you can view the screenshot captured at runtime from the Power Automate UI flow run details.  

    ![Todo](../media/create-processes/a43a1010ea3c9b203b8b2c2b1086b26e.png)

Currently you have to use certain WinAutomation steps to write results and outputs from the process into a file in the cloud share or email the results out. Then you can use connectors from Power Automate to access and use those
results.

## How to obtain an RPA trial license

Log in to [Power Automate](https://flow.microsoft.com/) then selecting the **UI flows** tab under **My flows**. You'll see the trial dialog from which you can start the trial.

![Start a trial or buy a license](../media/create-processes/ceecb625d84ae49ef7dc711a21cc3b54.png)

If you already have a paid plan or you used a trial previously, you cannot start a new trial. In this case, you will need to ask your administrator to buy or start a trial of the Power Automate *Per user plan with attended RPA*. They can make the purchase by going to **Billing** \> **Purchase services** in the Microsoft 365 admin center, and then searching for the right plan.

![Per user plan with attended RPA](../media/create-processes/07d23b56dcd2b5bdd42655e146bf47cd.png)

Finally, once they have purchased a plan or gotten the free trial, they need to
assign that plan to a user.

>[!IMPORTANT]
>When you assign a plan to a user, it may take few minutes before the assignment
becomes effective.

## Troubleshooting WinAutomation licensing issues

If you are receiving licensing errors during the launch of WinAutomation, ensure
the user you’re logging in as has a valid Power Automate RPA license. To confirm this:

1.  Go to [Power Automate](https://flow.microsoft.com/) and sign in.

1.  Select My flows on the left navigation bar.

1.  Select UI flows on the page on the right. You should see you can create new
    UI flows there if you have the correct license.

1.  You may need to start a trial or ask your administrator to do it.

    >[!NOTE]
    >The license is cached when users launch WinAutomation while connected to the Internet.

To reset the license information stored by WinAutomation, you can delete the following file: %localappdata%\\Softomotive\\WinAutomation\\msalcache.bin3.

## Learn more

-   Read about the [WinAutomation acquisition](https://flow.microsoft.com/blog/microsoft-acquires-softomotive-to-expand-low-code-robotic-process-automation-capabilities-in-microsoft-power-automate/).
-   Get support for [WinAutomation](https://support.softomotive.com/support/home).
-   Get a head start with [WinAutomation tutorials](https://www.winautomation.com/support/tutorials/).
-   Learn to [create desktop UI flows](https://docs.microsoft.com/power-automate/ui-flows/create-desktop).
-   Learn how to [run UI flows](https://docs.microsoft.com/power-automate/ui-flows/run-ui-flow).
-   Learn to [manage UI flows](https://docs.microsoft.com/power-automate/ui-flows/manage).
-   Learn more about the [on-premises gateway](https://docs.microsoft.com/power-automate/gateway-reference#use-a-gateway).
