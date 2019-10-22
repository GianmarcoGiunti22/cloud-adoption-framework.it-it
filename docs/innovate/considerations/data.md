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
ms.openlocfilehash: c0ef1165fc416814e0563ec29c4ad5901a83b032
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/21/2019
ms.locfileid: "72683264"
---
# <a name="democratize-data"></a>Democratizzare i dati

Il carbone, l'olio e il potenziale umano erano le tre risorse più consequenziali durante la rivoluzione industriale. Queste risorse compilavano società, mercati spostati e infine modifiche alle Nazioni. Nell'economia digitale esistono tre asset ugualmente importanti: dati, dispositivi e potenziale umano. In ognuno di questi asset è un potenziale innovazione. In ogni sforzo di innovazione, i dati sono il nuovo olio.

In ogni azienda oggi sono disponibili sacche di dati che potrebbero essere sfruttate per trovare e soddisfare le esigenze dei clienti più rapidamente. Sfortunatamente, il processo di data mining di questi dati per guidare l'innovazione è stato molto costoso e dispendioso in termini di tempo. Molte delle soluzioni più importanti alle esigenze dei clienti non sono soddisfatte perché le persone giuste non possono accedere ai dati necessari.

La democratizzazione dei dati è il processo che consente di ottenere questi dati nelle mani giuste per promuovere l'innovazione. Questo processo può assumere diverse forme, ma in genere include soluzioni per dati non elaborati inseriti o integrati, centralizzazione dei dati, condivisione dei dati e protezione dei dati. In caso di esito positivo, gli esperti della società possono sfruttare i dati per testare le ipotesi. In molti casi, i team di adozione del cloud possono [compilare con l'empatia dei clienti](./build.md) usando solo i dati, con un conseguente rapido effetto sulle esigenze dei clienti esistenti.

## <a name="process-of-democratizing-data"></a>Processo di democratizzazione dei dati

Le fasi seguenti guideranno le decisioni e gli approcci necessari per adottare una soluzione che consente di democratizzare i dati. Ogni fase potrebbe non essere necessaria per compilare una soluzione specifica. Ogni caso, tuttavia, deve essere valutato quando si compila una soluzione a un'ipotesi del cliente. Ognuno fornisce un approccio univoco alla creazione di soluzioni innovative.

![Processo per la democratizzazione dei dati](../../_images/innovate/democratize-data.png)

### <a name="share-data"></a>Condividere dati

