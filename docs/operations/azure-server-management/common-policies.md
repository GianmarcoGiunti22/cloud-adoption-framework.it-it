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
ms.openlocfilehash: 40849abab5616343ae49400a126e2d1cf4c0a34f
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70833258"
---
# <a name="common-azure-policy-examples"></a>Esempi comuni di criteri di Azure

I [criteri di Azure](https://docs.microsoft.com/azure/governance/policy/overview) consentono di applicare la governance alle risorse cloud. Questo servizio può essere utile per creare Guardrails che garantiscano la conformità a livello aziendale ai requisiti dei criteri di governance. Per creare i criteri, usare il portale di Azure o i cmdlet di PowerShell. Questo articolo fornisce esempi di cmdlet di PowerShell.

> [!NOTE]
> Con criteri di Azure, i criteri di imposizione (**deployIfNotExists**) non vengono distribuiti automaticamente nelle macchine virtuali esistenti. La correzione è necessaria per assicurare la conformità di queste macchine virtuali. Per altre informazioni, vedere [correggere le risorse non conformi con i criteri di Azure](https://docs.microsoft.com/en-us/azure/governance/policy/how-to/remediate-resources).

## <a name="common-policy-examples"></a>Esempi di criteri comuni

Nelle sezioni seguenti vengono descritti alcuni criteri di uso comune.

### <a name="restrict-resource-regions"></a>Limitare le aree delle risorse

La conformità alle normative e ai criteri dipende spesso dal controllo della posizione fisica in cui vengono distribuite le risorse. È possibile usare un criterio predefinito per consentire agli utenti di creare risorse solo nelle aree di Azure incluse nell'elenco elementi consentiti. È possibile trovare questi criteri nel portale cercando "location" nella pagina di definizione dei criteri.

In alternativa, è possibile eseguire questo cmdlet per trovare i criteri:

```powershell
Get-AzPolicyDefinition | Where-Object { ($_.Properties.policyType -eq "BuiltIn") -and ($_.Properties.displayName -like "*location*") }
```

Nello script seguente viene illustrato come assegnare i criteri. Per usare lo script, modificare il `$SubscriptionID` valore in modo che punti alla sottoscrizione a cui si vuole assegnare il criterio. Prima di eseguire lo script, è necessario eseguire l'accesso usando il cmdlet [Connect-AzAccount](https://docs.microsoft.com/powershell/module/az.accounts/connect-azaccount?view=azps-2.1.0) .

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

È possibile usare lo stesso script per applicare gli altri criteri descritti in questo articolo. È sufficiente sostituire il GUID nella riga che imposta `$AllowedLocationPolicy` con il GUID del criterio che si desidera applicare.

### <a name="block-certain-resource-types"></a>Blocca determinati tipi di risorse

Un altro criterio incorporato comune usato per controllare i costi consente di bloccare determinati tipi di risorse. È possibile trovare questi criteri nel portale cercando "tipi di risorse consentiti" nella pagina Definizione criterio.

In alternativa, è possibile eseguire questo cmdlet per trovare i criteri:

```powershell
Get-AzPolicyDefinition | Where-Object { ($_.Properties.policyType -eq "BuiltIn") -and ($_.Properties.displayName -like "*allowed resource types") }
```

Dopo aver identificato il criterio che si vuole usare, è possibile modificare l'esempio di PowerShell nella sezione [limitare le aree delle risorse](#restrict-resource-regions) per assegnare il criterio.

### <a name="restrict-vm-size"></a>Limitare le dimensioni della macchina virtuale

Azure offre un'ampia gamma di dimensioni di VM per supportare diversi tipi di carichi di lavoro. Per controllare il budget, è possibile creare un criterio che consenta solo un subset di dimensioni di VM nelle sottoscrizioni.

### <a name="deploy-antimalware"></a>Distribuisci antimalware

È possibile usare questo criterio per distribuire un'estensione Microsoft IaaSAntimalware con una configurazione predefinita per le macchine virtuali che non sono protette da antimalware.

Il GUID del criterio `2835b622-407b-4114-9198-6f7064cbe0dc`è.

Nello script seguente viene illustrato come assegnare i criteri. Per usare lo script, modificare il `$SubscriptionID` valore in modo che punti alla sottoscrizione a cui si vuole assegnare il criterio. Prima di eseguire lo script, è necessario eseguire l'accesso usando il cmdlet [Connect-AzAccount](https://docs.microsoft.com/powershell/module/az.accounts/connect-azaccount?view=azps-2.1.0) .

```powershell
#Specify the value for $SubscriptionID.
$SubscriptionID = <subscription ID>
$scope = "/subscriptions/$SubscriptionID"

$AntimalwarePolicy = Get-AzPolicyDefinition -Name "2835b622-407b-4114-9198-6f7064cbe0dc"

#Replace location “eastus” with the value you want to use.
New-AzPolicyAssignment -Name "Deploy Antimalware" -DisplayName "Deploy default Microsoft IaaSAntimalware extension for Windows Server" -Scope $scope -PolicyDefinition $AntimalwarePolicy -Location eastus –AssignIdentity

```

## <a name="next-steps"></a>Passaggi successivi

Informazioni sugli altri strumenti e servizi di gestione server disponibili.

> [!div class="nextstepaction"]
> [Strumenti e servizi di gestione del server di Azure](./tools-services.md)
