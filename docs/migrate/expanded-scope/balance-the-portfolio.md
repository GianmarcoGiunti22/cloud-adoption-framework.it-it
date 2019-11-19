---
title: Bilanciare il portfolio
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: È possibile bilanciare il portfolio cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 9834778e7aaddc616d595e874459fa7bd3eb61e3
ms.sourcegitcommit: 50788e12bb744dd44da14184b3e884f9bddab828
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2019
ms.locfileid: "74159905"
---
# <a name="balance-the-portfolio"></a>Bilanciare il portfolio

L'adozione del cloud è un progetto di gestione del portfolio, astutamente camuffato da implementazione tecnica. Analogamente a qualsiasi esercizio di gestione del portfolio, il bilanciamento del portfolio è fondamentale. A livello strategico, ciò significa bilanciamento della migrazione, dell'innovazione e della sperimentazione per sfruttare al meglio il cloud. Quando il lavoro richiesto per l'adozione del cloud si spinge troppo in una direzione o in un'altra, la complessità si insinua nel lavoro richiesto per la migrazione. Questo articolo illustra gli approcci per ottenere il bilanciamento del portfolio.

## <a name="general-scope-expansion"></a>Espansione dell'ambito generale

Questo argomento è strategico. Di conseguenza, l'approccio adottato in questo articolo lo è altrettanto. Per fondare la strategia nelle decisioni basate sui dati, questo articolo presuppone che sia già stata fatta una valutazione riguardo il [digital estate](../../digital-estate/index.md) esistente o si sia in procinto di farlo. L'obiettivo di questo approccio consiste nell'agevolare la valutazione dei carichi di lavoro per garantire un bilanciamento corretto del portfolio attraverso domande qualitative e perfezionamento del portfolio.

### <a name="document-business-outcomes"></a>Documentare i risultati aziendali

Prima di bilanciare il portfolio, è importante documentare e condividere i risultati aziendali alla base del lavoro richiesto per la migrazione del cloud. Per alcuni esempi di risultati aziendali generali relativi alle migrazioni cloud, vedere il [riepilogo di cloud Migration Executive](../../getting-started/migrate.md).

La tabella seguente può essere utile per documentare e condividere i risultati aziendali desiderati. È importante notare che la maggior parte delle aziende sta perseguendo diversi risultati alla volta. L'importanza di questo esercizio consiste nel chiarire i risultati correlati più direttamente al lavoro richiesto per la migrazione al cloud:

|Risultato  |Misurato da  |Obiettivo  |Intervallo di tempo  |Priorità per il lavoro richiesto  |
|---------|---------|---------|---------|---------|
|Riduzione dei costi IT     |Budget per il data center         |Riduzione di 2 milioni di dollari         |12 mesi         |#1         |
|Uscita data center     |Uscire dai data center         |2 data center         |6 mesi         |#2         |
|Aumentare l'agilità aziendale     |Migliorare il time-to-market  |Ridurre i tempi di distribuzione di sei mesi         |2 anni         |#3        |
|Migliorare l'esperienza dei clienti     |Soddisfazione dei clienti (indice CSAT)         |10% del piano di query         |12 mesi         |#4         |

> [!IMPORTANT]
> La tabella precedente è un esempio fittizio e non deve essere usata per impostare le priorità. In molti casi, questa tabella potrebbe considerare un antipattern posizionando i risparmi sui costi al di sopra delle esperienze dei clienti.

La tabella precedente potrebbe rappresentare accuratamente le priorità del team di strategia del cloud e del team di adozione del cloud che si occupano della supervisione di una migrazione al cloud. A causa dei vincoli a breve termine, questo team pone una maggiore enfasi sulla riduzione dei costi IT e dà priorità a un'uscita del data center come mezzo per ottenere tali riduzioni. Tuttavia, documentando le priorità concorrenti in questa tabella, il team di adozione del cloud può aiutare il team di strategia del cloud a identificare le opportunità per allineare meglio l'implementazione della strategia di portfolio globale.

### <a name="move-fast-while-maintaining-balance"></a>Spostarsi velocemente mantenendo il bilanciamento

