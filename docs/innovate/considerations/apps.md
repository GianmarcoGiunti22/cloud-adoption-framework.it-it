---
title: 'Innovazione nel cloud: coinvolgere le applicazioni'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Introduzione all'innovazione nel cloud-coinvolgere le applicazioni
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/24/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: 5dcfbc34c31346b4efada049fc46effac149cd68
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72557258"
---
# <a name="engage-through-applications"></a>Coinvolgi le applicazioni

Come illustrato nell'articolo sulla [democratizzazione dei dati](./data.md), i dati sono il nuovo petrolio. Alimenta la maggior parte delle innovazioni nell'economia digitale. Basandosi su tale analogia, le applicazioni sono la stazione di carburante e l'infrastruttura necessarie per ottenere tale carburante nelle mani giuste.

In alcuni casi, i dati sono sufficienti per apportare modifiche e soddisfare le esigenze dei clienti. Più comunemente, la soluzione per le esigenze dei clienti richiede che le applicazioni formino i dati e creino un'esperienza. Le applicazioni sono la modalità di coinvolgimento dell'utente. Sono la casa per i processi necessari per rispondere ai trigger dei clienti. Si tratta dei clienti che consentono di fornire dati e ricevere indicazioni. In questo articolo verranno illustrati alcuni principi che aiuteranno ad allineare la soluzione dell'applicazione corretta, in base alle ipotesi da convalidare.

## <a name="shared-code"></a>Codice condiviso

I team che possono rispondere in modo più rapido e accurato ai suggerimenti dei clienti, alle modifiche al mercato e alle opportunità di innovazione, determineranno i rispettivi mercati nell'innovazione. Il primo principio di applicazioni innovative è descritto nella [panoramica sulla tendenza alla crescita](./learn.md#growth-mindset), "condividere il codice". L'innovazione nel tempo può provenire solo da uno stato attivo culturale. Per sostenere l'innovazione, saranno necessari diversi punti di vista e contributi.

Per essere pronti per l'innovazione, tutto lo sviluppo di applicazioni dovrebbe iniziare con un repository di codice condiviso. Lo strumento più comune per la gestione dei repository di codice è [GitHub](https://guides.github.com/), che consente la creazione di un repository di codice condiviso con pochi clic. In alternativa, è possibile usare la funzionalità [Azure Repos](/azure/devops/repos/get-started/what-is-repos?view=azure-devops) di Azure DevOps per creare un repository [git](/azure/devops/repos/get-started/what-is-repos?view=azure-devops#git) o [Team Foundation](/azure/devops/repos/get-started/what-is-repos?view=azure-devops#tfvc) .

## <a name="citizen-developers"></a>Sviluppatori cittadini

Gli sviluppatori professionisti sono un componente fondamentale dell'innovazione. Quando un'ipotesi dimostra un'accuratezza su larga scala, gli sviluppatori professionisti sono tenuti a stabilizzare e preparare la soluzione per la scalabilità. La maggior parte dei principi a cui si fa riferimento in questo articolo richiederà il supporto per gli sviluppatori professionisti. Sfortunatamente, le tendenze correnti suggeriscono che ci sono più aperture per gli sviluppatori professionisti, quindi ci sono sviluppatori. Il costo e la velocità dell'innovazione, inoltre, possono essere meno favorevoli quando sono necessari i rigore dello sviluppo professionale. Gli sviluppatori cittadini forniscono un modo per ridimensionare le attività di sviluppo e accelerare i test di ipotesi preliminari.

