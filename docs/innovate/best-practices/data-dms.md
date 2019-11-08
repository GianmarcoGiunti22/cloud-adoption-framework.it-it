---
title: 'Innovazione nel cloud: servizio migrazione del database di Azure'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Innovazione nel cloud-servizio migrazione del database di Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: 46e21c08bac9501dd9b99fceb4ef3040cc9f0a83
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73752039"
---
# <a name="collect-data-through-the-migration-and-modernization-of-existing-data-sources"></a>Raccogliere dati attraverso la migrazione e la modernizzazione di origini dati esistenti

Le aziende hanno spesso tipi diversi di dati esistenti che possono [democratizzare](../considerations/data.md). Quando un'ipotesi del cliente richiede l'uso di dati esistenti per creare soluzioni moderne, un primo passaggio potrebbe essere la migrazione e la modernizzazione dei dati da preparare per le innovazioni e le innovazioni. Per allinearsi alle attività di migrazione esistenti all'interno di un piano di adozione del cloud, è possibile eseguire più facilmente la migrazione e la modernizzazione all'interno della [metodologia di migrazione](../../migrate/index.md).

## <a name="use-of-this-article"></a>Uso di questo articolo

Questo articolo illustra una serie di approcci che si allineano con il processo di migrazione. È possibile allineare meglio questi approcci alla procedura di migrazione standard.

Durante il processo di valutazione all'interno della metodologia di migrazione, un team di adozione del cloud valuta lo stato corrente e lo stato futuro desiderato per l'asset migrato. Quando tale processo fa parte di un'attività di innovazione, entrambi i team di adozione del cloud possono usare questo articolo per contribuire a eseguire tali valutazioni.

## <a name="primary-toolset"></a>Set di strumenti primario

Quando si esegue la migrazione e la modernizzazione dei dati locali, la scelta più comune di strumenti di Azure è il [servizio migrazione del database di Azure](https://docs.microsoft.com/azure/dms). Questo servizio fa parte della più ampia [Azure migrate](https://docs.microsoft.com/azure/migrate/migrate-services-overview) . Per le origini dati esistenti SQL Server, [Data Migration Assistant](https://docs.microsoft.com/sql/dma/dma-overview) possibile valutare ed eseguire la migrazione di un numero ridotto di strutture di dati.

Per supportare le migrazioni Oracle e NoSQL, è anche possibile usare il [servizio migrazione del database](https://docs.microsoft.com/azure/dms) per determinati tipi di database da origine a destinazione. Gli esempi includono Oracle per PostgreSQL e MongoDB per Cosmos DB. Più comunemente, i team di adozione usano gli strumenti per i partner o gli script personalizzati per eseguire la migrazione alle opzioni Azure Cosmos DB, Azure HDInsight o Virtual Machine basate sull'infrastruttura distribuita come servizio (IaaS).

## <a name="considerations-and-guidance"></a>Considerazioni e indicazioni

Quando si usa il servizio migrazione del database di Azure per la migrazione e la modernizzazione dei dati, è importante comprendere quanto segue:

- Piattaforma corrente per ospitare l'origine dati.
- Versione corrente.
- La piattaforma e la versione future che meglio supportano l'ipotesi o la destinazione del cliente.

La tabella seguente illustra le coppie di origine e di destinazione da esaminare con il team di migrazione. Ogni coppia include una scelta di strumenti e un collegamento a una guida correlata.

### <a name="migration-type"></a>Tipo di migrazione

Con una migrazione offline, i tempi di inattività dell'applicazione partono dall'inizio della migrazione. Con una migrazione online, il tempo di inattività è limitato al tempo di trasferimento al termine della migrazione.

Si consiglia di decidere il tempo di inattività aziendale accettabile e testare una migrazione offline. Questa operazione viene eseguita per verificare se il tempo di ripristino soddisfa i tempi di inattività accettabili. Se il tempo di ripristino non è accettabile, eseguire una migrazione in linea.

|Source (Sorgente)  |Obiettivo  |Strumento  |Tipo di migrazione  |Guida  |
|---------|---------|---------|---------|---------|
|SQL Server|database SQL di Azure|Database Migration Service|Offline|[Esercitazione](https://docs.microsoft.com/azure/dms/tutorial-sql-server-to-azure-sql)|
|SQL Server|database SQL di Azure|Database Migration Service|Online|[Esercitazione](https://docs.microsoft.com/azure/dms/tutorial-sql-server-azure-sql-online)|
|SQL Server|Istanza gestita di Database SQL di Azure|Database Migration Service|Offline|[Esercitazione](https://docs.microsoft.com/azure/dms/tutorial-sql-server-to-managed-instance)|
|SQL Server|Istanza gestita di Database SQL di Azure|Database Migration Service|Online|[Esercitazione](https://docs.microsoft.com/azure/dms/tutorial-sql-server-managed-instance-online)|
|SQL Server RDS|Database SQL di Azure o istanza gestita di database SQL di Azure|Database Migration Service|Online|[Esercitazione](https://docs.microsoft.com/azure/dms/tutorial-rds-sql-server-azure-sql-and-managed-instance-online)|
|MySQL|Database di Azure per MySQL|Database Migration Service|Online|[Esercitazione](https://docs.microsoft.com/azure/dms/tutorial-mysql-azure-mysql-online)|
|PostgreSQL|Database di Azure per PostgreSQL|Database Migration Service|Online|[Esercitazione](https://docs.microsoft.com/azure/dms/tutorial-postgresql-azure-postgresql-online)|
|MongoDB|Azure Cosmos DB l'API Mongo|Database Migration Service|Offline|[Esercitazione](https://docs.microsoft.com/azure/dms/tutorial-mongodb-cosmos-db)|
|MongoDB|Azure Cosmos DB l'API Mongo|Database Migration Service|Online|[Esercitazione](https://docs.microsoft.com/azure/dms/tutorial-mongodb-cosmos-db-online)|
|Oracle|Diverse opzioni di piattaforma distribuita come servizio (PaaS) e IaaS|Uno strumento o Azure Migrate del partner|Offline o online|[Albero delle decisioni](../../migrate/expanded-scope/data-oracle-migration.md)|
|Opzioni di database NoSQL diverse|Opzioni di Cosmo DB o IaaS|Migrazioni procedurali o Azure Migrate|Offline o online|[Albero delle decisioni](../../migrate/expanded-scope/data-no-sql-migration.md)|
