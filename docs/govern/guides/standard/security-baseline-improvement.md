---
title: 'Guida aziendale standard: Migliorare la disciplina della linea di base di sicurezza'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Guida aziendale standard: Migliorare la disciplina della linea di base di sicurezza'
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 37d47b0a190506f84ed2b973b44ca731e70ad664
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71223776"
---
# <a name="standard-enterprise-guide-improve-the-security-baseline-discipline"></a>Guida aziendale standard: Migliorare la disciplina della linea di base di sicurezza

Questo articolo fa avanzare il racconto aggiungendo controlli di sicurezza che supportano lo spostare dati protetti nel cloud.

## <a name="advancing-the-narrative"></a>Avanzamento della descrizione

I responsabili IT e aziendali sono soddisfatti dei risultati della sperimentazione iniziale condotta dai team responsabili di IT, sviluppo di app e business intelligence. Per concretizzare valore tangibile per l'azienda da questi esperimenti, tali team devono essere autorizzati a integrare i dati protetti nelle soluzioni. Questa operazione attiva le modifiche ai criteri aziendali, ma richiede anche un miglioramento incrementale delle implementazioni di governance del cloud prima che i dati protetti possano essere presenti nel cloud.

### <a name="changes-to-the-cloud-governance-team"></a>Modifiche al team di governance del cloud

Dato l'effetto della modifica della descrizione e del supporto offerti finora, il team di governance del cloud viene ora visualizzato in modo diverso. I due amministratori di sistema che hanno avviato il team vengono ora considerati cloud architect esperti. Con lo sviluppo dello scenario, verranno percepiti inizialmente come custodi del cloud e infine più come guardiani del cloud.

Sebbene la differenza sia sottile, si tratta di una distinzione importante per lo sviluppo di una cultura IT orientata alla governance. Un custode del cloud mette a posto i pasticci di cloud architect innovativi. I due ruoli hanno obiettivi naturalmente in conflitto e opposti. Lo scopo di un guardiano del cloud è invece quello di mantenere sicuro il cloud, in modo che altri cloud architect possano procedere rapidamente, senza troppi pasticci. Inoltre, un tutore cloud è impegnato nella creazione di modelli che accelerano la distribuzione e l'adozione, rendendoli un acceleratore di innovazione e un difensore delle cinque discipline della governance del cloud.

### <a name="changes-in-the-current-state"></a>Modifiche nello stato corrente

All'inizio di questo scenario, i team di sviluppo delle applicazioni lavoravano ancora in modalità sviluppo/test e il team di business intelligence era ancora in fase di sperimentazione. Il reparto IT gestiva operativamente due ambienti di infrastruttura ospitati, denominati PROD e DR.

Da allora, sono avvenuti alcuni cambiamenti che influiranno sulla governance:

- Il team di sviluppo di applicazioni ha implementato una pipeline CI/CD per distribuire un'applicazione nativa del cloud con un'esperienza utente migliorata. L'app interagisce ancora con i dati protetti, pertanto non è pronta per l'ambiente di produzione.
- Il team di business intelligence al suo interno ha curato attivamente i dati nel cloud dalla logistica, dall'inventario e dalle fonti di terze parti. Questi dati vengono usati per effettuare nuove stime, che possono influire sui processi aziendali. Tuttavia, queste stime e informazioni dettagliate non hanno utilità pratica fino a quando i dati finanziari e dei clienti non possono essere integrati nella piattaforma di dati.
- Il team IT sta procedendo con i piani del CIO e del CFO per il ritiro del data center DR. Più di 1.000 dei 2.000 asset nel data center DR sono stati ritirati o migrati.
- Sono stati modernizzati i criteri definiti in termini di dati personali e finanziari. Tuttavia, i nuovi criteri aziendali dipendono dall'implementazione dei criteri di governance e sicurezza correlati. I team sono ancora bloccati.

### <a name="incrementally-improve-the-future-state"></a>Migliorare in modo incrementale lo stato futuro

Dagli esperimenti iniziali dei team di sviluppo delle applicazioni e di business intelligence è emersa la possibilità di apportare miglioramenti per quanto riguarda l'esperienza dei clienti e le decisioni basate sui dati. Entrambi i team voglio espandere l'adozione del cloud nei prossimi 18 mesi distribuendo tali soluzioni nell'ambiente di produzione.

Durante i restanti sei mesi, il team di governance del cloud implementerà i requisiti di sicurezza e governance per consentire ai team di adozione del cloud di migrare i dati protetti in questi Data Center.

I cambiamenti che riguardano lo stato attuale e quello futuro creano nuovi rischi che richiedono nuove definizioni di criteri.

## <a name="changes-in-tangible-risks"></a>Modifiche ai rischi tangibili

**Violazione dei dati:** quando si adotta qualsiasi nuova piattaforma di dati, si verifica un aumento intrinseco delle responsabilità correlate alle potenziali violazioni dei dati. I tecnici che adottano le tecnologie cloud hanno maggiori responsabilità di implementare soluzioni in grado di ridurre questo rischio. È necessario implementare una solida strategia di governance e sicurezza per fare in modo che i tecnici adempiano a queste responsabilità.

