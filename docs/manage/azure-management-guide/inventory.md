---
title: Inventario e visibilità in Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni su come configurare l'inventario, il monitoraggio, la creazione di report e gli avvisi per l'ambiente di gestione di Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: 8b7902910de3df729524b1625fe83b0681eeef5b
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72556786"
---
# <a name="inventory-and-visibility-in-azure"></a>Inventario e visibilità in Azure

_Inventario e visibilità_ è la prima di tre discipline della baseline di gestione del cloud.

![Baseline di gestione del cloud](../../_images/manage/management-baseline.png)

Questa disciplina è la più importante perché è fondamentale per raccogliere i dati operativi appropriati quando si prendono decisioni sulle operazioni. I team di gestione del cloud devono capire quali asset vengono gestiti e con quale livello di efficienza. Questo articolo illustra i vari strumenti che forniscono sia un inventario che la visibilità sul relativo stato di esecuzione.

Per qualsiasi ambiente di livello aziendale, la tabella seguente include il minimo consigliato per qualsiasi baseline di gestione.

|Process  |Strumento  |Scopo  |
|---------|---------|---------|
|Monitoraggio dell'integrità dei servizi di Azure|Integrità dei servizi di Azure|Integrità, prestazioni e diagnostica per i servizi in esecuzione in Azure|
|Centralizzazione dei log|Log Analytics|Registrazione centrale per tutti gli scopi di visibilità|
|Centralizzazione del monitoraggio|Monitoraggio di Azure|Monitoraggio centrale di dati operativi e tendenze|
|Inventario delle VM e rilevamento delle modifiche|Servizio Rilevamento modifiche e inventario di Azure|Inventario delle VM e monitoraggio delle modifiche per il livello del sistema operativo guest|
|Integrità del servizio|Azure Activity Log|Monitoraggio delle modifiche a livello di sottoscrizione|
|Monitoraggio del sistema operativo host|Monitoraggio di Azure per le macchine virtuali|Monitoraggio delle modifiche e delle prestazioni delle VM|
|Monitoraggio della rete|Azure Network Watcher|Monitoraggio delle modifiche e delle prestazioni della rete|
|Monitoraggio del DNS|Analisi DNS|Sicurezza, prestazioni e operazioni del DNS|

::: zone target="docs"

## <a name="azure-service-health"></a>Integrità dei servizi di Azure

::: zone-end
::: zone target="chromeless"

## <a name="azure-service-healthtabazureservicehealth"></a>[Integrità dei servizi di Azure](#tab/AzureServiceHealth)

::: zone-end

Integrità dei servizi di Azure fornisce una visualizzazione personalizzata dell'integrità dei servizi e delle aree di Azure che vengono usati. Le informazioni sui problemi attivi vengono pubblicate in Integrità dei servizi per comprendere meglio l'impatto per le risorse. Sono previsti aggiornamenti regolari per essere informati quando viene risolto il problema.

In Integrità dei servizi vengono anche pubblicati gli eventi di manutenzione pianificata, in modo che gli utenti siano a conoscenza delle modifiche che potrebbero influire sulla disponibilità delle risorse. Configurare gli avvisi di Integrità dei servizi per ricevere notifiche in caso di problemi dei servizi, eventi di manutenzione pianificata o altre modifiche che potrebbero influire sui servizi e sulle aree di Azure che vengono usati.

Integrità dei servizi di Azure include le informazioni seguenti:

- **Stato di Azure:** visualizzazione completa dell'integrità dei servizi di Azure.
- **Integrità dei servizi:** visualizzazione personalizzata dell'integrità dei servizi di Azure.
- **Integrità risorsa:** visualizzazione più dettagliata dell'integrità di ogni singola risorsa.

::: zone target="chromeless"

<!-- markdownlint-disable MD024 -->

### <a name="action"></a>Azione

Per configurare un avviso di Integrità dei servizi:

1. Passare a **Integrità dei servizi**.
2. Selezionare **Avvisi di integrità**.
3. Creare un avviso di integrità dei servizi.

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/Microsoft_Azure_Health/AzureHealthBrowseBlade/healthalerts]" submitText="Go to Service Health" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Per configurare un avviso di Integrità dei servizi, accedere al [portale di Azure](https://portal.azure.com/#blade/Microsoft_Azure_Health/AzureHealthBrowseBlade/healthalerts).

### <a name="learn-more"></a>Altre informazioni

