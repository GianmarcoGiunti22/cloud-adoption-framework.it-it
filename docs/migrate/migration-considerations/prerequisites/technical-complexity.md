---
title: 'Superare la complessità tecnica: gestione delle modifiche agile'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Superamento della complessità tecnica: gestione delle modifiche agile'
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 842143afbb042ceddee5029a3fa86d0aa8cdd997
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73564540"
---
# <a name="prepare-for-technical-complexity-agile-change-management"></a>Superare la complessità tecnica: gestione delle modifiche agile

Quando è possibile effettuare il deprovisioning di un intero data center e ricrearlo con una sola riga di codice, i processi tradizionali faticano a rimanere al passo. Le informazioni aggiuntive del Cloud Adoption Framework si basano su procedure come Gestione dei servizi IT (ITSM), Open Group Architecture Framework (TOGAF) e altre. Tuttavia, per garantire agilità e velocità di risposta ai cambiamenti aziendali, questo framework definisce tali procedure per adattare metodologie agili e approcci DevOps.

Quando si passa a un modello agile in cui vengono evidenziate flessibilità e iterazioni, la complessità tecnica e la gestione delle modifiche sono gestite in modo diverso rispetto a un modello a cascata tradizionale, che si concentra su una serie lineare di passaggi di migrazione. Questo articolo illustra un approccio di alto livello alla gestione delle modifiche in un lavoro richiesto di migrazione basato su procedure agili. Alla fine di questo articolo sarà stata acquisita una conoscenza generale dei livelli di gestione delle modifiche e della documentazione che interessano l'approccio di migrazione incrementale. Per selezionare e implementare procedure agili basate su tale conoscenza saranno necessarie altre attività di training e decisioni. Lo scopo di questo articolo è quello di preparare i Cloud Architect a una conversazione facilitata con il project management per illustrare il concetto generale di gestione del cambiamento in questo approccio.

## <a name="address-technical-complexity"></a>Risolvere la complessità tecnica

Quando si modifica un sistema tecnico, la complessità e l'interdipendenza generano rischi nei piani del progetto. Le migrazioni cloud non fanno eccezione. Quando si trasferiscono migliaia o decine di migliaia di risorse nel cloud, questi rischi sono amplificati. Il rilevamento e il mapping di tutte le dipendenze in un digital estate particolarmente ampio possono richiedere anni. Poche aziende possono tollerare un ciclo di analisi così lungo. Per bilanciare la necessità di un'analisi dell'architettura e di accelerazione aziendale, il Cloud Adoption Framework si concentra su un modello INVEST per la gestione del backlog di prodotto. Nelle sezioni seguenti viene riepilogato questo tipo di modello.

## <a name="invest-in-workloads"></a>Il modello INVEST nei carichi di lavoro

Il termine _carico di lavoro_ viene visualizzato spesso nel Cloud Adoption Framework. Un carico di lavoro è un'unità di funzionalità dell'applicazione di cui è possibile eseguire la migrazione nel cloud. Può trattarsi di una singola applicazione, un livello di un'applicazione o una raccolta di un'applicazione. La definizione è flessibile e può variare a seconda delle diverse fasi di migrazione. Per definire un carico di lavoro, il Cloud Adoption Framework usa il termine _INVEST_.

INVEST è un acronimo comune in molte metodologie agili per la scrittura di storie utente o elementi del backlog del prodotto, entrambi unità di output in strumenti di gestione dei progetti agili. L'unità di output misurabile in una migrazione è un carico di lavoro migrato. Il Cloud Adoption Framework modifica leggermente l'acronimo INVEST per creare un costrutto per la definizione dei carichi di lavoro:

