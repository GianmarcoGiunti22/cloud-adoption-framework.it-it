---
title: Ruolo della replica e della sincronizzazione nel processo di migrazione
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Processo nell'ambito della migrazione al cloud che è incentrato sulle attività di migrazione dei carichi di lavoro nel cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 62c12796abf8921c13cebe471fe555d012bab15c
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72549134"
---
<!-- markdownlint-disable MD026 -->

# <a name="what-role-does-replication-play-in-the-migration-process"></a>Ruolo della replica nel processo di migrazione

I data center locali contengono asset fisici, ad esempio server, appliance e dispositivi di rete. Ogni server tuttavia è solo un involucro fisico. Il valore reale è associato ai dati binari in esecuzione sul server. Le applicazioni e i dati sono lo scopo del data center. Si tratta dei dati binari principali di cui eseguire la migrazione. Queste applicazioni e questi archivi dati sono potenziati da altri asset digitali e da altre origini di dati binari, ad esempio sistemi operativi, route di rete, file e protocolli di sicurezza.

La replica rappresenta il lavoro duro delle attività di migrazione. Si tratta del processo di copia di una versione temporizzata di vari dati binari. Gli snapshot dei dati binari vengono quindi copiati in una nuova piattaforma e distribuiti nel nuovo hardware in un processo denominato *seeding*. Se eseguita correttamente, la copia con seeding dei dati binari dovrebbe comportarsi in modo identico ai dati binari originali dell'hardware precedente. Lo snapshot dei dati binari però è immediatamente obsoleto e non allineato con l'origine. Per fare in modo che i nuovi dati binari e quelli precedenti siano allineati, un processo denominato *sincronizzazione* aggiorna continuamente la copia archiviata nella nuova piattaforma. La sincronizzazione continua fino a quando l'asset non viene promosso in allineamento con il modello di promozione scelto. A questo punto la sincronizzazione viene interrotta.

## <a name="required-prerequisites-to-replication"></a>Prerequisiti necessari per la replica

Prima della replica, la *nuova piattaforma* e l'hardware devono essere preparati a ricevere le copie dei dati binari. L'articolo sui [prerequisiti](../prerequisites/index.md) descrive i requisiti di ambiente minimi per la creazione di una piattaforma sicura, affidabile ed efficiente per la ricezione delle repliche dei dati binari.

Anche i *dati binari di origine* devono essere preparati per la replica e la sincronizzazione. Gli articoli sulla valutazione, l'architettura e la correzione illustrano le azioni necessarie per garantire che i dati binari di origine siano pronti per la replica e la sincronizzazione.

Per eseguire e gestire i processi di replica e sincronizzazione, è necessario implementare una *toolchain* allineata con i dati binari di origine e della nuova piattaforma. L'articolo sulle [opzioni di replica](./replicate-options.md) delinea diversi strumenti che possono contribuire a una migrazione ad Azure.

## <a name="replication-risks---physics-of-replication"></a>Rischi della replica - Fisica della replica

Quando si pianifica la replica di un'origine di dati binari in una nuova destinazione, è necessario prendere in considerazione alcune leggi fondamentali per la pianificazione e l'esecuzione.