Per altre informazioni, vedere [Documentazione di Integrità dei servizi di Azure](https://docs.microsoft.com/azure/service-health).

## <a name="log-analytics"></a>Log Analytics

::: zone-end
::: zone target="chromeless"

## <a name="log-analyticstablog-analytics"></a>[Log Analytics](#tab/Log-Analytics)

::: zone-end

Un'[area di lavoro Log Analytics](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace) è un ambiente univoco per l'archiviazione dei dati dei log di Monitoraggio di Azure. Ogni area di lavoro include un proprio repository di dati e una configurazione specifica. Le origini dati e le soluzioni sono configurate per archiviare i dati in determinate aree di lavoro. Per le soluzioni di monitoraggio di Azure è necessario che tutti i server siano connessi a un'area di lavoro, in modo che sia possibile archiviare e accedere ai dati dei relativi log.

::: zone target="chromeless"

### <a name="action"></a>Azione

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.OperationalInsights%2Fworkspaces]" submitText="Explore Azure Monitor" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

### <a name="learn-more"></a>Altre informazioni

Per altre informazioni, vedere la [documentazione relativa alla creazione di aree di lavoro Log Analytics](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace).

## <a name="azure-monitor"></a>Monitoraggio di Azure

::: zone-end
::: zone target="chromeless"

## <a name="azure-monitortabazure-monitor"></a>[Monitoraggio di Azure](#tab/Azure-Monitor)

::: zone-end

Monitoraggio di Azure offre un solo hub unificato per tutti i dati di monitoraggio e diagnostica in Azure. È possibile usarlo per ottenere visibilità nelle risorse. Monitoraggio di Azure consente di individuare e correggere i problemi e di ottimizzare le prestazioni. Consente inoltre di comprendere il comportamento dei clienti.

- **Monitorare e visualizzare metriche:** le metriche sono valori numerici disponibili dalle risorse di Azure che consentono di determinare l'integrità dei sistemi. È possibile personalizzare i grafici per i dashboard e usare cartelle di lavoro per la creazione di report.

- **Eseguire query e analisi dei log:** i log includono log di attività e log di diagnostica di Azure. È possibile raccogliere log aggiuntivi da altre soluzioni di monitoraggio e gestione per le risorse cloud o locali. Log Analytics fornisce un repository centrale per aggregare tutti questi dati. Da qui è possibile eseguire query per semplificare la risoluzione dei problemi o per visualizzare i dati.

- **Configurare avvisi e azioni:** gli avvisi avvertono in modo proattivo riguardo a eventuali condizioni critiche. È possibile adottare azioni correttive in base a trigger generati da metriche, log o problemi di integrità dei servizi. È possibile configurare diverse notifiche e azioni e inviare i dati agli strumenti di gestione dei servizi IT.

::: zone target="chromeless"

### <a name="action"></a>Azione

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/Microsoft_Azure_Monitoring/AzureMonitoringBrowseBlade/overview]" submitText="Explore Azure Monitor" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

 Iniziare monitorando gli elementi seguenti:

- [Applicazioni](https://docs.microsoft.com/azure/application-insights/app-insights-overview)
- [Contenitori](https://docs.microsoft.com/azure/monitoring/monitoring-container-overview)
- [Macchine virtuali](https://docs.microsoft.com/azure/monitoring/monitoring-service-map)
- [Reti](https://docs.microsoft.com/azure/networking/network-monitoring-overview)

Per monitorare altre risorse, è possibile trovare soluzioni aggiuntive in Azure Marketplace.

Per esplorare Monitoraggio di Azure, accedere al [portale di Azure](https://portal.azure.com/#blade/Microsoft_Azure_Monitoring/AzureMonitoringBrowseBlade/overview).

### <a name="learn-more"></a>Altre informazioni

Per altre informazioni, vedere la [documentazione di Monitoraggio di Azure](https://docs.microsoft.com/azure/monitoring-and-diagnostics).

## <a name="onboard-solutions"></a>Onboarding di soluzioni

::: zone-end
::: zone target="chromeless"

## <a name="onboard-solutionstabconfigure-solutions"></a>[Onboarding di soluzioni](#tab/Configure-solutions)

::: zone-end

Per abilitare le soluzioni, è necessario configurare l'area di lavoro Log Analytics. Dopo l'onboarding, le VM di Azure e i server locali otterranno le soluzioni dalle aree di lavoro Log Analytics a cui sono connessi.

Sono disponibili due approcci all'onboarding:

- [Singola macchina virtuale](https://docs.microsoft.com/azure/cloud-adoption-framework/manage/azure-server-management/onboard-single-vm)
- [Intera sottoscrizione](https://docs.microsoft.com/azure/cloud-adoption-framework/manage/azure-server-management/onboard-at-scale)

Ogni articolo illustra una serie di procedure per eseguire l'onboarding delle soluzioni seguenti:

- Gestione degli aggiornamenti
- Rilevamento modifiche e inventario
- Azure Activity Log
- Integrità agente di Azure Log Analytics
- Antimalware Assessment
- Monitoraggio di Azure per le macchine virtuali
- Centro sicurezza di Azure

Ognuno degli articoli precedenti consentirà di stabilire l'inventario e la visibilità.
