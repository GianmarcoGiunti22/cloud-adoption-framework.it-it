---
title: Decisioni che influiscono sulle migrazioni
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Decisioni importanti da prendere in merito al processo di migrazione
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 01380bdd795fac0fc2740e4e41c3638a8b8d93f3
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548301"
---
# <a name="decisions-that-affect-migrations"></a>Decisioni che influiscono sulle migrazioni

Durante la migrazione, sono numerosi i fattori che influiscono sulle decisioni e sulle attività di esecuzione. Questo articolo illustra il tema centrale di tali decisioni ed esamina alcune domande che illustrano i principi della migrazione in questa sezione delle linee guida sul Cloud Adoption Framework.

## <a name="business-outcomes"></a>Risultati aziendali

Il fine o l'obiettivo di qualsiasi lavoro richiesto per l'adozione può avere un impatto significativo sull'approccio consigliato all'esecuzione.

- **Migrazione.** Driver aziendali pressanti, velocità di adozione o risparmio sui costi sono esempi di risultati operativi. Questi risultati sono fondamentali per i lavori richiesti che traggono valore aziendale dalla modifica transitiva in modelli operativi o IT. La sezione relativa alla migrazione del Cloud Adoption Framework è dedicata principalmente ai risultati aziendali mirati alla migrazione.
- **Innovazione delle applicazioni.** Il miglioramento dell'esperienza dei clienti e la crescente quota di mercato sono esempi di risultati incrementali. I risultati derivano da una raccolta di modifiche incrementali mirate alle esigenze e ai desideri dei clienti attuali.
- **Innovazione incentrata sui dati.** I nuovi prodotti o servizi, in particolare quelli che nascono dalla potenza dei dati, sono esempi di risultati dirompenti. Questi risultati derivano da sperimentazioni e stime che usano i dati per interferire con lo status quo sul mercato.

Nessuna azienda può perseguire uno solo di questi risultati. Senza operazioni non ci sono clienti e viceversa. L'adozione del cloud non fa eccezione. Le aziende in genere lavorano per realizzare ognuno di questi risultati, ma il tentativo di concentrarsi su tutti simultaneamente può suddividere il lavoro richiesto in modo troppo frammentario e rallentare le attività più vantaggiose per le esigenze aziendali.

Questo prerequisito non presuppone la necessità di scegliere uno di questi tre obiettivi, quanto piuttosto di aiutare il team di strategia cloud e il team di adozione del cloud a definire un set di priorità operative che guideranno l'esecuzione nei successivi tre-sei mesi. Queste priorità vengono impostate in base alla classificazione di ognuna delle tre opzioni dettagliate, dalla *più significativa* alla *meno significativa*, in quanto sono correlate al lavoro richiesto a cui questo team può contribuire nel trimestre o nei due trimestri successivi.

### <a name="acting-on-migration-outcomes"></a>Agire sui risultati della migrazione

Se i risultati operativi occupano il primo posto nell’elenco, questa sezione del Cloud Adoption Framework funzionerà in modo ottimale per il team. In questa sezione si presuppone che sia necessario assegnare una priorità alla velocità e ai risparmi sui costi come indicatori di prestazioni chiave (KPI) principali, nel qual caso un modello di migrazione da adottare sarebbe ben allineato con i risultati. Un modello incentrato sulla migrazione si fonda principalmente su una migrazione "lift-and-shift" di asset IaaS (Infrastruttura distribuita come servizio) per esaurire un data center e produrre risparmi sui costi. In questo modello la modernizzazione, benché possa verificarsi, rappresenta un interesse secondario, fino a quando non viene realizzata la missione principale di migrazione.

### <a name="acting-on-application-innovations"></a>Agire sulle innovazioni delle applicazioni

