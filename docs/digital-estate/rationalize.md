---
title: Razionalizzare il digital estate
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Valutare gli asset digitali per determinare il modo migliore per ospitarli nel cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 12/10/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: plan
ms.custom: governance
ms.openlocfilehash: fee983ba2379bb84d56f23139bba987a56e5c54d
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73564699"
---
# <a name="rationalize-the-digital-estate"></a>Razionalizzare il digital estate

La razionalizzazione del cloud è il processo di valutazione delle risorse per determinare l'approccio migliore per l’hosting delle risorse stesse nel cloud. Dopo aver determinato un [approccio](./approach.md) e aver aggregato un [inventario](./inventory.md), è possibile iniziare la razionalizzazione del cloud. La [razionalizzazione cloud](./rationalize.md) illustra le opzioni di razionalizzazione più comuni.

## <a name="traditional-view-of-rationalization"></a>Visione tradizionale della razionalizzazione

È facile comprendere la razionalizzazione quando si Visualizza il processo tradizionale di razionalizzazione come un albero delle decisioni complesso. Ogni asset nell'area digitale è alimentato da un processo che restituisce una delle cinque risposte (le cinque RS). Per piccoli estate, questo processo funziona bene. Per le aziende di grandi dimensioni, non è efficiente e può causare ritardi significativi. Cerchiamo di capirne il motivo esaminando il processo. In seguito presenteremo un modello più efficiente.

**Inventario:** Per completare una razionalizzazione completa con i modelli tradizionali, è necessario un inventario completo delle risorse, tra cui applicazioni, software, hardware, sistemi operativi e metriche delle prestazioni di sistema.

**Analisi quantitativa:** Nell'albero delle decisioni le domande quantitative determinano il primo livello di decisione. Di seguito sono riportate alcune domande comuni: l'asset attualmente in uso? In questo caso, è ottimizzata e valutata in modo corretto? Quali dipendenze esistono tra le risorse? Queste domande sono fondamentali per la classificazione dell'inventario.

**Analisi qualitativa:** Il set di decisioni successivo richiede l'intelligenza umana sotto forma di analisi qualitativa. Spesso le domande che si trovano qui sono univoche per la soluzione e possono ricevere una risposta solo dagli stakeholder aziendali e dagli utenti esperti. Queste decisioni ritardano in genere il processo, rallentando considerevolmente le attività. Questa analisi USA in genere da 40 a 80 ETP ore per applicazione.

Per indicazioni sulla creazione di un elenco di domande relative all'analisi qualitativa, vedere [approcci alla pianificazione delle proprietà digitali](./approach.md).

**Decisione di razionalizzazione:** Nelle mani di un team di razionalizzazione esperto, i dati qualitativi e quantitativi creano decisioni chiare. Sfortunatamente, i team con un elevato livello di esperienza sulla razionalizzazione sono costosi e il training richiede mesi.

## <a name="rationalization-at-enterprise-scale"></a>Razionalizzazione su scala aziendale

Se questa operazione richiede molto tempo ed è scoraggiante per una macchina virtuale di 50 VM, si supponga di voler gestire la trasformazione aziendale in un ambiente con migliaia di macchine virtuali e centinaia di applicazioni. Gli sforzi umani necessari possono superare facilmente 1.500 ETP e nove mesi di pianificazione.

Sebbene la razionalizzazione completa sia lo stato finale e una direzione ideale per spostarsi, raramente produce un ROI elevato (ritorno sugli investimenti) rispetto al tempo e all'energia richiesti.

Quando la razionalizzazione è essenziale per le decisioni finanziarie, vale la pena considerare un'organizzazione di servizi professionali specializzata nella razionalizzazione del cloud per accelerare il processo. Anche in questo caso, la razionalizzazione completa può essere un'attività costosa e dispendiosa in termini di tempo che ritarda la trasformazione o i risultati aziendali.

Nella parte restante di questo articolo viene descritto un approccio alternativo, noto come razionalizzazione incrementale.

## <a name="incremental-rationalization"></a>Razionalizzazione incrementale

La razionalizzazione completa di un grande patrimonio digitale è soggetta a rischi e può subire ritardi a causa della complessità. Il presupposto alla base dell'approccio incrementale è che le decisioni ritardate sfalsano il carico dell'azienda per ridurre il rischio di blocchi stradali. Nel corso del tempo, questo approccio crea un modello organico per lo sviluppo di processi ed esperienze necessari per prendere decisioni di razionalizzazione qualificate in modo più efficiente.

