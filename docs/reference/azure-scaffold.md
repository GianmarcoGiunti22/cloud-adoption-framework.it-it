---
title: Procedure consigliate per le aziende che passano ad Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Viene descritto uno scaffold che le organizzazioni possono usare per garantire un ambiente protetto e gestibile.
author: rdendtler
ms.author: rodend
ms.date: 09/22/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: reference
ms.openlocfilehash: 3ad84a52b35a98744f59b0d719e61f2c83a61af0
ms.sourcegitcommit: 50788e12bb744dd44da14184b3e884f9bddab828
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2019
ms.locfileid: "74160452"
---
# <a name="azure-enterprise-scaffold-prescriptive-subscription-governance"></a>Scaffold Azure enterprise: governance prescrittiva per le sottoscrizioni

> [!NOTE]
> Azure Enterprise ponteggi è stato integrato nel Framework di adozione Microsoft Cloud. Il contenuto di questo articolo è ora rappresentato nella sezione [Ready](../ready/index.md) del nuovo Framework. Questo articolo verrà deprecato nelle prime 2020. Per iniziare a usare il nuovo processo, vedere la [Panoramica pronta](../ready/index.md), [creazione della prima zona di destinazione](../ready/azure-setup-guide/migration-landing-zone.md)e [considerazioni sulla zona di destinazione](../ready/considerations/index.md).

Le organizzazioni stanno adottando sempre di più il cloud pubblico per la sua agilità e la sua flessibilità. Si basano sui punti di forza del cloud per generare ricavi e ottimizzare l'utilizzo delle risorse per l'azienda. Microsoft Azure fornisce numerosi servizi e funzionalità che le organizzazioni assemblano come blocchi predefiniti per affrontare le esigenze di una vasta gamma di applicazioni e carichi di lavoro.

L'unico punto di partenza per ottenere i vantaggi del cloud è decidere di usare Microsoft Azure. Il secondo passaggio è comprendere come l'azienda può usare Azure in modo efficace e identificare le funzionalità di base da adottare per rispondere a domande come:

- "Mi preoccupa la sovranità dei dati. Come è possibile assicurarsi che i dati e i sistemi soddisfino i requisiti normativi?"
- "Come è possibile determinare cosa è supportato da ogni risorsa, in modo da poterlo giustificare e fatturare con precisione?"
- "Vorrei avere la certezza che tutto ciò che viene distribuito o eseguito nel cloud pubblico abbia come priorità la sicurezza. Come posso fare?"

La prospettiva di una sottoscrizione vuota senza Guardrails è scoraggiante. Questo spazio vuoto può ostacolare la migrazione ad Azure.

Questo articolo offre un punto di partenza per i professionisti tecnici, in modo da aiutarli a soddisfare le esigenze in termini di governance e bilanciarle con la richiesta di agilità. Introduce il concetto di un scaffold enterprise per guidare le organizzazioni nell'implementazione e nella gestione degli ambienti Azure in un modo sicuro. Fornisce il framework per sviluppare controlli efficienti ed efficaci.

## <a name="need-for-governance"></a>Esigenza di governance

Durante il passaggio ad Azure, è necessario affrontare in anticipo l'argomento della governance per garantire il corretto uso del cloud all'interno dell'organizzazione. Purtroppo, il tempo necessario e le procedure per creare un sistema di governance completo implicano che alcuni gruppi aziendali si rivolgano direttamente ai provider senza coinvolgere l'IT aziendale. Se le risorse non vengono gestite correttamente, questo approccio rischia di lasciare l'azienda in balia dei compromessi. Le caratteristiche del cloud pubblico &mdash;agility, la flessibilità e i prezzi basati sul consumo &mdash;are importante per i gruppi aziendali che devono soddisfare rapidamente le esigenze dei clienti (sia interni che esterni). Ma è necessario garantire che i dati e i sistemi siano protetti in modo efficace.

Quando si costruisce un edificio, viene usata un'impalcatura (in inglese scaffold) per creare l'intelaiatura della struttura. Questa impalcatura descrive la struttura generale e fornisce punti di ancoraggio per il montaggio di sistemi più permanenti. Un scaffold enterprise è lo stesso: un set di controlli flessibili e funzionalità di Azure che forniscono la struttura per l'ambiente e punti di ancoraggio per servizi basati su cloud pubblico. Fornisce ai generatori (IT e gruppi aziendali) una base per creare e collegare nuovi servizi, tenendo a mente l'importanza della velocità di distribuzione.

Lo scaffold si basa su procedure raccolte attraverso le varie interazioni con i client di diverse dimensioni. Questi client variano da organizzazioni di piccole dimensioni che sviluppano soluzioni nel cloud a grandi aziende multinazionali e fornitori di software indipendenti che eseguono la migrazione di carichi di lavoro e sviluppano soluzioni native per il cloud. Il patibolo aziendale è "progettato" per essere flessibile per supportare i carichi di lavoro IT tradizionali e i carichi di lavoro agile, ad esempio gli sviluppatori che creano applicazioni SaaS (Software as a Service) basate sulle funzionalità della piattaforma Azure.

L'impalcatura aziendale può fungere da base per ogni nuova sottoscrizione in Azure. Consente agli amministratori di verificare che i carichi di lavoro soddisfino i requisiti minimi di governance di un'organizzazione senza impedire che i gruppi e gli sviluppatori aziendali soddisfino i propri obiettivi. La nostra esperienza dimostra che questa operazione accelera molto, anziché ostacolare, la crescita del cloud pubblico.