Il materiale sussidiario relativo alla [razionalizzazione incrementale del digital estate](../../digital-estate/index.md) suggerisce un approccio in cui la razionalizzazione inizia con una posizione sbilanciata. Il team di strategia del cloud deve valutare ogni carico di lavoro per la compatibilità con un approccio di rehosting. Questo approccio è consigliato perché consente la valutazione rapida di un digital estate complesso basato su dati quantitativi. Questo presupposto iniziale consente al team di adozione del cloud di interagire rapidamente, riducendo i tempi per i risultati aziendali. Tuttavia, come indicato in questo articolo, le domande qualitative forniranno il bilanciamento necessario nel portfolio. Questo articolo descrive il processo di creazione del bilanciamento promesso.

### <a name="importance-of-sunset-and-retire-decisions"></a>Importanza delle decisioni relative al termine e al ritiro

La tabella presente nella sezione precedente relativa alla [documentazione dei risultati aziendali](#document-business-outcomes), non presenta un risultato chiave che supporterebbe l'obiettivo principale nella riduzione dei costi IT. Quando le riduzioni dei costi IT si collocano in qualsiasi punto dell'elenco dei risultati aziendali, è importante considerare il potenziale per terminare o ritirare i carichi di lavoro. In alcuni scenari, il risparmio sui costi può derivare dalla MANCATA migrazione dei carichi di lavoro che non garantiscono un investimento a breve termine. Alcuni clienti hanno segnalato risparmi sui costi superiori al 20% di riduzione dei costi totali grazie al ritiro dei carichi di lavoro poco sfruttati.

Per bilanciare il portfolio in modo da riflettere meglio le decisioni relative al termine e al ritiro, il team di strategia del cloud e il team di adozione del cloud sono invitati a porre le domande seguenti riguardo ogni carico di lavoro all'interno dei processi di valutazione e migrazione:

- Il carico di lavoro è stato usato dagli utenti finali negli ultimi sei mesi?
- Il traffico dell'utente finale è coerente o in crescita?
- Questo carico di lavoro sarà necessario per l'azienda da qui a un anno?

Se la risposta a una di queste domande è "No", il carico di lavoro in questione potrebbe essere candidato al ritiro. Se il potenziale di ritiro viene confermato dal proprietario dell'app, potrebbe non essere utile eseguire la migrazione del carico di lavoro. Questa operazione richiede alcune domande di qualifica:

- È possibile stabilire un piano di ritiro o un piano di termine per questo carico di lavoro?
- Questo carico di lavoro può essere ritirato prima dell'uscita del data center?

Se la risposta a entrambe le domande è "Sì", sarebbe opportuno prendere in considerazione la _mancata_ migrazione del carico di lavoro. Questo approccio consente di soddisfare gli obiettivi di riduzione dei costi e di uscita dal data center.

Se la risposta a una delle due domande è "No", potrebbe essere opportuno stabilire un piano per l'hosting del carico di lavoro fino a quando non può essere ritirato. Questo piano può includere lo stato di trasferimento delle risorse a un data center con costi inferiori o a un data center alternativo per ridurre i costi e uscire da un data center.

## <a name="suggested-prerequisites"></a>Prerequisiti suggeriti

I prerequisiti specificati nella guida della linea di base dovrebbero comunque essere sufficienti per risolvere questo argomento complesso. Tuttavia, l'inventario delle risorse e il patrimonio digitale dovrebbero essere evidenziati e in grassetto tra questi prerequisiti, poiché i dati saranno in grado di gestire le attività seguenti.

## <a name="assess-process-changes"></a>Modifiche del processo di valutazione

Per il bilanciamento del portfolio è necessaria un'analisi qualitativa aggiuntiva durante il processo di valutazione per semplificare la razionalizzazione del portfolio.

### <a name="suggested-action-during-the-assess-process"></a>Azione suggerita durante il processo di valutazione

In base ai dati della tabella riportata nella sezione precedente relativa alla [documentazione dei risultati aziendali](#document-business-outcomes) è probabile che il portfolio si avvicini troppo a un modello di esecuzione incentrato sulla migrazione. Se l'esperienza del cliente fosse in cima alle priorità sarebbe più probabile ottenere un portfolio altamente innovativo. Non è giusto o sbagliato, ma propendere troppo in una direzione si traduce comunemente in una diminuzione dei ritorni, aggiunge inutili complessità e aumenta i tempi di esecuzione legati ai lavori richiesti per l'adozione del cloud.

Per ridurre la complessità, è consigliabile seguire un approccio tradizionale alla razionalizzazione del portfolio, ma in un modello iterativo. La procedura seguente illustra un modello qualitativo per un approccio di questo tipo:

- Il team di strategia del cloud mantiene un backlog con priorità dei carichi di lavoro da sottoporre a migrazione.
- Il team di strategia del cloud e il team di adozione del cloud organizzano una riunione di pianificazione del rilascio prima del completamento di ogni versione.
- Nella riunione di pianificazione del rilascio, i team si accordano sui primi 5-10 carichi di lavoro nel backlog con priorità.
- Al di fuori della riunione di pianificazione del rilascio, il team di adozione del cloud pone le domande seguenti sui proprietari dell'applicazione e sugli esperti di dominio:
  - Questa applicazione può essere sostituita con una piattaforma distribuita come servizio Piattaforma distribuita come servizio (PaaS, Platform as a Service) equivalente?
  - Questa applicazione è un'applicazione di terze parti?
  - Il budget è stato approvato per investire nello sviluppo continuo dell'applicazione nei prossimi 12 mesi?
  - Lo sviluppo aggiuntivo di questa applicazione migliora l'esperienza del cliente? Crea un differenziatore competitivo? Aumenta i ricavi per l'azienda?
  - I dati all'interno di questo carico di lavoro contribuiranno a un'innovazione downstream correlata a BI, Machine Learning, Internet delle cose o tecnologie correlate?
  - Il carico di lavoro è compatibile con le moderne piattaforme di applicazioni come Servizio app di Azure?
- Le risposte alle domande precedenti e qualsiasi altra analisi qualitativa richiesta influenzeranno quindi le rettifiche del backlog con priorità. Queste rettifiche possono includere:
  - Se un carico di lavoro può essere sostituito con una soluzione PaaS, può essere rimosso completamente dal backlog di migrazione. Come attività, è necessario aggiungere almeno una diligenza per decidere tra rehost e Replace, riducendo temporaneamente la priorità del carico di lavoro dal backlog di migrazione.
  - Se un carico di lavoro è (o dovrebbe essere) sottoposto a un avanzamento dello sviluppo, può rientrare in un modello refactoring-Rebuild. Poiché l'innovazione e la migrazione richiedono competenze tecniche diverse, le applicazioni che si allineano a un approccio refactoring-Rebuild devono essere gestite tramite un backlog di innovazione anziché un backlog di migrazione.
  - Se un carico di lavoro fa parte di un'innovazione downstream, potrebbe essere opportuno effettuare il refactoring della piattaforma dati lasciando però i livelli dell'applicazione come candidato per il rehosting. Effettuare il refactoring secondario della piattaforma dati di un carico di lavoro può spesso essere risolto in una migrazione o in un backlog di innovazione. Questo risultato della razionalizzazione può risultare in elementi di lavoro più dettagliati nel backlog, ma in caso contrario non è necessario modificare le priorità.
  - Se un carico di lavoro non è strategico ma è compatibile con le moderne piattaforme di hosting di applicazioni basate sul cloud, potrebbe essere opportuno eseguire un refactoring secondario all'applicazione per distribuirla come app moderna. Questo può contribuire al risparmio complessivo grazie alla riduzione dei requisiti generali per le licenze IaaS e del sistema operativo della migrazione al cloud.
  - Se un carico di lavoro è un'applicazione di terze parti e i dati del carico di lavoro non sono pianificati per l'uso in un'innovazione downstream, potrebbe essere preferibile lasciare l'opzione di rehosting nel backlog.

Queste domande non devono essere la portata dell'analisi qualitativa completata per ogni carico di lavoro, ma sono utili per condurre una conversazione sull'indirizzamento della complessità di un portfolio sbilanciato.

## <a name="migrate-process-changes"></a>Modifiche del processo di migrazione

Durante la migrazione, le attività di bilanciamento del portfolio possono avere un impatto negativo sulla velocità di migrazione (velocità con cui viene eseguita la migrazione delle risorse). Il materiale sussidiario seguente consente di approfondire i motivi e le modalità in cui allineare il lavoro per evitare interruzioni del lavoro richiesto per la migrazione.

### <a name="suggested-action-during-the-migrate-process"></a>Azione suggerita durante il processo di migrazione

La razionalizzazione del portfolio richiede una diversità di lavoro tecnico richiesto. Si tenta di far corrispondere i team di adozione del cloud alla diversità del portfolio all'interno dei lavori richiesti per la migrazione. Gli stakeholder aziendali di richiedono un singolo team di adozione del cloud per affrontare l'intero backlog di migrazione. Si tratta di un approccio consigliato raramente, in molti casi può essere controproducente.

Queste diverse attività devono essere segmentate in due o più team di adozione del cloud. Se come modalità di esecuzione di esempio viene usato un modello a due team, allora Team 1 corrisponde al team di migrazione e Team 2 a quello di innovazione. Per i lavori che richiedono uno sforzo maggiore, questi team possono essere ulteriormente segmentati per affrontare altri approcci, ad esempio i lavori richiesti di sostituzione/PaaS o refactoring secondario. Di seguito vengono descritte le competenze e i ruoli necessari per il rehosting, il refactoring o il refactoring secondario:

**Rehost:** Rehost richiede che i membri del team implementino le modifiche incentrate sull'infrastruttura. In genere si usa uno strumento come Azure Site Recovery per eseguire la migrazione di macchine virtuali o altre risorse in Azure. Questo lavoro si allinea perfettamente agli amministratori di Data Center o agli implementatori IT. Il team di migrazione del cloud è strutturato per offrire questo lavoro su larga scala. Si tratta dell'approccio più veloce per eseguire la migrazione delle risorse esistenti nella maggior parte degli scenari.

**Refactoring:** Il refactoring richiede che i membri del team modifichino il codice sorgente, modifichino l'architettura di un'applicazione o adotti nuovi servizi cloud. In genere, questo lavoro richiesto usa strumenti di sviluppo come Visual Studio e strumenti della pipeline di distribuzione come Azure DevOps per ridistribuire le applicazioni modernizzate in Azure. Questo lavoro si allineato bene ai ruoli di sviluppo dell'applicazione o ai ruoli di sviluppo della pipeline DevOps. Il team di innovazione del cloud è strutturato per la distribuzione di questo lavoro. Questo approccio può richiedere più tempo per sostituire le risorse esistenti con risorse cloud, tuttavia le app possono sfruttare le funzionalità native del cloud.

**Refactoring secondario:** Alcune applicazioni possono essere modernizzate con il refactoring secondario a livello di dati o di applicazione. Questo lavoro richiede che i membri del team distribuiscano i dati in piattaforme dati basate su cloud o che apportino modifiche secondarie alla configurazione dell'applicazione. Questo potrebbe richiedere un supporto limitato per gli esperti di dominio dati o sviluppo di applicazioni. Tuttavia, questo lavoro è simile a quello condotto dagli implementatori IT durante la distribuzione di app di terze parti. Questo lavoro si allinea facilmente al team di migrazione del cloud o al team di strategia del cloud. Sebbene questa operazione non sia più veloce di una migrazione di rehosting, è necessario meno tempo per eseguire il refactoring.

Durante la migrazione, le attività devono essere segmentate nei tre modi elencati sopra ed eseguite dal team appropriato nell'iterazione appropriata. Sebbene sia necessario diversificare il portfolio, assicurarsi che gli sforzi continuino a concentrarsi e separare.

## <a name="optimize-and-promote-process-changes"></a>Modifiche dei processi di ottimizzazione e promozione

Non sono necessarie altre modifiche durante i processi di ottimizzazione e promozione all'interno del lavoro richiesto per la migrazione.

## <a name="secure-and-manage-process-changes"></a>Proteggere e gestire le modifiche al processo

Non sono necessarie modifiche aggiuntive durante i processi di sicurezza e gestione all'interno del lavoro richiesto per la migrazione.

## <a name="next-steps"></a>Passaggi successivi

Tornare all'[elenco di controllo per l'espansione dell'ambito](./index.md) per verificare che il metodo di migrazione sia completamente allineato.

> [!div class="nextstepaction"]
> [Elenco di controllo per l'espansione dell'ambito](./index.md)