### <a name="inventory-reduce-discovery-data-points"></a>Inventario: ridurre i punti dati di individuazione

Poche organizzazioni investono il tempo, l'energia e le spese per mantenere un inventario accurato e in tempo reale dell'intera proprietà digitale. La perdita, il furto, i cicli di aggiornamento e l'onboarding dei dipendenti spesso giustificano il rilevamento dettagliato delle risorse per i dispositivi degli utenti finali. Tuttavia, il ROI della gestione di un inventario accurato di server e applicazioni in un Data Center locale tradizionale è spesso basso. La maggior parte delle organizzazioni IT ha problemi più pressanti da risolvere rispetto alla verifica dell’uso delle risorse fisse di un data center.

In una trasformazione cloud, l'inventario è correlato direttamente ai costi operativi. Per una pianificazione corretta sono necessari dati di inventario precisi. Sfortunatamente, le opzioni di analisi ambientale correnti possono ritardare le decisioni di settimane o mesi. Fortunatamente, alcuni trucchi possono accelerare la raccolta dei dati.

L'analisi basata sugli agenti è la causa di ritardo più citata. I dati affidabili necessari per una razionalizzazione tradizionale possono spesso essere raccolti solo con un agente in esecuzione in ogni asset. Questa dipendenza dagli agenti spesso rallenta lo stato di avanzamento, perché può richiedere feedback da funzioni di sicurezza, operazioni e amministrazione.

In un processo di razionalizzazione incrementale, è possibile utilizzare una soluzione senza agente per un’individuazione preliminare, in modo da accelerare le prime decisioni. A seconda del livello di complessità dell'ambiente, potrebbe essere ancora necessaria una soluzione basata su agenti. Tuttavia, può essere rimosso dal percorso critico alla modifica aziendale.

### <a name="quantitative-analysis-streamline-decisions"></a>Analisi quantitativa: semplificare le decisioni

Indipendentemente dall'approccio all'individuazione dell'inventario, l'analisi quantitativa può condurre a decisioni e presupposti iniziali. Ciò vale soprattutto quando si tenta di identificare il primo carico di lavoro o quando l'obiettivo della razionalizzazione è un confronto dei costi di alto livello. In un processo di razionalizzazione incrementale, il team di strategia cloud e i team di adozione del cloud limitano i [cinque RS della razionalizzazione](./5-rs-of-rationalization.md) a due decisioni concise e applicano solo questi fattori quantitativi. In questo modo si semplifica l'analisi e si riduce la quantità di dati iniziali necessaria per l'unità di modifica.

Se, ad esempio, un'organizzazione si trova nel mezzo di una migrazione IaaS al cloud, è possibile presupporre che la maggior parte dei carichi di lavoro verrà ritirata o riallocata.

### <a name="qualitative-analysis-temporary-assumptions"></a>Analisi qualitativa: presupposti temporanei

Grazie alla riduzione del numero di potenziali risultati, è più semplice raggiungere una decisione iniziale sullo stato futuro di un asset. Quando si riducono le opzioni, si riduce anche il numero di domande poste dall'azienda in questa fase iniziale.

Se, ad esempio, le opzioni sono limitate alla riallocazione o alla disattivazione, l'azienda deve rispondere a una sola domanda durante la razionalizzazione iniziale, ovvero se ritirare l'asset.

"Analysis suggerisce che nessun utente sta usando attivamente questo asset. Si tratta di un aspetto accurato, Una domanda binaria di questo tipo è in genere molto più semplice da eseguire tramite analisi qualitative.

Questo approccio semplificato genera linee di base, piani finanziari, strategia e direzione. Nelle attività successive ogni asset passa attraverso un'ulteriore razionalizzazione e analisi qualitativa per valutare le altre opzioni. Tutte le ipotesi apportate in questa razionalizzazione iniziale sono testate prima

## <a name="challenge-assumptions"></a>Presupposti per la sfida

Il risultato della sezione precedente è una razionalizzazione approssimativa che è piena di presupposti. A questo punto è tempo di verificare alcuni di questi presupposti.

### <a name="retire-assets"></a>Ritira asset

