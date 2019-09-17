---
title: Eseguire il rehosting di un'app con la migrazione a macchine virtuali di Azure mediante Azure Site Recovery
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni su come Contoso esegue il rehosting di un'app locale con una migrazione "lift-and-shift" di macchine locali ad Azure i mediante il servizio Azure Site Recovery.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/11/2018
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
services: site-recovery
ms.openlocfilehash: 3bc125145afce529507a341eae6b818cceee9330
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71024017"
---
# <a name="rehost-an-on-premises-app-to-azure-vms"></a>Rehosting di un'app locale in macchine virtuali di Azure

Questo articolo illustra come la società fittizia Contoso esegue il rehosting di un'app front-end di Windows .NET a due livelli in esecuzione su macchine virtuali VMware eseguendo la migrazione delle macchine virtuali dell'app a macchine virtuali di Azure.

L'app SmartHotel360 usata in questo esempio viene fornita come open source. È possibile scaricarla da [GitHub](https://github.com/Microsoft/SmartHotel360) per usarla a scopi di test personalizzati.

## <a name="business-drivers"></a>Driver di business

Il team di leadership IT collabora attivamente con i partner commerciali per capire gli obiettivi da raggiungere con questa migrazione:

- **Stare al passo con la crescita del business:** Contoso è in espansione e di conseguenza l'infrastruttura e i sistemi locali sono sotto pressione.
- **Limitare i rischi:** l'app SmartHotel360 è fondamentale per il business di Contoso. L'obiettivo è spostare l'app in Azure senza correre alcun rischio.
- **Estendere:** Contoso non vuole modificare l'app, ma vuole assicurarsi che sia stabile.

## <a name="migration-goals"></a>Obiettivi della migrazione

Il team di cloud di Contoso ha fissato alcuni obiettivi per la migrazione. Questi obiettivi consentono di determinare il metodo di migrazione ideale:

- Dopo la migrazione, l'app in Azure dovrà avere le stesse caratteristiche prestazionali riscontrate oggi in VMware. L'app manterrà la stessa importanza critica nel cloud come la corrispondente versione in locale.
- Contoso non intende investire in questa app. L'app è importante per l'azienda, ma Contoso vuole semplicemente eseguirne la migrazione sicura al cloud nella sua forma attuale.
- Contoso non intende modificare il modello operativo dell'app. Punta all'interazione nel cloud esattamente come avviene ora.
- Contoso non intende modificare le funzionalità dell'app. Cambierà solo la posizione.

## <a name="solution-design"></a>Progettazione della soluzione

Dopo aver definito i propri obiettivi e requisiti, Contoso progetta ed esamina una soluzione di distribuzione, identificando il processo di migrazione, tra cui i servizi di Azure da usare per la migrazione.

### <a name="current-app"></a>App attuale

- L'app è suddivisa a livelli tra due VM (**WEBVM** e **SQLVM**).
- Le macchine virtuali si trovano nell'host VMware ESXi **contosohost1.contoso.com** (versione 6.5).
- L'ambiente VMware viene gestito dal server vCenter 6.5 (**vcenter.contoso.com**) in esecuzione in una macchina virtuale.
- Contoso ha un data center locale (contoso-datacenter) con un controller di dominio locale (**contosodc1**).

### <a name="proposed-architecture"></a>Architettura proposta

- Poiché l'app costituisce un carico di lavoro di produzione, le macchine virtuali dell'app in Azure risiederanno nel gruppo di risorse di produzione ContosoRG.
- Le macchine virtuali dell'app verranno migrate nell'area primaria di Azure (Stati Uniti orientali 2) e collegate alla rete di produzione (VNET-PROD-EUS2).
- La macchina virtuale front-end Web risiederà nella subnet front-end (PROD-FE-EUS2) nella rete di produzione.
- La macchina virtuale del database risiederà nella subnet del database (PROD-DB-EUS2) nella rete di produzione.
- Le macchine virtuali locali nel data center Contoso verranno rimosse al termine della migrazione.

![Architettura dello scenario](./media/contoso-migration-rehost-vm/architecture.png)

### <a name="database-considerations"></a>Considerazioni sul database

Come parte del processo di progettazione della soluzione, Contoso ha eseguito un confronto delle funzionalità tra Database SQL di Azure e SQL Server. Le considerazioni seguenti hanno portato alla decisione di usare SQL Server in esecuzione su una macchina virtuale IaaS di Azure:

- L'uso di una macchina virtuale di Azure con SQL Server sembra essere una soluzione ottimale se Contoso ha l'esigenza di personalizzare il sistema operativo o il server di database oppure se vuole posizionare ed eseguire app di terze parti nella stessa macchina virtuale.
- Con Software Assurance, Contoso può scambiare in futuro le licenze esistenti con tariffe scontate per un'istanza gestita di database SQL usando l'offerta Vantaggio Azure Hybrid per SQL Server. In questo modo può risparmiare fino al 30% sull'istanza gestita.

### <a name="solution-review"></a>Revisione della soluzione

Contoso valuta la progettazione proposta elaborando un elenco di vantaggi e svantaggi.

<!-- markdownlint-disable MD033 -->

**Considerazioni** | **Dettagli**
--- | ---
**Vantaggi** | Entrambe le macchine virtuali dell'app verranno spostate in Azure senza modifiche, semplificando così la migrazione.<br/><br/> Poiché Contoso usa la modalità "lift and shift" per entrambe le macchine virtuali dell'app, non sono necessari particolari strumenti di configurazione o migrazione per il database dell'app.<br/><br/> Contoso può sfruttare il proprio investimento in Software Assurance usando l'offerta Vantaggio Azure Hybrid.<br/><br/> Contoso manterrà il controllo completo delle macchine virtuali dell'app in Azure.
**Svantaggi** | WEBVM e SQLVM eseguono Windows Server 2008 R2. Il sistema operativo è supportato da Azure per ruoli specifici (luglio 2018). [Altre informazioni](https://support.microsoft.com/help/2721672/microsoft-server-software-support-for-microsoft-azure-virtual-machines)<br/><br/> I livelli Web e dati dell'app rimarranno come singolo punto di failover.<br/><br/> SQLVM è in esecuzione in SQL Server 2008 R2, che non è incluso nel supporto Mainstream, anche se è supportato per le macchine virtuali di Azure (luglio 2018). [Altre informazioni](https://support.microsoft.com/help/956893)<br/><br/> Contoso dovrà continuare a supportare l'app come macchine virtuali di Azure anziché passare a un servizio gestito come Servizio app di Azure e Database SQL di Azure.

<!-- markdownlint-enable MD033 -->

### <a name="migration-process"></a>Processo di migrazione

Contoso eseguirà la migrazione delle macchine virtuali front-end e del database dell'app a macchine virtuali di Azure con il metodo senza agente per lo strumento Migrazione server di Azure Migrate.

- In primo luogo, Contoso prepara e configura i componenti di Azure per Migrazione server di Azure Migrate e predispone l'infrastruttura VMware locale.
- L'[infrastruttura di Azure](./contoso-migration-infrastructure.md) è già presente, quindi Contoso deve semplicemente aggiungere e configurare la replica delle macchine virtuali tramite lo strumento Migrazione server di Azure Migrate.
- Al termine delle attività di preparazione, Contoso può iniziare a replicare le macchine virtuali.
- Non appena la replica è abilitata e operativa, Contoso esegue la migrazione della macchina eseguendone il failover in Azure.

![Processo di migrazione](./media/contoso-migration-rehost-vm/migration-process-az-migrate.png)

### <a name="azure-services"></a>Servizi di Azure

**Servizio** | **Descrizione** | **Costii**
--- | --- | ---
[Migrazione server di Azure Migrate](https://docs.microsoft.com/azure/migrate/contoso-migration-rehost-vm) | Il servizio orchestra e gestisce la migrazione delle app e dei carichi di lavoro locali e delle istanze di macchine virtuali AWS/GCP. | Durante la replica in Azure vengono addebitati costi relativi all'archiviazione di Azure. In caso di failover vengono create macchine virtuali di Azure, le quali sono soggette a costi. [Altre informazioni](https://azure.microsoft.com/pricing/details/azure-migrate/) su addebiti e prezzi.

## <a name="prerequisites"></a>Prerequisiti

Ecco i requisiti che Contoso dovrà soddisfare per questo scenario.

<!-- markdownlint-disable MD033 -->

**Requisiti** | **Dettagli**
--- | ---
**Sottoscrizione di Azure** | Contoso ha creato le sottoscrizioni in un articolo precedente di questa serie. Se non si ha una sottoscrizione di Azure, creare un [account gratuito](https://azure.microsoft.com/pricing/free-trial).<br/><br/> Se si crea un account gratuito, si è l'amministratore della sottoscrizione e si possono eseguire tutte le azioni.<br/><br/> Se si usa una sottoscrizione esistente e non si ha il ruolo di amministratore, è necessario rivolgersi all'amministratore per l'assegnazione delle autorizzazioni di proprietario o collaboratore.<br/><br/> Se sono necessarie autorizzazioni più granulari, vedere [questo articolo](https://docs.microsoft.com/azure/site-recovery/site-recovery-role-based-linked-access-control).
**Infrastruttura di Azure** | [Informazioni](./contoso-migration-infrastructure.md) sul modo in cui Contoso configura un'infrastruttura di Azure.<br/><br/> Altre informazioni sui [prerequisiti](https://docs.microsoft.com/azure/migrate/contoso-migration-rehost-vm#prerequisites) specifici per Migrazione server di Azure Migrate.
**Server locali** | I server vCenter locali devono eseguire la versione 5.5, 6.0 o 6.5<br/><br/> Gli host ESXi devono eseguire la versione 5.5, 6.0 o 6.5<br/><br/> Nell'host ESXi devono essere in esecuzione una o più VM VMware.

<!-- markdownlint-enable MD033 -->

## <a name="scenario-steps"></a>Passaggi dello scenario

Ecco in che modo gli amministratori di Contoso eseguiranno la migrazione:

> [!div class="checklist"]
>
> - **Passaggio 1: Preparare Azure per Migrazione server di Azure Migrate.** Contoso aggiunge lo strumento Migrazione server al progetto di Azure Migrate.
> - **Passaggio 2: Preparare VMware locale per Migrazione server di Azure Migrate.** Contoso prepara gli account per l'individuazione delle macchine virtuali e si prepara alla connessione alle macchine virtuali di Azure dopo il failover.
> - **Passaggio 3: Replicare le macchine virtuali:** viene configurata e avviata la replica delle VM in Archiviazione di Azure.
> - **Passaggio 4: Eseguire la migrazione delle macchine virtuali con Migrazione server di Azure Migrate.** vengono effettuati un failover di test per verificare che tutto funzioni come previsto e un failover completo per eseguire la migrazione delle macchine virtuali ad Azure.

## <a name="step-1-prepare-azure-for-the-azure-migrate-server-migration-tool"></a>Passaggio 1: Preparare Azure per lo strumento Migrazione server di Azure Migrate

Ecco i componenti di Azure necessari a Contoso per la migrazione delle VM ad Azure:

- Una rete virtuale in cui verranno collocate le VM di Azure al momento della creazione, durante il failover.
- Lo strumento Migrazione server di Azure Migrate di cui è stato effettuato il provisioning.

Per configurare questi elementi, Contoso segue questa procedura:

1. Configurare una rete. Contoso ha già configurato una rete che può usare Migrazione server di Azure Migrate quando ha [distribuito l'infrastruttura di Azure](./contoso-migration-infrastructure.md).

    - SmartHotel360 è un'app di produzione e le VM verranno migrate alla rete di produzione di Azure (VNET-PROD-EUS2) nell'area primaria degli Stati Uniti orientali 2.
    - Entrambe le VM verranno inserite nel gruppo di risorse ContosoRG, usato per le risorse di produzione.
    - La macchina virtuale front-end dell'app (WEBVM) verrà migrata alla subnet front-end (PROD-FE-EUS2) nella rete di produzione.
    - La VM del database dell'app (SQLVM) verrà migrata alla subnet del database (PROD-DB-EUS2) nella rete di produzione.

2. Effettuare il provisioning dello strumento Migrazione server di Azure Migrate. Dopo la configurazione della rete e dell'account di archiviazione, Contoso crea un insieme di credenziali di Servizi di ripristino (ContosoMigrationVault) e lo inserisce nel gruppo di risorse ContosoFailoverRG nell'area primaria Stati Uniti orientali 2.

    ![Strumento Migrazione server di Azure Migrate](./media/contoso-migration-rehost-vm/server-migration-tool.png)

**Ulteriore assistenza?**

[Informazioni](https://docs.microsoft.com/azure/migrate/) su come configurare lo strumento Migrazione server di Azure Migrate.

### <a name="prepare-to-connect-to-azure-vms-after-failover"></a>Preparare la connessione alle macchine virtuali di Azure dopo il failover

Dopo il failover, Contoso intende connettersi alle VM di Azure. A tale scopo, gli amministratori di Contoso eseguono le operazioni seguenti prima della migrazione:

1. Per l'accesso tramite Internet:

    - Abilitano RDP nella VM locale prima del failover.
    - Verifica che per il profilo **Pubblico** siano aggiunte le regole TCP e UDP.
    - Verifica che RDP sia consentito in **Windows Firewall** > **App consentite** per tutti i profili.

2. Per l'accesso tramite VPN da sito a sito:

    - Abilita RDP nella macchina virtuale locale.
    - Consente RDP in **Windows Firewall** -> **App e funzionalità consentite** per le reti di **dominio e private**.
    - Imposta i criteri SAN del sistema operativo nella VM locale su **OnlineAll**.

Inoltre, quando esegue un failover, deve verificare quanto segue:

- Quando si attiva un failover, nella VM non devono essere presenti aggiornamenti di Windows in sospeso. Se sono presenti aggiornamenti in sospeso, non sarà possibile accedere alla VM finché questi non sono completati.
- Dopo il failover, può selezionare **Diagnostica di avvio** per visualizzare uno screenshot della VM. Se l'operazione non funziona, verifica che la VM sia in esecuzione e rivede questi [suggerimenti per la risoluzione dei problemi](https://social.technet.microsoft.com/wiki/contents/articles/31666.troubleshooting-remote-desktop-connection-after-failover-using-asr.aspx).

**Ulteriore assistenza?**

- [Informazioni](https://docs.microsoft.com/azure/migrate/contoso-migration-rehost-vm#prepare-vms-for-migration) su come preparare le macchine virtuali per la migrazione

## <a name="step-3-replicate-the-on-premises-vms"></a>Passaggio 3: Replicare le macchine virtuali locali

Prima di poter eseguire una migrazione ad Azure, gli amministratori di Contoso devono configurare e abilitare la replica.

Al termine dell'individuazione, è possibile avviare la replica delle VM VMware in Azure.

1. Nel progetto di Azure Migrate selezionare **Server** e **Azure Migrate: Migrazione server**, quindi **Replica**.

    ![Replicare le VM](./media/contoso-migration-rehost-vm/select-replicate.png)

2. In **Replica** > **Impostazioni origine**  > **I computer sono virtualizzati?** selezionare **Sì, con VMware vSphere**.

3. In **Appliance locale** selezionare il nome dell'appliance di Azure Migrate configurata e quindi **OK**.

    ![Impostazioni origine](./media/contoso-migration-rehost-vm/source-settings.png)

4. In **Macchine virtuali** selezionare le VM da replicare.
    - Se è stata eseguita una valutazione delle VM, è possibile applicare i consigli dei risultati della valutazione in merito al tipo di disco (Premium/Standard) e alle dimensioni delle VM. A questo scopo, in **Importare le impostazioni di migrazione da una valutazione di Azure Migrate?** selezionare l'opzione **Sì**.
    - Se non è stata eseguita una valutazione o non si vogliono usare le impostazioni della valutazione, selezionare l'opzione **No**.
    - Se si è scelto di usare la valutazione, selezionare il gruppo di VM e il nome della valutazione.

    ![Selezionare la valutazione](./media/contoso-migration-rehost-vm/select-assessment.png)

5. In **Macchine virtuali** cercare le VM in base alle esigenze e selezionare ogni macchina virtuale di cui si vuole eseguire la migrazione. Fare quindi clic su **Avanti: Impostazioni di destinazione**.

6. In **Impostazioni di destinazione** selezionare la sottoscrizione e l'area di destinazione in cui eseguire la migrazione e quindi specificare il gruppo di risorse in cui risiederanno le VM di Azure dopo la migrazione. In **Rete virtuale** selezionare la rete virtuale e la subnet di Azure a cui verranno aggiunte le VM di Azure dopo la migrazione.

7. In **Vantaggio Azure Hybrid**:

    - Selezionare **No** se non si vuole applicare Vantaggio Azure Hybrid. Scegliere quindi **Avanti**.
    - Selezionare **Sì** se si hanno computer Windows Server con copertura Software Assurance o sottoscrizioni di Windows Server attive e si vuole applicare il vantaggio alle VM di cui si sta eseguendo la migrazione. Scegliere quindi **Avanti**.

8. In **Calcolo** controllare il nome, le dimensioni, il tipo di disco del sistema operativo e il set di disponibilità delle VM. Le VM devono essere conformi ai [requisiti di Azure](https://docs.microsoft.com/azure/migrate/migrate-support-matrix-vmware#agentless-migration-vmware-vm-requirements).

    - **Dimensioni macchina virtuale**: se si usano i consigli per la valutazione, l'elenco a discesa Dimensioni macchina virtuale conterrà le dimensioni consigliate. In caso contrario, Azure Migrate seleziona le dimensioni più simili nella sottoscrizione di Azure. In alternativa, selezionare manualmente le dimensioni in **Dimensioni macchina virtuale di Azure**.
    - **Disco del sistema operativo**: specificare il disco del sistema operativo (di avvio) per la VM. È il disco che contiene il bootloader e il programma di installazione del sistema operativo.
    - **Set di disponibilità**: se la VM deve essere inclusa in un set di disponibilità di Azure dopo la migrazione, specificare il set. Il set deve trovarsi nel gruppo di risorse di destinazione specificato per la migrazione.

9. In **Dischi** specificare se i dischi delle VM devono essere replicati in Azure e selezionare il tipo di disco in Azure (dischi gestiti Premium o SSD/HDD Standard). Scegliere quindi **Avanti**.
    - È possibile escludere dischi dalla replica.
    - I dischi esclusi non saranno presenti nella VM di Azure dopo la migrazione.

10. In **Rivedi e avvia replica** verificare le impostazioni e fare clic su **Replica** per avviare la replica iniziale dei server.

> [!NOTE]
> È possibile aggiornare le impostazioni di replica in qualsiasi momento prima dell'avvio della replica, selezionando **Gestisci** > **Replica delle macchine virtuali**. Le impostazioni non possono essere modificate dopo l'avvio della replica.

## <a name="step-4-migrate-the-vms"></a>Passaggio 4: Eseguire la migrazione delle macchine virtuali

Gli amministratori di Contoso eseguono un rapido failover di test e poi un failover completo per la migrazione delle VM.

### <a name="run-a-test-failover"></a>Eseguire un failover di test

1. In **Obiettivi della migrazione** > **Server** > **Azure Migrate: Migrazione server** fare clic su **Testare i server con migrazione completata**.

     ![Testare i server con migrazione completata](./media/contoso-migration-rehost-vm/test-migrated-servers.png)

2. Fare clic con il pulsante destro del mouse sulla VM da testare e scegliere **Migrazione di test**.

    ![Migrazione di test](./media/contoso-migration-rehost-vm/test-migrate.png)

3. In **Migrazione di test** selezionare la rete virtuale di Azure in cui verrà inserita la VM di Azure dopo la migrazione. Si consiglia di usare un VNet di non produzione.
4. Verrà avviato il processo **Migrazione di test**. Monitorare il processo nelle notifiche del portale.
5. Al termine della migrazione, visualizzare la VM di Azure di cui è stata eseguita la migrazione in **Macchine virtuali** nel portale di Azure. Il nome della macchina virtuale ha il suffisso **-Test**.
6. Al termine del test, fare clic con il pulsante destro del mouse sulla macchina virtuale di Azure in **Replica delle macchine virtuali** e scegliere **Pulisci migrazione di test**.

    ![Eseguire la pulizia della migrazione](./media/contoso-migration-rehost-vm/clean-up.png)

### <a name="migrate-the-vms"></a>Eseguire la migrazione delle macchine virtuali

Gli amministratori di Contoso possono ora eseguire un failover completo per completare la migrazione.

1. Nel progetto di Azure Migrate selezionare **Server** > **Azure Migrate: Migrazione server** e fare clic su **Replica dei server**.

    ![Replica dei server](./media/contoso-migration-rehost-vm/replicating-servers.png)

2. In **Replica delle macchine virtuali** fare clic con il pulsante destro del mouse sulla VM e scegliere **Esegui la migrazione**.
3. In **Esegui la migrazione** > **Spegnere le macchine virtuali ed eseguire una migrazione pianificata senza perdita di dati** selezionare **Sì** > **OK**.
    - Per impostazione predefinita, Azure Migrate arresta la VM locale ed esegue una replica su richiesta per sincronizzare le eventuali modifiche apportate alla macchina virtuale dopo l'ultima replica. Questa operazione assicura che non vi sia alcuna perdita di dati.
    - Se non si vuole arrestare la VM, selezionare **No**
4. Verrà avviato un processo di migrazione per la VM. Tenere traccia del processo nelle notifiche di Azure.
5. Al termine del processo, è possibile visualizzare e gestire la VM dalla pagina **Macchine virtuali**.

**Ulteriore assistenza?**

- Sono disponibili [informazioni](https://docs.microsoft.com/azure/migrate/tutorial-migrate-vmware#run-a-test-migration) su come eseguire un failover di test.
- [Informazioni](https://docs.microsoft.com/azure/migrate/tutorial-migrate-vmware#migrate-vms) su come eseguire la migrazione delle macchine virtuali ad Azure.

## <a name="clean-up-after-migration"></a>Eseguire la pulizia dopo la migrazione

Al termine della migrazione i livelli dell'app SmartHotel360 saranno in esecuzione in VM di Azure.

Ora Contoso deve eseguire le operazioni di pulizia seguenti:

- Al termine della migrazione, arrestare la replica.
- Rimuovere il computer WEBVM dall'inventario di vCenter.
- Rimuovere il computer SQLVM dall'inventario di vCenter.
- Rimuovere WEBVM e SQLVM dai processi di backup locali.
- Aggiornare la documentazione interna per visualizzare la nuova posizione e gli indirizzi IP per le VM.
- Esaminare le risorse che interagiscono con le VM e aggiornare eventuali impostazioni o documenti pertinenti in modo che riflettano la nuova configurazione.

## <a name="review-the-deployment"></a>Esaminare la distribuzione

Ora che l'app è in esecuzione, Contoso deve operazionalizzarla e proteggerla completamente in Azure.

### <a name="security"></a>Security

Il team di sicurezza Contoso esamina le VM di Azure per determinare eventuali problemi di sicurezza.

- Per controllare l'accesso, il team esamina i gruppi di sicurezza di rete (NSG) per le macchine virtuali. I gruppi di sicurezza di rete fanno in modo che l'app possa essere raggiunta solo dal traffico consentito.
- Il team valuta inoltre l'opportunità di proteggere i dati sul disco usando Crittografia dischi di Azure e Key Vault.

[Altre informazioni](https://docs.microsoft.com/azure/security/azure-security-best-practices-vms) sulle procedure di sicurezza per le macchine virtuali.

## <a name="bcdr"></a>BCDR

Per la continuità aziendale e il ripristino di emergenza (BCDR), Contoso esegue le azioni seguenti:

- Proteggere i dati: Contoso esegue il backup dei dati nelle macchine virtuali usando il servizio Backup di Azure. [Altre informazioni](https://docs.microsoft.com/azure/backup/backup-introduction-to-azure-backup?toc=%2fazure%2fvirtual-machines%2flinux%2ftoc.json)
- Mantenere le app in esecuzione: Contoso esegue la replica delle macchine virtuali dell'app in Azure in un'area secondaria usando Site Recovery. [Altre informazioni](https://docs.microsoft.com/azure/site-recovery/azure-to-azure-quickstart)

### <a name="licensing-and-cost-optimization"></a>Licenze e ottimizzazione dei costi

1. Contoso dispone di licenze esistenti per le macchine virtuali e sfrutterà il Vantaggio Azure Hybrid. Convertirà le VM di Azure esistenti per usufruire di questi prezzi.
2. Contoso abiliterà Gestione costi, concesso in licenza da Cloudyn, una affiliata Microsoft. Si tratta di una soluzione di gestione dei costi multi-cloud che consente di usare e gestire Azure e altre risorse cloud. [Altre informazioni](https://docs.microsoft.com/azure/cost-management/overview) sulla Gestione costi di Azure.

## <a name="conclusion"></a>Conclusione

In questo articolo Contoso ha eseguito il rehosting dell'app SmartHotel360 in Azure eseguendo la migrazione delle macchine virtuali dell'app alle macchine virtuali di Azure mediante lo strumento Migrazione server di Azure Migrate.
