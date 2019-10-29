---
title: 'Guida al monitoraggio del cloud: raccogliere i dati corretti'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Scegliere quando usare monitoraggio di Azure o System Center Operations Manager in Microsoft Azure
author: MGoedtel
ms.author: magoedte
ms.date: 06/26/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: operate
services: azure-monitor
ms.openlocfilehash: 0328ea8487817b9c8b74bda2200af9353a56e047
ms.sourcegitcommit: 74c1eb00a3bfad1b24f43e75ae0340688e7aec48
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72979830"
---
# <a name="cloud-monitoring-guide-collect-the-right-data"></a>Guida al monitoraggio del cloud: raccogliere i dati corretti

Questo articolo descrive alcune considerazioni per la raccolta dei dati di monitoraggio in un'applicazione cloud.

Per osservare l'integrità e la disponibilità della soluzione cloud, è necessario configurare gli strumenti di monitoraggio per raccogliere un livello di segnali basati su stati di errore prevedibili. Questi segnali sono i sintomi dell'errore e non la loro origine. Gli strumenti di monitoraggio usano le metriche e, per la diagnostica avanzata e l'analisi delle cause principali, log.

Pianificare con attenzione il monitoraggio e la migrazione. Per iniziare, includere il servizio di monitoraggio proprietario, il responsabile delle operazioni e altri membri del personale correlato durante la fase di pianificazione e continuare a coinvolgerli durante il ciclo di sviluppo e rilascio. Lo scopo è quello di sviluppare una configurazione di monitoraggio basata sui criteri seguenti:

- Qual è la composizione del servizio e sono attualmente monitorate le dipendenze? In caso affermativo, sono presenti più strumenti necessari? Esiste un'opportunità per consolidare, senza introdurre rischi?
- Qual è il contratto di servizio del servizio e come viene misurato e segnalato?
- Come dovrebbe apparire il dashboard del servizio quando viene generato un evento imprevisto? Come dovrebbe apparire il dashboard per il proprietario del servizio e per il team che supporta il servizio?
- Quali metriche produce la risorsa che è necessario monitorare?  
- In che modo il proprietario del servizio, i team di supporto e gli altri addetti alla ricerca nei log?

La modalità di risposta a tali domande e i criteri per l'invio di avvisi determinano la modalità di utilizzo della piattaforma di monitoraggio. Se si esegue la migrazione da una piattaforma di monitoraggio esistente o da un set di strumenti di monitoraggio, usare la migrazione come opportunità per rivalutare i segnali raccolti. Ciò vale soprattutto per il caso in cui è necessario considerare diversi fattori di costo quando si esegue la migrazione o l'integrazione con una piattaforma di monitoraggio basata sul cloud, ad esempio monitoraggio di Azure. Tenere presente che il monitoraggio dei dati deve essere praticabile. È necessario aver raccolto i dati ottimizzati per offrire una visualizzazione a 10.000 piedi dell'integrità complessiva del servizio. La strumentazione definita per identificare gli eventi imprevisti reali dovrebbe essere il più semplice, prevedibile e affidabile possibile.

## <a name="develop-a-monitoring-configuration"></a>Sviluppare una configurazione di monitoraggio

Il proprietario e il team del servizio di monitoraggio seguono in genere un set comune di attività per sviluppare una configurazione di monitoraggio. Queste attività iniziano nelle fasi di pianificazione iniziali, continuano a eseguire il test e la convalida in un ambiente non di produzione e si estendono alla distribuzione nell'ambiente di produzione. Le configurazioni di monitoraggio derivano da modalità di errore note, risultati dei test di errori simulati e l'esperienza di diverse persone nell'organizzazione (il Service Desk, le operazioni, i tecnici e gli sviluppatori). Tali configurazioni presuppongono che il servizio esista già, viene migrato nel cloud e non è stato riprogettato.

Per ottenere risultati qualitativi a livello di servizio, monitorare l'integrità e la disponibilità di questi servizi nelle fasi iniziali del processo di sviluppo. Se si monitora la progettazione del servizio o dell'applicazione come un ripensamento, i risultati non saranno riusciti.

Per una risoluzione più rapida dell'evento imprevisto, tenere presenti le raccomandazioni seguenti:

- Definire un dashboard per ogni componente del servizio.
- Usare le metriche per facilitare la diagnosi e identificare una risoluzione o una soluzione alternativa del problema se non è possibile individuare una causa principale.
- Usare le funzionalità di drill-down del dashboard o supportare la personalizzazione della visualizzazione per rifinirla.
- Se sono necessari log dettagliati, le metriche dovrebbero avere consentito di individuare i criteri di ricerca. Se le metriche non sono state utili, migliorarle per l'evento imprevisto successivo.

L'adozione di questo set di principi guida consente di ottenere informazioni dettagliate quasi in tempo reale, nonché una migliore gestione del servizio.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Strategia di avviso](./alerting.md)
