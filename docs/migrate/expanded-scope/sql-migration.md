---
title: Accelera la migrazione con una migrazione SQL
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Accelera la migrazione con una migrazione SQL
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/10/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 4af94af91874ac666f45a917eed003b3cf881c51
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72558220"
---
# <a name="accelerate-migration-with-a-sql-migration"></a>Accelera la migrazione con una migrazione SQL

La migrazione di intere istanze di SQL Server può accelerare gli sforzi di migrazione Le linee guida riportate di seguito consentono di espandere l'ambito della [Guida alla migrazione di Azure](../azure-migration-guide/index.md) eseguendo la migrazione di un SQL Server al di fuori di una migrazione incentrata sul carico Questo approccio consente di effettuare il seeding della migrazione di più carichi di lavoro con una singola migrazione della piattaforma dati.

## <a name="general-scope-expansion"></a>Espansione dell'ambito generale

La maggior parte degli sforzi necessari in questa espansione dell'ambito si verificherà durante i prerequisiti, la valutazione, la migrazione e i processi di ottimizzazione di un'operazione di migrazione.

<!-- markdownlint-disable MD026 -->

## <a name="is-this-expanded-scope-right-for-you"></a>Questo ambito è più adatto per l'utente?

L'approccio consigliato descritto nella [Guida alla migrazione di Azure](../azure-migration-guide/index.md) consiste nel migrare ogni struttura dei dati insieme ai carichi di lavoro associati come parte di una singola operazione di migrazione. L'approccio iterativo alla migrazione riduce l'individuazione, la valutazione e altre attività in grado di creare blocchi e restituire valori di business lenti.

Tuttavia, è possibile eseguire la migrazione di alcune strutture di dati in modo più efficace tramite una migrazione della piattaforma dati separata. Di seguito sono riportati alcuni esempi che possono comportare l'uso di queste linee guida per l'ambito espanse:

