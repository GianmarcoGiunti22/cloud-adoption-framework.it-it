---
title: Automatizzare l'onboarding e la configurazione degli avvisi
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Automatizzare l'onboarding e la configurazione degli avvisi
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: a3a1ae1f49fea514ce2ab194f7e959e428b37ad6
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71027788"
---
# <a name="automate-onboarding"></a>Automatizzare il caricamento

Per migliorare l'efficienza della distribuzione dei servizi di gestione del server di Azure, è consigliabile automatizzare la distribuzione dei servizi di gestione usando i consigli descritti nelle sezioni precedenti di questa guida. Lo script e i modelli di esempio forniti nelle sezioni seguenti sono punti di partenza per lo sviluppo di un'automazione dei processi di onboarding.

## <a name="onboarding-by-using-automation"></a>Onboarding tramite automazione

Questa guida include un repository GitHub di esempio di codice di esempio, [CloudAdoptionFramework](https://aka.ms/CAF/manage/automation-samples), che fornisce script di esempio e modelli di Azure Resource Manager che consentono di automatizzare la distribuzione dei servizi di gestione del server di Azure.

Questi file di esempio illustrano come usare i cmdlet di Azure PowerShell per automatizzare le attività seguenti:

1. Creare un' [area di lavoro log Analytics](https://docs.microsoft.com/azure/azure-monitor/platform/manage-access) (oppure usare un'area di lavoro esistente se&mdash;soddisfa i requisiti, vedere [pianificazione dell'area di lavoro](./prerequisites.md#log-analytics-workspace-and-automation-account-planning)).

2. Creare un account di automazione (oppure usare un account esistente se soddisfa i requisiti&mdash;vedere [pianificazione dell'area di lavoro](./prerequisites.md#log-analytics-workspace-and-automation-account-planning)).

3. Collegare l'account di automazione e l'area di lavoro Log Analytics (non necessario se si sta caricando tramite il portale).

4. Abilitare Gestione aggiornamenti e Rilevamento modifiche e l'inventario per l'area di lavoro.

5. Caricare le macchine virtuali di Azure con criteri di Azure. un criterio consente di installare l'agente Log Analytics e Dependency Agent nelle VM di Azure.

6. Eseguire l'onboarding dei server locali installando l'agente di Log Analytics su di essi.

In questo esempio vengono usati i file descritti nella tabella seguente ed è possibile personalizzarli in modo da supportare scenari di distribuzione personalizzati.

| Nome file | DESCRIZIONE |
|-----------|-------------|
| New-AMSDeployment.ps1 | Script di orchestrazione principale che automatizza l'onboarding. Questo script di PowerShell richiede una sottoscrizione esistente, ma creerà gruppi di risorse, percorso, area di lavoro e account di automazione, se non esistono. |
| Workspace-AutomationAccount.json | Modello di Gestione risorse che distribuisce l'area di lavoro e le risorse dell'account di automazione. |
| WorkspaceSolutions.json | Un modello di Gestione risorse che Abilita le soluzioni desiderate nell'area di lavoro Log Analytics. |
| ScopeConfig.json | Modello di Gestione risorse che usa il modello di consenso esplicito per i server locali con la soluzione di rilevamento delle modifiche. L'uso del modello di consenso esplicito è facoltativo. |
| Enable-VMInsightsPerfCounters.ps1 | Uno script di PowerShell che Abilita VMInsight per i server e configura i contatori delle prestazioni. |
| ChangeTracking-Filelist.json | Modello di Gestione risorse che definisce l'elenco dei file che verranno monitorati da Rilevamento modifiche. |

È possibile eseguire New-AMSDeployment. ps1 usando il comando seguente:

```powershell
.\New-AMSDeployment.ps1 -SubscriptionName '{Subscription Name}' -WorkspaceName '{Workspace Name}' -WorkspaceLocation '{Azure Location}' -AutomationAccountName {Account Name} -AutomationAccountLocation {Account Location}
```

## <a name="next-steps"></a>Passaggi successivi

Informazioni su come configurare gli avvisi di base per notificare al team gli eventi e i problemi di gestione delle chiavi.

> [!div class="nextstepaction"]
> [Impostazione degli avvisi di base](./setup-alerts.md)
