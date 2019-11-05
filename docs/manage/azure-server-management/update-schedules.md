---
title: Creare pianificazioni degli aggiornamenti
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Creare pianificazioni degli aggiornamenti
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 5bb3e37073c3c5d7f401f6d6c706314172eecf88
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565257"
---
# <a name="create-update-schedules"></a>Creare pianificazioni degli aggiornamenti

È possibile gestire le pianificazioni degli aggiornamenti usando il portale di Azure o i nuovi moduli dei cmdlet di PowerShell.

Per creare una pianificazione degli aggiornamenti tramite la portale di Azure, vedere [pianificare una distribuzione degli aggiornamenti](https://docs.microsoft.com/azure/automation/automation-tutorial-update-management#schedule-an-update-deployment).

Il modulo AZ. Automation supporta ora la configurazione della gestione degli aggiornamenti tramite Azure PowerShell. La [versione 1.7.0](https://www.powershellgallery.com/packages/Az/1.7.0) del modulo aggiunge il supporto per il cmdlet [New-AzAutomationUpdateManagementAzureQuery](https://docs.microsoft.com/powershell/module/az.automation/new-azautomationupdatemanagementazurequery?view=azps-1.7.0) . Questo cmdlet consente di usare tag, percorso e ricerche salvate per configurare le pianificazioni degli aggiornamenti per un gruppo di computer flessibile.

## <a name="example-script"></a>Script di esempio

Lo script di esempio in questa sezione illustra l'uso di tag e query per creare gruppi dinamici di computer a cui è possibile applicare le pianificazioni degli aggiornamenti. Esegue le azioni seguenti. Quando si creano script personalizzati, è possibile fare riferimento alle implementazioni delle azioni specifiche.

- Crea una pianificazione di aggiornamento di automazione di Azure che viene eseguita ogni sabato alle 8:00 AM.
- Crea una query per i computer che soddisfano i criteri seguenti:
  - Distribuito in `westus`, `eastus`o `eastus2` percorso di Azure
  - È possibile applicare un tag `Owner` con un valore impostato su `JaneSmith`
  - È possibile applicare un tag di `Production` con un valore impostato su `true`
- Applica la pianificazione dell'aggiornamento ai computer sottoposti a query e imposta una finestra di aggiornamento di due ore.

Prima di eseguire lo script di esempio, è necessario accedere usando il cmdlet [Connect-AzAccount](https://docs.microsoft.com/powershell/module/az.accounts/connect-azaccount?view=azps-2.1.0) . Quando si avvia lo script, fornire le seguenti informazioni:

- ID sottoscrizione di destinazione
- Gruppo di risorse di destinazione
- Nome dell'area di lavoro Log Analytics
- Nome dell'account di automazione di Azure

```powershell

    <#
        .SYNOPSIS
            This script orchestrates the deployment of the solutions and the agents.
        .Parameter SubscriptionName
        .Parameter WorkspaceName
        .Parameter AutomationAccountName
        .Parameter ResourceGroupName

    #>

    param (
        [Parameter(Mandatory=$true)]
        [string]$SubscriptionId,

        [Parameter(Mandatory=$true)]
        [string]$ResourceGroupName,

        [Parameter(Mandatory=$true)]
        [string]$WorkspaceName,

        [Parameter(Mandatory=$true)]
        [string]$AutomationAccountName,

        [Parameter(Mandatory=$false)]
        [string]$scheduleName = "SaturdayCritialSecurity"
    )

    Import-Module Az.Automation

    $startTime = ([DateTime]::Now).AddMinutes(10)
    $schedule = New-AzAutomationSchedule -ResourceGroupName $ResourceGroupName `
        -AutomationAccountName $AutomationAccountName `
        -StartTime $startTime `
        -Name $scheduleName `
        -Description "Saturday patches" `
        -DaysOfWeek Saturday `
        -WeekInterval 1 `
        -ForUpdateConfiguration

    # Using AzAutomationUpdateManagementAzureQuery to create dynamic groups.

    $queryScope = @("/subscriptions/$SubscriptionID/resourceGroups/")

    $query1Location =@("westus", "eastus", "eastus2")
    $query1FilterOperator = "Any"
    $ownerTag = @{"Owner"= @("JaneSmith")}
    $ownerTag.add("Production", "true")

    $DGQuery = New-AzAutomationUpdateManagementAzureQuery -ResourceGroupName $ResourceGroupName `
        -AutomationAccountName $AutomationAccountName `
        -Scope $queryScope `
        -Tag $ownerTag

    $AzureQueries = @($DGQuery)

    $UpdateConfig = New-AzAutomationSoftwareUpdateConfiguration -ResourceGroupName $ResourceGroupName `
        -AutomationAccountName $AutomationAccountName `
        -Schedule $schedule `
        -Windows `
        -Duration (New-TimeSpan -Hours 2) `
        -AzureQuery $AzureQueries `
        -IncludedUpdateClassification Security,Critical
```

## <a name="next-steps"></a>Passaggi successivi

Vedere esempi di come implementare [criteri comuni in Azure](./common-policies.md) che consentono di gestire i server.

> [!div class="nextstepaction"]
> [Criteri comuni in Azure](./common-policies.md)
