---
title: Effettuare il refactoring di un'app Service Desk Linux in Servizio app di Azure e in Database di Azure per MySQL
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni su come Contoso effettua il refactoring dell'app di Linux locale eseguendo la migrazione nel Servizio app di Azure usando GitHub per il livello Web e il database SQL di Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/11/2018
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: e504d4032fc019af43ec7cb1e8513504196559a2
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71024205"
---
# <a name="refactor-a-linux-app-to-multiple-regions-using-azure-app-service-traffic-manager-and-azure-database-for-mysql"></a>Effettuare il refactoring di un'app Linux in più aree con Servizio app di Azure, Gestione traffico e Database di Azure per MySQL

Questo articolo illustra come la società fittizia Contoso effettui il refactoring di un'app Apache/MySQL PHP (LAMP) a due livelli eseguendone la migrazione dall'ambiente locale ad Azure usando Servizio app di Azure con l'integrazione GitHub e Database di Azure per MySQL.

osTicket, l'app Service Desk usata in questo esempio, viene fornita come open source. È possibile scaricarla da [GitHub](https://github.com/osTicket/osTicket) per usarla a scopi di test personalizzati.

## <a name="business-drivers"></a>Driver di business

Il team di responsabili IT ha lavorato a stretto contatto con i partner di business per comprenderne le effettive esigenze:

- **Stare al passo con la crescita aziendale:** Contoso è in crescita e si sta espandendo in nuovi mercati. Sono pertanto necessari addetti al servizio clienti aggiuntivi.
- **Scalabilità.** la soluzione deve essere compilata in modo che Contoso possa aggiungere altri addetti al servizio clienti man mano che l'azienda aumenta di dimensioni.
- **Migliorare la resilienza:**  in precedenza, i problemi riguardanti il sistema interessavano solo gli utenti interni. Con il nuovo modello di business, saranno interessati anche gli utenti esterni e per Contoso è necessario che l'app sia configurata e operativa in qualsiasi momento.

## <a name="migration-goals"></a>Obiettivi della migrazione

Il team cloud di Contoso ha stabilito gli obiettivi di questa migrazione, per determinare il metodo di migrazione più consono:

- L'applicazione deve scalare superando la capacità e le prestazioni locali correnti. Contoso sta spostando l'applicazione per sfruttare i vantaggi della scalabilità su richiesta di Azure.
- Contoso vuole spostare la base di codice dell'app in una pipeline di recapito continuo. Poiché viene eseguito il push delle modifiche dell'app a GitHub, Contoso vuole distribuire tali modifiche senza interventi da parte del personale operativo.
- L'applicazione deve essere resiliente con capacità di crescita e failover. Contoso vuole distribuire l'app in due diverse aree di Azure e configurarla per il ridimensionamento automatico.
- Contoso desidera ridurre al minimo le attività di amministrazione del database dopo che l'app è stata spostata nel cloud.

## <a name="solution-design"></a>Progettazione della soluzione

Dopo aver definito i propri obiettivi e requisiti, Contoso progetta ed esamina una soluzione di distribuzione, identificando il processo di migrazione, tra cui i servizi di Azure da usare per la migrazione.

## <a name="current-architecture"></a>Architettura corrente

- L'app è su più livelli tra due macchine virtuali (OSTICKETWEB e OSTICKETMYSQL).
- Le macchine virtuali si trovano nell'host VMware ESXi **contosohost1.contoso.com** (versione 6.5).
- L'ambiente VMware viene gestito dal server vCenter 6.5 (**vcenter.contoso.com**) in esecuzione in una macchina virtuale.
- Contoso ha un data center locale (contoso-datacenter) con un controller di dominio locale (**contosodc1**).

![Architettura corrente](./media/contoso-migration-refactor-linux-app-service-mysql/current-architecture.png)

## <a name="proposed-architecture"></a>Architettura proposta

Ecco l’architettura proposta:

- Verrà eseguita la migrazione dell'app di livello Web su OSTICKETWEB tramite la creazione di un Servizio app di Azure in due aree di Azure. Il Servizio app di Azure per Linux viene implementato usando il contenitore Docker di PHP 7.0.
- Il codice dell'app verrà spostato in GitHub e l'app Web di Servizio app di Azure verrà configurata per il recapito continuo con GitHub.
- I server di app di Azure verranno distribuiti nelle aree primaria (Stati Uniti orientali 2) e secondaria (Stati Uniti centrali).
- Per le due app Web in entrambe le aree verrà configurato il servizio Gestione traffico.
- Gestione traffico verrà configurato in modalità di priorità per forzare il traffico attraverso l'area Stati Uniti orientali 2.
- Se il server di app di Azure negli Stati Uniti orientali 2 è offline, gli utenti possono accedere all'app su cui è stato effettuato il failover negli Stati Uniti centrali.
- Verrà effettuata la migrazione del database dell'app nel servizio Database di Azure per MySQL usando gli strumenti MySQL Workbench. Verrà eseguito localmente il backup del database locale, che verrà ripristinato direttamente in Database di Azure per MySQL.
- Il database risiederà nell'area primaria Stati Uniti orientali 2, nella subnet di database (PROD-DB-EUS2) della rete di produzione (VNET-PROD-EUS2):
- Poiché l'azienda intende eseguire la migrazione di un carico di lavoro di produzione, le risorse Azure per l'app risiederanno nel gruppo di risorse di produzione **ContosoRG**.
- La risorsa di Gestione traffico verrà distribuita nel gruppo di risorse di infrastruttura di Contoso **ContosoInfraRG**.
- Le macchine virtuali locali nel data center Contoso verranno rimosse al termine della migrazione.

![Architettura dello scenario](./media/contoso-migration-refactor-linux-app-service-mysql/proposed-architecture.png)

## <a name="migration-process"></a>Processo di migrazione

In Contoso il processo di migrazione verrà completato come indicato di seguito:

1. In una prima fase gli amministratori Contoso configurano l'infrastruttura di Azure, effettuando tra l'altro il provisioning di Servizio app di Azure, la configurazione di Gestione traffico e il provisioning di un'istanza di Database di Azure per MySQL.
2. Dopo la preparazione di Azure, viene effettuata la migrazione del database usando MySQL Workbench.
3. Una volta che il database è in esecuzione in Azure, configurano un repository di GitHub privato per Servizio app di Azure con recapito continuo e vi caricano l'app osTicket.
4. Nel portale di Azure, vengono caricate le app da GitHub nel contenitore Docker che sta eseguendo il Servizio app di Azure.
5. Vengono modificate le impostazioni DNS e viene configurata la scalabilità automatica per l'app.

![Processo di migrazione](./media/contoso-migration-refactor-linux-app-service-mysql/migration-process.png)

### <a name="azure-services"></a>Servizi di Azure