In un ambiente locale tradizionale, che ospita risorse di piccole dimensioni e non usate, raramente causa un notevole impatto sui costi annuali. Con poche eccezioni, il lavoro richiesto per l'analisi e il ritiro dell'asset effettivo comporta un notevole risparmio sui costi derivanti dall'eliminazione e dalla rimozione di tali asset.

Tuttavia, quando si passa a un modello di contabilità cloud, la disattivazione degli asset può produrre risparmi significativi nei costi operativi annuali e nelle attività di migrazione iniziali.

Non è insolito per le organizzazioni ritirare il 20% o più delle proprie proprietà digitali dopo aver completato un'analisi quantitativa. Prima di decidere su tale azione, è consigliabile eseguire un'analisi qualitativa aggiuntiva. Dopo la conferma, il ritiro di tali asset può produrre la prima vittoria del ROI nella migrazione cloud. In molti casi, si tratta di uno dei principali fattori di risparmio sui costi. Di conseguenza, è consigliabile che il team di strategia cloud sorvegli la convalida e il ritiro delle risorse, in parallelo con la fase di compilazione del processo di migrazione, per consentire una vittoria finanziaria anticipata.

### <a name="program-adjustments"></a>Regolazioni del programma

Raramente una società intraprende una sola trasformazione. La scelta tra riduzione dei costi, crescita del mercato e nuovi flussi di ricavi raramente è una decisione binaria. Di conseguenza, è consigliabile che il team di strategia cloud collabori con esso per identificare le risorse sulle attività di trasformazione parallele che esulano dall'ambito del percorso di trasformazione principale.

Nell'esempio di migrazione di IaaS fornito in questo articolo:

- Richiedere al team di DevOps di identificare gli asset che fanno già parte di un'automazione della distribuzione e di rimuovere tali asset dal piano di migrazione principale.

- Chiedere ai team Dati e R&S di identificare le risorse che favoriscono nuovi flussi di ricavi e rimuoverle dal piano di migrazione principale.

Questa analisi qualitativa incentrata sul programma può essere eseguita rapidamente e crea l'allineamento tra più backlog di migrazione.

Per un periodo di tempo, potrebbe essere necessario prendere in considerazione alcuni asset come riallocare le risorse. Dopo la migrazione iniziale è possibile la fase in una razionalizzazione successiva.

## <a name="select-the-first-workload"></a>Selezionare il primo carico di lavoro

L’implementazione del primo carico di lavoro è fondamentale per le verifiche e l’apprendimento. È la prima opportunità per dimostrare e creare un mindset di crescita.

### <a name="business-criteria"></a>Criteri aziendali

Per garantire la trasparenza aziendale, identificare un carico di lavoro supportato da un membro della business unit del team di strategia cloud. È preferibile sceglierne una in cui il team dispone di un palo e motivazioni forti per passare al cloud.

### <a name="technical-criteria"></a>Criteri tecnici

Selezionare un carico di lavoro con dipendenze minime e che possa essere spostato come piccolo gruppo di risorse. Si consiglia di selezionare un carico di lavoro con un percorso di test definito per semplificare la convalida.

Il primo carico di lavoro è spesso distribuito in un ambiente sperimentale senza capacità operativa o di governance. È importante selezionare un carico di lavoro che non interagisce con i dati protetti.

### <a name="qualitative-analysis"></a>Analisi qualitativa

I team di adozione del cloud e il team di strategia cloud possono collaborare per analizzare questo carico di lavoro ridotto. Questa collaborazione crea un'opportunità controllata per creare e testare criteri di analisi qualitativi. La popolazione più piccola crea un'opportunità per esaminare gli utenti interessati e per completare un'analisi qualitativa dettagliata in una settimana o meno. Per i fattori di analisi qualitativi comuni, vedere la destinazione di razionalizzazione specifica in [5 RS di razionalizzazione](./5-rs-of-rationalization.md).

### <a name="migration"></a>Migrazione

Parallelamente alla razionalizzazione continua, il team di adozione del cloud può iniziare a migrare il carico di lavoro ridotto per espandere l'apprendimento nelle aree principali seguenti:

