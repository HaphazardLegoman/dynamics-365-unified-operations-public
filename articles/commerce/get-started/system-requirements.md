---
# required metadata

title: System requirements for cloud deployments of Dynamics 365 Commerce
description: This topic lists the system requirements for cloud deployments for the current version of Dynamics 365 Commerce.
author: jashanno 
ms.date: 02/11/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 55651
ms.search.region: Global
ms.search.industry: retail 
ms.author: jashanno
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 10.0.5

---

# System requirements for cloud deployments of Dynamics 365 Commerce

[!include [banner](../includes/banner.md)]

This topic lists the system requirements for cloud deployments of the current version of Dynamics 365 Commerce. If this step is appropriate, before you install Commerce, you should verify that the system that you're working with meets or exceeds the minimum network, hardware, and software requirements.

## Supported web browsers

The web application can run in any of the following web browsers that run on the specified operating systems:

- Microsoft Edge (latest publicly available version) on Windows 10
- Internet Explorer 11 on Windows 10, Windows 8.1, or Windows 7
- Google Chrome (latest publicly available version) 
- Apple Safari (latest publicly available version)

> [!NOTE]
> It is possible for the Safari browser to show an error during device activation of a Cloud POS device due to an Azure Active Directory token being unattainable. You can resolve this issue by utilizing the [Microsoft Enterprise SSO plug-in for Apple devices](https://docs.microsoft.com/azure/active-directory/develop/apple-sso-plugin).

To find the latest release for each web browser, go to the software manufacturer's website.

> [!NOTE]
> - To enable Task Recorder to capture screenshots and include them in Microsoft Word documents that are generated, you must install a pre-release Chrome extension. <!---For instructions about how to install the extension, see [Screenshot Extension setup](../../dev-itpro/user-interface/task-recorder).-->
> - The Workflow Editor and Report Designer for Financial reporting are started as ClickOnce applications. They require a 64-bit-compatible operating system. Only Microsoft Edge and Internet Explorer (on a supported version of Microsoft Windows) support ClickOnce applications out of the box. If you're using Chrome, you must install a ClickOnce extension, such as [Meta4](https://chrome.google.com/webstore/detail/meta4-clickonce-launcher/jkncabbipkgbconhaajbapbhokpbgkdc) to use ClickOnce applications. If you use Chrome in incognito mode, make sure that the ClickOnce extension is also enabled for incognito mode.
> - To preview PDF files, we recommend that you use browsers such as Microsoft Edge (latest publicly available version) on Windows 10, or Google Chrome (latest publicly available version) on Windows 10, Windows 8.1, Windows 8, Windows 7, or Google Nexus 10 tablet.

### Supported web browsers for Cloud POS

Cloud point of sale (POS) can run in any of the following web browsers that run on the specified operating systems:

- Microsoft Edge (latest publicly available version) on Windows 10
- Internet Explorer 11 on Windows 10, Windows 8.1, or Windows 7
  > [!NOTE]
  > Beginning with release 10.0.17, Internet Explorer will no longer be supported.
- Chrome (latest publicly available version) on Windows 10, Windows 8.1, or Windows 7

## Network requirements

- Commerce is designed for networks that have a latency of 250–300 milliseconds (ms) or less. This latency is the latency from a browser client to the Microsoft Azure datacenter that hosts Commerce. We recommend that you test network latency at [AzureSpeed.com](http://www.azurespeed.com).
- Bandwidth requirements for Commerce depend on your scenario. Most typical scenarios require a bandwidth that is more than 50 kilobytes per second (KBps). However, we recommend more bandwidth for scenarios that have high payload requirements, such as scenarios that involve workspaces or extensive customization.

In general, Commerce is optimized for the internet. The number of round trips from a browser client to the Azure datacenter is very small, and the whole payload is compressed.

> [!WARNING]
> Don't calculate bandwidth requirements from a client location by multiplying the number of users by the minimum bandwidth requirements. The concurrent usage of a given location is very difficult to calculate. Customers who are concerned about bandwidth requirements should use a preview version of Commerce.

## .NET Framework requirements

Commerce requires Microsoft .NET Framework 4.7.1 or later for all ClickOnce applications, such as the document routing agent. For installation instructions, see [Install the .NET Framework for developers](https://msdn.microsoft.com/library/5a4x27ek(v=vs.110).aspx). 

## Supported Microsoft Office applications

The following Microsoft Office applications are supported:

- To run the Microsoft Excel and Word add-ins, you must have Microsoft Office 2016 for Windows installed. For more information about version requirements, see [Troubleshoot the Office integration](../../fin-ops-core/dev-itpro/office-integration/office-integration-troubleshooting.md).
- To view documents that are generated by the Export to Excel or Export to Word functionality, you must have Microsoft Office 2007 or later installed.

## System requirements for Commerce client components

It is critical to perform proper performance testing prior to going live in production. The following are considered minimum system requirements for applications to function. To achieve desired performance, consider concepts like data volumes, transactional load per hour, and customization impact. Proper performance testing both early into implementation and again prior to final testing will allow for any necessary performance improvements to be made and to validate that the base solution meets the expected operation times required.

[!WARNING] The Microsoft Windows 7 operating system is no longer supported for anything other than security-related fixes. As a result, while Dynamics 365 Commerce components may function on Windows 7, there will be no bug fixes that specifically relate to supporting this operating system. Workarounds may be required for components to function properly on Windows 7, so it is highly recommended to upgrade to a supported operating system.

## Modern POS for Windows requirements

> [!NOTE]
> - If Modern POS will use an offline database, the computer must meet all system requirements for Microsoft SQL Server and the system must have no less than 10 GB of disk space available. It is recommended to have no less than 20 GB of disk space available. An offline database for Modern POS requires SQL Server 2014 with Service Pack 3 or later, SQL Server 2016 with Service Pack 2, SQL Server 2017, or newer. The SQL Server version used must have the Full-Text Search feature installed. We recommend that you always use the latest version that is available, and that you install all the latest service packs. By following these recommendations, you can help to ensure both compatibility and security.
> - Starting August 1, 2019, Modern POS and other client-side components require that the Microsoft .NET Framework version 4.7.1 or later be installed. For installation instructions, see [Install the .NET Framework for developers](https://msdn.microsoft.com/library/5a4x27ek(v=vs.110).aspx).

### Supported Windows operating systems

- Modern POS is a 32-bit application, but it will run on both x86 and x64 architectures.
- Modern POS is supported on Windows Server 2016, Windows 10 Pro, Windows 10 Enterprise, Windows 10 Enterprise Long Term Service Branch (LTSB), and Windows 10 IOT Enterprise editions. At a minimum, the Windows 10 Anniversary Update (version 1607), build 14393, must be installed.
- It is not recommended to use Modern POS and other Commerce components on Windows 10 Pro unless within a domain as Windows 10 Pro doesn't allow for advanced management of updates to the operating system.
- It is not recommended to use Modern POS and any other Commerce component together on the same computer.

### Minimum system requirements

- The minimum supported effective resolution for POS Full layout (PCs and tablets) is 1,024 × 768 (recommended 1366 x 768 or greater)
- The minimum supported effective resolution for POS Compact layout (phones and small tablets) is 320 x 568 (recommended 360x640 or greater)
- The computer that Modern POS runs on must meet these requirements:

    - It must have, at a minimum, a dual-core processor that runs at no less than 2 gigahertz (GHz).
    - It must have, at a minimum, 3 gigabytes (GB) of random-access memory (RAM). When combining with SQL Server for offline, no less than 4 GB of RAM is required.
    - It must have internet access.

## Modern POS for Apple iPhone or iPad requirements

- iOS 11 or later

## Modern POS for Android phone or tablet requirements

- Android OS 6.0 or later

## Retail hardware station requirements

> [!NOTE]
> Starting August 1, 2019, Retail hardware station and other client-side components require that the .NET Framework version 4.7.1 or later be installed. For installation instructions, see [Install the .NET Framework for developers](https://msdn.microsoft.com/library/5a4x27ek(v=vs.110).aspx).
> It is critical to note that this component utilizes a server certificate. Server certificates must be managed for expiration. By default, a certificate expires in one calendar year (365 days).

### Supported operating systems

- Retail hardware station is a 32-bit application, but it will run on both x86 and x64 architectures.
- Retail hardware station is supported on the following operating systems:

    - Windows 8.1 Update 1 Professional, Enterprise, and Embedded editions.
    - Windows 10 Pro, Enterprise, Enterprise LTSB, and IOT Enterprise editions.
    - Windows Server 2016 and Windows Server 2019.
    - It is not recommended to use Retail hardware station and other Commerce components on Windows 10 Pro unless within a domain as Windows 10 Pro doesn't allow for advanced management of updates to the operating system.

### Minimum system requirements

The computer must meet all system requirements for installing and using the following items:

- Microsoft Internet Information Services (IIS)
- Third-party hardware

## Commerce Scale Unit (self-hosted) requirements

> [!NOTE]
> Starting August 1, 2019, Commerce Scale Unit and other client-side components require that the .NET Framework version 4.7.1 or later be installed. For installation instructions, see [Install the .NET Framework for developers](https://msdn.microsoft.com/library/5a4x27ek(v=vs.110).aspx).
>
> It is critical to note that this component utilizes a server certificate in addition to Azure Service to Service authentication.  Both the generated Azure web application keys (formerly called *secrets*) and the server certificate must be managed for expiration.  By default, a certificate and a generated Azure web application key expires in one calendar year (365 days).

Take note that the minimum system requirements listed below are the bare minimum necessary to get a Commerce Scale Unit to function in a test scenario. The following is not representative of a realistic production environment. It is critical to perform proper performance testing and validate that the hardware used will meet the needs of the users.

### Supported operating systems

- Commerce Scale Unit is a 32-bit application, but it will run on both x86 and x64 architectures.
- Commerce Scale Unit is supported on the following operating systems:

    - Windows 8.1 Update 1 Professional, Enterprise, and Embedded editions.
    - Windows 10 Pro, Enterprise, Enterprise LTSB, and IOT Enterprise editions.
    - Windows Server 2016 and Windows Server 2019.
    - It is not recommended to use Commerce Scale Unit and other Commerce components on Windows 10 Pro unless within a domain as Windows 10 Pro doesn't allow for advanced management of updates to the operating system.

### Minimum system requirements

> [!NOTE]
> The following are the minimum system requirements for Commerce Scale Unit.  Both these and the recommended requirements are the minimum possible for testing and basic functionality.  It is crucial to perform performance testing and validate that the hardware used for Commerce Scale Unit meets expectations.

- 4 GB of RAM
- 1.6 GHz i5 (or equivalent) minimum CPU speed per core (2 cores are the minimum).
- At least 15 GB of free space (the channel database can require a large amount of space).

### Recommended system requirements

- 6 GB of RAM
- 2.4 GHz i7 (or equivalent) minimum CPU speed per core (4 cores are recommended).
- At least 20 GB of free space (the channel database can require a large amount of space).

It would be in an organization's best interest to also take the following items into consideration when determining personal hardware needs:

- Number of physical network ports (more ports enhances throughput per second).
- SQL Server log flush size (this directly impacts SQL Server performance).
- Data read and write capabilities (this directly impacts SQL Server performance).
- Number of CPU(s) core, number of simultaneous threads per core, and speed per core (this impacts overall throughput of the system).
- Whether load balancing will be required.

## Connector requirements

### Supported operating systems

- The Connector for Microsoft Dynamics AX has two separate installers, one for Async Server Connector service and one for Real-time service for Microsoft Dynamics AX 2012 R3.
- Both components are 32-bit applications, but they will run on both x86 and x64 architectures.
- Both components are supported on the following operating systems:

    - Windows 8.1 Update 1 Professional, Enterprise, and Embedded editions.
    - Windows 10 Pro, Enterprise, and Enterprise LTSB editions.
    - Windows Server 2016 and Windows Server 2019.
    - It is not recommended to use Commerce components on Windows 10 Pro unless within a domain as Windows 10 Pro doesn't allow for advanced management of updates to the operating system.

### Minimum system requirements

- 2 GB of RAM (4 GB of RAM are recommended).
- 1.6 GHz peak CPU speed per core (2 cores are the minimum).
- At least 10 GB of free space (the channel database can require a large amount of space).

## Requirements for development on local VMs

For information about the requirements for development on local virtual machines (VMs), see [VM that is running on-premises](../../dev-itpro/dev-tools/access-instances.md#vm-that-is-running-on-premises).

## Database collation

The only supported collation for Commerce databases in the cloud is **SQL\_Latin1\_General\_CP1\_CI\_AS**. Please ensure that your SQL Server and database collations in development environments are set to this. Also ensure that any configuration environments that are published to Sandbox have this same collation.

## Additional resources

[Get an evaluation copy](../../dev-itpro/dev-tools/get-evaluation-copy.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]