---
title: 'Innovazione nel cloud: democratizzazione dei dati'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Introduzione all'innovazione cloud-democratizzare i dati
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: 242985f57cc377b78328e2277ba76f15abaec8b8
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73753028"
---
# <a name="democratize-data"></a>Democratizzare i dati

Carbone, olio e potenziale umano sono le tre risorse più consequenziali durante la rivoluzione industriale. Queste risorse compilavano società, mercati spostati e infine modifiche alle Nazioni. Nell'economia digitale esistono tre asset ugualmente importanti: dati, dispositivi e potenziale umano. Ognuno di questi asset ha un notevole potenziale di innovazione. Per qualsiasi lavoro di innovazione nell'era moderna, i dati sono il nuovo petrolio.

Attualmente, in ogni azienda ci sono sacche di dati che possono essere usati per trovare e soddisfare le esigenze dei clienti in modo più efficace. Sfortunatamente, il processo di data mining di questi dati per guidare l'innovazione è stato molto costoso e dispendioso in termini di tempo. Molte delle soluzioni più importanti alle esigenze dei clienti non sono soddisfatte perché le persone giuste non possono accedere ai dati necessari.

La democratizzazione dei dati è il processo che consente di ottenere questi dati nelle mani giuste per promuovere l'innovazione. Questo processo può assumere diverse forme, ma in genere include soluzioni per dati non elaborati inseriti o integrati, centralizzazione dei dati, condivisione dei dati e protezione dei dati. Quando questi metodi hanno esito positivo, gli esperti di tutta la società possono usare i dati per testare le ipotesi. In molti casi, i team di adozione del cloud possono [compilare con l'empatia dei clienti](./build.md) usando solo i dati e risolvendo rapidamente le esigenze dei clienti esistenti.

## <a name="process-of-democratizing-data"></a>Processo di democratizzazione dei dati

Le fasi seguenti guideranno le decisioni e gli approcci necessari per adottare una soluzione che consente di democratizzare i dati. Non tutte le fasi saranno necessariamente necessarie per compilare una soluzione specifica. Tuttavia, è necessario valutare ogni fase quando si compila una soluzione per un'ipotesi del cliente. Ognuno fornisce un approccio univoco alla creazione di soluzioni innovative.

![Processo per la democratizzazione dei dati](../../_images/innovate/democratize-data.png)

### <a name="share-data"></a>Condividere dati

Quando si esegue la [compilazione con Customer empatia](./build.md), tutti i processi elevano la necessità dei clienti su una soluzione tecnica. Poiché la democratizzazione dei dati non è un'eccezione, si inizia condividendo i dati. Per democratizzare i dati, deve includere una soluzione che condivide i dati con un consumer di dati. Il consumer di dati può essere un cliente diretto o un proxy che prende decisioni per i clienti. I consumer di dati approvati possono analizzare, interrogare e creare report sui dati centralizzati, senza alcun supporto da parte del personale IT.

Molte innovazioni riuscite sono state avviate come un prodotto minimo valido (MVP) che fornisce processi manuali basati sui dati per conto del cliente. In questo modello di concierge, un dipendente è il consumer di dati. Il dipendente usa i dati per aiutare il cliente. Ogni volta che il cliente attiva il supporto manuale, un'ipotesi può essere testata e convalidata. Questo approccio è spesso un mezzo economico per testare un'ipotesi incentrata sul cliente prima di investire molto in soluzioni integrate.

