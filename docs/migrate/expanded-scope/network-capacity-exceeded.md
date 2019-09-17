---
title: Capacità di rete superata
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: I requisiti di archiviazione superano la capacità della rete durante un'attività di migrazione.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 9b1078cbb6b7ca40b7a38ea56ae803fd61e67449
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71024763"
---
# <a name="storage-requirements-exceed-network-capacity-during-a-migration-effort"></a>I requisiti di archiviazione superano la capacità della rete durante una migrazione

In una migrazione nel cloud gli asset vengono replicati e sincronizzati attraverso la rete tra il data center esistente e il cloud. Non è insolito che i requisiti di dimensione dei dati esistenti di diversi carichi di lavoro superino la capacità di rete. In uno scenario di questo tipo il processo di migrazione può essere rallentato radicalmente oppure, in alcuni casi, interrotto completamente. Le indicazioni riportate di seguito consentono di espandere l'ambito della [Guida alla migrazione ad Azure](../azure-migration-guide/index.md) per fornire una soluzione che consenta di ovviare alle limitazioni della rete.

## <a name="general-scope-expansion"></a>Espansione dell'ambito generale

La maggior parte delle attività necessarie per questa espansione dell'ambito si verificherà durante i processi relativi ai prerequisiti, alla valutazione e alla migrazione vera e propria.

## <a name="suggested-prerequisites"></a>Prerequisiti suggeriti

