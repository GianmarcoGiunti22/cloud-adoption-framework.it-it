---
title: Panoramica degli esempi di migrazione delle applicazioni per Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Fornisce una panoramica degli esempi di migrazione delle applicazioni inclusi nella sezione relativa alla migrazione di Cloud Adoption Framework.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/11/2018
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: a6af51f1fa6526e2ea7cf13a824c7834d631aa59
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70820583"
---
# <a name="application-migration-patterns-and-examples"></a>Esempi e modelli di migrazione delle applicazioni

Questa sezione di Cloud Adoption Framework fornisce esempi di diversi scenari di migrazione comuni che illustrano come è possibile eseguire la migrazione dell'infrastruttura locale al cloud di [Microsoft Azure](https://azure.microsoft.com/overview/what-is-azure).

## <a name="introduction"></a>Introduzione

Azure offre l'accesso a un set completo di servizi cloud. Sviluppatori e professionisti IT possono usare questi servizi per creare, distribuire e gestire applicazioni in un'ampia gamma di strumenti e framework, attraverso una rete globale di data center. Il cloud di Azure consente alle aziende che affrontano le sfide associate al passaggio al digitale di determinare come ottimizzare le risorse e le operazioni, interagire con clienti e dipendenti e trasformare i prodotti offerti.

Nonostante tutti i vantaggi offerti dal cloud in termini di velocità e flessibilità, riduzione al minimo dei costi, prestazioni e affidabilità, tuttavia, Azure riconosce che molte organizzazioni dovranno eseguire data center locali ancora per un certo periodo. In risposta agli ostacoli all'adozione del cloud, Azure offre una strategia di cloud ibrido che collega i data center locali e il cloud pubblico di Azure, ad esempio usando risorse del cloud di Azure come Backup di Azure per proteggere le risorse locali oppure usando le funzionalità di analisi di Azure per ottenere informazioni dettagliate sui carichi di lavoro locali.

Nell'ambito della strategia di cloud ibrido, Azure offre sempre più soluzioni per eseguire la migrazione al cloud di app e carichi di lavoro locali. Con semplici procedure, è possibile valutare in modo completo le risorse locali per determinare come verranno eseguite nel cloud di Azure. Con una valutazione approfondita a disposizione, si può quindi eseguire in tutta sicurezza la migrazione delle risorse ad Azure. Quando saranno operative in Azure, le risorse potranno essere ottimizzate per mantenere e migliorare l'accesso, la flessibilità, la sicurezza e l'affidabilità.

## <a name="migration-patterns"></a>Modelli di migrazione

Le strategie per la migrazione al cloud rientrano in quattro grandi categorie: rehosting, refactoring, riprogettazione e ricostruzione. La strategia adottata dipende dai fattori chiave dello sviluppo aziendale e dagli obiettivi di migrazione prefissati. È possibile adottare più modelli. È ad esempio possibile scegliere di eseguire il rehosting di app semplici o che non hanno particolare rilevanza per l'azienda e di riprogettare invece app più complesse e business critical. Di seguito vengono esaminati questi modelli.

<!-- markdownlint-disable MD033 -->

