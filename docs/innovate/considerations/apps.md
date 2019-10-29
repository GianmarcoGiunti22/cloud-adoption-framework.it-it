---
title: 'Innovazione nel cloud: coinvolgere le applicazioni'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: "Introduzione all'innovazione nel cloud: è possibile coinvolgere le applicazioni."
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: 5f26cf77f918c12c46c653c6fc91ebc972d0db64
ms.sourcegitcommit: 7ffb0427bba71177f92618b2f980e864b72742f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/29/2019
ms.locfileid: "73047548"
---
# <a name="engage-through-applications"></a>Coinvolgi le applicazioni

Come descritto in [democratizzazione dei dati](./data.md), i dati sono il nuovo olio. Alimenta la maggior parte delle innovazioni nell'economia digitale. Basandosi su tale analogia, le applicazioni sono le stazioni di carburante e l'infrastruttura necessarie per ottenere tale carburante nelle mani giuste.

In alcuni casi, i dati da soli sono sufficienti per apportare modifiche e soddisfare le esigenze dei clienti. In genere, tuttavia, le soluzioni per le esigenze dei clienti richiedono che le applicazioni formino i dati e creino un'esperienza. Le applicazioni sono la modalità di coinvolgimento dell'utente. Sono la casa per i processi necessari per rispondere ai trigger dei clienti. Si tratta di mezzi per i clienti per fornire dati e ricevere indicazioni. Questo articolo riepiloga diversi principi che consentono di allinearsi alla soluzione di applicazione corretta, in base alle ipotesi da convalidare.

![Interagisci tramite app](../../_images/innovate/engage-via-apps.png)

## <a name="shared-code"></a>Codice condiviso

I team che rispondono in modo più rapido e accurato ai suggerimenti dei clienti, alle modifiche al mercato e alle opportunità di innovazione in genere portano i rispettivi mercati nell'innovazione. Il primo principio di applicazioni innovative viene riepilogato nella [panoramica sulla tendenza alla crescita](./learn.md#growth-mindset): "condividere il codice". Nel tempo, l'innovazione emerge da uno stato attivo culturale. Per sostenere l'innovazione, sono necessari diversi punti di vista e contributi.

Per essere pronti per l'innovazione, tutto lo sviluppo di applicazioni dovrebbe iniziare con un repository di codice condiviso. Lo strumento più usato per la gestione dei repository di codice è [GitHub](https://guides.github.com/), che consente di creare rapidamente un repository di codice condiviso. In alternativa, [Azure Repos](/azure/devops/repos/get-started/what-is-repos?view=azure-devops) è un set di strumenti di controllo della versione in Azure DevOps Services che è possibile usare per gestire il codice. Azure Repos fornisce due tipi di controllo della versione:

- [Git](/azure/devops/repos/get-started/what-is-repos?view=azure-devops#git): controllo della versione distribuito
- [Controllo della versione di Team Foundation (TFVC)](/azure/devops/repos/get-started/what-is-repos?view=azure-devops#tfvc): controllo della versione centralizzato

## <a name="citizen-developers"></a>Sviluppatori cittadini

Gli sviluppatori professionisti sono un componente fondamentale dell'innovazione. Quando un'ipotesi dimostra un'accuratezza su larga scala, gli sviluppatori professionisti sono tenuti a stabilizzare e preparare la soluzione per la scalabilità. La maggior parte dei principi a cui si fa riferimento in questo articolo richiede il supporto di sviluppatori professionisti. Sfortunatamente, le tendenze correnti suggeriscono una maggiore domanda per gli sviluppatori professionisti rispetto agli sviluppatori. Inoltre, il costo e la velocità dell'innovazione possono essere meno favorevoli quando si ritiene necessario lo sviluppo professionale. In risposta a tali problemi, gli sviluppatori di cittadini forniscono un modo per ridimensionare le attività di sviluppo e accelerare i test di ipotesi iniziali.

L'uso di sviluppatori di cittadini può essere valido ed efficace quando è possibile convalidare le ipotesi preliminari tramite strumenti come [PowerApps](https://docs.microsoft.com/powerapps/powerapps-overview) per le interfacce di app, [ai Builder](https://docs.microsoft.com//powerapps/use-ai-builder) per i processi e le stime, [Microsoft Flow](https://docs.microsoft.com/flow) per i flussi di lavoro e per l' [alimentazione BI](https://docs.microsoft.com/power-bi) per l'utilizzo dei dati.

> [!NOTE]
> Quando si fa affidamento sugli sviluppatori di cittadini per testare le ipotesi, è consigliabile avere a disposizione alcuni sviluppatori professionisti per fornire supporto, revisione e istruzioni. Dopo che un'ipotesi è stata convalidata su larga scala, un processo per la transizione dell'applicazione in un modello di programmazione più affidabile accelererà i ritorni sull'innovazione. Coinvolgendo gli sviluppatori professionisti nelle definizioni dei processi in anticipo, è possibile realizzare transizioni più pulite in un secondo momento.

## <a name="intelligent-experiences"></a>Esperienze intelligenti

Esperienze intelligenti combinano la velocità e la scalabilità delle applicazioni Web moderne con l'intelligence di servizi cognitivi e bot. Da solo, ciascuna di queste tecnologie potrebbe essere sufficiente per soddisfare le esigenze dei clienti. Quando vengono combinate in modo intelligente, ampliano la gamma di esigenze che possono essere soddisfatte tramite un'esperienza digitale, contribuendo al contempo a contenere i costi di sviluppo.

### <a name="modern-web-apps"></a>App Web moderne

Quando un'applicazione o un'esperienza è necessaria per soddisfare le esigenze dei clienti, le applicazioni Web moderne possono essere il modo più rapido per iniziare. Le esperienze Web moderne possono coinvolgere rapidamente i clienti interni o esterni e consentire un'iterazione rapida della soluzione.

### <a name="infusing-intelligence"></a>Infusione dell'Intelligence

Machine Learning e intelligenza artificiale sono sempre più disponibili per gli sviluppatori. La disponibilità ampia di API comuni con funzionalità predittive consente agli sviluppatori di soddisfare al meglio le esigenze del cliente tramite l'accesso espanso ai dati e alle stime.

L'aggiunta di informazioni di intelligence a una soluzione può consentire il riconoscimento vocale, la traduzione di testo, la visione artificiale e persino la ricerca visiva. Con queste funzionalità espanse, è più facile per gli sviluppatori creare soluzioni che sfruttano i vantaggi dell'Intelligence per creare un'esperienza interattiva e moderna.

### <a name="bots"></a>Bot

I bot offrono un'esperienza simile a quella di un computer e più simili alla gestione di una persona, almeno con un robot intelligente. Possono essere usati per spostare attività semplici e ripetitive, ad esempio la prenotazione di una cena o la raccolta di informazioni sul profilo, su sistemi automatizzati che potrebbero non richiedere più l'intervento umano diretto. Gli utenti si conversano con un bot tramite testo, schede interattive e sintesi vocale. Un'interazione bot può variare da una rapida domanda e risposta a una conversazione sofisticata che fornisce in modo intelligente l'accesso ai servizi.

I bot sono molto simili alle applicazioni Web moderne: vivono su Internet e usano le API per inviare e ricevere messaggi. Il contenuto di un bot varia notevolmente a seconda del tipo di bot. Il software per bot moderni si basa su uno stack di tecnologie e strumenti per offrire esperienze sempre più complesse su diverse piattaforme. Un bot semplice può tuttavia semplicemente ricevere un messaggio e inviarlo di nuovo all'utente con la necessità di pochissimo codice.

I bot possono eseguire le stesse operazioni di altri tipi di software: leggere e scrivere file, usare database e API e gestire attività di calcolo regolari. La peculiarità dei bot risiede nell'uso di meccanismi generalmente riservati alla comunicazione tra esseri umani.

## <a name="cloud-native-solutions"></a>Soluzioni native del cloud

Le applicazioni native del cloud vengono create da zero e sono ottimizzate per la scalabilità e le prestazioni del cloud. Le applicazioni native del cloud vengono in genere create usando approcci basati su microservizi, senza server, basati su eventi o basati su contenitori. In genere, le soluzioni native del cloud usano una combinazione di architetture di microservizi, servizi gestiti e recapito continuo per ottenere affidabilità e tempi di immissione sul mercato più rapidi.

Una soluzione nativa del cloud consente ai team di sviluppo centralizzati di mantenere il controllo della logica di business senza la necessità di soluzioni monolitiche e centralizzate. Questo tipo di soluzione crea anche un ancoraggio per garantire la coerenza tra l'input degli sviluppatori cittadini e le esperienze moderne. Infine, le soluzioni native del cloud offrono un acceleratore di innovazione liberando gli sviluppatori di cittadini e professionisti per l'innovazione in modo sicuro e con un minimo di blocchi.

## <a name="innovate-through-existing-solutions"></a>Innovazione attraverso le soluzioni esistenti

Molte ipotesi dei clienti possono essere distribuite in modo ottimale da una versione modernizzata di una soluzione esistente. Quando la logica di business corrente soddisfa le esigenze dei clienti (o si avvicina molto), potrebbe essere possibile accelerare l'innovazione basandosi su una soluzione moderna.

La maggior parte delle forme di modernizzazione, incluso il lieve refactoring dell'applicazione, è inclusa nella [metodologia di migrazione](../../migrate/index.md) all'interno del Framework di adozione del cloud. Questa metodologia guida i team di adozione del cloud attraverso il processo di migrazione di un [patrimonio digitale](../../digital-estate/index.md) al cloud. La [Guida alla migrazione di Azure](../../migrate/azure-migration-guide/index.md) fornisce un approccio semplificato alla stessa metodologia, ideale per un numero ridotto di carichi di lavoro o anche per una singola applicazione.

Dopo la migrazione e la modernizzazione di una soluzione, è possibile usare diversi modi per creare nuove soluzioni innovative per le esigenze dei clienti. Ad esempio, [gli sviluppatori di cittadini](#citizen-developers) possono testare le ipotesi oppure gli sviluppatori professionisti possono creare [esperienze intelligenti](#intelligent-experiences) o [soluzioni native del cloud](#cloud-native-solutions).

### <a name="extend-an-existing-solution"></a>Estendi una soluzione esistente

L'estensione di una soluzione è una forma comune di modernizzazione. Questo approccio può essere il percorso più veloce per l'innovazione quando si verificano le ipotesi seguenti:

- La logica di business esistente deve soddisfare la necessità del cliente esistente (o si avvicina alla riunione).
- Un'esperienza migliorata può soddisfare meglio le esigenze di una coorte di clienti specifica.
- La logica di business richiesta dalla soluzione (MVP) di prodotto minimo è stata centralizzata, in genere tramite una progettazione a più [livelli](/azure/architecture/guide/architecture-styles/n-tier), servizi Web, API o [microservizi](/azure/architecture/guide/architecture-styles/microservices) . Questo approccio è costituito dal wrapping della soluzione esistente in una nuova esperienza ospitata nel cloud. In Azure è probabile che questa soluzione risieda in app Azure Services.

### <a name="rebuild-an-existing-solution"></a>Ricompilare una soluzione esistente

Se un'applicazione non può essere facilmente estesa, potrebbe essere necessario effettuare il refactoring della soluzione. Con questo approccio, viene eseguita la migrazione del carico di lavoro nel cloud. Dopo la migrazione dell'applicazione, parti di esso vengono modificate o duplicate, come servizi Web o [microservizi](/azure/architecture/guide/architecture-styles/microservices), che vengono distribuiti in parallelo alla soluzione esistente. La soluzione basata su servizi paralleli potrebbe essere considerata come una soluzione estesa. Questa soluzione esegue semplicemente il wrapping della soluzione esistente con una nuova esperienza ospitata nel cloud. In Azure è probabile che questa soluzione risieda in app Azure Services.

> [!CAUTION]
> Il refactoring o la riprogettazione di soluzioni o la centralizzazione della logica di business può attivare rapidamente un [picco tecnico](./build.md#reduce-complexity-and-delay-technical-spikes)che richiede molto tempo anziché un'origine del valore del cliente. Si tratta di un rischio per l'innovazione, soprattutto in fase di convalida dell'ipotesi. Con un po' di creatività nella progettazione di una soluzione, dovrebbe esistere un percorso di MVP che non richiede il refactoring delle soluzioni esistenti. È consigliabile ritardare il refactoring fino a quando l'ipotesi iniziale non può essere convalidata su larga scala.

## <a name="operating-model-innovations"></a>Innovazioni del modello operativo

Oltre agli approcci moderni e innovativi per la creazione di app, sono state apportate importanti innovazioni nelle *operazioni*dell'app. Questi approcci hanno generato molti movimenti organizzativi. Uno dei più importanti è il [centro cloud di eccellenza del](../../organize/cloud-center-of-excellence.md) modello operativo. Una volta completati e maturi, i team aziendali hanno la possibilità di fornire il proprio supporto operativo per una soluzione.

Il tipo di modello di gestione operativa self-service disponibile in un cloud Center of Excellence consente controlli più rigorosi e iterazioni più veloci nell'ambiente della soluzione. Questi obiettivi vengono eseguiti trasferendo il controllo operativo e la responsabilità al team aziendale.

Se si intende ridimensionare o soddisfare la domanda globale per una soluzione esistente, è possibile trovare questo approccio sufficiente per convalidare un'ipotesi del cliente. Una volta eseguita la migrazione di una soluzione e leggermente modernizzata, il team aziendale può ridimensionarlo per testare una varietà di ipotesi. Che in genere coinvolgono le coorti dei clienti che riguardano le prestazioni, la distribuzione globale e altre esigenze del cliente ostacolate dalle operazioni IT.

## <a name="reduce-overhead-and-management"></a>Riduzione del sovraccarico e della gestione

Maggiore è la manutenzione in una soluzione, più lenta sarà l'iterazione della soluzione. Ciò significa che è possibile accelerare l'innovazione riducendo l'effetto delle operazioni sulla larghezza di banda disponibile.

Per preparare le numerose iterazioni necessarie per fornire una soluzione innovativa, è importante pensare in anticipo. Ad esempio, ridurre al minimo i costi operativi iniziali del processo privilegiando le opzioni senza server. In Azure le opzioni per le applicazioni senza server possono includere [app Azure servizio](https://docs.microsoft.com/azure/app-service/overview) o [contenitori](https://docs.microsoft.com/azure/architecture/cloud-adoption/migrate/azure-best-practices/contoso-migration-rearchitect-container-sql).

In parallelo, Azure offre opzioni di dati di transazione senza server che riducono anche l'overhead. Nell' [elenco prodotti database](https://docs.microsoft.com/azure/#pivot=products&panel=databases) sono disponibili opzioni per l'hosting dei dati senza la necessità di una piattaforma di dati completa.

## <a name="next-steps"></a>Passaggi successivi

A seconda dell'ipotesi e della soluzione, i principi in questo articolo possono essere utili per la progettazione di app che soddisfano le definizioni MVP e coinvolgono gli utenti. I principi successivi sono i principi per l' [adozione dell'adozione](./ci-cd.md), che offrono modi per rendere l'applicazione e i dati in mano ai clienti in modo più rapido ed efficiente.

> [!div class="nextstepaction"]
> [Adozione potenziata](./ci-cd.md)
