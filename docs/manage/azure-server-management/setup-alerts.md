---
title: Configurare avvisi di base
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Configurare avvisi di base
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 5d7469f8613b38ffdaefb41410409fba0c9109fd
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565289"
---
# <a name="set-up-basic-alerts"></a>Configurare avvisi di base

Una parte essenziale della gestione delle risorse è la ricezione di notifiche quando si verificano problemi. Gli avvisi notificano in modo proattivo le condizioni critiche, in base ai trigger provenienti da metriche, log o problemi di integrità del servizio. Come parte del caricamento dei servizi di gestione del server di Azure, è possibile configurare avvisi e notifiche che consentono ai team IT di tenere a conoscenza di eventuali problemi.

## <a name="azure-monitor-alerts"></a>Avvisi di monitoraggio di Azure

Monitoraggio di Azure offre funzionalità di [avviso](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-overview) per ricevere notifiche tramite posta elettronica o messaggistica, in caso di problemi. Queste funzionalità sono basate su una piattaforma di monitoraggio dei dati comune che include log e metriche generati dai server e da altre risorse. Usando un set comune di strumenti in monitoraggio di Azure, è possibile analizzare i dati combinati da più risorse e usarli per attivare gli avvisi. Questi trigger possono includere:

- Valori delle metriche.
- Query di ricerca nei log.
- Eventi del log attività.
- Integrità della piattaforma Azure sottostante.
- Verifica la disponibilità del sito Web.

Per una descrizione più dettagliata delle origini dei dati di monitoraggio raccolti da questo servizio, vedere l' [elenco delle origini dati di monitoraggio di Azure](https://docs.microsoft.com/azure/azure-monitor/platform/data-sources) .

Per informazioni dettagliate sulla creazione e gestione manuale di avvisi tramite la portale di Azure, vedere la [documentazione di monitoraggio di Azure](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-metric).

## <a name="automated-deployment-of-recommended-alerts"></a>Distribuzione automatica degli avvisi consigliati

In questa guida si consiglia di creare un set di 15 avvisi per il monitoraggio dell'infrastruttura di base. Trovare gli script di distribuzione nel [repository GitHub di Azure Alert Toolkit](https://github.com/Microsoft/manageability-toolkits).

Questo pacchetto crea avvisi per:

- Spazio su disco insufficiente
- Memoria disponibile insufficiente
- Utilizzo CPU elevato
- Arresti imprevisti
- File System danneggiati
- Errori hardware comuni

Il pacchetto usa l'hardware di HP Server come esempio. Modificare le impostazioni nel file di configurazione associato per riflettere l'hardware OEM. È inoltre possibile aggiungere altri contatori delle prestazioni al file di configurazione. Per distribuire il pacchetto, eseguire il file New-CoreAlerts. ps1.

## <a name="next-steps"></a>Passaggi successivi

Informazioni sulle operazioni e sui meccanismi di sicurezza che supportano le operazioni in corso.

> [!div class="nextstepaction"]
> [Gestione e sicurezza continuativa](./ongoing-management-overview.md)
