---
title: "Guida all'innovazione di Azure: Interagire tramite dispositivi"
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Guida all'innovazione di Azure - Interagire tramite dispositivi
author: umarmohamedusman
ms.author: umarm
ms.date: 10/10/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.custom: fasttrack-new, AQC
ms.localizationpriority: high
ms.openlocfilehash: 8f7882a28dc135763584c8f2af4f5d834160f3ba
ms.sourcegitcommit: 7ffb0427bba71177f92618b2f980e864b72742f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/29/2019
ms.locfileid: "73047563"
---
::: zone target="docs"

# <a name="azure-innovation-guide-interact-through-devices"></a>Guida all'innovazione di Azure: Interagire tramite dispositivi

::: zone-end

::: zone target="chromeless"

# <a name="interact-through-devices"></a>Interagire tramite dispositivi

::: zone-end

L'innovazione si può realizzare tramite dispositivi perimetrali percettivi e connessi in modo intermittente, con la possibilità di orchestrare milioni di dispositivi, acquisire ed elaborare quantità illimitate di dati e sfruttare un numero crescente di esperienze multisensoriali e multidispositivo. Per i dispositivi al perimetro della rete, Azure fornisce un framework per la creazione di soluzioni aziendali immersive ed efficaci. Il modello di ubiquitous computing, reso possibile dalla combinazione di Azure con la tecnologia di intelligenza artificiale, consente di creare qualsiasi tipo immaginabile di applicazione e sistema intelligente.

I clienti di Azure usano un set in continua espansione di sistemi e dispositivi connessi che raccolgono e analizzano i dati, vicino agli utenti, ai dati o a entrambi. Gli utenti ricevono informazioni ed esperienze in tempo reale, distribuite da app con riconoscimento del contesto e altamente reattive. Spostando parte del carico di lavoro nei dispositivi perimetrali, è possibile ridurre il tempo da dedicare all'invio di messaggi nel cloud e reagire più rapidamente agli eventi spaziali.

> [!div class="checklist"]
>
> - Asset industriali
> - HoloLens 2
> - Azure Sphere
> - Kinect DK
> - Droni
> - Database SQL Edge di Azure
> - Plug and Play IoT

<!-- markdownlint-disable MD025 -->

## <a name="global-scale-iot-servicetabiothub"></a>[Servizio IoT su scala globale](#tab/IoTHub)

<!-- markdownlint-enable MD025 -->

È possibile progettare soluzioni che usano la comunicazione bidirezionale con miliardi di dispositivi IoT, Fanno inoltre uso dei dati di telemetria predefiniti da dispositivo a cloud per acquisire informazioni sullo stato dei dispositivi e definire route per i messaggi da inviare ad altri servizi di Azure solo tramite configurazione. Sfruttando i messaggi da cloud a dispositivo, è possibile inviare in modo affidabile comandi e notifiche ai dispositivi connessi e tenere traccia del recapito con la conferma di ricezione. È inoltre possibile ripetere automaticamente l'invio di messaggi dei dispositivi in base alla necessità per supportare la connettività intermittente.

Di seguito sono elencate alcune funzionalità disponibili:

- **Canale di comunicazione con sicurezza avanzata** per l'invio e la ricezione di dati da dispositivi IoT.
- **Gestione dei dispositivi incorporata** e provisioning predefinito per la connessione e la gestione di dispositivi IoT su larga scala.
- **Piena integrazione completa con Griglia di eventi** ed elaborazione serverless per semplificare lo sviluppo di applicazioni IoT.
- **Compatibilità con Azure IoT Edge** per la creazione di applicazioni IoT ibride.

::: zone target="docs"

**Passare all'[hub IoT](https://docs.microsoft.com/azure/iot-dps)**

**Passare ai [servizi di provisioning di dispositivi](https://docs.microsoft.com/azure/iot-dps)**

::: zone-end

::: zone target="chromeless"

### <a name="action"></a>Azione

Per creare un hub IoT:

1. Passare a **Hub IoT**.
2. Selezionare **Create IoT hub** (Crea hub IoT).

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResource/resourceType/Microsoft.Devices%2FIotHubs]" submitText="Go to IoT Hub" :::

