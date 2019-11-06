---
title: Criteri di configurazione Guest
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Criteri di configurazione Guest
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 741a73bacadccc0ee7b06542b86b9958aa236982
ms.sourcegitcommit: 3669614902627f0ca61ee64d97621b2cfa585199
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/06/2019
ms.locfileid: "73656324"
---
# <a name="guest-configuration-policy"></a>Criteri di configurazione Guest

È possibile usare l'estensione di [configurazione Guest](https://docs.microsoft.com/azure/governance/policy/concepts/guest-configuration) di criteri di Azure per controllare le impostazioni di configurazione in una macchina virtuale. La configurazione Guest è attualmente supportata solo nelle VM di Azure.

Per trovare l'elenco dei criteri di configurazione Guest, cercare "configurazione Guest" nella pagina del portale di criteri di Azure. In alternativa, eseguire questo cmdlet in una finestra di PowerShell per trovare l'elenco:

```powershell
Get-AzPolicySetDefinition | where-object {$_.Properties.metadata.category -eq "Guest Configuration"}
```

> [!NOTE]
> La funzionalità di configurazione Guest viene aggiornata regolarmente per supportare set di criteri aggiuntivi. Verificare periodicamente la presenza di nuovi criteri supportati e valutare se saranno utili.

<!-- TODO: Update these links when available. 

By default, we recommend that you enable the following policies:

- [Preview]: Audit to verify that password-security settings are correct on Linux and Windows machines.
- Audit to verify that certificates are not nearing expiration on Windows VMs.

-->

## <a name="deployment"></a>Distribuzione

Usare lo script di PowerShell di esempio seguente per distribuire questi criteri in:

- Verificare che le impostazioni di sicurezza delle password nei computer Windows e Linux siano impostate correttamente.
- Verificare che i certificati non siano prossimi alla scadenza nelle macchine virtuali Windows.

 Prima di eseguire questo script, usare il cmdlet [Connect-AzAccount](https://docs.microsoft.com/powershell/module/az.accounts/connect-azaccount?view=azps-2.1.0) per accedere. Quando si esegue lo script, è necessario specificare il nome della sottoscrizione a cui si desidera applicare i criteri.

```powershell

    #Assign Guest Configuration policy.
    param (
        [Parameter(Mandatory=$true)]
        [string]$SubscriptionName
    )

    $Subscription = Get-AzSubscription -SubscriptionName $SubscriptionName
    $scope = "/subscriptions/" + $Subscription.Id

    $PasswordPolicy = Get-AzPolicySetDefinition -Name "3fa7cbf5-c0a4-4a59-85a5-cca4d996d5a6"
    $CertExpirePolicy = Get-AzPolicySetDefinition -Name "b6f5e05c-0aaa-4337-8dd4-357c399d12ae"

    New-AzPolicyAssignment -Name "PasswordPolicy" -DisplayName "[Preview]: Audit that password security settings are set correctly inside Linux and Windows machines" -Scope $scope -PolicySetDefinition $PasswordPolicy -AssignIdentity -Location eastus

    New-AzPolicyAssignment -Name "CertExpirePolicy" -DisplayName "[Preview]: Audit that certificates are not expiring on Windows VMs" -Scope $scope -PolicySetDefinition $CertExpirePolicy -AssignIdentity -Location eastus

```

## <a name="next-steps"></a>Passaggi successivi

Informazioni su come [abilitare il rilevamento delle modifiche e gli avvisi](./enable-tracking-alerting.md) per le modifiche critiche al file, al servizio, al software e al registro di sistema.

> [!div class="nextstepaction"]
> [Abilita rilevamento e avvisi per le modifiche critiche](./enable-tracking-alerting.md)
