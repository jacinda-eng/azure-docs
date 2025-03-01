---
title: Create a standalone Azure Automation account
description: This article tells how to create a standalone Azure Automation account.
services: automation
ms.subservice: process-automation
ms.date: 10/26/2021
ms.topic: conceptual
---
# Create a standalone Azure Automation account

This article shows you how to create an Azure Automation account using the Azure portal. You can use the Automation account to evaluate and learn about Automation without using additional management features or integrating with Azure Monitor Logs. You can add management features or integrate with Azure Monitor Logs for advanced monitoring of runbook jobs at any point in the future.

With an Automation account, you can authenticate runbooks by managing resources in either Azure Resource Manager or the classic deployment model. One Automation Account can manage resources across all regions and subscriptions for a given tenant.

With this account created for you, you can quickly start building and deploying runbooks to support your automation needs.

## Permissions required to create an Automation account

To create or update an Automation account, and to complete the tasks described in this article, you must have the following privileges and permissions:

To create an Automation account, your Azure AD user account must be added to a role with permissions equivalent to the Owner role for `Microsoft.Automation` resources. For more information, see [Role-Based Access Control in Azure Automation](automation-role-based-access-control.md).

## Create a new Automation account in the Azure portal

To create an Azure Automation account in the Azure portal, complete the following steps:

1. Sign in to the Azure portal with an account that's a member of the subscription Administrators role and a Co-Administrator of the subscription.
1. Select **+ Create a Resource**.
1. Search for **Automation**. In the search results, select **Automation**.

   :::image type="content" source="./media/automation-create-standalone-account/automation-account-portal.png" alt-text="Locating Automation accounts in portal":::

Options for your new Automation account are organized into tabs in the **Create an Automation Account** page. The following sections describe each of the tabs and their options.

### Basics

On the **Basics** tab, provide the essential information for your Automation account. After you complete the **Basics** tab, you can choose to further customize your new Automation account by setting options on the other tabs, or you can select **Review + create** to accept the default options and proceed to validate and create the account.

> [!NOTE]
> By default, a system-assigned managed identity is enabled for the Automation account.

The following table describes the fields on the **Basics** tab.

| **Field** | **Required**<br> **or**<br> **optional** |**Description** |
|---|---|---|
|Subscription|Required |From the drop-down list, select the Azure subscription for the account.|
|Resource group|Required |From the drop-down list, select your existing resource group, or select **Create new**.|
|Automation account name|Required |Enter a name unique for it's location and resource group. Names for Automation accounts that have been deleted might not be immediately available. You can't change the account name once it has been entered in the user interface. |
|Region|Required |From the drop-down list, select a region for the account. For an updated list of locations that you can deploy an Automation account to, see [Products available by region](https://azure.microsoft.com/global-infrastructure/services/?products=automation&regions=all).|

The following image shows a standard configuration for a new Automation account.

:::image type="content" source="./media/automation-create-standalone-account/create-account-basics.png" alt-text="Required fields for creating the Automation account on Basics tab":::

### Advanced

On the **Advanced** tab, you can configure the managed identity option for your new Automation account. The user-assigned managed identity option can also be configured after the Automation account is created.

For instructions on how to create a user-assigned managed identity, see [Create a user-assigned managed identity](../active-directory/managed-identities-azure-resources/how-to-manage-ua-identity-portal.md#create-a-user-assigned-managed-identity).

The following table describes the fields on the **Advanced** tab.

| **Field** | **Required**<br> **or**<br> **optional** |**Description** |
|---|---|---|
|System-assigned |Optional |An Azure Active Directory identity that is tied to the lifecycle of the Automation account. |
|User-assigned |Optional |A managed identity represented as a standalone Azure resource that is managed separately from the resources that use it.|

You can chose to enable managed identities later, and the Automation account is created without one. To enable a managed identity after the account is created, see [Enable managed identity](enable-managed-identity-for-automation.md). If you select both options, for the user-assigned identity, select the **Add user assigned identities** option. On the **Select user assigned managed identity** page, select a subscription and add one or more user-assigned identities created in that subscription to assign to the Automation account.

The following image shows a standard configuration for a new Automation account.

:::image type="content" source="./media/automation-create-standalone-account/create-account-advanced.png" alt-text="Required fields for creating the Automation account on Advanced tab":::

### Tags tab

On the **Tags** tab, you can specify Resource Manager tags to help organize your Azure resources. For more information, see [Tag resources, resource groups, and subscriptions for logical organization](../azure-resource-manager/management/tag-resources.md).

### Review + create tab

When you navigate to the **Review + create** tab, Azure runs validation on the Automation account settings that you have chosen. If validation passes, you can proceed to create the Automation account.

If validation fails, then the portal indicates which settings need to be modified.

Review your new Automation account.

:::image type="content" source="./media/automation-create-standalone-account/automation-account-overview.png" alt-text="Automation account overview page":::

When the Automation account is successfully created, several resources are automatically created for you. After creation, these runbooks can be safely deleted if you do not wish to keep them. The managed identities can be used to authenticate to your account in a runbook, and should be left unless you create another one or do not require them. The following table summarizes resources for the account.

|Resource |Description |
|------||------|
|AzureAutomationTutorial Runbook |An example graphical runbook that demonstrates how to authenticate by using a Run As account. The runbook gets all Resource Manager resources. |
|AzureAutomationTutorialScript |An example PowerShell runbook that demonstrates how to authenticate by using a Run As account. The runbook gets all Resource Manager resources.|
|AzureAutomationTutorialPython2Runbook |An example Python runbook that demonstrates how to authenticate by using a Run As account. The runbook lists all resource groups present in the subscription.|

> [!NOTE]
> The tutorial runbooks have not been updated to authenticate using a managed identity. Review the [Using system-assigned identity](enable-managed-identity-for-automation.md#assign-role-to-a-system-assigned-managed-identity) or [Using user-assigned identity](add-user-assigned-identity.md#assign-a-role-to-a-user-assigned-managed-identity) to learn how to grant the managed identity access to resources and configure your runbooks to authenticate using either type of managed identity.

## Next steps

* To get started with PowerShell runbooks, see [Tutorial: Create a PowerShell runbook](./learn/powershell-runbook-managed-identity.md).
* To get started with PowerShell Workflow runbooks, see [Tutorial: Create a PowerShell workflow runbook](learn/automation-tutorial-runbook-textual.md).
* To get started with Python 3 runbooks, see [Tutorial: Create a Python 3 runbook](learn/automation-tutorial-runbook-textual-python-3.md).
* For a PowerShell cmdlet reference, see [Az.Automation](/powershell/module/az.automation).