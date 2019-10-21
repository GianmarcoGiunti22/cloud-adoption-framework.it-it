---
title: Effettuare il refactoring di un'app eseguendone la migrazione in Servizio app di Azure e nel database SQL di Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni su come Contoso esegue il rehosting di un'app locale eseguendone la migrazione a un'app Web di Servizio app di Azure e al database SQL di Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/11/2018
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
services: site-recovery
ms.openlocfilehash: 0118fcf3ca5b724a90d5e68482bfe6fe1a7e6abb
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548212"
---
# <a name="refactor-an-on-premises-app-to-an-azure-app-service-web-app-and-azure-sql-database"></a>Effettuare il refactoring di un'app locale in un'app Web di Servizio app di Azure e nel database SQL di Azure

Questo articolo illustra come la società fittizia Contoso effettua il refactoring di un'app di Windows .NET a due livelli in esecuzione su macchine virtuali VMware come parte di una migrazione ad Azure. Esegue la migrazione della macchina virtuale front-end dell'app a un'app Web di Servizio app di Azure e del database dell'app a un database SQL di Azure.

L'app SmartHotel360 usata in questo esempio viene fornita come open source. È possibile scaricarla da [GitHub](https://github.com/Microsoft/SmartHotel360) per usarla a scopi di test personalizzati.

## <a name="business-drivers"></a>Fattori chiave per lo sviluppo aziendale

Il team di leadership IT collabora attivamente con i partner commerciali per capire gli obiettivi da raggiungere con questa migrazione:

- **Stare al passo con la crescita aziendale:** Contoso è in espansione e l'infrastruttura e i sistemi locali iniziano a sentirne la pressione.
- **Aumentare l'efficienza:** occorre rimuovere le procedure inutili e semplificare i processi per sviluppatori e utenti. L'azienda richiede un settore IT rapido ed efficiente in termini di tempo e costi, in modo da soddisfare più velocemente le esigenze dei clienti.
- **Aumentare l'agilità.**  il settore IT di Contoso deve essere più reattivo alle esigenze dell'azienda. Deve essere in grado di reagire più rapidamente ai cambiamenti nel marketplace, in modo da raggiungere risultati di successo in un'economia globale. Non deve rappresentare un ostacolo per le attività aziendali.
- **Scalabilità.** il settore IT di Contoso deve fornire sistemi in grado di crescere di pari passo con l'espansione dell'azienda.
- **Ridurre i costi:** Contoso desidera ridurre al minimo i costi di licenza.

## <a name="migration-goals"></a>Obiettivi della migrazione

Il team di cloud di Contoso ha fissato alcuni obiettivi per la migrazione. Questi obiettivi consentono di determinare il metodo di migrazione ideale.

<!-- markdownlint-disable MD033 -->

**Requisiti** | **Dettagli**
--- | ---
**App** | L'app in Azure manterrà il livello di criticità attuale.<br/><br/> Deve avere le stesse funzionalità di prestazioni di cui dispone attualmente in VMware.<br/><br/> Il team non intende investire nell'app. Per il momento, gli amministratori spostano semplicemente l'app in modo sicuro nel cloud.<br/><br/> Il team intende interrompere il supporto Windows Server 2008 R2, in cui viene attualmente eseguita l'app.<br/><br/> Il team intende passare da SQL Server 2008 R2 a una piattaforma di database PaaS moderna, per ridurre al minimo la necessità di gestione.<br/><br/> Contoso vuole sfruttare gli investimenti effettuati nelle licenze di SQL Server e Software Assurance, laddove possibile.<br/><br/> Contoso vuole anche ridurre il singolo punto di guasto nel livello Web.
**Limitazioni** | L'app è costituita da un'app ASP.NET e un servizio WCF in esecuzione nella stessa macchina virtuale. Si desidera suddividere questa tra due app Web usando il Servizio app di Azure.
**Azure** | Contoso intende spostare l'app in Azure, ma non eseguirlo nelle macchine virtuali. Contoso intende usare i servizi PaaS di Azure per i livelli Web e dati.
**DevOps** | Contoso intende passare a un modello DevOps usando Azure DevOps per le pipeline di compilazione e di versione del codice.

