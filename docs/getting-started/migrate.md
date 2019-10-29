---
title: Inizia un percorso di migrazione cloud in Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Inizia un percorso di migrazione cloud in Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/10/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: overview
ms.openlocfilehash: 8870f5ebeab855ec841ed00d109245a1efdeff20
ms.sourcegitcommit: 7ffb0427bba71177f92618b2f980e864b72742f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/29/2019
ms.locfileid: "73048325"
---
# <a name="begin-a-cloud-migration-journey-in-azure"></a>Inizia un percorso di migrazione cloud in Azure

Usare il Framework di adozione Microsoft Cloud per Azure per iniziare un percorso di migrazione cloud. Questo Framework fornisce indicazioni complete per la transizione dei carichi di lavoro delle applicazioni legacy al cloud usando tecnologie innovative basate sul cloud.

## <a name="executive-summary"></a>Riepilogo

Il Framework di adozione del cloud consente ai clienti di adottare un percorso semplificato di adozione del cloud. Questo Framework contiene informazioni dettagliate su un percorso di adozione cloud end-to-end, a partire da risultati aziendali mirati e quindi allineando la preparazione e le valutazioni del cloud con obiettivi aziendali chiaramente definiti. Questi risultati vengono realizzati tramite un percorso definito per l'adozione del cloud. Con l'adozione basata sulla migrazione, il percorso definito è incentrato principalmente sulla migrazione di carichi di lavoro locali nel cloud. In alcuni casi questo percorso include la modernizzazione dei carichi di lavoro per aumentare il ritorno sugli investimenti dal lavoro di migrazione.

Questo Framework è stato progettato principalmente per architetti Cloud e per i team strategici del cloud leader nell'adozione del cloud. Tuttavia, molti argomenti di questo Framework sono rilevanti per altri ruoli nell'ambito dell'azienda. Gli architetti del cloud vengono spesso usati come facilitatori per coinvolgere ciascuno dei ruoli pertinenti. Questo riepilogo esecutivo è progettato per preparare i vari ruoli prima di facilitare le conversazioni.

> [!NOTE]
> Questa guida è attualmente un'anteprima pubblica. La terminologia, gli approcci e le linee guida sono stati accuratamente testati con clienti, partner e team Microsoft durante questa fase di anteprima. Di conseguenza, il sommario e le linee guida possono cambiare leggermente nel tempo.

## <a name="motivations"></a>Motivazioni

Le migrazioni cloud possono aiutare le aziende a raggiungere i risultati aziendali desiderati. Una chiara comunicazione delle motivazioni, dei driver aziendali e delle misurazioni del successo sono importanti fondamenta per prendere decisioni sagge durante le attività di migrazione nel cloud. La tabella seguente classifica le motivazioni per semplificare la conversazione. Si presuppone che la maggior parte delle aziende abbia motivazioni in ogni classificazione. L'obiettivo di questa tabella non è quello di limitare i risultati, ma di rendere più semplice la definizione delle priorità per gli obiettivi e le motivazioni generali:

<!-- markdownlint-disable MD033 -->

|Eventi aziendali critici | Motivazioni della migrazione | Motivazioni dell'innovazione |
|---------|---------|---------|
| Uscita Data Center<br/><br/>Fusioni, acquisizioni o dismissioni<br/><br/>Riduzioni delle spese di capitale<br/><br/>Fine del supporto per le tecnologie mission-critical<br/><br/>Risposta alle modifiche di conformità alle normative<br/><br/>Soddisfare i nuovi requisiti di sovranità dei dati<br/><br/>Ridurre le rotture e migliorare la stabilità IT|Risparmio sui costi<br/><br/>Riduzione della complessità tecnica o del fornitore<br/><br/>Ottimizzazione delle operazioni interne<br/><br/>Aumentare l'agilità aziendale<br/><br/>Prepararsi per nuove funzionalità tecniche<br/><br/>Scalabilità per soddisfare le esigenze del mercato<br/><br/>Scalabilità per soddisfare le esigenze geografiche|Prepararsi per nuove funzionalità tecniche<br/><br/>Crea nuove funzionalità tecniche<br/><br/>Scalabilità per soddisfare le esigenze del mercato<br/><br/>Scalabilità per soddisfare le esigenze geografiche<br/><br/>Migliorare le esperienze dei clienti e gli impegni<br/><br/>Trasforma prodotti o servizi<br/><br/>Interrompi il mercato con nuovi prodotti o servizi|

