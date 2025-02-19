---
# required metadata

title: Human Resources virtual tables FAQ
description: This topic is a list of frequently asked questions about Human Resources virtual entities.
author: jaredha
ms.date: 12/15/2020
ms.topic: article
ms.prod:
ms.technology: 

# optional metadata

# ms.search.form:
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
# ms.custom: NotInToc
ms.search.region: Global
# ms.search.industry:
ms.author: sunilg
ms.search.validFrom: 2020-12-15
ms.dyn365.ops.version: 10.0.12
---

# Human Resources virtual tables FAQ

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic is a collection of frequently asked questions about virtual tables in Dynamics 365 Human Resources. 

> [!NOTE]
> For more information about Dataverse (formerly Common Data Service) and terminology updates, see [What is Microsoft Dataverse?](https://docs.microsoft.com/powerapps/maker/data-platform/data-platform-intro)

### Can a solution from an independent software vendor (ISV) take a dependency on virtual tables? What does the application lifecycle management (ALM) look like?

Yes. The virtual tables are all generated in the Dynamics 365 HR Virtual Entities solution, which is API-managed. The items in the solution change as you make tables visible or hidden. However, the solution is still a managed solution that you can take dependency on. The schema and contract for each table is maintained. The standard ALM flow just takes a standard reference to a virtual table from this solution with the ISV solution's **Add existing** option. Missing dependency of the solution will be checked when the solution is imported. During import, if a specified virtual table doesn't yet exist, the virtual table is automatically made visible.

### Which tables from Human Resources do users see in the catalog in Dataverse?

Generally, users see all tables where **IsPublic** is set to **Yes**. These tables are the same tables that are currently visible in Open Data Protocol (OData).

### Do all Microsoft Power Platform users have to be users in Human Resources?

Any user of Microsoft Power Platform who tries to access Human Resources data through a virtual table must also exist as a user in Human Resources. So not *all* users must be users in Human Resources. Only those users who access Human Resources data through virtual tables must be users in Human Resources.

### Where do I find the catalog table?

The table catalog is listed on the **Virtual tables** tab of the **Dataverse integration** page in the Human Resources application. All available tables are listed after setup and configuration is completed. For more information, see [Configure Dataverse virtual tables](hr-admin-integration-common-data-service-virtual-entities.md).

### Is there a way to specify a company when I perform data operations on a virtual table?

Yes. Although the company is implicit in Human Resources, it's an explicit column on each company-striped table in Dataverse. You can use either the **Company Code** column, where the value is a four-character string, or the **Company** column, which is a lookup to cdm\_Company. Both approaches provide the same information.

If you're accessing the table through the Dataverse Web API, the company is identified by the **Data Area ID** property (mshr\_dataareaid). Each company-specific table with this property has a navigation property to the cdm\_Company table.

### Can I change the prefix for the virtual tables?

No. All Human Resources virtual tables should be generated in the Dynamics 365 HR Virtual Entities solution and have the "mshr\_" prefix. Don't change this prefix. If you have a scenario where you believe the prefix has to be changed, you should share that scenario with Microsoft.

### How can I filter data in a Power Apps app, based on the current user or any other dynamic criteria, such as today-10?

You can write a pre-operation plug-in on the RetrieveMultiple message of the table and change the criteria on the query in it. Alternatively, you can write a post-operation plug-in to filter the results before they're returned.

### How can I show, in the same grid, data from multiple virtual tables that are joined to a physical table record in Dataverse?

This approach isn't currently possible in Dataverse.

### If I want a default value to be entered in a field during pre-create, will an initValue on the data table work?

Yes. Here's the order of calls:

1. Dataverse sends a create or update message.
2. All the existing logic on the Human Resources entity and backing tables is invoked. This logic includes default value entry that might change values.
3. Dataverse sends another Retrieve (single) message to get the latest copy of the data, including any columns that default values were entered for.

### Does the form business logic in Human Resources get called through virtual tables?

Human Resources business logic on forms isn't invoked through virtual tables. Instead, expect the same behavior that you get through OData access to the same tables. A table exposed to OData (that is, **IsPublic** is set to **Yes**) should have appropriate protections to ensure data can't be corrupted. If any table lacks this protection, that situation represents a bug in the table. If you see differences in table behavior between OData and virtual tables, that situation represents a bug in the virtual table feature.

### When adding records using virtual tables is there any way to use number sequences?

Yes, if the Human Resources table can auto generate number sequences, then it will work the same way from the virtual table.

### Why doesn't search view work in Power Apps?

If there are no columns added in the quick find view for the table, then the search box does nothing. The workaround is to add one or more columns of the table to the quick find view.

### Are custom fields supported on virtual tables?

Yes, custom fields are supported on virtual tables. You must first add the custom field to the data entity related to the virtual table. You can then generate or refresh the virtual table to include the custom field in its schema. For more information on adding custom fields to data entities, see [Exposing custom fields on data entities](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/get-started/user-defined-fields?toc=/dynamics365/human-resources/toc.json#exposing-custom-fields-on-data-entities).

### What do I do if I get an error that the Dynamics 365 for Talent user wasn't found?

When setting up virtual tables in the **Microsoft Dataverse integration** page, you may see an error message in the Action center stating the following:

`User Dynamics365 for Talent was not found in Finance and Operations. Please ensure this user exists.`

This message indicates that permissions haven't been granted in Human Resources application to the app set up for virtual tables. You can resolve this by completing the steps to [Grant app permissions in Human Resources](https://docs.microsoft.com/dynamics365/human-resources/hr-admin-integration-common-data-service-virtual-entities#grant-app-permissions-in-human-resources).

[!INCLUDE[footer-include](../includes/footer-banner.md)]