- **Indipendente:** Un carico di lavoro non deve avere dipendenze inaccessibili. Per prendere in considerazione la migrazione di un carico di lavoro, è necessario che tutte le dipendenze siano accessibili e incluse nell'operazione di migrazione.
- **Negoziabile:** Quando viene eseguita un'individuazione aggiuntiva, la definizione di un carico di lavoro cambia. Gli architetti che pianificano la migrazione possono negoziare fattori relativi alle dipendenze. Esempi di punti di negoziazione includono la creazione di una versione provvisoria di funzionalità, l'accessibilità di funzionalità tramite una rete ibrida o la creazione di un pacchetto contenente tutte le dipendenze in una singola versione.
- **Prezioso:** Il valore in un carico di lavoro viene misurato in base alla possibilità di fornire agli utenti l'accesso a un carico di lavoro di produzione.
- **Stimabile:** Le dipendenze, gli asset, i tempi di migrazione, le prestazioni e i costi cloud dovrebbero essere tutti stimabili e devono essere stimati prima della migrazione.
- **Piccolo:** L'obiettivo consiste nel creare un pacchetto dei carichi di lavoro in un unico Sprint. Tuttavia, questo potrebbe non essere sempre fattibile. Al contrario, i team sono invitati a pianificare sprint e versioni per ridurre al minimo il tempo necessario per spostare un carico di lavoro nell'ambiente di produzione.
- Verificabile **:** Deve essere sempre definito un metodo di test o convalida del completamento della migrazione di un carico di lavoro.

Questo acronimo non deve essere seguito in modo rigido, ma è volto a semplificare la definizione del termine _carico di lavoro_.

## <a name="migration-backlog-aligning-business-priorities-and-timing"></a>Backlog migrazione: allineamento di priorità e tempistiche aziendali

Il backlog di migrazione consente di tenere traccia del portfolio di primo livello dei carichi di lavoro di cui è possibile eseguire la migrazione. Prima della migrazione, il team di strategia del cloud e il team di adozione del cloud sono invitati a effettuare una verifica del [digital estate](../../../digital-estate/index.md) corrente e a concordare un elenco con priorità dei carichi di lavoro di cui eseguire la migrazione. Questo elenco costituisce la base del backlog di migrazione iniziale.

Inizialmente, è improbabile che i carichi di lavoro nel backlog di migrazione soddisfino i criteri INVEST descritti nella sezione precedente. Vengono invece usati come raggruppamento logico di asset da un inventario iniziale come segnaposto per il lavoro futuro. Questi segnaposto, benché possano non essere tecnicamente accurati, vengono usati come base per il coordinamento con l'azienda.

![Relazione tra i backlog di migrazione, versione e iterazione usati durante il processo di migrazione](../../../_images/migrate/backlog-relationships.png)

*I backlog di migrazione, versione e iterazione tengono traccia dei diversi livelli di attività durante i processi di migrazione.*

In qualsiasi backlog di migrazione, il team di gestione delle modifiche deve tentare di ottenere le informazioni seguenti per qualsiasi carico di lavoro incluso nel piano. Come minimo, questi dati devono essere disponibili per tutti i carichi di lavoro in ordine di priorità per la migrazione nelle due o tre versioni successive.

### <a name="migration-backlog-data-points"></a>Punti dati del backlog di migrazione

- **Impatto aziendale.** Comprendere l'effetto sull'azienda della mancanza della sequenza temporale prevista o della riduzione della funzionalità in caso di blocco di Windows.
- **Priorità aziendale relativa.** Elenco di carichi di lavoro classificati in base alle priorità aziendali.
- **Titolare dell'azienda.** Unico responsabile delle decisioni aziendali relative a questo carico di lavoro.
- **Proprietario tecnico.** Unico responsabile delle decisioni tecniche relative a questo carico di lavoro.
- **Sequenze temporali previste.** Quando la migrazione è pianificata per il completamento.
- **Il carico di lavoro si blocca.** Frame temporali in cui il carico di lavoro non deve essere idoneo per la modifica.
- **Nome del carico di lavoro.**
- **Inventario iniziale.** Tutte le risorse necessarie per garantire la funzionalità del carico di lavoro, tra cui macchine virtuali, appliance IT, dati, applicazioni, pipeline di distribuzione e altro ancora. Queste informazioni potrebbero non essere accurate.

## <a name="release-backlog-aligning-business-change-and-technical-coordination"></a>Backlog versione: allineamento delle modifiche aziendali e coordinamento tecnico