Gli sviluppatori di cittadini possono avere un approccio oculato quando è possibile convalidare le ipotesi preliminari usando strumenti come [PowerApps](https://docs.microsoft.com/powerapps/powerapps-overview) per le interfacce app, [ai Builder](/powerapps/use-ai-builder) per i processi e le stime, [Microsoft Flow](https://docs.microsoft.com/flow) per i flussi di lavoro o [Power bi](https://docs.microsoft.com/power-bi) per i dati consumo.

> [!NOTE]
> Quando si sfruttano gli sviluppatori di cittadini per testare le ipotesi, è consigliabile che gli sviluppatori professionisti forniscano supporto, revisione e istruzioni. Una volta convalidata un'ipotesi su larga scala, un processo di transizione dell'applicazione in un modello di programmazione più affidabile accelererà le restituzioni sull'innovazione. Il coinvolgimento degli sviluppatori professionisti nelle definizioni iniziali dei processi può comportare una transizione più pulita in un secondo momento.

## <a name="modern-web-experiences"></a>Esperienza web moderna

Quando un'applicazione o un'esperienza è necessaria per soddisfare le esigenze dei clienti, le applicazioni Web moderne possono essere il modo più rapido per soddisfare questa esigenza. Le esperienze Web moderne possono coinvolgere rapidamente i clienti interni o esterni e consentire un'iterazione rapida della soluzione.

App Azure servizio fornisce un ambiente di hosting per le applicazioni che elimina il carico di gestione dell'infrastruttura e l'applicazione di patch del sistema operativo. Consente di automatizzare la scalabilità per soddisfare le esigenze degli utenti, ma in base ai limiti definiti per la verifica dei costi. Il servizio app offre un supporto di prima classe per linguaggi come ASP.NET, ASP.NET Core, Java, Ruby, node. js, PHP o Python. Se è necessario ospitare un altro stack di runtime, app Web per il contenitore consente di ospitare in modo rapido e semplice un contenitore Docker all'interno dell'ambiente del servizio app per consentire all'utente di ospitare lo stack di codice personalizzato in un ambiente che consente di uscire dal server occupato ESS.

## <a name="cloud-native-solutions"></a>Soluzioni native del cloud

Le applicazioni cloud native vengono create da zero. Le applicazioni cloud native sono ottimizzate per le prestazioni e la scalabilità del cloud. Le applicazioni native del cloud vengono in genere create usando approcci basati su microservizi, senza server, basati su eventi o basati su contenitori. In genere, le soluzioni native del Cloud sfruttano una combinazione di architetture di microservizi, servizi gestiti e recapito continuo per ottenere affidabilità e tempi di immissione sul mercato più rapidi.

Una soluzione nativa del cloud consente ai team di sviluppo centralizzati di mantenere il controllo della logica di business, senza la necessità di soluzioni centralizzate monolitiche. Questo tipo di soluzione crea anche un ancoraggio per garantire la coerenza tra gli sviluppatori di cittadini e le esperienze moderne. Infine, le soluzioni native del cloud offrono un acceleratore di innovazione liberando gli sviluppatori di cittadini e professionisti per l'innovazione in modo sicuro e con blocchi minimi.

## <a name="innovate-through-existing-solutions"></a>Innovazione attraverso le soluzioni esistenti

Molte ipotesi dei clienti possono essere distribuite in modo ottimale da una versione modernizzata di una soluzione esistente. Quando la logica di business corrente soddisfa le esigenze del cliente (o si avvicina molto), è possibile accelerare l'innovazione basandosi su una soluzione modernizzata.

La maggior parte delle forme di modernizzazione, incluso il lieve refactoring dell'applicazione, è inclusa nella [metodologia di migrazione](../../migrate/index.md) all'interno del Framework di adozione del cloud. Questa metodologia guida i team di adozione del cloud attraverso i processi per la migrazione di un [patrimonio digitale](../../digital-estate/index.md) al cloud. La [Guida alla migrazione di Azure](../../migrate/azure-migration-guide/index.md) fornisce un approccio semplificato alla stessa metodologia, ideale per un numero ridotto di carichi di lavoro o anche per una singola applicazione.

Una volta eseguita la migrazione e la modernizzazione, esistono diversi modi per sfruttare la soluzione nella creazione di nuove soluzioni innovative per le esigenze dei clienti. Ad esempio, [gli sviluppatori di cittadini](#citizen-developers) possono testare le ipotesi o gli sviluppatori professionisti possono creare [esperienze Web moderne](#modern-web-experiences) o [soluzioni native del cloud](#cloud-native-solutions).

### <a name="extend-an-existing-solution"></a>Estendi una soluzione esistente

L'estensione di una soluzione è una forma comune di modernizzazione. Questo approccio può essere il percorso più veloce per l'innovazione quando si verificano le ipotesi seguenti:

- La logica di business esistente deve soddisfare la necessità del cliente esistente (o si avvicina alla riunione).
- Un'esperienza migliorata può soddisfare meglio le esigenze di una coorte di clienti specifica.
- La logica di business richiesta dalla soluzione MVP è stata centralizzata, in genere tramite una progettazione a più [livelli](/azure/architecture/guide/architecture-styles/n-tier), servizi Web, API o [microservizi](/azure/architecture/guide/architecture-styles/microservices) . Questo approccio è costituito dal wrapping della soluzione esistente con una nuova esperienza ospitata nel cloud. In Azure è probabile che questa soluzione risieda in app Azure Services.

### <a name="rebuild-an-existing-solution"></a>Ricompilare una soluzione esistente

Se un'applicazione non può essere facilmente estesa, potrebbe essere necessario effettuare il refactoring della soluzione. Con questo approccio, viene eseguita la migrazione del carico di lavoro nel cloud. Una volta eseguita la migrazione, le parti dell'applicazione vengono modificate o duplicate, come servizi Web o [microservizi](/azure/architecture/guide/architecture-styles/microservices), che vengono distribuite in parallelo alla soluzione esistente. La soluzione basata su servizi paralleli potrebbe essere considerata come una soluzione estesa. Questa soluzione esegue semplicemente il wrapping della soluzione esistente con una nuova esperienza ospitata nel cloud. In Azure è probabile che questa soluzione risieda in app Azure Services.

> [!CAUTION]
> Il refactoring e la riprogettazione di soluzioni o la centralizzazione della logica di business possono diventare rapidamente un [picco tecnico](./build.md#reduce-complexity-and-delay-technical-spikes)dispendioso in termini di tempo, in contrapposizione a un'origine del valore del cliente. Si tratta di un rischio per l'innovazione, soprattutto in fase di convalida dell'ipotesi. Con un po' di creatività nella progettazione di una soluzione, dovrebbe esistere un percorso di MVP che non richiede il refactoring delle soluzioni esistenti. È consigliabile ritardare il refactoring, fino a quando l'ipotesi iniziale non può essere convalidata su larga scala.

## <a name="operating-model-innovations"></a>Innovazioni del modello operativo

Oltre ai moderni approcci all'innovazione per la creazione di app, sono state introdotte innovazioni relative alle operazioni delle app. Gli approcci hanno generato molti movimenti organizzativi. Uno dei più importanti è costituito da uno spostamento verso i modelli operativi [cloud Center of Excellence](../../organize/cloud-center-of-excellence.md) . Una volta completati e maturi, i team aziendali hanno la possibilità di fornire il proprio supporto operativo per una soluzione.

Il tipo di modello di gestione operativa self-service, disponibile in un cloud Center of Excellence, consente controlli più rigorosi e iterazioni più veloci nell'ambiente della soluzione. Questa operazione viene eseguita trasferendo il controllo operativo e la responsabilità al team aziendale.

Quando l'obiettivo è scalare o soddisfare la domanda globale di una soluzione esistente, questo approccio può essere sufficiente per convalidare un'ipotesi del cliente. Una volta migrata e leggermente modernizzata, il team aziendale avrebbe la possibilità di ridimensionare le soluzioni per testare una varietà di ipotesi riguardanti le coorti dei clienti che si occupano delle prestazioni, della distribuzione globale o di altre esigenze dei clienti ostacolate dall'IT. operazioni.

## <a name="reduce-overhead-and-management"></a>Riduzione del sovraccarico e della gestione

Maggiore è la manutenzione in una soluzione, più lenta sarà l'iterazione della soluzione. Accelera l'innovazione riducendo le operazioni di conseguenze sulla velocità disponibile.

Per preparare le numerose iterazioni necessarie per fornire una soluzione innovativa, è importante pensare in anticipo. È necessario ridurre al minimo gli oneri operativi iniziali del processo, privilegiando le opzioni senza server.

In Azure le opzioni per le applicazioni senza server possono includere [app Azure servizio](https://docs.microsoft.com/azure/app-service/overview), [Service Fabric](https://docs.microsoft.com/azure/architecture/example-scenario/infrastructure/service-fabric-microservices), [contenitori](https://docs.microsoft.com/azure/architecture/cloud-adoption/migrate/azure-best-practices/contoso-migration-rearchitect-container-sql)e così via.

In parallelo, Azure offre opzioni di dati di transazione senza server che riducono anche l'overhead. Nell' [elenco prodotti database](https://docs.microsoft.com/azure/#pivot=products&panel=databases) sono disponibili opzioni per l'hosting dei dati, senza la necessità di una piattaforma di dati completa.

## <a name="next-steps"></a>Passaggi successivi

A seconda dell'ipotesi e della soluzione, i principi in questo articolo possono essere utili per la progettazione di app che soddisfano le definizioni MVP e coinvolgono gli utenti. A questo punto, verranno illustrati i principi di [empowerment dell'adozione](./ci-cd.md), che illustrano come ottenere rapidamente l'applicazione e i dati nelle mani dei clienti in modo più rapido.

> [!div class="nextstepaction"]
> [Adozione potenziata](./ci-cd.md)
