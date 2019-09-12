---
title: Risoluzione dei problemi legati alla complessità della migrazione di più aree geografiche
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Risoluzione dei problemi legati alla complessità della migrazione di più aree geografiche.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 3977618981212e2c0dc4dcd95ae14bf4dc773499
ms.sourcegitcommit: 5846ed4d0bf1b6440f5e87bc34ef31ec8b40b338
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2019
ms.locfileid: "70905596"
---
# <a name="multiple-geographic-regions"></a>Più aree geografiche

Quando le aziende operano in più aree geografiche è possibile che si aggiunga ulteriore complessità alle attività di migrazione al cloud. Queste complessità si manifestano in tre forme principali: distribuzione di risorse, profili di accesso utente e requisiti di conformità. Prima di affrontare le complessità correlate a più aree è importante riconoscere la portata della complessità potenziale.

## <a name="general-scope-expansion"></a>Espansione dell'ambito generale

L'approccio seguente consente di valutare i potenziali problemi e stabilire una linea di condotta generale:

- Prendere in considerazione una più solida preparazione e attuazione della governance.
- Rilevare le aree geografiche interessate. Compilare un elenco delle aree e dei paesi interessati dalla migrazione al cloud.
- Requisiti di sovranità dei dati del documento: I paesi identificati dispongono dei requisiti di conformità che regolano la sovranità dei dati?
- Documentare la base utenti: I dipendenti, i partner o i clienti del paese identificato saranno interessati dalla migrazione al cloud?
- Data center e risorse del documento: Nel paese identificato, sono presenti risorse che potrebbero essere incluse nel lavoro richiesto per la migrazione?

Allineare le modifiche nel processo di migrazione per affrontare l'inventario iniziale.

### <a name="documenting-complexity"></a>Documentazione della complessità

La tabella seguente può aiutare a documentare i risultati dei passaggi precedenti:

|Region  |Country  |Dipendenti locali  |Utenti esterni locali  |Data center o risorse locali |Requisiti di sovranità dei dati  |
|---------|---------|---------|---------|---------|---------|
|America del Nord     |Stati Uniti         |Sì         |Partner e clienti         |Sì         |No         |
|America del Nord     |Canada         |No         |Clienti         |Yes         |Sì         |
|Europa     |Germania         |Sì         |Partner e clienti         |No: nessuna rete         |Sì         |
|Asia/Pacifico     |Corea del Sud         |Sì         |Partner         |Yes         |No         |

<!-- markdownlint-disable MD026 -->

### <a name="why-is-data-sovereignty-relevant"></a>Perché la sovranità dei dati è rilevante?

In tutto il mondo, le organizzazioni governative hanno iniziato a definire i requisiti di sovranità dei dati; un esempio è dato dal Regolamento generale sulla protezione dei dati (GDPR). I requisiti di conformità di questa natura richiedono spesso la localizzazione in un'area specifica o in un paese specifico, per proteggere i propri cittadini. In alcuni casi, i dati relativi a clienti, dipendenti o partner devono essere archiviati in una piattaforma cloud nella stessa area dell'utente finale.

Affrontare questa sfida ha costituito una motivazione significativa per le migrazioni al cloud di aziende che operano su scala globale. Per mantenere i requisiti di conformità, alcune aziende hanno scelto di distribuire le risorse IT duplicate ai provider di servizi cloud all'interno dell'area. Nella tabella di esempio precedente, la Germania rappresenta un valido esempio di questo scenario. In questo esempio sono presenti clienti, partner e dipendenti in Germania, ma non le risorse IT esistenti. Questa società può scegliere di distribuire alcune risorse in un data center all'interno dell'area GDPR, potenzialmente anche usando i data center di Azure in Germania. Il riconoscimento dei dati interessati dal GDPR aiuta il team di adozione del cloud a comprendere qual è in questo caso il migliore approccio alla migrazione.

### <a name="why-is-the-location-of-end-users-relevant"></a>Perché la posizione degli utenti finali è rilevante?

Le aziende che supportano gli utenti finali in più paesi hanno sviluppato soluzioni tecniche per l'indirizzamento del traffico verso gli utenti finali. In alcuni casi, questo implica la localizzazione delle risorse. In altri scenari, l'azienda può invece scegliere di implementare soluzioni WAN globali per gestire basi utente diverse tramite soluzioni incentrate sulla rete. In entrambi i casi, la strategia di migrazione potrebbe essere influenzata dai profili d'uso degli utenti finali diversi.

