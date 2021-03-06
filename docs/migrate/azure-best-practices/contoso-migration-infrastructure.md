---
title: Distribuire un'infrastruttura di migrazione
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni sul modo in cui Contoso configura un'infrastruttura di Azure per la migrazione ad Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/1/2018
ms.topic: conceptual
ms.service: cloud-adoption-framework
ms.subservice: migrate
services: azure-migrate
ms.openlocfilehash: 44fb2e8d7fc71dfa676f5711ab50c2201d67f260
ms.sourcegitcommit: 50788e12bb744dd44da14184b3e884f9bddab828
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2019
ms.locfileid: "74160371"
---
# <a name="deploy-a-migration-infrastructure"></a>Distribuire un'infrastruttura di migrazione

Questo articolo illustra come la società fittizia Contoso prepara la propria infrastruttura locale per la migrazione, impostando un'infrastruttura Azure in preparazione per la migrazione e gestisce il business in un ambiente ibrido. Quando si usa questo esempio per pianificare le attività di migrazione dell'infrastruttura, tenere presente quanto segue:

- Si tratta di un'architettura di esempio specifica di Contoso. Esaminare le esigenze aziendali, la struttura e i requisiti tecnici della propria organizzazione quando si prendono decisioni importanti sull'infrastruttura per la progettazione delle sottoscrizioni o per l'architettura di rete.
- La necessità di disporre di tutti gli elementi descritti nell'articolo varia in base alla strategia di migrazione adottata. Ad esempio, in caso di creazione di sole app native per il cloud in Azure, potrebbe essere necessaria una struttura di rete meno complessa.

## <a name="overview"></a>Panoramica

Prima di eseguire la migrazione ad Azure, Contoso deve predisporre l'infrastruttura di Azure. In generale, Contoso deve considerare sei grandi aree:

> [!div class="checklist"]
>
> - **Passaggio 1: sottoscrizioni di Azure.** in che modo Contoso acquisterà Azure e interagirà con la piattaforma e i servizi di Azure?
> - **Passaggio 2: identità ibrida.** come gestirà e controllerà l'accesso alle risorse locali e di Azure dopo la migrazione? In che modo Contoso estenderà o migrerà la gestione delle identità al cloud?
> - **Passaggio 3: ripristino di emergenza e resilienza.** in che modo Contoso garantirà la resilienza delle app e dell'infrastruttura in caso di emergenze e interruzioni?
> - **Passaggio 4: rete.** in che modo Contoso deve progettare l'infrastruttura di rete e stabilire la connettività tra i data center locale e Azure?
> - **Passaggio 5: sicurezza.** In che modo proteggerà la distribuzione ibrida/Azure?
> - **Passaggio 6: governance.** in che modo Contoso manterrà allineata la distribuzione con i requisiti di sicurezza e di governance?

## <a name="before-you-start"></a>Prima di iniziare

Prima di iniziare a esaminare l'infrastruttura, è consigliabile leggere alcune informazioni generali sulle funzionalità di Azure affrontate in questo articolo:

