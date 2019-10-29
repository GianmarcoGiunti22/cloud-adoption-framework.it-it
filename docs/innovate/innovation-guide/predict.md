---
title: "Guida all'innovazione di Azure: Prevedere e influenzare"
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni su come prevedere e influenzare l'uso di Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: b2ed1b072d5226649e5248e350edfa3578978c4c
ms.sourcegitcommit: 910efd3e686bd6b9bf93951d84253b43d4cc82b5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72769253"
---
::: zone target="docs"

# <a name="azure-innovation-guide-predict-and-influence"></a>Guida all'innovazione di Azure: Prevedere e influenzare

::: zone-end

::: zone target="chromeless"

# <a name="predict-and-influence"></a>Prevedere e influenzare

::: zone-end

Le aziende innovative avranno a disposizione informazioni dettagliate sui dati, sul comportamento e sulle esigenze della base di clienti. L'analisi di queste informazioni può risultare utile per prevedere le esigenze dei clienti anche prima che siano consapevoli di averle. Questo articolo presenta alcuni approcci per la distribuzione di soluzioni predittive. Nella sezione successiva, l'articolo introduce gli approcci per l'integrazione di tali previsioni nella soluzione, in modo da influenzare i comportamenti dei clienti.

La tabella seguente aiuta a trovare la soluzione migliore in base alle esigenze di implementazione.

|Service  |Modelli predefiniti  |Creazione e sperimentazione  |Training e compilazione con Python|Competenze necessarie|
|---------|---------|---------|---------|---------|
|Servizi cognitivi|Sì|No|No|Competenze su API e sviluppo|
|Azure Machine Learning Studio|Sì|Sì|No|Conoscenza generale degli algoritmi predittivi|
|Servizio Azure Machine Learning|Sì|Sì|Sì|Data scientist|

## <a name="azure-cognitive-servicestabcognitiveservices"></a>[Servizi cognitivi di Azure](#tab/CognitiveServices)

La famiglia di Servizi cognitivi di Azure offre il percorso più rapido e semplice per la generazione di previsioni. L'offerta di Servizi cognitivi consente di eseguire previsioni in base a modelli esistenti, che non richiedono training aggiuntivo. Questi servizi sono ottimali nel caso il personale non includa un data scientist per eseguire il training del modello predittivo. Per alcuni servizi, non è richiesto alcun training. Per altri è necessario solo un training minimo.

Per un elenco dei servizi disponibili con informazioni sulla quantità di training necessaria, vedere [Servizi cognitivi e Machine Learning](https://docs.microsoft.com/azure/cognitive-services/cognitive-services-and-machine-learning#service-requirements-for-the-data-model).

### <a name="action"></a>Azione

Per usare l'API Servizi cognitivi:

1. Passare a **Servizi cognitivi**.
2. Fare clic su **Aggiungi +** per trovare un servizio cognitivo nel Marketplace.
3. Se si conosce il nome del servizio che si vuole usare, è possibile immetterlo nella casella di testo **Cerca nel Marketplace**.
4. In alternativa, per un elenco di servizi cognitivi, fare clic sul collegamento **Vedi altro** accanto all'intestazione Servizi cognitivi.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.CognitiveServices%2Faccounts]" submitText="Go to Cognitive Services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Passare direttamente a Servizi cognitivi nel [portale di Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.CognitiveServices%2Faccounts).

::: zone-end

## <a name="azure-machine-learning-studiotabmachinelearningstudio"></a>[Azure Machine Learning Studio](#tab/MachineLearningStudio)

Se i modelli esistenti all'interno dei servizi cognitivi non sono indicati per la previsione desiderata, Azure Machine Learning Studio offre la possibilità di crearne altre senza la necessità di competenze approfondite in data science.

<!-- markdownlint-disable MD024 -->

### <a name="action"></a>Azione

È possibile usare Azure Machine Learning Studio per creare un modello e usarlo per sperimentare:

1. Passare ad **Azure Machine Learning Studio**.
2. Fare clic su **Create Machine Learning Studio Workspace** (Crea un'area di lavoro di Microsoft Azure Machine Learning Studio) e seguire le istruzioni.
3. La nuova area di lavoro fornisce un'interfaccia con trascinamento della selezione per creare un modello con cui sperimentare, in alternativa al training approfondito.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.MachineLearning%2Fworkspaces]" submitText="Go to Azure Machine Learning Studio" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Passare direttamente ad Azure Machine Learning Studio nel [portale di Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.MachineLearning%2Fworkspaces).

::: zone-end

## <a name="azure-machine-learning-servicetabmachinelearningservice"></a>[Servizio Azure Machine Learning](#tab/MachineLearningService)

Il servizio Azure Machine Learning fornisce l'approccio più completo basato sul codice necessario per un training più approfondito dei set di dati dei clienti. Usando linguaggi come Python, i data scientist possono eseguire il training e quindi creare un algoritmo per prevedere le esigenze dei clienti.

### <a name="action"></a>Azione

Un data scientist può usare un servizio di Azure Machine Learning per eseguire il training e creare un modello usando linguaggi avanzati come Python:

1. Passare a **Servizio Azure Machine Learning**.
2. Fare clic su **Create Machine Learning service workspaces** (Crea aree di lavoro per il servizio Machine Learning) e seguire le istruzioni.
3. La nuova area di lavoro offre ai data scientist un approccio basato sul codice per il training e la creazione di modelli che richiedono analisi più avanzate per prevedere accuratamente le esigenze dei clienti.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.MachineLearningServices%2Fworkspaces]" submitText="Go to Azure Machine Learning Service" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Passare direttamente ad Azure Machine Learning Studio nel [portale di Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.MachineLearningServices%2Fworkspaces).

::: zone-end

## <a name="influence"></a>Influenza

Tutti gli approcci descritti in precedenza producono un'API che espone il modello di previsione alle applicazioni. All'interno della soluzione usare uno di questi approcci per inserire i dati raccolti dal cliente in un'API predittiva. I risultati possono quindi essere integrati nell'esperienza del cliente come passaggio successivo suggerito.

Questi passaggi successivi si prefiggono di definire i modelli di comportamento dei clienti e di influenzare il modo in cui reagiscono. Poiché i passaggi successivi suggeriti sono basati su algoritmi predittivi, verranno usati i dati dei clienti precedenti e disponibili per prevedere e soddisfare le esigenze, spesso anche prima che il cliente sia consapevole di averle.
