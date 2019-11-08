---
title: Accelerazione della migrazione mediante la migrazione di un'istanza di SQL Server
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: La migrazione di intere istanze di SQL Server può accelerare gli sforzi di migrazione
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/10/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 71632e8f3f995922f4021f216f2090b742141169
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73753532"
---
# <a name="accelerate-migration-by-migrating-an-instance-of-sql-server"></a>Accelerazione della migrazione mediante la migrazione di un'istanza di SQL Server

La migrazione di intere istanze di SQL Server può accelerare gli sforzi di migrazione Il materiale sussidiario seguente espande l'ambito della [Guida alla migrazione di Azure](../azure-migration-guide/index.md) eseguendo la migrazione di un'istanza di SQL Server al di fuori di un'attività di migrazione incentrata sul carico di lavoro. Questo approccio consente di effettuare il seeding della migrazione di più carichi di lavoro con una singola migrazione della piattaforma dati. La maggior parte degli sforzi richiesti in questa espansione dell'ambito si verifica durante i prerequisiti, la valutazione, la migrazione e i processi di ottimizzazione di un'operazione di migrazione.

<!-- markdownlint-disable MD026 -->

## <a name="is-this-expanded-scope-right-for-you"></a>Questo ambito è più adatto per l'utente?

L'approccio consigliato nella [Guida alla migrazione di Azure](../azure-migration-guide/index.md) consiste nel migrare ogni struttura dei dati insieme ai carichi di lavoro associati nell'ambito di una singola operazione di migrazione. L'approccio iterativo alla migrazione riduce l'individuazione, la valutazione e altre attività in grado di creare blocchi e restituire valori di business lenti.

Tuttavia, è possibile eseguire la migrazione di alcune strutture di dati in modo più efficace tramite una migrazione della piattaforma dati separata. Di seguito sono riportati alcuni esempi:

- **Fine del servizio:** Lo spostamento rapido di un'istanza di SQL Server per evitare problemi di fine servizio può giustificare l'utilizzo di questa guida al di fuori delle attività di migrazione standard.
- **Servizi SQL Server:** La struttura dei dati fa parte di una soluzione più ampia che richiede l'esecuzione di SQL Server in una macchina virtuale. Si tratta di un problema comune per le soluzioni che usano SQL Server servizi, ad esempio SQL Server Reporting Services, SQL Server Integration Services o SQL Server Analysis Services.
- **Database ad alta densità, utilizzo ridotto:** L'istanza di SQL Server dispone di una densità elevata di database. Ognuno di questi database dispone di volumi di transazione limitati e richiede poco in termini di risorse di calcolo. È consigliabile prendere in considerazione altre soluzioni più moderne, ma un approccio di infrastruttura distribuita come servizio (IaaS) può comportare un notevole riduzione dei costi operativi.
- **Costo totale di proprietà:** Quando applicabile, è possibile applicare i [vantaggi di Azure Hybrid](https://azure.microsoft.com/pricing/hybrid-benefit) al prezzo di listino creando il costo di proprietà più basso per le istanze di SQL Server. Questa operazione è particolarmente comune per i clienti che ospitano SQL Server in scenari con più cloud.
- **Acceleratore migrazione:** La migrazione "Lift-and-Shift" di un'istanza di SQL Server può spostare più database in un'unica iterazione. Questo approccio consente a volte le iterazioni future di concentrarsi più specificamente sulle applicazioni e sulle macchine virtuali, vale a dire che è possibile eseguire la migrazione di più carichi di lavoro in una singola iterazione.
- **Migrazione di VMware:** Un'architettura locale comune include le applicazioni e le macchine virtuali in un host virtuale e i database in bare metal. In questo scenario, è possibile eseguire la migrazione di intere istanze di SQL Server per supportare la migrazione dell'host VMware al servizio VMware di Azure. Per ulteriori informazioni, vedere [migrazione di host VMware](./vmware-host.md).

Se nessuno dei criteri precedenti si applica a questa migrazione, potrebbe essere consigliabile continuare con il processo di [migrazione standard](../index.md). Nel processo standard, le strutture dei dati vengono migrate in modo iterativo, insieme a ogni carico di lavoro.

Se questa guida è allineata ai criteri, continuare con questa guida all'ambito espansa come impegno nel [processo di migrazione standard](../index.md). Durante la fase dei prerequisiti, è possibile integrare il lavoro richiesto nel piano di adozione generale.

## <a name="suggested-prerequisites"></a>Prerequisiti suggeriti

Prima di eseguire una migrazione di SQL Server, è necessario iniziare con l'espansione del patrimonio digitale includendo una data. Il patrimonio di dati registra un inventario degli asset di dati che si sta considerando per la migrazione. Le tabelle seguenti illustrano un approccio per la registrazione del patrimonio di dati.

### <a name="server-inventory"></a>Inventario server

Di seguito è riportato un esempio di inventario server:

|SQL Server|Finalità|Versione|[Criticità](../../manage/considerations/criticality.md)|[Riservatezza](../../govern/policy-compliance/data-classification.md)|Conteggio database|SSIS|SSRS|SSAS|HDInsight|Numero di nodi|
|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|---------|
|SQL-01|App principali|2016|Cruciale|Riservatezza elevata|40|N/D|N/D|N/D|SÌ|3|
|SQL-02|App principali|2016|Cruciale|Riservatezza elevata|40|N/D|N/D|N/D|SÌ|3|
|SQL-03|App principali|2016|Cruciale|Riservatezza elevata|40|N/D|N/D|N/D|SÌ|3|
|SQL-04|BI|2012|Alte|XX|6|N/D|Riservate|Sì-cubo multidimensionale|No|1|
|SQL-05|Integrazione|2008 R2|Basse|Informazioni di carattere generale|20|SÌ|N/D|N/D|No|1|

### <a name="database-inventory"></a>Inventario database

Di seguito è riportato un esempio di inventario del database per uno dei server precedenti:

|Server|Database|[Criticità](../../manage/considerations/criticality.md)|[Riservatezza](../../govern/policy-compliance/data-classification.md)|Risultati di Data Migration Assistant (DMA)|Monitoraggio e aggiornamento DMA|Piattaforma di destinazione|
|---------|---------|---------|---------|---------|---------|---------|
|SQL-01|DB-1|Cruciale|Riservatezza elevata|Compatibile|N/D|database SQL di Azure|
|SQL-01|DB-2|Alte|Riservate|Modifica dello schema obbligatoria|Modifiche implementate|database SQL di Azure|
|SQL-01|DB-1|Alte|Informazioni di carattere generale|Compatibile|N/D|Istanza gestita di SQL di Azure|
|SQL-01|DB-1|Basse|Riservatezza elevata|Modifica dello schema obbligatoria|Modifiche pianificate|Istanza gestita di SQL di Azure|
|SQL-01|DB-1|Cruciale|Informazioni di carattere generale|Compatibile|N/D|Istanza gestita di SQL di Azure|
|SQL-01|DB-2|Alte|Riservate|Compatibile|N/D|database SQL di Azure|

### <a name="integration-with-the-cloud-adoption-plan"></a>Integrazione con il piano di adozione del cloud

Al termine del processo di individuazione, è possibile includerlo nel [piano di adozione del cloud](../../plan/template.md). All'interno del piano di adozione del cloud, aggiungere ogni istanza di SQL Server da migrare come [carico di lavoro distinto](../../plan/workloads.md). All'interno di ogni carico di lavoro, i database e i servizi (SSIS, SSAS, SSRS) possono essere aggiunti come [Asset](../../plan/workloads.md). Per aggiungere i carichi di lavoro e gli asset in blocco al piano di adozione, vedere [aggiunta e modifica di elementi di lavoro con Excel](https://docs.microsoft.com/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel?view=azure-devops).

Dopo che i carichi di lavoro e gli asset sono stati inclusi nel piano, l'utente e il team possono continuare con un processo di migrazione standard usando il piano di adozione. Quando il team di adozione si sposta nei processi di valutazione, migrazione e ottimizzazione, è importante considerare le modifiche descritte nelle sezioni seguenti.

## <a name="assessment-process-changes"></a>Modifiche al processo di valutazione

Se è possibile eseguire la migrazione di un database nel piano a una piattaforma dati PaaS (Platform as a Service), utilizzare DMA per valutare la compatibilità del database selezionato. Quando il database richiede le conversioni dello schema, è necessario completare le conversioni come parte del processo di valutazione, per evitare le rotture alla pipeline di migrazione.

### <a name="suggested-action-during-the-assessment-process"></a>Azione suggerita durante il processo di valutazione

Per i database di cui è possibile eseguire la migrazione a una soluzione PaaS, durante il processo di valutazione vengono completate le azioni seguenti.

- **Valutazione con DMA:** Usare Data Migration Assistant per rilevare i problemi di compatibilità che possono influire sulla funzionalità del database nell'istanza gestita di database SQL di Azure di destinazione. Utilizzare DMA per consigliare miglioramenti in merito a prestazioni e affidabilità e per spostare lo schema, i dati e gli oggetti non indipendenti dal server di origine al server di destinazione. Per ulteriori informazioni, vedere [Data Migration Assistant](https://docs.microsoft.com/sql/dma/dma-overview).
- **Correzione e conversione:** In base all'output di DMA, convertire lo schema dei dati di origine per correggere i problemi di compatibilità. Testare lo schema di dati convertito con le applicazioni dipendenti.

## <a name="migrate-process-changes"></a>Modifiche del processo di migrazione

Durante la migrazione è possibile scegliere tra molti strumenti e approcci diversi. Tuttavia, ogni approccio segue un processo semplice: eseguire la migrazione dello schema, dei dati e degli oggetti. Sincronizzare quindi i dati con l'origine dati di destinazione.

La destinazione e l'origine della struttura dei dati e dei servizi possono rendere questi due passaggi piuttosto complicati. Le sezioni seguenti consentono di comprendere meglio la scelta degli strumenti in base alle decisioni di migrazione.

### <a name="suggested-action-during-the-migrate-process"></a>Azione suggerita durante il processo di migrazione

Il percorso suggerito per la migrazione e la sincronizzazione utilizza una combinazione dei tre strumenti seguenti. Le sezioni seguenti descrivono le opzioni di migrazione e sincronizzazione più complesse che consentono una gamma più ampia di soluzioni di destinazione e di origine.

|Opzione di migrazione|Finalità|
|---------|---------|
|[Servizio Migrazione del database di Azure](https://docs.microsoft.com/sql/dma/dma-overview)|Supporta migrazioni in linea (tempo di inattività minimo) e offline (una volta) su larga scala a un'istanza gestita di database SQL di Azure. Supporta la migrazione da: SQL Server 2005, SQL Server 2008 e SQL Server 2008 R2, SQL Server 2012, SQL Server 2014, SQL Server 2016 e SQL Server 2017.|
|[Replica transazionale](https://docs.microsoft.com/sql/relational-databases/replication/administration/enhance-transactional-replication-performance)|La replica transazionale in un'istanza gestita di database SQL di Azure è supportata per le migrazioni da: SQL Server 2012 (SP2 CU8, SP3 o versioni successive), SQL Server 2014 (RTM CU10 dalla o versione successiva o SP1 CU3 o versione successiva), SQL Server 2016, SQL Server 2017.|
|[Caricamento bulk](https://docs.microsoft.com/sql/t-sql/statements/bulk-insert-transact-sql)|Usare il caricamento bulk in un'istanza gestita di database SQL di Azure per i dati archiviati in: SQL Server 2005, SQL Server 2008 e SQL Server 2008 R2, SQL Server 2012, SQL Server 2014, SQL Server 2016 e SQL Server 2017.|

### <a name="guidance-and-tutorials-for-suggested-migration-process"></a>Indicazioni ed esercitazioni per il processo di migrazione suggerito

La scelta delle linee guida consigliate per la migrazione tramite il servizio migrazione del database di Azure dipende dalla piattaforma di origine e destinazione scelta. La tabella seguente contiene collegamenti alle esercitazioni per ognuno degli approcci standard per la migrazione di un database SQL tramite il servizio migrazione del database di Azure.

|Source (Sorgente)  |Obiettivo  |Strumento  |Tipo di migrazione  |Guida  |
|---------|---------|---------|---------|---------|
|SQL Server|database SQL di Azure|Database Migration Service|Offline|[Esercitazione](https://docs.microsoft.com/azure/dms/tutorial-sql-server-to-azure-sql)|
|SQL Server|database SQL di Azure|Database Migration Service|Online|[Esercitazione](https://docs.microsoft.com/azure/dms/tutorial-sql-server-azure-sql-online)|
|SQL Server|Istanza gestita di Database SQL di Azure|Database Migration Service|Offline|[Esercitazione](https://docs.microsoft.com/azure/dms/tutorial-sql-server-to-managed-instance)|
|SQL Server|Istanza gestita di Database SQL di Azure|Database Migration Service|Online|[Esercitazione](https://docs.microsoft.com/azure/dms/tutorial-sql-server-managed-instance-online)|
|SQL Server RDS|Database SQL di Azure (o istanza gestita)|Database Migration Service|Online|[Esercitazione](https://docs.microsoft.com/azure/dms/tutorial-rds-sql-server-azure-sql-and-managed-instance-online)|

### <a name="guidance-and-tutorials-for-various-services-to-equivalent-paas-solutions"></a>Indicazioni ed esercitazioni per vari servizi per soluzioni PaaS equivalenti

Dopo lo spostamento dei database da un'istanza di SQL Server al servizio migrazione del database di Azure, lo schema e i dati possono essere riallocati in diverse soluzioni PaaS. Tuttavia, altri servizi necessari potrebbero essere ancora in esecuzione su tale server. Le tre esercitazioni seguenti facilitano lo trasferimento di SSIS, SSAS e SSRS ai servizi PaaS equivalenti in Azure.

|Source (Sorgente)  |Obiettivo  |Strumento  |Tipo di migrazione  |Guida  |
|---------|---------|---------|---------|---------|
|SQL Server Integration Services|Azure Data Factory runtime di integrazione|Data factory di Azure|Offline|[Esercitazione](https://docs.microsoft.com/azure/data-factory/create-azure-ssis-integration-runtime)|
|Modello tabulare SQL Server Analysis Services|Azure Analysis Services|SQL Server Data Tools|Offline|[Esercitazione](https://docs.microsoft.com/azure/analysis-services/analysis-services-deploy)|
|SQL Server Reporting Services|Server di report di Power BI|Power BI|Offline|[Esercitazione](https://docs.microsoft.com/power-bi/report-server/migrate-report-server)|

### <a name="guidance-and-tutorials-for-migration-from-sql-server-to-an-iaas-instance-of-sql-server"></a>Indicazioni ed esercitazioni per la migrazione da SQL Server a un'istanza IaaS di SQL Server

Dopo aver eseguito la migrazione di database e servizi a istanze PaaS, è possibile che siano ancora presenti strutture di dati e servizi non compatibili con PaaS. Quando i vincoli esistenti impediscono la migrazione di strutture di dati o servizi, l'esercitazione seguente può essere utile per la migrazione di varie risorse nel portfolio di dati alle soluzioni Azure IaaS.

Utilizzare questo approccio per eseguire la migrazione di database o altri servizi nell'istanza di SQL Server.

|Source (Sorgente)  |Obiettivo  |Strumento  |Tipo di migrazione  |Guida  |
|---------|---------|---------|---------|---------|
|SQL Server a istanza singola|SQL Server in IaaS|Diversi|Offline|[Esercitazione](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-migrate-sql)|

## <a name="optimization-process-changes"></a>Modifiche al processo di ottimizzazione

Durante l'ottimizzazione, è possibile eseguire test, ottimizzare e innalzare di livello alla produzione ogni struttura di dati, servizio o istanza di SQL Server. Questo è il maggior effetto della deviazione da un modello di migrazione per ogni carico di lavoro.

Idealmente, migrare i carichi di lavoro dipendenti, le applicazioni e le macchine virtuali all'interno della stessa iterazione dell'istanza di SQL Server. Quando si verifica questo scenario ideale, è possibile testare il carico di lavoro insieme all'origine dati. Dopo il test, è possibile alzare di livello la struttura dei dati alla produzione e terminare il processo di sincronizzazione.

Si prenda ora in considerazione lo scenario in cui si verifica un notevole gap di tempo tra migrazione del database e migrazione del carico di lavoro. Sfortunatamente, questo può essere il passaggio più importante per il processo di ottimizzazione durante una migrazione non basata sul carico di lavoro. Quando si esegue la migrazione di più database come parte di una migrazione SQL Server, i database possono coesistere sia nel cloud che in locale per più iterazioni. Durante questo periodo, è necessario mantenere la sincronizzazione dei dati fino a quando non viene eseguita la migrazione, il test e la promozione degli asset dipendenti.

Fino a quando non vengono promossi tutti i carichi di lavoro dipendenti, l'utente e il team sono responsabili del supporto della sincronizzazione dei dati dal sistema di origine al sistema di destinazione. Questa sincronizzazione usa la larghezza di banda di rete, i costi del cloud e, soprattutto, il tempo delle persone. Un corretto allineamento del piano di adozione nel carico di lavoro della migrazione SQL Server e di tutti i carichi di lavoro e le applicazioni dipendenti può ridurre il costo del sovraccarico.

### <a name="suggested-action-during-the-optimization-process"></a>Azione suggerita durante il processo di ottimizzazione

Durante i processi di ottimizzazione, completare le seguenti attività ogni iterazione, fino a quando tutti i servizi e le strutture di dati non sono stati promossi alla produzione.

1. Convalidare la sincronizzazione dei dati.
2. Testare tutte le applicazioni migrate.
3. Ottimizzare l'applicazione e la struttura dei dati per ottimizzare i costi.
4. Innalzare di livello le applicazioni alla produzione.
5. Testare il traffico locale continuato rispetto al database locale.
6. Termina la sincronizzazione dei dati promossi alla produzione.
7. Terminare il database di origine originale.

Non è possibile terminare i database e la sincronizzazione finché non viene superato il passaggio 5. Fino a quando tutti i database in un'istanza di non SQL Server stato sottoposto a tutti i sette passaggi, è consigliabile considerare l'istanza locale di SQL Server come produzione. È necessario mantenere tutte le sincronizzazioni.

## <a name="next-steps"></a>Passaggi successivi

Tornare all'[elenco di controllo per l'espansione dell'ambito](./index.md) per verificare che il metodo di migrazione sia completamente allineato.

> [!div class="nextstepaction"]
> [Elenco di controllo per l'espansione dell'ambito](./index.md)
