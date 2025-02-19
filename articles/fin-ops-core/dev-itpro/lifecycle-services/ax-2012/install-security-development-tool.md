---
# required metadata

title: Install the Security Development Tool
description: This topic provides information about how to install the Security Development Tool. 
author: kfend
ms.date: 07/26/2018
ms.topic: article
ms.prod: dynamics-ax-2012 
ms.technology:

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 18391
ms.assetid: f62f5636-4d63-473e-b326-277ea500c540
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# Install the Security Development Tool

[!include [banner](../../includes/banner.md)]

> [!NOTE] 

> This is pre-release documentation of a preliminary nature and is subject to change at any time without notice. Microsoft cannot guarantee the accuracy of any information provided herein. Before you install the Security Development Tool, be aware that we assume that you meet the following prerequisites:

-   You are familiar with the development environment in Microsoft Dynamics AX 2012.
-   You are familiar with the security model in Microsoft Dynamics AX 2012.
-   You have developer privileges in Microsoft Dynamics AX, so that you can run the tool from the Application Object Tree (AOT).

> [!IMPORTANT] 
> Some optional features of the Security Development Tool require that changes be made to framework classes, or that tracing be enabled. These changes can affect the overall performance of your Microsoft Dynamics AX system. Therefore, we recommend that you use this tool only in development or test environments.

## Procedures
This section lists the procedures required to install and configure the Security Development Tool.

### Install the tool

1.  Download the SecurityDevelopmentTool.msi from the Downloadable tools of [Microsoft Dynamics Lifecycle Services](https://lcs.dynamics.com) (note that the Downloadable tools is only accessible if you log in to LCS with a Microsoft account; it will not be shown if you sign in with an organizational account)
2.  Run **SecurityDevelopmentTool.msi** to open the **Installation Wizard**.
3.  Accept the Microsoft Software License Terms, and then click **Install**.
4.  When a message indicates that the tool has been successfully installed, click **Finish**. After the **Installation** **Wizard** has finished running, the files are available at the following locations:
    -   For 64-bit systems: %ProgramFiles (x86)%Microsoft%Security Development Tool
    -   For 32-bit systems: %ProgramFiles%Microsoft%Security Development Tool

### Import and compile the tool

1.  Drain the client connections from the instance of Application Object Server (AOS) that you are working with. For more information, see [Drain users from an AOS](https://technet.microsoft.com/library/hh433538.aspx).
2.  Go to **Administrative Tools**, click **Services**, and stop the **Microsoft Dynamics AX Object Server 6.0** service.
3.  Use Windows PowerShell or AXUtil to import the **SecurityDevelopmentTool.axmodel** model into the Microsoft Dynamics AX AOT.
    1.  On the Start menu, point to **All Programs**, point to **Administrative Tools**, and then click **Microsoft Dynamics AX Management Shell**.
    2.  At the Windows PowerShell command prompt, PS C:&gt;, type the following command, and then press Enter.

        ```powershell
        Install-AXModel -File “C:\Program Files (x86)\Microsoft\Security Development Tool\SecurityDevelopmentTool.axmodel”
        ```

        For more information, see [How to: Export and Import a Model](https://msdn.microsoft.com/library/c2449a03-7574-4b9d-8518-9005b560209f(AX.60).aspx).

4.  Start the Microsoft Dynamics AX Object Server 6.0 service.
5.  Start the Microsoft Dynamics AX client. The Model store has been modified dialog box opens.
6.  Click **Compile and Synchronize**.
7.  When synchronization is completed, press **Ctrl+Shift+W** to open a Development workspace.
8.  Run the **SysSecEntryPointManagerSetup** class to add the following menu items to the standard Microsoft Dynamics AX menus.

    | Menu item                     | Menu                               |
    |-------------------------------|------------------------------------|
    | SysSecRoleEntryPointDeveloper | SysContextMenu (AOT Add-Ins)       |
    | SysSecRoleEntryPoint          | System AdministrationSetupSecurity |


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]