- Rafforzare le competenze con la piattaforma del provider di servizi cloud.
- Definire i servizi principali (e gli standard di Azure) necessari per adattarsi alla visione a lungo termine.
- Comprendere meglio il modo in cui potrebbe essere necessario modificare le operazioni in un secondo momento nella trasformazione.
- Comprendere i rischi inerenti per le attività e la tolleranza per tali rischi.
- Stabilire una baseline o un prodotto minimo funzionante (MVP) per la governance basata sulla tolleranza del rischio aziendale.

## <a name="release-planning"></a>Pianificazione del rilascio

Mentre il team di adozione del cloud sta eseguendo la migrazione o l'implementazione del primo carico di lavoro, il team di strategia cloud può iniziare a classificare in ordine di priorità le applicazioni e i carichi di lavoro rimanenti.

### <a name="power-of-10"></a>Potenza di 10

L'approccio tradizionale alla razionalizzazione tenta di soddisfare tutte le esigenze prevedibili. Per fortuna, spesso non è necessario un piano per tutte le applicazioni per avviare un processo di trasformazione. In un modello incrementale, la potenza di 10 fornisce un valido punto di partenza. In questo modello, il team di strategia cloud seleziona le prime 10 applicazioni da migrare. Questi dieci carichi di dieci lavoro devono contenere una combinazione di carichi di lavoro semplici e complessi.

### <a name="build-the-first-backlogs"></a>Compila i primi backlog

I team di adozione del cloud e il team di strategia cloud possono collaborare all'analisi qualitativa per i primi 10 carichi di lavoro. Questo sforzo crea il primo backlog di migrazione con priorità e il primo backlog di rilascio con priorità. Questo metodo consente ai team di eseguire un'iterazione sull'approccio e fornisce tempo sufficiente per creare un processo adeguato per l'analisi qualitativa.

### <a name="mature-the-process"></a>Maturare il processo

Dopo che i due team hanno accettato i criteri di analisi qualitativa, la valutazione può diventare un'attività all'interno di ogni iterazione. Il raggiungimento del consenso sui criteri di valutazione richiede in genere da due a tre versioni.

Dopo che la valutazione è stata spostata nel processo di esecuzione incrementale della migrazione, il team di adozione del cloud può eseguire un'iterazione più veloce su valutazione e architettura. In questa fase, il team di strategia cloud viene anche sottratto, riducendo al tempo stesso lo svuotamento. In questo modo, il team di strategia cloud è in grado di concentrarsi sulla priorità delle applicazioni che non sono ancora in una versione specifica, garantendo un allineamento rigoroso con le mutevoli condizioni del mercato.

Non tutte le applicazioni prioritarie possono essere pronte per la migrazione. È probabile che la sequenziazione cambi quando il team esegue un'analisi qualitativa più approfondita e individua gli eventi aziendali e le dipendenze che potrebbero richiedere la riassegnazione della priorità del backlog. Alcune versioni potrebbero raggruppare un numero ridotto di carichi di lavoro. Altri potrebbero contenere solo un singolo carico di lavoro.

È probabile che il team di adozione del cloud esegua le iterazioni che non producono una migrazione completa del carico di lavoro. Minori sono il carico di lavoro e le dipendenze, più è probabile che un carico di lavoro rientri in un’unico sprint o iterazione. Per questo motivo, è consigliabile che le prime applicazioni nel backlog di versione siano ridotte e contengano alcune dipendenze esterne.

## <a name="end-state"></a>Stato finale

Nel corso del tempo, la combinazione del team di adozione del cloud e del team di strategia cloud completerà una razionalizzazione completa dell'inventario. Tuttavia, questo approccio incrementale consente ai team di ottenere sempre più velocemente il processo di razionalizzazione. Consente inoltre al percorso di trasformazione di ottenere prima i risultati aziendali tangibili, senza la necessità di un'analisi iniziale.

In alcuni casi, il modello finanziario potrebbe essere troppo stretto per prendere una decisione senza razionalizzazione aggiuntiva. In questi casi, potrebbe essere necessario un approccio più tradizionale alla razionalizzazione.

## <a name="next-steps"></a>Passaggi successivi

L'output di un lavoro di razionalizzazione è un backlog con priorità di tutti gli asset interessati dalla trasformazione scelta. Questo backlog sarà la base per i modelli di determinazione dei costi dei servizi cloud.

> [!div class="nextstepaction"]
> [Allineare i modelli di costo con il digital estate](./calculate.md)