Nel contesto di una migrazione, una _versione_ indica un'attività che distribuisce uno o più carichi di lavoro nell'ambiente di produzione. Una versione in genere copre diverse iterazioni o lavori tecnici. Tuttavia, rappresenta una singola iterazione della modifica aziendale. Quando uno o più carichi di lavoro sono preparati per la promozione in produzione, si ha una versione. La decisione di creare un pacchetto di una versione viene presa quando i carichi di lavoro migrati rappresentano un valore aziendale sufficiente a giustificare l'inserimento delle modifiche in un ambiente aziendale. Le versioni vengono eseguite assieme a un [piano di modifica aziendale](../optimize/business-change-plan.md), dopo il completamento di [test aziendali](../optimize/business-test.md). Il team di strategia del cloud è responsabile della pianificazione e della supervisione dell'esecuzione di una versione per garantire che la modifica aziendale desiderata venga rilasciata.

Un *backlog versione* è il piano di stato futuro che definisce una versione imminente. Il backlog versione è il punto pivot tra la gestione delle modifiche aziendali (*backlog di migrazione*)e la gestione delle modifiche tecniche (*backlog sprint*). Un backlog versione è costituito da un elenco di carichi di lavoro del backlog di migrazione allineati a un subset specifico di realizzazione dei risultati aziendali. La definizione e l'invio di un backlog versione al team di adozione del cloud servono come trigger per un'analisi e una pianificazione della migrazione più approfondite. Dopo che il team di adozione del cloud ha verificato i dettagli tecnici associati a una versione, può scegliere di eseguire il commit nella versione, definendo una sequenza temporale di rilascio basata sulla conoscenza corrente.

Dato il livello di analisi necessario per convalidare una versione, il team di strategia del cloud deve stilare un elenco di esecuzione delle prossime due-quattro versioni. Prima di definire e inviare una versione, il team deve provare anche a convalidare la maggior parte delle informazioni riportate di seguito. Un team di strategia del cloud disciplinato e in grado di gestire le quattro versioni successive può aumentare in modo significativo la coerenza e l'accuratezza delle stime relative alla sequenza temporale della versione.

### <a name="release-backlog-data-points"></a>Punti dati del backlog versione

La collaborazione tra il team di strategia del cloud e il team di adozione del cloud consente di aggiungere i punti dati seguenti per tutti i carichi di lavoro nel backlog versione:

- **Inventario ottimizzato.** Convalida degli asset necessari di cui eseguire la migrazione. La convalida viene spesso eseguita tramite dati di log o di monitoraggio a livello di host, rete o sistema operativo per assicurare una conoscenza accurata delle dipendenze di rete e hardware di ogni asset con carico standard.
- **Modelli d'uso.** Informazioni sui modelli d'uso degli utenti finali. Questi modelli includono spesso un'analisi della distribuzione geografica dell'utente finale, delle route di rete, dei picchi d'uso stagionali, dei picchi d'uso giornalieri/orari e della composizione dell'utente finale (interna ed esterna a confronto).
- **Aspettative delle prestazioni.** Analisi dei dati di log disponibili per l'acquisizione di velocità effettiva, visualizzazioni di pagina, route di rete e altri dati sulle prestazioni necessari per replicare l'esperienza dell'utente finale.
- **Dipendenze.** Analisi del traffico di rete e dei modelli d'uso delle applicazioni per identificare eventuali dipendenze aggiuntive del carico di lavoro, di cui tenere conto per la sequenziazione e la conformità ambientale. Nessun carico di lavoro può essere incluso in una versione fino a quando non è possibile soddisfare uno dei criteri seguenti:
  - La migrazione di tutti i carichi di lavoro dipendenti è stata eseguita.
  - Le configurazioni di rete e di sicurezza sono state implementate per consentire al carico di lavoro di accedere a tutte le dipendenze, in linea con le aspettative in termini di prestazioni.
