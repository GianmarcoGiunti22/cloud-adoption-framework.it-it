---
title: Strumenti di coerenza delle risorse in Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Strumenti di coerenza delle risorse in Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 6a0a2303473cffd9bb5175c67e12a84d6baa2814
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70824093"
---
# <a name="resource-consistency-tools-in-azure"></a>Strumenti di coerenza delle risorse in Azure

La [Coerenza delle risorse](index.md) è una delle [cinque discipline della governance del cloud](../governance-disciplines.md). Questa disciplina riguarda le modalità di definizione dei criteri di gestione operativa di ambienti, applicazioni o carichi di lavoro. All'interno delle cinque discipline della governance del cloud, la disciplina della coerenza delle risorse implica il monitoraggio delle prestazioni dell'applicazione, del carico di lavoro e degli asset. Sono inoltre incluse le attività necessarie per soddisfare le esigenze di scalabilità, correggere le violazioni dei contratti di lavoro delle prestazioni ed evitare in modo proattivo le violazioni dei contratti di prestazioni tramite la correzione automatica.

Di seguito è riportato un elenco di strumenti di Azure che possono consentire di sviluppare i criteri e i processi che supportano la disciplina di governance.

| Strumento | [Portale di Azure](https://azure.microsoft.com/features/azure-portal)  | [Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview)  | [Azure Blueprint](/azure/governance/blueprints/overview) | [Automazione di Azure](/azure/automation/automation-intro) | [Azure AD](/azure/active-directory/fundamentals/active-directory-whatis) | [Backup di Azure](/azure/backup/backup-introduction-to-azure-backup) | [Azure Site Recovery](/azure/site-recovery/site-recovery-overview) |
|---------|---------|---------|---------|---------|---------|---------|---------|
| Distribuire le risorse                             | Yes | Sì | Sì | Sì | No  | No | No |
| Gestire risorse                             | Sì | Sì | Sì | Sì | No  | No | No |
| Implementare le risorse tramite modelli             | No  | Sì | No  | Sì | No  | No | No |
| Distribuire l'ambiente orchestrato          | No  | No  | Sì | No  | No  | No | No |
| Definire gruppi di risorse                       | Sì | Sì | Sì | No  | No  | No | No |
| Gestire i proprietari dell'account e i carichi di lavoro           | Yes | Sì | Sì | No  | No  | No | No |
| Gestire le risorse di accesso condizionale       | Sì | Sì | Sì | No  | No  | No | No |
| Configurare gli utenti per il controllo degli accessi in base al ruolo                         | Yes | No  | No  | No  | Sì | No | No |
| Assegnare autorizzazioni e ruoli per le risorse | Sì | Sì | Sì | No  | Sì | No | No |
| Definire le dipendenze tra le risorse        | No  | Yes | Sì | No  | No  | No | No |
| Applicare il controllo di accesso                         | Sì | Sì | Sì | No  | Sì | No | No |
| Valutare la disponibilità e la scalabilità          | No  | No  | No  | Sì | No  | No | No |
| Applicare tag alle risorse                      | Yes | Sì | Sì | No  | No  | No | No |
| Assegnare regole di Criteri in Azure                    | Sì | Sì | Sì | No  | No  | No | No |
| Applicare la correzione automatizzata                  | No  | No  | No  | Sì | No  | No | No |
| Gestire la fatturazione                               | Yes | No  | No  | No  | No  | No | No |
| Pianificare le risorse per il ripristino di emergenza         | Sì | Sì | Sì | No  | No  | Yes | Sì |
|Ripristinare i dati durante un'interruzione o una violazione del contratto di servizio     | No | No  | No  | No  | No  | Yes | Sì |
|Ripristinare le applicazioni durante un'interruzione o una violazione del contratto di servizio     | No | No  | No  | No  | No  | Yes | Sì |

Oltre a questi strumenti di funzionalità e coerenza delle risorse, è necessario monitorare le risorse implementate per le prestazioni e i problemi di integrità. [Monitoraggio di Azure](/azure/azure-monitor/overview) è l'impostazione predefinita per il monitoraggio e il reporting relativi alle soluzioni in Azure. Monitoraggio di Azure offre funzionalità per il monitoraggio delle risorse cloud. Questo elenco Mostra la funzionalità che soddisfa i requisiti di monitoraggio più comuni.

| Strumento | [Portale di Azure](https://azure.microsoft.com/features/azure-portal) | [Application Insights](/azure/application-insights/app-insights-overview) | [Log Analytics](/azure/azure-monitor/log-query/log-query-overview) | [API REST di Monitoraggio di Azure](/rest/api/monitor) |
|----------------------------------------------------|--------------|----------------------|---------------|------------------------|
| Dati di telemetria di macchine virtuali log                 | No           | No                   | Sì           | No                     |
| Dati di telemetria di reti virtuali log              | No           | No                   | Sì           | No                     |
| Dati di telemetria di servizi PaaS di log                   | No           | No                   | Sì           | No                     |
| Dati di telemetria per applicazioni log                     | No           | Sì                  | No            | No                     |
| Configurare report e avvisi                       | Sì          | No                   | No            | Sì                    |
| Pianificare report a intervalli regolari o analisi personalizzate        | No           | No                   | No            | No                     |
| Visualizzare e analizzare i dati di prestazioni e log     | Sì          | No                   | No            | No                     |
| Integrare una soluzione di monitoraggio locale o di terze parti     | No           | No                   | No            | Sì                    |

Quando si pianifica la distribuzione, si dovrà considerare dove sono archiviati i dati di registrazione e come si desidera integrare gli strumenti e i processi esistenti nei [servizi di monitoraggio e reporting](../../decision-guides/log-and-report/index.md) integrati basati su cloud.

> [!NOTE]
> Le organizzazioni usano anche strumenti Azure DevOps di terze parti per monitorare i carichi di lavoro e le risorse. Per altre informazioni, vedere [integrazione degli strumenti DevOps](https://azure.microsoft.com/products/devops-tool-integrations).

## <a name="next-steps"></a>Passaggi successivi

Informazioni su come creare, assegnare e gestire le [definizioni dei criteri](/azure/governance/policy) in Azure.
