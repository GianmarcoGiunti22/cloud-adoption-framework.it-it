---
title: 'Guida alla governance per le aziende complesse: Migliorare la disciplina della coerenza delle risorse'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Guida alla governance per le aziende complesse: Migliorare la disciplina della coerenza delle risorse'
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 7e10f9262e7b29df98e2341cbae0ef05f85cd954
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71030535"
---
# <a name="governance-guide-for-complex-enterprises-improve-the-resource-consistency-discipline"></a>Guida alla governance per le aziende complesse: Migliorare la disciplina della coerenza delle risorse

Questo articolo fa avanzare il racconto aggiungendo controlli di coerenza delle risorse all'MVP della governance per supportare le applicazioni cruciali.

## <a name="advancing-the-narrative"></a>Avanzamento della descrizione

I team di adozione del cloud hanno soddisfatto tutti i requisiti per lo spostamento dei dati protetti. Con tali applicazioni entrano in gioco anche gli impegni per i contratti di servizio con l'azienda e la necessità di supporto dal team responsabile delle operazioni IT. Dietro il team che esegue la migrazione dei due Data Center, lo sviluppo di più applicazioni e i team di business intelligence sono pronti per iniziare a avviare nuove soluzioni nell'ambiente di produzione. Le operazioni IT sono nuove per le operazioni cloud ed è necessario integrare rapidamente i processi operativi esistenti.

### <a name="changes-in-the-current-state"></a>Modifiche nello stato corrente

- Il reparto IT si sta occupando attivamente dello spostamento dei carichi di lavoro di produzione con dati protetti in Azure. Alcuni carichi di lavoro con priorità bassa servono il traffico di produzione. Un maggior numero di operazioni può essere ridotto non appena le operazioni vengono disattivate in conformità per supportare i carichi di lavoro.
- I team di sviluppo delle applicazioni sono pronti per il traffico di produzione.
- Il team di business intelligence è pronto per l'integrazione di stime e informazioni dettagliate nei sistemi che eseguono le operazioni per le tre business unit.

### <a name="incrementally-improve-the-future-state"></a>Migliorare in modo incrementale lo stato futuro

- Le operazioni IT sono nuove per le operazioni cloud ed è necessario integrare rapidamente i processi operativi esistenti.
- I cambiamenti che riguardano lo stato attuale e quello futuro espongono a nuovi rischi che richiedono nuove definizioni di criteri.

## <a name="changes-in-tangible-risks"></a>Modifiche ai rischi tangibili

**Interruzione aziendale:** vi è un rischio intrinseco che qualsiasi nuova piattaforma possa causare l'interruzione di processi aziendali cruciali. Il team responsabile delle operazioni IT e i team che si occupano in vari modi delle adozioni del cloud sono relativamente inesperti per quanto riguarda le operazioni nel cloud. Questa operazione aumenta il rischio di interruzione e deve essere risolta e regolata.

Questo rischio aziendale può tradursi in diversi rischi tecnici:

1. I processi operativi non allineati possono causare interruzioni che non possono essere rilevate o mitigate rapidamente.
2. Eventuali intrusioni dall'esterno o attacchi Denial of Service potrebbero causare un'interruzione delle attività aziendali.
3. È possibile che asset cruciali non vengano individuati nel modo appropriato e pertanto non vengano gestiti correttamente.
4. Gli asset non individuati o mal definiti possono non essere supportati dai processi di gestione operativa esistenti.
5. La configurazione degli asset distribuiti potrebbe non soddisfare le aspettative in termini di prestazioni.
6. La registrazione potrebbe non essere effettuata e centralizzata correttamente per consentire la risoluzione dei problemi di prestazioni.
7. Le procedure di ripristino possono non riuscire o impiegare più tempo del previsto.
8. Processi di distribuzione incoerenti potrebbero produrre lacune a livello di sicurezza che possono causare perdite di dati o interruzioni.
9. Deviazioni di configurazione e patch non applicate potrebbero produrre lacune a livello di sicurezza non intenzionali che possono causare perdite di dati o interruzioni.
10. La configurazione potrebbe non soddisfare i requisiti dei contratti di servizio definiti o quelli di ripristino concordati.
11. Le applicazioni o i sistemi operativi distribuiti potrebbero non soddisfare i requisiti di protezione avanzata del sistema operativo o delle applicazioni.
12. Esiste il rischio di incoerenza a causa dei numerosi team che lavorano nel cloud.

