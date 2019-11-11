---
title: Specializzazione dei carichi di lavoro per la gestione del cloud in Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Migliorare le operazioni di gestione del cloud specifiche dei carichi di lavoro
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: 92b9988d47dcc8ba4b7a7e3dd02a4ec9ff3ed2e9
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565386"
---
# <a name="workload-specialization-for-cloud-management"></a>Specializzazione dei carichi di lavoro per la gestione del cloud

La specializzazione dei carichi di lavoro si basa sui concetti illustrati in [Specializzazione della piattaforma](./platform-specialization.md).

![Oltre la baseline di gestione del cloud](../../_images/manage/beyond-the-baseline.png)

- **Operazioni per i carichi di lavoro:** il maggiore investimento in operazioni per carico di lavoro e il massimo livello di resilienza. Queste operazioni sono consigliate per circa il 20% dei carichi di lavoro che generano valore di business. La specializzazione è in genere riservata ai carichi di lavoro ad alta criticità o cruciali.
- **Operazioni della piattaforma:** investimenti in operazioni distribuiti su molti carichi di lavoro. I miglioramenti della resilienza hanno effetto su tutti i carichi di lavoro che usano la piattaforma definita. Queste operazioni sono consigliate per circa il 20% delle piattaforme con la massima criticità. La specializzazione è in genere riservata ai carichi di lavoro con criticità medio-alta.
- **Baseline di gestione ottimizzata:** l'investimento relativamente minimo in operazioni. La specializzazione migliora leggermente gli impegni aziendali tramite l'aggiunta di strumenti e processi operativi nativi del cloud.

## <a name="high-level-process"></a>Processo di alto livello

La specializzazione dei carichi di lavoro consiste nell'esecuzione disciplinata dei quattro processi seguenti in un approccio iterativo. Ogni processo viene illustrato in maggior dettaglio nell'articolo [Specializzazione della piattaforma](./platform-specialization.md).

- **Miglioramento della progettazione dei sistemi:** migliorare la progettazione di un carico di lavoro specifico, in modo da ridurre al minimo le interruzioni.
- **Automazione della correzione:** alcuni miglioramenti non sono economicamente convenienti. In questi casi, può essere opportuno automatizzare la correzione dei problemi e ridurre l'impatto delle interruzioni.
- **Scalabilità della soluzione:** con il miglioramento della progettazione dei sistemi e della correzione automatizzata, questi cambiamenti possono essere applicati nell'intero ambiente tramite il catalogo di servizi.
- **Miglioramento continuo:** è possibile usare diversi strumenti di monitoraggio per individuare i miglioramenti incrementali, che possono essere affrontati nella fase successiva della progettazione dei sistemi, dell'automazione e della scalabilità.

## <a name="cultural-change"></a>Cambiamento culturale

La specializzazione dei carichi di lavoro spesso innesca un cambiamento culturale nei tradizionali processi di sviluppo IT che puntano a offrire una baseline di gestione, le baseline ottimizzate e le operazioni della piattaforma. Questi tipi di offerta possono essere distribuiti nell'intero ambiente. L'implementazione della specializzazione dei carichi di lavoro è simile a quella della specializzazione della piattaforma. Ma, a differenza delle piattaforme comuni, la specializzazione richiesta dai singoli carichi di lavoro non è quasi mai scalabile.

Quando è necessaria tale specializzazione, in genere la gestione operativa si evolve oltre una prospettiva di IT centralizzata. L'approccio suggerito in Cloud Adoption Framework è una distribuzione delle funzionalità di gestione del cloud.

In questo modello, le attività operative come il monitoraggio, la distribuzione, DevOps e altre funzioni incentrate sull'innovazione vengono spostate in un'organizzazione di sviluppo di applicazioni o di tipo business unit. I team che della piattaforma cloud e del monitoraggio del cloud continuano comunque a mantenere la baseline di gestione nell'ambiente.

Questi team centralizzati inoltre guidano e istruiscono sulle rispettive operazioni i team specializzati in carichi di lavoro. Ma la responsabilità operativa quotidiana ricade sul team di gestione del cloud, che esula dall'IT. Questo tipo di controllo distribuito è uno dei principali indicatori del livello di maturità del centro di eccellenza cloud.

## <a name="beyond-platform-specialization---application-insights"></a>Oltre la specializzazione della piattaforma - Application Insights

Per realizzare operazioni ben definite, è necessario prestare una maggiore attenzione al carico di lavoro in questione. Durante la fase di miglioramento continuo, Application Insights sarà un'aggiunta necessaria per la toolchain della gestione del cloud.

|Requisito|Strumento|Scopo|
|---|---|---|
|Monitoraggio delle applicazioni|Application Insights|Monitoraggio e diagnostica per le app|
|Prestazioni, disponibilità e utilizzo|Application Insights|Monitoraggio avanzato delle applicazioni con dashboard, mappe composite, dati di utilizzo e traccia|

### <a name="deploy-application-insights"></a>Distribuire Application Insights

1. Nella portale di Azure passare ad **Application Insights**.
1. Selezionare **+ Aggiungi** per creare una risorsa di Application Insights per il monitoraggio dell'applicazione Web live.
1. Seguire le istruzioni visualizzate sullo schermo.

Per istruzioni sulla configurazione dell'applicazione per il monitoraggio, vedere [Hub Application Insights di Monitoraggio di Azure](https://docs.microsoft.com/azure/azure-monitor/azure-monitor-app-hub).

::: zone target="chromeless"

::: form action="OpenBlade[#create/Microsoft.AppInsights]" submitText="Create Application Insight resources" :::

::: zone-end

### <a name="monitor-performance-availability-and-usage"></a>Monitorare le prestazioni, la disponibilità e l'utilizzo

1. Nel portale di Azure cercare **Application Insights**.
1. Scegliere una delle risorse di Application Insights nell'elenco.

Application Insights include diversi tipi di opzioni per il monitoraggio di prestazioni, disponibilità, utilizzo e dipendenze. Ognuna di queste visualizzazioni dei dati dell'applicazione fornisce chiarezza nel ciclo di feedback di miglioramento continuo.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/microsoft.insights%2Fcomponents]" submitText="Monitor applications" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end
