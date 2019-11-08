---
title: Valutare l'idoneità dei carichi di lavoro
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Processo nell'ambito della migrazione al cloud che è incentrato sulle attività di migrazione dei carichi di lavoro nel cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 05b713c2f1f88f50829e38db8a0a0343d3afd32d
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73753505"
---
# <a name="evaluate-workload-readiness"></a>Valutare l'idoneità dei carichi di lavoro

Questa attività è incentrata sulla valutazione dell'idoneità di un carico di lavoro per la migrazione nel cloud. Durante questa attività, il team di adozione del cloud verifica che tutti gli asset e le dipendenze associate siano compatibili con il modello di distribuzione e il provider di servizi cloud scelti. Durante il processo, il team documenta tutto il lavoro richiesto per [correggere](../migrate/remediate.md) i problemi di compatibilità.

## <a name="evaluation-assumptions"></a>Presupposti di valutazione

La maggior parte del contenuto che discute i principi nel Framework di adozione del cloud è indipendente dal cloud. Il processo di valutazione dell'idoneità tuttavia deve essere in gran parte specifico per ogni piattaforma cloud. Le indicazioni seguenti presuppongono l'intenzione di eseguire la migrazione in Azure, nonché l'uso di Azure Migrate (noto anche come Azure Site Recovery) per [le attività di replica](../migrate/replicate.md). Per strumenti alternativi, vedere le [opzioni di replica](../migrate/replicate-options.md).

Questo articolo non ha l'obiettivo di illustrare tutte le attività di valutazione possibili. Si presuppone che per ogni ambiente e risultato di business siano definiti requisiti specifici. Per accelerare la creazione di tali requisiti, la parte restante di questo articolo condivide alcune attività comuni di valutazione dell'[infrastruttura](#common-infrastructure-evaluation-activities), dei [database](#common-database-evaluation-activities) e della [rete ](#common-network-evaluation-activities).

## <a name="common-infrastructure-evaluation-activities"></a>Attività comuni di valutazione dell'infrastruttura

- Requisiti VMware: [esaminare i requisiti di Azure Site Recovery per VMware](https://docs.microsoft.com/azure/site-recovery/vmware-physical-azure-support-matrix).
- Requisiti di Hyper-V: [esaminare i requisiti di Azure Site Recovery per Hyper-v](https://docs.microsoft.com/azure/site-recovery/hyper-v-azure-support-matrix).

Assicurarsi di documentare eventuali discrepanze nella configurazione host, nella configurazione delle macchine virtuali replicate, nei requisiti di archiviazione o nella configurazione di rete.

## <a name="common-database-evaluation-activities"></a>Attività comuni di valutazione dei database

- Documentare gli obiettivi del punto di ripristino e gli obiettivi del tempo di ripristino della distribuzione dei database corrente. Questi dati vengono usati nelle [attività di architettura](./architect.md) per semplificare il processo decisionale.
- Documentare i requisiti per la configurazione della disponibilità elevata. Per informazioni sui requisiti di SQL Server, vedere la [Guida alle soluzioni di disponibilità elevata di SQL Server](https://docs.microsoft.com/sql/sql-server/failover-clusters/high-availability-solutions-sql-server).
- Valutare la compatibilità PaaS. La [Guida alla migrazione dei dati di Azure](https://datamigration.microsoft.com) esegue il mapping dei database locali a soluzioni di Azure PaaS compatibili, ad esempio [Cosmos DB](https://docs.microsoft.com/azure/cosmos-db) o [DB di Azure](https://docs.microsoft.com/azure/sql-database) per [MySQL](https://docs.microsoft.com/azure/mysql), [PostgreSQL](https://docs.microsoft.com/azure/postgresql)o [MariaDB](https://docs.microsoft.com/azure/mariadb).
- Quando la compatibilità PaaS è un'opzione e non è richiesta alcuna correzione, consultare il team responsabile delle [attività di architettura](./architect.md). Le migrazioni PaaS possono garantire un risparmio di tempo notevole e riduzioni significative del costo totale di proprietà (TCO) della maggior parte delle soluzioni cloud.
- Quando la compatibilità PaaS è un'opzione ma è richiesta la correzione, consultare i team responsabili delle [attività di architettura](./architect.md) e delle [attività di correzione](../migrate/remediate.md). In molti scenari i vantaggi delle migrazioni PaaS per le soluzioni di database possono essere superiori allo svantaggio di un aumento del tempo di correzione.
- Documentare le dimensioni e la frequenza di modifica per ogni database di cui eseguire la migrazione.
- Quando possibile, documentare le applicazioni o altri asset che effettuano chiamate a ogni database.

> [!NOTE]
> Per la sincronizzazione di un asset viene usata la larghezza di banda durante i processi di replica. Un tranello molto comune consiste nel trascurare l'uso della larghezza di banda per la sincronizzazione degli asset tra il punto di replica e il rilascio. I database usano in genere la larghezza di banda durante i cicli di rilascio e i database con footprint di archiviazione di grandi dimensioni o una frequenza di modifica elevata richiedono particolare attenzione. Si consideri un approccio che prevede la replica della struttura dei dati, con aggiornamenti controllati prima del test di accettazione utente e del rilascio. In scenari di questo tipo le alternative ad Azure Site Recovery possono essere più appropriate. Per informazioni dettagliate, vedere la [Guida alla migrazione dei dati di Azure](https://datamigration.microsoft.com).

## <a name="common-network-evaluation-activities"></a>Attività comuni di valutazione della rete

- Calcolare lo spazio di archiviazione totale per tutte le macchine virtuali da replicare durante le iterazioni che portano a un rilascio.
- Calcolare la frequenza di deviazione o di modifica dello spazio di archiviazione per tutte le macchine virtuali da replicare durante le iterazioni che portano a un rilascio.
- Calcolare i requisiti di larghezza di banda necessari per ogni iterazione sommando l'archiviazione e la deviazione totali.
- Calcolare la larghezza di banda inutilizzata disponibile nella rete corrente per convalidare l'allineamento dell'iterazione.
- Documentare la larghezza di banda necessaria per raggiungere la velocità di migrazione prevista. Se è necessaria una correzione per fornire la larghezza di banda necessaria, inviare una notifica al team responsabile delle [attività di correzione](../migrate/remediate.md).

> [!NOTE]
> L'archiviazione totale influisce direttamente sui requisiti di larghezza di banda durante la replica iniziale. Tuttavia la deviazione di archiviazione continua dal punto di replica fino al rilascio. Questo significa che la deviazione ha un effetto cumulativo sulla larghezza di banda disponibile.

## <a name="next-steps"></a>Passaggi successivi

Al termine della valutazione di un sistema, gli output forniscono la base per lo sviluppo di una nuova [architettura cloud](./architect.md).

> [!div class="nextstepaction"]
> [Progettare i carichi di lavoro prima della migrazione](./architect.md)
