---
title: eseguire il rehosting di un'app Linux locale in macchine virtuali di Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni su come Contoso esegue il rehosting di un'app Linux locale eseguendone la migrazione a macchine virtuali di Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
services: site-recovery
ms.openlocfilehash: 8b925564b3186e153cdd9a8139499a83a1fd96ff
ms.sourcegitcommit: 57390e3a6f7cd7a507ddd1906e866455fa998d84
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2019
ms.locfileid: "73239418"
---
# <a name="rehost-an-on-premises-linux-app-to-azure-vms"></a>eseguire il rehosting di un'app Linux locale in macchine virtuali di Azure

Questo articolo illustra come la società fittizia Contoso esegue il rehosting di un'app LAMP (Apache MySQL PHP basata su Linux) a due livelli usando macchine virtuali IaaS di Azure.

osTicket, l'app Service Desk usata in questo esempio, viene fornita come open source. È possibile scaricarla da [GitHub](https://github.com/osTicket/osTicket) per usarla a scopi di test personalizzati.

## <a name="business-drivers"></a>Fattori chiave per lo sviluppo aziendale

Il team di leadership IT collabora attivamente con i partner commerciali per capire gli obiettivi da raggiungere con questa migrazione:

- **Stare al passo con la crescita del business.** Contoso è in espansione e di conseguenza l'infrastruttura e i sistemi locali iniziano a sentirne la pressione.
- **Limitare i rischi.** l'app Service Desk è fondamentale per il business di Contoso. L'obiettivo è spostare l'app in Azure senza correre alcun rischio.
- **Procedere all'estensione.** Contoso non prevede di sostituire subito l'app. Vuole semplicemente verificare che l'app sia stabile.

## <a name="migration-goals"></a>Obiettivi della migrazione

Il team cloud di Contoso ha stabilito gli obiettivi di questa migrazione, per determinare il metodo di migrazione più consono:

- Dopo la migrazione, l'app in Azure dovrà avere le stesse caratteristiche prestazionali di cui dispone attualmente nell'ambiente VMware locale. L'app manterrà la stessa importanza critica nel cloud come la corrispondente versione in locale.
- Contoso non vuole investire in questa app. L'app è importante per l'azienda, ma Contoso vuole semplicemente eseguirne la migrazione sicura al cloud nella sua forma attuale.
- Contoso non intende modificare il modello operativo dell'app. Vuole interagire con l'app nel cloud esattamente come avviene ora.
- Contoso non intende modificare le funzionalità dell'app. Cambierà solo la posizione.
- Dopo aver completato un paio di migrazioni di app di Windows, Contoso desidera scoprire come usare un'infrastruttura basata su Linux in Azure.

## <a name="solution-design"></a>Progettazione della soluzione

Dopo aver definito i propri obiettivi e requisiti, Contoso progetta ed esamina una soluzione di distribuzione, identificando il processo di migrazione, tra cui i servizi di Azure da usare per la migrazione.

### <a name="current-app"></a>App attuale

- L'app OSTicket è suddivisa in livelli tra due macchine virtuali (**OSTICKETWEB** e **OSTICKETMYSQL**).
- Le macchine virtuali si trovano nell'host VMware ESXi **contosohost1.contoso.com** (versione 6.5).
- L'ambiente VMware è gestito da vCenter Server 6.5 (**vcenter.contoso.com**) in esecuzione in una VM.
- Contoso ha un data center locale (**contoso-datacenter**) con un controller di dominio locale (**contosodc1**).

### <a name="proposed-architecture"></a>Architettura proposta

- Poiché l'app costituisce un carico di lavoro di produzione, le macchine virtuali in Azure risiederanno nel gruppo di risorse di produzione **ContosoRG**.
- Le risorse verranno migrate nell'area primaria (Stati Uniti orientali 2) e collegate alla rete di produzione (VNET-PROD-EUS2):
  - La macchina virtuale Web si troverà nella subnet front-end (PROD-FE-EUS2).
  - La macchina virtuale del database si troverà nella subnet del database (PROD-DB-EUS2).
- Le autorizzazioni delle VM locali nel data center Contoso verranno rimosse al termine della migrazione.

![Architettura dello scenario](./media/contoso-migration-rehost-linux-vm/architecture.png)

### <a name="solution-review"></a>Revisione della soluzione

Contoso valuta la progettazione proposta elaborando un elenco di vantaggi e svantaggi.

<!-- markdownlint-disable MD033 -->