Questo rischio aziendale può comportare alcuni rischi tecnici:

1. Le applicazioni mission-critical o i dati protetti potrebbero essere distribuiti involontariamente.
2. Dati protetti potrebbero venire esposti in fase di archiviazione a causa di scelte non adeguate in relazione alla crittografia.
3. Utenti non autorizzati potrebbero accedere ai dati protetti.
4. Un'intrusione esterna potrebbe consentire l'accesso ai dati protetti.
5. Eventuali intrusioni dall'esterno o attacchi Denial of Service potrebbero causare un'interruzione delle attività aziendali.
6. Modifiche all'interno dell'organizzazione o tra i dipendenti potrebbero consentire l'accesso non autorizzato ai dati protetti.
7. Nuovi exploit potrebbero creare nuove opportunità di intrusione o accesso.
8. Processi di distribuzione incoerenti potrebbero produrre lacune a livello di sicurezza che possono causare perdite di dati o interruzioni.
9. Deviazioni di configurazione e patch non applicate potrebbero produrre lacune a livello di sicurezza non intenzionali che possono causare perdite di dati o interruzioni.

## <a name="incremental-improvement-of-the-policy-statements"></a>Miglioramento incrementale delle istruzioni dei criteri

Le seguenti modifiche ai criteri consentono di monitorare e aggiornare i nuovi rischi e l'implementazione della guida. L'elenco può sembrare lungo, ma l'adozione di questi criteri può essere più semplice di quanto non sembri.

1. tutti gli asset distribuiti devono essere ordinati in categorie in base a criticità e classificazione dei dati. Le classificazioni devono essere esaminate dal team di governance del cloud e dal proprietario dell'applicazione prima della distribuzione nel cloud.
2. Le applicazioni che archiviano o accedono ai dati protetti devono essere gestite in modo diverso rispetto a quelle che non lo fanno. Come minimo, devono essere segmentate per evitare accessi non intenzionali ai dati protetti.
3. tutti i dati protetti devono essere crittografati quando inattivi. Anche se questa è l'impostazione predefinita per tutti gli account di archiviazione di Azure, potrebbero essere necessarie strategie di crittografia aggiuntive, inclusa la crittografia dei dati nell'account di archiviazione, la crittografia delle VM e la crittografia a livello di database se si usa SQL in una VM (Transparent Data Encryption e colonna) crittografia).
4. Le autorizzazioni con privilegi elevati in qualsiasi segmento contenente dati protetti devono essere un'eccezione. Tali eccezioni verranno registrate con il team di governance del cloud e controllate regolarmente.
5. le subnet di rete contenenti dati protetti devono essere isolate dalle altre subnet. Il traffico di rete tra le subnet di dati protetti verrà controllato regolarmente.
6. Alle subnet contenenti dati protetti non deve essere possibile accedere direttamente tramite la rete Internet pubblica o tra data center. L'accesso a tali subnet deve essere instradato tramite subnet intermedie. Tutti gli accessi a tali subnet devono passare attraverso una soluzione firewall in grado di eseguire la scansione dei pacchetti e applicare funzioni di blocco.
7. Gli strumenti di governance devono controllare e soddisfare i requisiti di configurazione della rete definiti dal team di gestione della sicurezza.
8. Gli strumenti di governance devono limitare la distribuzione di macchine virtuali solo alle immagini approvate.
9. Quando possibile, la gestione della configurazione dei nodi deve applicare i requisiti dei criteri alla configurazione di qualsiasi sistema operativo guest.
10. Gli strumenti di governance devono imporre l'abilitazione degli aggiornamenti automatici per tutti gli asset distribuiti. Le violazioni devono essere esaminate con i team di gestione operativa e risolte in base ai criteri relativi alle operazioni. Gli asset che non vengono aggiornati automaticamente devono essere inclusi in processi di proprietà del team responsabile delle operazioni IT.
11. La creazione di nuove sottoscrizioni o gruppi di gestione per tutte le applicazioni cruciali o i dati protetti richiederà una revisione da parte del team di governance del cloud, per assicurare che venga assegnato il progetto appropriato.
12. Un modello di accesso con privilegi minimi verrà applicato a qualsiasi gruppo di gestione o sottoscrizione che contiene app cruciali o dati protetti.
13. Tendenze ed exploit che possono influire sulle distribuzioni cloud devono essere esaminati regolarmente dal team responsabile della sicurezza in modo da fornire aggiornamenti per gli strumenti di gestione della sicurezza usati nel cloud.
14. Gli strumenti di distribuzione devono essere approvati dal team di governance del cloud per garantire la governance continua degli asset distribuiti.
15. Gli script di distribuzione devono essere conservati in un repository centrale accessibile dal team di governance del cloud per la revisione e il controllo periodici.
16. I processi di governance devono includere controlli in fase di distribuzione e in base a cicli regolari per garantire la coerenza tra tutti gli asset.
17. Per la distribuzione di applicazioni che richiedono l'autenticazione del cliente è necessario usare un provider di identità approvato compatibile con il provider di identità primario per gli utenti interni.
18. I processi di governance del cloud devono includere revisioni trimestrali con i team di gestione delle identità. Queste revisioni possono essere utili per identificare attori o modelli di utilizzo dannosi, che dovrebbero essere bloccati dalla configurazione degli asset del cloud.