**Convalida dei rischi relativi alla capacità della rete:** la [razionalizzazione del digital estate](../../digital-estate/rationalize.md) è un prerequisito altamente consigliato, soprattutto se esiste il rischio di sovraccarico della capacità di rete disponibile. Durante la razionalizzazione del digital estate, viene effettuato un [inventario delle risorse digitali](../../digital-estate/inventory.md). Tale inventario deve includere i requisiti di archiviazione esistenti nel digital estate. Come descritto in [Rischi della replica - Fisica della replica](../migration-considerations/migrate/replicate.md#replication-risks---physics-of-replication), questo inventario può essere usato per una stima delle **dimensioni totali dei dati di migrazione**, che possono essere confrontati con la **larghezza di banda disponibile totale per la migrazione**. Se il confronto non è allineato alla **modifica del time-to-business** necessaria, questo articolo consente di accelerare la velocità di migrazione riducendo il tempo necessario per la migrazione del data center.

**Trasferimento offline di archivi dati indipendenti:** nel diagramma seguente sono illustrati esempi di trasferimenti di dati online e offline con Azure Data Box. Questi approcci possono essere usati per inviare volumi elevati di dati nel cloud prima della migrazione del carico di lavoro. In un trasferimento dati offline i dati di origine vengono copiati in Azure Data Box, che viene quindi inviato fisicamente a Microsoft per il trasferimento in un account di archiviazione di Azure come file o BLOB. Questo processo può essere usato per inviare dati non direttamente collegati a un carico di lavoro specifico prima di altre attività di migrazione. In questo modo si riduce la quantità di dati che devono essere inviati in rete, nel tentativo di completare una migrazione rispettando i vincoli di rete.

Questo approccio può essere usato per trasferire tra l'altro backup, archivi, file server, applicazioni e HDFS dati. Le indicazioni tecniche esistenti spiegano come usare questo approccio per trasferire a Data Box i dati da un [archivio HDFS](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-migrate-on-premises-hdfs-cluster) o da dischi con [SMB](https://docs.microsoft.com/azure/databox/data-box-deploy-copy-data), [NFS](https://docs.microsoft.com/azure/databox/data-box-deploy-copy-data-via-nfs), [REST](https://docs.microsoft.com/azure/databox/data-box-deploy-copy-data-via-rest) o il [servizio di copia dei dati](https://docs.microsoft.com/azure/databox/data-box-deploy-copy-data-via-copy-service).

Esistono anche [soluzioni di partner di terze parti](https://azuremarketplace.microsoft.com/campaigns/databox/azure-data-box) che usano Azure Data Box per una migrazione "seed and feed", in cui un volume elevato di dati viene spostato tramite un trasferimento offline, ma in seguito viene sincronizzato in scala minore sulla rete.

![Trasferimento di dati offline e online con Azure Data Box](../../_images/migrate/databox.png)

## <a name="assess-process-changes"></a>Modifiche del processo di valutazione

Se i requisiti di archiviazione di uno o più carichi di lavoro superano la capacità della rete, è comunque possibile usare Azure Data Box in un trasferimento dati offline.

Secondo la posizione generale di Microsoft, la trasmissione sulla rete è l'approccio consigliato, a meno che la rete non sia disponibile. Questo suggerimento è dovuto alla velocità dei trasferimenti. Il trasferimento di dati attraverso la rete (anche in presenza di vincoli di larghezza di banda) è in genere più veloce rispetto all'invio fisico della stessa quantità di dati tramite un meccanismo di trasferimento offline, ad esempio Data Box.

Se è disponibile la connettività ad Azure, è necessario eseguire un'analisi prima di usare Data Box, soprattutto se la migrazione del carico di lavoro è urgente. È consigliabile usare Data Box solo quando il tempo per il trasferimento dei dati necessari supera il tempo richiesto per popolare, inviare e ripristinare i dati usando Data Box.

### <a name="suggested-action-during-the-assess-process"></a>Azione suggerita durante il processo di valutazione

**Analisi della capacità di rete:** quando i requisiti per il trasferimento dei dati relativi al carico di lavoro rischiano di superare la capacità della rete, il team di adozione del cloud aggiungerà al processo di valutazione un'ulteriore attività di analisi, denominata analisi della capacità di rete. Durante questa analisi, un membro del team con competenze in materia di rete locale e connettività di rete stimerà la capacità di rete disponibile e il tempo necessario per il trasferimento dei dati. La capacità disponibile verrà confrontata con i requisiti di archiviazione di tutti gli asset di cui deve essere eseguita la migrazione durante il rilascio corrente. Se i requisiti di archiviazione superano la larghezza di banda disponibile, gli asset che supportano il carico di lavoro verranno selezionati per il trasferimento offline.

> [!IMPORTANT]
> Al termine dell'analisi, potrebbe essere necessario aggiornare il piano di rilascio per riflettere il tempo necessario per l'invio, il ripristino e la sincronizzazione degli asset da trasferire offline.

**Analisi della deviazione:** ogni asset da trasferire offline deve essere analizzato per rilevare la deviazione dell'archiviazione e della configurazione. La deviazione dell'archiviazione è la quantità di modifiche nell'archiviazione sottostante nel tempo. La deviazione della configurazione è la modifica della configurazione dell'asset nel tempo. Dal momento in cui la risorsa di archiviazione viene copiata al momento in cui l'asset viene promosso alla produzione, è possibile che si verifichi una perdita di deviazione. Se tale deviazione deve essere riflessa nell'asset migrato, è necessaria una forma di sincronizzazione tra l'asset locale e l'asset migrato. Questa operazione deve essere contrassegnata per la valutazione durante l'esecuzione della migrazione.

## <a name="migrate-process-changes"></a>Modifiche del processo di migrazione

Quando si usano meccanismi di trasferimento offline, è improbabile che siano richiesti [processi di replica](../migration-considerations/migrate/replicate.md). Potrebbero essere necessaria tuttavia [processi di sincronizzazione](../migration-considerations/migrate/replicate.md). L'esame dei risultati dell'analisi della deviazione completata durante il processo di valutazione fornirà informazioni sulle attività richieste durante la migrazione, qualora un asset venga trasferito offline.

### <a name="suggested-action-during-the-migrate-process"></a>Azione suggerita durante il processo di migrazione

**Copia della risorsa di archiviazione:** questo approccio può essere usato per trasferire tra l'altro backup, archivi, file server, applicazioni e HDFS dati. Le indicazioni tecniche esistenti spiegano come usare questo approccio per trasferire a Data Box i dati da un [archivio HDFS](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-migrate-on-premises-hdfs-cluster) o da dischi con [SMB](https://docs.microsoft.com/azure/databox/data-box-deploy-copy-data), [NFS](https://docs.microsoft.com/azure/databox/data-box-deploy-copy-data-via-nfs), [REST](https://docs.microsoft.com/azure/databox/data-box-deploy-copy-data-via-rest) o il [servizio di copia dei dati](https://docs.microsoft.com/azure/databox/data-box-deploy-copy-data-via-copy-service).

Esistono anche [soluzioni di partner di terze parti](https://azuremarketplace.microsoft.com/campaigns/databox/azure-data-box) che usano Azure Data Box per una migrazione "seed and sync", in cui un volume elevato di dati viene spostato tramite un trasferimento offline, ma in seguito viene sincronizzato in scala minore sulla rete.

**Spedizione del dispositivo:** dopo la copia dei dati, il dispositivo può essere [spedito a Microsoft](https://docs.microsoft.com/azure/databox/data-box-deploy-picked-up). Dopo essere stati ricevuti e importati, i dati sono disponibili in un account di archiviazione di Azure.

**Ripristino dell'asset:** [verificare che i dati](https://docs.microsoft.com/azure/databox/data-box-deploy-picked-up#verify-data-upload-to-azure) siano disponibili nell'account di archiviazione. Dopo essere stati verificati, i dati possono essere usati come BLOB o in File di Azure. Se i dati sono file VHD/VHDX, possono essere dischi gestiti convertiti. Questi dischi gestiti possono quindi essere usati per creare un'istanza di una macchina virtuale, che crea una replica dell'asset locale originale.

**Sincronizzazione:** se la sincronizzazione della deviazione è un requisito per un asset migrato, è possibile usare una delle [soluzioni di partner di terze parti](https://azuremarketplace.microsoft.com/campaigns/databox/azure-data-box) per sincronizzare i file fino a quando l'asset non viene ripristinato.

## <a name="optimize-and-promote-process-changes"></a>Modifiche dei processi di ottimizzazione e promozione

È improbabile che le attività di ottimizzazione siano interessate da questa modifica dell'ambito.

## <a name="secure-and-manage-process-changes"></a>Modifiche dei processi di protezione e gestione

È improbabile che le attività di protezione e gestione siano interessate da questa modifica dell'ambito.

## <a name="next-steps"></a>Passaggi successivi

Tornare all'[elenco di controllo per l'espansione dell'ambito](./index.md) per verificare che il metodo di migrazione sia completamente allineato.

> [!div class="nextstepaction"]
> [Elenco di controllo per l'espansione dell'ambito](./index.md)