Gli strumenti principali per la condivisione diretta dei dati con i consumer di dati includono la creazione di report Self-Service o dati incorporati in altre esperienze, usando strumenti come [Power bi](https://docs.microsoft.com/power-bi).

> [!NOTE]
> Prima di condividere i dati, assicurarsi di aver letto le sezioni seguenti. La condivisione dei dati potrebbe richiedere la governance per fornire protezione per i dati condivisi. Inoltre, i dati potrebbero essere distribuiti in più cloud e potrebbero richiedere la centralizzazione. Molti dei dati potrebbero anche risiedere all'interno delle applicazioni, che richiedono la raccolta dei dati prima di poterla condividere.

### <a name="govern-data"></a>Governance dei dati

La condivisione dei dati può produrre rapidamente un MVP che è possibile usare nelle conversazioni dei clienti. Tuttavia, per trasformare i dati condivisi in una conoscenza utile e praticabile, è in genere necessario un po' di più. Dopo che un'ipotesi è stata convalidata tramite la condivisione dei dati, la fase successiva dello sviluppo è in genere governance dei dati.

La governance dei dati è un argomento ampio che può richiedere un framework dedicato. Tale grado di granularità esula dall'ambito del [Framework di adozione del cloud](../../index.md). Tuttavia, esistono diversi aspetti della governance dei dati che è opportuno prendere in considerazione non appena viene convalidata l'ipotesi del cliente. ad esempio:

- **I dati condivisi sono sensibili?** I [dati devono essere classificati](../../govern/policy-compliance/data-classification.md) prima di essere condivisi pubblicamente per proteggere gli interessi dei clienti e dell'azienda.
- **Se i dati sono sensibili, sono stati protetti?** La protezione dei dati sensibili deve essere un requisito per tutti i dati democratizzati. Il carico di lavoro di esempio incentrato sulla [protezione delle soluzioni dati](https://docs.microsoft.com/azure/architecture/data-guide/scenarios/securing-data-solutions) fornisce alcuni riferimenti per la protezione dei dati.
- **I dati sono catalogati?** Per la gestione dei dati a lungo termine è possibile acquisire i dettagli relativi ai dati condivisi. Gli strumenti per documentare i dati, ad esempio Azure Data Catalog, possono rendere questo processo molto più facile nel cloud. Le linee guida per l' [annotazione dei dati](https://docs.microsoft.com/azure/data-catalog/data-catalog-how-to-annotate) e la [documentazione delle origini dati](https://docs.microsoft.com/azure/data-catalog/data-catalog-how-to-documentation) possono contribuire ad accelerare il processo.

Quando la democratizzazione dei dati è importante per un'ipotesi mirata ai clienti, assicurarsi che la governance dei dati condivisi si trovi in un punto del piano di rilascio. Ciò consente di proteggere clienti, consumer di dati e la società.

### <a name="centralize-data"></a>Centralizzare i dati

Quando i dati vengono interrotti in un ambiente IT, le opportunità di innovazione possono essere estremamente vincolate, costose e dispendiose in termini di tempo. Il cloud offre nuove opportunità per centralizzare i dati tra i silo di dati. Quando è necessario centralizzare più origini dati per la [compilazione con l'empatia del cliente](./build.md), il cloud può accelerare il test delle ipotesi.

> [!CAUTION]
> La centralizzazione dei dati rappresenta un punto di rischio in qualsiasi processo di innovazione. Quando la centralizzazione dei dati è un [picco tecnico](./build.md#reduce-complexity-and-delay-technical-spikes) (in contrapposizione a un'origine del valore del cliente), si consiglia di ritardare la centralizzazione fino a quando non vengono convalidate le ipotesi del cliente.

Se è necessario centralizzare i dati, è necessario innanzitutto definire l'archivio dati appropriato per i dati centralizzati. È consigliabile stabilire una data warehouse nel cloud. Questa opzione scalabile offre una posizione centralizzata per tutti i dati. Questo tipo di soluzione è disponibile nelle opzioni OLAP (Online Analytical Processing) o Big Data.

Le architetture di riferimento per le soluzioni [OLAP](https://docs.microsoft.com/azure/architecture/data-guide/relational-data/online-analytical-processing) e [Big Data](https://docs.microsoft.com/azure/architecture/data-guide/big-data) possono essere utili per scegliere la soluzione più appropriata in Azure. Se è necessaria una soluzione ibrida, l'architettura di riferimento per l' [estensione dei dati locali](https://docs.microsoft.com/azure/architecture/data-guide/scenarios/hybrid-on-premises-and-cloud) può anche contribuire ad accelerare lo sviluppo di soluzioni.

> [!IMPORTANT]
> A seconda delle esigenze dei clienti e della soluzione allineata, un approccio più semplice può essere sufficiente. L'architetto del cloud deve sfidare il team a prendere in considerazione soluzioni di costo più ridotte che potrebbero comportare una convalida più rapida dell'ipotesi dei clienti, soprattutto durante le fasi iniziali dello sviluppo. La sezione seguente sulla raccolta di dati riguarda alcuni scenari che possono suggerire una soluzione diversa per la situazione specifica.

### <a name="collect-data"></a>Raccogliere i dati

Quando è necessario centralizzare i dati per soddisfare le esigenze dei clienti, è molto probabile che sia necessario raccogliere i dati da diverse origini e spostarli nell'archivio dati centralizzato. Esistono due forme principali di raccolta dati: *integrazione* e inserimento.

**Integrazione:** I dati che si trovano in un archivio dati esistente possono essere integrati nell'archivio dati centralizzato utilizzando tecniche tradizionali di spostamento dei dati. Questa operazione è particolarmente comune per gli scenari che interessano l'archiviazione dei dati multicloud. Queste tecniche prevedono l'estrazione dei dati dall'archivio dati esistente e quindi il relativo caricamento nell'archivio dati centrale. A un certo punto del processo, i dati vengono in genere trasformati in modo da essere più utilizzabili e pertinenti nell'archivio centrale.

Gli strumenti basati sul cloud hanno trasformato queste tecniche in strumenti con pagamento in base al consumo, riducendo la barriera all'ingresso per la raccolta e la centralizzazione dei dati. Strumenti come il servizio migrazione del database di Azure e Azure Data Factory sono due esempi. L'architettura di riferimento per [Data Factory con un archivio dati OLAP](https://docs.microsoft.com/azure/architecture/data-guide/relational-data/etl) è un esempio di una soluzione di questo tipo.

Inserimento **:** Alcuni dati non si trovano in un archivio dati esistente. Quando questi dati temporanei sono una fonte primaria di innovazione, è opportuno prendere in considerazione approcci alternativi. I dati temporanei possono trovarsi in un'ampia gamma di origini esistenti, ad esempio applicazioni, API, flussi di dati, dispositivi Internet degli elementi, blockchain, cache di applicazioni, contenuto multimediale o anche in file flat.

È possibile integrare queste diverse forme di dati in un archivio dati centrale in una soluzione OLAP o Big Data. Tuttavia, per le prime iterazioni del ciclo Build-Measure-Learn, una soluzione di elaborazione transazionale in linea (OLTP) potrebbe essere più che sufficiente per convalidare un'ipotesi del cliente. Le soluzioni OLTP non sono la soluzione di qualità più elevata per qualsiasi scenario di Reporting. Tuttavia, quando si esegue [la compilazione con l'empatia del cliente](./build.md), è più importante concentrarsi sulle esigenze dei clienti rispetto alle decisioni relative agli strumenti tecnici. Una volta convalidata l'ipotesi dei clienti su larga scala, potrebbe essere necessaria una piattaforma più adatta. L'architettura di riferimento negli [archivi dati OLTP](https://docs.microsoft.com/azure/architecture/data-guide/relational-data/online-transaction-processing) può aiutarti a determinare quale archivio dati è più appropriato per la tua soluzione.

**Virtualizza:** L'integrazione e l'inserimento dei dati possono a volte rallentare l'innovazione. Quando una soluzione per la virtualizzazione dei dati è già disponibile, può rappresentare un approccio più ragionevole. L'inserimento e l'integrazione possono duplicare i requisiti di archiviazione e sviluppo, aggiungere la latenza dei dati, aumentare la superficie di attacco, attivare problemi di qualità e migliorare le attività di governance. La virtualizzazione dei dati è un'alternativa più contemporanea che lascia i dati originali in un'unica posizione e crea query pass-through o memorizzate nella cache dei dati di origine.

SQL Server 2017 e Azure SQL Data Warehouse supportano entrambi la [polibase](https://docs.microsoft.com/sql/relational-databases/polybase/polybase-guide) , ovvero l'approccio alla virtualizzazione dei dati usata più di frequente in Azure.

## <a name="next-steps"></a>Passaggi successivi

Con una strategia per la democratizzazione dei dati sul posto, è opportuno valutare gli approcci per [coinvolgere i clienti attraverso le app](./apps.md).

> [!div class="nextstepaction"]
> [Coinvolgere i clienti tramite le app](./apps.md)
