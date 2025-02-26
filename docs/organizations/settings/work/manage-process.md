---
title: Create and manage an inherited process 
titleSuffix: Azure DevOps Services
description: Add custom fields, work item types, and more by creating and applying an inherited process to a project  
ms.custom: inherited-process
ms.technology: devops-agile
ms.assetid: 6EB45080-22E2-43AD-92F9-77D03D5C136F  
ms.author: kaelli
author: KathrynEE
ms.topic: tutorial
monikerRange: '>= azure-devops-2019'
ms.date: 07/08/2022
---

<!-- supports the FWLink: https://go.microsoft.com/fwlink/?LinkID=616878 --> 


# Create and manage inherited processes 

[!INCLUDE [version-gt-eq-2019](../../../includes/version-gt-eq-2019.md)]

You customize your project, Agile tools, and the work tracking system through an inherited process. The customizations you make are in effect for all projects that use the process. A process defines the building blocks of the work tracking system. Whenever you create a project, you select the process you want your project to use. 

[!INCLUDE [temp](../includes/note-on-prem-link.md)]

To learn more about what you can customize, see [About process customization and inherited processes](inheritance-process-model.md). 

Learn how to perform these tasks:  

> [!div class="checklist"] 
> * Open **Settings>Process**
> * Create an inherited process   
> * Customize an inherited process  
> * Copy an inherited process   
> * Change projects to use an inherited process or a system process    
> * Add a project based on a process   
> * Enable or disable a process
> * Set a process as the default to use when adding projects  

[!INCLUDE [temp](../includes/note-audit-log-support-process.md)]

[!INCLUDE [temp](../includes/process-prerequisites.md)] 

[!INCLUDE [temp](../includes/open-process-admin-context-ts.md)]

<a id="create-inherited-process"></a>


## Create an inherited process

You can create an inherited process from any one of the four system processes: [Basic](../../../boards/get-started/plan-track-work.md), [Agile](../../../boards/work-items/guidance/agile-process.md), [Scrum](../../../boards/work-items/guidance/scrum-process.md), or [CMMI](../../../boards/work-items/guidance/cmmi-process.md).   

1. From the **Process** page, open the **&hellip;** context menu of the process you'll use to create an inherited process, and then choose **Create inherited process**. 

	Here, we create an inherited process from the Agile system process.   

	> [!div class="mx-imgBorder"]  
	> ![Screenshot of Context menu, Choose Create inherited process.](media/process/create-inherited-process.png) 

	If you don't have access to these options, ask a member of your **Project Collection Administrators** group to grant you permissions. To find a member, see [Look up a project collection administrator](../../security/look-up-project-collection-administrators.md).

