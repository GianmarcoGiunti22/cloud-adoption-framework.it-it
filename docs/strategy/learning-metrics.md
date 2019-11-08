---
title: In che modo è possibile allineare le attività alle metriche di apprendimento significative?
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Spiegazione del concetto di metriche di apprendimento
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: strategy
ms.openlocfilehash: b19357bd98858cc227426d2adb03a6e84210b9b3
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73753786"
---
<!-- markdownlint-disable MD026 -->

# <a name="how-can-we-align-efforts-to-meaningful-learning-metrics"></a>In che modo è possibile allineare le attività alle metriche di apprendimento significative?

La [Panoramica dei risultati aziendali](./business-outcomes/index.md) ha illustrato modi per misurare e comunicare l'effetto di una trasformazione nell'azienda. Sfortunatamente, alcuni di questi risultati possono richiedere anni per produrre risultati misurabili. La lavagna e C-Suite non sono contenti dei report che mostrano un Delta 0% per lunghi periodi di tempo.

Le metriche di apprendimento sono metriche provvisorie e a breve termine che possono essere associate ai risultati aziendali a lungo termine. Queste metriche si allineano bene con una mentalità di crescita e consentono di posizionare le impostazioni cultura per diventare più resilienti. Piuttosto che evidenziare la mancanza di avanzamento prevista per un obiettivo aziendale a lungo termine, le metriche di apprendimento evidenziano i primi indicatori di successo. Le metriche evidenziano anche i primi indicatori di errore, che probabilmente producono la massima opportunità per apprendere e modificare il piano.

Come per la maggior parte del materiale presente in questo Framework, si presuppone che l'utente abbia familiarità con il [percorso di trasformazione](../govern/guides/index.md) che meglio si allinea ai risultati aziendali desiderati. In questo articolo vengono illustrate alcune metriche di apprendimento per ogni percorso di trasformazione per illustrare il concetto.

## <a name="cloud-migration"></a>Migrazione cloud

Questa trasformazione è incentrata su costi, complessità ed efficienza, con particolare attenzione alle operazioni IT. I dati più facilmente misurati dietro questa trasformazione sono lo spostamento delle risorse nel cloud. In questo tipo di trasformazione, l'area digitale è misurata da macchine virtuali (VM), rack o cluster che ospitano tali VM, i costi operativi del datacenter, le spese di capitale obbligatorie per la gestione dei sistemi e l'ammortamento di tali asset nel tempo.

Quando le macchine virtuali vengono spostate nel cloud, la dipendenza dalle risorse legacy locali è ridotta. Anche il costo della manutenzione degli asset è ridotto. Sfortunatamente, le aziende non possono realizzare la riduzione dei costi fino a quando non viene effettuato il deprovisioning dei cluster e la scadenza dei lease dei data center. In molti casi, il valore completo dello sforzo non viene realizzato fino al completamento dei cicli di ammortamento.

È sempre consigliabile allinearsi con il CFO o l'ufficio finanziario prima di prendere le istruzioni finanziarie. Tuttavia, i team IT possono in genere stimare i costi monetari correnti e i valori di costo monetario futuri per ogni macchina virtuale in base alla CPU, alla memoria e allo spazio di archiviazione utilizzato. È quindi possibile applicare tale valore a ogni macchina virtuale migrata per stimare il risparmio di costi immediato e il valore monetario futuro del lavoro richiesto.

## <a name="application-innovation"></a>Innovazione delle applicazioni

L'innovazione delle applicazioni abilitata per il cloud è incentrata principalmente sull'esperienza dei clienti e sulla volontà del cliente di utilizzare i prodotti e i servizi forniti dall'azienda. Il tempo necessario per incrementi di modifiche influisce sui comportamenti di acquisto dei clienti o dei clienti. Tuttavia, i cicli di innovazione delle applicazioni tendono a essere molto più brevi rispetto alle altre forme di trasformazione. Il suggerimento tradizionale è che è necessario iniziare con una comprensione dei comportamenti specifici che si desidera influenzare e utilizzare tali comportamenti come metriche di apprendimento. Ad esempio, in un'applicazione di e-commerce, gli acquisti totali o gli acquisti di componenti aggiuntivi potrebbero essere il comportamento di destinazione. Per una società video, il tempo di osservazione dei flussi video potrebbe essere la destinazione.

La sfida con le metriche del comportamento dei clienti è che possono essere facilmente influenzate da variabili esterne. Quindi, è spesso importante includere statistiche correlate con le metriche di apprendimento. Queste statistiche correlate possono includere la cadenza di rilascio, i bug risolti per versione, code coverage di unit test, il numero di visualizzazioni di pagina, la velocità effettiva della pagina, il tempo di caricamento della pagina e altre metriche delle prestazioni dell'app. Ognuno può mostrare diverse attività e modifiche alla codebase e l'esperienza del cliente per la correlazione con modelli di comportamento dei clienti di livello superiore.

## <a name="data-innovation"></a>Innovazione dei dati

La modifica di un settore, l'interferenza dei mercati o la trasformazione di prodotti e servizi possono richiedere anni. In un'attività di innovazione dei dati abilitata per il cloud, la sperimentazione è fondamentale per misurare il successo. Essere trasparente condividendo le metriche di stima, ad esempio la percentuale di probabilità, il numero di esperimenti non riusciti e il numero di modelli sottoposti a training. Gli errori si accumuleranno più velocemente dei successi. Queste metriche possono essere scoraggianti e il team dirigente deve comprendere il tempo e l'investimento necessari per usare correttamente queste metriche.

D'altra parte, alcuni indicatori positivi sono spesso associati all'apprendimento basato sui dati: la centralizzazione di set di dati eterogenei, l'ingresso di dati e la democratizzazione dei dati. Mentre il team sta imparando a conoscere il cliente di domani, è possibile produrre risultati reali. Il supporto delle metriche di apprendimento potrebbe includere:

- Numero di modelli disponibili
- Numero di origini dati partner utilizzate
- Dispositivi che producono dati in ingresso
- Volume dei dati in ingresso
- Tipi di dati

Una metrica ancora più preziosa è il numero di dashboard creati da origini dati combinate. Questo numero riflette i processi aziendali di stato attuale interessati da nuove origini dati. Condividendo le nuove origini dati in modo aperto, l'azienda può sfruttare i dati usando strumenti per la creazione di report come Power BI per produrre informazioni incrementali e promuovere il cambiamento aziendale.

## <a name="next-steps"></a>Passaggi successivi

Una volta allineate le metriche di apprendimento, si è pronti per iniziare a [valutare il patrimonio digitale](../digital-estate/index.md) in base a tali metriche. Il risultato sarà un [backlog di trasformazione o di migrazione](../migrate/migration-considerations/prerequisites/technical-complexity.md).

> [!div class="nextstepaction"]
> [Valutazione del patrimonio digitale](../digital-estate/index.md)