- **Velocità della luce.** Quando si trasferiscono volumi elevati di dati, la fibra ottica è ancora l'opzione più rapida. I cavi in fibra ottica però possono spostare i dati solo a una velocità pari a due terzi della velocità della luce. Ciò significa che non esiste alcun metodo per la replica immediata o illimitata di dati.
- **Velocità della pipeline WAN.** Una maggiore consistenza della velocità di spostamento dei dati è la larghezza di banda uplink, che definisce il volume di dati al secondo che può essere trasferito sulla rete WAN esistente di una società nel Data Center di destinazione.
- **Espansione della velocità della WAN.** Se il budget lo consente, è possibile aggiungere altra larghezza di banda alla soluzione WAN di una società. Tuttavia, l'approvvigionamento, il provisioning e l'integrazione di connessioni in fibra ottica aggiuntive possono richiedere settimane o addirittura mesi.
- **Velocità dei dischi.** Se i dati potessero essere spostarsi più velocemente e non esistesse alcun limite di larghezza di banda tra i dati binari di origine e la destinazione, la fisica rappresenterebbe ancora un limite. I dati possono essere replicati solo con la stessa velocità con cui possono essere letti dai dischi di origine. La lettura di ogni 1 o 0 da ogni disco di un data center richiede tempo.
- **Velocità dei calcoli umani.** I dischi e la luce si muovono più velocemente dei processi decisionali umani. Quando viene richiesto a un gruppo di persone di collaborare e prendere decisioni congiunte, i risultati sono ancora più lenti. La replica non può mai superare i ritardi correlati all'intelligenza umana.

Ognuna di queste leggi della fisica comporta i rischi seguenti che in genere influiscono sui piani di migrazione:

- **Tempi di replica.** Gli strumenti di replica avanzati non possono prevalere sulla fisica di base: la replica richiede tempo e larghezza di banda. I piani devono includere sequenze temporali realistiche che riflettano la quantità di tempo necessaria per replicare i dati binari. La *larghezza di banda totale disponibile per la migrazione* è la quantità di larghezza di banda in uscita, misurata in megabit al secondo (Mbps) o gigabit al secondo (Gbps), che non viene usata per altre esigenze aziendali con priorità più elevata. Lo *spazio di archiviazione totale per la migrazione* è lo spazio totale su disco, espresso in gigabyte o terabyte, necessario per archiviare uno snapshot di tutti gli asset di cui eseguire la migrazione. Una stima iniziale del tempo può essere calcolata dividendo lo *spazio di archiviazione totale per la migrazione* per la *larghezza di banda totale disponibile per la migrazione*. Si noti la conversione da bit a byte. Per un calcolo più preciso del tempo, vedere il punto successivo "Effetto cumulativo della deviazione dei dischi".
- **Effetto cumulativo della deviazione dei dischi.** Dal punto di replica alla promozione di un asset alla produzione, i dati binari di origine e di destinazione devono rimanere sincronizzati. La *deviazione* nei dati binari usa larghezza di banda aggiuntiva perché tutte le modifiche apportate ai dati binari devono essere replicate su base periodica. Durante la sincronizzazione, tutte le deviazioni dei dati binari devono essere incluse nel calcolo per lo spazio di archiviazione totale per la migrazione. Maggiore è il tempo necessario per la promozione di un asset alla produzione, maggiore sarà la deviazione cumulativa. Maggiore è il numero di asset sincronizzati, maggiore sarà la larghezza di banda usata. Con ogni asset mantenuto in uno stato di sincronizzazione, viene persa ancora altra larghezza di banda disponibile totale per la migrazione.
- **Modifica del time-to-business.** Come indicato nel punto precedente, "Effetto cumulativo della deviazione dei dischi", il tempo di sincronizzazione ha un effetto negativo cumulativo sulla velocità di migrazione. La definizione delle priorità del backlog della migrazione e la preparazione avanzata del [piano per le modifiche aziendali](../optimize/business-change-plan.md) sono fondamentali per la velocità della migrazione. Il test più significativo dell'allineamento aziendale e tecnico durante un'operazione di migrazione è la velocità della promozione. Più velocemente un asset può essere promosso alla produzione, minore sarà l'impatto della deviazione dei dischi sulla larghezza di banda e maggiori saranno la larghezza di banda e il tempo che possono essere allocati alla replica del carico di lavoro successivo.

## <a name="next-steps"></a>Passaggi successivi

Al termine della replica, è possibile iniziare le [attività di gestione temporanea](./stage.md).

> [!div class="nextstepaction"]
> [Attività di gestione temporanea durante una migrazione](./stage.md)
