---
title: Guida al monitoraggio del cloud-raccolta dei dati corretti
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Scegliere quando usare monitoraggio di Azure o System Center Operations Manager in Microsoft Azure
author: MGoedtel
ms.author: magoedte
ms.date: 06/26/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: operate
services: azure-monitor
ms.openlocfilehash: 8b0aebe00d987ac49ba965fc1982c1615372ba92
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71026965"
---
# <a name="cloud-monitoring-guide-collecting-the-right-data"></a>Guida al monitoraggio del cloud: Raccolta dei dati corretti

Questo articolo descrive alcune considerazioni per la raccolta dei dati di monitoraggio in un'applicazione cloud.

Per osservare l'integrità e la disponibilità della soluzione cloud, è necessario configurare gli strumenti di monitoraggio per raccogliere un livello di segnali basati su stati di errore prevedibili. Questi segnali sono i sintomi dell'errore e non la loro origine. Gli strumenti di monitoraggio usano le metriche e, nel caso di diagnostica avanzata e di analisi delle cause principali, usano anche i log.

Pianificare con attenzione il monitoraggio e la migrazione. Per iniziare, includere il servizio di monitoraggio proprietario, il responsabile delle operazioni e altri membri del personale correlato durante la fase di pianificazione e continuare a coinvolgerli durante il ciclo di sviluppo e rilascio. Lo scopo è quello di sviluppare una configurazione di monitoraggio basata sui criteri seguenti:

- Qual è la composizione del servizio e sono attualmente monitorate le dipendenze? In caso affermativo, sono presenti più strumenti necessari? Esiste un'opportunità per consolidare, senza introdurre rischi?
- Qual è il contratto di servizio del servizio e come viene misurato e segnalato?
- Come dovrebbe apparire il dashboard del servizio quando viene generato un evento imprevisto? Come dovrebbe apparire il dashboard per il proprietario del servizio e il team che supporta il servizio?
- Quali metriche produce la risorsa che è necessario monitorare?  
- In che modo il proprietario del servizio, i team di supporto e gli altri addetti alla ricerca nei log?

La modalità di risposta a tali domande e i criteri per l'invio di avvisi determinano la modalità di utilizzo della piattaforma di monitoraggio. Se si esegue la migrazione da una piattaforma di monitoraggio esistente o da un set di strumenti di monitoraggio, usare la migrazione come opportunità per rivalutare i segnali raccolti. Ciò vale soprattutto quando esistono diversi fattori di costo da considerare quando si esegue la migrazione o l'integrazione con una piattaforma di monitoraggio basata sul cloud come monitoraggio di Azure. Tenere presente che il monitoraggio dei dati deve essere praticabile. È necessario aver raccolto i dati ottimizzati per offrire una visualizzazione a 10.000 piedi dell'integrità complessiva del servizio. La strumentazione definita per identificare gli eventi imprevisti reali dovrebbe essere il più semplice, prevedibile e affidabile possibile.

## <a name="develop-a-monitoring-configuration"></a>Sviluppare una configurazione di monitoraggio

Il proprietario e il team del servizio di monitoraggio seguono in genere un set comune di attività per sviluppare una configurazione di monitoraggio. Queste attività iniziano nelle fasi di pianificazione iniziali, continuano a eseguire il test e la convalida in un ambiente non di produzione e si estendono alla distribuzione nell'ambiente di produzione. Le configurazioni di monitoraggio derivano da modalità di errore note, risultati dei test di errori simulati e l'esperienza di diverse persone nell'organizzazione (il Service Desk, le operazioni, i tecnici e gli sviluppatori). Tali configurazioni presuppongono che il servizio esista già, viene migrato nel cloud e non è stato riprogettato.

Monitorare l'integrità e la disponibilità di questi servizi nelle fasi iniziali del processo di sviluppo, per ottenere risultati qualitativi a livello di servizio. Se si monitora la progettazione del servizio o dell'applicazione come un ripensamento, i risultati non saranno riusciti.

Per una risoluzione più rapida dell'evento imprevisto, tenere presenti le raccomandazioni seguenti:

- Definire un dashboard per ogni componente del servizio.
- Usare le metriche per contribuire a una maggiore diagnosi, per identificare una soluzione o una soluzione alternativa del problema se non è possibile individuare una causa radice.
- Usare le funzionalità di drill-down del dashboard o supportare la personalizzazione della visualizzazione per rifinirla.
- Se sono necessari log dettagliati, le metriche dovrebbero avere consentito di individuare i criteri di ricerca. In caso contrario, migliorare le metriche per l'evento imprevisto successivo.

L'adozione di questo insieme di principi guida offre informazioni quasi in tempo reale, nonché una migliore gestione del servizio.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Strategia di avviso](./alerting.md)