## <a name="incremental-improvement-of-the-policy-statements"></a>Miglioramento incrementale delle istruzioni dei criteri

Le seguenti modifiche ai criteri consentono di monitorare e aggiornare i nuovi rischi e l'implementazione della guida. L'elenco può sembrare lungo, ma l'adozione di questi criteri può essere più semplice di quanto non sembri.

1. tutti gli asset distribuiti devono essere ordinati in categorie in base a criticità e classificazione dei dati. Le classificazioni devono essere esaminate dal team di governance del cloud e dal proprietario dell'applicazione prima della distribuzione nel cloud.
2. Le subnet che contengono applicazioni cruciali devono essere protette tramite una soluzione firewall in grado di rilevare le intrusioni e rispondere agli attacchi.
3. Gli strumenti di governance devono controllare e soddisfare i requisiti di configurazione definiti dal team della baseline di sicurezza.
4. Gli strumenti di governance devono convalidare che tutti gli asset correlati alle applicazioni cruciali o ai dati protetti siano inclusi nel monitoraggio per l'esaurimento e l'ottimizzazione delle risorse.
5. Gli strumenti di governance devono convalidare che venga raccolto il livello appropriato di dati di registrazione per tutti i dati protetti o le applicazioni cruciali.
6. Il processo di governance deve convalidare che il backup, il ripristino e il rispetto dei contratti di servizio vengano implementati correttamente per le applicazioni cruciali e i dati protetti.
7. Gli strumenti di governance devono limitare la distribuzione di macchine virtuali solo alle immagini approvate.
8. Gli strumenti di governance devono soddisfare il requisito in base al quale gli aggiornamenti automatici **non** devono essere applicati a tutti gli asset distribuiti che supportano applicazioni cruciali. Le violazioni devono essere esaminate con i team di gestione operativa e risolte in base ai criteri relativi alle operazioni. Gli asset che non vengono aggiornati automaticamente devono essere inclusi in processi di proprietà del team responsabile delle operazioni IT.
9. Gli strumenti di governance devono convalidare l'assegnazione di tag correlati a costo, criticità, contratto di servizio, applicazione e classificazione dei dati. Tutti i valori devono essere allineati ai valori predefiniti gestiti dal team di governance del cloud.
10. I processi di governance devono includere controlli in fase di distribuzione e in base a cicli regolari per garantire la coerenza tra tutti gli asset.
11. Tendenze ed exploit che possono influire sulle distribuzioni cloud devono essere esaminati regolarmente dal team responsabile della sicurezza in modo da fornire aggiornamenti per gli strumenti della baseline di sicurezza usati nel cloud.
12. Prima del rilascio in produzione, è necessario aggiungere tutte le applicazioni cruciali e i dati protetti alla soluzione di monitoraggio operativa designata. Gli asset che non possono essere individuati dagli strumenti per le operazioni IT scelti non possono essere distribuiti nell'ambiente di produzione. Qualsiasi modifica necessaria per rendere gli asset individuabili deve essere apportata ai processi di distribuzione pertinenti per garantire che gli asset siano individuabili nelle distribuzioni future.
13. Quando viene individuato, il dimensionamento delle risorse deve essere convalidato dai team di gestione operativi per verificare che l'asset soddisfi i requisiti di prestazioni.
14. Gli strumenti di distribuzione devono essere approvati dal team di governance del cloud per garantire la governance continua degli asset distribuiti.
15. Gli script di distribuzione devono essere conservati nel repository centrale accessibile dal team di governance del cloud per la revisione e il controllo periodici.
16. I processi di revisione della governance devono convalidare che gli asset distribuiti siano configurati correttamente in base ai requisiti relativi a contratti di servizio e ripristino.