Quando si [Compila con l'empatia del cliente](./build.md), tutti i processi si concentrano sulle esigenze dei clienti su una soluzione tecnica. La democratizzazione dei dati non è un'eccezione, pertanto si inizia con la condivisione dei dati. Per democratizzare i dati, deve includere una soluzione che condivide i dati con un consumer di dati. Il consumer dei dati può essere un cliente diretto o un proxy che prende decisioni per i clienti. I consumer di dati approvati hanno la possibilità di analizzare, interrogare e creare report sui dati centralizzati, senza alcun supporto da parte del personale IT.

Sono state avviate molte innovazioni di successo come MVP che forniscono processi manuali basati sui dati per conto del cliente. In questo modello di concierge, un dipendente è il consumer di dati. Il dipendente usa i dati per aiutare il cliente. Ogni volta che il cliente attiva il supporto manuale, un'ipotesi può essere testata e convalidata. Questo approccio è spesso un mezzo economico per testare un'ipotesi incentrata sul cliente prima di investire molto in soluzioni integrate.

Gli strumenti principali per la condivisione diretta dei dati con i consumer di dati, includono la creazione di report Self-Service o dati incorporati in altre esperienze, usando strumenti come [Power bi](https://docs.microsoft.com/power-bi).

> [!NOTE]
> Prima di condividere i dati, è importante tenere presente le sezioni seguenti. La condivisione dei dati può richiedere la governance per fornire protezione per i dati condivisi. Inoltre, i dati possono essere distribuiti in più cloud e potrebbero richiedere la centralizzazione. Molti dei dati possono anche trovarsi all'interno di applicazioni che richiedono la raccolta dei dati prima di condividerli.

### <a name="govern-data"></a>Governare i dati

La condivisione dei dati può produrre rapidamente un MVP che può essere usato nelle conversazioni dei clienti. Tuttavia, i dati da soli sono solo i dati. Per trasformare i dati condivisi in una conoscenza pratica, è spesso necessario un po' di più. Una volta che un'ipotesi è stata convalidata tramite la condivisione dei dati, la fase di sviluppo successiva è spesso la governance dei dati.

La governance dei dati è un argomento ampio che può richiedere un framework dedicato. Non rientra nell'ambito del [Framework di adozione del cloud](../../index.md). Tuttavia, esistono alcuni aspetti della governance dei dati che devono essere considerati, non appena viene convalidata l'ipotesi del cliente. Di seguito sono riportati alcuni esempi di queste domande:

- **I dati condivisi sono sensibili?** I [dati devono essere classificati](../../govern/policy-compliance/data-classification.md) prima di qualsiasi condivisione pubblica per proteggere gli interessi dei clienti e dell'azienda.
- **Se i dati sono sensibili, sono stati protetti?** La protezione dei dati sensibili deve essere un requisito per tutti i dati democratizzati. Il carico di lavoro di esempio incentrato sulla [protezione delle soluzioni dati](https://docs.microsoft.com/azure/architecture/data-guide/scenarios/securing-data-solutions.md) fornisce alcuni riferimenti per la protezione dei dati.
- **I dati sono catalogati?** Per la gestione dei dati a lungo termine è possibile acquisire i dettagli relativi ai dati condivisi. Gli strumenti per documentare i dati, ad esempio Azure Data Catalog, possono rendere questo processo molto più facile nel cloud. Le linee guida per l' [annotazione dei dati](https://docs.microsoft.com/azure/data-catalog/data-catalog-how-to-annotate) e la [documentazione delle origini dati](https://docs.microsoft.com/azure/data-catalog/data-catalog-how-to-documentation) possono contribuire ad accelerare il processo.

Quando la democratizzazione dei dati è importante per un'ipotesi mirata ai clienti, la governance dei dati condivisi dovrebbe essere in un punto del piano di rilascio per proteggere i clienti, i consumer di dati e la società.

### <a name="centralize-data"></a>Centralizzare i dati

Quando i dati vengono interrotti in un ambiente IT, le opportunità di innovazione possono essere estremamente vincolate, dispendiose e dispendiose in termini di tempo. Il cloud offre nuove opportunità per centralizzare i dati in diversi silo di dati. Quando è necessario centralizzare più origini dati per [creare con l'empatia del cliente](./build.md) , il cloud può accelerare il test delle ipotesi.

> [!CAUTION]
> La centralizzazione dei dati è un punto di rischio comune in qualsiasi processo di innovazione. Quando la centralizzazione dei dati è un [picco tecnico](./build.md#reduce-complexity-and-delay-technical-spikes), anziché un'origine del valore del cliente, è consigliabile ritardare la centralizzazione fino a quando l'ipotesi del cliente non è stata convalidata.

Se è necessario centralizzare i dati, il primo passaggio consiste nel definire l'archivio dati appropriato per i dati centralizzati. L'approccio consigliato consiste nel creare un data warehouse nel cloud. Questa opzione scalabile fornirà una posizione centrale per tutti i dati. Questo tipo di soluzione è disponibile nelle opzioni OLAP (Online Analytical Processing) o Big Data.

Le architetture di riferimento per le soluzioni [OLAP](https://docs.microsoft.com/azure/architecture/data-guide/relational-data/online-analytical-processing) e [Big Data](https://docs.microsoft.com/azure/architecture/data-guide/big-data) possono aiutare a scegliere la soluzione più appropriata in Azure. Se è necessaria una soluzione ibrida, l'architettura di riferimento per l' [estensione dei dati locali](https://docs.microsoft.com/azure/architecture/data-guide/scenarios/hybrid-on-premises-and-cloud) può anche contribuire ad accelerare lo sviluppo di soluzioni.

> [!IMPORTANT]
> A seconda delle esigenze del cliente e della soluzione allineata, potrebbe essere sufficiente una soluzione più semplice. L'architetto del cloud deve sfidare il team a prendere in considerazione soluzioni di costo più ridotte che potrebbero comportare una convalida più rapida dell'ipotesi dei clienti, soprattutto durante le fasi iniziali dello sviluppo. La sezione sulla raccolta dei dati di seguito definirà alcuni scenari che potrebbero richiedere una soluzione diversa.

### <a name="collect-data"></a>Raccogliere i dati

Quando i dati devono essere centralizzati per fornire una necessità del cliente, è molto probabile che i dati debbano essere raccolti anche da varie origini e spostati nell'archivio dati centralizzato. Esistono due forme principali di raccolta dati: integrazione e inserimento. Ogni metodo consente di raccogliere i dati in modo diverso.

**Integra:** I dati esistenti che si trovano in un archivio dati esistente possono essere integrati nell'archivio dati centralizzato utilizzando tecniche tradizionali di spostamento dei dati. Questa operazione è particolarmente comune per gli scenari che interessano l'archiviazione dei dati multicloud. Queste tecniche sono costituite dall'estrazione dei dati dall'archivio dati esistente. Quindi caricare i dati nell'archivio dati centrale. A un certo punto del processo, i dati vengono spesso trasformati in modo da essere più utilizzabili e pertinenti nell'archivio centrale.

Gli strumenti basati su cloud hanno trasformato queste tecniche in strumenti con pagamento in base al consumo, riducendo la barriera all'ingresso per la raccolta e la centralizzazione dei dati. Strumenti come servizio migrazione dati e Data Factory sono due esempi comuni in Azure. L'architettura di riferimento per [Data Factory con un archivio dati OLAP](https://docs.microsoft.com/azure/architecture/data-guide/relational-data/etl) fornisce un esempio di tale soluzione.

Inserimento **:** Alcuni dati non sono in alcun archivio dati esistente. Quando questi dati temporanei rappresentano una fonte primaria di innovazione, è opportuno considerare approcci alternativi. I dati temporanei possono essere trovati in un'ampia gamma di origini esistenti, ad esempio applicazioni, API, flussi di dati, dispositivi per le cose, blockchain, cache di applicazioni, contenuto multimediale o persino file flat.

Queste diverse forme di dati possono essere integrate in un archivio dati centrale in una soluzione OLAP o Big Data. Tuttavia, per le prime iterazioni dei cicli Build-Measure-Learning, una soluzione di elaborazione transazionale (OLTP) online può essere più che sufficiente per convalidare un'ipotesi del cliente. Le soluzioni OLTP non sono la soluzione di qualità più elevata per qualsiasi scenario di Reporting. Tuttavia, quando la [compilazione con il Customer empatia](./build.md) si concentra sulla necessità del cliente, ha la priorità rispetto alle decisioni tecniche di strumenti. Una volta convalidata l'ipotesi dei clienti su larga scala, potrebbe essere necessaria una piattaforma più appropriata. L'architettura di riferimento negli [archivi dati OLTP](https://docs.microsoft.com/azure/architecture/data-guide/relational-data/online-transaction-processing) può aiutare a determinare quale archivio dati è più appropriato per la soluzione.

**Virtualizza:** L'integrazione e l'inserimento dei dati possono a volte rallentare l'innovazione. Quando è già disponibile una soluzione per la virtualizzazione dei dati, potrebbe trattarsi di un approccio più pertinente. L'inserimento e l'integrazione possono duplicare i requisiti di archiviazione/sviluppo, aggiungere la latenza dei dati, aumentare la superficie di attacco, inserire problemi di qualità e migliorare le attività di governance. La virtualizzazione dei dati è un'alternativa più moderna che lascia i dati originali in un'unica posizione e crea query pass-through o memorizzate nella cache dei dati di origine.

SQL Server 2017 e Azure SQL Data Warehouse supportano entrambi la [polibase](/sql/relational-databases/polybase/polybase-guide) , ovvero l'approccio alla virtualizzazione dei dati usata più di frequente in Azure.

## <a name="next-steps"></a>Passaggi successivi

Con una strategia per la democratizzazione dei dati sul posto, il passaggio successivo consiste nel valutare gli approcci per [coinvolgere i clienti attraverso le app](./apps.md).

> [!div class="nextstepaction"]
> [Coinvolgere i clienti tramite le app](./apps.md)
