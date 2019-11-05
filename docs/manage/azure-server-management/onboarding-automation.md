---
title: Automatizzare il caricamento
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Automatizzare il caricamento
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: f5dd418a03dd35ebced1a9c73eb8fe6567339859
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565401"
---
# <a name="automate-onboarding"></a>Automatizzare il caricamento

Per migliorare l'efficienza della distribuzione dei servizi di gestione del server di Azure, è consigliabile automatizzare la distribuzione come descritto nelle sezioni precedenti di questa guida. Lo script e i modelli di esempio forniti nelle sezioni seguenti sono punti di partenza per lo sviluppo di un'automazione personalizzata dei processi di onboarding.

Questa guida include un repository GitHub di supporto per il codice di esempio [CloudAdoptionFramework](https://aka.ms/caf/manage/automation-samples). Il repository fornisce script di esempio e modelli di Azure Resource Manager che consentono di automatizzare la distribuzione dei servizi di gestione del server di Azure.

Nei file di esempio viene illustrato come utilizzare i cmdlet di Azure PowerShell per automatizzare le attività seguenti:

- Creare un' [area di lavoro log Analytics](https://docs.microsoft.com/azure/azure-monitor/platform/manage-access). In alternativa, usare un'area di lavoro esistente se soddisfa i requisiti. Per informazioni dettagliate, vedere [pianificazione dell'area di lavoro](./prerequisites.md#log-analytics-workspace-and-automation-account-planning).

- Creare un account di automazione. In alternativa, usare un account esistente se soddisfa i requisiti. Per informazioni dettagliate, vedere [pianificazione dell'area di lavoro](./prerequisites.md#log-analytics-workspace-and-automation-account-planning).

- Collegare l'account di automazione e l'area di lavoro Log Analytics. Questo passaggio non è necessario se si sta eseguendo l'onboarding usando il portale di Azure.

- Abilitare Gestione aggiornamenti e Rilevamento modifiche e l'inventario per l'area di lavoro.

- Caricare le macchine virtuali di Azure usando criteri di Azure. Un criterio consente di installare l'agente Log Analytics e il Microsoft Dependency Agent nelle VM di Azure.

- Eseguire l'onboarding dei server locali installando l'agente di Log Analytics su di essi.

In questo esempio vengono utilizzati i file descritti nella tabella seguente. È possibile personalizzarli per supportare scenari di distribuzione personalizzati.

| Nome file | Descrizione |
|-----------|-------------|
| New-AMSDeployment. ps1 | Script di orchestrazione principale che automatizza l'onboarding. Viene creato un gruppo di risorse, un percorso, un'area di lavoro e gli account di automazione, se non esistono già. Questo script di PowerShell richiede una sottoscrizione esistente. |
| Area di lavoro-AutomationAccount. JSON | Modello di Gestione risorse che distribuisce l'area di lavoro e le risorse dell'account di automazione. |
| WorkspaceSolutions. JSON | Un modello di Gestione risorse che Abilita le soluzioni desiderate nell'area di lavoro Log Analytics. |
| ScopeConfig. JSON | Un modello di Gestione risorse che usa il modello di consenso esplicito per i server locali con la soluzione Rilevamento modifiche. L'uso del modello di consenso esplicito è facoltativo. |
| Enable-VMInsightsPerfCounters. ps1 | Uno script di PowerShell che Abilita VM Insights per i server e configura i contatori delle prestazioni. |
| Rilevamento modifiche-filefile. JSON | Modello di Gestione risorse che definisce l'elenco dei file che verranno monitorati da Rilevamento modifiche. |

Usare il comando seguente per eseguire New-AMSDeployment. ps1:

```powershell
.\New-AMSDeployment.ps1 -SubscriptionName '{Subscription Name}' -WorkspaceName '{Workspace Name}' -WorkspaceLocation '{Azure Location}' -AutomationAccountName {Account Name} -AutomationAccountLocation {Account Location}
```

## <a name="next-steps"></a>Passaggi successivi

Informazioni su come configurare gli avvisi di base per notificare al team gli eventi e i problemi di gestione delle chiavi.

> [!div class="nextstepaction"]
> [Configurare gli avvisi di base](./setup-alerts.md)