<!-- markdownlint-enable DOCSMD001 -->

Il servizio Device Provisioning in hub IoT è un servizio di supporto per l'hub IoT che consente il provisioning JIT completamente automatico.

<!-- markdownlint-disable MD024 -->

### <a name="action"></a>Azione

Per creare servizi Device Provisioning in hub IoT:

1. Passare a **Servizi Device Provisioning in hub IoT**.
2. Selezionare **Create Device Provisioning Services** (Crea servizi Device Provisioning).

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResource/resourceType/Microsoft.Devices%2FProvisioningServices]" submitText="Go to Device Provisioning Services" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

<!-- markdownlint-disable MD025 -->

## <a name="azure-digital-twinstabdigitaltwins"></a>[Gemelli digitali di Azure](#tab/DigitalTwins)

È possibile creare esperienze riutilizzabili, ampiamente scalabili e con riconoscimento dello spazio che collegano flussi di dati nel mondo fisico e digitale, migliorare l'engagement dei clienti con modelli completi di ambienti fisici, generare grafici di intelligenza spaziale per modellare le relazioni e le interazioni tra persone, spazi e dispositivi, nonché eseguire query sui dati da uno spazio fisico invece che da sensori distinti.

**Modelli a oggetti di Gemelli digitali di Azure:** con i modelli a oggetti e le ontologie dei gemelli digitali, è possibile modellare un'ontologia che descrive aree, sedi, piani, uffici, zone, sale riunioni e sale dedicate di un edificio intelligente, oppure varie centrali elettriche, sottostazioni, risorse energetiche e clienti di una rete elettrica.

**Grafico di intelligenza spaziale:** il grafico gerarchico di spazi, dispositivi e persone definito nel modello a oggetti di Gemelli digitali che supporta ereditarietà, filtro, attraversamento, scalabilità ed estendibilità. È possibile gestire e interagire con il grafico spaziale tramite una raccolta di API REST ospitate in Azure.

::: zone target="docs"

**Passare a [Gemelli digitali di Azure](https://docs.microsoft.com/azure/digital-twins/about-digital-twins)**

::: zone-end

::: zone target="chromeless"

### <a name="action"></a>Azione

Per creare Gemelli digitali di Azure:

1. Nel riquadro a sinistra selezionare **Crea risorsa**.
2. Cercare **gemelli digitali** e quindi selezionare **Gemelli digitali**.
3. Selezionare **Crea** per avviare il processo di distribuzione.
4. Per esaminare i gemelli digitali esistenti, selezionare questo pulsante:

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResource/resourceType/Microsoft.IoTSpaces%2FGraph]" submitText="Go to Digital Twins" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

<!-- markdownlint-disable MD025 -->

## <a name="location-intelligencetabazuremaps"></a>[Intelligenza della posizione](#tab/AzureMaps)

Oltre alle tradizionali funzionalità di localizzazione, come prossimità, traffico e routing, il servizio Mappe di Azure consente alle organizzazioni di creare soluzioni usando le funzionalità in tempo reale di intelligenza della posizione rese disponibili dai partner tecnologici di fama mondiale per la mobilità, **TomTom** e **Moovit**. Con i servizi geospaziali è possibile integrare con facilità le funzionalità avanzate per posizione e mobilità nelle applicazioni.

**Servizio dati (anteprima):** è possibile caricare e archiviare dati geospaziali per l'uso con operazioni spaziali o composizione di immagini per ridurre la latenza, incrementare la produttività e abilitare nuovi scenari nelle applicazioni.

**Operazioni spaziali:** una libreria di calcoli matematici geospaziali comuni, tra cui geofencing, punto più vicino, ortodromia e buffer, ottimizza l'intelligenza della posizione.

**Georilevazione:** è possibile cercare il paese a cui corrisponde a un indirizzo IP, personalizzare contenuti e servizi in base alla posizione dell'utente e acquisire informazioni dettagliate sulla distribuzione geografica dei clienti.