<!-- markdownlint-enable MD033 -->

Quando una risposta a eventi aziendali critici è la priorità più elevata, è importante impegnarsi prima di tutto nell' [implementazione del cloud](#cloud-implementation) , spesso in parallelo con la strategia e le attività di pianificazione. Adottare un approccio di questo tipo richiede un mindset di crescita e una volontà di migliorare in modo iterativo i processi, in base a lezioni dirette apprese.

Quando le motivazioni della migrazione rappresentano una priorità, la [strategia e la pianificazione](#cloud-strategy-and-planning) svolgono un ruolo fondamentale prima del processo. Tuttavia, è consigliabile che l' [implementazione](#cloud-implementation) del primo carico di lavoro venga eseguita in parallelo con la pianificazione, per aiutare il team a comprendere e pianificare le curve di apprendimento associate al cloud.

Quando le motivazioni dell'innovazione sono la priorità più alta, la strategia e la pianificazione richiedono investimenti aggiuntivi nelle fasi iniziali del processo, per garantire il bilanciamento del portfolio e il corretto allineamento degli investimenti effettuati durante il cloud. Per altre informazioni su come realizzare le motivazioni dell'innovazione, vedere [comprendere il percorso di innovazione](./innovate.md).

Preparare tutti i partecipanti attraverso l'impegno di migrazione con la consapevolezza delle motivazioni garantirà decisioni più sagge. La metodologia di migrazione seguente illustra il modo in cui Microsoft suggerisce ai clienti di prendere le decisioni in una metodologia coerente.

## <a name="migration-approach"></a>Approccio alla migrazione

Il Framework di adozione del cloud stabilisce un costrutto di alto livello di piano, pronto, adozione per raggruppare i tipi di lavoro richiesto per qualsiasi adozione del cloud. Questo riepilogo esecutivo si basa su tale flusso di alto livello per stabilire processi iterativi che consentono di semplificare le attività di sviluppo/spostamento/ottimizzazione **e** l'impegno di modernizzazione in un unico approccio tra tutte le attività di migrazione nel cloud.

Questo approccio è costituito da due metodologie o aree di interesse: strategia cloud & pianificazione e implementazione cloud. La [motivazione](#motivations) o il risultato aziendale desiderato per una migrazione cloud determina spesso quanto un team deve investire in [strategia e pianificazione](#cloud-strategy-and-planning) e [implementazione](#cloud-implementation). Queste motivazioni possono anche influenzare le decisioni di esecuzione in sequenza o in parallelo.

## <a name="cloud-implementation"></a>Implementazione cloud

L'implementazione cloud è un processo iterativo per la migrazione e la modernizzazione delle proprietà digitali in linea con i risultati aziendali mirati e i controlli di gestione delle modifiche. Durante ogni iterazione, viene eseguita la migrazione o la modernizzazione dei carichi di lavoro in linea con la strategia e il piano. Le decisioni relative a IaaS, PaaS o Hybrid vengono effettuate durante la fase di valutazione per ottimizzare il controllo e l'esecuzione. Tali decisioni guideranno gli strumenti usati durante la fase di migrazione. Questo modello può essere utilizzato con una strategia e una pianificazione minime. Tuttavia, per garantire la massima redditività dell'azienda, è consigliabile che sia l'IT che l'azienda si allineano a una strategia chiara e pianificano di guidare le attività di implementazione.

![Metodologia di implementazione cloud del Framework di adozione cloud](../_images/operational-transformation-migrate.png)

L'obiettivo di questo sforzo è la migrazione o la modernizzazione dei carichi di lavoro. Un carico di lavoro è una raccolta di infrastruttura, applicazioni e dati che supporta collettivamente un obiettivo aziendale comune o l'esecuzione di un processo di business comune. Esempi di carichi di lavoro possono includere elementi come un'applicazione line-of-business, una soluzione per la contabilità delle risorse umane, una soluzione CRM, un flusso di lavoro di approvazione di documenti finanziari o una soluzione business intelligence. I carichi di lavoro possono includere anche risorse tecniche condivise come una data warehouse che supporta diverse altre soluzioni. In alcuni casi, un carico di lavoro può essere rappresentato da un singolo asset come un server autonomo, un'applicazione o una piattaforma dati.

Le migrazioni cloud sono spesso considerate un singolo progetto all'interno di un programma più ampio per semplificare le operazioni IT, i costi o la complessità. La metodologia di implementazione del cloud consente di allineare le attività tecniche all'interno di una serie di migrazioni del carico di lavoro a valori di business di livello superiore descritti nella strategia e nel piano cloud.

**Guida introduttiva:** Per iniziare a usare un'implementazione cloud, la [Guida alla migrazione di Azure](../migrate/azure-migration-guide/index.md) e la [Guida all'installazione di Azure](../ready/azure-setup-guide/index.md) descrivono gli strumenti e i processi di alto livello necessari per la corretta esecuzione di un'implementazione cloud. La migrazione del primo carico di lavoro con queste guide consentirà al team di superare le curve di apprendimento iniziali prima del processo di pianificazione. Successivamente, è opportuno considerare altre considerazioni sull' [elenco di controllo dell'ambito espanso](../migrate/expanded-scope/index.md), le [procedure consigliate](../migrate/azure-best-practices/index.md) per la migrazione e la [valutazione della migrazione](../migrate/migration-considerations/index.md), per allineare le linee guida di base ai vincoli, ai processi e ai team univoci del proprio lavoro. strutture e obiettivi.

## <a name="cloud-strategy-and-planning"></a>Strategia e pianificazione cloud

La strategia e la pianificazione del cloud sono una metodologia incentrata sull'allineamento di risultati aziendali, priorità e vincoli per definire una strategia e un piano di migrazione chiari. Il piano risultante (o backlog di migrazione) delinea l'approccio alla migrazione e alla modernizzazione nel portfolio IT, che può estendersi a interi Data Center, più carichi di lavoro o raccolte varie di infrastruttura, applicazioni e dati. Una gestione corretta del portfolio IT attraverso le attività di implementazione del cloud aiuterà i risultati aziendali desiderati.

![Panoramica di Cloud Adoption Framework (CAF)](../_images/caf-overview.png)

**Guida introduttiva:** Il resto di questo articolo prepara il lettore per l'applicazione corretta della metodologia di pianificazione e strategia cloud di adozione del cloud. Vengono inoltre descritte risorse e collegamenti aggiuntivi che consentono al lettore di adottare questo approccio per guidare le attività di implementazione del cloud.

### <a name="methodology-explained"></a>Spiegazione della metodologia

La metodologia di pianificazione e strategia cloud di adozione del cloud si basa su un approccio incrementale all'implementazione cloud che è allineato alle strategie tecnologiche agile, alla maturità culturale basata sugli approcci alla crescita mentale e alle strategie basate su risultati aziendali. Questa metodologia è costituita dai seguenti componenti di alto livello che guidano l'implementazione di ogni strategia.

Come illustrato nell'immagine precedente, questo framework allinea le decisioni strategiche a un numero ridotto di processi contenuti che operano all'interno di un modello iterativo. Sebbene venga descritta in un documento lineare, è previsto che ognuno dei processi seguenti venga maturo in parallelo con le iterazioni dell'implementazione del cloud. I collegamenti per ogni processo consentiranno di definire lo stato finale e i mezzi di maturazione verso lo stato finale desiderato:

- **[Piano](../strategy/index.md):** Quando l'implementazione tecnica è allineata con obiettivi aziendali chiari, è molto più facile misurare e allineare il successo tra più attività di implementazione del cloud, indipendentemente dalle decisioni tecniche.
- **[Pronto](../ready/index.md):** Preparare l'azienda, la cultura, le persone e l'ambiente per le modifiche in arrivo comportano un successo in ogni sforzo e accelerano l'implementazione e i progetti di modifica.
- **Adottare:** Garantire la corretta implementazione delle modifiche desiderate, nei processi IT e aziendali, per ottenere risultati aziendali.
  - **[Migrate](../migrate/index.md):** esecuzione iterativa della [metodologia di implementazione del cloud](#cloud-implementation) che rispetta il processo testato di valutazione, migrazione, ottimizzazione e sicurezza & gestire per creare un processo ripetibile per la migrazione dei carichi di lavoro.
  - **[Innovazione](../innovate/index.md):** Valorizza le attività aziendali attraverso attività di innovazione che sbloccano nuove competenze tecniche e funzionalità aziendali espanse.
- **[Regola](../govern/index.md):** Allinea i criteri aziendali ai rischi tangibili, attenuati tramite i criteri, i processi e gli strumenti di governance basati sul cloud.
- **[Gestione](../manage/index.md):** Espandi le operazioni IT per garantire che le soluzioni basate sul cloud possano essere gestite tramite processi sicuri e convenienti usando strumenti operativi moderni e basati sul cloud.
- **[Organizzare](../organize/index.md):** Allinea persone e team per offrire operazioni e adozione appropriate per il cloud.

In questa esperienza di migrazione questo Framework verrà usato per risolvere le ambiguità, gestire le modifiche e guidare i team interfunzionali attraverso la realizzazione di risultati aziendali.

### <a name="common-cultural-changes-resulting-from-adherence-to-this-methodology"></a>Modifiche culturali comuni risultanti dall'aderenza a questa metodologia

Il lavoro richiesto per realizzare i risultati aziendali desiderati può provocare lievi modifiche alle impostazioni cultura e a un certo grado di cultura dell'azienda. Di seguito sono riportate alcune modifiche culturali comuni riscontrate in questo processo:

- È probabile che il team IT adotti nuove competenze per supportare i carichi di lavoro nel cloud.
- L'esecuzione di una migrazione cloud incoraggia approcci iterativi o agile.
- L'inclusione della governance del cloud tende anche ad ispirare approcci DevOps.
- La creazione di un team strategico Cloud può condurre a una stretta integrazione tra i responsabili IT e aziendali.
- Collettivamente, queste modifiche tendono a produrre agilità aziendale e IT.

La modifica culturale non è un obiettivo della migrazione cloud o del Framework di adozione del cloud, ma si tratta di un risultato comunemente sperimentato.
Le modifiche culturali non sono direttamente guidate, ma le modifiche minime apportate alle impostazioni cultura sono incorporate nei miglioramenti e negli approcci del processo suggerito per tutte le linee guida.

### <a name="common-technical-efforts-associated-with-this-methodology"></a>Attività tecniche comuni associate a questa metodologia

Durante l'implementazione della strategia cloud e la pianificazione del team IT si concentrerà su una percentuale elevata di tempo per la migrazione delle risorse digitali esistenti al cloud. Durante questa operazione, sono previste modifiche minime al codice, ma possono essere spesso limitate alle modifiche di configurazione. In molti casi, è possibile effettuare una forte motivazione aziendale per la modernizzazione nell'ambito della migrazione cloud.

### <a name="common-workload-examples"></a>Esempi di carico di lavoro comuni

La strategia e la pianificazione del cloud spesso sono destinate a una vasta gamma di carichi di lavoro e applicazioni. All'interno del portfolio, viene in genere eseguita la migrazione dei tipi di applicazioni o carichi di lavoro comuni. Di seguito sono riportati alcuni esempi:

- Applicazioni line-of-business
- Applicazioni rivolte ai clienti
- Applicazioni di terze parti
- Piattaforme di analisi dei dati
- Soluzioni distribuite a livello globale
- Soluzioni a scalabilità elevata

### <a name="common-technologies-migrated"></a>Tecnologie comuni migrate

Le tecnologie migrate nel cloud si espandono costantemente quando i provider di servizi cloud aggiungono nuove funzionalità. Di seguito sono riportati alcuni esempi di tecnologie comunemente riscontrate in una migrazione:

- Windows e SQL Server
- Database Linux e Open Source (OSS)
- Unstructure/NoSQL database
- SAP in Azure
- Analytics (data warehouse, Data Lake)

## <a name="next-steps-lifecycle-solution"></a>Passaggi successivi: soluzione ciclo di vita

Il Framework di adozione del cloud è una soluzione del ciclo di vita. È progettato per aiutare i lettori a iniziare a eseguire il proprio viaggio e ai lettori che si trovano a fondo nella migrazione. Di conseguenza, il contenuto è molto contesto e specifico del pubblico. I passaggi successivi sono più allineati al processo di alto livello che il lettore desidera migliorare successivamente.

> [!div class="nextstepaction"]
> [Strategia](../strategy/index.md)
>
> [Pianificare](../plan/index.md)
>
> [Pronto](../ready/index.md)
>
> [Migrazione](../migrate/index.md)
>
> [Innovazione](../innovate/index.md)
>
> [Governare](../govern/index.md)
>
> [Manage](../manage/index.md)
>
> [Organizzare](../organize/index.md)