- Sono disponibili diverse opzioni per l'acquisto dell'accesso ad Azure, tra cui la tariffa con pagamento in base al consumo, i Contratti Enterprise (EA) o le licenze Open di rivenditori di Microsoft o partner Microsoft noti come Cloud Solution Provider (CSP). Informazioni sulle [opzioni per l'acquisto](https://azure.microsoft.com/pricing/purchase-options) e sull'[organizzazione delle sottoscrizioni di Azure](https://azure.microsoft.com/blog/organizing-subscriptions-and-resource-groups-within-the-enterprise).
- È disponibile una panoramica della [gestione delle identità e degli accessi](https://www.microsoft.com/trustcenter/security/identity) di Azure, oltre a informazioni su [Azure Active Directory e sull'estensione di Active Directory locali nel cloud](https://docs.microsoft.com/azure/active-directory/identity-fundamentals). È anche disponibile un utile e-Book scaricabile sulla [gestione delle identità e degli accessi (IAM) in un ambiente ibrido](https://azure.microsoft.com/resources/hybrid-cloud-identity).
- Azure offre un'infrastruttura di rete affidabile con opzioni di connettività ibrida. È disponibile una panoramica delle [reti e del controllo di accesso di rete](https://docs.microsoft.com/azure/security/security-network-overview).
- È possibile consultare un'introduzione alla [sicurezza di Azure](https://docs.microsoft.com/azure/security/azure-security) e ottenere informazioni sulla creazione di un piano per la [governance](https://docs.microsoft.com/azure/security/governance-in-azure).

## <a name="on-premises-architecture"></a>Architettura locale

Ecco un diagramma che illustra l'infrastruttura locale corrente di Contoso.

 ![Architettura di Contoso](./media/contoso-migration-infrastructure/contoso-architecture.png)

- Contoso dispone di un data center principale nella città di New York, negli Stati Uniti orientali.
- Esistono anche tre filiali locali dislocate in tre località negli Stati Uniti.
- Il data center principale è connesso a Internet tramite connessione Metro Ethernet in fibra (500 Mbps).
- Ogni filiale è connessa in locale a Internet tramite connessioni aziendali, con tunnel VPN IPSec in uscita nel data center principale. In questo modo l'intera rete è connessa in modo permanente e la connettività Internet risulta ottimizzata.
- Il data center principale è completamente virtualizzato con VMware. Contoso dispone di due host di virtualizzazione ESXi 6.5, gestiti dal server vCenter 6.5.
- Contoso usa Active Directory per la gestione delle identità e server DNS nella rete interna.
- I controller di dominio nel data center vengono eseguiti in macchine virtuali VMware. Il controller di dominio nelle filiali locali vengono eseguiti in server fisici.

## <a name="step-1-buy-and-subscribe-to-azure"></a>Passaggio 1: Acquistare ed eseguire la sottoscrizione a Azure

Contoso deve decidere come acquistare Azure, architettare le sottoscrizioni e concedere in licenza servizi e risorse.

### <a name="buy-azure"></a>Acquistare Azure

Contoso seleziona un [Contratto Enterprise (EA)](https://azure.microsoft.com/pricing/enterprise-agreement), che prevede un impegno monetario anticipato ad Azure per consentire a Contoso di acquisire notevoli vantaggi, tra cui opzioni di fatturazione flessibili e prezzi ottimizzati.

- Contoso ha stimato la spesa annuale per Azure. Quando ha firmato il contratto, Contoso ha pagato per intero il primo anno.
- Contoso deve usare tutti gli impegni prima della fine dell'anno per non perderli.
- Se per qualche motivo Contoso supera l'impegno e spende un importo superiore, Microsoft le addebiterà la differenza.
- Eventuali costi sostenuti oltre l'impegno verranno addebitati alla stessa tariffa e alle stesse condizioni previste nel contratto con Contoso. Non sono previste penali per il superamento.

### <a name="manage-subscriptions"></a>Gestire le sottoscrizioni

Dopo il pagamento di Azure, Contoso deve decidere come gestire le sottoscrizioni di Azure. Poiché Contoso ha stipulato un EA, non sussistono limiti sul numero di sottoscrizioni di Azure configurabili.

- Un'iscrizione Enterprise di Azure definisce la forma e l'uso dei servizi di Azure all'interno di un'azienda e una struttura di governance di base.
- Per iniziare, Contoso ha determinato una struttura (nota come scaffolding aziendale) per l'iscrizione a Enterprise. Contoso ha usato [questo articolo](https://docs.microsoft.com/azure/azure-resource-manager/resource-manager-subscription-governance) per comprendere e progettare uno scaffolding.
- Per il momento, Contoso ha deciso di adottare un approccio funzionale alla gestione delle sottoscrizioni.
  - All'interno dell'azienda averà un unico reparto IT a controllo del budget di Azure. Si tratterà dell'unico gruppo con sottoscrizioni.
  - Contoso estenderà il modello in futuro, in modo che altri gruppi aziendali possano aderire come reparti all'iscrizione Enterprise.
  - Nel reparto IT Contoso ha strutturato due sottoscrizioni, Produzione e Sviluppo.
  - Se Contoso avrà bisogno di altre sottoscrizioni in futuro, dovrà gestire l'accesso, i criteri e la conformità per queste sottoscrizioni. A tale scopo Contoso introdurrà [gruppi di gestione di Azure](https://docs.microsoft.com/azure/azure-resource-manager/management-groups-overview) come livello aggiuntivo al di sopra delle sottoscrizioni.

  ![Struttura aziendale](./media/contoso-migration-infrastructure/enterprise-structure.png)

### <a name="examine-licensing"></a>Esaminare le licenze

Una volta configurate le sottoscrizioni, Contoso potrà esaminare le licenze Microsoft. La strategia di gestione delle licenze dipende dalle risorse che Contoso intende migrare ad Azure e dalla modalità di selezione e distribuzione delle VM e dei servizi di Azure.

#### <a name="azure-hybrid-benefit"></a>Vantaggio Azure Hybrid

In caso di distribuzione di VM in Azure, le immagini standard includono una licenza che prevede per Contoso un addebito per minuto di software usato. Tuttavia, Contoso è cliente Microsoft da lungo tempo e ha gestito contratti EA e licenze open con Software Assurance (SA).

Vantaggio Azure Hybrid offre un metodo conveniente per la migrazione di Contoso, consentendo di risparmiare sulle VM di Azure e sui carichi di lavoro SQL Server convertendo o riusando le licenze Windows Server Datacenter e Standard Edition coperte con Software Assurance. In questo modo Contoso può pagare una tariffa di calcolo di base inferiore per VM e SQL Server. [Altre informazioni](https://azure.microsoft.com/pricing/hybrid-benefit).

#### <a name="license-mobility"></a>Mobilità delle licenze

Mobilità delle licenze tramite Software Assurance fornisce ai clienti dei contratti multilicenza Microsoft come Contoso la flessibilità di distribuire le app server idonee con SA attivo in Azure. In questo modo non è necessario acquistare nuove licenze. Senza costi per la mobilità associati, le licenze esistenti possono essere facilmente distribuite in Azure. [Altre informazioni](https://azure.microsoft.com/pricing/license-mobility).

#### <a name="reserve-instances-for-predictable-workloads"></a>Riservare istanze per carichi di lavoro prevedibili

I carichi di lavoro prevedibili devono essere sempre disponibili con VM in esecuzione. Ad esempio, applicazioni line-of-business come un sistema ERP SAP. D'altra parte, i carichi di lavoro imprevedibili sono quelli variabili, ad esempio le macchine virtuali attive quando la domanda è elevata e quelle disattivate quando la domanda è bassa.

![Istanza riservata](./media/contoso-migration-infrastructure/reserved-instance.png)

Anziché usare istanze riservate per specifiche istanze di VM che dovrà sottoporre a manutenzione per lunghi periodi, Contoso può ottenere uno sconto e capacità in ordine di priorità. Grazie alle [istanze riservate di Azure](https://azure.microsoft.com/pricing/reserved-vm-instances), unitamente a Vantaggio Azure Hybrid, Contoso può risparmiare fino all'82% sui prezzi normali con pagamento in base al consumo (aprile 2018).

## <a name="step-2-manage-hybrid-identity"></a>Passaggio 2: Gestire l'identità ibrida

Fornire e controllare l'accesso utente alle risorse di Azure con la gestione delle identità e degli accessi (IAM) è essenziale nell'assemblaggio di un'infrastruttura Azure.

- Contoso decide di estendere gli account Active Directory locali nel cloud, anziché creare un nuovo sistema distinto in Azure.
- A tale scopo, crea un account Active Directory basato su Azure.
- Poiché Contoso non dispone di Office 365, deve eseguire il provisioning di un nuovo account Azure AD.
- Office 365 usa Azure AD per la gestione degli utenti. Se Contoso usasse Office 365, avrebbe già un tenant Azure AD da usare come directory primaria.
- [Altre informazioni](https://support.office.com/article/understanding-office-365-identity-and-azure-active-directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9) su Azure AD per Office 365 e su [come aggiungere una sottoscrizione](https://docs.microsoft.com/azure/active-directory/active-directory-how-subscriptions-associated-directory) a un tenant Azure AD esistente.

### <a name="create-an-azure-ad"></a>Creare Azure AD

Contoso usa l'edizione Azure Active Directory Free inclusa con una sottoscrizione di Azure. Gli amministratori Contoso configurano una directory come segue:

1. Nel [portale di Azure](https://portal.azure.com) si passa a **Crea una risorsa** > **Identità** > **Azure Active Directory**.
2. In **Crea directory** specificano un nome per la directory, un nome di dominio iniziale e l'area in cui deve essere creata la directory di Azure AD.

    ![Creare Azure AD](./media/contoso-migration-infrastructure/azure-ad-create.png)

    > [!NOTE]
    > La directory creata include un nome di dominio iniziale in formato **nomedominio.onmicrosoft.com**. Il nome non può essere modificato o eliminato. Contoso deve invece aggiungere il nome di dominio registrato ad Azure AD.

### <a name="add-the-domain-name"></a>Aggiungere il nome di dominio

Per usare il nome di dominio standard, gli amministratori Contoso devono aggiungerlo come nome di dominio personalizzato ad Azure AD. Questa opzione consente loro di assegnare nomi utente familiari. Ad esempio, un utente può accedere con l'indirizzo di posta elettronica billg@contoso.com, anziché con billg@contosomigration.microsoft.com.

Per impostare il nome di dominio personalizzato, lo aggiunge alla directory, aggiunge una voce DNS e verifica il nome in Azure AD.

1. In **Nomi di dominio personalizzati** > **Aggiungi dominio personalizzato** aggiunge il dominio.
2. Per usare una voce DNS, deve registrarla con il registrar di dominio.

    - Nell'elenco **Nomi di dominio personalizzati** prende nota delle informazioni DNS per il nome. Si usa una voce MX.
    - A tale scopo, deve poter accedere al Domain Name Server. L'azienda ha eseguito l'accesso al dominio Contoso.com e creato un nuovo record MX per la voce DNS fornita da Azure AD usando i dettagli di cui ha preso nota.

3. In seguito alla propagazione dei record DNS, nel nome dettagliato del dominio selezionano **Verifica** per controllare il nome di dominio personalizzato.

     ![DNS di Azure AD](./media/contoso-migration-infrastructure/azure-ad-dns.png)

### <a name="set-up-on-premises-and-azure-groups-and-users"></a>Configurare gruppi e utenti locali e di Azure

Ora che Azure AD è in esecuzione, gli amministratori di Contoso devono aggiungere dipendenti ai gruppi di Active Directory locali che eseguiranno la sincronizzazione con Azure Active Directory. Devono usare nomi di gruppi locali che corrispondono ai nomi dei gruppi di risorse in Azure. In questo modo è più semplice identificare le corrispondenze ai fini della sincronizzazione.

#### <a name="create-resource-groups-in-azure"></a>Creare gruppi di risorse in Azure

I gruppi di risorse di Azure raccolgono le risorse di Azure. L'uso di un ID gruppo di risorse consente ad Azure di eseguire operazioni sulle risorse all'interno del gruppo.

- Una sottoscrizione di Azure può avere più gruppi di risorse, ma un gruppo di risorse può essere presente in una sola sottoscrizione.
- Inoltre, un singolo gruppo di risorse può avere più risorse, ma una risorsa può appartenere solo a un singolo gruppo di risorse.

Gli amministratori Contoso configurano i gruppi di risorse di Azure, come riepilogato nella tabella seguente.

<!-- markdownlint-disable MD033 -->

**Gruppo di risorse** | **Dettagli**
--- | ---
**ContosoCobRG** | Questo gruppo contiene tutte le risorse correlate alla continuità aziendale. Include gli insiemi di credenziali che verranno usati da Contoso per il servizio Site Recovery e del servizio Backup di Azure.<br/><br/> Include anche le risorse usate per la migrazione, compresi Azure Migrate e il Servizio Migrazione del database di Azure.
**ContosoDevRG** | Questo gruppo contiene le risorse di sviluppo e test.
**ContosoFailoverRG** | Questo gruppo viene usato come destinazione per le risorse sottoposte a failover.
**ContosoNetworkingRG** | Questo gruppo contiene tutte le risorse di rete.
**ContosoRG** | Questo gruppo contiene le risorse correlate ai database e alle app di produzione.

<!-- markdownlint-disable MD026 -->

L'azienda crea gruppi di risorse come indicato di seguito:

1. Nel portale di Azure > **Gruppi di risorse**, aggiunge un gruppo.
2. Per ogni gruppo specifica un nome, la sottoscrizione a cui appartiene e l'area.
3. I gruppi di risorse vengono visualizzati nell'elenco **Gruppi di risorse**.

    ![Gruppi di risorse](./media/contoso-migration-infrastructure/resource-groups.png)

##### <a name="scale-resource-groups"></a>Ridimensionare i gruppi di risorse

In futuro, Contoso aggiungerà altri gruppi di risorse in base alle esigenze. Ad esempio, potrebbero definire un gruppo di risorse per ogni app o servizio, in modo che possano essere gestite e protette in modo indipendente.

#### <a name="create-matching-security-groups-on-premises"></a>Creare gruppi di sicurezza corrispondenti in locale

1. Nell'account Active Directory locale, gli amministratori Contoso impostano i gruppi di sicurezza con nomi che corrispondono a quelli dei gruppi di risorse di Azure.

    ![Gruppi di sicurezza di Active Directory locali](./media/contoso-migration-infrastructure/on-prem-ad.png)

2. Per motivi di gestione, crea un gruppo aggiuntivo che verrà aggiunto a tutti gli altri gruppi. Questo gruppo disporrà di diritti su tutti i gruppi di risorse in Azure. A questo gruppo verrà aggiunto un numero limitato di amministratori globali.

### <a name="synchronize-active-directory"></a>Sincronizzare Active Directory

Contoso intende fornire un'identità comune per l'accesso alle risorse locali e nel cloud. A tale scopo, integra gli account Active Directory locali in Azure AD. Con questo modello:

- Utenti e organizzazioni possono usufruire di una singola identità per l'accesso alle applicazioni locali e ai servizi cloud, come Office 365, o a migliaia di altri siti su Internet.
- Gli amministratori possono usare i gruppi in Active Directory per implementare il [Controllo degli accessi in base al ruolo](https://docs.microsoft.com/azure/role-based-access-control/role-assignments-portal) in Azure.

Per agevolare l'integrazione, Contoso usa lo [strumento Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect). Con l'installazione e la configurazione in un controller di dominio, lo strumento sincronizza le identità di Active Directory locali con Azure AD.

### <a name="download-the-tool"></a>Scaricare lo strumento

1. Nel portale di Azure, gli amministratori Contoso passano ad **Azure Active Directory** > **Azure AD Connect** e scarica la versione più recente dello strumento nel server usato per la sincronizzazione.

    ![Scaricare Azure AD Connect](./media/contoso-migration-infrastructure/download-ad-connect.png)

2. Avvia il file di installazione **AzureADConnect.msi** con **Usa impostazioni rapide**. Si tratta dell'installazione più comune, che può essere usata per una topologia a foresta singola con sincronizzazione dell'hash delle password per l'autenticazione.

    ![Procedura guidata di Azure AD Connect](./media/contoso-migration-infrastructure/ad-connect-wiz1.png)

3. In **Connessione ad Azure AD** specificano le credenziali per la connessione ad Azure AD (nel formato admin@contoso.com o admin@contoso.onmicrosoft.com).

    ![Procedura guidata di Azure AD Connect](./media/contoso-migration-infrastructure/ad-connect-wiz2.png)

4. In **Connessione a Servizi di dominio Active Directory** specificano le credenziali per la connessione ad Azure Active Directory (nel formato CONTOSO\admin o contoso.com\admin).

     ![Procedura guidata di Azure AD Connect](./media/contoso-migration-infrastructure/ad-connect-wiz3.png)

5. In **Pronto per la configurazione** selezionano **Avvia il processo di sincronizzazione al termine della configurazione** per avviare immediatamente la sincronizzazione. Quindi Contoso esegue l'installazione.

Si noti che:

- Contoso dispone di una connessione diretta ad Azure. Se l'account Active Directory locale è protetto da un proxy, leggere questo [articolo](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-troubleshoot-connectivity).

- Dopo la prima sincronizzazione, gli oggetti Active Directory locali sono visibili nella directory Azure AD.

    ![Active Directory locale in Azure](./media/contoso-migration-infrastructure/on-prem-ad-groups.png)

- Il team IT di Contoso è rappresentato in ogni gruppo, in base al ruolo.

    ![Membri di Active Directory locale in Azure](./media/contoso-migration-infrastructure/on-prem-ad-group-members.png)

### <a name="set-up-rbac"></a>Impostare il Controllo degli accessi in base al ruolo

Il [Controllo degli accessi in base al ruolo](https://docs.microsoft.com/azure/role-based-access-control/role-assignments-portal) di Azure consente la gestione specifica degli accessi per Azure. L'uso del Controllo degli accessi in base al ruolo permette di concedere agli utenti solo il livello di accesso necessario per eseguire le attività. L'utente assegna il ruolo Controllo degli accessi appropriato a utenti, gruppi e applicazioni a livello di ambito. L'ambito di un'assegnazione di ruolo può essere una sottoscrizione, un gruppo di risorse o una singola risorsa.

Gli amministratori Contoso ora assegnano ruoli ai gruppi di Active Directory sincronizzati in locale.

1. Nel gruppo di risorse **ControlCobRG** selezionano **Controllo di accesso (IAM)**  > **Aggiungi un'assegnazione di ruolo**.
2. In **Aggiungi un'assegnazione di ruolo** > **Ruolo** > **Collaboratore** selezionano il gruppo **ContosoCobRG** dall'elenco. Il gruppo viene visualizzato nell'elenco **Membri selezionati**.
3. Ripetono questa operazione con le stesse autorizzazioni per gli altri gruppi di risorse (ad eccezione di **ContosoAzureAdmins**), aggiungendo le autorizzazioni Collaboratore all'account che corrisponde al gruppo di risorse.
4. Per il gruppo **ContosoAzureAdmins** assegnano il ruolo **Proprietario**.

    ![Membri di Active Directory locale in Azure](./media/contoso-migration-infrastructure/on-prem-ad-groups.png)

## <a name="step-3-design-for-resiliency"></a>Passaggio 3: progettare per la resilienza

### <a name="set-up-regions"></a>Configurare le regioni

Le risorse di Azure vengono distribuite all'interno di aree.

- Le aree sono organizzate in sottoaree geografiche e il rispetto dei requisiti di residenza, sovranità, conformità e resilienza viene garantito entro limiti geografici.
- Un'area è composta da un set dei centri dati. Questi data center vengono distribuiti entro un perimetro definito dalla latenza e connessi tramite una rete regionale dedicata a bassa latenza.
- Ogni area di Azure è associata a un'altra area per la resilienza.
- Informazioni sulle [aree di Azure](https://azure.microsoft.com/global-infrastructure/regions)e sul [modo in cui vengono abbinate le aree](https://docs.microsoft.com/azure/best-practices-availability-paired-regions).

Contoso ha scelto gli Stati Uniti orientali 2 (in Virginia) come area primaria e gli Stati Uniti centrali (in Iowa) come area secondaria. Questa scelta è dettata da un paio di motivi:

- Il data center Contoso si trova a New York e l'azienda ha tenuto conto della latenza al più vicino data center.
- L'area degli Stati Uniti orientali 2 include tutti i servizi e i prodotti che Contoso deve usare. Non tutte le aree di Azure sono uguali in termini di prodotti e servizi disponibili. È possibile consultare [Prodotti di Azure in base all'area](https://azure.microsoft.com/global-infrastructure/services).
- Quella degli Stati Uniti centrali è l'area abbinata di Azure per gli Stati Uniti orientali 2.

Tenendo conto dell'ambiente ibrido, Contoso deve ora considerare come creare una strategia di resilienza e ripristino di emergenza nella progettazione dell'area. Su vasta scala, le strategie spaziano da una distribuzione in una singola area, che si basa sulle funzionalità della piattaforma di Azure come i domini di errore e le associazioni regionali per la resilienza, fino a un modello attivo/attivo completo in cui i servizi cloud e il database vengono distribuiti e usati dagli utenti di due aree.

Contoso ha optato per una via intermedia. Distribuirà le app e le risorse in un'area primaria e manterrà una copia completa dell'infrastruttura nell'area secondaria, in modo che possa agire da backup completo in caso di emergenza completa per l'app o di un errore nell'area.

### <a name="set-up-availability"></a>Configurazione della disponibilità

**Set di disponibilità:**

I set di disponibilità consentono di proteggere le app e i dati da un'interruzione di rete e hardware locale all'interno di un data center.

- I set di disponibilità distribuiscono le macchine virtuali di Azure su hardware fisici diversi all'interno di un data center.
- I domini di errore rappresentano l'hardware sottostante con una fonte di alimentazione e uno switch di rete comuni all'interno del data center. Le macchine virtuali in un set di disponibilità vengono distribuite in diversi domini di errore per ridurre al minimo le interruzioni dovute a un singolo errore hardware o di rete.
- Un dominio di aggiornamento rappresenta un hardware sottostante che può essere sottoposto a manutenzione oppure riavviato nello stesso momento. I set di disponibilità distribuiscono anche le macchine virtuali in più domini di aggiornamento per garantire che almeno un'istanza sia in esecuzione in qualsiasi momento.

Contoso implementa i set di disponibilità ogni volta che i carichi di lavoro della macchina virtuale richiedono una disponibilità elevata. [Altre informazioni](https://docs.microsoft.com/azure/virtual-machines/windows/manage-availability).

**Zone di disponibilità:**

Le zone di disponibilità consentono di proteggere le app e i dati dagli errori che interessano un intero data center all'interno di un'area.

- Ogni zona di disponibilità rappresenta una località fisica esclusiva all'interno di un'area di Azure.
- Ogni zona è costituita da uno o più data center dotati di impianti indipendenti per l'alimentazione, il raffreddamento e la connettività di rete.
- Sono presenti almeno tre zone separate in tutte le aree abilitate.
- La separazione fisica delle zone all'interno di un'area consente di proteggere le applicazioni e i dati da eventuali guasti del data center.

Contoso implementerà zone di disponibilità dal momento che le app richiedono scalabilità, alta disponibilità e resilienza. [Altre informazioni](https://docs.microsoft.com/azure/availability-zones/az-overview).

### <a name="set-up-backup"></a>Configurare il backup

**Backup di Azure:**

Backup di Azure consente di eseguire il backup e il ripristino dei dischi delle macchine virtuali di Azure.

- Backup di Azure consente backup automatici delle immagini del disco della macchina virtuale, archiviati in archiviazione di Azure.
- I backup sono coerenti con l'applicazione, garantendo che i dati di cui è stato eseguito il backup siano coerenti a livello di transazione e che le applicazioni avviino il post-ripristino.
- Backup di Azure supporta l'archiviazione con ridondanza locale per replicare più copie dei dati di backup in un data center, in caso di errore hardware locale.
- In caso di interruzione a livello di area, Backup di Azure supporta anche l'archiviazione con ridondanza geografica, replicando i dati di backup in un'area associata secondaria.
- Backup di Azure crittografa i dati in transito usando AES 256. I dati di backup inattivi sono crittografati usando la [crittografia del servizio di archiviazione.](https://docs.microsoft.com/azure/storage/common/storage-service-encryption)

Contoso userà Azure Backup con archiviazione con ridondanza geografica in tutte le macchine virtuali di produzione per garantire il backup dei dati del carico di lavoro e che i dati possono essere ripristinati rapidamente in caso di interruzione o di altre interruzioni. [Altre informazioni](https://docs.microsoft.com/azure/backup/backup-introduction-to-azure-backup).

### <a name="set-up-disaster-recovery"></a>Configurare il ripristino di emergenza

**Azure Site Recovery:**

Azure Site Recovery aiuta a garantire la continuità aziendale, mantenendo carichi di lavoro e app aziendali in esecuzione in caso di interruzioni a livello di area.

- Azure Site Recovery replica continuamente le macchine virtuali di Azure da un'area primaria a un'area secondaria, garantendo la copia funzionale in entrambe le posizioni.
- In caso di interruzione nell'area primaria, l'applicazione o il servizio esegue il failover all'uso delle istanze di macchine virtuali replicate nell'area secondaria, riducendo al minimo le potenziali interruzioni.
- Quando le operazioni tornano alla normalità, le applicazioni o i servizi possono eseguire il failback sulle macchine virtuali nell'area primaria.

Contoso implementerà Azure Site Recovery per tutte le macchine virtuali di produzione usate nei carichi di lavoro cruciali, assicurando un'interruzione minima durante un'interruzione nell'area primaria. [Ulteriori informazioni](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)

## <a name="step-4-design-a-network-infrastructure"></a>Passaggio 4: Progettare un'infrastruttura di rete

Una volta progettata l'area, Contoso è pronta considerare una strategia di rete. Deve capire in che modo il data center locale e Azure si connetteranno e comunicheranno tra loro e come progettare l'infrastruttura di rete in Azure. In particolare Contoso deve:

- **Pianificare una connettività di rete ibrida.** decidere come connettere le reti in locale e in Azure.
- **Progettare l'infrastruttura di rete di Azure.** decidere in che modo distribuire le reti nelle aree e in che modo le reti comunicheranno nella stessa area e tra aree diverse.
- **Progettare e configurare le reti di Azure.** configurare le reti e le subnet di Azure e decidere cosa si troverà al loro interno.

### <a name="plan-hybrid-network-connectivity"></a>Pianificare una connettività di rete ibrida

Contoso ha considerato una [serie di architetture](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking) per la rete ibrida tra Azure e il data center locale. Per altre informazioni, vedere [scegliere una soluzione per la connessione di una rete locale ad Azure](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/considerations).

Come promemoria, l'infrastruttura di rete locale di Contoso è attualmente costituita dal data center di New York e da filiali locali nell'area orientale degli Stati Uniti. Tutte le sedi dispongono di connessione aziendale a Internet. Ogni filiale è connessa al data center con un tunnel VPN IPSec tramite Internet.

![Rete di Contoso](./media/contoso-migration-infrastructure/contoso-networking.png)

Ecco in che modo Contoso ha deciso di implementare la connettività ibrida:

1. Ha configurato una nuova connessione VPN da sito a sito tra il data center di Contoso a New York e le due aree di Azure negli Stati Uniti orientali 2 e negli Stati Uniti centrali.
2. Il traffico delle filiali per le reti virtuali di Azure verrà instradato attraverso il data center principale di Contoso.
3. Nel momento in cui Contoso aumenta la distribuzione di Azure, stabilirà una connessione ExpressRoute tra i data center e le aree di Azure. In questo caso Contoso manterrà la connessione VPN da sito a sito solo a fini del failover.
    - [Altre informazioni](https://docs.microsoft.com/azure/architecture/reference-architectures/hybrid-networking/considerations) sulla scelta tra una soluzione ibrida VPN ed ExpressRoute.
    - Verificare le [sedi e il supporto ExpressRoute](https://docs.microsoft.com/azure/expressroute/expressroute-locations-providers).

**Solo VPN:**

![VPN di Contoso](./media/contoso-migration-infrastructure/hybrid-vpn.png)

**VPN ed ExpressRoute:**

![VPN Contoso/ExpressRoute](./media/contoso-migration-infrastructure/hybrid-vpn-expressroute.png)

### <a name="design-the-azure-network-infrastructure"></a>Progettare l'infrastruttura di rete di Azure

È essenziale che Contoso posizioni le reti in modo da rendere la distribuzione ibrida sicura e scalabile. A tale scopo, Contoso adotta un approccio a lungo termine e progetta reti virtuali resilienti e pronte per l'azienda. [Altre informazioni](https://docs.microsoft.com/azure/virtual-network/virtual-network-vnet-plan-design-arm) sulla pianificazione di reti virtuali.

Per connettere le due aree, Contoso ha deciso di implementare un modello di rete da hub a hub:

- In ogni area, Contoso userà un modello hub e spoke.
- Per connettere reti e hub, Contoso userà il peering di rete di Azure.

#### <a name="network-peering"></a>Peering di rete

Azure offre il peering di rete per connettere reti virtuali e hub. Il peering globale consente connessioni tra reti virtuali/hub in aree diverse. Il peering locale connette le reti virtuali nella stessa area. Il peering VNet offre diversi vantaggi:

- Il traffico di rete tra reti virtuali di cui è stato eseguito il peering è privato.
- Il traffico tra le reti virtuali viene mantenuto nella rete backbone Microsoft. Nella comunicazione tra le reti virtuali non sono necessari gateway, una rete Internet pubblica o la crittografia.
- Il peering offre una connessione predefinita a larghezza di banda elevata e bassa latenza tra le risorse in reti virtuali diverse.

[Altre informazioni](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview) sul peering di rete.

#### <a name="hub-to-hub-across-regions"></a>Da hub a hub tra regioni

Contoso distribuirà un hub in ogni area. Un hub è una rete virtuale in Azure che funge da punto di connettività centrale alla rete locale. Le reti virtuali dell'hub si connetteranno tra loro mediante peering globale. Il peering globale di reti virtuali connette le reti virtuali in diverse aree di Azure.

- L'hub in ogni regione è associato all'hub partner nell'altra regione.
- L'hub è associato a ogni rete nell'area e può connettersi a tutte le risorse di rete.

    ![Peering globale](./media/contoso-migration-infrastructure/global-peering.png)

#### <a name="hub-and-spoke-model-within-a-region"></a>Modello hub e spoke in un'area

All'interno di ogni area, Contoso distribuirà le reti virtuali per scopi diversi, come le reti spoke dall'hub dell'area. Le reti virtuali all'interno di un'area usano il peering connettersi all'hub e tra loro.

#### <a name="design-the-hub-network"></a>Progettare la rete dell'hub

All'interno del modello hub e spoke scelto da Contoso, l'azienda deve decidere come verrà instradato il traffico dal data center locale e da Internet. Ecco come Contoso ha deciso di gestire il routing per gli hub degli Stati Uniti orientali 2 e degli Stati Uniti centrali:

- Contoso progetta una rete nota come "reverse c", poiché si tratta del percorso che seguono i pacchetti dalla rete in ingresso a quella in uscita.
- L'architettura di rete prevede due limiti, una zona perimetrale front-end non attendibile e una zona back-end attendibile.
- Un firewall avrà una scheda di rete in ogni area per il controllo dell'accesso alle zone attendibili.
- Da Internet:
  - Il traffico Internet accede a un indirizzo IP pubblico con bilanciamento del carico nella rete perimetrale.
  - Il traffico viene instradato attraverso il firewall ed è soggetto alle regole del firewall.
  - Una volta implementati i controlli di accesso alla rete, il traffico verrà inoltrato alla posizione appropriata nella zona attendibile.
  - Il traffico in uscita dalla rete virtuale verrà instradato in Internet mediante route definite dall'utente. Il traffico viene forzato attraverso il firewall e controllato in linea con i criteri di Contoso.
- Dal data center di Contoso:
  - Il traffico in ingresso tramite VPN da sito a sito (ExpressRoute) accede all'indirizzo IP pubblico del gateway VPN di Azure.
  - Il traffico viene instradato attraverso il firewall ed è soggetto alle regole del firewall.
  - Dopo aver applicato le regole del firewall, il traffico verrà inoltrato a un bilanciamento del carico interno (SKU Standard) nella subnet della zona interna attendibile.
  - Il traffico in uscita dalla subnet attendibile verso il data center locale tramite VPN viene instradato attraverso il firewall e vengono applicate regole prima di attraversare la connessione VPN da sito a sito.

### <a name="design-and-set-up-azure-networks"></a>Progettare e configurare reti di Azure

Con una topologia di rete e routing, Contoso è pronta a configurare le reti e le subnet di Azure.

- Contoso implementerà una rete privata di classe A in Azure (da 0.0.0.0 a 127.255.255.255). La rete funzione, dal momento che l'azienda dispone in locale di uno spazio di indirizzi privato di classe B 172.160.0/16, quindi Contoso può essere certa che non si verificheranno sovrapposizioni tra gli intervalli di indirizzi.
- Intende distribuire le reti virtuali nelle aree primarie e secondarie.
- Contoso userà una convenzione di denominazione che include il prefisso **VNET** e l'abbreviazione **EUS2** o **CUS** per l'area. Con questo standard, le reti dell'hub verranno denominate **VNET-HUB-EUS2** (Stati Uniti orientali 2) e **VNET-HUB-CUS** (Stati Uniti centrali).
- Contoso non ha una [soluzione IPAM](https://docs.microsoft.com/windows-server/networking/technologies/ipam/ipam-top), quindi deve predisporre il routing di rete senza NAT.

#### <a name="virtual-networks-in-east-us-2"></a>Reti virtuali negli Stati Uniti orientali 2

Quella degli Stati Uniti orientali 2 è l'area primaria che Contoso userà per distribuire risorse e servizi. Ecco in che modo Contoso intende architettare le reti al suo interno:

- **Hub:** L'hub VNet in Stati Uniti orientali 2 è il punto centrale della connettività primaria al Data Center locale.
- **Reti virtuali:** Per isolare i carichi di lavoro, se necessario, è possibile usare spoke reti virtuali nell'area Stati Uniti orientali 2. Oltre alla rete virtuale dell'hub, Contoso avrà due reti virtuali spoke negli Stati Uniti orientali 2:
  - **VNET-DEV-EUS2**. Questa rete virtuale offre al team di sviluppo e test una rete completamente funzionale per i progetti di sviluppo. Verrà usata come area pilota di produzione e si baserà sull'infrastruttura di produzione.
    - **VNET-PROD-EUS2**. i componenti di produzione Azure IaaS si troveranno in questa rete.
  - Ogni rete virtuale avrà un proprio spazio di indirizzi univoco, senza sovrapposizioni. Contoso intende configurare il routing senza NAT.
- **Subnet:**
  - Sarà presente una subnet in ogni rete per ogni livello di app
  - Ogni subnet nella rete di produzione avrà una subnet corrispondente nella rete virtuale di sviluppo.
  - La rete di produzione ha anche una subnet per i controller di dominio.

Le reti virtuali negli Stati Uniti orientali 2 sono riepilogate nella tabella seguente.

**Rete virtuale** | **Range** | **Peer**
--- | --- | ---
**VNET-HUB-EUS2** | 10.240.0.0/20 | VNET-HUB-CUS2, VNET-DEV-EUS2, VNET-PROD-EUS2
**VNET-DEV-EUS2** | 10.245.16.0/20 | VNET-HUB-EUS2
**VNET-PROD-EUS2** | 10.245.32.0/20 | VNET-HUB-EUS2, VNET-PROD-CUS

![Modello hub e spoke nell'area primaria](./media/contoso-migration-infrastructure/primary-hub-peer.png)

#### <a name="subnets-in-the-east-us-2-hub-network-vnet-hub-eus2"></a>Subnet nella rete dell'hub degli Stati Uniti orientali 2 (VNET-HUB-EUS2)

**Subnet/zona** | **CIDR** | **Indirizzi IP utilizzabili
--- | --- | ---
**IB-UntrustZone** | 10.240.0.0/24 | 251
**IB-TrustZone** | 10.240.1.0/24 | 251
**OB-UntrustZone** | 10.240.2.0/24 | 251
**OB-TrustZone** | 10.240.3.0/24 | 251
**GatewaySubnets** | 10.240.10.0/24 | 251

#### <a name="subnets-in-the-east-us-2-dev-network-vnet-dev-eus2"></a>Subnet nella rete di sviluppo degli Stati Uniti orientali 2 (VNET-DEV-EUS2)

La rete virtuale di sviluppo viene usata dal team di sviluppo come area pilota di produzione. Include tre subnet.

**Subnet** | **CIDR** | **Indirizzi** | **Nella subnet**
--- | --- | --- | ---
**DEV-FE-EUS2** | 10.245.16.0/22 | 1019 | VM front-end/di livello Web
**DEV-APP-EUS2** | 10.245.20.0/22 | 1019 | VM livello app
**DEV-DB-EUS2** | 10.245.24.0/23 | 507 | VM database

#### <a name="subnets-in-the-east-us-2-production-network-vnet-prod-eus2"></a>Subnet nella rete di produzione degli Stati Uniti orientali 2 (VNET-PROD-EUS2)

I componenti Azure IaaS si trovano nella rete di produzione. Ogni livello dell'app presenta una subnet specifica. Le subnet corrispondono a quelle nella rete di sviluppo, con l'aggiunta di una subnet per i controller di dominio.

**Subnet** | **CIDR** | **Indirizzi** | **Nella subnet**
--- | --- | --- | ---
**PROD-FE-EUS2** | 10.245.32.0/22 | 1019 | VM front-end/di livello Web
**PROD-APP-EUS2** | 10.245.36.0/22 | 1019 | VM livello app
**PROD-DB-EUS2** | 10.245.40.0/23 | 507 | VM database
**PROD-DC-EUS2** | 10.245.42.0/24 | 251 | VM controller di dominio

![Architettura di rete dell'hub](./media/contoso-migration-infrastructure/azure-networks-eus2.png)

#### <a name="virtual-networks-in-central-us-secondary-region"></a>Reti virtuali negli Stati Uniti centrali (area secondaria)

Quella degli Stati Uniti centrali è l'area secondaria di Contoso. Ecco in che modo Contoso intende architettare le reti al suo interno:

- **Hub:** L'hub VNet in Stati Uniti orientali 2 è il punto centrale di connettività al Data Center locale e il reti virtuali spoke nell'area Stati Uniti orientali 2 può essere usato per isolare i carichi di lavoro, se necessario, gestiti separatamente dagli altri spoke.
- **Reti virtuali:** Contoso avrà due reti virtuali negli Stati Uniti centrali:
  - VNET-PROD-CUS. Questa rete virtuale è una rete di produzione, simile a VNET-PROD_EUS2.
  - VNET-ASR-CUS. Questa rete virtuale verrà usata come posizione in cui creare le VM dopo il failover da locale o come posizione per le VM di Azure di cui è stato effettuato il failover dall'area primaria all'area secondaria. Questa rete è simile alle reti di produzione, ma è sprovvista di controller di dominio.
  - Ogni rete virtuale nell'area avrà un proprio spazio di indirizzi, senza sovrapposizioni. Contoso configurerà il routing senza NAT.
- **Subnet:** Le subnet verranno progettate in modo analogo a quelle negli Stati Uniti orientali 2. ad eccezione del fatto che per Contoso non sarà necessaria una subnet per i controller di dominio.

Le reti virtuali negli Stati Uniti centrali sono riepilogate nella tabella seguente.

**Rete virtuale** | **Range** | **Peer**
--- | --- | ---
**VNET-HUB-CUS** | 10.250.0.0/20 | VNET-HUB-EUS2, VNET-ASR-CUS, VNET-PROD-CUS
**VNET-ASR-CUS** | 10.255.16.0/20 | VNET-HUB-CUS, VNET-PROD-CUS
**VNET-PROD-CUS** | 10.255.32.0/20 | VNET-HUB-CUS, VNET-ASR-CUS, VNET-PROD-EUS2

![Modello hub e spoke nell'area accoppiata](./media/contoso-migration-infrastructure/paired-hub-peer.png)

#### <a name="subnets-in-the-central-us-hub-network-vnet-hub-cus"></a>Subnet nella rete dell'hub degli Stati Uniti centrali (VNET-HUB-CUS)

**Subnet** | **CIDR** | **Indirizzi IP utilizzabili**
--- | --- | ---
**IB-UntrustZone** | 10.250.0.0/24 | 251
**IB-TrustZone** | 10.250.1.0/24 | 251
**OB-UntrustZone** | 10.250.2.0/24 | 251
**OB-TrustZone** | 10.250.3.0/24 | 251
**GatewaySubnet** | 10.250.2.0/24 | 251

#### <a name="subnets-in-the-central-us-production-network-vnet-prod-cus"></a>Subnet nella rete di produzione degli Stati Uniti centrali (VNET-PROD-CUS)

In parallelo con la rete di produzione nell'area primaria Stati Uniti orientali 2, è presente una rete di produzione nell'area Stati Uniti centrali secondari.

**Subnet** | **CIDR** | **Indirizzi** | **Nella subnet**
--- | --- | --- | ---
**PROD-FE-CUS** | 10.255.32.0/22 | 1019 | Macchine virtuali front-end/di livello Web
**PROD-APP-CUS** | 10.255.36.0/22 | 1019 | VM livello app
**PROD-DB-CUS** | 10.255.40.0/23 | 507 | VM database
**PROD-DC-CUS** | 10.255.42.0/24 | 251 | VM controller di dominio

#### <a name="subnets-in-the-central-us-failoverrecovery-network-in-central-us-vnet-asr-cus"></a>Subnet nella rete di failover/recupero negli Stati Uniti centrali (VNET-ASR-CUS)

La rete VNET-ASR-CUS viene usata a scopo di failover tra le aree. Verrà usato Site Recovery per la replica e il failover delle VM di Azure tra le aree. Funge anche da data center di Contoso per la rete di Azure per i carichi di lavoro protetti che rimangono in locale, ma vengono sottoposti a failover in Azure per il ripristino di emergenza.

VNET-ASR-CUS è la stessa subnet di base della rete virtuale di produzione negli Stati Uniti orientali 2, ma senza richiedere una subnet per i controller di produzione.

**Subnet** | **CIDR** | **Indirizzi** | **Nella subnet**
--- | --- | --- | ---
**ASR-FE-CUS** | 10.255.16.0/22 | 1019 | Macchine virtuali front-end/di livello Web
**ASR-APP-CUS** | 10.255.20.0/22 | 1019 | VM livello app
**ASR-DB-CUS** | 10.255.24.0/23 | 507 | VM database

![Architettura di rete dell'hub](./media/contoso-migration-infrastructure/azure-networks-cus.png)

#### <a name="configure-peered-connections"></a>Configurare connessioni con peering

L'hub in ogni area verrà associato all'hub nell'altra area e a tutte le reti virtuali all'interno dell'area dell'hub. In questo modo gli hub potranno comunicare e visualizzare tutte le reti virtuali all'interno di un'area. Si noti che:

- Il peering crea una connessione doppia, una dal peer di avvio sulla prima rete virtuale e un'altra sulla seconda rete virtuale.
- In una distribuzione ibrida, il traffico tra i peer deve essere visibile dalla connessione VPN tra il data center locale e Azure. A tale scopo, è necessario configurare alcune impostazioni specifiche sulle connessioni con peering.

Per qualsiasi connessione dalle reti virtuali spoke attraverso l'hub al data center locale, Contoso deve consentire l'inoltro del traffico e attraversare i gateway VPN.

##### <a name="domain-controller"></a>Controller di dominio

Per i controller di dominio nella rete VNET-PROD-EUS2, Contoso vuole indirizzare sia il traffico tra la rete di produzione e l'hub EUS2 sia la connessione VPN in locale. Per fare questo, gli amministratori Contoso devono permettere quanto segue:

1. **Consenti traffico inoltrato** e **Consenti transito gateway** sulla connessione con peering. In questo esempio si tratta della connessione da VNET-HUB-EUS2 a VNET-PROD-EUS2.

    ![Peering](./media/contoso-migration-infrastructure/peering1.png)

2. **Consenti traffico inoltrato** e **Usa gateway remoti** sull'altro lato del peering, nella connessione da VNET-PROD-EUS2 a VNET-HUB-EUS2.

    ![Peering](./media/contoso-migration-infrastructure/peering2.png)

3. In locale l'azienda configura una route statica che indirizza il traffico attraverso il tunnel VPN alla rete virtuale. La configurazione verrà completata nel gateway che fornisce il tunnel VPN da Contoso ad Azure. Per questa operazione viene usato RRAS.

    ![Peering](./media/contoso-migration-infrastructure/peering3.png)

##### <a name="production-networks"></a>Reti di produzione

Una rete di peer con spoke non può visualizzarne un'altra in un'altra regione tramite un hub.

Affinché le reti di produzione di Contoso possano visualizzarsi a vicenda in entrambe le aree, gli amministratori Contoso devono creare una connessione con peering diretta per VNET-PROD-EUS2 e VENT-PROD-CUS.

![Peering](./media/contoso-migration-infrastructure/peering4.png)

### <a name="set-up-dns"></a>Configurare DNS

In caso di distribuzione di risorse in reti virtuali, per la risoluzione dei nomi di dominio sono disponibili due opzioni. È possibile usare la risoluzione dei nomi fornita da Azure oppure fornire server DNS per la risoluzione. Il tipo di risoluzione dei nomi usato dipende dal modo in cui le risorse devono comunicare tra loro. [Altre informazioni](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances#azure-provided-name-resolution) sul servizio DNS di Azure.

Gli amministratori Contoso hanno deciso che il servizio DNS di Azure non è una scelta ottimale per il proprio ambiente ibrido. Scelgono quindi di usare i server DNS locali.

- Poiché si tratta di una rete ibrida, tutte le VM in locale e in Azure devono essere in grado di risolvere i nomi. È quindi necessario applicare impostazioni DNS personalizzate a tutte le reti virtuali.
- Contoso ha attualmente distribuito controller di dominio nel suo data center e nelle filiali. I server DNS primari sono CONTOSODC1(172.16.0.10) e CONTOSODC2(172.16.0.1)
- Quando vengono distribuite le reti virtuali, i controller di dominio locali verranno configurati per essere usati come server DNS nelle reti.
- A tale scopo, se per la rete virtuale sono specificate impostazioni DNS personalizzate, è necessario aggiungere all'elenco DNS l'indirizzo IP dei resolver ricorsivi di Azure (ad esempio 168.63.129.16). Contoso configura le impostazioni del server DNS in ogni rete virtuale. Ad esempio, le impostazioni DNS personalizzate per la rete VNET-HUB-EUS2 saranno:

    ![DNS personalizzato](./media/contoso-migration-infrastructure/custom-dns.png)

Oltre ai controller di dominio locali, Contoso intende implementarne altri quattro per supportare le reti di Azure, due per ogni area. Ecco cosa distribuirà Contoso in Azure.

**Area** | **Controller di dominio** | **Rete virtuale** | **Subnet** | **Indirizzo IP**
--- | --- | --- | --- | ---
EUS2 | CONTOSODC3 | VNET-PROD-EUS2 | PROD-DC-EUS2 | 10.245.42.4
EUS2 | CONTOSODC4 | VNET-PROD-EUS2 | PROD-DC-EUS2 | 10.245.42.5
CUS | CONTOSODC5 | VNET-PROD-CUS | PROD-DC-CUS | 10.255.42.4
CUS | CONTOSODC6 | VNET-PROD-CUS | PROD-DC-CUS | 10.255.42.4

Dopo aver distribuito i controller di dominio locali, Contoso dovrà aggiornare le impostazioni di DNS nelle reti in una delle aree per includere i nuovi controller di dominio nell'elenco di server DNS.

#### <a name="set-up-domain-controllers-in-azure"></a>Configurare i controller di dominio in Azure

Dopo aver aggiornato le impostazioni di rete, gli amministratori Contoso sono pronti a creare i controller di dominio in Azure.

1. Nel portale di Azure distribuisce una nuova VM Windows Server nella rete virtuale appropriata.
2. Crea set di disponibilità in ogni posizione per la VM. I set di disponibilità:

    - Fanno in modo che l'infrastruttura di Azure separi le VM in infrastrutture distinte nell'area di Azure.
    - Garantiscono a Contoso l'idoneità del contratto di servizio al 99,95% per le VM in Azure. [Altre informazioni](https://docs.microsoft.com/azure/virtual-machines/windows/tutorial-availability-sets).

    ![Gruppo di disponibilità](./media/contoso-migration-infrastructure/availability-group.png)

3. Dopo aver distribuito la VM, apre l'interfaccia di rete per la VM. Viene impostato come statico l'indirizzo IP privato e specifica un indirizzo valido.

    ![Scheda NIC della VM](./media/contoso-migration-infrastructure/vm-nic.png)

4. A questo punto l'azienda collega un nuovo disco dati alla VM. Il disco contiene il database Active Directory e la condivisione sysvol.
    - Le dimensioni del disco determinano il numero di IOPS supportate.
    - Nel tempo le dimensioni del disco potrebbero dover aumentare contestualmente all'ambiente.
    - L'unità non deve essere impostata su Lettura/Scrittura per la memorizzazione nella cache dell'host. I database Active Directory non supportano questa condizione.

     ![Disco Active Directory](./media/contoso-migration-infrastructure/ad-disk.png)

5. Dopo aver aggiunto il disco, l'azienda si connette alla VM tramite Desktop remoto e apre Server Manager.

6. In **Servizi file e archiviazione** esegue la Procedura guidata Nuovo volume, verificando che all'unità sia assegnata la lettera F: o una lettera superiore nella VM locale.

     ![Procedura guidata Nuovo volume](./media/contoso-migration-infrastructure/volume-wizard.png)

7. In Server Manager aggiunge il ruolo **Active Directory Domain Services**. Configura la VM come controller di dominio.

      ![Ruolo server](./media/contoso-migration-infrastructure/server-role.png)

8. Dopo aver configurato la VM come controller di dominio e riavviato, apre Gestore DNS e configura il resolver DNS di Azure come server d'inoltro. In questo il controller di dominio può inoltrare le query DNS che non riesce a risolvere a DNS di Azure.

    ![Server d'inoltro DNS](./media/contoso-migration-infrastructure/dns-forwarder.png)

9. A questo punto, l'azienda aggiorna le impostazioni DNS personalizzate per ogni rete virtuale con il controller di dominio appropriato per l'area della rete virtuale. Nell'elenco include i controller di dominio locali.

### <a name="set-up-active-directory"></a>Configurare Active Directory

Active Directory è un servizio fondamentale nella rete e deve essere configurato correttamente. Gli amministratori Contoso creeranno altri siti Active Directory per il data center di Contoso e per le aree EUS2 e CUS.

1. Crea due nuovi siti (AZURE-EUS2 e AZURE-CUS) insieme al sito del data center (ContosoDatacenter).
2. Dopo aver creato i siti, creerà subnet al loro interno per la corrispondenza con le reti virtuali e il data center.

    ![Subnet di controller di dominio](./media/contoso-migration-infrastructure/dc-subnets.png)

3. Ora crea due collegamenti ai siti per connettere tutti gli elementi. I controller di dominio devono essere spostati nelle relative posizioni.

    ![Collegamenti ai controller di dominio](./media/contoso-migration-infrastructure/dc-links.png)

4. In seguito alla configurazione, la topologia di replica di Active Directory è pronta.

    ![Replica di controller di dominio](./media/contoso-migration-infrastructure/ad-resolution.png)

5. Al termine verrà visualizzato un elenco dei controller di dominio e dei siti nel Centro di amministrazione di Active Directory locale.

    ![Centro di amministrazione di Active Directory](./media/contoso-migration-infrastructure/ad-center.png)

## <a name="step-5-plan-for-governance"></a>Passaggio 5: Pianificare la governance

Azure offre una gamma di controlli di governance nei servizi e nella piattaforma di Azure. Per ulteriori informazioni, vedere le [Opzioni di governance di Azure](https://docs.microsoft.com/azure/security/governance-in-azure).

Nel momento in cui configura il controllo delle identità e degli accessi, Contoso ha già iniziato a implementare alcuni aspetti di governance e sicurezza. Su vasta scala, sono tre le aree che deve prendere in considerazione:

- **Criterio:** Criteri di Azure applica e impone regole ed effetti sulle risorse, in modo che le risorse restino conformi ai requisiti aziendali e ai contratti di contratto.
- **Blocchi:** Azure consente di bloccare sottoscrizioni, gruppi di risorse e altre risorse, in modo che possano essere modificate solo da quelli con autorità.
- **Tag:** È possibile controllare, controllare e gestire le risorse con i tag. I tag collegano i metadati alle risorse, fornendo informazioni sulle risorse o sui proprietari.

### <a name="set-up-policies"></a>Configurare i criteri

Il servizio Criteri di Azure esegue una valutazione delle risorse, alla ricerca di quelle che non sono conformi alle definizioni di criteri specificate. Ad esempio, potrebbero essere presenti criteri che consentono solo un determinato tipo di VM o che richiedono un tag specifico nelle risorse.

I criteri di Azure specificano la definizione dei criteri e l'assegnazione specifica l'ambito in cui devono essere applicati. L'ambito può spaziare da un gruppo di gestione a un gruppo di risorse. [Informazioni](https://docs.microsoft.com/azure/governance/policy/tutorials/create-and-manage) sulla creazione e sulla gestione dei criteri.

Contoso intende iniziare con un paio di criteri:

- Desidera un criterio per garantire che le risorse possano essere distribuite solo nelle aree EUS2 e CUS.
- Intende limitare gli SKU di VM ai soli SKU approvati. La finalità è quella di garantire che non vengano usati SKU di VM dispendiosi.

#### <a name="limit-resources-to-regions"></a>Limitare le risorse alle aree

Contoso usa la definizione dei criteri predefinita **Località consentite** per limitare le aree delle risorse.

1. Nel portale di Azure l'azienda seleziona **Tutti i servizi** e cerca **Criteri**.
2. Seleziona **Assegnazioni** > **Assegna criteri**.
3. Nell'elenco dei criteri seleziona **Località consentite**.
4. Imposta **Ambito** sul nome della sottoscrizione di Azure e seleziona le due aree nell'elenco di elementi consentiti.

    ![Regioni consentite dai criteri](./media/contoso-migration-infrastructure/policy-region.png)

5. Per impostazione predefinita i criteri vengono impostati con **Nega**, vale a dire che se un utente avvia una distribuzione nella sottoscrizione che non si trova nell'area EUS2 o CUS, la distribuzione avrà esito negativo. Ecco cosa accade se un utente nella sottoscrizione Contoso tenta di configurare una distribuzione negli Stati Uniti occidentali.

    ![Criterio non riuscito](./media/contoso-migration-infrastructure/policy-failed.png)

#### <a name="allow-specific-vm-skus"></a>Consentire specifici SKU di VM

Contoso userà la definizione dei criteri predefinita **Allow virtual machines SKUs** (Consenti SKU macchine virtuali) per limitare il tipo di VM che possono essere create nella sottoscrizione.

![SKU criteri](./media/contoso-migration-infrastructure/policy-sku.png)

#### <a name="check-policy-compliance"></a>Controllare la conformità dei criteri

I criteri hanno effetto immediato e Contoso può verificare la conformità delle risorse.

1. Nel portale di Azure l'azienda seleziona il collegamento **Conformità**.
2. Viene visualizzato il dashboard di conformità. È possibile eseguire il drill-down per maggiori dettagli.

    ![Conformità ai criteri](./media/contoso-migration-infrastructure/policy-compliance.png)

### <a name="set-up-locks"></a>Configurare i blocchi

Contoso usa da tempo il framework ITIL per la gestione dei sistemi. Uno degli aspetti più importanti del framework è il controllo modifiche. Contoso intende assicurarsi che venga implementato nella distribuzione di Azure.

Contoso implementerà i blocchi nel modo seguente:

- Qualsiasi componente di produzione o failover deve essere in un gruppo di risorse con un blocco ReadOnly. Ciò significa che, per modificare o eliminare gli elementi di produzione, è necessario rimuovere il blocco.
- I gruppi di risorse non di produzione non avranno blocchi CanNotDelete. Questo significa che gli utenti autorizzati possono leggere o modificare una risorsa, ma non eliminarla.

[Altre informazioni](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-lock-resources) sui blocchi.

### <a name="set-up-tagging"></a>Impostare i tag

Per tenere traccia delle risorse man mano che vengono aggiunte, sarà sempre più importante per Contoso associarle a un reparto, un cliente e un ambiente appropriati.

Oltre a fornire informazioni sulle risorse e sui proprietari, i tag consentiranno a Contoso di aggregare e raggruppare le risorse e usare tali dati ai fini di chargeback.

Contoso deve visualizzare le risorse di Azure in modo significativo per l'azienda. Ad esempio, come ruolo o reparto. Non è necessario che le risorse si trovino nello stesso gruppo di risorse per condividere un tag. Contoso creerà una tassonomia di tag semplice in modo che tutti usino gli stessi tag.

**Nome del tag** | **Valore**
--- | ---
CostCenter | 12345: deve essere un centro di costo valido di SAP.
BusinessUnit | Nome della business unit (di SAP). Corrisponde a CostCenter.
ApplicationTeam | Alias di posta elettronica del team responsabile del supporto dell'app.
CatalogName | Nome dell'app o ShareServices, in base al catalogo di servizi supportato dalla risorsa.
ServiceManager | Alias di posta elettronica dell'ITIL Service Manager per la risorsa.
COBPriority | Priorità impostata dall'azienda per BCDR. Valori da 1 a 5.
ENV | I valori possibili sono DEV, STG, PROD, che rappresentano sviluppo, gestione temporanea e produzione.

ad esempio:

 ![Tag di Azure](./media/contoso-migration-infrastructure/azure-tag.png)

Dopo aver creato il tag, Contoso creerà nuove definizioni e assegnazioni dei criteri per promuovere l'uso dei tag richiesti nell'intera organizzazione.

## <a name="step-6-consider-security"></a>Passaggio 6: Considerare la sicurezza

La sicurezza è fondamentale nel cloud e Azure offre un'ampia gamma di funzionalità e strumenti di sicurezza, che consentono di creare soluzioni sicure nella piattaforma di Azure. In [Fiducia nel cloud attendibile](https://azure.microsoft.com/overview/trusted-cloud) sono disponibili altre informazioni sulla sicurezza di Azure.

Contoso deve prendere in considerazione alcuni aspetti:

- **Centro sicurezza di Azure:** Il Centro sicurezza di Azure offre la gestione unificata della sicurezza e la protezione avanzata dalle minacce nei carichi di lavoro cloud ibridi. Con il Centro sicurezza, è possibile applicare i criteri di sicurezza sui carichi di lavoro, limitare l'esposizione alle minacce, rilevare e rispondere agli attacchi. [Altre informazioni](https://docs.microsoft.com/azure/security-center/security-center-intro).
- **Gruppi di sicurezza di rete (gruppi):** Un NSG è un filtro (firewall) che contiene un elenco di regole di sicurezza che, se applicate, consentono o negano il traffico di rete alle risorse connesse ad Azure reti virtuali. [Altre informazioni](https://docs.microsoft.com/azure/virtual-network/security-overview).
- **Crittografia dei dati:** Crittografia dischi di Azure è una funzionalità che consente di crittografare i dischi delle macchine virtuali IaaS Windows e Linux. [Altre informazioni](https://docs.microsoft.com/azure/security/azure-security-encryption-atrest).

### <a name="work-with-the-azure-security-center"></a>Uso del Centro sicurezza di Azure

Contoso ha bisogno di una rapida panoramica dell'approccio alla sicurezza del nuovo cloud ibrido e, in particolare, dei carichi di lavoro di Azure. Di conseguenza, ha deciso di implementare il Centro sicurezza di Azure iniziando con le funzionalità seguenti:

- Gestione centralizzata dei criteri
- Valutazione continua
- Consigli operativi

#### <a name="centralize-policy-management"></a>Gestione centralizzata dei criteri

Con la gestione centralizzata dei criteri Contoso garantisce la conformità ai requisiti di sicurezza nell'intero ambiente. Può implementare in modo rapido e semplice un criterio applicabile a tutte le risorse di Azure.

![Criteri di sicurezza](./media/contoso-migration-infrastructure/security-policy.png)

#### <a name="assess-and-action"></a>Valutazione e azione

Contoso usa la valutazione continua della sicurezza, che monitora la sicurezza delle macchine, delle reti, delle risorse di archiviazione, dei dati e delle applicazioni per individuare potenziali problemi di sicurezza.

- Il Centro sicurezza analizza lo stato di sicurezza delle risorse di calcolo, infrastruttura e dati di Contoso e di app e servizi di Azure.
- La valutazione continua consente al team delle operazioni di Contoso di individuare potenziali problemi di sicurezza, ad esempio i sistemi con aggiornamenti della sicurezza mancanti o con porte di rete esposte.
- In particolare Contoso intende assicurarsi che tutte le VM siano protette. Il Centro sicurezza è utile in tal senso, in quanto verifica l'integrità delle VM e offre consigli operativi e in ordine di priorità per risolvere le vulnerabilità della sicurezza prima che vengano sfruttate.

![Monitorare](./media/contoso-migration-infrastructure/monitoring.png)

### <a name="work-with-nsgs"></a>Uso dei gruppi di sicurezza di rete

Contoso può limitare il traffico di rete verso le risorse in una rete virtuale usando gruppi di sicurezza di rete.

- Un gruppo di sicurezza di rete contiene un elenco di regole di sicurezza che consentono o impediscono il traffico di rete in ingresso o in uscita in base all'indirizzo IP di origine o di destinazione, alla porta e al protocollo.
- Se applicate a una subnet, le regole si applicano a tutte le risorse al suo interno. Oltre alle interfacce di rete, sono incluse le istanze dei servizi di Azure distribuiti nella subnet.
- I gruppi di sicurezza delle applicazioni consentono di configurare la sicurezza di rete come un'estensione naturale della struttura di un'app, raggruppando le VM e definendo i criteri di sicurezza di rete in base a tali gruppi.
  - Con i gruppi di sicurezza delle app Contoso può riusare i criteri di sicurezza su larga scala senza gestire manualmente indirizzi IP espliciti. La piattaforma gestisce la complessità degli indirizzi IP espliciti e di più set di regole, consentendo all'utente di concentrarsi sulla logica di business.
  - Contoso può specificare un gruppo di sicurezza delle applicazioni come origine e destinazione in una regola di sicurezza. Dopo aver definito i criteri di sicurezza, Contoso potrà creare VM e assegnare le relative schede di interfaccia a un gruppo.

Contoso implementerà una combinazione di gruppi di sicurezza di rete e delle applicazioni. Contoso è interessata alla gestione dei gruppi di sicurezza di rete. È inoltre preoccupata per l'uso eccessivo dei NSG e per la maggiore complessità che ne deriva per il personale operativo. Ecco le operazioni che eseguirà Contoso:

- Tutto il traffico in ingresso e in uscita da tutte le subnet (nord-sud) sarà soggetto a una regola NSG, ad eccezione delle GatewaySubnet nelle reti dell'hub.
- Eventuali firewall o controller di dominio saranno protetti dai gruppi di sicurezza di rete delle subnet e delle schede di interfaccia rete.
- A tutte le applicazioni di produzione verranno applicati gruppi di sicurezza delle applicazioni.

Contoso ha creato un modello che riflette l'aspetto di questa condizione per le sue applicazioni.

![Sicurezza](./media/contoso-migration-infrastructure/asg.png)

I gruppi di sicurezza di rete associati ai gruppi di sicurezza delle applicazioni verranno configurati con privilegi minimi per garantire che solo i pacchetti consentiti possano essere trasmessi da una parte della rete alla destinazione.

**Azione** | **Nome** | **Origine** | **Destinazione** | **Porta**
--- | --- | --- | --- | ---
Allow | AllowInternetToFE | VNET-HUB-EUS1/IB-TrustZone | APP1-FE 80, 443
Allow | AllowWebToApp | APP1-FE | APP1-APP | 80, 443
Allow | AllowAppToDB | APP1-APP | APP1-DB | 1433
Deny | DenyAllInbound | Qualsiasi | Qualsiasi | Qualsiasi

### <a name="encrypt-data"></a>Crittografare i dati

Crittografia dischi di Azure è integrata con Azure Key Vault per consentire di controllare e gestire le chiavi di crittografia dei dischi e i segreti in una sottoscrizione dell'insieme di credenziali delle chiavi. Assicura anche che tutti i dati nei dischi delle VM vengano crittografati quando inattivi in Archiviazione di Azure.

- Contoso ha deciso che per alcune VM è necessaria la crittografia:
- Contoso ha intenzione di applicarla per le VM con dati PPI, riservati o dei clienti.

## <a name="conclusion"></a>Conclusione

In questo articolo Contoso ha configurato un'infrastruttura di Azure e criteri per la sottoscrizione di Azure, identità ibride, ripristino di emergenza, reti, governance e sicurezza.

Non tutti i passaggi completati da Contoso in questo articolo sono obbligatori per la migrazione al cloud. Nel caso specifico, l'azienda intendeva pianificare un'infrastruttura di rete che potesse essere usata per tutti i tipi di migrazioni e che fosse sicura, resiliente e scalabile.

Una volta implementata questa infrastruttura, Contoso è pronta a proseguire e provare la migrazione.

## <a name="next-steps"></a>Passaggi successivi

Dopo aver configurato l'infrastruttura di Azure, Contoso è pronto per iniziare la migrazione dei carichi di lavoro nel cloud. Vedere la sezione [Panoramica degli esempi e dei modelli di migrazione](./contoso-migration-overview.md#windows-server-workloads) per una selezione di scenari che usano questa infrastruttura di esempio come destinazione della migrazione.