**Modello** | **Definizione** | **Quando usarla**
--- | --- | ---
**Rehosting** | Spesso indicato come migrazione in modalità "lift-and-shift". Adottando questa strategia non è necessario apportare modifiche al codice ed è possibile eseguire rapidamente la migrazione ad Azure delle app esistenti. Ogni app viene migrata così com'è, in modo da sfruttare i vantaggi del cloud senza i rischi e i costi associati alle modifiche del codice. | Quando è necessario spostare rapidamente le app nel cloud.<br/><br/> Quando si vuole spostare un'app senza modificarla.<br/><br/> Quando le app sono progettate in modo da sfruttare la scalabilità dell'[infrastruttura Iaas di Azure](https://azure.microsoft.com/overview/what-is-iaas) dopo la migrazione.<br/><br/> Quando le app sono importanti per l'azienda, ma non è necessario apportare modifiche immediate alle loro funzionalità.
**Refactoring** | Noto anche come "riassemblaggio", il refactoring richiede modifiche minime delle app, in modo che possano connettersi alla [piattaforma Paas di Azure](https://azure.microsoft.com/overview/what-is-paas) e sfruttare le offerte del cloud.<br/><br/> È ad esempio possibile eseguire la migrazione delle app esistenti al Servizio app di Azure o al servizio Azure Kubernetes.<br/><br/> In alternativa, è possibile eseguire il refactoring di database relazionali e non relazionali in opzioni quali Istanza gestita di database SQL di Azure, Database di Azure per MySQL, Database di Azure per PostgreSQL e Azure Cosmos DB. | Se l'app può essere facilmente riassemblata in modo da funzionare in Azure.<br/><br/> Se si vogliono applicare le procedure DevOps innovative offerte da Azure o si sta valutando l'opportunità di investire in DevOps adottando una strategia basata su contenitori per carichi di lavoro.<br/><br/> Per il refactoring, è necessario considerare la portabilità della codebase esistente e le competenze di sviluppo disponibili.
**Riprogettazione** | La riprogettazione per la migrazione è incentrata sulla modifica e sull'estensione della codebase e delle funzionalità delle app al fine di ottimizzarne l'architettura per la scalabilità nel cloud.<br/><br/> Può ad esempio essere opportuno suddividere un'applicazione monolitica in un gruppo di microservizi che funzionano insieme e sono facilmente scalabili.<br/><br/> In alternativa, è possibile riprogettare database relazionali e non relazionali e trasformarli in soluzioni di database completamente gestite, ad esempio Istanza gestita di database SQL di Azure, Database di Azure per MySQL, Database di Azure per PostgreSQL e Azure Cosmos DB. | Quando si devono apportare revisioni significative alle app per incorporare nuove funzionalità o per migliorarne il funzionamento su una piattaforma cloud.<br/><br/> Quando si vogliono sfruttare gli investimenti esistenti per le applicazioni, rispettare i requisiti di scalabilità, applicare le procedure DevOps di Azure innovative e ridurre al minimo l'uso di macchine virtuali.
**Ricostruzione** | Questa strategia consente di compiere un passo in avanti ricostruendo un'app da zero con le tecnologie cloud di Azure.<br/><br/> È ad esempio possibile creare app greenfield con tecnologie [native del cloud](https://azure.com/cloudnative) come Funzioni di Azure, Azure per intelligenza artificiale, Istanza gestita di database SQL di Azure e Azure Cosmos DB. | Quando si vogliono sviluppare app rapidamente e le app esistenti hanno funzionalità e ciclo di vita limitati.<br/><br/> Quando si è pronti ad accelerare l'innovazione aziendale (adottando anche le procedure DevOps fornite da Azure), creare nuove applicazioni con tecnologie native del cloud e sfruttare i miglioramenti delle tecnologie di intelligenza artificiale, Blockchain e IoT.

<!-- markdownlint-enable MD033 -->

## <a name="migration-example-articles"></a>Articoli di esempio sulla migrazione

Negli articoli di questa sezione vengono forniti esempi di diversi scenari di migrazione comuni. Ciascuno di questi articoli include informazioni generali e scenari di distribuzione dettagliati che illustrano come configurare un'infrastruttura di migrazione e valutare l'idoneità delle risorse locali per la migrazione. Verranno aggiunti altri articoli in futuro in questa sezione.

![Progetti di migrazione/modernizzazione comuni](./media/migration-patterns.png)

*Categorie di progetti di migrazione/modernizzazione comuni.*

Di seguito sono riepilogati gli articoli della serie.

- Ogni scenario di migrazione è guidato da obiettivi aziendali leggermente diversi che determinano la strategia di migrazione.
- Ogni scenario di distribuzione presenta informazioni sui fattori chiave per lo sviluppo e gli obiettivi aziendali, propone un'architettura, illustra i passaggi per la migrazione, fornisce indicazioni per la pulizia e suggerisce i passaggi successivi da eseguire al termine della migrazione.

### <a name="assessment"></a>Valutazione

**Articolo** | **Dettagli**
--- | ---
[Valutare le risorse locali per la migrazione ad Azure](contoso-migration-assessment.md) | Questo articolo illustra come eseguire una valutazione di un'app locale in esecuzione in VMware. Nell'esempio un'organizzazione di esempio valuta le macchine virtuali dell'app con il servizio Azure Migrate e il database SQL Server dell'app con Data Migration Assistant.

### <a name="infrastructure"></a>Infrastruttura

**Articolo** | **Dettagli**
--- | ---
[Distribuire l'infrastruttura di Azure](contoso-migration-infrastructure.md) | Questo articolo illustra il modo in cui un'organizzazione può preparare la propria infrastruttura locale e l'infrastruttura di Azure per la migrazione. L'esempio di infrastruttura definito in questo articolo viene usato come riferimento negli altri esempi forniti in questa sezione.

### <a name="windows-server-workloads"></a>Carichi di lavoro di Windows Server

**Articolo** | **Dettagli**
--- | ---
[Effettuare il rehosting di un'app in macchine virtuali di Azure](contoso-migration-rehost-vm.md) | Questo articolo fornisce un esempio di migrazione di macchine virtuali di un'app locale a macchine virtuali di Azure con il servizio Site Recovery.
[Riprogettare un'app in contenitori di Azure e nel database SQL di Azure](contoso-migration-rearchitect-container-sql.md) | Questo articolo fornisce un esempio di migrazione di un'app e ridefinisce il livello di app Web come contenitore Windows in esecuzione in Azure Service Fabric e il database con il database SQL di Azure.

### <a name="linux-workloads"></a>Carichi di lavoro di Linux

**Articolo** | **Dettagli**
--- | ---
[Eseguire il rehosting di un'app Linux in macchine virtuali di Azure e in Database di Azure per MySQL](contoso-migration-rehost-linux-vm-mysql.md) | Questo articolo fornisce un esempio di migrazione di un'app ospitata in Linux a macchine virtuali di Azure con Site Recovery. Esegue la migrazione del database dell'app in Database di Azure per MySQL tramite MySQL Workbench.
[Eseguire il rehosting di un'app Linux in macchine virtuali di Azure](contoso-migration-rehost-linux-vm.md) | Questo esempio mostra come completare una migrazione in modalità "lift-and-shift" di un'app basata su Linux a macchine virtuali di Azure con il servizio Site Recovery.

### <a name="sql-server-workloads"></a>Carichi di lavoro di SQL Server

**Articolo** | **Dettagli**
--- | ---
[Eseguire il rehosting di un'app in una macchina virtuale di Azure e in Istanza gestita di database SQL](contoso-migration-rehost-vm-sql-managed-instance.md) | Questo articolo fornisce un esempio di migrazione in modalità "lift-and-shift" di un'app locale ad Azure. Questa operazione comporta la migrazione della macchina virtuale front-end dell'app con [Azure Site Recovery](/azure/site-recovery/site-recovery-overview) e del database dell'app a Istanza gestita di database SQL di Azure con [Servizio Migrazione del database di Azure](/azure/dms/dms-overview).
[Eseguire il rehosting di un'app in macchine virtuali di Azure e in un gruppo di disponibilità AlwaysOn di SQL Server](contoso-migration-rehost-vm-sql-ag.md) | Questo esempio illustra come eseguire la migrazione di un'app e dei dati usando macchine virtuali di SQL Server ospitate in Azure. Viene usato Site Recovery per la migrazione delle macchine virtuali dell'app e Servizio Migrazione del database di Azure per la migrazione del database dell'app a un cluster di SQL Server protetto da un gruppo di disponibilità AlwaysOn.

### <a name="aspnet--php--java-apps"></a>App ASP.NET/PHP/Java

**Articolo** | **Dettagli**
--- | ---
[Eseguire il refactoring di un'app in un'app Web di Azure e un database SQL di Azure](contoso-migration-refactor-web-app-sql.md) | Questo esempio illustra come eseguire la migrazione di un'app locale basata su Windows a un'app Web di Azure e del database dell'app a un'istanza di SQL Server di Azure con Data Migration Assistant.
[Eseguire il refactoring di un'app Linux in più aree con il Servizio app di Azure, Gestione traffico di Azure e Database di Azure per MySQL](contoso-migration-refactor-linux-app-service-mysql.md) | Questo esempio illustra come eseguire la migrazione di un'app locale basata su Linux a un'app Web di Azure in più aree di Azure con Gestione traffico di Azure, con l'integrazione con GitHub per il recapito continuo. Viene eseguita la migrazione del database dell'app a un'istanza di Database di Azure per MySQL.
[Ricompilare un'app in Azure](contoso-migration-rebuild.md) | Questo articolo fornisce un esempio di ricompilazione di un'app locale con una gamma di funzionalità e servizi gestiti di Azure, tra cui il Servizio app di Azure, il servizio Azure Kubernetes, Funzioni di Azure, Servizi cognitivi di Azure e Azure Cosmos DB.
[Eseguire il refactoring di Team Foundation Server in Azure DevOps Services](contoso-migration-tfs-vsts.md) | Questo articolo illustra una migrazione di esempio di una distribuzione di Team Foundation Server locale ad Azure DevOps Services in Azure.

### <a name="migration-scaling"></a>Ridimensionamento della migrazione

**Articolo** | **Dettagli**
--- | ---
[Passare a una migrazione completa ad Azure](contoso-migration-scale.md) | Questo articolo illustra in che modo un'organizzazione di esempio prepara il passaggio a una migrazione completa ad Azure.

### <a name="demo-apps"></a>App demo

Gli articoli di esempio forniti in questa sezione usano due app demo: SmartHotel360 e osTicket.

- **SmartHotel360:** questa app è stata sviluppata da Microsoft come app di test che è possibile usare con Azure. È disponibile per l'uso in modalità open source e può essere scaricata da [GitHub](https://github.com/Microsoft/SmartHotel360). È un'app ASP.NET connessa a un database di SQL Server. Negli scenari illustrati in questi articoli la versione corrente di questa app viene distribuita in due macchine virtuali VMware che eseguono Windows Server 2008 R2 e SQL Server 2008 R2. Le macchine virtuali dell'app sono ospitate in locale e gestite da un server vCenter.
- **osTicket:** un'app open source per la gestione di ticket di assistenza che viene eseguita su Linux. È possibile scaricarlo da [GitHub](https://github.com/osTicket/osTicket). Negli scenari illustrati in questi articoli la versione corrente di questa app viene distribuita in locale in due macchine virtuali VMware che eseguono Ubuntu 16.04 LTS, con Apache 2, PHP 7.0 e MySQL 5.7.
