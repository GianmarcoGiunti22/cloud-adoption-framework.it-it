---
title: "Guida all'innovazione di Azure: Democratizzare i dati"
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni su come democratizzare i dati con Azure.
author: absheik
ms.author: absheik
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.custom: fasttrack-new, AQC
ms.localizationpriority: high
ms.openlocfilehash: 65c1ecd1d722286fb495af3069862131629c35d1
ms.sourcegitcommit: 0d14d89b9004a65a322724342cb5086ad2c77467
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72777079"
---
::: zone target="docs"

# <a name="azure-innovation-guide-democratize-data"></a>Guida all'innovazione di Azure: Democratizzare i dati

::: zone-end

::: zone target="chromeless"

# <a name="democratize-data"></a>Democratizzare i dati

::: zone-end

Uno dei primi passaggi per democratizzare i dati consiste nel migliorarne l'individuabilità. La catalogazione e la gestione della condivisione dei dati possono aiutare le aziende a ottenere il massimo valore dagli asset informatici esistenti. Un catalogo di dati rende le origini facilmente individuabili e comprensibili per gli utenti che li gestiscono. Azure Data Catalog consente la gestione all'interno di un'organizzazione, mentre Condivisione dati di Azure consente la gestione e la condivisione all'esterno dell'organizzazione.

Anche i servizi di Azure che forniscono funzionalità di elaborazione dati, come Azure Time Series Insights e Analisi di flusso, vengono usati con successo da clienti e partner per le loro esigenze di innovazione.

# <a name="catalogtabcatalog"></a>[Catalogo](#tab/Catalog)

## <a name="azure-data-catalog"></a>Azure Data Catalog

Azure Data Catalog soddisfa le esigenze di individuazione dei consumer di dati, oltre a consentire ai producer di dati di gestire gli asset informatici. Consente di ridurre le distanze tra IT e azienda, in modo che ognuno possa contribuire con le proprie intuizioni, di lasciare i dati live dove si vuole, di accedere con gli strumenti preferiti e di controllare chi può individuare gli asset di dati registrati. Inoltre, si integra con gli strumenti e i processi esistenti tramite API REST aperte.

> [!div class="checklist"]
>
> - Register
> - Ricerca e annotazione
> - Connessione e gestione

::: zone target="docs"

**Passare ad [Azure Data Catalog](https://docs.microsoft.com/azure/data-catalog).**

::: zone-end

::: zone target="chromeless"

### <a name="action"></a>Azione

Per ogni organizzazione è supportata una sola istanza di Azure Data Catalog. Se è già stato creato un catalogo per l'organizzazione, non è possibile aggiungerne altri.

Per creare un'istanza di Azure Data Catalog per l'organizzazione:

1. Passare ad **Azure Data Catalog**.
2. Fare clic sul pulsante **Create** (Crea).

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.DataCatalog%2Fcatalogs]" submitText="Go to Azure Data Catalog" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

# <a name="sharetabshare"></a>[Share](#tab/Share) (Condividi)

## <a name="azure-data-share"></a>Condivisione dati di Azure

L'equilibrio tra la condivisione aperta dei dati e la possibilità di controllare quali dati condividere e con chi rappresenta un importante fattore trainante per l'innovazione. Nel tentativo di democratizzare i dati, le organizzazioni possono essere facilmente sopraffatte dall'enorme quantità disponibile, dal ritmo di crescita e dal ciclo di vita di tali dati. Con Condivisione dati di Azure, il provider può mantenere il controllo del modo in cui vengono gestiti i dati specificando apposite condizioni per la condivisione. Il consumer dei dati deve accettare queste condizioni prima di iniziare a riceverli. I provider di dati possono specificare la frequenza con cui i consumer ricevono gli aggiornamenti. L'accesso a nuovi aggiornamenti può essere revocato in qualsiasi momento dal provider di dati.

> [!div class="checklist"]
>
> - Creare una condivisione dati.
> - Aggiungere set di dati alla condivisione dati.
> - Abilitare una pianificazione della sincronizzazione per la condivisione dati.
> - Aggiungere i destinatari alla condivisione dati.

::: zone target="docs"
**Passare a [Condivisione dati di Azure](https://docs.microsoft.com/azure/data-share).**

::: zone-end

::: zone target="chromeless"

<!-- markdownlint-disable MD024 -->

### <a name="action"></a>Azione

Per creare una condivisione dati di Azure:

1. Passare a **Condivisione dati di Azure**.
2. Fare clic su **Create Data Share** (Crea condivisione dati).

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.DataShare%2Faccounts]" submitText="Go to Azure Data Share" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

Usare i [set di dati aperti di Azure](https://docs.microsoft.com/azure/open-datasets/overview-what-are-open-datasets) per migliorare l'analisi incorporando dati su [festività](https://azure.microsoft.com/services/open-datasets/catalog/public-holidays), [meteo](https://azure.microsoft.com/services/open-datasets/catalog/noaa-global-forecast-system) e [immagini spaziali](https://azure.microsoft.com/services/open-datasets/catalog/hls) nei modelli.

Nei passaggi successivi vengono fornite informazioni sulla [democratizzazione dei processi aziendali](https://docs.microsoft.com/business-applications-release-notes/october18/microsoft-flow/democratize-business-processes) e sul [supporto per sviluppatori non professionisti](https://docs.microsoft.com/business-applications-release-notes/october18/microsoft-flow/empower-citizen-developers).

# <a name="insightstabinsights"></a>[Insights](#tab/Insights)

## <a name="azure-time-series-insights"></a>Azure Time Series Insights

L'innovazione dei dati offre infinite possibilità, come l'esplorazione quasi in tempo reale di flussi di dati e l'archiviazione in più livelli per i dati e i modelli delle serie temporali su scala IoT, per contestualizzare i dati di telemetria non elaborati e ricavarne informazioni basate sugli asset. La piattaforma Time Series Insights offre l'integrazione uniforme e continua con altre soluzioni per i dati, con l'analisi della causa radice e il rilevamento delle anomalie, anche con opzioni di applicazioni personalizzate.

> [!div class="checklist"]
>
> - Pianificare l'ambiente Time Series Insights.
> - Visualizzare i dati nello strumento di esplorazione.
> - Comprendere la conservazione dei dati.
> - Sviluppare e condividere visualizzazioni personalizzate.

::: zone target="docs"

**Passare ad [Azure Time Series Insights](https://docs.microsoft.com/azure/time-series-insights/time-series-insights-update-overview).**

::: zone-end

::: zone target="chromeless"

<!-- markdownlint-disable DOCSMD001 -->

### <a name="action"></a>Azione

Per creare un ambiente Azure Time Series Insights:

1. Passare ad **Azure Time Series Insights**.
2. Fare clic su **Crea ambiente Time Series Insights**.
3. Puntare questo ambiente a un'origine evento, ossia un hub IoT o un hub eventi.

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.TimeSeriesInsights%2Fenvironments]" submitText="Go to Azure Time Series Insights" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end