**Considerazioni** | **Dettagli**
--- | ---
**Vantaggi** | Entrambe le macchine virtuali dell'app verranno spostate in Azure senza modifiche, semplificando così la migrazione.<br/><br/> Poiché Contoso usa un approccio Lift-and-Shift per entrambe le VM dell'app, non è necessario alcun strumento di configurazione o migrazione speciale per il database dell'app.<br/><br/> Contoso manterrà il controllo completo delle macchine virtuali dell'app in Azure. <br/><br/> Le macchine virtuali dell'app eseguono Ubuntu 16.04-TLS, una distribuzione Linux approvata. [Altre informazioni](https://docs.microsoft.com/azure/virtual-machines/linux/endorsed-distros).
**Svantaggi** | I livelli Web e dati dell'app rimarranno come singolo punto di failover. <br/><br/> Contoso dovrà continuare a supportare l'app come macchine virtuali di Azure anziché passare a un servizio gestito come Servizio app di Azure e Database di Azure per MySQL.<br/><br/> Contoso è consapevole del fatto che, grazie alla migrazione di una macchina virtuale in modalità Lift-and-Shift, gli utenti non sfruttano appieno le funzionalità offerte da [database di Azure per MySQL](https://docs.microsoft.com/azure/mysql/overview) (disponibilità elevata predefinita, prestazioni prevedibili, scalabilità semplice, automatica backup e sicurezza incorporata).

<!-- markdownlint-enable MD033 -->

### <a name="migration-process"></a>Processo di migrazione

Contoso eseguirà la migrazione nel modo seguente:

- In primo luogo, Contoso prepara e configura i componenti di Azure per Migrazione server di Azure Migrate e predispone l'infrastruttura VMware locale.
- L'[infrastruttura di Azure](./contoso-migration-infrastructure.md) è già presente, quindi Contoso deve semplicemente aggiungere e configurare la replica delle macchine virtuali tramite lo strumento Migrazione server di Azure Migrate.
- Al termine delle attività di preparazione, Contoso può iniziare a replicare le macchine virtuali.
- Non appena la replica è abilitata e operativa, Contoso esegue la migrazione della macchina eseguendone il failover in Azure.

![Processo di migrazione](./media/contoso-migration-rehost-linux-vm/migration-process-az-migrate.png)

### <a name="azure-services"></a>Servizi di Azure

**Servizio** | **Descrizione** | **Costii**
--- | --- | ---
[Migrazione server di Azure Migrate](https://docs.microsoft.com/azure/migrate/contoso-migration-rehost-linux-vm) | Il servizio orchestra e gestisce la migrazione delle app e dei carichi di lavoro locali e delle istanze di macchine virtuali AWS/GCP. | Durante la replica in Azure vengono addebitati costi relativi all'archiviazione di Azure. In caso di failover vengono create macchine virtuali di Azure, le quali sono soggette a costi. [Altre informazioni](https://azure.microsoft.com/pricing/details/azure-migrate) su addebiti e prezzi.

## <a name="prerequisites"></a>Prerequisiti

Ecco i requisiti che Contoso dovrà soddisfare per questo scenario.

<!-- markdownlint-disable MD033 -->

**Requisiti** | **Dettagli**
--- | ---
**Sottoscrizione di Azure** | Contoso ha creato le sottoscrizioni in un articolo precedente di questa serie. Se non si ha una sottoscrizione di Azure, creare un [account gratuito](https://azure.microsoft.com/pricing/free-trial).<br/><br/> Se si crea un account gratuito, si è l'amministratore della sottoscrizione e si possono eseguire tutte le azioni.<br/><br/> Se si usa una sottoscrizione esistente e non si ha il ruolo di amministratore, è necessario rivolgersi all'amministratore per l'assegnazione delle autorizzazioni di proprietario o collaboratore.<br/><br/> Se sono necessarie autorizzazioni più granulari, vedere [questo articolo](https://docs.microsoft.com/azure/site-recovery/site-recovery-role-based-linked-access-control).
**Infrastruttura di Azure** |  [Informazioni](./contoso-migration-infrastructure.md) sul modo in cui Contoso configura un'infrastruttura di Azure.<br/><br/> Altre informazioni sui [prerequisiti](https://docs.microsoft.com/azure/migrate/contoso-migration-rehost-linux-vm#prerequisites) specifici per Migrazione server di Azure Migrate.
**Server locali** | Il server vCenter locale deve eseguire la versione 5.5, 6.0 o 6.5<br/><br/> Host ESXi che esegue la versione 5.5, 6.0 o 6.5.<br/><br/> Una o più macchine virtuali VMware in esecuzione nell'host ESXi.
**VM locali** | [Esaminare i computer Linux](https://docs.microsoft.com/azure/virtual-machines/linux/endorsed-distros) approvati per l'esecuzione in Azure.

<!-- markdownlint-enable MD033 -->

## <a name="scenario-steps"></a>Passaggi dello scenario

Ecco come Contoso eseguirà la migrazione:

> [!div class="checklist"]
>
> - **Passaggio 1: preparare Azure per la migrazione di Azure Migrate server.** Contoso aggiunge lo strumento Migrazione server al progetto di Azure Migrate.
> - **Passaggio 2: preparare VMware locale per la migrazione di Azure Migrate server.** Contoso prepara gli account per l'individuazione delle macchine virtuali e si prepara alla connessione alle macchine virtuali di Azure dopo il failover.
> - **Passaggio 3: replicare le macchine virtuali.** viene configurata e avviata la replica delle VM in Archiviazione di Azure.
> - **Passaggio 4: eseguire la migrazione delle macchine virtuali con Azure Migrate migrazione del server.** vengono effettuati un failover di test per verificare che tutto funzioni come previsto e un failover completo per eseguire la migrazione delle macchine virtuali ad Azure.

## <a name="step-1-prepare-azure-for-the-azure-migrate-server-migration-tool"></a>Passaggio 1: preparare Azure per lo strumento di migrazione di Azure Migrate server

Ecco i componenti di Azure necessari a Contoso per la migrazione delle VM ad Azure:

- Una rete virtuale in cui verranno collocate le VM di Azure al momento della creazione, durante il failover.
- Lo strumento Migrazione server di Azure Migrate di cui è stato effettuato il provisioning.

Per configurare questi elementi, Contoso segue questa procedura:

1. **Configurare una rete:** Contoso ha già configurato una rete che può essere per la migrazione del server Azure Migrate durante [la distribuzione dell'infrastruttura di Azure](./contoso-migration-infrastructure.md)

    - SmartHotel360 è un'app di produzione e le VM verranno migrate alla rete di produzione di Azure (VNET-PROD-EUS2) nell'area primaria degli Stati Uniti orientali 2.
    - Entrambe le VM verranno inserite nel gruppo di risorse ContosoRG, usato per le risorse di produzione.
    - La macchina virtuale front-end dell'app (WEBVM) verrà migrata alla subnet front-end (PROD-FE-EUS2) nella rete di produzione.
    - La VM del database dell'app (SQLVM) verrà migrata alla subnet del database (PROD-DB-EUS2) nella rete di produzione.

2. Eseguire **il provisioning dello strumento di migrazione Azure migrate server:** Con l'account di rete e di archiviazione sul posto, Contoso crea ora un insieme di credenziali di servizi di ripristino (ContosoMigrationVault) e lo inserisce nel gruppo di risorse ContosoFailoverRG nell'area Stati Uniti orientali 2.

    ![Strumento Migrazione server di Azure Migrate](./media/contoso-migration-rehost-linux-vm/server-migration-tool.png)

**Ulteriore assistenza?**

[Informazioni](https://docs.microsoft.com/azure/migrate) su come configurare lo strumento Migrazione server di Azure Migrate.

### <a name="prepare-to-connect-to-azure-vms-after-failover"></a>Preparare la connessione alle macchine virtuali di Azure dopo il failover

Dopo il failover in Azure, Contoso intende connettersi alle macchine virtuali di Azure replicate. A tale scopo, gli amministratori di Contoso devono eseguire alcune operazioni:

- Per accedere alle macchine virtuali di Azure attraverso Internet, abilitano il protocollo SSH nella macchina virtuale Linux in locale prima della migrazione. Per Ubuntu questa operazione può essere eseguita con il comando seguente: **Sudo apt-get ssh install -y**.
- Dopo aver eseguito la migrazione (failover), possono selezionare **Boot diagnostics** (Diagnostica di avvio) per visualizzare uno screenshot della macchina virtuale.
- Se l'operazione non riesce, devono verificare che la macchina virtuale sia in esecuzione e rivedere questi [suggerimenti per la risoluzione dei problemi](https://social.technet.microsoft.com/wiki/contents/articles/31666.troubleshooting-remote-desktop-connection-after-failover-using-asr.aspx).

**Ulteriore assistenza?**

- [Informazioni](https://docs.microsoft.com/azure/migrate/contoso-migration-rehost-linux-vm#prepare-vms-for-migration) su come preparare le macchine virtuali per la migrazione

## <a name="step-3-replicate-the-on-premises-vms"></a>Passaggio 3: Replicare le macchine virtuali locali

Prima di poter eseguire una migrazione ad Azure, gli amministratori di Contoso devono configurare e abilitare la replica.

Al termine dell'individuazione, è possibile avviare la replica delle VM VMware in Azure.

1. In Azure Migrate Project > **servers** **Azure migrate: Server Migration**, fare clic su **replicate**.

    ![Replicare le VM](./media/contoso-migration-rehost-linux-vm/select-replicate.png)

2. In **Replica** > **Impostazioni origine**  > **I computer sono virtualizzati?** selezionare **Sì, con VMware vSphere**.
3. In **Appliance locale** selezionare il nome dell'appliance di Azure Migrate configurata e quindi **OK**.

    ![Impostazioni origine](./media/contoso-migration-rehost-linux-vm/source-settings.png)

4. In **Macchine virtuali** selezionare le VM da replicare.
    - Se è stata eseguita una valutazione delle VM, è possibile applicare i consigli dei risultati della valutazione in merito al tipo di disco (Premium/Standard) e alle dimensioni delle VM. A questo scopo, in **Importare le impostazioni di migrazione da una valutazione di Azure Migrate?** selezionare l'opzione **Sì**.
    - Se non è stata eseguita una valutazione o non si vogliono usare le impostazioni della valutazione, selezionare l'opzione **No**.
    - Se si è scelto di usare la valutazione, selezionare il gruppo di VM e il nome della valutazione.

    ![Selezionare la valutazione](./media/contoso-migration-rehost-linux-vm/select-assessment.png)

5. In **Macchine virtuali** cercare le VM in base alle esigenze e selezionare ogni macchina virtuale di cui si vuole eseguire la migrazione. Quindi fare clic su **Avanti: impostazioni di destinazione**.

6. In **Impostazioni di destinazione** selezionare la sottoscrizione e l'area di destinazione in cui eseguire la migrazione e quindi specificare il gruppo di risorse in cui risiederanno le VM di Azure dopo la migrazione. In **Rete virtuale** selezionare la rete virtuale e la subnet di Azure a cui verranno aggiunte le VM di Azure dopo la migrazione.
7. In **Vantaggio Azure Hybrid**:

    - Selezionare **No** se non si vuole applicare Vantaggio Azure Hybrid. Quindi fare clic su **Next**.
    - Selezionare **Sì** se si hanno computer Windows Server con copertura Software Assurance o sottoscrizioni di Windows Server attive e si vuole applicare il vantaggio alle VM di cui si sta eseguendo la migrazione. Quindi fare clic su **Next**.

8. In **Calcolo** controllare il nome, le dimensioni, il tipo di disco del sistema operativo e il set di disponibilità delle VM. Le VM devono essere conformi ai [requisiti di Azure](https://docs.microsoft.com/azure/migrate/migrate-support-matrix-vmware#agentless-migration-vmware-vm-requirements).

    - **Dimensioni macchina virtuale**: se si usano le raccomandazioni per la valutazione, l'elenco a discesa Dimensioni macchina virtuale conterrà le dimensioni consigliate. In caso contrario, Azure Migrate seleziona le dimensioni più simili nella sottoscrizione di Azure. In alternativa, selezionare manualmente le dimensioni in **Dimensioni macchina virtuale di Azure**.
    - **Disco del sistema operativo**: specificare il disco del sistema operativo (avvio) per la macchina virtuale. È il disco che contiene il bootloader e il programma di installazione del sistema operativo.
    - **Set di disponibilità**: se la macchina virtuale deve trovarsi in un set di disponibilità di Azure dopo la migrazione, specificare il set. Il set deve trovarsi nel gruppo di risorse di destinazione specificato per la migrazione.

9. In **Dischi** specificare se i dischi delle VM devono essere replicati in Azure e selezionare il tipo di disco in Azure (dischi gestiti Premium o SSD/HDD Standard). Quindi fare clic su **Next**.
    - È possibile escludere dischi dalla replica.
    - I dischi esclusi non saranno presenti nella VM di Azure dopo la migrazione.

10. In **Rivedi e avvia replica** verificare le impostazioni e fare clic su **Replica** per avviare la replica iniziale dei server.

> [!NOTE]
> È possibile aggiornare le impostazioni di replica in qualsiasi momento prima dell'avvio della replica, selezionando **Gestisci** > **Replica delle macchine virtuali**. Le impostazioni non possono essere modificate dopo l'avvio della replica.

## <a name="step-4-migrate-the-vms"></a>Passaggio 4: Eseguire la migrazione delle macchine virtuali

Gli amministratori di Contoso eseguono un rapido failover di test e poi un failover completo per la migrazione delle VM.

### <a name="run-a-test-failover"></a>Eseguire un failover di test

1. In **obiettivi di migrazione**  > **Server**  > **Azure migrate: migrazione del server**, fare clic su server di **test migrati**.

     ![Testare i server con migrazione completata](./media/contoso-migration-rehost-linux-vm/test-migrated-servers.png)

2. Fare clic con il pulsante destro del mouse sulla VM da testare e scegliere **Migrazione di test**.

    ![Migrazione di test](./media/contoso-migration-rehost-linux-vm/test-migrate.png)

3. In **Migrazione di test** selezionare la rete virtuale di Azure in cui verrà inserita la VM di Azure dopo la migrazione. Si consiglia di usare un VNet di non produzione.
4. Verrà avviato il processo **Migrazione di test**. Monitorare il processo nelle notifiche del portale.
5. Al termine della migrazione, visualizzare la VM di Azure di cui è stata eseguita la migrazione in **Macchine virtuali** nel portale di Azure. Il nome della macchina virtuale ha il suffisso **-Test**.
6. Al termine del test, fare clic con il pulsante destro del mouse sulla macchina virtuale di Azure in **Replica delle macchine virtuali** e scegliere **Pulisci migrazione di test**.

    ![Eseguire la pulizia della migrazione](./media/contoso-migration-rehost-linux-vm/clean-up.png)

### <a name="migrate-the-vms"></a>Eseguire la migrazione delle macchine virtuali

Gli amministratori di Contoso possono ora eseguire un failover completo per completare la migrazione.

1. Nel progetto Azure Migrate > **server**  > **Azure migrate: migrazione server**, fare clic su **server di replica**.

    ![Replica dei server](./media/contoso-migration-rehost-linux-vm/replicating-servers.png)

2. In **Replica delle macchine virtuali** fare clic con il pulsante destro del mouse sulla VM e scegliere **Esegui la migrazione**.
3. In **Esegui la migrazione** > **Spegnere le macchine virtuali ed eseguire una migrazione pianificata senza perdita di dati** selezionare **Sì** > **OK**.
    - Per impostazione predefinita, Azure Migrate arresta la VM locale ed esegue una replica su richiesta per sincronizzare le eventuali modifiche apportate alla macchina virtuale dopo l'ultima replica. Questa operazione assicura che non vi sia alcuna perdita di dati.
    - Se non si vuole arrestare la VM, selezionare **No**
4. Verrà avviato un processo di migrazione per la VM. Tenere traccia del processo nelle notifiche di Azure.
5. Al termine del processo, è possibile visualizzare e gestire la VM dalla pagina **Macchine virtuali**.

### <a name="connect-the-vm-to-the-database"></a>Connettere la macchina virtuale al database

Come passaggio finale del processo di migrazione, gli amministratori di Contoso aggiornano la stringa di connessione dell'applicazione in modo che punti al database dell'app in esecuzione sulla macchina virtuale **OSTICKETMYSQL**.

1. Crea una connessione SSH alla macchina virtuale **OSTICKETWEB** tramite Putty o un altro client SSH. La macchina virtuale è privata, pertanto Contoso si connette usando l'indirizzo IP privato.

    ![Connettersi al database](./media/contoso-migration-rehost-linux-vm/db-connect.png)

    ![Connettersi al database](./media/contoso-migration-rehost-linux-vm/db-connect2.png)

2. Contoso aggiorna le impostazioni in modo che la macchina virtuale **OSTICKETWEB** possa comunicare con la macchina virtuale **OSTICKETMYSQL**. Attualmente la configurazione è hardcoded con l'indirizzo IP locale 172.16.0.43.

    **Prima dell'aggiornamento:**

    ![Aggiornare l'indirizzo IP](./media/contoso-migration-rehost-linux-vm/update-ip1.png)

    **Dopo l'aggiornamento:**

    ![Aggiornare l'indirizzo IP](./media/contoso-migration-rehost-linux-vm/update-ip2.png)

3. Contoso riavvia il servizio con **systemctl restart apache2**.

    ![Riavvio](./media/contoso-migration-rehost-linux-vm/restart.png)

4. Aggiorna infine i record DNS per **OSTICKETWEB** e **OSTICKETMYSQL**, in uno dei controller di dominio Contoso.

    ![Aggiornare il DNS](./media/contoso-migration-rehost-linux-vm-mysql/update-dns.png)

    ![Aggiornare il DNS](./media/contoso-migration-rehost-linux-vm-mysql/update-dns.png)

**Ulteriore assistenza?**

- Sono disponibili [informazioni](https://docs.microsoft.com/azure/migrate/tutorial-migrate-vmware#run-a-test-migration) su come eseguire un failover di test.
- [Informazioni](https://docs.microsoft.com/azure/migrate/tutorial-migrate-vmware#migrate-vms) su come eseguire la migrazione delle macchine virtuali ad Azure.

## <a name="clean-up-after-migration"></a>Eseguire la pulizia dopo la migrazione

Al termine della migrazione, i livelli dell'app osTicket sono in esecuzione nelle macchine virtuali di Azure.

Ora Contoso deve eseguire le operazioni di pulizia seguenti:

- Rimuovere le VM locali dall'inventario vCenter.
- Rimuovere le macchine virtuali in locale dai processi di backup locali.
- Aggiornare la documentazione interna per mostrare la nuova posizione e gli indirizzi IP per OSTICKETWEB e OSTICKETMYSQL.
- Esaminare le risorse che interagiscono con le VM e aggiornare eventuali impostazioni o documenti pertinenti in modo che riflettano la nuova configurazione.
- Contoso ha usato il servizio Azure Migrate con il mapping delle dipendenze per valutare le macchine virtuali per la migrazione. Gli amministratori devono rimuovere la Microsoft Monitoring Agent e Microsoft Dependency Agent che hanno installato a questo scopo dalla macchina virtuale.

## <a name="review-the-deployment"></a>Esaminare la distribuzione

Con l'app in esecuzione, Contoso deve rendere pienamente operativa e proteggere la nuova infrastruttura.

### <a name="security"></a>Sicurezza

Il team di sicurezza di Contoso esamina le macchine virtuali OSTICKETWEB e OSTICKETMYSQL per determinare eventuali problemi di sicurezza.

- Il team esamina i gruppi di sicurezza di rete (NSG) per le macchine virtuali per controllare l'accesso. I gruppi di sicurezza di rete vengono usati per assicurarsi che possa passare solo il traffico consentito all'applicazione.
- Il team considera inoltre l'opportunità di proteggere i dati sui dischi delle macchine virtuali usando la crittografia dei dischi e Azure Key Vault.

Per altre informazioni, vedere [procedure consigliate per la sicurezza per carichi di lavoro IaaS in Azure](https://docs.microsoft.com/azure/security/fundamentals/iaas).

### <a name="bcdr"></a>BCDR

Per la continuità aziendale e il ripristino di emergenza, Contoso esegue le azioni seguenti:

- **Proteggere i dati.** Contoso esegue il backup dei dati nelle macchine virtuali usando il servizio Backup di Azure. [Altre informazioni](https://docs.microsoft.com/azure/backup/backup-introduction-to-azure-backup?toc=%2fazure%2fvirtual-machines%2flinux%2ftoc.json).
- **Mantenere le app in esecuzione.** Contoso esegue la replica delle macchine virtuali dell'app in Azure in un'area secondaria usando Site Recovery. [Altre informazioni](https://docs.microsoft.com/azure/site-recovery/azure-to-azure-quickstart).

### <a name="licensing-and-cost-optimization"></a>Licenze e ottimizzazione dei costi

- Dopo la distribuzione delle risorse, Contoso assegna tag di Azure, in base alle decisioni prese durante la [distribuzione dell'infrastruttura di Azure](./contoso-migration-infrastructure.md#set-up-tagging).
- Contoso non ha problemi di licenza con i server Ubuntu.
- Abiliterà Gestione costi di Azure, concesso in licenza da Cloudyn, un'affiliata Microsoft. Si tratta di una soluzione di gestione dei costi multi-cloud che consente di usare e gestire Azure e altre risorse cloud. Vedere [questo articolo](https://docs.microsoft.com/azure/cost-management/overview) per altre informazioni su Gestione costi di Azure.