<!-- markdownlint-enable MD033 -->

## <a name="solution-design"></a>Progettazione della soluzione

Dopo aver definito obiettivi e requisiti, Contoso progetta ed esamina una soluzione di distribuzione, identificando il processo di migrazione, tra cui i servizi di Azure da usare per la migrazione.

### <a name="current-app"></a>App attuale

- L'app locale SmartHotel360 è suddivisa in livelli tra due macchine virtuali (WEBVM e SQLVM).
- Le VM si trovano nell'host VMware ESXi **contosohost1.contoso.com** (versione 6.5).
- L'ambiente VMware è gestito da vCenter Server 6.5 (**vcenter.contoso.com**) in esecuzione in una VM.
- Contoso ha un data center locale (contoso-datacenter) con un controller di dominio locale (**contosodc1**).
- Le autorizzazioni delle VM locali nel data center Contoso verranno rimosse al termine della migrazione.

### <a name="proposed-solution"></a>Soluzione proposta

- Per il livello di database dell'app, Contoso ha confrontato il database SQL di Azure con SQL Server usando [questo articolo](https://docs.microsoft.com/azure/sql-database/sql-database-features). Contoso ha deciso di usare il database SQL di Azure per diversi motivi:
  - Il database SQL di Azure è un servizio gestito di database relazionale. Offre prestazioni prevedibili a più livelli di servizio, con esigenze di amministrazione quasi nulle. Tra i vantaggi: scalabilità dinamica senza tempi di inattività, ottimizzazione dell'intelligente incorporata, scalabilità e disponibilità globali.
  - Contoso può usare lo strumento semplificato Data Migration Assistant (DMA) per valutare il database locale ed eseguirne la migrazione ad Azure SQL.
  - Con Software Assurance, Contoso può scambiare le licenze esistenti con tariffe scontate per un database SQL tramite l'offerta Vantaggio Azure Hybrid per SQL Server. È possibile risparmiare fino al 30%.
  - Il database SQL offre diverse funzionalità di sicurezza tra cui funzionalità Always Encrypted, maschera dati dinamica e sicurezza a livello di riga/rilevamento di minacce.
- Per il livello di app Web, Contoso ha deciso di usare Servizio app di Azure. Questo servizio PaaS consente di distribuire l'app con poche modifiche alla configurazione. Contoso userà Visual Studio per apportare modifiche e distribuire due app Web. Una per il sito Web e l'altra per il servizio WCF.
- Per soddisfare i requisiti di una pipeline di DevOps, Contoso ha scelto di usare Azure DevOps per la gestione del codice sorgente con i repository GIT. Le build e le versioni automatizzate vengono usate per compilare il codice e distribuirlo in Servizio app di Azure.

### <a name="solution-review"></a>Revisione della soluzione

Contoso valuta la progettazione proposta elaborando un elenco di vantaggi e svantaggi.

<!-- markdownlint-disable MD033 -->

