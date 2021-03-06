---
title: Guida al monitoraggio del cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Panoramica di Monitoraggio di Azure e System Center Operations Manager
author: MGoedtel
ms.author: magoedte
ms.date: 07/31/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: operate
services: azure-monitor
ms.openlocfilehash: 0920e834bcec0fc5885650ba5cab7ec28eac669f
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73752786"
---
# <a name="cloud-monitoring-guide-introduction"></a>Guida al monitoraggio del cloud: Introduzione

Il cloud cambia sostanzialmente il modo in cui le aziende ottengono e usano le risorse tecnologiche. In passato le aziende si assumevano la proprietà e la responsabilità di tutti i livelli della tecnologia, dall'infrastruttura al software. Il cloud offre ora alle aziende la possibilità di effettuare il provisioning delle risorse e utilizzarle in base a esigenze specifiche.

Benché il cloud offra flessibilità quasi illimitata a livello di opzioni di progettazione, le aziende cercano una metodologia convalidata e coerente per l'adozione delle tecnologie cloud. Ogni azienda ha obiettivi e tempistiche diverse per l'adozione del cloud, quindi un approccio unico per tutte le situazioni è quasi impossibile.

![Diagramma delle strategie di adozione del cloud](./media/monitoring-management-guidance-cloud-and-on-premises/introduction-cloud-adoption.png)

La trasformazione digitale offre anche l'opportunità di modernizzare l'infrastruttura, i carichi di lavoro e le applicazioni. In base alla strategia e agli obiettivi aziendali, l'adozione di un modello di cloud ibrido fa probabilmente parte del percorso di migrazione dall'ambiente locale alla piena operatività nel cloud. Durante questo percorso trasformativo, i team IT non devono solo occuparsi di adottare il cloud e realizzare rapidamente valore dalla nuova infrastruttura. Devono anche capire come monitorare efficacemente la migrazione di applicazioni o servizi ad Azure, continuando ad assicurare l'efficienza delle operazioni IT e DevOps.

Gli stakeholder sono interessati a sfruttare strumenti basati sul cloud di tipo SaaS (Software as a Service) per il monitoraggio e la gestione. Vogliono capire quali servizi e soluzioni adottare per ottenere visibilità completa, ridurre i costi e dedicare meno risorse all'infrastruttura e alla manutenzione dei tradizionali strumenti basati su software per le operazioni IT.

I team IT, però, spesso preferiscono continuare a usare gli strumenti per cui hanno sostenuto investimenti significativi. Grazie a questo approccio possono supportare i processi e le operazioni dei servizi e monitorare entrambi i modelli cloud, con l'obiettivo finale di passare a un'offerta basata su SaaS. I team IT preferiscono questo approccio non solo perché il cambiamento richiede tempo, pianificazione, risorse e finanziamenti, ma anche perché non sempre è immediato capire quali prodotti o servizi di Azure sono appropriati o applicabili per eseguire la transizione.

L'obiettivo di questa guida è fornire informazioni di riferimento dettagliate per aiutare responsabili IT, decisori aziendali, architetti di applicazioni e sviluppatori a individuare:

* Le piattaforme di monitoraggio di Azure, con una panoramica e un confronto delle funzionalità che offrono.
* La soluzione ideale per il monitoraggio di carichi di lavoro ibridi, privati e nativi di Azure.
* L'approccio consigliato per il monitoraggio end-to-end sia dell'infrastruttura che delle applicazioni incluse le soluzioni distribuibili per la migrazione di questi carichi di lavoro comuni in Azure.

La guida non include procedure per l'uso o la configurazione di singoli servizi e soluzioni di Azure, ma vi fa riferimento, se applicabili o disponibili. Dopo aver letto questa guida, sarà possibile capire come gestire con successo un carico di lavoro seguendo procedure e modelli consigliati.

Se non si ha familiarità con Monitoraggio di Azure e System Center Operations Manager e si vogliono acquisire maggiori informazioni sulle caratteristiche esclusive che offrono e sulle differenze tra i due servizi, vedere la [panoramica delle piattaforme di monitoraggio](./platform-overview.md).

## <a name="audience"></a>Audience

I principali destinatari di questa guida includono amministratori di aziende, reparto operativo IT, reparto di sicurezza e conformità IT, architetti di applicazioni, titolari dello sviluppo e delle attività operative dei carichi di lavoro.

## <a name="how-this-guide-is-structured"></a>Struttura della guida

Questo articolo fa parte di una serie. Gli articoli seguenti sono concepiti per essere letti insieme, nell'ordine indicato:

* Introduzione (questo articolo)
* [Strategia di monitoraggio per i modelli di distribuzione cloud](./cloud-models-monitor-overview.md)
* [Raccogliere i dati appropriati](./data-collection.md)
* [Invio di avvisi](./alerting.md)

## <a name="products-and-services"></a>Prodotti e servizi

Per il monitoraggio e la gestione di un'ampia varietà di risorse ospitate in Azure, nella rete aziendale o in altri provider di servizi cloud, sono disponibili diversi prodotti software e servizi. Sono:

* System Center Operations Manager
* Monitoraggio di Azure, che ora include Log Analytics e Application Insights
* Criteri di Azure e Azure Blueprints
* Automazione di Azure
* App per la logica di Azure
* Hub eventi di Azure

Questa prima versione della guida illustra le piattaforme di monitoraggio correnti: Monitoraggio di Azure e System Center Operations Manager. Descrive inoltre la strategia consigliata per il monitoraggio di ognuno dei modelli di distribuzione cloud. È anche incluso il primo set di raccomandazioni per il monitoraggio, a partire dalla raccolta di dati e dagli avvisi.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Strategia di monitoraggio per i modelli di distribuzione cloud](./cloud-models-monitor-overview.md)
