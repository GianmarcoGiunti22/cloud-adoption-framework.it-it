---
title: Strumenti di coerenza delle risorse in Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Strumenti di coerenza delle risorse in Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: a09e4748dd805757d9f78e8dd927737ca9a91f7f
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71222935"
---
# <a name="resource-consistency-tools-in-azure"></a>Strumenti di coerenza delle risorse in Azure

La [Coerenza delle risorse](./index.md) è una delle [cinque discipline della governance del cloud](../governance-disciplines.md). Questa disciplina riguarda le modalità di definizione dei criteri di gestione operativa di ambienti, applicazioni o carichi di lavoro. All'interno delle cinque discipline della governance del cloud, la disciplina della coerenza delle risorse implica il monitoraggio delle prestazioni dell'applicazione, del carico di lavoro e degli asset. Sono inoltre incluse le attività necessarie per soddisfare le esigenze di scalabilità, correggere le violazioni dei contratti di lavoro delle prestazioni ed evitare in modo proattivo le violazioni dei contratti di prestazioni tramite la correzione automatica.

Di seguito è riportato un elenco di strumenti di Azure che possono consentire di sviluppare i criteri e i processi che supportano la disciplina di governance.

| Tool | [Portale di Azure](https://azure.microsoft.com/features/azure-portal)  | [Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview)  | [Azure Blueprint](https://docs.microsoft.com/azure/governance/blueprints/overview) | [Automazione di Azure](https://docs.microsoft.com/azure/automation/automation-intro) | [Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis) | [Backup di Azure](https://docs.microsoft.com/azure/backup/backup-introduction-to-azure-backup) | [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) |
|---------|---------|---------|---------|---------|---------|---------|---------|
| Distribuire le risorse                             | Yes | Yes | Yes | Sì | No  | No | No |
| Gestisci risorse                             | Yes | Yes | Yes | Sì | No  | No | No |
| Implementare le risorse tramite modelli             | No  | Yes | No  | Yes | No  | No | No |
| Distribuire l'ambiente orchestrato          | No  | No  | Yes | No  | No  | No | No |
| Definire gruppi di risorse                       | Yes | Yes | Sì | No  | No  | No | No |
| Gestire i proprietari dell'account e i carichi di lavoro           | Yes | Yes | Sì | No  | No  | No | No |
| Gestire le risorse di accesso condizionale       | Yes | Yes | Sì | No  | No  | No | No |
| Configurare gli utenti per il controllo degli accessi in base al ruolo                         | Yes | No  | No  | No  | Yes | No | No |
| Assegnare autorizzazioni e ruoli per le risorse | Yes | Yes | Sì | No  | Yes | No | No |
| Definire le dipendenze tra le risorse        | No  | Yes | Sì | No  | No  | No | No |
| Applicare il controllo di accesso                         | Yes | Yes | Sì | No  | Yes | No | No |
| Valutare la disponibilità e la scalabilità          | No  | No  | No  | Yes | No  | No | No |
| Applicare tag alle risorse                      | Yes | Yes | Sì | No  | No  | No | No |
| Assegnare regole di Criteri in Azure                    | Yes | Yes | Sì | No  | No  | No | No |
| Applicare la correzione automatizzata                  | No  | No  | No  | Yes | No  | No | No |
| Gestisci la fatturazione                               | Yes | No  | No  | No  | No  | No | No |
| Pianificare le risorse per il ripristino di emergenza         | Yes | Yes | Sì | No  | No  | Yes | Yes |
|Ripristinare i dati durante un'interruzione o una violazione del contratto di servizio     | No | No  | No  | No  | No  | Yes | Yes |
|Ripristinare le applicazioni durante un'interruzione o una violazione del contratto di servizio     | No | No  | No  | No  | No  | Yes | Yes |

Oltre a questi strumenti di funzionalità e coerenza delle risorse, è necessario monitorare le risorse implementate per le prestazioni e i problemi di integrità. [Monitoraggio di Azure](https://docs.microsoft.com/azure/azure-monitor/overview) è l'impostazione predefinita per il monitoraggio e il reporting relativi alle soluzioni in Azure. Monitoraggio di Azure offre funzionalità per il monitoraggio delle risorse cloud. Questo elenco Mostra la funzionalità che soddisfa i requisiti di monitoraggio più comuni.

| Tool | [Portale di Azure](https://azure.microsoft.com/features/azure-portal) | [Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview) | [Log Analytics](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview) | [API REST di Monitoraggio di Azure](https://docs.microsoft.com/rest/api/monitor) |
|----------------------------------------------------|--------------|----------------------|---------------|------------------------|
| Dati di telemetria di macchine virtuali log                 | No           | No                   | Yes           | No                     |
| Dati di telemetria di reti virtuali log              | No           | No                   | Yes           | No                     |
| Dati di telemetria di servizi PaaS di log                   | No           | No                   | Yes           | No                     |
| Dati di telemetria per applicazioni log                     | No           | Yes                  | No            | No                     |
| Configurare report e avvisi                       | Yes          | No                   | No            | Yes                    |
| Pianificare report a intervalli regolari o analisi personalizzate        | No           | No                   | No            | No                     |
| Visualizzare e analizzare i dati di prestazioni e log     | Yes          | No                   | No            | No                     |
| Integrare una soluzione di monitoraggio locale o di terze parti     | No           | No                   | No            | Yes                    |

Quando si pianifica la distribuzione, si dovrà considerare dove sono archiviati i dati di registrazione e come si desidera integrare gli strumenti e i processi esistenti nei [servizi di monitoraggio e reporting](../../decision-guides/logging-and-reporting/index.md) integrati basati su cloud.

> [!NOTE]
> Le organizzazioni usano anche strumenti Azure DevOps di terze parti per monitorare i carichi di lavoro e le risorse. Per altre informazioni, vedere [integrazione degli strumenti DevOps](https://azure.microsoft.com/products/devops-tool-integrations).

## <a name="next-steps"></a>Passaggi successivi

Informazioni su come creare, assegnare e gestire le [definizioni dei criteri](https://docs.microsoft.com/azure/governance/policy) in Azure.