1. Enter a name for your process and optionally a description. (For naming restrictions, see [About process customization and inherited processes, Process name restrictions](inheritance-process-model.md#process-naming).

   <img src="media/process/mprocess-create-inherited-process-dialog.png" alt="Create inherited process dialog." />  

Once you've defined the inherited process, you can perform these actions: 
- [Customize a project using an inherited process](customize-process.md)   
- [Create a project](#create-team-project) that uses the inherited process  
- [Change project(s) to use the inherited process](#migrate)        

> [!NOTE]
> All inherited processes and their child processes are automatically updated with any updates made to their parent system processes. Updates to processes are documented in [Changes made to process templates](../../../boards/work-items/guidance/changes-to-process-templates.md).
 

<a id="migrate"></a>


## Change the process used by a project    

You can change the process a project uses from a system process or inherited process to another inherited process. There are two mechanisms to change a projects process. The first is to switch to a process where the project is derived from the same system process. Meaning, you can move a project between processes that use the same base process like Agile or Scrum.

The second method is to migrate your project from one process model to another process model. For example, change the process model used by the project from Agile to Scrum, or Basic to Agile.

For the second method, we have provided detailed steps for three common scenarios of changing the process used by a project.

- [Scrum to Agile](./change-process-scrum-to-agile.md)
- [Agile to Scrum](./change-process-agile-to-scrum.md)
- [Basic to Agile](./change-process-basic-to-agile.md)

> [!NOTE]    
> You can change the process of a project as long as you don't have any undeleted work items of a custom work item type that isn't also defined in the target process. 
>
> Also, if you change a project to a system process or other inherited process that doesn't contain the same custom fields, data is still maintained. However, the custom fields that aren't represented in the current process won't appear on the work item form. You can still access the field data through a query or REST APIs. These fields are essentially locked from changes and appear as read-only values.  

1. Choose the process that contains the project you want to change. For example, say you want to change a project from from Agile to Scrum, then choose the **Agile** process.

   > [!div class="mx-imgBorder"]  
   > ![Screenshot of Choose the Agile process.](media/agile-to-scrum/choose-agile.png)

2. Choose **Projects**, and then choose the :::image type="icon" source="../../../media/icons/actions-icon.png" border="false"::: actions icon for the project you want to change, and select **Change process**. 

   > [!div class="mx-imgBorder"]  
   > ![Screenshot of Choose Projects tab.](media/agile-to-scrum/choose-projects-myfirstproject.png)

Follow the steps in the wizard

> [!IMPORTANT]  
> When you change a project to use an inherited process, you may find one or more Agile tools or work items appear in an invalid state. For example: 
> 
> - If you make a field required, work items with that field undefined show an error message. You'll need to resolve the errors to make additional changes and save the work item. 
> - If you add or remove/hide workflow states of a WIT that appears on the Kanban board, you'll need to update the Kanban board column configurations for all teams defined in the project. 

<a id="create-team-project">  </a>

## Create a project from a process 

1. Open the &hellip; context menu for the process you want to use and choose **New team project**.  

	::: moniker range=">= azure-devops-2020"
	> [!div class="mx-imgBorder"]  
	> ![Screenshot of Create a project from the selected process.](media/process/new-team-project-from-inherited-process-menu.png) 
	::: moniker-end
	::: moniker range="azure-devops-2019"
	> [!div class="mx-imgBorder"]  
	> ![Screenshot of Create a project from selected process, Azure DevOps Server 2019.](media/process/add-new-team-project.png) 
	::: moniker-end

2. The Create new project page opens. Fill out the form. To learn more, see [Create a project](../../projects/create-project.md).

	::: moniker range=">= azure-devops-2020"
	> [!div class="mx-imgBorder"]  
	> ![Create new project dialog.](media/process/create-test-project-sprint166.png) 
	::: moniker-end
	::: moniker range="azure-devops-2019"
	> [!div class="mx-imgBorder"]  
	> ![Create new project form dialog, Azure DevOps Server 2019.](media/process/create-test-project.png) 
	::: moniker-end

<a id="copy-process">  </a>

## Copy a process

It's a good practice to test the customizations you make before rolling out the changes to your organization.  To test your customization, you create a copy of a process, make your updates, verify the updates appear as desired, and then move projects to the new process.  
 
> [!TIP]    
> If you make a change to a process that is used by one or more projects, each project that uses the process updates immediately to the incremental process change. To bundle your process changes before you roll them out to all projects, following the  steps outlined next.

1. Create a copy of the process that you want to change. From the **Process** page, open the &hellip; context menu for the process you want to copy and choose **Copy process**.  

	> [!div class="mx-imgBorder"]  
	> ![Screenshot of selection to Make a copy of an inherited process.](media/process/copy-process.png) 

2. Fill out the form with the name of the copied process and choose **Copy process**.

	> [!div class="mx-imgBorder"]  
	> ![Copy process dialog.](media/process/copy-process-dialog.png) 
	
1. Make your changes to the copied process. Since no project is using this process, these changes do not impact any project. 

1. To verify your changes, create a test project based on the copied and updated process. If you have already created a test project, change the process of the test project using the [**Change project to use <em>ProcessName</em>**](#migrate) option from the context menu. 

1. Once you have fully tested your customizations, you're ready to roll out your changes to all projects. To roll out your changes, change the process of the projects that need the new changes. Select the [**Change project to use <em>ProcessName</em>**](#migrate) option from the context menu.  

1.  Disable or delete the original process. 
 

<a id="enable-process">  </a>

## Enable/disable a process

To prevent projects being created from a process, you disable it. You might choose this option when you want to apply several customizations and don't want the process used until they are complete. Or, you might want to retire use of a process in favor of moving  projects to a new process. 

All system processes and newly created inherited processes are enabled by default. 

- To disable or enable a process, open the &hellip; context menu for the process and choose **Disable process** or **Enable process**. 


<a id="default-process">  </a>

## Set the default process

Set an inherited process as the default to have it pre-selected for other projects you plan to create. 

To set a process as the default, open the &hellip; context menu for the inherited process and choose **Set as default process**. This option isn't available with any of the system processes. 

Project Collection Administrators can [add projects](../../projects/create-project.md) from the **Projects** page. 

## Try this next

> [!div class="nextstepaction"]
> [Add and manage fields for an inherited process](customize-process-field.md) 
> Or
> [Add and manage work item types](customize-process-work-item-type.md)


## Related articles  

- [About process customization and inherited processes](inheritance-process-model.md)
- [Customize a project using an inherited process](customize-process.md). 


<a id="process-rest-api">  </a>

### Programmatically work with processes 

You can get, create, update, and delete processes defined for an organization using the [REST API, Processes](/rest/api/azure/devops/processes/processes/list).