- **Approccio alla migrazione desiderato.** A livello di backlog di migrazione, l'attività di migrazione presunta è l'unica considerazione usata nell'analisi. Se, ad esempio, il risultato aziendale è l'uscita da un data center esistente, si presuppone che tutte le migrazioni rappresentino uno scenario di rehosting nel backlog di migrazione. Nel backlog versione il team di strategia del cloud e il team di adozione del cloud devono valutare il valore a lungo termine di funzionalità aggiuntive, modernizzazione e investimenti di sviluppo costanti per determinare se sia necessario un approccio più moderno.
- **Criteri di test aziendali.** Dopo che un carico di lavoro è stato aggiunto al backlog di migrazione, è necessario concordare i criteri di test. In alcuni casi, i criteri di test possono essere limitati a un test delle prestazioni con un gruppo di utenti esperti definito. Per la convalida statistica, tuttavia, è necessario includere un test automatizzato delle prestazioni. L'istanza dell'applicazione esistente spesso non dispone di funzionalità di test automatizzate. In tal caso, non è insolito che i Cloud Architect collaborino con utenti esperti per creare un test di carico di base sulla soluzione esistente e stabilire un benchmark da usare durante la migrazione.

### <a name="release-backlog-cadence"></a>Frequenza del backlog versione

Nelle migrazioni avanzate, le versioni vengono rilasciate con cadenza regolare. La velocità del team di adozione del cloud è spesso normalizzata, pertanto viene prodotta una versione ogni due-quattro iterazioni (approssimativamente ogni mese o ogni due mesi). Tuttavia, deve trattarsi di un risultato organico. La creazione di cadenze di rilascio artificiali può influire negativamente sulla capacità del team di adozione del cloud di ottenere una velocità effettiva coerente.

Per stabilizzare l'impatto aziendale, il team di strategia del cloud deve stabilire un processo di rilascio mensile con l'azienda per mantenere un dialogo regolare, ma deve anche chiarire che passeranno diversi mesi prima che possa essere prevista una cadenza di rilascio regolare.

## <a name="sprint-or-iteration-backlog-aligning-technical-change-and-effort"></a>Backlog di iterazione o Sprint: allineamento di modifiche tecniche e impegno

Uno *sprint*, o *iterazione*, è un'unità di lavoro coerente con vincoli di tempo. Nel processo di migrazione, viene spesso misurata in incrementi di due settimane. Tuttavia, non si è mai sentito di avere iterazioni di una settimana o di quattro settimane. La creazione di iterazioni con vincoli di tempo impone intervalli coerenti di completamento del lavoro richiesto e consente una maggiore regolarizzazione dei piani, in base alle nuove informazioni. Durante uno sprint specifico, in genere sono presenti attività per la valutazione, la migrazione e l'ottimizzazione dei carichi di lavoro definiti nel backlog di migrazione. Queste unità di lavoro devono essere rilevate e gestite nello stesso strumento di gestione dei progetti del backlog di migrazione e versione, per garantire coerenza tra ogni livello di gestione del cambiamento.

Un *backlog sprint*, o *backlog di iterazione*, è costituito dal lavoro tecnico da completare in un singolo sprint o in una singola iterazione, che riguarda la migrazione di singoli asset. Tale operazione deve essere derivata dall'elenco dei carichi di lavoro di cui viene eseguita la migrazione. Quando si usano strumenti come Azure DevOps (in precedenza Visual Studio Online) per la gestione dei progetti, gli elementi di lavoro presenti in uno sprint sono figli degli elementi del backlog di prodotto in un backlog versione e delle epiche in un backlog di migrazione. Questa relazione padre-figlio consente di chiarire tutti i livelli di gestione del cambiamento.

All'interno di un singolo sprint o di una singola iterazione, il team di adozione del cloud si impegna a fornire la quantità di lavoro tecnico prevista, in vista della migrazione di un carico di lavoro definito. Questo è il risultato finale della strategia di gestione del cambiamento. Al termine, questo lavoro richiesto può essere testato convalidando l'idoneità alla produzione di un carico di lavoro di gestione preparato per il commit nel cloud.

### <a name="large-or-complex-sprint-structures"></a>Strutture sprint grandi o complesse

Per una migrazione di piccole dimensioni con un team di migrazione autonomo, un singolo sprint può includere tutte e quattro le fasi della migrazione per un singolo carico di lavoro (*valutazione*, *migrazione*, *ottimizzazione*, *protezione e gestione*). Più comunemente, ognuno di questi processi è condiviso da più team in elementi di lavoro distinti in diversi sprint. A seconda del tipo di lavoro richiesto, della scalabilità del lavoro richiesto e dei ruoli, questi sprint possono assumere forme diverse.

