---
title: "Guida all'innovazione di Azure: Democratizzare i dati"
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni su come usare Azure per democratizzare i dati
author: absheik
ms.author: absheik
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.custom: fasttrack-new, AQC
ms.localizationpriority: high
ms.openlocfilehash: 6c1e253d2ff49c331f4f1c153124f2ca06c81c36
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565545"
---
::: zone target="docs"

# <a name="azure-innovation-guide-democratize-data"></a>Guida all'innovazione di Azure: Democratizzare i dati

::: zone-end

::: zone target="chromeless"

# <a name="democratize-data"></a>Democratizzare i dati

::: zone-end

Uno dei primi passaggi per democratizzare i dati consiste nel migliorarne l'individuabilità. La catalogazione e la gestione della condivisione dei dati possono aiutare le aziende a ottenere il massimo valore dagli asset informatici esistenti. Un catalogo rende le origini dati facilmente individuabili e comprensibili per gli utenti che gestiscono i dati. È possibile usare Azure Data Catalog per la gestione dei dati all'interno di un'organizzazione e Condivisione dati di Azure per attività di gestione e condivisione all'esterno.

Anche i servizi di Azure per l'elaborazione di dati, come Azure Time Series Insights e Analisi di flusso, offrono funzionalità che clienti e partner usano con successo per soddisfare le loro esigenze di innovazione.

# <a name="catalogtabcatalog"></a>[Catalogo](#tab/Catalog)

## <a name="azure-data-catalog"></a>Azure Data Catalog

Azure Data Catalog soddisfa le esigenze di individuazione dei consumer di dati e consente ai producer di dati di gestire gli asset informatici. Questo servizio consente di ridurre la distanza tra il reparto IT e gli altri reparti aziendali, in modo che ognuno possa contribuire con le proprie intuizioni. È possibile archiviare i dati nel luogo desiderato e connettersi con gli strumenti che si preferisce usare. Con Azure Data Catalog è inoltre possibile controllare gli utenti autorizzati a individuare gli asset di dati registrati e anche integrare la soluzione con gli strumenti e i processi esistenti tramite API REST aperte.

> [!div class="checklist"]
>
> - Register
> - Ricerca e annotazione
> - Connessione e gestione

::: zone target="docs"

**Passare alla [documentazione di Azure Data Catalog](https://docs.microsoft.com/azure/data-catalog)**

::: zone-end

::: zone target="chromeless"

### <a name="action"></a>Azione

Per ogni organizzazione è possibile usare una sola istanza di Azure Data Catalog. Se è già stato creato un catalogo dati per l'organizzazione, non è possibile aggiungerne altri.

Per creare un'istanza di Azure Data Catalog per l'organizzazione:

1. Passare ad **Azure Data Catalog**.
2. Selezionare **Create** (Crea).

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.DataCatalog%2Fcatalogs]" submitText="Go to Azure Data Catalog" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

# <a name="sharetabshare"></a>[Share](#tab/Share) (Condividi)

## <a name="azure-data-share"></a>Condivisione dati di Azure

L'equilibrio tra la condivisione aperta dei dati e la possibilità di controllare quali dati condividere e con quali utenti rappresenta un fattore trainante per l'innovazione. Nel tentativo di democratizzare i dati, le organizzazioni possono essere facilmente sopraffatte dall'enorme quantità disponibile, dal ritmo di crescita e dal ciclo di vita dei dati. Con Condivisione dati di Azure, i provider possono controllare il modo in cui vengono gestiti i dati specificando apposite condizioni per la condivisione. Il consumer dei dati deve accettare queste condizioni prima di iniziare a riceverli. I provider di dati possono specificare la frequenza con cui i consumer ricevono gli aggiornamenti. L'accesso a nuovi aggiornamenti può essere revocato in qualsiasi momento dal provider di dati.

> [!div class="checklist"]
>
> - Creare una condivisione dati.
> - Aggiungere set di dati alla condivisione dati.
> - Abilitare una pianificazione della sincronizzazione per la condivisione dati.
> - Aggiungere i destinatari alla condivisione dati.

::: zone target="docs"
**Passare alla [documentazione di Condivisione dati di Azure](https://docs.microsoft.com/azure/data-share)**

::: zone-end

::: zone target="chromeless"

<!-- markdownlint-disable MD024 -->

### <a name="action"></a>Azione

Per creare una condivisione dati:

1. Passare a **Condivisione dati di Azure**.
2. Selezionare **Create data share** (Crea condivisione dati).

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.DataShare%2Faccounts]" submitText="Go to Azure Data Shares" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

# <a name="insightstabinsights"></a>[Insights](#tab/Insights)

## <a name="azure-time-series-insights"></a>Azure Time Series Insights

Le funzionalità innovative di Azure Time Series Insights per i dati offrono infinite possibilità. Questo servizio consente l'esplorazione quasi in tempo reale dei flussi di dati e l'archiviazione in più livelli per i dati delle serie temporali su scala IoT, oltre a offrire modelli per contestualizzare i dati di telemetria non elaborati e ricavarne informazioni basate sugli asset. Nella piattaforma Time Series Insights è inoltre supportata l'integrazione uniforme e continua con altre soluzioni per i dati e sono disponibili funzionalità per l'analisi della causa radice e il rilevamento delle anomalie, incluse opzioni per applicazioni personalizzate.

> [!div class="checklist"]
>
> - Pianificare l'ambiente Time Series Insights.
> - Visualizzare i dati nello strumento di esplorazione.
> - Comprendere la conservazione dei dati.
> - Sviluppare e condividere visualizzazioni personalizzate.

::: zone target="docs"

**Passare alla [panoramica di Azure Time Series Insights](https://docs.microsoft.com/azure/time-series-insights/time-series-insights-update-overview)**

::: zone-end

::: zone target="chromeless"

### <a name="action"></a>Azione

Per creare un ambiente Azure Time Series Insights:

1. Passare ad **Ambienti Time Series Insights**.
2. Selezionare **Crea ambiente Time Series Insights**.
3. In questo ambiente definire un puntatore a un'origine evento, ovvero Hub IoT o Hub eventi di Azure.

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.TimeSeriesInsights%2Fenvironments]" submitText="Go to Azure Time Series Insights" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end
