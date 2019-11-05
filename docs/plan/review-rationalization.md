---
title: Esaminare le decisioni sulla razionalizzazione
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Esaminare le decisioni sulla razionalizzazione
author: BrianBlanchard
ms.author: brblanch
ms.date: 07/01/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: plan
ms.openlocfilehash: a5ccbe2f3dd754914997ccba7b49ba47505dffa3
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73564147"
---
# <a name="review-rationalization-decisions"></a>Esaminare le decisioni sulla razionalizzazione

Durante le fasi iniziali della strategia e della pianificazione, è consigliabile applicare un approccio di [razionalizzazione incrementale](../digital-estate/rationalize.md#incremental-rationalization) al patrimonio digitale. Tuttavia, questo approccio incorpora alcune ipotesi nelle decisioni risultanti. Microsoft consiglia al team di strategia cloud e ai team di adozione del cloud di esaminare le decisioni in modo chiaro dalla documentazione espansa del carico di lavoro. Questa revisione rappresenta anche il momento ideale per coinvolgere gli stakeholder aziendali e gli sponsor esecutivi nelle decisioni relative agli Stati futuri.

> [!IMPORTANT]
> Durante la fase di valutazione della migrazione si verificherà un'ulteriore convalida delle decisioni di razionalizzazione. Questa convalida è incentrata sulla revisione aziendale della razionalizzazione per allineare le risorse in modo appropriato.

Per convalidare le decisioni di razionalizzazione, utilizzare le domande seguenti per facilitare una conversazione con l'azienda. Le domande sono raggruppate in base all'allineamento di razionalizzazione probabile.

## <a name="innovation-indicators"></a>Indicatori di innovazione

Se la revisione congiunta delle domande seguenti genera una risposta "Sì", un carico di lavoro potrebbe essere un candidato migliore per l'innovazione. Non verrà eseguita la migrazione di tale carico di lavoro tramite un modello lift-and-Shift o modernizzate. Al contrario, la logica di business o le strutture di dati verrebbero ricreate come un'applicazione nuova o riprogettata. Questo approccio può essere più laborioso e richiede molto tempo. Tuttavia, per un carico di lavoro che rappresenta una significativa redditività, l'investimento è giustificato.

- Le applicazioni in questo carico di lavoro creano una differenziazione del mercato?
- Un investimento proposto o approvato mira a migliorare le esperienze associate alle applicazioni in questo carico di lavoro?
- I dati in questo carico di lavoro rendono disponibili nuove offerte di prodotti o servizi?
- È previsto un investimento proposto o approvato mirato a sfruttare i dati associati a questo carico di lavoro?
- È possibile quantificare l'effetto della differenziazione del mercato o delle nuove offerte? In caso affermativo, restituisce un risultato che giustifica l'aumento dei costi di innovazione durante l'adozione del cloud?

Le due domande seguenti possono essere utili per includere scenari tecnici di alto livello nella revisione della razionalizzazione. La risposta a "Sì" può identificare le modalità di contabilità o riduzione del costo associato all'innovazione.

- Le strutture di dati o la logica di business cambiano nel corso dell'adozione del cloud?
- Si tratta di una pipeline di distribuzione esistente usata per distribuire questo carico di lavoro nell'ambiente di produzione?

Se la risposta a una delle due domande è "Sì", il team deve considerare l'inclusione di questo carico di lavoro come candidato all'innovazione. Come minimo, il team deve contrassegnare questo carico di lavoro per la revisione dell'architettura per identificare le opportunità di modernizzazione.

## <a name="migration-indicators"></a>Indicatori di migrazione

La migrazione è un modo più rapido e conveniente per adottare il cloud. Ma non sfrutta le opportunità di innovazione. Prima di investire nell'innovazione, rispondere alle domande seguenti. Consentono di determinare se un modello di migrazione è più adatto per un carico di lavoro.

- Il codice sorgente supporta questa applicazione stabile? Si prevede che rimanga stabile e invariato durante l'intervallo di tempo del ciclo di rilascio?
- Questo carico di lavoro supporta oggi i processi aziendali di produzione? Questa operazione verrà eseguita nel corso del ciclo di rilascio?
- Si tratta di una priorità che questa operazione di adozione del cloud migliora la stabilità e le prestazioni di questo carico di lavoro?
- La riduzione dei costi associata a questo carico di lavoro è un obiettivo durante questo lavoro?
- La riduzione della complessità operativa per questo carico di lavoro è un obiettivo durante questa operazione?
- L'innovazione è limitata dall'architettura corrente o dai processi dell'operazione IT?

Se la risposta a una di queste domande è "Sì", è opportuno considerare un modello di migrazione per questo carico di lavoro. Questa raccomandazione è vera anche se il carico di lavoro è un candidato per l'innovazione.

Problemi di complessità operativa, costi, prestazioni o stabilità possono ostacolare i ritorni aziendali. È possibile usare il cloud per produrre rapidamente miglioramenti correlati a tali problemi. Se applicabile, è consigliabile usare l'approccio di migrazione per stabilizzare prima il carico di lavoro. Espandi quindi le opportunità di innovazione nell'ambiente cloud stabile e agile. Questo approccio fornisce ritorni a breve termine e riduce il costo necessario per la modifica a lungo termine.

> [!IMPORTANT]
> I modelli di migrazione includono la modernizzazione incrementale. L'utilizzo di architetture di piattaforma distribuita come servizio (PaaS) è un aspetto comune delle attività di migrazione. Sono anche modifiche di configurazione secondarie che usano i servizi della piattaforma. Il limite per la migrazione viene definito come una modifica sostanziale della logica di business o del supporto di strutture aziendali. Tale modifica è considerata un impegno di innovazione.

## <a name="update-the-project-plan"></a>Aggiornare il piano del progetto

Le competenze necessarie per l'attività di migrazione sono diverse da quelle necessarie per un impegno di innovazione. Durante l'implementazione di un piano di adozione del cloud, è consigliabile assegnare le attività di migrazione e innovazione a diversi team. Ogni team ha una propria iterazione, rilascio e cadenza di pianificazione. L'assegnazione di team distinti fornisce la flessibilità del processo per mantenere un piano di adozione del cloud, tenendo conto degli sforzi di innovazione e migrazione.

Quando si gestisce il piano di adozione del cloud in Azure DevOps, tale gestione si riflette cambiando l'elemento di lavoro padre (o epico) dalla migrazione cloud all'innovazione nel cloud. Questa modifica sottile contribuisce a garantire che tutti i partecipanti al piano di adozione del cloud possano tenere traccia rapidamente del lavoro richiesto e delle modifiche alle attività correttive. Questo rilevamento consente inoltre di allineare le assegnazioni appropriate al team di adozione del cloud pertinente.

Per piani di adozione complessi e di grandi dimensioni con più progetti distinti, è consigliabile aggiornare il percorso di iterazione. Se si modifica il percorso area, il carico di lavoro viene reso visibile solo al team assegnato a tale percorso area. Questa modifica può semplificare il lavoro del team di adozione del cloud riducendo il numero di attività visibili. Ma aggiunge complessità per i processi di gestione del progetto.

## <a name="next-steps"></a>Passaggi successivi

[Definire le iterazioni e le versioni](./iteration-paths.md) per iniziare a pianificare il lavoro.

> [!div class="nextstepaction"]
> [Definire le iterazioni e le versioni](./iteration-paths.md) per iniziare a pianificare il lavoro.