Se i driver principali sono la quota di mercato e l'esperienza del cliente, questa potrebbe non essere la sezione migliore del Cloud Adoption Framework per favorire il lavoro richiesto ai team. L'innovazione delle applicazioni richiede un piano incentrato sulla modernizzazione e la transizione dei carichi di lavoro, indipendentemente dall'infrastruttura sottostante. In tal caso, il materiale sussidiario contenuto in questa sezione, anche se può essere utile a livello informativo, potrebbe non rappresentare l'approccio migliore per prendere decisioni chiave.

### <a name="acting-on-data-innovations"></a>Agire sull'innovazione dei dati

Se la priorità dei prossimi sei mesi sono i dati, la sperimentazione, la ricerca e lo sviluppo (R&D) o i nuovi prodotti, questa potrebbe non essere la sezione migliore del Cloud Adoption Framework per favorire il lavoro richiesto ai team. Qualsiasi lavoro richiesto di innovazione dei dati può trarre vantaggio dalle linee guida relative alla migrazione dei dati di origine esistenti. Tuttavia, l'obiettivo più ampio di tale lavoro richiesto sono l'immissione e l'integrazione di origini dati aggiuntive. L'ampliamento di tali linee guida con stime e nuove esperienze è molto più importante della migrazione di asset IaaS.

## <a name="balancing-the-portfolio"></a>Bilanciamento del portfolio

Questa sezione del Cloud Adoption Framework definisce gli aspetti teorici per aiutare i lettori a comprendere i diversi approcci all'indirizzamento delle modifiche in un portfolio bilanciato. L'articolo relativo al [bilanciamento del portfolio](../../expanded-scope/balance-the-portfolio.md) offre un esempio di ambito espanso, progettato per agire in base a questa teoria.

## <a name="effort"></a>Lavoro richiesto