**Servizio** | **Descrizione** | **Costii**
--- | --- | ---
[Servizio app di Azure](https://azure.microsoft.com/services/app-service) | Il servizio viene eseguito e ridimensiona le applicazioni mediante il servizio PaaS di Azure per i siti Web. | I prezzi sono basati sulle dimensioni delle istanze e sulle funzionalità necessarie. [Altre informazioni](https://azure.microsoft.com/pricing/details/app-service/windows)
[Gestione traffico](https://azure.microsoft.com/services/traffic-manager) | Un bilanciamento del carico che usa il DNS per indirizzare gli utenti ad Azure, o siti Web e servizi esterni. | I prezzi si basano sul numero di query DNS ricevute e sul numero di endpoint monitorati. | [Altre informazioni](https://azure.microsoft.com/pricing/details/traffic-manager)
[Database di Azure per MySQL](https://docs.microsoft.com/azure/mysql) | Il database si basa sul motore del server MySQL open source. Offre un database MySQL come servizio completamente gestito, di livello aziendale e supportato dalla community per lo sviluppo e la distribuzione di app. | I prezzi si basano sui requisiti di calcolo, archiviazione e backup. [Altre informazioni](https://azure.microsoft.com/pricing/details/mysql)

## <a name="prerequisites"></a>Prerequisiti

Ecco i requisiti che Contoso dovrà soddisfare per questo scenario.

<!-- markdownlint-disable MD033 -->

**Requisiti** | **Dettagli**
--- | ---
**Sottoscrizione di Azure** | Contoso ha creato le sottoscrizioni in un articolo precedente di questa serie. Se non si ha una sottoscrizione di Azure, creare un [account gratuito](https://azure.microsoft.com/pricing/free-trial).<br/><br/> Se si crea un account gratuito, si è l'amministratore della sottoscrizione e si possono eseguire tutte le azioni.<br/><br/> Se si usa una sottoscrizione esistente e non si ha il ruolo di amministratore, è necessario rivolgersi all'amministratore per l'assegnazione delle autorizzazioni di proprietario o collaboratore.
**Infrastruttura di Azure** | Contoso configura la propria infrastruttura di Azure come descritto in [Azure infrastructure for migration](./contoso-migration-infrastructure.md) (Infrastruttura di Azure per la migrazione).

<!-- markdownlint-enable MD033 -->

## <a name="scenario-steps"></a>Passaggi dello scenario

Ecco come Contoso eseguirà la migrazione:

> [!div class="checklist"]
>
> - **Passaggio 1: Effettuare il provisioning di Servizio app di Azure.** Gli amministratori Contoso effettuano il provisioning delle app Web nelle aree primaria e secondaria.
> - **Passaggio 2: Configurare Gestione traffico.** Configurano Gestione traffico per le app Web per il routing e il bilanciamento del carico del traffico.
> - **Passaggio 3: Effettuare il provisioning di MySQL.** In Azure effettuano il provisioning di un'istanza di Database di Azure per MySQL.
> - **Passaggio 4: Eseguire la migrazione del database.** Dopo la preparazione di Azure, viene effettuata la migrazione del database usando MySQL Workbench.
> - **Passaggio 5: Configurare GitHub.** Viene configurato un repository di GitHub locale per i siti Web/codice dell'app.
> - **Passaggio 6: Distribuire le app Web.** Le app Web vengono distribuite da GitHub.

## <a name="step-1-provision-azure-app-service"></a>Passaggio 1: Effettuare il provisioning di Servizio app di Azure

Gli amministratori Contoso effettuano il provisioning di due app Web (una in ogni area) con Servizio app di Azure.

1. Creano una risorsa app Web nell'area primaria Stati Uniti orientali 2 (**osticket eus2**) da Azure Marketplace.
2. La risorsa viene inserita nel gruppo di risorse di produzione **ContosoRG**.

    ![App Azure](./media/contoso-migration-refactor-linux-app-service-mysql/azure-app1.png)

3. Viene creato un nuovo piano di servizio app nell'area primaria (**APP-Vice-EUS2**), usando le dimensioni standard.

     ![App Azure](./media/contoso-migration-refactor-linux-app-service-mysql/azure-app2.png)

4. Viene selezionato un sistema operativo Linux con stack di runtime PHP 7.0, un contenitore Docker.

    ![App Azure](./media/contoso-migration-refactor-linux-app-service-mysql/azure-app3.png)

5. Gli amministratori creano una seconda app Web (**osticket cus**) e il piano di Servizio app di Azure per l'area Stati Uniti centrali.

    ![App Azure](./media/contoso-migration-refactor-linux-app-service-mysql/azure-app4.png)

**Ulteriore assistenza?**

- Informazioni sulle [app Web di Servizio app di Azure](https://docs.microsoft.com/azure/app-service/overview).
- Informazioni sul [Servizio app di Azure in Linux](https://docs.microsoft.com/azure/app-service/containers/app-service-linux-intro).

## <a name="step-2-set-up-traffic-manager"></a>Passaggio 2: configurare Gestione traffico

Gli amministratori Contoso configurano Gestione traffico per indirizzare le richieste Web in ingresso alle app Web in esecuzione nel livello Web osTicket.

1. Viene creata una risorsa Gestione traffico (**osticket.trafficmanager.net**) da Microsoft Azure Marketplace. Viene usato il routing prioritario, in modo che l'area Stati Uniti orientali 2 sia il sito primario. La risorsa viene posizionata nel gruppo di risorse dell'infrastruttura (**ContosoInfraRG**). Si noti che il servizio Gestione traffico è globale e non è associato a una posizione specifica.

    ![Gestione traffico](./media/contoso-migration-refactor-linux-app-service-mysql/traffic-manager1.png)

2. A questo punto, viene configurato Gestione traffico con gli endpoint. Gli amministratori aggiungono l'app Web di Stati Uniti orientali 2 come sito primario (**osticket eus2**) e l'app di Stati Uniti centrali come sito secondario (**osticket cus**).

    ![Gestione traffico](./media/contoso-migration-refactor-linux-app-service-mysql/traffic-manager2.png)

3. Dopo aver aggiunto gli endpoint, è possibile monitorarli.

    ![Gestione traffico](./media/contoso-migration-refactor-linux-app-service-mysql/traffic-manager3.png)

**Ulteriore assistenza?**

- Informazioni su [Gestione traffico](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).
- Informazioni su come [indirizzare il traffico a un endpoint prioritario](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-configure-priority-routing-method).

## <a name="step-3-provision-azure-database-for-mysql"></a>Passaggio 3: eseguire il provisioning del database di Azure per MySQL

In Contoso gli amministratori eseguono il provisioning di un'istanza del database MySQL nell'area primaria Stati Uniti orientali 2.

1. Nel portale di Azure si crea una risorsa per il database di Azure per MySQL.

    ![MySQL](./media/contoso-migration-refactor-linux-app-service-mysql/mysql-1.png)

2. Si aggiunge il nome **contosoosticket** per il database di Azure. Si aggiunge il database al gruppo di risorse di produzione **ContosoRG** e se ne specificano le credenziali.
3. Il database MySQL locale è la versione 5.7, pertanto si seleziona questa versione per compatibilità. Si usano le dimensioni predefinite, che corrispondono ai relativi requisiti di database.

     ![MySQL](./media/contoso-migration-refactor-linux-app-service-mysql/mysql-2.png)

4. Per **Opzioni di ridondanza per il backup**, selezionano l'uso **Con ridondanza geografica**. Questa opzione consente di ripristinare il database nell'area secondaria Stati Uniti centrali in caso di interruzione. Si può configurare questa opzione solo quando si esegue il provisioning del database.

    ![Ridondanza](./media/contoso-migration-refactor-linux-app-service-mysql/db-redundancy.png)

5. Viene impostata la sicurezza della connessione. Nel database > **Sicurezza della connessione**, vengono impostate le regole del Firewall per consentire al database di accedere ai servizi di Azure.

6. Le regole aggiungono l'indirizzo IP del client per workstation locale agli indirizzi IP iniziale e finale. In questo modo le app Web hanno accesso al database MySQL, insieme al client del database che sta eseguendo la migrazione.

    ![MySQL](./media/contoso-migration-refactor-linux-app-service-mysql/mysql-3.png)

## <a name="step-4-migrate-the-database"></a>Passaggio 4: Eseguire la migrazione del database

Gli amministratori di Contoso eseguiranno la migrazione del database tramite backup e ripristino, con gli strumenti di MySQL. Si installa MySQL Workbench, si esegue il backup del database da OSTICKETMYSQL e quindi lo si ripristina in Database di Azure per il server MySQL.

### <a name="install-mysql-workbench"></a>Installare MySQL Workbench

1. Verificano i [prerequisiti e scaricano MySQL Workbench](https://dev.mysql.com/downloads/workbench/?utm_source=tuicool).
2. Si installa MySQL Workbench per Windows in conformità con le [istruzioni di installazione](https://dev.mysql.com/doc/workbench/en/wb-installing.html). Il computer su cui viene installato deve essere accessibile alla VM OSTICKETMYSQL e ad Azure tramite Internet.
3. In MySQL Workbench si crea una connessione MySQL a OSTICKETMYSQL.

    ![MySQL Workbench](./media/contoso-migration-refactor-linux-app-service-mysql/workbench1.png)

4. Si esporta il database come **osticket**, in un file autonomo locale.

    ![MySQL Workbench](./media/contoso-migration-refactor-linux-app-service-mysql/workbench2.png)

5. Dopo avere eseguito il backup del database localmente, si crea una connessione all'istanza di Database di Azure per MySQL.

    ![MySQL Workbench](./media/contoso-migration-refactor-linux-app-service-mysql/workbench3.png)

6. A questo punto, possono importare (ripristinare) il database nell'istanza di Database di Azure per MySQL dal file autonomo. Viene creato un nuovo schema (osticket) per l'istanza.

    ![MySQL Workbench](./media/contoso-migration-refactor-linux-app-service-mysql/workbench4.png)

7. Dopo il ripristino dei dati, è possibile eseguire query usando Workbench, visualizzandoli nel portale di Azure.

    ![MySQL Workbench](./media/contoso-migration-refactor-linux-app-service-mysql/workbench5.png)

    ![MySQL Workbench](./media/contoso-migration-refactor-linux-app-service-mysql/workbench6.png)

8. Infine, devono aggiornare le informazioni del database nelle app Web. Nell'istanza di MySQL, si apre**Stringhe di connessione**.

     ![MySQL Workbench](./media/contoso-migration-refactor-linux-app-service-mysql/workbench7.png)

9. Nell'elenco delle stringhe individuano le impostazioni dell'app Web e scelgono di copiarle.

    ![MySQL Workbench](./media/contoso-migration-refactor-linux-app-service-mysql/workbench8.png)

10. Si apre una finestra Blocco note e si incolla la stringa in un nuovo file, e lo si aggiorna in modo che corrisponda al database osticket, all'istanza di MySQL e alle impostazioni delle credenziali.

     ![MySQL Workbench](./media/contoso-migration-refactor-linux-app-service-mysql/workbench9.png)

11. Possono verificare il nome del server e accedere da **Panoramica** nell'istanza di MySQL nel portale di Azure.

    ![MySQL Workbench](./media/contoso-migration-refactor-linux-app-service-mysql/workbench10.png)

## <a name="step-5-set-up-github"></a>Passaggio 5: configurare GitHub

Gli amministratori Contoso creano un nuovo repository di GitHub privato e configurano una connessione al database osTicket in Database di Azure per MySQL. Caricano quindi l'app Web in Servizio app di Azure.

1. Si passa al repository di GitHub pubblico del software OsTicket ed si esegue il fork all'account GitHub di Contoso.

    ![GitHub](./media/contoso-migration-refactor-linux-app-service-mysql/github1.png)

2. Dopo aver eseguito il fork, ci si sposta alla cartella di **inclusione** e si trova il file **ost-config**.

    ![GitHub](./media/contoso-migration-refactor-linux-app-service-mysql/github2.png)

3. Il file verrà aperto nel browser e verrà modificato.

    ![GitHub](./media/contoso-migration-refactor-linux-app-service-mysql/github3.png)

4. Nell'editor, vengono aggiornati i dettagli del database, in particolare **DBHOST** e **DBUSER**.

    ![GitHub](./media/contoso-migration-refactor-linux-app-service-mysql/github4.png)

5. Quindi viene eseguito il commit delle modifiche.

    ![GitHub](./media/contoso-migration-refactor-linux-app-service-mysql/github5.png)

6. Per ogni app Web (**osticket eus2** e **osticket cus**), vengono modificate le **Impostazioni dell'applicazione** nel portale di Azure.

    ![GitHub](./media/contoso-migration-refactor-linux-app-service-mysql/github6.png)

7. Viene immessa la stringa di connessione con il nome **osticket**e la stringa viene copiata dal blocco note nell'**area valore**. Infine, viene selezionato **MySQL** dall'elenco a discesa accanto alla stringa, quindi si salvano le impostazioni.

    ![GitHub](./media/contoso-migration-refactor-linux-app-service-mysql/github7.png)

## <a name="step-6-configure-the-web-apps"></a>Passaggio 6: Configurare le app Web

Come passaggio finale del processo di migrazione, gli amministratori Contoso configurano le app Web con siti Web osTicket.

1. Nell'app Web primaria (**osticket eus2**) si apre **Opzione di distribuzione** e si imposta l'origine per **GitHub**.

    ![Configurare un'app](./media/contoso-migration-refactor-linux-app-service-mysql/configure-app1.png)

2. Vengono scelte le opzioni di distribuzione.

    ![Configurare un'app](./media/contoso-migration-refactor-linux-app-service-mysql/configure-app2.png)

3. Dopo aver impostato le opzioni per la configurazione, questa viene visualizzata come in sospeso nel portale di Azure.

    ![Configurare un'app](./media/contoso-migration-refactor-linux-app-service-mysql/configure-app3.png)

4. In seguito all'aggiornamento della configurazione e al caricamento dell'app Web osTicket da GitHub per il contenitore Docket su cui è in esecuzione il Servizio app di Azure, il sito viene visualizzato come attivo.

    ![Configurare un'app](./media/contoso-migration-refactor-linux-app-service-mysql/configure-app4.png)

5. Vengono ripetuti quindi i passaggi precedenti per l'app Web secondaria (**osticket cus**).
6. Dopo aver configurato il sito, questo è accessibile tramite il profilo Gestione traffico. Il nome DNS è il nuovo percorso dell'app osTicket. [Altre informazioni](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-custom-domain#map-a-cname-record)

    ![Configurare un'app](./media/contoso-migration-refactor-linux-app-service-mysql/configure-app5.png)

7. Per Contoso è necessario un nome DNS facile da ricordare. Viene creato un record alias (CNAME) **osticket.contoso.com** che punta al nome di Gestione traffico, nel DNS nei controller di dominio.

    ![Configurare un'app](./media/contoso-migration-refactor-linux-app-service-mysql/configure-app6.png)

8. Vengono configurate entrambe le app Web **osticket eus2** e **osticket cus** per consentire i nomi host personalizzati.

    ![Configurare un'app](./media/contoso-migration-refactor-linux-app-service-mysql/configure-app7.png)

### <a name="set-up-autoscaling"></a>Configurare la scalabilità automatica

Infine, viene configurata la scalabilità automatica per l'app. Ciò garantisce che, quando gli addetti usano l'app, le istanze di app aumentano e diminuiscono in base alle esigenze aziendali.

1. Nel Servizio app **APP-SRV-EUS2**, viene aperta **Unità di scala**.
2. Viene configurata una nuova impostazione di scalabilità automatica con una singola regola che aumenta di uno il numero di istanze quando la percentuale di CPU per l'istanza corrente è superiore al 70% per 10 minuti.

    ![Autoscale](./media/contoso-migration-refactor-linux-app-service-mysql/autoscale1.png)

3. Si configura la stessa impostazione su **APP-SRV-CUS** per assicurarsi che lo stesso comportamento si applica se viene eseguito il failover dell'app nell'area secondaria. L'unica differenza è che l'istanza predefinita viene impostata su 1, poiché è solo per il failover.

   ![Autoscale](./media/contoso-migration-refactor-linux-app-service-mysql/autoscale2.png)

## <a name="clean-up-after-migration"></a>Eseguire la pulizia dopo la migrazione

Al termine della migrazione, l'app osTicket viene sottoposta a refactoring per l'esecuzione in un'app Web di Servizio app di Azure con recapito continuo tramite un repository di GitHub privato. L'app è in esecuzione in due aree per aumentare la resilienza. Dopo la migrazione alla piattaforma PaaS, il database osTicket è in esecuzione nel database di Azure per MySQL.

Per la pulizia, Contoso deve eseguire le operazioni seguenti:

- Rimuovere le macchine virtuali VMware dall'inventario vCenter.
- Rimuovere le macchine virtuali in locale dai processi di backup locali.
- Aggiornare la documentazione interna in modo da mostrare i nuovi percorsi e gli indirizzi IP.
- Esaminare le risorse che interagiscono con le macchine virtuali locali e aggiornare eventuali impostazioni o documenti pertinenti in modo che riflettano la nuova configurazione.
- Riconfigurare il monitoraggio in modo da puntare all'URL osticket trafficmanager.net, per rilevare che l'app sia attiva e in esecuzione.

## <a name="review-the-deployment"></a>Esaminare la distribuzione

Con l'app in esecuzione, occorre rendere pienamente operativa e sicura la nuova infrastruttura.

### <a name="security"></a>Security

Il team di sicurezza di Contoso ha esaminato le app per determinare eventuali problemi di sicurezza. Ha individuato che la comunicazione tra l'app osTicket e l'istanza del database MySQL non è configurata per SSL. Sarà necessario eseguire questa operazione per proteggere il traffico del database. [Altre informazioni](https://docs.microsoft.com/azure/mysql/howto-configure-ssl)

### <a name="backups"></a>Backup

- Le app Web osTicket non contengono dati relativi allo stato e quindi non è necessario eseguire il backup.
- Non è necessario configurare il backup per il database. Database di Azure per MySQL crea automaticamente i backup del server e gli archivi. In Contoso è stato scelto di usare la ridondanza geografica per il database, in modo che sia resiliente e pronto per la produzione. I backup possono essere usati per ripristinare il server a un momento specifico. [Altre informazioni](https://docs.microsoft.com/azure/mysql/concepts-backup)

### <a name="licensing-and-cost-optimization"></a>Licenze e ottimizzazione dei costi

- Non vi sono problemi di gestione delle licenze per la distribuzione di PaaS.
- Contoso abiliterà Gestione costi, concesso in licenza da Cloudyn, una affiliata Microsoft. Si tratta di una soluzione di gestione dei costi multi-cloud che consente di usare e gestire Azure e altre risorse cloud. [Altre informazioni](https://docs.microsoft.com/azure/cost-management/overview) sulla Gestione costi di Azure.
