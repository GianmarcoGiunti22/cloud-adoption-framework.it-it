---
title: Più data center
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Più data center
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: b2491d349628d2c9640097ddd2c94b79505a0921
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71024797"
---
# <a name="multiple-datacenters"></a>Più data center

Spesso l'ambito di una migrazione implica la transizione di più data center. Le indicazioni seguenti consentono di espandere l'ambito della [Guida alla migrazione di Azure](../azure-migration-guide/index.md) in modo da prendere in considerazione più data center.

## <a name="general-scope-expansion"></a>Espansione dell'ambito generale

La maggior parte delle attività necessarie per questa espansione dell'ambito si verificherà durante i processi relativi ai prerequisiti, alla valutazione e all'ottimizzazione di una migrazione.

## <a name="suggested-prerequisites"></a>Prerequisiti suggeriti

Prima di iniziare la migrazione, è consigliabile creare nell'ambito dello strumento di gestione dei progetti epiche che rappresentino ogni data center di cui eseguire la migrazione. È quindi importante comprendere i risultati e le motivazioni aziendali che giustificano questa migrazione. Queste motivazioni possono essere usate per classificare in ordine di priorità l'elenco di epiche (o data center). Se ad esempio la migrazione è determinata dal desiderio di abbandonare i data center prima del rinnovo dei lease, a ogni epica deve assegnata una priorità in base alla data di rinnovo del lease.

All'interno di ogni epica i carichi di lavoro di cui eseguire la valutazione e la migrazione devono essere gestiti come funzionalità. Ogni asset all'interno di tale carico di lavoro verrà gestito come una storia utente. Il lavoro necessario per la valutazione, la migrazione, l'ottimizzazione, la promozione, la protezione e la gestione di ogni asset verrà rappresentato come attività per ogni asset.

Gli sprint o le iterazioni saranno quindi costituiti da una serie di attività necessarie per eseguire la migrazione degli asset e delle storie utente di cui è stato eseguito il commit dal team di adozione del cloud. Le versioni saranno quindi costituite da uno o più carichi di lavoro o funzionalità da promuovere alla produzione.

## <a name="assess-process-changes"></a>Modifiche del processo di valutazione

La modifica più importante del processo di valutazione quando si espande l'ambito per prendere in considerazione più data center è correlata a operazioni accurate di registrazione e definizione delle priorità dei carichi di lavoro e delle dipendenze nei data center.

### <a name="suggested-action-during-the-assess-process"></a>Azione suggerita durante il processo di valutazione

**Valutare le dipendenze tra data center:** gli [strumenti di visualizzazione delle dipendenze in Azure Migrate](https://docs.microsoft.com/azure/migrate/concepts-dependency-visualization) consentono di individuare le dipendenze. L'uso di questo set di strumenti prima della migrazione è un'ottima procedura consigliata generale. Questo set di strumenti diventa tuttavia un passaggio necessario del processo di valutazione quando si gestiscono complessità globali. Tramite il [raggruppamento delle dipendenze](https://docs.microsoft.com/azure/migrate/how-to-create-group-machine-dependencies), la visualizzazione consente di identificare gli indirizzi IP e le porte di tutti gli asset necessari per supportare il carico di lavoro.

> [!IMPORTANT]
> Due note importanti: in primo luogo, è necessario un esperto con una conoscenza degli schemi di posizionamento degli asset e degli indirizzi IP per identificare gli asset che si trovano in un data center secondario. In secondo luogo, è importante valutare i client e le dipendenze downstream per comprendere le dipendenze bidirezionali.

## <a name="migrate-process-changes"></a>Modifiche del processo di migrazione

La migrazione di più data center è simile al consolidamento dei data center. Dopo la migrazione, il cloud diventa la soluzione unica di data center per più asset. L'espansione dell'ambito più probabile durante il processo di migrazione è la convalida e l'allineamento degli indirizzi IP.

### <a name="suggested-action-during-the-migrate-process"></a>Azione suggerita durante il processo di migrazione

Di seguito sono riportate le attività che influiscono in modo significativo sul successo di una migrazione nel cloud:

- **Valutare i conflitti di rete:** quando si consolidano i data center in un singolo provider di servizi cloud, è probabile che si creino conflitti di rete, di DNS o di altro tipo. Durante la migrazione, è importante verificare la presenza di conflitti per evitare interruzioni nei sistemi di produzione ospitati nel cloud.
- **Aggiornare le tabelle di routing:** spesso è necessario apportare modifiche alle tabelle di routing durante il consolidamento delle reti o dei data center.

## <a name="optimize-and-promote-process-changes"></a>Modifiche dei processi di ottimizzazione e promozione

Durante l'ottimizzazione, potrebbe essere necessario eseguire test aggiuntivi.

### <a name="suggested-action-during-the-optimize-and-promote-process"></a>Azione suggerita durante il processo di ottimizzazione e promozione

Prima della promozione, è importante fornire livelli di test aggiuntivi durante l'espansione dell'ambito. Durante i test, è importante verificare la presenza di conflitti di routing o di altri conflitti di rete. Inoltre, è importante isolare l'applicazione distribuita e rieseguire i test per verificare che tutte le dipendenze siano state migrate nel cloud. In questo caso, l'isolamento significa separare l'ambiente distribuito dalle reti di produzione. In questo modo è possibile rilevare asset trascurati che sono ancora in esecuzione in locale.

## <a name="secure-and-manage-process-changes"></a>Modifiche dei processi di protezione e gestione

I processi di protezione e gestione non devono essere modificati dall'espansione dell'ambito.

## <a name="next-steps"></a>Passaggi successivi

Tornare all'[elenco di controllo per l'espansione dell'ambito](./index.md) per verificare che il metodo di migrazione sia completamente allineato.

> [!div class="nextstepaction"]
> [Elenco di controllo per l'espansione dell'ambito](./index.md)
