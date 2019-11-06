---
title: Esempi comuni di criteri di Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Esempi comuni di criteri di Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 7008809ef2e80cd5f1c263b705b46a37b6028482
ms.sourcegitcommit: 3669614902627f0ca61ee64d97621b2cfa585199
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/06/2019
ms.locfileid: "73656413"
---
# <a name="common-azure-policy-examples"></a>Esempi comuni di criteri di Azure

I [criteri di Azure](https://docs.microsoft.com/azure/governance/policy/overview) consentono di applicare la governance alle risorse cloud. Questo servizio può essere utile per creare Guardrails che garantiscano la conformità a livello aziendale ai requisiti dei criteri di governance. Per creare i criteri, usare il portale di Azure o i cmdlet di PowerShell. Questo articolo fornisce esempi di cmdlet di PowerShell.

> [!NOTE]
> Con criteri di Azure, i criteri di imposizione (**deployIfNotExists**) non vengono distribuiti automaticamente nelle macchine virtuali esistenti. La correzione è necessaria per assicurare la conformità delle VM. Per altre informazioni, vedere monitorare e [aggiornare le risorse non conformi con criteri di Azure](https://docs.microsoft.com/azure/governance/policy/how-to/remediate-resources).

## <a name="common-policy-examples"></a>Esempi di criteri comuni

Nelle sezioni seguenti vengono descritti alcuni criteri di uso comune.

### <a name="restrict-resource-regions"></a>Limitare le aree delle risorse

La conformità alle normative e ai criteri dipende spesso dal controllo della posizione fisica in cui vengono distribuite le risorse. È possibile usare un criterio predefinito per consentire agli utenti di creare risorse solo in determinate aree di Azure consentite.

Per trovare questi criteri nel portale, cercare "location" nella pagina di definizione dei criteri. In alternativa, eseguire questo cmdlet per trovare i criteri:

```powershell
Get-AzPolicyDefinition | Where-Object { ($_.Properties.policyType -eq "BuiltIn") -and ($_.Properties.displayName -like "*location*") }
```

Nello script seguente viene illustrato come assegnare i criteri. Modificare il valore di `$SubscriptionID` in modo che punti alla sottoscrizione a cui si desidera assegnare il criterio. Prima di eseguire lo script, usare il cmdlet [Connect-AzAccount](https://docs.microsoft.com/powershell/module/az.accounts/connect-azaccount?view=azps-2.1.0) per accedere.

```powershell
#Specify the value for $SubscriptionID.
$SubscriptionID = <subscription ID>
$scope = "/subscriptions/$SubscriptionID"

#Replace the -Name GUID with the policy GUID you want to assign.
$AllowedLocationPolicy = Get-AzPolicyDefinition -Name "e56962a6-4747-49cd-b67b-bf8b01975c4c"

#Replace the locations with the ones you want to specify.
$policyParam = '{"listOfAllowedLocations":{"value":["eastus","westus"]}}'
New-AzPolicyAssignment -Name "Allowed Location" -DisplayName "Allowed locations for resource creation" -Scope $scope -PolicyDefinition $AllowedLocationPolicy -Location eastus -PolicyParameter $policyparam
```

È anche possibile usare questo script per applicare gli altri criteri descritti in questo articolo. È sufficiente sostituire il GUID nella riga che imposta `$AllowedLocationPolicy` con il GUID del criterio che si desidera applicare.

### <a name="block-certain-resource-types"></a>Blocca determinati tipi di risorse

Un altro criterio incorporato comune usato per controllare i costi può essere usato anche per bloccare determinati tipi di risorse.

Per trovare questi criteri nel portale, cercare "tipi di risorse consentiti" nella pagina Definizione criterio. In alternativa, eseguire questo cmdlet per trovare i criteri:

```powershell
Get-AzPolicyDefinition | Where-Object { ($_.Properties.policyType -eq "BuiltIn") -and ($_.Properties.displayName -like "*allowed resource types") }
```

Dopo aver identificato il criterio che si vuole usare, è possibile modificare l'esempio di PowerShell nella sezione [limitare le aree delle risorse](#restrict-resource-regions) per assegnare il criterio.

### <a name="restrict-vm-size"></a>Limitare le dimensioni della macchina virtuale

Azure offre un'ampia gamma di dimensioni di VM per supportare vari carichi di lavoro. Per controllare il budget, è possibile creare un criterio che consenta solo un subset di dimensioni di VM nelle sottoscrizioni.

### <a name="deploy-antimalware"></a>Distribuisci antimalware

È possibile usare questo criterio per distribuire un'estensione Microsoft *IaaSAntimalware* con una configurazione predefinita per le macchine virtuali che non sono protette da antimalware.

Il GUID del criterio è `2835b622-407b-4114-9198-6f7064cbe0dc`.

Nello script seguente viene illustrato come assegnare i criteri. Per utilizzare lo script, modificare il valore di `$SubscriptionID` in modo che punti alla sottoscrizione a cui si desidera assegnare il criterio. Prima di eseguire lo script, usare il cmdlet [Connect-AzAccount](https://docs.microsoft.com/powershell/module/az.accounts/connect-azaccount?view=azps-2.1.0) per accedere.

```powershell
#Specify the value for $SubscriptionID.
$SubscriptionID = <subscription ID>
$scope = "/subscriptions/$SubscriptionID"

$AntimalwarePolicy = Get-AzPolicyDefinition -Name "2835b622-407b-4114-9198-6f7064cbe0dc"

#Replace location “eastus” with the value that you want to use.
New-AzPolicyAssignment -Name "Deploy Antimalware" -DisplayName "Deploy default Microsoft IaaSAntimalware extension for Windows Server" -Scope $scope -PolicyDefinition $AntimalwarePolicy -Location eastus –AssignIdentity

```

## <a name="next-steps"></a>Passaggi successivi

Informazioni sugli altri strumenti e servizi di gestione server disponibili.

> [!div class="nextstepaction"]
> [Strumenti e servizi di gestione del server di Azure](./tools-services.md)