**Considerazioni** | **Dettagli**
--- | ---
**Vantaggi** | Il codice dell'app SmartHotel360 non dovrà essere modificato per eseguire la migrazione ad Azure.<br/><br/> Contoso può sfruttare i propri investimenti in Software Assurance usando l'offerta Vantaggio Azure Hybrid per SQL Server e Windows Server.<br/><br/> Dopo la migrazione, Windows Server 2008 R2 non dovrà essere supportato. [Altre informazioni](https://support.microsoft.com/lifecycle).<br/><br/> Contoso può configurare il livello Web dell'app con più istanze, in modo che non sia più un singolo punto di guasto.<br/><br/> Il database non dipenderà più da SQL Server 2008 R2, non più recente.<br/><br/> Il database SQL supporta i requisiti tecnici. Contoso ha valutato il database locale usando Data Migration Assistant e ne ha verificato la compatibilità.<br/><br/> Il database SQL di Azuere dispone di tolleranza di errore incorporata; la configurazione da parte di Contoso non è necessaria. Ciò garantisce che il livello dati non sia più un singolo punto di failover.
**Svantaggi** | Servizio app di Azure supporta solo una distribuzione di app per ogni applicazione Web. Ciò significa che è necessario effettuare il provisioning di due app Web (una per il sito Web e l'altra per il servizio WCF).<br/><br/> Se contoso usa il Data Migration Assistant anziché il servizio migrazione del database di Azure per eseguire la migrazione del database, non avrà l'infrastruttura pronta per la migrazione dei database su larga scala. Sarà necessario creare un'altra area per garantire il failover, se non disponibile nell'area primaria.

<!-- markdownlint-enable MD033 -->

## <a name="proposed-architecture"></a>Architettura proposta

![Architettura dello scenario](media/contoso-migration-refactor-web-app-sql/architecture.png)

### <a name="migration-process"></a>Processo di migrazione

1. Contoso effettua il provisioning di un'istanza di Azure SQL e la migrazione del database di SmartHotel360 nell'istanza stessa.
2. Contoso effettua il provisioning e configura le app Web e distribuisce SmartHotel360 in tali app.

    ![Processo di migrazione](media/contoso-migration-refactor-web-app-sql/migration-process.png)

### <a name="azure-services"></a>Servizi di Azure

**Servizio** | **Descrizione** | **Costii**
--- | --- | ---
[Data Migration Assistant (DMA)](/sql/dma/dma-overview?view=ssdt-18vs2017) | Contoso usa DMA per valutare e rilevare i problemi di compatibilità che possono compromettere le funzionalità dei database in Azure. DMA valuta l'analogia nelle funzionalità tra le origini e le destinazioni SQL e consiglia miglioramenti nelle prestazioni e nell'affidabilità. | Questo strumento è scaricabile gratuitamente.
[Database SQL di Azure](https://azure.microsoft.com/services/sql-database) | Servizio di database cloud relazionale intelligente completamente gestito. | Costo in base a funzionalità, velocità effettiva e dimensioni. [Altre informazioni](https://azure.microsoft.com/pricing/details/sql-database/managed).
[Informazioni sul servizio app di Azure](https://docs.microsoft.com/azure/app-service/overview) | Crea app cloud avanzate usando una piattaforma completamente gestita | Costo in base a durata, dimensioni, posizione e utilizzo. [Altre informazioni](https://azure.microsoft.com/pricing/details/app-service/windows).
[Azure DevOps](https://docs.microsoft.com/azure/azure-portal/tutorial-azureportal-devops) | Fornisce una pipeline di integrazione e distribuzione continua (CI/CD) per lo sviluppo delle app. La pipeline inizia con un repository GIT per la gestione del codice app, un sistema di compilazione per la produzione di pacchetti e altri artefatti di compilazione, nonché un sistema di Release Management per implementare le modifiche negli ambienti di sviluppo, test e produzione.

## <a name="prerequisites"></a>Prerequisiti

Di seguito vengono indicati i requisiti che Contoso deve soddisfare per questo scenario.

<!-- markdownlint-disable MD033 -->

**Requisiti** | **Dettagli**
--- | ---
**Sottoscrizione di Azure** | Contoso ha creato le sottoscrizioni in un articolo precedente. Se non si ha una sottoscrizione di Azure, creare un [account gratuito](https://azure.microsoft.com/pricing/free-trial).<br/><br/> Se si crea un account gratuito, si è l'amministratore della sottoscrizione e si possono eseguire tutte le azioni.<br/><br/> Se si usa una sottoscrizione esistente e non si ha il ruolo di amministratore, è necessario rivolgersi all'amministratore per l'assegnazione delle autorizzazioni di proprietario o collaboratore.
**Infrastruttura di Azure** | [Informazioni](./contoso-migration-infrastructure.md) sul modo in cui Contoso configura un'infrastruttura di Azure.

<!--markdownlint-enable MD033 -->

## <a name="scenario-steps"></a>Passaggi dello scenario

Ecco in che modo Contoso eseguirà la migrazione:

> [!div class="checklist"]
>
> - **Passaggio 1: effettuare il provisioning di un'istanza del database SQL in Azure.** Contoso esegue il provisioning di un'istanza SQL in Azure. Dopo la migrazione del sito Web dell'app in Azure, l'app web del servizio WCF punta a questa istanza.
> - **Passaggio 2: eseguire la migrazione del database con DMA.** Contoso esegue la migrazione del database dell'app con Data Migration Assistant.
> - **Passaggio 3: eseguire il provisioning di app Web.** Contoso esegue il provisioning di due app Web.
> - **Passaggio 4: configurare Azure DevOps.** Contoso crea un nuovo progetto di Azure DevOps e importa il repository Git.
> - **Passaggio 5: configurare le stringhe di connessione.** Contoso configura le stringhe di connessione in modo che l'app Web di livello Web, l'app Web del servizio WCF e l'istanza SQL siano in grado di comunicare.
> - **Passaggio 6: configurare le pipeline di compilazione e rilascio.** Come passaggio finale, Contoso configura pipeline di compilazione e versione per creare l'app e le distribuisce in due app Web di separate.

## <a name="step-1-provision-an-azure-sql-database"></a>Passaggio 1: Effettuare il provisioning del database SQL di Azure

1. Gli amministratori di Contoso scelgono di creare un database SQL di Azure.

    ![Effettuare il provisioning di SQL](media/contoso-migration-refactor-web-app-sql/provision-sql1.png)

2. Specificano un nome di database in modo che corrisponda al database in esecuzione nella macchina virtuale locale (**SmartHotel.Registration**). Il database viene posizionato nel gruppo di risorse ContosoRG. Si tratta del gruppo di risorse usato per le risorse di produzione in Azure.

    ![Effettuare il provisioning di SQL](media/contoso-migration-refactor-web-app-sql/provision-sql2.png)

3. Viene configurata una nuova istanza di SQL Server (**sql-smarthotel-eus2**) nell'area primaria.

    ![Effettuare il provisioning di SQL](media/contoso-migration-refactor-web-app-sql/provision-sql3.png)

4. Viene impostato il piano tariffario in modo che soddisfi le esigenze del server e del database. Inoltre, Contoso sceglie di risparmiare denaro con Vantaggio Azure Hybrid poiché si dispone già di una licenza di SQL Server.
5. Per il ridimensionamento si procede all'acquisto basato su v-Core-e si impostano i limiti per i requisiti previsti.

    ![Effettuare il provisioning di SQL](media/contoso-migration-refactor-web-app-sql/provision-sql4.png)

6. Quindi si crea l'istanza del database.

    ![Effettuare il provisioning di SQL](media/contoso-migration-refactor-web-app-sql/provision-sql5.png)

7. Dopo la creazione dell'istanza, avviene l'apertura del database e l'annotazione di dettagli necessari per eseguire la migrazione usando Data Migration Assistant.

    ![Effettuare il provisioning di SQL](media/contoso-migration-refactor-web-app-sql/provision-sql6.png)

**Ulteriore assistenza?**

- Sono disponibili [informazioni](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal) per il provisioning di un database SQL di Microsoft Azure.
- [Informazioni](https://docs.microsoft.com/azure/sql-database/sql-database-vcore-resource-limits-elastic-pools) sui limiti delle risorse basate su v-Core.

## <a name="step-2-migrate-the-database-with-dma"></a>Passaggio 2: Eseguire la migrazione del database con DMA

Gli amministratori di Contoso eseguiranno la migrazione del database SmartHotel360 tramite DMA.

### <a name="install-dma"></a>Installare DMA

1. Scarica lo strumento dal [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53595) nella VM di SQL Server locale (**SQLVM**).
2. Esegue il programma di installazione (DownloadMigrationAssistant.msi) nella VM.
3. Nella pagina **Fine** si seleziona **Avvia Microsoft Data Migration Assistant** prima di completare la procedura guidata.

### <a name="migrate-the-database-with-dma"></a>Eseguire la migrazione del database tramite DMA

1. In DMA viene creato un nuovo progetto (**SmartHotelDB**) e viene selezionata l'opzione **Migrazione**.
2. Viene specificato il tipo di server di origine come **SQL Server** e la destinazione come **Database SQL di Azure**.

    ![DMA](media/contoso-migration-refactor-web-app-sql/dma-1.png)

3. Nei dettagli della migrazione, viene aggiunto **SQLVM** come server di origine e **SmartHotel.Registration** come database.

     ![DMA](media/contoso-migration-refactor-web-app-sql/dma-2.png)

4. Viene ricevuto un errore che sembra essere associato con l'autenticazione. Dopo aver ricercato la causa, il problema risulta essere il punto (.) nel nome del database. Come soluzione alternativa, per risolvere il problema si decide di eseguire il provisioning di un nuovo database SQL usando il nome **SmartHotell-Registration**. Quando si esegue nuovamente DMA, è possibile selezionare **SmartHotel-Registration** e continuare la procedura guidata.

    ![DMA](media/contoso-migration-refactor-web-app-sql/dma-3.png)

5. In **Seleziona oggetti**, Contoso seleziona le tabelle di database e genera uno script SQL.

    ![DMA](media/contoso-migration-refactor-web-app-sql/dma-4.png)

6. Una volta che il Servizio Data Migration Assistant crea lo script, selezionare **Distribuisci schema**.

    ![DMA](media/contoso-migration-refactor-web-app-sql/dma-5.png)

7. DMA conferma che la distribuzione è stata completata.

    ![DMA](media/contoso-migration-refactor-web-app-sql/dma-6.png)

8. A questo punto, si avvia la migrazione.

    ![DMA](media/contoso-migration-refactor-web-app-sql/dma-7.png)

9. Al termine della migrazione, gli amministratori di Contoso possono verificare che il database sia in esecuzione nell'istanza di Azure SQL.

    ![DMA](media/contoso-migration-refactor-web-app-sql/dma-8.png)

10. Elimina il database SQL aggiuntivo **SmartHotel.Registration** nel portale di Azure.

    ![DMA](media/contoso-migration-refactor-web-app-sql/dma-9.png)

## <a name="step-3-provision-web-apps"></a>Passaggio 3: effettuare il provisioning di app Web

Dopo la migrazione del database, gli amministratori di Contoso possono eseguire il provisioning delle due app Web.

1. Seleziona **App Web** nel portale.

    ![App Web](media/contoso-migration-refactor-web-app-sql/web-app1.png)

2. Fornisce un nome dell'app (**SHWEB EUS2**), esegue il provisioning in Windows e lo posiziona in gruppo di risorse di produzione **ContosoRG**. Creano una nuova app Web e un piano di Servizio app di Azure.

    ![App Web](media/contoso-migration-refactor-web-app-sql/web-app2.png)

3. Dopo il provisioning dell'app Web, ripete il processo per creare un'app web per il servizio WCF (**SHWCF EUS2**)

    ![App Web](media/contoso-migration-refactor-web-app-sql/web-app3.png)

4. Una volta completato, passa all'indirizzo delle app per controllare che siano state create correttamente.

## <a name="step-4-set-up-azure-devops"></a>Passaggio 4: Configurare Azure DevOps

Contoso deve creare l'infrastruttura DevOps e le pipeline per l'applicazione. A tale scopo, gli amministratori di Contoso creano un nuovo progetto DevOps, importano il codice e quindi configurano le pipeline di compilazione e versione.

1. Nell'account Azure DevOps di Contoso creano un nuovo progetto (**ContosoSmartHotelRefactor**) e selezionano **GIT** per il controllo della versione.

    ![Nuovo progetto](./media/contoso-migration-refactor-web-app-sql/vsts1.png)

2. Importano il repository GIT che attualmente contiene il codice dell'app. Si trova in un [repository pubblico](https://github.com/Microsoft/SmartHotel360-internal-booking-apps) ed è possibile scaricarlo.

    ![Scaricare il codice dell'app](./media/contoso-migration-refactor-web-app-sql/vsts2.png)

3. Dopo aver importato il codice, connettono Visual Studio al repository e clonano il codice con Team Explorer.

    ![Connettersi al progetto](./media/contoso-migration-refactor-web-app-sql/devops1.png)

4. In seguito alla clonazione del repository nel computer dello sviluppatore, aprono il file della soluzione per l'app. L'app Web e il servizio wcf hanno entrambi un progetto distinto nel file.

    ![File di soluzione](./media/contoso-migration-refactor-web-app-sql/vsts4.png)

## <a name="step-5-configure-connection-strings"></a>Passaggio 5: Configurare le stringhe di connessione

Gli amministratori di Contoso devono verificare che le app Web e il database siano in grado di comunicare. A tale scopo, configura le stringhe di connessione nel codice e nelle app Web.

1. Nell'app Web per il servizio WCF (**SHWCF EUS2**) > **Impostazioni** > **Impostazioni applicazione**, aggiunge una nuova stringa di connessione denominata  **DefaultConnection**.
2. La stringa di connessione viene spostata dal database **SmartHotel registrazione** e deve essere aggiornata con le credenziali corrette.

    ![Stringa di connessione](media/contoso-migration-refactor-web-app-sql/string1.png)

3. Con Visual Studio, si apre il progetto **SmartHotel.Registration.wcf** dal file di soluzione. La sezione **connectionStrings** del file di configurazione Web per il servizio WCF SmartHotel.Registration.Wcf deve essere aggiornata con la stringa di connessione.

     ![Stringa di connessione](media/contoso-migration-refactor-web-app-sql/string2.png)

4. La sezione **client** del file Web di configurazione per SmartHotel.Registration.Web deve essere modificata in modo da puntare al nuovo percorso del servizio WCF. Si tratta dell'URL dell'app web WCF che ospita l'endpoint del servizio.

    ![Stringa di connessione](media/contoso-migration-refactor-web-app-sql/strings3.png)

5. Dopo che le modifiche sono state apportate al codice, gli amministratori devono eseguire il commit delle modifiche. Il commit e la sincronizzazione vengono eseguiti tramite Team Explorer in Visual Studio.

## <a name="step-6-set-up-build-and-release-pipelines-in-azure-devops"></a>Passaggio 6: Configurare pipeline di compilazione e di versione in Azure DevOps

Gli amministratori di Contoso configurano ora Azure DevOps per eseguire il processo di compilazione e versione.

1. In Azure DevOps selezionano **Compilazione e versione** > **Nuova pipeline**.

    ![Nuova pipeline](./media/contoso-migration-refactor-web-app-sql/pipeline1.png)

2. Selezionano **GIT Azure Repos** e il repository pertinente.

    ![GIT e repository](./media/contoso-migration-refactor-web-app-sql/pipeline2.png)

3. In **Seleziona un modello** gli amministratori selezionano il modello ASP.NET per la compilazione.

     ![Modello ASP.NET](./media/contoso-migration-refactor-web-app-sql/pipeline3.png)

4. Il nome **ContosoSmartHotelRefactor-ASP.NET-CI** viene usato per la compilazione. Fanno clic su **Salva e accoda**.

     ![Salva e accoda](./media/contoso-migration-refactor-web-app-sql/pipeline4.png)

5. In questo modo viene avviata la prima compilazione. Gli amministratori selezionano il numero di build per visualizzare il processo. Dopo il completamento possono vedere i suggerimenti del processo e selezionare **Artefatti** per esaminare i risultati della compilazione.

    ![Verifica](./media/contoso-migration-refactor-web-app-sql/pipeline5.png)

6. La cartella **Drop** (Rilascio) contiene i risultati della compilazione.

    - I due file con estensione due zip sono i pacchetti che contengono le app.
    - Tali file vengono usati nella pipeline di versione per la distribuzione in Servizio app di Azure.

     ![Elemento](./media/contoso-migration-refactor-web-app-sql/pipeline6.png)

7. Gli amministratori selezionano **Versioni** >  **+Nuova pipeline**.

    ![Nuova pipeline](./media/contoso-migration-refactor-web-app-sql/pipeline7.png)

8. Selezionano il modello di distribuzione di Servizio app di Azure.

    ![Modello di distribuzione di Servizio app di Azure](./media/contoso-migration-refactor-web-app-sql/pipeline8.png)

9. Gli amministratori assegnano un nome alla pipeline di versione **ContosoSmartHotel360Refactor** e specificano il nome dell'app Web WCF (SHWCF-EUS2) per il nome della **Fase**.

    ![Ambiente](./media/contoso-migration-refactor-web-app-sql/pipeline9.png)

10. Nelle fasi fanno clic su **1 processo, 1 attività** per configurare la distribuzione del servizio WCF.

    ![Distribuire WCF](./media/contoso-migration-refactor-web-app-sql/pipeline10.png)

11. Verificano che la sottoscrizione sia selezionata e autorizzata e selezionano **Nome del servizio app**.

     ![Selezionare il nome del servizio app](./media/contoso-migration-refactor-web-app-sql/pipeline11.png)

12. Sulla pipeline > **Artifacts** (Artefatti) selezionano **+Add an artifact** (+Aggiungi artefatto) e scelgono di eseguire la compilazione con la pipeline **ContosoSmarthotel360Refactor**.

     ![Creare](./media/contoso-migration-refactor-web-app-sql/pipeline12.png)

13. Gli amministratori fanno clic sull'icona a forma di fulmine sull'artefatto selezionato per abilitare il trigger di distribuzione continua.

     ![Fulmine](./media/contoso-migration-refactor-web-app-sql/pipeline13.png)

14. Si noti anche che il trigger di distribuzione continua deve essere impostato su **Attivato**.

    ![Distribuzione continua abilitata](./media/contoso-migration-refactor-web-app-sql/pipeline14.png)

15. A questo punto, ritornano alla fase 1 processo, 1 attività e fanno clic su **Distribuisci Servizio app di Azure**.

    ![Distribuire Servizio app di Azure](./media/contoso-migration-refactor-web-app-sql/pipeline15.png)

16. In **Seleziona un file o una cartella** individuano il file **SmartHotel.Registration.Wcf.zip** creato durante la compilazione e fanno clic su **Salva**.

    ![Salvare WCF](./media/contoso-migration-refactor-web-app-sql/pipeline16.png)

17. Selezionano **Pipeline** > **Fasi** **+ Aggiungi** per aggiungere un ambiente per **SHWEB EUS2**. Selezionano un'altra distribuzione di Servizio app di Azure.

    ![Aggiungere l'ambiente](./media/contoso-migration-refactor-web-app-sql/pipeline17.png)

18. Ripetono il processo di pubblicazione del file dell'app Web (**SmartHotel.Registration.Web.zip**) nell'app Web corretta.

    ![Pubblicare l'app Web](./media/contoso-migration-refactor-web-app-sql/pipeline18.png)

19. Dopo il salvataggio, la pipeline di versione è analoga alla seguente.

     ![Riepilogo pipeline di versione](./media/contoso-migration-refactor-web-app-sql/pipeline19.png)

20. Gli amministratori si spostano su **Compila** e selezionano **Trigger** > **Abilita l'integrazione continua**. La pipeline viene abilitata in modo che, quando si esegue il commit delle modifiche nel codice, vengano implementate la compilazione e la versione.

    ![Abilitare l'integrazione continua](./media/contoso-migration-refactor-web-app-sql/pipeline20.png)

21. Fanno clic su **Salva e accoda** per eseguire la pipeline completa. Viene attivata una nuova compilazione che a sua volta crea la prima versione dell'app in Servizio app di Azure.

    ![Salvare la pipeline](./media/contoso-migration-refactor-web-app-sql/pipeline21.png)

22. Gli amministratori di Contoso possono seguire l'elaborazione della pipeline di compilazione e versione in Azure DevOps. Al termine della compilazione, viene avviata la versione.

    ![Compilare e rilasciare l'app](./media/contoso-migration-refactor-web-app-sql/pipeline22.png)

23. Al termine dell'esecuzione della pipeline, entrambi i siti sono stati distribuiti e l'app è operativa e in esecuzione online.

    ![Completare la versione](./media/contoso-migration-refactor-web-app-sql/pipeline23.png)

A questo punto, l'app è stata migrata in modo corretto in Azure.

## <a name="clean-up-after-migration"></a>Eseguire la pulizia dopo la migrazione

Dopo la migrazione, Contoso deve eseguire le operazioni di pulizia seguenti:

- Rimuovere le VM locali dall'inventario vCenter.
- Rimuovere le VM dai processi di backup locali.
- Aggiornare la documentazione interna per visualizzare i nuovi percorsi per l'app SmartHotel360. Mostrare il database come in esecuzione nel database SQL di Azure e il front-end in esecuzione nelle due app Web.
- Esaminare le risorse che interagiscono con le VM di cui sono state rimosse le autorizzazioni e aggiornare eventuali impostazioni o documenti pertinenti in base alla nuova configurazione.

## <a name="review-the-deployment"></a>Esaminare la distribuzione

Al termine della migrazione delle risorse in Azure, Contoso deve rendere pienamente operativa la nuova infrastruttura e proteggerla.

### <a name="security"></a>Sicurezza

- Contoso intende verificare che il nuovo database **SmartHotel-Registration** sia protetto. [Altre informazioni](https://docs.microsoft.com/azure/sql-database/sql-database-security-overview).
- In particolare, Contoso deve aggiornare le app Web per usare SSL con le autorizzazioni.

### <a name="backups"></a>Backup

- Contoso deve esaminare i requisiti di backup per il database SQL di Azure. [Altre informazioni](https://docs.microsoft.com/azure/sql-database/sql-database-automated-backups).
- Contoso ha anche bisogno di altre informazioni sulla gestione di backup e ripristini del database SQL. [Altre informazioni](https://docs.microsoft.com/azure/sql-database/sql-database-automated-backups) sui backup automatici.
- Contoso deve considerare l'implementazione di gruppi di failover per fornire un failover al database a livello di area. [Altre informazioni](https://docs.microsoft.com/azure/sql-database/sql-database-geo-replication-overview).
- Contoso considera la distribuzione dell'app Web nelle regione principale Stati Uniti orientali 2 e Stati Uniti centrali per la resilienza. Contoso può configurare Gestione traffico per garantire il failover in caso di interruzioni a livello di area.

### <a name="licensing-and-cost-optimization"></a>Licenze e ottimizzazione dei costi

- Dopo che tutte le risorse vengono distribuite, Contoso deve assegnare i tag di Azure in base alla [pianificazione dell'infrastruttura](./contoso-migration-infrastructure.md#set-up-tagging).
- Tutte le licenze includono il costo dei servizi PaaS di cui si serve Contoso. Questo verrà dedotto dal contratto Enterprise.
- Abiliterà Gestione costi di Azure, concesso in licenza da Cloudyn, un'affiliata Microsoft. Si tratta di una soluzione di gestione dei costi multi-cloud che consente di usare e gestire Azure e altre risorse cloud. Vedere [questo articolo](https://docs.microsoft.com/azure/cost-management/overview) per altre informazioni su Gestione costi di Azure.

## <a name="conclusion"></a>Conclusione

In questo articolo Contoso ha effettuato il refactoring dell'app SmartHotel360 in Azure tramite la migrazione della macchina virtuale front-end dell'app a due app Web di Servizio app di Azure. Il database di app è stato migrato a un database SQL di Azure.
