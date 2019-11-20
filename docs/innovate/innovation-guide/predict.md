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
ms.openlocfilehash: bee593827b58f1ccca6e82a3ae36d2b6352f0754
ms.sourcegitcommit: 50788e12bb744dd44da14184b3e884f9bddab828
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2019
ms.locfileid: "74160405"
---
::: zone target="docs"

# <a name="azure-innovation-guide-predict-and-influence"></a>Guida all'innovazione di Azure: Prevedere e influenzare

::: zone-end

::: zone target="chromeless"

# <a name="predict-and-influence"></a>Prevedere e influenzare

::: zone-end

Le aziende innovative hanno a disposizione informazioni dettagliate sui dati, sul comportamento e sulle esigenze della base di clienti. L'analisi di queste informazioni può risultare utile per prevedere le esigenze dei clienti, preferibilmente prima che i clienti stessi siano consapevoli di averle. Questo articolo presenta alcuni approcci per la distribuzione di soluzioni predittive. Nelle sezioni finali vengono illustrati gli approcci per l'integrazione di tali previsioni nella soluzione adottata, in modo da influenzare i comportamenti dei clienti.

La tabella seguente consente di trovare la soluzione migliore in base alle proprie esigenze di implementazione.

|Service  |Modelli predefiniti  |Creazione e sperimentazione  |Training e compilazione con Python|Competenze necessarie|
|---------|---------|---------|---------|---------|
|Servizi cognitivi di Azure|Sì|No|No|Competenze su API e sviluppo|
|Azure Machine Learning Studio|Sì|Sì|No|Conoscenza generale degli algoritmi predittivi|
|Servizio Azure Machine Learning|Sì|Sì|Sì|Data scientist|

## <a name="azure-cognitive-servicestabcognitiveservices"></a>[Servizi cognitivi di Azure](#tab/CognitiveServices)

La famiglia di Servizi cognitivi di Azure offre il percorso più rapido e semplice per generare previsioni sulle esigenze dei clienti. L'offerta di Servizi cognitivi consente di eseguire previsioni in base a modelli esistenti, che non richiedono training aggiuntivo. Questi servizi offrono una soluzione ottimale ed efficace quando nel personale di un'azienda non è disponibile un data scientist per eseguire il training del modello predittivo. Per alcuni servizi, non è richiesto alcun training. Per altri è sufficiente un training minimo.

Per un elenco dei servizi disponibili con informazioni sull'eventuale training necessario, vedere [Servizi cognitivi e Machine Learning](https://docs.microsoft.com/azure/cognitive-services/cognitive-services-and-machine-learning#service-requirements-for-the-data-model).

### <a name="action"></a>Azione

Per usare un'API Servizi cognitivi:

1. Nel [portale di Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.CognitiveServices%2Faccounts) passare a **Servizi cognitivi**.
2. Selezionare **Aggiungi** per trovare un'API Servizi cognitivi in Azure Marketplace.
3. Eseguire una di queste operazioni:
   - Se si conosce il nome del servizio da usare, immetterlo nella casella **Cerca nel Marketplace**.
   - In alternativa, per un elenco di API Servizi cognitivi, selezionare il collegamento **Vedi altro** accanto all'intestazione Servizi cognitivi.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.CognitiveServices%2Faccounts]" submitText="Go to Cognitive Services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Passare direttamente a Servizi cognitivi nel [portale di Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.CognitiveServices%2Faccounts).

::: zone-end

## <a name="azure-machine-learning-studiotabmachinelearningstudio"></a>[Azure Machine Learning Studio](#tab/MachineLearningStudio)

Se i modelli esistenti all'interno di Servizi cognitivi non sono adatti alla previsione desiderata, Azure Machine Learning Studio offre la possibilità di creare altre previsioni, senza che sia necessario avere competenze approfondite di data science.

<!-- markdownlint-disable MD024 -->

### <a name="action"></a>Azione

È possibile usare Azure Machine Learning Studio per creare un modello e usarlo per sperimentare eseguendo queste operazioni:

1. Nel [portale di Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.MachineLearning%2Fworkspaces) passare a **Azure Machine Learning Studio**.
2. Selezionare **Create Machine Learning Studio Workspace** (Crea un'area di lavoro di Machine Learning Studio) e seguire le istruzioni.

   La nuova area di lavoro offre un'interfaccia con trascinamento della selezione per creare un modello con cui sperimentare, in alternativa al training approfondito.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.MachineLearning%2Fworkspaces]" submitText="Go to Azure Machine Learning Studio" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Passare direttamente ad Azure Machine Learning Studio nel [portale di Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.MachineLearning%2Fworkspaces).

::: zone-end

## <a name="azure-machine-learning-servicetabmachinelearningservice"></a>[Servizio Azure Machine Learning](#tab/MachineLearningService)

Il servizio Azure Machine Learning offre l'approccio più completo basato sul codice necessario per un training più approfondito dei set di dati dei clienti. Usando linguaggi come Python, i data scientist possono eseguire il training e quindi creare un algoritmo per prevedere le esigenze dei clienti.

### <a name="action"></a>Azione

Un data scientist può usare il servizio Azure Machine Learning per eseguire il training e creare un modello usando linguaggi avanzati come Python:

1. Passare a **Servizio Azure Machine Learning**.
2. Selezionare **Create Machine Learning service workspaces** (Crea aree di lavoro per il servizio Machine Learning) e seguire le istruzioni.
3. La nuova area di lavoro offre ai data scientist un approccio basato sul codice per il training e la creazione di modelli che richiedono analisi più avanzate per prevedere accuratamente le esigenze dei clienti.

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.MachineLearningServices%2Fworkspaces]" submitText="Go to Azure Machine Learning service" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

::: zone target="docs"

Passare direttamente ad Azure Machine Learning Studio nel [portale di Azure](https://portal.azure.com/#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.MachineLearningServices%2Fworkspaces).

::: zone-end

## <a name="influence"></a>Influenza

Tutti gli approcci descritti in precedenza hanno come risultato un'API che espone il modello di previsione alle applicazioni. All'interno della soluzione, adottare uno di questi approcci per inserire i dati raccolti dal cliente in un'API predittiva. I risultati possono quindi essere integrati nell'esperienza del cliente come passaggio successivo suggerito.

Questi passaggi successivi possono essere utili per definire i modelli di comportamento dei clienti e influenzare il modo in cui reagiscono. Poiché sono basati su algoritmi predittivi, i passaggi successivi suggeriti usano i dati precedenti dei clienti e altri dati disponibili per prevedere e soddisfare le loro esigenze, spesso anche prima che i clienti siano consapevoli di averle.