Il lavoro di migrazione richiesto può variare notevolmente a seconda delle dimensioni e delle complessità dei carichi di lavoro. La migrazione di carichi di lavoro più piccoli che coinvolge alcune centinaia di macchine virtuali è un processo tattico, potenzialmente implementato con strumenti automatici come [Azure Migrate](https://docs.microsoft.com/azure/migrate/migrate-overview). Viceversa, una grande migrazione aziendale di decine di migliaia di carichi di lavoro richiede un processo altamente strategico e può comportare un refactoring esteso, così come la ricompilazione e la sostituzione di applicazioni esistenti attraverso l'integrazione di una piattaforma PaaS e software SaaS. [L'identificazione e il bilanciamento dell'ambito](../../expanded-scope/balance-the-portfolio.md) delle migrazioni pianificate sono essenziali.

Prima di prendere decisioni che potrebbero avere un impatto a lungo termine sul programma di migrazione corrente, è fondamentale raggiungere un consenso sulle decisioni seguenti.

### <a name="effort-type"></a>Tipo di lavoro richiesto

In qualsiasi migrazione di una scala significativa (> macchine virtuali da 250), viene eseguita la migrazione degli asset usando un'ampia gamma di opzioni di transizione, illustrate nella pagina relativa alla razionalizzazione, ovvero la *rehost*, il *refactoring* *, la riprogettazione, la* *ricompilazione*e la *sostituzione*.

Alcuni carichi di lavoro vengono modernizzati tramite un processo di *ricompilazione* o *riprogettazione*, creando applicazioni più moderne con nuove funzioni e funzionalità tecniche. Altri asset vengono sottoposti a un processo di *refactoring*, ad esempio un passaggio a contenitori o altri approcci operativi e di hosting più moderni che non influiscono necessariamente sulla codebase delle soluzioni. In genere, le macchine virtuali e altri asset definiti in modo più adeguato vengono sottoposti a un processo di *rehosting*, passando le risorse dal data center al cloud. Alcuni carichi di lavoro possono essere potenzialmente migrati nel cloud, ma devono essere *sostituiti* con servizi cloud basati su servizi (basati su SaaS) che soddisfino le stesse esigenze aziendali, ad esempio usando Office 365 come alternativa alla migrazione di istanze di Exchange Server.

Nella maggior parte degli scenari, un evento di business crea una funzione di forzatura che consente di migrare temporaneamente una percentuale elevata di risorse tramite un processo di *rehosting*, seguito da una transizione secondaria più significativa tramite una delle altre strategie di migrazione non appena si trovano nel cloud. Questo processo è comunemente noto come *transizione al cloud*.

Durante il processo di [razionalizzazione delle proprietà digitali](../../../digital-estate/calculate.md), questi tipi di decisioni vengono applicati a ogni asset da migrare. Tuttavia, il prerequisito necessario in questo momento consiste nel creare un presupposto di base. Delle cinque strategie di migrazione, quale si allinea meglio agli obiettivi o ai risultati aziendali per questa operazione di migrazione? Questa decisione funge da presupposto di guida per l'intero lavoro di migrazione.

### <a name="effort-scale"></a>Portata del lavoro richiesto

La portata della migrazione rappresenta la successiva decisione importante tra i prerequisiti. I processi necessari per eseguire la migrazione di 1.000 asset sono diversi dal processo necessario per migrarne 10.000. Prima di iniziare qualsiasi lavoro di migrazione richiesto, è importante rispondere alle domande seguenti:

- **Quanti asset supportano attualmente i carichi di lavoro di migrazione?** Gli asset includono strutture dei dati, applicazioni, macchine virtuali e appliance IT necessarie. Come primo candidato per la migrazione è consigliabile scegliere un carico di lavoro relativamente piccolo.
- **Di tali asset, quanti sono pianificati per la migrazione?** È normale che una percentuale di asset venga terminata durante un processo di migrazione, a causa del mancato mantenimento di una dipendenza da parte dell'utente finale.
- **Quali sono le stime dall'alto verso il basso riguardo alla portata degli asset di cui è possibile eseguire la migrazione?** Per i carichi di lavoro inclusi nella migrazione, stimare il numero di asset di supporto, ad esempio applicazioni, macchine virtuali, origini dati e appliance IT. Per informazioni aggiuntive sull'identificazione delle risorse rilevanti, vedere la sezione relativa alle [proprietà digitali](../../../digital-estate/index.md) del Cloud Adoption Framework.

### <a name="effort-timing"></a>Tempistiche del lavoro richiesto

Spesso, le migrazioni si basano su un evento aziendale interessante, soggetto a variazioni nel tempo. Ad esempio, un driver comune è rappresentato dalla risoluzione o dal rinnovo di un contratto di hosting di terze parti. Sebbene siano molti i potenziali eventi aziendali che necessitano di una migrazione, questi hanno un solo elemento in comune: una data di fine. È importante comprendere la tempistica degli eventi di business che si avvicinano, in modo da pianificare e convalidare correttamente le attività e la velocità.

## <a name="recap"></a>Riepilogo

Prima di procedere, documentare i presupposti seguenti e condividerli con i team di strategia cloud e di adozione del cloud:

- Risultati aziendali.
- Ruoli. Questa operazione verrà documentata e perfezionata per i processi di migrazione relativi a *valutazione*, *migrazione*, *ottimizzazione*, *protezione e gestione*.
- Definizione di completato. Questa operazione verrà documentata e perfezionata separatamente per i processi di migrazione relativi a *valutazione*, *migrazione*, *ottimizzazione*, *protezione e gestione*.
- Tipo di lavoro richiesto.
- Portata del lavoro richiesto.
- Tempistiche del lavoro richiesto.

## <a name="next-steps"></a>Passaggi successivi

Una volta compreso il processo tra il team, è possibile esaminare i prerequisiti tecnici. L'[elenco di controllo per la pianificazione dell'ambiente di migrazione](./planning-checklist.md) consente di assicurarsi che la base tecnica sia pronta per la migrazione.

Una volta che il processo è stato compreso tra il team, il suo tempo per esaminare i prerequisiti tecnici di [elenco di controllo per la pianificazione della migrazione] contribuirà a garantire che la base tecnica sia pronta per la migrazione.

> [!div class="nextstepaction"]
> [Rivedere l'elenco di controllo per la pianificazione della migrazione](./planning-checklist.md)