- **Fine del servizio:** Lo spostamento rapido di un'istanza di SQL Server per evitare problemi di fine servizio può giustificare l'uso di questa guida al di fuori delle attività di migrazione standard.
- **Servizi SQL Server:** La struttura dei dati fa parte di una soluzione più ampia che richiede l'esecuzione di SQL Server in una macchina virtuale. Si tratta di un problema comune per le soluzioni che sfruttano SQL Server servizi, ad esempio SQL Server Reporting Services, SQL Server Integration Services o SQL Server Analysis Services.
- **Database ad alta densità, utilizzo ridotto:** Il SQL Server ha una densità elevata di database. Ognuno di questi database dispone di volumi di transazione limitati e richiede piccole risorse di calcolo. È consigliabile prendere in considerazione altre soluzioni più moderne, ma un approccio IaaS può comportare un notevole riduzione dei costi operativi.
- **Costo totale di proprietà:** Se applicabile, i [vantaggi di Azure Hybrid](https://azure.microsoft.com/pricing/hybrid-benefit) possono essere applicati al prezzo di listino creando il costo di proprietà più basso per SQL Server. Questa operazione è particolarmente comune per i clienti che ospitano SQL Server in scenari con più cloud.
- **Acceleratore migrazione:** La migrazione in modalità Lift-and-Shift di un'istanza di SQL Server può spostare più database in un'unica iterazione. Questo approccio talvolta consente alle iterazioni future di concentrarsi più specificamente sulle applicazioni e sulle macchine virtuali, eseguendo la migrazione di più carichi di lavoro in una singola iterazione.
- **Migrazione di VMware:** Un'architettura locale comune include le applicazioni e le macchine virtuali in un host virtuale e i database in bare metal. Quando si esegue la migrazione di questa architettura comune, la migrazione dell'host VMWare al servizio VMWare di Azure (AVS) può essere completata da questa guida per eseguire la migrazione di intere istanze di SQL Server per supportare tali host virtuali. Per istruzioni gratuite, vedere [migrazione di host VMware](./vmware-host.md).

Se nessuno dei criteri precedenti si applica a questa migrazione, potrebbe essere consigliabile continuare con il processo di [migrazione standard](../index.md). Nel processo standard, le strutture dei dati vengono migrate in modo iterativo insieme a ogni carico di lavoro.

Se questa guida è allineata ai criteri, continuare con questa guida all'ambito espansa come impegno nel [processo di migrazione standard](../index.md). Durante la fase dei prerequisiti, il lavoro richiesto può essere integrato nel piano di adozione generale.

## <a name="suggested-prerequisites"></a>Prerequisiti suggeriti

Prima di eseguire una migrazione di SQL Server, è necessario iniziare con l'espansione del **patrimonio digitale** includendo una data. Il patrimonio di dati registra un inventario degli asset di dati considerati per la migrazione. Le tabelle seguenti illustrano un approccio per la registrazione del patrimonio di dati.

### <a name="server-inventory"></a>Inventario server

Di seguito è riportato un esempio di inventario server per SQL Server:

|SQL Server|Finalità|Versione|[Criticità](../../manage/considerations/criticality.md)|[Riservatezza](../../govern/policy-compliance/data-classification.md)|Conteggio database|SSIS|SSRS|SSAS|HDInsight|Numero di nodi|
|---------|---------|---------|---------|---------|---------|---------|---------|
|SQL-01|App principali|2016|Mission-critical|Riservatezza elevata|40|N/D|N/D|N/D|SÌ|3|
|SQL-02|App principali|2016|Mission-critical|Riservatezza elevata|40|N/D|N/D|N/D|SÌ|3|
|SQL-03|App principali|2016|Mission-critical|Riservatezza elevata|40|N/D|N/D|N/D|SÌ|3|
|SQL-04|BI|2012|Alte|XX|6|N/D|Riservate|Sì-cubo multidimensionale|No|1|
|SQL-05|Integrazione|2008 R2|Basse|Informazioni di carattere generale|20|SÌ|N/D|N/D|No|1|

### <a name="database-inventory"></a>Inventario database

Di seguito è riportato un esempio di inventario di un database per una delle versioni precedenti di SQL Server:

|Server|Database|[Criticità](../../manage/considerations/criticality.md)|[Riservatezza](../../govern/policy-compliance/data-classification.md)|Risultati DMA|Monitoraggio e aggiornamento DMA|Piattaforma di destinazione|
|---------|---------|---------|---------|---------|---------|---------|
|SQL-01|DB-1|Mission-critical|Riservatezza elevata|Compatibile|N/D|database SQL di Azure|
|SQL-01|DB-2|Alte|Riservate|Modifica dello schema obbligatoria|Modifiche implementate|database SQL di Azure|
|SQL-01|DB-1|Alte|Informazioni di carattere generale|Compatibile|N/D|Istanza gestita di SQL di Azure|
|SQL-01|DB-1|Basse|Riservatezza elevata|Modifica dello schema obbligatoria|Modifiche pianificate|Istanza gestita di SQL di Azure|
|SQL-01|DB-1|Mission-critical|Informazioni di carattere generale|Compatibile|N/D|Istanza gestita di SQL di Azure|
|SQL-01|DB-2|Alte|Riservate|Compatibile|N/D|database SQL di Azure|

### <a name="integration-with-the-cloud-adoption-plan"></a>Integrazione con il piano di adozione del cloud

Al termine dell'individuazione, il piano può essere incluso nel [piano di adozione del cloud](../../plan/template.md). All'interno del piano di adozione del cloud, aggiungere ogni istanza di SQL Server da migrare come [carico di lavoro distinto](../../plan/workloads.md). All'interno di ogni carico di lavoro, i database e i servizi (SSIS, SSAS, SSRS) possono essere aggiunti come [Asset](../../plan/workloads.md). Per aggiungere i carichi di lavoro e gli asset in blocco al piano di adozione, vedere [aggiunta e modifica di elementi di lavoro con Excel](https://docs.microsoft.com/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel?view=azure-devops).

Una volta inclusi i carichi di lavoro e gli asset nel piano, il team può proseguire con un processo di migrazione standard usando il piano di adozione per guidare le attività. Quando il team di adozione si sposta nei processi di valutazione, migrazione e ottimizzazione, le modifiche seguenti dovrebbero essere suddivise in sforzi.

## <a name="assessment-process-changes"></a>Modifiche al processo di valutazione

Se è possibile eseguire la migrazione di un database nel piano a una piattaforma dati PaaS (Platform as a Service), utilizzare Data Migration Assistant per valutare la compatibilità del database selezionato. Quando il database richiede le conversioni dello schema, è consigliabile che tali conversioni siano completate come parte del processo di valutazione per evitare le rotture alla pipeline di migrazione.

### <a name="suggested-action-during-the-assessment-process"></a>Azione suggerita durante il processo di valutazione

Per i database di cui è possibile eseguire la migrazione a una soluzione PaaS, durante il processo di valutazione verranno completate le azioni seguenti.

- **Valutazione con Data Migration Assistant:** Usare Data Migration Assistant per rilevare i problemi di compatibilità che possono influisca sulle funzionalità di database nell'istanza gestita di database SQL di Azure di destinazione, per consigliare miglioramenti delle prestazioni e dell'affidabilità e per spostare lo schema, i dati e gli oggetti non contenuti dal server di origine al server di destinazione. Per ulteriori informazioni, vedere [Data Migration Assistant](/sql/dma/dma-overview).
- **Correzione e conversione:** In base all'output di Data Migration Assistant, convertire lo schema dei dati di origine per correggere i problemi di compatibilità. Testare lo schema di dati convertito con le applicazioni dipendenti.

## <a name="migrate-process-changes"></a>Modifiche del processo di migrazione

Durante la migrazione sono disponibili diverse opzioni di strumenti e approcci. Tuttavia, ogni approccio segue un processo semplice: eseguire la migrazione dello schema, dei dati e degli oggetti. Sincronizzare i dati con l'origine dati di destinazione.

La destinazione e l'origine della struttura dei dati e dei servizi possono rendere questi due passaggi piuttosto complicati. Per comprendere meglio la scelta degli strumenti in base alle decisioni di migrazione, vedere le sezioni seguenti.

### <a name="suggested-action-during-the-migrate-process"></a>Azione suggerita durante il processo di migrazione

Il percorso suggerito per la migrazione e la sincronizzazione utilizza una combinazione dei tre strumenti seguenti. Le sezioni seguenti descrivono le opzioni di migrazione e sincronizzazione più complesse che consentono una gamma più ampia di soluzioni di destinazione e di origine.

|Opzione di migrazione|Finalità|
|---------|---------|
|[Servizio Migrazione del database di Azure](/sql/dma/dma-overview)|Azure DMS supporta le migrazioni online (tempo di inattività minimo) e offline (una volta) su larga scala a un'istanza gestita di database SQL di Azure da SQL Server 2005, SQL Server 2008 e SQL Server 2008 R2, SQL Server 2012, SQL Server 2014, SQL Server 2016 e SQL Server 2017.|
|[Replica transazionale](/sql/relational-databases/replication/administration/enhance-transactional-replication-performance)|La replica transazionale in un'istanza gestita di database SQL di Azure è supportata per le migrazioni da: SQL Server 2012 (SP2 CU8, SP3 o versioni successive), SQL Server 2014 (RTM CU10 dalla o versione successiva o SP1 CU3 o versione successiva), SQL Server 2016, SQL Server 2017|
|[Caricamento bulk](/sql/t-sql/statements/bulk-insert-transact-sql)|Usare il caricamento bulk in un'istanza gestita di database SQL di Azure per i dati archiviati in SQL Server 2005, SQL Server 2008 e SQL Server 2008 R2, SQL Server 2012, SQL Server 2014, SQL Server 2016 e SQL Server 2017.|

### <a name="guidance-and-tutorials-for-suggested-migration-process"></a>Indicazioni ed esercitazioni per il processo di migrazione suggerito

La scelta delle linee guida ottimali per la migrazione tramite DMS è contingente alla piattaforma di origine e di destinazione scelta. Nella tabella seguente vengono descritte le esercitazioni per ognuno degli approcci standard per la migrazione di un database SQL tramite DMS.

|Source (Sorgente)  |Obiettivo  |Strumento  |Tipo di migrazione  |Guida  |
|---------|---------|---------|---------|---------|
|SQL Server|database SQL di Azure|Servizio Migrazione del database|Offline|[Esercitazione](https://docs.microsoft.com/azure/dms/tutorial-sql-server-to-azure-sql)|
|SQL Server|database SQL di Azure|Servizio Migrazione del database|Online|[Esercitazione](https://docs.microsoft.com/azure/dms/tutorial-sql-server-azure-sql-online)|
|SQL Server|Istanza gestita di database SQL di Azure|Servizio Migrazione del database|Offline|[Esercitazione](https://docs.microsoft.com/azure/dms/tutorial-sql-server-to-managed-instance)|
|SQL Server|Istanza gestita di database SQL di Azure|Servizio Migrazione del database|Online|[Esercitazione](https://docs.microsoft.com/azure/dms/tutorial-sql-server-managed-instance-online)|
|SQL Server RDS|Database SQL di Azure (o Istanza gestita)|Servizio Migrazione del database|Online|[Esercitazione](https://docs.microsoft.com/azure/dms/tutorial-rds-sql-server-azure-sql-and-managed-instance-online)|

### <a name="guidance-and-tutorials-for-various-services-to-equivalent-paas-solutions"></a>Indicazioni ed esercitazioni per vari servizi per soluzioni PaaS equivalenti

Dopo aver spostato i database da SQL Server a DMS, lo schema e i dati possono essere riallocati in diverse soluzioni PaaS. Tuttavia, altri servizi necessari potrebbero essere ancora in esecuzione su tale server. Le tre esercitazioni seguenti aiuteranno a trasferire SSIS, SSAS e SSRS ai servizi PaaS equivalenti in Azure.

|Source (Sorgente)  |Obiettivo  |Strumento  |Tipo di migrazione  |Guida  |
|---------|---------|---------|---------|---------|
|Servizio di integrazione SQL Server|Data Factory Integration Runtime|Data factory di Azure|Offline|[Esercitazione](https://docs.microsoft.com/azure/data-factory/create-azure-ssis-integration-runtime)|
|SQL Server Analysis Services-modello tabulare|Azure Analysis Services|SSDT|Offline|[Esercitazione](https://docs.microsoft.com/azure/analysis-services/analysis-services-deploy)|
|SQL Server Reporting Service|Server di report di Power BI|Power BI|Offline|[Esercitazione](/power-bi/report-server/migrate-report-server)|

### <a name="guidance-and-tutorials-for-migration-from-sql-server-to-an-iaas-instance-of-sql-server"></a>Indicazioni ed esercitazioni per la migrazione da SQL Server a un'istanza IaaS di SQL Server

Dopo la migrazione di database e servizi a istanze PaaS, è possibile che esistano ancora strutture di dati e servizi che non sono compatibili con PaaS. Quando i vincoli esistenti impediscono la migrazione di strutture di dati o servizi, l'esercitazione seguente può essere utile per la migrazione di varie risorse nel portfolio di dati alle soluzioni Azure IaaS.

Questo approccio può essere usato per eseguire la migrazione dei database nel SQL Server o in altri servizi in esecuzione nell'SQL Server di origine.

|Source (Sorgente)  |Obiettivo  |Strumento  |Tipo di migrazione  |Guida  |
|---------|---------|---------|---------|---------|
|SQL Server a istanza singola|SQL Server in IaaS|Diversi|Offline|[Esercitazione](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-migrate-sql)|

## <a name="optimization-process-changes"></a>Modifiche al processo di ottimizzazione

Durante l'ottimizzazione, ogni istanza di struttura di dati, servizio o SQL Server può essere testata, ottimizzata e promossa alla produzione. Questo è il maggior effetto della deviazione da un modello di migrazione per ogni carico di lavoro.

Idealmente, verrà eseguita la migrazione dei carichi di lavoro, delle applicazioni e delle macchine virtuali dipendenti nella stessa iterazione dell'istanza di SQL Server. Quando si verifica questo scenario ideale, il carico di lavoro può essere testato insieme all'origine dati. Una volta testato, la struttura dei dati può essere promossa alla produzione e il processo di sincronizzazione può essere terminato.

Sfortunatamente, la maggiore variazione del processo di ottimizzazione durante una migrazione non basata su carico di lavoro si verifica quando si verifica un lasso di tempo significativo tra la migrazione del database e la migrazione del carico di lavoro. Quando si esegue la migrazione di più database come parte di una migrazione SQL Server, i database possono coesistere sia nel cloud che in locale per più iterazioni. Durante questo intervallo di tempo, è necessario mantenere la sincronizzazione dei dati fino a quando non viene eseguita la migrazione, il test e la promozione degli asset dipendenti.

Fino a quando non vengono promossi tutti i carichi di lavoro dipendenti, il team sarà responsabile del supporto della sincronizzazione dei dati dal sistema di origine al sistema di destinazione. Questa sincronizzazione usa la larghezza di banda di rete, i costi del cloud e, soprattutto, il tempo delle persone. Un corretto allineamento del piano di adozione nel SQL Server "carico di lavoro" della migrazione e in tutti i carichi di lavoro o le applicazioni dipendenti, ridurrebbe questo costo di overhead.

### <a name="suggested-action-during-the-optimization-process"></a>Azione suggerita durante il processo di ottimizzazione

Durante i processi di ottimizzazione, le attività seguenti devono essere completate ogni iterazione fino a quando tutti i servizi e le strutture di dati non sono stati promossi alla produzione.

1. Convalidare la sincronizzazione dei dati.
2. Testare tutte le applicazioni migrate.
3. Ottimizzare l'applicazione e la struttura dei dati per ottimizzare i costi.
4. Innalzare di livello le applicazioni alla produzione.
5. Testare il traffico locale continuato rispetto al database locale.
6. Termina la sincronizzazione dei dati promossi alla produzione.
7. Terminare il database di origine originale.

Fino al passaggio 5, i database e la sincronizzazione non possono essere terminati. Fino a quando tutti i database in un SQL Server non sono passati attraverso i passaggi 1-7, la SQL Server locale deve essere considerata come produzione e deve essere mantenuta tutta la sincronizzazione.

## <a name="next-steps"></a>Passaggi successivi

Tornare all'[elenco di controllo per l'espansione dell'ambito](./index.md) per verificare che il metodo di migrazione sia completamente allineato.

> [!div class="nextstepaction"]
> [Elenco di controllo per l'espansione dell'ambito](./index.md)