> [!NOTE]
> Microsoft ha rilasciato in anteprima una nuova funzionalità denominata [Azure Blueprint](https://docs.microsoft.com/azure/governance/blueprints/overview) che consentirà di creare pacchetti, gestire e distribuire immagini, modelli, criteri e script comuni tra le sottoscrizioni e i gruppi di gestione. Questa funzionalità fa da ponte tra lo scopo dello scaffold come modello di riferimento e la distribuzione di tale modello all'organizzazione.
>
L'immagine seguente mostra i componenti dello scaffold. Le fondamenta sono rappresentate da un saldo piano per la gerarchia di gestione e le sottoscrizioni. Le colonne sono i criteri di Resource Manager e saldi standard di denominazione. Il resto dello scaffold è rappresentato dalle principali funzionalità di Azure e dalle funzioni che garantiscono e connettono un ambiente protetto e gestibile.

![Impalcature Enterprise](../_images/reference/scaffoldv2.png)

## <a name="define-your-hierarchy"></a>Definire la gerarchia

Le fondamenta dello scaffold sono rappresentate dalla gerarchia e dalla relazione tra l'iscrizione ad Azure enterprise e le sottoscrizioni e i gruppi di risorse. L'iscrizione enterprise definisce la forma e l'uso dei servizi Azure all'interno di una società da un punto di vista contrattuale. All'interno del Enterprise Agreement è possibile suddividere ulteriormente l'ambiente in reparti, account, sottoscrizioni e gruppi di risorse in base alla struttura dell'organizzazione.

![Hierarchy](../_images/reference/agreement.png)

Una sottoscrizione Azure è l'unità di base che contiene tutte le risorse. Definisce anche diversi limiti all'interno di Azure, ad esempio il numero di memorie centrali, reti virtuali e altre risorse. I gruppi di risorse vengono usati per perfezionare ulteriormente il modello di sottoscrizione e abilitare un raggruppamento più naturale di risorse.

Ogni azienda è diversa e la gerarchia nell'immagine sopra consente una notevole flessibilità nell'organizzazione di Azure all'interno della società. La modellazione della gerarchia per riflettere le esigenze di fatturazione, gestione delle risorse e accesso alle risorse dell'azienda è la prima e più importante decisione da prendere quando si inizia dal cloud pubblico.

### <a name="departments-and-accounts"></a>Reparti e account

I tre modelli comuni per le iscrizioni ad Azure sono:

- Modello **funzionale** :

  ![Modello funzionale](../_images/reference/functional.png)

- Modello **Business Unit** :

  ![Modello business unit](../_images/reference/business.png)

- Modello **geografico** :

  ![Modello geografico](../_images/reference/geographic.png)

Anche se ognuno di questi modelli ha un suo posto, il modello **business unit** viene sempre più spesso adottato per la sua flessibilità nella creazione di modelli di costo dell'organizzazione e per riflettere il campo di controllo. Microsoft Core Engineering and Operational Group ha creato un subset efficace dello schema **Business Unit** basato su **federale**, **stato**e **locale**. Per altre informazioni, vedere [organizzazione delle sottoscrizioni e dei gruppi di risorse all'interno dell'azienda](https://azure.microsoft.com/blog/organizing-subscriptions-and-resource-groups-within-the-enterprise).

### <a name="azure-management-groups"></a>Gruppi di gestione di Azure

Microsoft offre ora un altro modo per modellare la gerarchia, ovvero i [gruppi di gestione di Azure](https://docs.microsoft.com/azure/azure-resource-manager/management-groups-overview). I gruppi di gestione sono molto più flessibili dei reparti e degli account e possono essere annidati fino a sei livelli. I gruppi di gestione consentono di creare una gerarchia separata dalla gerarchia di fatturazione, esclusivamente per una gestione efficiente delle risorse. I gruppi di gestione possono eseguire il mirroring della gerarchia di fatturazione e spesso le aziende iniziano in questo modo. Tuttavia, la potenza dei gruppi di gestione è quando vengono usati per modellare l'organizzazione, raggruppando le sottoscrizioni correlate (indipendentemente dalla loro posizione nella gerarchia di fatturazione) e assegnando ruoli, criteri e iniziative comuni. Di seguito sono riportati alcuni esempi:

- **Produzione e non produzione.** Alcune aziende creano gruppi di gestione per identificare le sottoscrizioni di produzione e non di produzione. I gruppi di gestione consentono a questi clienti di gestire più facilmente ruoli e criteri. Ad esempio, la sottoscrizione non di produzione può consentire agli sviluppatori di accedere "collaboratore", ma in produzione hanno solo l'accesso "Reader".
- **Servizi interni rispetto ai servizi esterni.** Le aziende hanno spesso requisiti, criteri e ruoli diversi per i servizi interni rispetto ai servizi rivolte ai clienti.

I gruppi di gestione ben progettati sono, insieme alle iniziative e ai criteri di Azure, la spina principale della governance efficiente di Azure.

### <a name="subscriptions"></a>Sottoscrizioni

Quando si prendono decisioni su reparti e account (o gruppi di gestione), principalmente si cerca di capire come dividere l'ambiente di Azure per farlo corrispondere all'organizzazione. Tuttavia, le sottoscrizioni sono il luogo in cui si verifica il lavoro reale e le decisioni in questo caso influiscono su sicurezza, scalabilità e fatturazione. Molte organizzazioni cercano come guide i criteri seguenti:

- **Applicazione/servizio:** Le sottoscrizioni rappresentano un'applicazione o un servizio (portfolio di applicazioni)
- **Ciclo** di vita: Le sottoscrizioni rappresentano un ciclo di vita di un servizio, ad esempio produzione o sviluppo.
- **Reparto:** Le sottoscrizioni rappresentano i reparti all'interno dell'organizzazione.

I primi due criteri, quelli più usati, sono entrambi vivamente consigliati. L'approccio "ciclo di vita" è appropriato per la maggior parte delle organizzazioni. In questo caso, la raccomandazione generale consiste nell'usare due sottoscrizioni di base, `Production` e `Nonproduction` e quindi usare i gruppi di risorse per separare ulteriormente gli ambienti.

### <a name="resource-groups"></a>Gruppi di risorse

Azure Resource Manager consente di inserire le risorse in gruppi significativi per gestione, fatturazione o affinità naturale. I gruppi di risorse sono contenitori di risorse che hanno un ciclo di vita comune o condividono un attributo, ad esempio "tutti i server SQL" o "Applicazione A".

I gruppi di risorse non possono essere nidificati e le risorse possono appartenere a un solo gruppo di risorse. Alcune azioni possono essere applicate a tutte le risorse di un gruppo di risorse. Ad esempio, l'eliminazione di un gruppo di risorse comporta la rimozione di tutte le risorse all'interno del gruppo di risorse. Come per le sottoscrizioni, ci sono criteri comuni durante la creazione di gruppi di risorse, che variano da carichi di lavoro di tipo "IT tradizionale" a "IT agile":

- I carichi di lavoro di tipo "IT tradizionale" sono più comunemente raggruppati in base agli elementi all'interno di uno stesso ciclo di vita, ad esempio un'applicazione. Il raggruppamento in base all'applicazione consente la gestione di singole applicazioni.
- I carichi di lavoro di tipo "IT agile" tendono a concentrarsi su applicazioni cloud orientate ai clienti esterni. I gruppi di risorse spesso riflettono i livelli di distribuzione (ad esempio livello Web o livello app) e gestione.

> [!NOTE]
> Conoscere il carico di lavoro aiuta a sviluppare una strategia di gruppo di risorse. Questi modelli possono essere mischiati e combinati. Ad esempio, un gruppo di risorse di servizi condivisi nella stessa sottoscrizione come gruppi di risorse "agile".

## <a name="naming-standards"></a>Standard di denominazione

Il primo pilastro dello scaffolding è uno standard di denominazione coerente. Standard di denominazione ben progettati consentono di identificare le risorse nel portale, in una fattura e all'interno degli script. È probabile che si disponga già di standard di denominazione per l'infrastruttura locale. Quando si aggiunge Azure all'ambiente, è opportuno estendere tali standard di denominazione alle risorse di Azure.

> [!TIP]
> Per le convenzioni di denominazione:
>
> - Esaminare [Patterns and Practices guidance (Linee guida su modelli e procedure)](https://docs.microsoft.com/azure/architecture/best-practices/resource-naming) e adottarle dove possibile. Queste linee guida consentono di stabilire uno standard di denominazione significativo e offre esempi dettagliati.
> - Uso dei criteri di Gestione risorse per applicare gli standard di denominazione.
>
> Occorre tenere presente che è difficile modificare i nomi in un secondo momento, pertanto spendere alcuni minuti a farlo a questo punto consentiranno di non dover affrontare problemi più avanti.

È necessario concentrare gli standard di denominazione sulle risorse usate e cercate più comunemente. Ad esempio, tutti i gruppi di risorse devono seguire uno standard sicuro per maggiore chiarezza.

### <a name="resource-tags"></a>Tag delle risorse

I tag delle risorse sono strettamente allineati agli standard di denominazione. Man mano che le risorse vengono aggiunte alle sottoscrizioni, diventa sempre più importante categorizzarle in maniera logica a scopo di fatturazione, gestione e svolgimento delle operazioni. Per altre informazioni, vedere [Usare tag per organizzare le risorse di Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-using-tags).

> [!IMPORTANT]
> I tag possono contenere informazioni personali ed essere sottoposti alle normative del GDPR. Pianificare con attenzione la gestione dei tag. Per informazioni generali su GDPR, vedere la sezione GDPR del [portale di attendibilità del servizio](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).

I tag vengono usati in molti modi, oltre a fatturazione e gestione. Spesso vengono usati nell'ambito dell'automazione (vedere la sezione successiva). Se non affrontati in anticipo, possono verificarsi conflitti. La procedura consigliata consiste nell'identificare tutti i tag comuni a livello aziendale, ad esempio ApplicationOwner e CostCenter, e applicarli in modo coerente durante la distribuzione delle risorse tramite l'automazione.

## <a name="azure-policy-and-initiatives"></a>Iniziative e criteri di Azure

Il secondo pilastro del patibolo prevede l'uso di [criteri e iniziative di Azure](https://docs.microsoft.com/azure/azure-policy/azure-policy-introduction) per gestire i rischi applicando regole (con effetti) sulle risorse e sui servizi nelle sottoscrizioni. Le iniziative di Azure sono raccolte di criteri progettati per raggiungere un unico obiettivo. I criteri e le iniziative vengono quindi assegnati a un ambito di risorsa per avviare l'applicazione di tali criteri.

I criteri e le iniziative sono ancora più potenti se usati con i gruppi di gestione citati in precedenza. I gruppi di gestione consentono l'assegnazione di un'iniziativa o dei criteri a un intero set di sottoscrizioni.

### <a name="common-uses-of-resource-manager-policies"></a>Uso comune dei criteri di Resource Manager

I criteri e le iniziative sono uno strumento potente nel Toolkit di Azure. I criteri consentono alle aziende di fornire controlli per i carichi di lavoro "IT tradizionali" che consentono la stabilità necessaria per le applicazioni line-of-business, consentendo allo stesso tempo i carichi di lavoro "agile" &mdash;for esempio, lo sviluppo di applicazioni dei clienti senza esposizione dell'azienda a rischi aggiuntivi. I modelli più comuni per i criteri sono:

- **Conformità geografica e sovranità dei dati.** Azure dispone di un elenco sempre crescente di aree geografiche in tutto il mondo. Le aziende hanno spesso la necessità di garantire che le risorse in un ambito specifico rimangano in un'area geografica per soddisfare i requisiti normativi.
- **Evitare di esporre i server pubblicamente.** Criteri di Azure può impedire la distribuzione di determinati tipi di risorse. È comune creare un criterio per negare la creazione di un indirizzo IP pubblico all'interno di un ambito specifico, evitando l'esposizione involontaria di un server a Internet.
- **Gestione dei costi e metadati.** I tag delle risorse vengono spesso usati per aggiungere importanti dati di fatturazione a risorse e gruppi di risorse, ad esempio CostCenter, Owner e altro ancora. Questi tag hanno un'importanza inestimabile per fatturare e gestire con precisione le risorse. I criteri possono imporre l'applicazione di tag a tutte le risorse distribuite, rendendole più facili da gestire.

### <a name="common-uses-of-initiatives"></a>Usi comuni delle iniziative

Le iniziative offrono alle aziende la possibilità di raggruppare i criteri logici e di tenerne traccia come una singola entità. Le iniziative consentono all'azienda di soddisfare le esigenze dei carichi di lavoro agili e tradizionali. Gli usi comuni delle iniziative includono:

- **Abilitare il monitoraggio nel centro sicurezza di Azure.** Si tratta di un'iniziativa predefinita nei criteri di Azure ed è un ottimo esempio delle iniziative. Consente i criteri che identificano i database SQL non crittografati, le vulnerabilità delle macchine virtuali (VM) e le esigenze più comuni correlate alla sicurezza.
- **Iniziativa specifica delle normative.** Spesso le aziende raggruppano i criteri comuni a un requisito normativo (ad esempio HIPAA) in modo che i controlli e la conformità a tali controlli vengano monitorati in modo efficiente.
- **Tipi di risorse e SKU.** La creazione di un'iniziativa che limita i tipi di risorse che è possibile distribuire, nonché gli SKU che possono essere distribuiti, può contribuire a controllare i costi e a garantire che l'organizzazione stia distribuendo solo le risorse che il team ha il set di competenze e le procedure da supportare.

> [!TIP]
> È consigliabile usare sempre le definizioni delle iniziative invece di quelle dei criteri. Dopo aver assegnato un'iniziativa a un ambito, ad esempio una sottoscrizione o un gruppo di gestione, è possibile aggiungere facilmente un altro criterio all'iniziativa senza dover modificare le assegnazioni. In questo modo si semplificano la comprensione di ciò che viene applicato e il monitoraggio della conformità.

### <a name="policy-and-initiative-assignments"></a>Assegnazioni di criteri e iniziative

Dopo aver creato i criteri e averli raggruppati in iniziative logiche, è necessario assegnarli a un ambito, che può essere un gruppo di gestione, una sottoscrizione o perfino un gruppo di risorse. Le assegnazioni consentono inoltre di escludere un ambito Sottoambito dall'assegnazione di un criterio. Ad esempio, se si nega la creazione di indirizzi IP pubblici in una sottoscrizione, è possibile creare un'assegnazione con un'esclusione per un gruppo di risorse connesso alla rete perimetrale protetta.

Sono disponibili diversi esempi di criteri che mostrano come iniziative e criteri possono essere applicati a varie risorse all'interno di Azure in questo repository [GitHub](https://github.com/Azure/azure-policy).

## <a name="identity-and-access-management"></a>Gestione degli accessi e delle identità

Una delle prime e più cruciali domande che ci si pone quando si inizia a usare il cloud pubblico è chi deve avere accesso alle risorse e come è possibile controllare tale accesso. Il controllo dell'accesso alla portale di Azure e alle risorse nel portale è essenziale per la sicurezza a lungo termine degli asset nel cloud.

Per proteggere l'accesso alle risorse, è necessario innanzitutto configurare il provider di identità e quindi configurare i ruoli e l'accesso. Azure Active Directory (Azure AD), connesso ad Active Directory locale, è la base dell'identità di Azure. Ciò premesso, Azure AD *non* è lo stesso Active Directory locale ed è importante comprendere che cos'è un tenant di Azure ad e in che modo è correlato alla registrazione di Azure. Esaminare le [informazioni](../govern/resource-consistency/resource-access-management.md) disponibili per ottenere una solida base su Azure AD e Active Directory locali. Per connettere e sincronizzare il Active Directory Azure AD, installare e configurare lo [strumento di Azure ad Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) in locale.

![Diagramma dell'architettura di AD](../_images/reference/ad-architecture.png)

Quando Azure è stato originariamente rilasciato, i controlli degli accessi a una sottoscrizione erano elementari: Amministratore o Coamministratore. L'accesso a una sottoscrizione nel modello classico implicava l'accesso a tutte le risorse del portale. Questa mancanza di un controllo granulare ha portato alla proliferazione di sottoscrizioni per fornire un livello ragionevole di controllo degli accessi per un'iscrizione ad Azure. La proliferazione di sottoscrizioni non è più necessaria. Con il controllo degli accessi in base al ruolo, è possibile assegnare utenti a ruoli standard che forniscono accesso comune, ad esempio "proprietario", "collaboratore" o "lettore", o persino creare ruoli personalizzati.

Quando si implementa l'accesso in base al ruolo, è consigliabile tenere presente gli aspetti seguenti:

- Controllare l'amministratore/il coamministratore di una sottoscrizione, perché questi ruoli dispongono delle autorizzazioni complete. È necessario aggiungere il proprietario della sottoscrizione come coamministratore solo se deve gestire distribuzioni classiche di Azure.
- Usare i gruppi di gestione per assegnare i [ruoli](https://docs.microsoft.com/azure/azure-resource-manager/management-groups-overview#management-group-access) in più sottoscrizioni e ridurre il carico derivante dalla gestione a livello di sottoscrizione.
- Aggiungere gli utenti di Azure a un gruppo (ad esempio, Proprietari dell'applicazione X) in Active Directory. Utilizzare il gruppo sincronizzato per fornire ai membri del gruppo i diritti appropriati per gestire il gruppo di risorse contenente l'applicazione.
- Seguire il principio di concedere il **privilegio minimo** necessario per svolgere il lavoro previsto.

> [!IMPORTANT]
>È consigliabile usare le funzionalità di [Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/privileged-identity-management/pim-configure), Azure [Multi-Factor Authentication](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-getstarted) e [accesso condizionale](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) per offrire migliore protezione e maggiore visibilità sulle azioni amministrative nelle sottoscrizioni di Azure. Queste funzionalità provengono da una licenza Azure AD Premium valida (a seconda della funzione) per proteggere e gestire ulteriormente l'identità. Azure AD PIM fornisce all'accesso amministrativo "JIT" il flusso di lavoro di approvazione, oltre al controllo completo delle attività e delle attivazioni dell'amministratore. Azure Multi-Factor Authentication è un'altra funzionalità fondamentale e consente la verifica in due passaggi per l'accesso al portale di Azure. In combinazione con i controlli per l'accesso condizionale, consente di gestire efficacemente il rischio di compromissione.

Una delle migliori strategie per mitigare i rischi che è possibile adottare ed è consigliabile considerare obbligatoria per ogni distribuzione consiste nel pianificare e preparare l'identità e i controlli degli accessi e seguire la procedura consigliata di Azure Identity Management ([collegamento](https://docs.microsoft.com/azure/security/azure-security-identity-management-best-practices)).

## <a name="security"></a>Sicurezza

Uno dei principali ostacoli per l'adozione del cloud è generalmente rappresentato dalle preoccupazioni legate alla sicurezza. I responsabili della gestione dei costi dell'IT e i reparti della sicurezza devono assicurarsi che le risorse in Azure siano al sicuro e protette per impostazione predefinita. Azure fornisce le funzionalità che è possibile usare per proteggere le risorse durante il rilevamento e l'eliminazione di minacce da tali risorse.

### <a name="azure-security-center"></a>Centro sicurezza Azure

Il [Centro sicurezza di Azure](https://docs.microsoft.com/azure/security-center/security-center-intro) offre una visualizzazione unificata dello stato della sicurezza delle risorse nell'intero ambiente oltre alla protezione avanzata dalle minacce. Il Centro sicurezza di Azure è una piattaforma aperta che consente ai partner Microsoft di creare un software che si inserisce al suo interno e ne migliora le funzionalità. Le funzionalità di base del Centro sicurezza di Azure (livello gratuito) forniscono valutazioni e consigli che migliorano il comportamento di sicurezza. I livelli a pagamento consentono funzionalità aggiuntive e utili, ad esempio l'accesso di amministratore JIT e i controlli delle applicazioni adattivi (whitelist).

> [!TIP]
>Il Centro sicurezza di Azure è uno strumento potente che viene regolarmente migliorato con le nuove funzionalità che è possibile usare per rilevare le minacce e proteggere l'azienda. È consigliabile abilitare sempre il Centro sicurezza di Azure.

### <a name="locks-for-azure-resources"></a>Blocchi per le risorse di Azure

Con l'aggiunta di servizi di base alle sottoscrizioni, l'organizzazione diventa sempre più importante per evitare l'intralcio aziendale. Un'interferenza comune si verifica quando uno script o uno strumento in esecuzione in una sottoscrizione di Azure Elimina involontariamente una risorsa. I [blocchi](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-lock-resources) limitano le operazioni sulle risorse di valore elevato in cui la modifica o l'eliminazione potrebbe avere un impatto significativo. È possibile applicare blocchi a sottoscrizioni, gruppi di risorse o singole risorse. Applicare i blocchi alle risorse di base, ad esempio reti virtuali, gateway, gruppi di sicurezza di rete e account di archiviazione delle chiavi.

### <a name="secure-devops-kit-for-azure"></a>Secure DevOps kit per Azure

Secure DevOps kit per Azure (AzSK) è una raccolta di script, strumenti, estensioni e funzionalità di automazione creati originariamente dal team IT di Microsoft e [rilasciati come Open Source tramite GitHub](https://github.com/azsk/devopskit-docs). AzSK soddisfa le esigenze di sicurezza delle risorse e delle sottoscrizioni di Azure end-to-end per i team che usano un'automazione completa e integrano senza problemi la sicurezza nei flussi di lavoro DevOps nativi, contribuendo a garantire DevOps sicuri con queste sei aree di interesse:

- Proteggere la sottoscrizione
- Offrire uno sviluppo sicuro
- Integrazione della sicurezza in CI/CD
- Garanzia continua
- Avvisi e monitoraggio
- Governance del rischio cloud

![Diagramma di panoramica del kit Secure DevOps per Azure](../_images/reference/secure-devops-kit.png)

AzSK è un set completo di strumenti, script e informazioni che rappresentano una parte importante di un piano di governance di Azure completo e l'incorporamento di questo nell'impalcatura è fondamentale per supportare gli obiettivi di gestione dei rischi per le organizzazioni.

### <a name="azure-update-management"></a>Gestione aggiornamenti di Azure

Una delle attività principali da eseguire per proteggere l'ambiente è garantire che i server vengano protetti con gli aggiornamenti più recenti. Sebbene vi siano molti strumenti per eseguire questa operazione, Azure offre la soluzione [Gestione aggiornamenti di Azure](https://docs.microsoft.com/azure/automation/automation-update-management) per risolvere l'identificazione e l'implementazione di patch critiche per il sistema operativo. Usa Automazione di Azure, di cui nella sezione [Automatizzare](#automate), più avanti in questa guida.

## <a name="monitor-and-alerts"></a>Monitoraggio e avvisi

La raccolta e l'analisi dei dati di telemetria che forniscono informazioni dettagliate sulle attività, sulle metriche delle prestazioni, sull'integrità e sulla disponibilità dei servizi in uso nelle sottoscrizioni di Azure sono fondamentali per gestire in modo proattivo le applicazioni e infrastruttura ed è una necessità fondamentale di ogni sottoscrizione di Azure. Ogni servizio di Azure genera dati di telemetria sotto forma di log attività, metriche e log di diagnostica.

- I **log attività** descrivono tutte le operazioni eseguite sulle risorse nelle sottoscrizioni.
- Le **metriche** sono informazioni numeriche emesse da una risorsa che descrivono le prestazioni e l'integrità di una risorsa.
- I **log di diagnostica** vengono generati da un servizio di Azure e forniscono dati avanzati e frequenti sul funzionamento di tale servizio.

Queste informazioni possono essere visualizzate e gestite a più livelli e vengono continuamente migliorate. Azure offre funzionalità di monitoraggio **condivise**, di **base**e **complete** delle risorse di Azure tramite i servizi descritti nella figura seguente.

![Monitorare](../_images/reference/monitoring.png)

### <a name="shared-capabilities"></a>Funzionalità condivise

- **Avvisi:** È possibile raccogliere tutti i log, gli eventi e le metriche dalle risorse di Azure, ma senza la possibilità di ricevere notifiche relative a condizioni e azioni critiche, questi dati sono utili solo per scopi cronologici e forensi. Gli avvisi di Azure comunicano in modo proattivo le condizioni definite dall'utente in tutte le applicazioni e nell'infrastruttura. È possibile creare regole di avviso tra log, eventi e metriche che usano i gruppi di azioni per notificare set di destinatari. I gruppi di azioni offrono anche la possibilità di automatizzare la correzione tramite azioni esterne, ad esempio i webhook per eseguire i runbook di Automazione di Azure e Funzioni di Azure.

- **Dashboard:** I dashboard consentono di aggregare le visualizzazioni di monitoraggio e combinare i dati tra le risorse e le sottoscrizioni per offrire una visualizzazione a livello aziendale dei dati di telemetria delle risorse di Azure. È possibile creare e configurare le proprie visualizzazioni e condividerle con altri utenti. Ad esempio, è possibile creare un dashboard costituito da diversi riquadri per gli amministratori di database per fornire informazioni su tutti i servizi di database di Azure, tra cui il database SQL di Azure, il database di Azure per PostgreSQL e il database di Azure per MySQL.

- **Esplora metriche:** Le metriche sono valori numerici generati dalle risorse di Azure, ad esempio% CPU o I/O del disco, che forniscono informazioni approfondite sul funzionamento e sulle prestazioni delle risorse. Utilizzando Esplora metriche, è possibile definire e inviare le metriche che interessano Log Analytics per l'aggregazione e l'analisi.

### <a name="core-monitoring"></a>Monitoraggio di base

- **Monitoraggio di Azure:** Monitoraggio di Azure è il servizio principale della piattaforma che fornisce un'unica origine per il monitoraggio delle risorse di Azure. L'interfaccia portale di Azure di monitoraggio di Azure offre un punto di partenza centralizzato per tutte le funzionalità di monitoraggio in Azure, incluse le funzionalità di monitoraggio approfondite di Application Insights, Log Analytics, monitoraggio della rete, soluzioni di gestione e Mappe del servizio. Con monitoraggio di Azure è possibile visualizzare, eseguire query, indirizzare, archiviare ed eseguire operazioni sulle metriche e sui log provenienti dalle risorse di Azure nell'intera area cloud. Oltre al portale è possibile recuperare i dati tramite i cmdlet di monitoraggio PowerShell, l'interfaccia della riga di comando multipiattaforma o le API REST di monitoraggio di Azure.

- **Azure Advisor:** Azure Advisor monitora costantemente i dati di telemetria tra le sottoscrizioni e gli ambienti e fornisce consigli sulle procedure consigliate per l'ottimizzazione delle risorse di Azure per ridurre i costi e migliorare le prestazioni, la sicurezza e la disponibilità delle risorse che costituiscono le applicazioni.

- **Integrità del servizio:** Integrità dei servizi di Azure identifica eventuali problemi con i servizi di Azure che possono influire sulle applicazioni, oltre a facilitare la pianificazione per le finestre di manutenzione pianificata.

- **Log attività:** Il log attività descrive tutte le operazioni sulle risorse nelle sottoscrizioni. Offre un audit trail per determinare il cosa, il chi e il quando di qualsiasi operazione di creazione, aggiornamento ed eliminazione effettuata sulle risorse. Gli eventi del log attività vengono archiviati nella piattaforma e sono disponibili per eseguire query per 90 giorni. È possibile inserire i log attività in Log Analytics per periodi di conservazione più lunghi e per eseguire query e analisi più approfondite su più risorse.

### <a name="deep-application-monitoring"></a>Monitoraggio avanzato delle applicazioni

- **Application Insights:** Application Insights consente di raccogliere dati di telemetria specifici dell'applicazione e di monitorare le prestazioni, la disponibilità e l'utilizzo delle applicazioni nel cloud o in locale. Grazie alla strumentazione dell'applicazione con SDK supportati per più linguaggi, tra cui .NET, JavaScript, JAVA, node. js, Ruby e Python. Gli eventi di Application Insights vengono inseriti nello stesso archivio dati di Log Analytics che supporta l'infrastruttura e il monitoraggio della protezione per consentire di correlare e aggregare gli eventi nel tempo grazie a un linguaggio di query avanzato.

### <a name="deep-infrastructure-monitoring"></a>Monitoraggio avanzato dell'infrastruttura

- **Log Analytics:** Log Analytics svolge un ruolo centrale nel monitoraggio di Azure raccogliendo dati di telemetria e altri dati da diverse origini e fornendo un linguaggio di query e un motore di analisi che offrono informazioni dettagliate sul funzionamento delle applicazioni e delle risorse. È possibile interagire direttamente con i dati Log Analytics tramite le ricerche e le visualizzazioni log veloci oppure è possibile usare gli strumenti di analisi in altri servizi di Azure che archiviano i dati in Log Analytics, ad esempio Application Insights o il Centro sicurezza di Azure.

- **Monitoraggio della rete:** I servizi di monitoraggio di rete di Azure consentono di ottenere informazioni sul flusso del traffico di rete, le prestazioni, la sicurezza, la connettività e i colli di bottiglia. Una rete ben progettata deve includere la configurazione di servizi di monitoraggio di rete di Azure, ad esempio Network Watcher ed ExpressRoute Monitor.

- **Soluzioni di gestione:** Le soluzioni di gestione sono set di logica in pacchetto, informazioni dettagliate e query Log Analytics predefinite per un'applicazione o un servizio. Si basano su Log Analytics per archiviare e analizzare i dati dell'evento. Esempi di soluzioni di gestione includono il monitoraggio dei contenitori e l'analisi dl database SQL di Azure.

- **Mapping dei servizi:** Mapping dei servizi fornisce una visualizzazione grafica dei componenti dell'infrastruttura, dei relativi processi e delle interdipendenze in altri computer e processi esterni. Integra eventi, dati sulle prestazioni e soluzioni di gestione in Log Analytics.

> [!TIP]
> Prima di creare singoli avvisi, creare e gestire un insieme di gruppi di azioni condivisi che possano essere usati negli avvisi di Azure. In questo modo è possibile gestire centralmente il ciclo di vita degli elenchi di destinatari, i metodi di recapito delle notifiche (posta elettronica, i numeri di telefono SMS) e i webhook a azioni esterne (manuali operativi di automazione di Azure, funzioni di Azure e app per la logica, ITSM).

## <a name="cost-management"></a>Gestione dei costi

Una delle principali modifiche che si dovranno affrontare al momento del passaggio dal cloud locale al cloud pubblico è il passaggio da CAPEX (acquisto dell'hardware) a OPEX (pagamento per il servizio in base all'uso). Questa opzione richiede anche una gestione più attenta dei costi. Il vantaggio del cloud consiste nel fatto che è possibile influire in modo sostanziale e positivo sul costo di un servizio utilizzato semplicemente chiudendo o ridimensionando il servizio quando non è necessario. Gestire deliberatamente i costi nel cloud è una procedura consigliata e una che i clienti maturi eseguono quotidianamente.

Microsoft offre diversi strumenti per poter visualizzare, tenere traccia e gestire i costi. Viene inoltre offerto un set completo di API per personalizzare e integrare la gestione dei costi negli strumenti e nei dahsboard degli utenti. Questi strumenti sono raggruppati in senso libero in portale di Azure funzionalità e funzionalità esterne.

### <a name="azure-portal-capabilities"></a>Funzionalità di portale di Azure

Si tratta di strumenti per fornire informazioni immediate sui costi, oltre alla possibilità di intraprendere azioni.

- **Costo risorsa sottoscrizione:** Disponibile nel portale, la visualizzazione [analisi dei costi di Azure](https://docs.microsoft.com/azure/cost-management/overview) fornisce una rapida panoramica dei costi e delle informazioni sulle spese giornaliere per risorsa o gruppo di risorse.
- **Gestione dei costi di Azure:** Questo prodotto è il risultato dell'acquisto di Cloudyn da parte di Microsoft e consente di gestire e analizzare la spesa di Azure, oltre a quanto speso in altri provider di cloud pubblico. Esistono sia livelli gratuiti che a pagamento, con l'ampia gamma di funzionalità viste nella [panoramica](https://docs.microsoft.com/azure/cost-management/overview).
- **Budget e gruppi di azioni di Azure:** Sapere quali sono i costi e fare qualcosa su di esso fino a quando recentemente non è stato un esercizio manuale. Con l'introduzione dei budget di Azure e delle relative API, è ora possibile creare azioni, come illustrato in [questo esempio](https://channel9.msdn.com/Shows/Azure-Friday/Managing-costs-with-the-Azure-Budgets-API-and-Action-Groups), quando i costi raggiungeranno una soglia. Ad esempio, arrestare un gruppo di risorse di test quando raggiunge il 100% del budget dedicato o [altro esempio].
- **Azure Advisor**: conoscere i costi di qualcosa è solo uno dei punti fondamentali; l'altro è sapere a quale scopo usare tali informazioni. [Azure Advisor](https://docs.microsoft.com/azure/advisor/advisor-overview) offre consigli su come intervenire per risparmiare denaro, migliorare l'affidabilità o perfino aumentare la sicurezza.

### <a name="external-cost-management-tools"></a>Strumenti esterni per la gestione dei costi

- **Informazioni dettagliate sul consumo di Azure Power bi:** Si desidera creare visualizzazioni personalizzate per la propria organizzazione? In tal caso, il pacchetto di contenuto Informazioni dettagliate sul consumo di Azure per Power BI è lo strumento preferito. Usando questo pacchetto di contenuto e Power BI è possibile creare visualizzazioni personalizzate per rappresentare l'organizzazione, eseguire un'analisi più approfondita sui costi e aggiungere altre origini dati per un ulteriore arricchimento.

- **API a consumo:** Le [API a consumo](https://docs.microsoft.com/rest/api/consumption) consentono di accedere a livello di codice ai dati relativi a costi e utilizzo oltre alle informazioni sui budget, le istanze riservate e gli addebiti per il Marketplace. Queste API sono accessibili solo per le iscrizioni Enterprise e alcune sottoscrizioni dirette sul Web, tuttavia offrono la possibilità di integrare i dati dei costi nei propri strumenti e data warehouse. È possibile [accedere a queste API anche tramite l'interfaccia della riga di comando di Azure](https://docs.microsoft.com/cli/azure/consumption?view=azure-cli-latest).

I clienti che sono utenti cloud a lungo termine e maturi seguono alcune procedure consigliate:

- **Monitora attivamente i costi.** Le organizzazioni che hanno familiarità con Azure monitorano costantemente i costi e intraprendono azioni quando necessario. Alcune organizzazioni dispongono perfino di persone dedicate a effettuare analisi e suggerire modifiche all'uso; il costo di queste persone per l'organizzazione viene ammortizzato già dalla prima volta che trovano un cluster HDInsight inutilizzato in uso da mesi.
- **Usare le istanze di VM riservate.** Un altro principio chiave per gestire i costi nel cloud consiste nell'usare lo strumento appropriato per il processo. Se si dispone di una macchina virtuale IaaS che deve rimanere in 24x7, l'uso di un'istanza di VM riservata consentirà di risparmiare denaro significativo. Trovare il giusto equilibrio tra l'automazione dell'arresto delle macchine virtuali e l'uso delle istanze di VM riservate richiede esperienza e analisi.
- **Usare l'automazione in modo efficace.** Molti carichi di lavoro non devono essere eseguiti ogni giorno. La disattivazione di una macchina virtuale per un periodo di quattro ore ogni giorno può ridurre il 15% dei costi. I costi dell'automazione verranno ammortizzati rapidamente.
- **Usare i tag delle risorse per la visibilità.** come descritto in un altro punto di questo documento, l'uso dei tag delle risorse supporta una migliore analisi dei costi.

La gestione costi è una disciplina fondamentale per eseguire un cloud pubblico in modo efficiente ed efficace. Le aziende che riescono a raggiungere il successo possono controllare i loro costi e associarle alla propria richiesta effettiva, invece di sovraacquistare e sperare che venga richiesta.

## <a name="automate"></a>Automatizzare

Una delle molte funzionalità che distinguono la familiarità delle organizzazioni con l'uso di provider cloud è il livello di automazione incorporato. L'automazione è un processo che non finisce mai e, man mano che l'organizzazione passa al cloud, richiede un investimento di risorse e denaro. L'automazione svolge molti scopi, inclusa l'implementazione coerente delle risorse (in cui si collega direttamente a un altro concetto di impalcatura principale, modelli e DevOps) alla correzione dei problemi. L'automazione è il tessuto connettivo dello scaffold Azure e tiene insieme ogni area.

Diversi strumenti consentono di sviluppare questa funzionalità, da strumenti di prima entità, ad esempio automazione di Azure, griglia di eventi e l'interfaccia della riga di comando di Azure, a un ampio numero di strumenti di terze parti, ad esempio bonifica, Jenkins, chef e Puppet. Gli strumenti di automazione di base includono automazione di Azure, griglia di eventi e il Azure Cloud Shell.

- **Automazione di Azure** È una funzionalità basata sul cloud che consente di creare manuali operativi (in PowerShell o Python) e consente di automatizzare i processi, configurare le risorse e persino applicare le patch. [Automazione di Azure](https://docs.microsoft.com/azure/automation/automation-intro) dispone di un'ampia gamma di funzionalità multipiattaforma che sono parte integrante della distribuzione ma sono troppo vaste per essere descritte in modo approfondito in questo articolo.
- **Griglia di eventi** è un sistema di routing di eventi completamente gestito che consente di reagire agli eventi nell'ambiente Azure. Così come automazione di Azure è il tessuto connettivo delle organizzazioni cloud mature, [griglia di eventi](https://docs.microsoft.com/azure/event-grid) è il tessuto connettivo di un'automazione efficace. Tramite griglia di eventi è possibile creare una semplice azione senza server per inviare un messaggio di posta elettronica a un amministratore ogni volta che viene creata una nuova risorsa e registrare tale risorsa in un database. Questa stessa griglia di eventi può comunicare quando una risorsa viene eliminata e rimuovere l'elemento dal database.
- **Azure cloud Shell** è una [Shell](https://docs.microsoft.com/azure/cloud-shell/overview) interattiva basata su browser per la gestione delle risorse in Azure. Offre un ambiente completo per PowerShell o Bash, che viene avviato quando serve (ed è gestito per l'utente), in modo da disporre di un ambiente coerente da cui eseguire gli script. Il Azure Cloud Shell fornisce l'accesso ad altri strumenti chiave, già installati, per automatizzare l'ambiente, tra cui l'interfaccia della riga di comando di [Azure](https://docs.microsoft.com/cli/azure/get-started-with-azure-cli?view=azure-cli-latest), la [bonifica](https://docs.microsoft.com/azure/virtual-machines/linux/terraform-install-configure) e un elenco in continua crescita di [strumenti](https://azure.microsoft.com/updates/cloud-shell-new-cli-tools-and-font-size-selection) aggiuntivi per gestire i contenitori, i database (sqlcmd) e più.

L'automazione è un processo a tempo pieno, che diventerà rapidamente una delle attività operative più importanti all'interno del team cloud. Le organizzazioni che adottano l'approccio "automatizzare prima di tutto" hanno più successo quando usano Azure:

- **Gestione dei costi:** Cerco attivamente opportunità e creazione di automazione per ridimensionare le risorse, aumentare o ridurre le prestazioni e disattivare le risorse inutilizzate.
- **Flessibilità operativa:** Con l'automazione (insieme a modelli e DevOps), si ottiene un livello di ripetibilità che consente di aumentare la disponibilità, aumentare la sicurezza e consentire al team di concentrarsi sulla risoluzione dei problemi aziendali.

## <a name="templates-and-devops"></a>Modelli e DevOps

Come evidenziato nella sezione sull'automazione, l'obiettivo in qualità di organizzazione dovrebbe essere effettuare il provisioning delle risorse tramite script e modelli controllati attraverso il codice sorgente e ridurre al minimo la configurazione interattiva degli ambienti. Questo approccio, denominato di "infrastruttura come codice", insieme a un processo DevOps disciplinato per la distribuzione continua può garantire la coerenza e ridurre le differenze nei vari ambienti. Quasi tutte le risorse di Azure possono essere distribuite tramite [modelli JSON di Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-template-deploy) in combinazione con PowerShell o con l'interfaccia della riga di comando multipiattaforma di Azure e strumenti come Terraform di Hashicorp, che garantisce un eccellente supporto ed è integrato in Azure Cloud Shell.

Un articolo come le procedure consigliate [per l'uso di modelli di Azure Resource Manager](https://blogs.msdn.microsoft.com/mvpawardprogram/2018/05/01/azure-resource-manager) fornisce un'ottima descrizione delle procedure consigliate e delle lezioni apprese per l'applicazione di un approccio DevOps ai modelli di Azure Resource Manager con [Azure DevOps](https://docs.microsoft.com/azure/devops/user-guide/?view=vsts) . . È possibile sviluppare un set di base di modelli specifici per i requisiti dell'organizzazione e sviluppare pipeline di recapito continuo con DevOps toolchain (ad esempio Azure DevOps, Jenkins, Bamboo, TeamCity e Concourse), in particolare per il ambienti di produzione e QA. È disponibile un'ampia libreria di [modelli di avvio rapido di Azure](https://github.com/Azure/azure-quickstart-templates) su GitHub che è possibile usare come punto di partenza per i modelli ed è possibile creare rapidamente pipeline di recapito basate sul cloud con Azure DevOps.

Come procedura consigliata per le sottoscrizioni o i gruppi di risorse di produzione, è consigliabile usare la sicurezza RBAC per non consentire gli utenti interattivi per impostazione predefinita e usare pipeline di recapito continuo automatizzate basate su entità servizio per il provisioning di tutte le risorse e recapitare tutto il codice dell'applicazione. Nessun amministratore o sviluppatore deve toccare il portale di Azure per configurare le risorse in modo interattivo. Questo livello di DevOps si impegna in un concerto e usa tutti i concetti dell'impalcatura di Azure, offrendo un ambiente coerente e più sicuro che soddisferà la necessità di ridimensionare la propria organizzazione.

> [!TIP]
> Durante la progettazione e lo sviluppo di modelli di Azure Resource Manager complessi, usare [modelli collegati](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-linked-templates) per organizzare ed effettuare il refactoring di relazioni complesse di risorse da file JSON compatti. Ciò consentirà di gestire le risorse singolarmente e di rendere i modelli più leggibili, testabili e riutilizzabili.

Azure è un provider di servizi cloud con iperscalabilità. Quando si sposta l'organizzazione dai server locali al cloud, basarsi sugli stessi concetti usati dai provider di servizi cloud e dalle applicazioni SaaS aiuterà l'organizzazione a rispondere alle esigenze dell'azienda in modo molto più efficiente.

## <a name="core-network"></a>Rete core

Il componente finale del modello di riferimento dello scaffold Azure è la base per la modalità in cui l'organizzazione accede ad Azure, in modo sicuro. È possibile accedere alle risorse dall'interno (nella rete di un'azienda) o dall'esterno (tramite Internet). Può capitare che gli utenti interni all'organizzazione inseriscano involontariamente le risorse nel punto sbagliato e le rendano vulnerabili all'accesso di utenti malintenzionati. Come per i dispositivi locali, le aziende devono aggiungere controlli appropriati per accertarsi che gli utenti di Azure prendano le decisioni giuste. Per la governance delle sottoscrizioni, vengono identificate le risorse principali che garantiscono il controllo di base degli accessi. Le risorse principali sono:

- **Reti virtuali**, cioè oggetti contenitore per le subnet. Sebbene non sia strettamente necessario, vengono spesso usate per la connessione delle applicazioni alle risorse aziendali interne.
- Le **route definite dall'utente** consentono di modificare la tabella di route all'interno di una subnet consentendo di inviare il traffico attraverso un'appliance virtuale di rete o a un gateway remoto in una rete virtuale con peering.
- Il **peering di rete virtuale** consente di connettere facilmente due o più reti virtuali di Azure, creando progettazioni Hub e spoke più complesse o reti di servizi condivisi.
- **Endpoint di servizio.** In passato, i servizi PaaS si basavano sui diversi metodi per proteggere l'accesso a queste risorse dalle reti virtuali. Gli endpoint di servizio consentono di proteggere l'accesso ai servizi PaaS abilitati **solo** da endpoint connessi, aumentando la sicurezza complessiva.
- I **gruppi di sicurezza** sono un ampio set di regole che consentono o negano il traffico in ingresso e in uscita verso/dalle risorse di Azure. I [gruppi di sicurezza](https://docs.microsoft.com/azure/virtual-network/security-overview) sono costituiti da regole di sicurezza che possono essere aumentate con i tag del **servizio** (che definiscono i servizi di Azure comuni, ad esempio Azure Key Vault o il database SQL di Azure) e i gruppi di **sicurezza delle applicazioni** (che definiscono l'applicazione struttura, ad esempio server Web o server applicazioni.

> [!TIP]
> Usare i tag di servizio e i gruppi di sicurezza delle applicazioni nei gruppi di sicurezza di rete non solo per migliorare la leggibilità delle regole &mdash;which è fondamentale per comprendere l'effetto &mdash;but anche per abilitare una microsegmentazione efficace all'interno di una subnet più grande, riduzione dell'espansione e maggiore flessibilità.

### <a name="azure-virtual-datacenter"></a>Data center virtuale di Azure

Azure offre sia funzionalità interne che funzionalità di terze parti provenienti dalla nostra ampia rete di partner, che consentono di disporre di una posizione di sicurezza efficace. Ancora più importante, Microsoft fornisce procedure consigliate e informazioni aggiuntive sotto forma di [data center virtuale di Azure (VCC)](./networking-vdc.md). Quando si passa da un singolo carico di lavoro a più carichi di lavoro che usano funzionalità ibride, le linee guida di data center virtuale forniscono "ricette" per abilitare una rete flessibile che aumenterà man mano che i carichi di lavoro in Azure crescono.

## <a name="next-steps"></a>Passaggi successivi

La governance è fondamentale per il successo di Azure. In questo articolo è descritta l'implementazione tecnica di uno scaffold enterprise, tuttavia sono illustrati solo il processo più ampio e le relazioni tra i componenti. La governance dei criteri scorre dall'alto verso il basso e dipende dai risultati che l'azienda desidera ottenere. Naturalmente, la creazione di un modello di governance per Azure include rappresentanti dell'IT, ma soprattutto deve prevedere una significativa rappresentanza di leader di gruppo aziendali e gestione di rischi e sicurezza. Fondamentalmente, uno scaffold enterprise consiste nella riduzione dei rischi aziendali per facilitare la missione e gli obiettivi dell'organizzazione.

Ora che sono state acquisite informazioni sulla governance delle sottoscrizioni, è il momento di vedere l'applicazione pratica di questi consigli. Per ulteriori informazioni, vedere le [procedure consigliate per la preparazione di Azure](../ready/azure-best-practices/index.md).
