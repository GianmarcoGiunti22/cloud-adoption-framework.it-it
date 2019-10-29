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
ms.openlocfilehash: 51bdf23ccb2262202dfa095c5e9b57f727d11d3b
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72556990"
---
# <a name="workload-specialization-for-cloud-management"></a>Specializzazione dei carichi di lavoro per la gestione del cloud

La specializzazione dei carichi di lavoro si basa sui concetti illustrati in [Specializzazione della piattaforma](./platform-specialization.md).

![Oltre la baseline di gestione del cloud](../../_images/manage/beyond-the-baseline.png)

- **Operazioni per i carichi di lavoro:** investimento maggiore in operazioni per i carichi di lavoro. Massimo grado di resilienza. Suggerite per circa il 20% dei carichi di lavoro che determinano un valore di business. Generalmente riservate ai carichi di lavoro ad alta criticità o cruciali.
- **Operazioni della piattaforma:** investimenti in operazioni distribuiti su molti carichi di lavoro. I miglioramenti della resilienza hanno effetto su tutti i carichi di lavoro che sfruttano la piattaforma definita. Suggerite per circa il 20% delle piattaforme con la massima criticità. Generalmente riservate ai carichi di lavoro con criticità medio-alta.
- **Baseline di gestione ottimizzata:** investimento minimo relativo in operazioni. Impegni aziendali leggermente migliorati tramite l'aggiunta di strumenti e processi operativi nativi del cloud.

## <a name="high-level-process"></a>Processo di alto livello

La specializzazione dei carichi di lavoro consiste nell'esecuzione disciplinata dei quattro processi seguenti in un approccio iterativo. Ogni processo viene illustrato in maggior dettaglio nell'articolo [Specializzazione della piattaforma](./platform-specialization.md).

- **Miglioramento della progettazione dei sistemi:** migliorare la progettazione di un carico di lavoro specifico, in modo da ridurre al minimo le interruzioni.
- **Automazione della correzione:** alcuni miglioramenti non sono economicamente convenienti. In questi casi, può essere opportuno automatizzare la correzione e ridurre l'impatto delle interruzioni.
- **Scalabilità della soluzione:** con il miglioramento della progettazione dei sistemi e della correzione automatizzata, questi cambiamenti possono essere applicati gradualmente nell'intero ambiente tramite il catalogo di servizi.
- **Miglioramento continuo:** è possibile usare vari strumenti di monitoraggio per individuare i miglioramenti incrementali che possono essere affrontati come fase successiva della progettazione dei sistemi, dell'automazione e della scalabilità.

## <a name="cultural-change"></a>Cambiamento culturale

La specializzazione dei carichi di lavoro spesso genera un cambiamento culturale. I processi sviluppati dall'IT tradizionale sono destinati a offrire una baseline di gestione, le baseline ottimizzate e le operazioni della piattaforma. Questi tipi di offerta possono essere distribuiti nell'intero ambiente. L'implementazione della specializzazione dei carichi di lavoro è molto simile a quella della specializzazione della piattaforma. Ma, a differenza delle piattaforme comuni, la specializzazione richiesta dai singoli carichi di lavoro non è sempre scalabile.

Quando è richiesta la specializzazione dei carichi di lavoro, in genere la gestione operativa si evolve oltre una prospettiva di IT centralizzata. L'approccio suggerito in Cloud Adoption Framework è una distribuzione delle funzionalità di gestione del cloud.

In questo modello, le attività operative come il monitoraggio, la distribuzione, DevOps e altre funzioni incentrate sull'innovazione vengono spostate in un'organizzazione di sviluppo di applicazioni o di tipo business unit. I team che della piattaforma cloud e del monitoraggio del cloud continuano comunque a mantenere la baseline di gestione nell'ambiente. Questi team centralizzati inoltre guidano e istruiscono sulle rispettive operazioni i team specializzati in carichi di lavoro. Ma la responsabilità operativa quotidiana ricade sul team di gestione del cloud, che esula dall'IT. Questo tipo di controllo distribuito è uno dei principali indicatori del livello di maturità del centro di eccellenza cloud.

## <a name="beyond-platform-specialization---application-insights"></a>Oltre la specializzazione della piattaforma - Application Insights

Per realizzare operazioni ben definite, è necessario prestare una maggiore attenzione al carico di lavoro in questione. Durante la fase di miglioramento continuo, Application Insights sarà un'aggiunta necessaria per la toolchain della gestione del cloud.

|Monitoraggio applicazioni|Application Insights|Monitoraggio e diagnostica per le app| |Prestazioni, disponibilità, utilizzo|Application Insights|Monitoraggio avanzato delle applicazioni con dashboard per le app, mappe composite, utilizzo e traccia|

### <a name="deploy-application-insights"></a>Distribuire Application Insights

1. Nel portale di Azure cercare **Application Insights**.
2. Fare clic su **+ Aggiungi** per creare una risorsa di Application Insights per il monitoraggio dell'applicazione Web live.
3. Seguire le istruzioni visualizzate sullo schermo

Per istruzioni sulla configurazione dell'applicazione per il monitoraggio, vedere [Hub Application Insights di Monitoraggio di Azure](https://docs.microsoft.com/azure/azure-monitor/azure-monitor-app-hub).

::: zone target="chromeless"

::: form action="OpenBlade[#create/Microsoft.AppInsights]" submitText="Create Application Insight resources" :::

::: zone-end

### <a name="monitor-performance-availability-and-usage"></a>Monitorare le prestazioni, la disponibilità e l'utilizzo

1. Nel portale di Azure cercare **Application Insights**.
2. Scegliere una delle risorse di Application Insights nell'elenco

Il riquadro di spostamento di Application Insights contiene un'ampia varietà di opzioni per il monitoraggio di prestazioni, disponibilità, utilizzo e dipendenze. Ognuna di queste visualizzazioni dei dati dell'applicazione fornirà chiarezza nel ciclo di feedback di miglioramento continuo.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/microsoft.insights%2Fcomponents]" submitText="Monitor applications" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end