## <a name="incremental-improvement-of-the-best-practices"></a>Miglioramento incrementale delle procedure consigliate

Questa sezione dell'articolo consentirà di migliorare la progettazione degli MVP di governance per includere nuovi criteri di Azure e un'implementazione di gestione costi di Azure. Insieme, queste due modifiche di progettazione riusciranno a soddisfare le nuove istruzioni dei criteri aziendali.

Seguendo l'esperienza di questo esempio fittizio, si presuppone che le modifiche ai dati protetti si siano già verificate. Sulla base di tale procedura consigliata, di seguito verranno aggiunti requisiti di monitoraggio operativo, per preparare una sottoscrizione per applicazioni cruciali.

**Sottoscrizione IT aziendale:** Aggiungere quanto segue alla sottoscrizione IT aziendale, che funge da hub.

1. Come dipendenza esterna, il team operativo cloud dovrà definire gli strumenti per il monitoraggio operativo, la continuità aziendale e il ripristino di emergenza (BCDR) e gli strumenti per la correzione automatica. Il team di governance del cloud può quindi supportare i processi di individuazione necessari.
    1. In questo caso di utilizzo, il team operativo cloud ha scelto monitoraggio di Azure come strumento principale per il monitoraggio di applicazioni cruciali.
    1. Il team ha inoltre scelto Azure Site Recovery come strumento BCDR primario.
1. Implementazione di Azure Site Recovery.
    1. Definire e distribuire l'insieme di credenziali di Azure per i processi di backup e ripristino.
    1. Creare un modello di gestione risorse di Azure per la creazione di un insieme di credenziali in ogni sottoscrizione.
1. Implementazione di monitoraggio di Azure.
    1. Una volta identificata una sottoscrizione cruciale, è possibile creare un'area di lavoro di Log Analytics tramite PowerShell. Si tratta di un processo di pre-distribuzione.

**Sottoscrizione per l'adozione di singoli cloud:** gli elementi seguenti assicurano che ogni sottoscrizione sia individuabile dalla soluzione di monitoraggio e pronta per essere inclusa nelle procedure BCDR.

1. Criteri di Azure per i nodi mission-critical:
    1. Controllare e imporre l'uso solo dei ruoli standard.
    1. Controllare e imporre l'applicazione della crittografia per tutti gli account di archiviazione.
    1. Controllare e imporre l'uso di reti virtuali e subnet di rete approvate per ogni interfaccia di rete.
    1. Controllare e imporre la limitazione delle tabelle di routing definite dall'utente.
    1. Controllare e imporre la distribuzione di agenti di Log Analytics per macchine virtuali Windows e Linux.
2. Azure Blueprints:
    1. Creare un progetto denominato `mission-critical-workloads-and-protected-data`. Questo progetto applicherà gli asset oltre al progetto per i dati protetti.
    1. Aggiungere i nuovi criteri di Azure al progetto.
    1. Applicare il progetto a qualsiasi sottoscrizione che si prevede ospiti un'applicazione cruciale.

## <a name="conclusion"></a>Conclusione

L'aggiunta di questi processi e modifiche all'MVP di governance consente di correggere molti dei rischi associati alla governance delle risorse. Insieme, aggiungono i controlli di ripristino, ridimensionamento e monitoraggio necessari per le operazioni basate sul cloud.

## <a name="next-steps"></a>Passaggi successivi

Man mano che l'adozione del cloud aumenta e offre un valore aziendale aggiuntivo, anche i rischi e le esigenze di governance del cloud cambiano. Per la società fittizia in questa guida, il trigger successivo si verifica quando la scalabilità della distribuzione supera 1.000 risorse al cloud o la spesa mensile supera $10.000 USD al mese. A questo punto, il team di governance del cloud aggiunge i controlli di gestione dei costi.

> [!div class="nextstepaction"]
> [Migliorare la disciplina di gestione dei costi](./cost-management-improvement.md)