Poiché l'azienda supporta dipendenti, partner e clienti in Germania, ma non dispone attualmente di data center in quel paese, è probabile che abbia implementato una forma di soluzione a linea dedicata per indirizzare il traffico ai data center di altri paesi. Questo routing esistente presenta un rischio significativo per le prestazioni percepite delle applicazioni sottoposte a migrazione. L'inserimento di hop aggiuntivi in una WAN globale stabilita e ottimizzata può creare la percezione di avere applicazioni con prestazioni scarse dopo la migrazione. L'individuazione e la correzione di tali problemi può comportare ritardi significativi a un progetto. In ogni processo riportato di seguito, le informazioni aggiuntive per risolvere questa complessità sono incluse nei prerequisiti, nella valutazione, nella migrazione e nell'ottimizzazione dei processi. Il riconoscimento dei profili utente in ogni paese è essenziale per gestire correttamente questa complessità.

### <a name="why-is-the-location-of-datacenters-relevant"></a>Perché la posizione dei data center è rilevante?

La posizione dei data center esistenti può influire sulla strategia di migrazione. Di seguito sono riportati alcuni degli effetti più comuni:

**Decisioni relative all'architettura:** Area o percorso di destinazione: uno dei primi passaggi nella progettazione della strategia di migrazione. Spesso viene influenzato dalla posizione delle risorse esistenti. Inoltre, la disponibilità dei servizi cloud e il costo unitario di tali servizi possono variare da un'area all'altra. Di conseguenza, il riconoscimento del percorso corrente e futuro delle risorse influisce sulle decisioni relative all'architettura e può inoltre influenzare le stime del budget.

**Dipendenze tra data center:** In base ai dati nella tabella precedente, è probabile che esistano dipendenze tra i vari data center in tutto il mondo. In molte organizzazioni che operano in questo tipo di scalabilità, tali dipendenze potrebbero non essere documentate o riconosciute. Gli approcci usati per valutare i profili utente consentiranno di identificare alcune di queste dipendenze. Tuttavia, durante il processo di valutazione vengono suggeriti passaggi aggiuntivi per attenuare i rischi associati a questa complessità.

## <a name="implementing-the-general-approach"></a>Implementazione dell'approccio generale

Questo approccio è basato su informazioni quantificabili. Di conseguenza, l'approccio seguente segue un modello basato su dati per risolvere le complessità della migrazione globale.

## <a name="suggested-prerequisites"></a>Prerequisiti suggeriti

È consigliabile che il team di adozione del cloud inizi con la migrazione di un semplice carico di lavoro usando la [Guida alla migrazione di Azure](../azure-migration-guide/index.md), prima di tentare di affrontare il ridimensionamento globale. In questo modo il team acquisisce familiarità con il processo generale di migrazione al cloud prima di tentare uno scenario di migrazione più complesso.

Quando l'ambito di una migrazione include più aree, il team di adozione del cloud deve tenere conto delle considerazioni seguenti sulla conformità:

- La sovranità dei dati potrebbe richiedere la localizzazione di alcune risorse, ma ne sono presenti molte che potrebbero non essere regolate da tali vincoli di conformità. Registrazione, creazione di report, routing di rete, identità e altri servizi IT centrali possono essere ospitati come servizi condivisi tra più sottoscrizioni o più aree. Si consiglia al team di adozione del cloud di valutare un modello di servizio di condivisione per tali servizi, come descritto nell'[architettura di riferimento per una topologia hub-spoke con servizi condivisi](/azure/architecture/reference-architectures/hybrid-networking/shared-services)
- Quando si distribuiscono più istanze di ambienti simili, una factory di ambiente potrebbe creare coerenza, migliorare la governance e accelerare la distribuzione. Il [grande percorso di governance aziendale](../../governance/journeys/complex-enterprise/index.md) stabilisce un approccio che consente di creare una factory di ambiente scalabile in più aree.

Una volta che la conformità è allineata e il team ha acquisito familiarità con l'approccio di base, bisogna considerare alcuni prerequisiti basati sui dati:

- **Individuazione generale:** Completare la tabella precedente relativa alla [Documentazione della complessità](#documenting-complexity).
- **Eseguire un'analisi del profilo utente per ogni paese interessato:** È importante riconoscere il routing generale degli utenti finali all'inizio del processo di migrazione. La modifica delle linee di lease globali e l'aggiunta di connessioni come ExpressRoute a un data center cloud può comportare mesi di ritardi di rete. Risolvere il problema nel processo il prima possibile.
- **Razionalizzazione iniziale del digital estate:** Ogni volta che viene introdotta complessità in una strategia di migrazione è necessario completare una razionalizzazione iniziale del digital estate. Per assistenza, vedere le linee guida sulla [razionalizzazione del digital estate](../../digital-estate/index.md).
  - **Requisiti digitale estate aggiuntivi:** Definire i criteri di assegnazione di tag per identificare qualsiasi carico di lavoro interessato dai requisiti di sovranità dei dati. Nella razionalizzazione del digital estate è necessario partire con i tag obbligatori per proseguire fino alle risorse sottoposte a migrazione.
- **Valutare un modello hub-spoke:** I sistemi distribuiti condividono spesso dipendenze comuni. Tali dipendenze possono essere risolte tramite l'implementazione di un modello hub-spoke. Anche se un modello di questo tipo non è compreso nel processo di migrazione è consigliabile contrassegnarlo per la valutazione durante le iterazioni future dei [Processi pronti](../../ready/index.md).
- **Dare priorità al backlog di migrazione:** Se sono necessarie modifiche alla rete per supportare la distribuzione di produzione di un carico di lavoro che supporta più aree, il team di strategia cloud deve tenere traccia e gestire le escalation relative a tali modifiche. L'alto livello di supporto tecnico Executive contribuisce ad accelerare la modifica. Tuttavia, l'aspetto più importante è fornire al team di strategia la possibilità di ridefinire la priorità del backlog per garantire che i carichi di lavoro globali non siano stati bloccati dalle modifiche alla rete. Tali carichi di lavoro devono essere classificati in ordine di priorità solo dopo il completamento delle modifiche alla rete.

Questi prerequisiti consentono di definire i processi che possono risolvere questa complessità durante l'esecuzione della strategia di migrazione.

## <a name="assess-process-changes"></a>Modifiche del processo di valutazione

È bene aggiungere alcune attività chiave alla valutazione di qualsiasi candidato alla migrazione nella gestione delle complessità globali di base di risorse e utenti. Ognuna di queste modifiche renderà più chiaro l'effetto sugli utenti e sulle risorse globali, grazie a un approccio basato sui dati.

### <a name="suggested-action-during-the-assess-process"></a>Azione suggerita durante il processo di valutazione

**Valutare le dipendenze tra data center:** gli [strumenti di visualizzazione delle dipendenze in Azure Migrate](/azure/migrate/concepts-dependency-visualization) consentono di individuare le dipendenze. L'uso di questo set di strumenti prima della migrazione è un'ottima procedura consigliata generale. Questo set di strumenti diventa tuttavia un passaggio necessario del processo di valutazione quando si gestiscono complessità globali. Tramite il [raggruppamento delle dipendenze](/azure/migrate/how-to-create-group-machine-dependencies), la visualizzazione consente di identificare gli indirizzi IP e le porte di tutti gli asset necessari per supportare il carico di lavoro.

> [!IMPORTANT]
> Due note importanti: In primo luogo, è necessario un esperto con una conoscenza degli schemi di posizionamento degli asset e degli indirizzi IP per identificare gli asset che si trovano in un data center secondario. In secondo luogo, è importante valutare i Client e le dipendenze downstream per riconoscere le dipendenze bidirezionali.

**Identificare l'impatto utente globale:** Gli output dall'analisi dei profili utente prerequisiti dovrebbero identificare qualsiasi carico di lavoro interessato dai profili utente globali. Quando un candidato alla migrazione è nell'elenco dei carichi di lavoro interessati, l'architetto che prepara la migrazione deve consultare gli esperti di dominio di rete e di operazioni per convalidare le aspettative riguardo a routing e prestazioni di rete. Come minimo, l'architettura deve includere una connessione ExpressRoute tra il network operations center più vicino (NOC) e Azure. L'[architettura di riferimento per le connessioni ExpressRoute](/azure/architecture/reference-architectures/hybrid-networking/expressroute) può facilitare la configurazione della connessione necessaria.

**Progettare per la conformità:** Gli output dall'analisi dei profili utente prerequisiti dovrebbero identificare qualsiasi carico di lavoro interessato dai requisiti di sovranità dei dati. Durante le attività di architettura del processo di valutazione, l'architetto assegnato deve consultare gli esperti di dominio per la conformità al fine di comprendere eventuali requisiti per la migrazione o la distribuzione in più aree. Tali requisiti avranno un impatto significativo sulle strategie di progettazione. Possono contribuire alla progettazione le architetture di riferimento per le [applicazioni Web multiarea](/azure/architecture/reference-architectures/app-service-web-app/multi-region) e per le [applicazioni a più livelli multiarea](/azure/architecture/reference-architectures/n-tier/multi-region-sql-server).

> [!WARNING]
> Quando si usa una delle architetture di riferimento precedenti, potrebbe essere necessario escludere elementi dati specifici dai processi di replica per rispettare i requisiti di sovranità dei dati. Viene quindi aggiunto un passaggio aggiuntivo al processo di innalzamento di livello.

## <a name="migrate-process-changes"></a>Modifiche del processo di migrazione

Quando si esegue la migrazione di un'applicazione che deve essere distribuita in più aree, è necessario che il team di adozione del cloud tenga conto di alcune considerazioni. Queste considerazioni consistono nella progettazione dell'insieme di credenziali di Azure Site Recovery, nella progettazione del server di configurazione/elaborazione, nella progettazione della larghezza di banda di rete e nella sincronizzazione dei dati.

### <a name="suggested-action-during-the-migrate-process"></a>Azione suggerita durante il processo di migrazione

**Progettazione dell'insieme di credenziali di Azure Site Recovery:** Azure Site Recovery è lo strumento consigliato per la replica nativa del cloud e per la sincronizzazione di risorse digitali in Azure. Site Recovery replica i dati relativi alla risorsa in un insieme di credenziali di Site Recovery associato a una sottoscrizione specifica in un'area specifica e in un data center di Azure. Quando si replicano le risorse in una seconda area potrebbe essere necessario un secondo insieme di credenziali di Site Recovery.

**Progettazione del server di configurazione/elaborazione:** Site Recovery funziona con un'istanza locale di un server di configurazione ed elaborazione, associato a un singolo insieme di credenziali Site Recovery. Ciò significa che potrebbe essere necessario installare una seconda istanza di questi server nel data center di origine per facilitare la replica.

**Progettazione della larghezza di banda di rete:** Durante la replica e la sincronizzazione in corso, i dati binari vengono spostati in rete dal data center di origine all'insieme di credenziali Site Recovery nel data center di destinazione di Azure. Questo processo usa la larghezza di banda. La duplicazione del carico di lavoro in una seconda area raddoppierà la quantità di larghezza di banda utilizzata. Se la larghezza di banda è limitata o se un carico di lavoro comporta una grande quantità di configurazione o deriva di dati, può interferire con il tempo necessario per completare la migrazione. Ancora più importante, potrebbe influire sull'esperienza degli utenti o delle applicazioni che continuano a dipendere dalla larghezza di banda del data center di origine.

**Sincronizzazione dati:** Spesso lo svuotamento maggiore della larghezza di banda deriva dalla sincronizzazione della piattaforma dati. Come definito nelle architetture di riferimento per [le applicazioni Web multiarea](/azure/architecture/reference-architectures/app-service-web-app/multi-region) e per [le applicazioni a più livelli multiarea](/azure/architecture/reference-architectures/n-tier/multi-region-sql-server), la sincronizzazione dei dati è spesso necessaria per mantenere le applicazioni allineate. Se questo è lo stato operativo dell'applicazione desiderato potrebbe essere opportuno completare una sincronizzazione tra la piattaforma dei dati di origine e ognuna delle piattaforme cloud prima di eseguire la migrazione delle risorse di livello intermedio e dell'applicazione.
**Sincronizzazione dati:** Spesso lo svuotamento maggiore della larghezza di banda deriva dalla sincronizzazione della piattaforma dati. Come definito nelle architetture di riferimento per [le applicazioni Web multiarea](/azure/architecture/reference-architectures/app-service-web-app/multi-region) e per [le applicazioni a più livelli multiarea](/azure/architecture/reference-architectures/n-tier/multi-region-sql-server), la sincronizzazione dei dati è spesso necessaria per mantenere le applicazioni allineate. Se questo è lo stato operativo dell'applicazione desiderato potrebbe essere opportuno completare una sincronizzazione tra la piattaforma dei dati di origine e ognuna delle piattaforme cloud prima di eseguire la migrazione delle risorse di livello intermedio e dell'applicazione.

**Ripristino di emergenza da Azure ad Azure:** È disponibile un'opzione alternativa che può ridurre ulteriormente la complessità. Se le sequenze temporali e la sincronizzazione dei dati si avvicinano a una distribuzione in due passaggi, [il ripristino di emergenza da Azure ad Azure](/azure/site-recovery/azure-to-azure-architecture) potrebbe essere una soluzione accettabile. In questo scenario viene eseguita la migrazione del carico di lavoro al primo data center di Azure usando un unico insieme di credenziali Site Recovery e la configurazione o progettazione del server di elaborazione. Una volta testato, il carico di lavoro può essere recuperato in un secondo data center di Azure dalle risorse sottoposte a migrazione. Questo approccio riduce l'impatto sulle risorse nel data center di origine e sfrutta le velocità di trasferimento maggiori e i limiti di larghezza di banda elevata disponibili tra i data center di Azure.

> [!NOTE]
> Questo approccio può aumentare il costo a breve termine della migrazione, perché può comportare costi aggiuntivi per la larghezza di banda in uscita.

## <a name="optimize-and-promote-process-changes"></a>Ottimizzare e alzare il livello alle modifiche del processo

Affrontare la complessità globale durante l'ottimizzazione e la promozione potrebbe richiedere ulteriori sforzi in ognuna delle aree aggiuntive. Quando una singola distribuzione è accettabile, potrebbe essere ancora necessaria la duplicazione dei piani di test e di modifiche aziendali.

### <a name="suggested-action-during-the-optimize-and-promote-process"></a>Azione suggerita durante il processo di ottimizzazione e promozione

**Ottimizzazione dei pretest:** I test di automazione iniziali possono identificare potenziali opportunità di ottimizzazione, come per qualsiasi operazione di migrazione. Nel caso di carichi di lavoro globali, è importante testare il carico di lavoro in ogni area in modo indipendente, in quanto le modifiche minime alla configurazione della rete o del data center di destinazione di Azure potrebbero influire sulle prestazioni.

**Piani per le modifiche aziendali:** Per qualsiasi scenario di migrazione complesso, si consiglia di creare un piano di modifiche aziendali per garantire una comunicazione chiara riguardo alle modifiche apportate ai processi aziendali, alle esperienze utente e alla tempistica degli sforzi necessari per l'integrazione delle modifiche. Nel caso di attività di migrazione globale, il piano deve includere considerazioni per gli utenti finali in ogni geografia interessata.

**Test aziendali:** In combinazione con il piano di modifica aziendale, il test aziendale potrebbe essere necessario in ogni area per garantire prestazioni adeguate e aderenza ai modelli di routing di rete modificati.

**Versioni di anteprima promozionali:** Spesso la promozione viene eseguita come singola attività, reindirizzando il traffico di produzione ai carichi di lavoro sottoposti a migrazione. Nel caso di attività di rilascio globale, è consigliabile che l'innalzamento di livello sia distribuito in versioni di anteprima (o raccolte predefinite di utenti). Ciò consente al team di strategia cloud e al team di adozione del cloud di osservare meglio le prestazioni e di migliorare il supporto degli utenti in ogni area. Le versioni di anteprima promozionali sono spesso controllate a livello di rete modificando il routing di intervalli IP specifici dalle risorse del carico di lavoro di origine alle risorse appena sottoposte a migrazione. Dopo aver sottoposto a migrazione una raccolta specificata di utenti finali, è possibile reindirizzare il gruppo successivo.

**Ottimizzazione della distribuzione in anteprima:** Uno dei vantaggi offerti dalle versioni di anteprima promozionali è che consente di ottenere osservazioni più approfondite e ottimizzazione aggiuntiva delle risorse distribuite. Dopo un breve periodo di utilizzo della produzione da parte della prima versione di anteprima, viene suggerito un ulteriore perfezionamento delle risorse sottoposte a migrazione, quando consentito dalle procedure operative IT.

## <a name="next-steps"></a>Passaggi successivi

Un punto di complessità separato, spesso correlato a più aree, è la necessità di prepararsi a sottoporre a migrazione [più data center](./multiple-datacenters.md). Nonostante sia di natura simile, questa complessità riguarda il volume delle risorse da sottoporre a migrazione quando si spostano più data center al cloud.

> [!div class="nextstepaction"]
> [Migrazione di più data center](./multiple-datacenters.md)
