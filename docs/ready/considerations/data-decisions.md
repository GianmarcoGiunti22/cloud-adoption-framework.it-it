---
title: Decisioni relative alla progettazione del database per l'idoneità ad Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Decisioni relative alla progettazione del database per l'idoneità ad Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/15/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: e95817396fb898c3460874e0e63bf793628a4d16
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71022059"
---
# <a name="data-design-decisions"></a>Decisioni relative alla progettazione dei dati

Quando si prepara l'ambiente della zona di destinazione per l'adozione del cloud, è necessario determinare i requisiti dei dati per ospitare i carichi di lavoro. I prodotti e i servizi di database di Azure supportano un'ampia gamma di scenari e funzionalità di archiviazione dei dati. Il modo in cui si configura l'ambiente della zona di destinazione per supportare i requisiti dei dati dipende dai requisiti di governance, tecnici e aziendali dei carichi di lavoro.

## <a name="identify-data-services-requirements"></a>Identificare i requisiti dei servizi dati

Nell'ambito della valutazione e della preparazione della zona di destinazione è necessario identificare gli archivi dati che dovranno essere supportati. Il processo comporta la valutazione delle applicazioni e dei servizi che costituiscono i carichi di lavoro allo scopo di determinare i requisiti di accesso e archiviazione dei dati. Dopo aver identificato e documentato questi requisiti, è possibile creare criteri per la zona di destinazione in modo da controllare i tipi di risorse consentiti in base alle esigenze del carico di lavoro.

Per ogni applicazione o servizio che verrà distribuito nell'ambiente della zona di destinazione, usare l'albero delle decisioni seguente come punto di partenza per determinare i servizi di archiviazione dei dati appropriati da usare:

![Albero delle decisioni per i servizi di database di Azure](../../_images/ready/data-decision-tree.png)

### <a name="key-questions"></a>Domande principali

Rispondere alle domande seguenti sui carichi di lavoro per prendere decisioni in base all'albero delle decisioni per i servizi di database di Azure:

- **È necessario il controllo completo o la proprietà del software di database o del sistema operativo host?** Alcuni scenari richiedono un elevato livello di controllo o proprietà della configurazione software e dei server host per i carichi di lavoro di database. In questi scenari è possibile distribuire macchine virtuali IaaS (Infrastructure as a Service) personalizzate per il controllo completo della distribuzione e della configurazione dei servizi dati. Se il proprio ambiente non soddisfa questi requisiti, i servizi di database gestiti da servizi PaaS (Platform as a Service) possono ridurre i costi operativi e di gestione.
- **I carichi di lavoro useranno una tecnologia di database relazionale?** In tal caso, quale tecnologia si prevede di usare? Azure offre funzionalità di database PaaS gestite per [database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview), [MySQL](https://docs.microsoft.com/azure/mysql/overview), [PostgreSQL](https://docs.microsoft.com/azure/postgresql/overview) e [MariaDB](https://docs.microsoft.com/azure/mariadb/overview).
- **I carichi di lavoro useranno SQL Server?** In Azure i carichi di lavoro possono essere eseguiti nel servizio [SQL Server in Macchine virtuali di Azure](https://azure.microsoft.com/services/virtual-machines/sql-server/) basato su IaaS o nel [servizio ospitato dal database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) basato su PaaS. La scelta dell'opzione da usare dipende principalmente dalle esigenze di gestione dei carichi di lavoro, a seconda che si voglia gestire il database, applicare patch ed eseguire backup oppure che si vogliano delegare queste operazioni ad Azure. In alcuni scenari, i problemi di compatibilità possono richiedere l'uso di SQL Server ospitato in IaaS. Per altre informazioni su come scegliere l'opzione corretta per i carichi di lavoro, vedere [Scegliere l'opzione SQL Server più adatta in Azure](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas).
- **I carichi di lavoro useranno l'archiviazione di database di tipo chiave/valore?** [Cache di Azure per Redis](https://docs.microsoft.com/azure/azure-cache-for-redis/cache-overview) offre una soluzione di archiviazione dei dati di tipo chiave/valore memorizzata nella cache a prestazioni elevate che può supportare applicazioni veloci e scalabili. Anche [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) fornisce funzionalità di archiviazione di tipo chiave/valore per utilizzo generico.
- **I carichi di lavoro useranno i dati di documenti o grafici?** [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) è un servizio di database multimodello che supporta un'ampia gamma di API e tipi di dati. Azure Cosmos DB offre anche funzionalità di database per documenti e grafici.
- **I carichi di lavoro useranno dati organizzati in famiglie di colonne?** [Apache HBase in Azure HDInsight](https://docs.microsoft.com/azure/hdinsight/hbase/apache-hbase-overview) è basato su Apache Hadoop. Supporta grandi quantità di dati non strutturati e semistrutturati in un database senza schema organizzato in famiglie di colonne.
- **I carichi di lavoro richiederanno funzionalità di analisi dei dati ad alta capacità?** È possibile usare [Azure SQL Data Warehouse](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-overview-what-is) per archiviare ed eseguire query su dati strutturati disponibili in quantità dell'ordine di petabyte. Per i carichi di lavoro basati su Big Data non strutturati, è possibile usare [Azure Data Lake](https://azure.microsoft.com/solutions/data-lake/) per archiviare e analizzare file di dimensioni dell'ordine di petabyte e trilioni di oggetti.
- **I carichi di lavoro richiederanno funzionalità di motore di ricerca?** È possibile usare [Ricerca di Azure](https://docs.microsoft.com/azure/search/search-what-is-azure-search) per creare indici di ricerca basati sul cloud ottimizzati per l'intelligenza artificiale che possono essere integrati nelle applicazioni.
- **I carichi di lavoro useranno dati relativi a serie temporali?** [Azure Time Series Insights](https://docs.microsoft.com/azure/time-series-insights/time-series-insights-overview) è una soluzione per archiviare, visualizzare ed eseguire query su grandi quantità di dati relativi a serie temporali, ad esempio i dati generati dai dispositivi IoT.

> [!NOTE]
> Sono disponibili altre informazioni su come valutare le opzioni di database per ogni applicazione o servizio nella [Guida all'architettura delle applicazioni Azure](https://docs.microsoft.com/azure/architecture/guide/technology-choices/data-store-comparison).

## <a name="common-database-scenarios"></a>Scenari di database comuni

La tabella seguente illustra i requisiti di alcuni scenari di uso comune e i servizi di database consigliati per gestirli:

| **Scenario** | **Servizio dati** |
|-----|-----|
| È necessario un database multimodello distribuito a livello globale con supporto nativo per le opzioni NoSQL. | [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) |
| È necessario un database relazionale completamente gestito che offre provisioning rapido, ridimensionamento veloce e intelligence e sicurezza incorporate. | [Database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) |
| È necessario un database relazionale MySQL completamente gestito e scalabile con disponibilità elevata e sicurezza integrate senza costi aggiuntivi. | [Database di Azure per MySQL](https://docs.microsoft.com/azure/mysql/overview) |
| È necessario un database relazionale PostgreSQL completamente gestito e scalabile con disponibilità elevata e sicurezza integrate senza costi aggiuntivi. | [Database di Azure per PostgreSQL](https://docs.microsoft.com/azure/postgresql/overview) |
| Si prevede di ospitare app SQL Server aziendali nel cloud e di avere il controllo completo sul sistema operativo del server. | [SQL Server in macchine virtuali](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-iaas-overview) |
| È necessario un data warehouse elastico e completamente gestito in grado di offrire sicurezza a qualsiasi livello di scalabilità e senza costi aggiuntivi. | [Azure SQL Data Warehouse](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-overview-what-is) |
| Sono necessarie risorse di archiviazione in Data Lake in grado di supportare cluster Hadoop o dati HDFS. | [Azure Data Lake](https://azure.microsoft.com/solutions/data-lake/) |
| È necessario l'accesso ai dati con bassa latenza costante e velocità effettiva elevata per supportare applicazioni scalabili e veloci. | [Cache Redis di Azure](https://docs.microsoft.com/azure/azure-cache-for-redis/cache-overview) |
| È necessario un database relazionale MariaDB completamente gestito e scalabile con disponibilità elevata e sicurezza integrate senza costi aggiuntivi. | [Database di Azure per MariaDB](https://docs.microsoft.com/azure/mariadb/overview) |

## <a name="regional-availability"></a>Disponibilità a livello di area

Azure consente di offrire servizi con la scalabilità necessaria per raggiungere clienti e partner,  _ovunque si trovino_. Un fattore chiave nella pianificazione della distribuzione cloud consiste nel determinare l'area di Azure che ospiterà le risorse dei carichi di lavoro.

La maggior parte dei servizi di database è in genere disponibile nella maggior parte delle aree di Azure. Esistono tuttavia alcune aree, destinate principalmente ai clienti governativi, che supportano solo un sottoinsieme di questi prodotti. Prima di decidere in quali aree distribuire le risorse di database, è consigliabile fare riferimento alla [pagina relativa alle aree](https://azure.microsoft.com/global-infrastructure/services/?regions=all&products=data-factory,sql-server-stretch-database,redis-cache,database-migration,sql-data-warehouse,postgresql,mariadb,cosmos-db,mysql,sql-database) per verificare lo stato più recente della disponibilità a livello di area.

Per altre informazioni sull'infrastruttura globale di Azure, vedere la [pagina Aree di Azure](https://azure.microsoft.com/global-infrastructure/regions). È anche possibile consultare la pagina  [Prodotti disponibili in base all'area](https://azure.microsoft.com/global-infrastructure/services/?regions=all&products=all) per trovare dettagli specifici sui servizi globali disponibili in ogni area di Azure.

## <a name="data-residency-and-compliance-requirements"></a>Requisiti di conformità e residenza dei dati

Ai carichi di lavoro sono spesso applicati requisiti legali e contrattuali correlati all'archiviazione dei dati. Questi requisiti possono variare in base alla sede dell'organizzazione, alla giurisdizione delle risorse fisiche che ospitano gli archivi dati e al settore aziendale applicabile. I componenti degli obblighi relativi ai dati da considerare includono la classificazione dei dati, la posizione dei dati e le rispettive responsabilità per la protezione dei dati nel modello di responsabilità condivisa. Per comprendere meglio questi requisiti, consultare il white paper  [Ottenere la conformità in materia di sicurezza e residenza dei dati con Azure](https://azure.microsoft.com/resources/achieving-compliant-data-residency-and-security-with-azure).

Una parte degli sforzi di conformità potrebbe includere il controllo della posizione fisica delle risorse del database. Le aree di Azure sono organizzate in gruppi denominati "aree geografiche". Un' [area geografica di Azure](https://azure.microsoft.com/global-infrastructure/geographies) assicura il rispetto dei requisiti di residenza, sovranità, conformità e resilienza dei dati entro limiti geografici e politici. Se i carichi di lavoro sono soggetti a sovranità dei dati o ad altri requisiti di conformità, è necessario distribuire le risorse di archiviazione in aree situate in un'area geografica di Azure conforme.

## <a name="establish-controls-for-database-services"></a>Definire i controlli per i servizi di database

Quando si prepara l'ambiente della zona di destinazione, è possibile stabilire i controlli che limitano gli archivi dati che gli utenti possono distribuire. I controlli possono aiutare a gestire i costi e a limitare i rischi per la sicurezza, consentendo allo stesso tempo agli sviluppatori e ai team IT di distribuire e configurare le risorse necessarie per supportare i carichi di lavoro.

Dopo aver identificato e documentato i requisiti della zona di destinazione, è possibile usare [Criteri di Azure](https://docs.microsoft.com/azure/governance/policy/overview) per controllare le risorse di database che possono essere create dagli utenti. I controlli possono consistere nel [consentire o negare la creazione di tipi di risorse di database](https://docs.microsoft.com/azure/governance/policy/samples/allowed-resource-types). È ad esempio possibile limitare gli utenti consentendo loro di creare solo risorse del database SQL di Azure. È anche possibile usare i criteri per controllare le opzioni consentite quando viene creata una risorsa, ad esempio [limitare gli SKU del database SQL di cui è possibile eseguire il provisioning](https://docs.microsoft.com/azure/governance/policy/samples/allowed-sql-db-skus) o [consentire solo versioni specifiche del server SQL](https://docs.microsoft.com/azure/governance/policy/samples/require-sql-12) da installare in una macchina virtuale IaaS.

I criteri possono essere limitati a risorse, gruppi di risorse, sottoscrizioni e gruppi di gestione. È possibile includere i criteri nelle definizioni di [Azure Blueprints](https://docs.microsoft.com/azure/governance/blueprints/overview) e applicarli ripetutamente all'interno dell'ambiente cloud.