## <a name="incremental-improvement-of-governance-practices"></a>Miglioramento incrementale delle procedure di governance

La progettazione degli MVP di governance cambierà in modo da includere i nuovi criteri di Azure e un'implementazione di gestione costi di Azure. Insieme, queste due modifiche di progettazione riusciranno a soddisfare le nuove istruzioni dei criteri aziendali.

1. I team responsabili della rete e della sicurezza IT definiranno i requisiti di rete. Il team di governance del cloud supporterà la conversazione.
2. I team responsabili delle identità e della sicurezza IT definiranno i requisiti di identità e apporteranno le eventuali modifiche necessarie all'implementazione di Active Directory locale. Il team di governance del cloud verificherà le modifiche.
3. Creare un archivio in Azure DevOps per l'archiviazione e il controllo delle versioni di tutti i modelli di Azure Resource Manager e le configurazioni tramite script pertinenti.
4. Implementazione del Centro sicurezza di Azure:
    1. Configurare il Centro sicurezza di Azure per qualsiasi gruppo di gestione che contiene le classificazioni dei dati protetti.
    2. Attivare il provisioning automatico per impostazione predefinita per garantire la conformità delle patch.
    3. Definire configurazioni di sicurezza del sistema operativo. La configurazione verrà definita dal team responsabile della sicurezza IT.
    4. Supportare il team responsabile della sicurezza IT per l'uso iniziale del Centro sicurezza. Passare la responsabilità dell'uso del Centro sicurezza al team responsabile della sicurezza IT, ma mantenere l'accesso allo scopo di migliorare continuamente la governance.
    5. Creare un modello di Resource Manager che riflette le modifiche necessarie per la configurazione del Centro sicurezza all'interno di una sottoscrizione.
5. Aggiornare i criteri di Azure per tutte le sottoscrizioni:
    1. Controllare e applicare la criticità e la classificazione dei dati in tutti i gruppi di gestione e le sottoscrizioni per identificare quelle con classificazioni di dati protetti.
    2. Controllare e imporre l'uso delle sole immagini approvate.
6. Aggiornare i criteri di Azure per tutte le sottoscrizioni che contengono classificazioni di dati protetti:
    1. Controllare e imporre l'uso dei soli ruoli di controllo degli accessi in base al ruolo di Azure.
    2. Controllo e imporre la crittografia per tutti gli account di archiviazione e i file inattivi nei singoli nodi.
    3. Controllare e imporre l'applicazione di un gruppo di sicurezza di rete per tutte le schede di interfaccia di rete e subnet. I team responsabili della rete e della sicurezza IT definiranno il gruppo di sicurezza di rete.
    4. Controllare e imporre l'uso di reti virtuali e subnet di rete approvate per ogni interfaccia di rete.
    5. Controllare e imporre la limitazione delle tabelle di routing definite dall'utente.
    6. Applicare i criteri predefiniti per la configurazione guest come indicato di seguito:
        1. Controllare che i server Web Windows usino protocolli di comunicazione sicuri.
        2. Controllare che le impostazioni di sicurezza della password siano configurate correttamente nelle macchine virtuali Linux e Windows.
7. Configurazione del firewall:
    1. Identificare una configurazione di Firewall di Azure che soddisfi i requisiti di sicurezza necessari. In alternativa, identificare un'appliance di terze parti compatibile con Azure.
    2. Creare un modello di Resource Manager per distribuire il firewall con le configurazioni necessarie.
8. Azure Blueprints:
    1. Creare un nuovo progetto denominato `protected-data`.
    2. Aggiungere il firewall e i modelli del Centro sicurezza di Azure al progetto.
    3. Aggiungere i nuovi criteri per le sottoscrizioni con dati protetti.
    4. Pubblicare il progetto in un gruppo di gestione che attualmente prevede l'hosting dei dati protetti.
    5. Applicare il nuovo progetto a ogni sottoscrizione interessata, nonché ai progetti esistenti.

## <a name="conclusion"></a>Conclusione

L'aggiunta dei processi e delle modifiche precedenti all'MVP di governance consente di correggere molti dei rischi associati alla governance della sicurezza. Nel loro insieme aggiungono gli strumenti per il monitoraggio di rete, identità e sicurezza necessari per proteggere i dati.

## <a name="next-steps"></a>Passaggi successivi

Quando l'adozione del cloud continua e offre un valore aziendale aggiuntivo, anche i rischi e le esigenze di governance del cloud cambiano. Per la società fittizia in questa guida, il passaggio successivo consiste nel supportare i carichi di lavoro cruciali. Questo è il punto in cui diventano necessari i controlli di coerenza delle risorse.

> [!div class="nextstepaction"]
> [Miglioramento della coerenza delle risorse](./resource-consistency-improvement.md)