::: zone target="docs"

**Passare a [Mappe di Azure](https://docs.microsoft.com/azure/azure-maps)**

::: zone-end

::: zone target="chromeless"

### <a name="action"></a>Azione

Per usare l'intelligenza della posizione:

1. Passare ad **Account Mappe di Azure**.
2. Selezionare **Crea account Mappe di Azure**.

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Maps%2Faccounts]" submitText="Go to Azure Maps Account" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="spatial-experiencestabspatial"></a>[Esperienze spaziali](#tab/spatial)

Ancoraggi nello spazio di Azure consente agli sviluppatori di usare piattaforme di realtà mista per percepire lo spazio, designare punti di interesse precisi e richiamarli dai dispositivi supportati.

**Aggiunta di contesto al mondo reale:** posizionando e connettendo il contenuto digitale a punti di interesse fisici, è possibile offrire agli utenti maggiori informazioni sui dati, dove e quando necessario.

**Condivisione di ologrammi in più dispositivi:** offrendo funzionalità 3D al team e ai clienti nei dispositivi che preferiscono, è possibile accelerare decisioni e risultati. Ancoraggi nello spazio consente a persone presenti nello stesso posto di partecipare ad applicazioni di realtà mista multiutente.

**Esperienze coinvolgenti:** è possibile creare relazioni tra ancoraggi dello spazio per connetterli e offrire un'esperienza utente che può includere due o più punti di interesse con cui un utente deve interagire per completare un'attività. L'app può consentire a un utente di inserire un artefatto virtuale nel mondo reale. In un ambiente industriale, un utente potrebbe ricevere informazioni contestuali su una macchina puntandovi la fotocamera di un dispositivo supportato.

Ancoraggi nello spazio di Azure è costituito da un servizio gestito e da SKD client per le piattaforme di dispositivi supportate.

::: zone target="docs"

**Passare a [Ancoraggi nello spazio di Azure](https://azure.microsoft.com/services/spatial-anchors)**

::: zone-end

::: zone target="chromeless"

### <a name="action"></a>Azione

Per usare esperienze spaziali:

1. Passare a **Account ancoraggi nello spazio**.
2. Selezionare **Create spatial anchors accounts** (Crea account ancoraggio nello spazio).

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResource/resourceType/Microsoft.MixedReality%2FspatialAnchorsAccounts]" submitText="Go to Spatial Anchors Accounts" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end

## <a name="azure-remote-renderingtabremoterender"></a>[Rendering remoto di Azure](#tab/RemoteRender)

È possibile eseguire il rendering di contenuti 3D interattivi di qualità elevata e trasmetterli in streaming ai dispositivi in tempo reale. I carichi di lavoro di rendering vengono usati in modo intensivo per gli effetti speciali (VFX) nel settore di media e intrattenimento. Il rendering viene usato anche in molti altri settori, tra cui quelli pubblicitario, manifatturiero, petrolchimico e della vendita al dettaglio.

Il processo di rendering è a uso intensivo di calcoli. Può essere necessario produrre molti fotogrammi o immagini e il rendering di ogni immagine può richiedere diverse ore. Di conseguenza, il rendering è un carico di lavoro perfetto per l'elaborazione batch ed è possibile usare Azure e Azure Batch per eseguire molte operazioni in parallelo.

::: zone target="docs"

**Passare a [Rendering remoto di Azure](https://azure.microsoft.com/services/remote-rendering)**

**Passare a [Rendering tramite Azure](https://docs.microsoft.com/azure/batch/batch-rendering-service)**

::: zone-end

::: zone target="chromeless"

### <a name="action"></a>Azione

Per usare Rendering remoto:

1. Passare ad **Account Batch**.
2. Selezionare **Create batch accounts** (Crea account Batch).

<!-- markdownlint-disable DOCSMD001 -->

::: form action="OpenBlade[#blade/HubsExtension/BrowseResourceBlade/resourceType/Microsoft.Batch%2FbatchAccounts]" submitText="Go to Azure Batch" :::

<!-- markdownlint-enable DOCSMD001 -->

::: zone-end