- **Factory di migrazione.** Le migrazioni su larga scala richiedono talvolta un approccio simile a una factory nel modello di esecuzione. In questo modello, diversi team vengono allocati all'esecuzione di un processo di migrazione specifico (o subset del processo). Al termine, l'output dello sprint di un team popola il backlog per il team successivo. Si tratta di un approccio efficace per migrazioni di rehosting su larga scala di molti carichi di lavoro potenziali, in cui sono coinvolte migliaia di macchine virtuali che passano attraverso fasi di valutazione, architettura, monitoraggio, correzione e migrazione. Tuttavia, per il corretto funzionamento di questo approccio è necessario un nuovo ambiente omogeneo con processi di approvazione e gestione delle modifiche ottimizzati.
- **Cicli di migrazione.** Un altro approccio efficace per migrazioni di grandi dimensioni consiste in un modello ciclico. In questo modello, la suddivisione del lavoro non è altrettanto chiara. I team si dedicano all'esecuzione del processo di migrazione di singoli carichi di lavoro. Tuttavia, la natura di ogni sprint cambia. In uno sprint, il team può completare il lavoro di valutazione e architettura. In un altro sprint, può completare il lavoro di migrazione. In un altro sprint ancora, l'attenzione si concentra sull'ottimizzazione e la versione di produzione. Questo approccio consente a un team di base di restare allineato ai carichi di lavoro, acquistandone una panoramica completa nel processo. Quando si usa questo approccio, la diversità di competenze e il cambio di contesto possono ridurre la velocità potenziale del team, rallentando il lavoro di migrazione richiesto. Alcuni ostacoli durante i cicli di approvazione possono anche causare ritardi significativi. Con questo modello, è importante mantenere più opzioni nel backlog di versione per far progredire il team durante i periodi di blocco. È anche importante eseguire il training dei membri del team e garantire che i set di competenze si allineano al tema di ogni sprint.

### <a name="sprint-backlog-data-points"></a>Punti dati del backlog sprint

Il risultato di uno sprint acquisisce e documenta le modifiche apportate a un carico di lavoro, chiudendo in questo modo il ciclo di gestione del cambiamento. Al termine, è necessario documentare almeno quanto segue. Durante l'esecuzione di uno sprint, questa documentazione dovrà essere completata in tandem con gli elementi di lavoro tecnici.

- **Asset distribuiti.** Tutti gli asset distribuiti nel cloud per l'hosting del carico di lavoro.
- **Correzione.** Eventuali modifiche agli asset da preparare per la migrazione nel cloud.
- **Configurazione.** Configurazione scelta per gli asset distribuiti, inclusi eventuali riferimenti agli script di configurazione.
- **Modello di distribuzione.** Approccio usato per distribuire l'asset nel cloud, inclusi eventuali riferimenti a script o strumenti di distribuzione.
- **Architettura.** Documentazione dell'architettura distribuita nel cloud.
- **Metriche delle prestazioni.** Risultati di test automatizzati o test aziendali eseguiti per convalidare le prestazioni al momento della distribuzione.
- **Requisiti o configurazione univoci.** Qualsiasi aspetto univoco della distribuzione, della configurazione o dei requisiti tecnici necessario per il funzionamento del carico di lavoro.
- **Approvazione operativa.** Approvazione della convalida della conformità operativa da parte del proprietario dell'applicazione e del personale IT responsabile della gestione della post-distribuzione del carico di lavoro.
- **Approvazione dell'architettura.** Approvazione del proprietario del carico di lavoro e del team di adozione del cloud per convalidare tutte le modifiche relative all'architettura necessarie per ospitare ogni asset.

## <a name="next-steps"></a>Passaggi successivi

Una volta stabiliti gli approcci alla gestione del cambiamento, è tempo di affrontare il prerequisito finale, la [revisione del backlog di migrazione](./migration-backlog-review.md)

> [!div class="nextstepaction"]
> [Revisione del backlog di migrazione](./migration-backlog-review.md)
