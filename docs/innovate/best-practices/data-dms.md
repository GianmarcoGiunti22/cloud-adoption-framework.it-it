---
title: 'Innovazione nel cloud: servizio di migrazione dei dati'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Innovazione Cloud-Servizio migrazione dati
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/24/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: 7b6d9d2bb08bd4e3e34fe1cc67f4c6a006a75bb5
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72557401"
---
# <a name="collect-data-through-the-migration-and-modernization-of-existing-data-sources"></a>Raccogliere dati attraverso la migrazione e la modernizzazione di origini dati esistenti

Le aziende spesso hanno un'ampia gamma di dati esistenti che possono essere [democratizzati](../considerations/data.md). Quando l'ipotesi del cliente richiede l'uso di dati esistenti per creare soluzioni moderne, un primo passaggio potrebbe essere la migrazione e la modernizzazione dei dati da preparare per le invenzioni e le innovazioni. Per allinearsi alle attività di migrazione esistenti all'interno di un piano di adozione del cloud, la migrazione e la modernizzazione possono essere eseguite più facilmente all'interno della [metodologia di migrazione](../../migrate/index.md).

## <a name="use-of-this-article"></a>Uso di questo articolo

Questo articolo illustra una serie di approcci che si allineano con il processo di migrazione, ma potrebbe essere più allineata alla catena di migrazione standard. Durante il processo di valutazione all'interno della metodologia di migrazione, il team di adozione del cloud valuterebbe lo stato corrente e desiderasse eseguire la migrazione dello stato futuro per l'asset. Quando tale processo fa parte di un'attività di innovazione, entrambi i team di adozione del cloud possono usare questo articolo per prendere queste decisioni.

## <a name="primary-toolset"></a>Set di strumenti primario

Quando si esegue la migrazione e la modernizzazione dei dati risiedono in locale, la scelta più comune di strumenti di Azure è il [servizio di migrazione dei dati (DMS)](https://docs.microsoft.com/azure/dms) , che fa parte del più ampio [Azure migrate](https://docs.microsoft.com/azure/migrate/migrate-services-overview) . Per le origini dati SQL Server esistenti, il [Data Migration Assistant (DMA)](/sql/dma/dma-overview) può fornire anche assistenza per la valutazione e la migrazione di un numero inferiore di strutture di dati.

Per supportare le migrazioni Oracle e NoSQL, il [servizio di migrazione dei dati (DMS)](https://docs.microsoft.com/azure/dms) può essere usato anche per determinati tipi di origine nei database di destinazione, ad esempio da Oracle a PostgreSQL o MongoDB, per Cosmos DB. È più comune per i team di adozione sfruttare gli strumenti di terze parti o gli script di migrazione personalizzati per eseguire la migrazione alle opzioni di VM basate su Cosmos DB, HDInsight o IaaS.

## <a name="considerations-and-guidance"></a>Considerazioni e indicazioni

Quando si usa DMS per la migrazione e la modernizzazione dei dati, è importante comprendere la piattaforma corrente per ospitare i dati (origine), la versione e la piattaforma e la versione futura che meglio supportano l'ipotesi del cliente (destinazione). Di seguito è riportato un elenco di coppie di origine e di destinazione da esaminare con il team di migrazione. Ognuna include una scelta di strumenti e un collegamento a una guida basata su tali considerazioni.

**Tipo di migrazione:** Con una migrazione offline, il tempo di inattività dell'applicazione viene avviato all'avvio della migrazione. Con una migrazione online, il tempo di inattività è limitato al tempo di trasferimento al termine della migrazione. Si consiglia di comprendere il tempo di inattività aziendale accettabile e testare una migrazione offline per determinare se il tempo di ripristino soddisfa questo aspetto. in caso contrario, eseguire una migrazione in linea.

|Source (Sorgente)  |Obiettivo  |Strumento  |Tipo di migrazione  |Guida  |
|---------|---------|---------|---------|---------|
|SQL Server|database SQL di Azure|Servizio Migrazione del database|Offline|[Esercitazione](https://docs.microsoft.com/azure/dms/tutorial-sql-server-to-azure-sql)|
|SQL Server|database SQL di Azure|Servizio Migrazione del database|Online|[Esercitazione](https://docs.microsoft.com/azure/dms/tutorial-sql-server-azure-sql-online)|
|SQL Server|Istanza gestita di database SQL di Azure|Servizio Migrazione del database|Offline|[Esercitazione](https://docs.microsoft.com/azure/dms/tutorial-sql-server-to-managed-instance)|
|SQL Server|Istanza gestita di database SQL di Azure|Servizio Migrazione del database|Online|[Esercitazione](https://docs.microsoft.com/azure/dms/tutorial-sql-server-managed-instance-online)|
|SQL Server RDS|Database SQL di Azure (o Istanza gestita)|Servizio Migrazione del database|Online|[Esercitazione](https://docs.microsoft.com/azure/dms/tutorial-rds-sql-server-azure-sql-and-managed-instance-online)|
|MySQL|Database di Azure per MySQL|Servizio Migrazione del database|Online|[Esercitazione](https://docs.microsoft.com/azure/dms/tutorial-mysql-azure-mysql-online)|
|PostgreSQL|Database di Azure per PostgreSQL|Servizio Migrazione del database|Online|[Esercitazione](https://docs.microsoft.com/azure/dms/tutorial-postgresql-azure-postgresql-online)|
|MongoDB|Azure Cosmos DB l'API Mongo|Servizio Migrazione del database|Offline|[Esercitazione](https://docs.microsoft.com/azure/dms/tutorial-mongodb-cosmos-db)|
|MongoDB|Azure Cosmos DB l'API Mongo|Servizio Migrazione del database|Online|[Esercitazione](https://docs.microsoft.com/azure/dms/tutorial-mongodb-cosmos-db-online)|
|Oracle|Intervallo di opzioni di PaaS & IaaS|Terze parti o Azure Migrate|Vari|[Albero delle decisioni](../considerations/data-oracle-migration.md)|
|Diversi database NoSQL|Opzioni di Cosmo DB o IaaS|Migrazioni procedurali o Azure Migrate|Vari|[Albero delle decisioni](../considerations/data-no-sql-migration.md)|
