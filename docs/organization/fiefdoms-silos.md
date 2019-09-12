---
title: Silos e feudi
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Comprendere gli antipattern di silos e feudi.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: organize
ms.custom: organize
ms.openlocfilehash: 4f9c1f13c6d6c0fe6cbb272d93f6cad2570e9a83
ms.sourcegitcommit: 5846ed4d0bf1b6440f5e87bc34ef31ec8b40b338
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2019
ms.locfileid: "70906349"
---
# <a name="organizational-antipatterns-silos-and-fiefdoms"></a>Antipattern aziendali: Silos e feudi

Il successo di qualsiasi modifica sostanziale alle procedure aziendali, alle impostazioni cultura o alle operazioni tecnologiche richiede un approccio mentale alla crescita. Alla base della mentalità di crescita si intende un'accettazione delle modifiche e la possibilità di condurre senza ambiguità.

Alcuni anti-patterns possono bloccare un mindset di crescita nelle organizzazioni che vogliono crescere e trasformare, tra cui la microgestione, il pensiero distorta e le procedure di esclusione. Molti di questi blocchi sono problemi personali che creano opportunità di crescita personale per tutti. Tuttavia, due antipattern comuni in essa richiedano più di una crescita o maturità singola: silos e feudi.

![Confronto tra team integri e antipattern aziendali](../_images/ready/fiefdom-and-silo.png)

Questi antipattern sono il risultato di modifiche organiche all'interno di diversi team, causando comportamenti aziendali non integri. Per risolvere la resistenza causata da ogni antipattern, è importante comprendere la causa principale di questa formazione.

## <a name="healthy-organic-it-teams"></a>Team IT integri, organici

È naturale creare una divisione del lavoro al suo interno. È integro per stabilire i team con competenze simili, processi condivisi, un obiettivo comune e una visione allineata. È anche naturale che i team abbiano una propria microcultura, norme condivise e prospettive.

I team IT integri si concentrano sulla collaborazione con altri team per promuovere il corretto completamento delle proprie mansioni. I team IT integri cercano di comprendere gli obiettivi aziendali progettati per supportare il loro contributo tecnologico. I dettagli e l'effetto fiscale potrebbero essere fuzzy, ma il contributo ai valori del team viene spesso riconosciuto all'interno del team.

Sebbene i team IT integri abbiano la passione per la tecnologia che supportano, sono aperti per la modifica e la volontà di provare nuovi elementi. Questi team sono spesso i collaboratori più primitivi e più affidabili per le attività [CCoE (cloud Center of Excellence)](./cloud-center-excellence.md) . Il loro contributo dovrebbe essere fortemente consigliato.

### <a name="natural-resistance-to-change"></a>Resistenza naturale a modifiche

In alcuni casi, le microcolture nei team IT integri potrebbero reagire in modo non corretto alle decisioni esecutive o dall'alto verso il basso per apportare modifiche. Questa reazione è naturale, perché i collettivi di esseri umani con normative condivise spesso collaborano per superare le minacce esterne.

Le modifiche che interessano i processi quotidiani del team, il senso di sicurezza o l'autonomia possono essere considerate come un rischio per il collettivo. I segni di resistenza sono spesso un indicatore tempestivo che i membri del team non sono in grado di far parte del processo decisionale.

Quando architetti del cloud e altri leader investono nell'abolizione dei bias personali e la guida per l'inclusione dei team IT esistenti, è probabile che questa resistenza si ridurrà rapidamente e si dissolva nel tempo. Uno strumento disponibile per architetti e responsabili del cloud per creare un processo decisionale inclusivo è la formazione di un CCoE.

### <a name="healthy-friction"></a>Attrito integro

È facile confondere la resistenza con attrito. I team IT esistenti possono essere informati sugli errori precedenti, sui rischi tangibili, sulle informazioni di carattere tribale sulle soluzioni e sui debiti tecnici non documentati. Sfortunatamente, anche i team IT più sani possono rientrare nella trappola di descrivere questi punti dati importanti come parte di una soluzione tecnica specifica, che non deve essere modificata. Questo approccio alla comunicazione maschera le conoscenze dei team, creando una percezione della resistenza.

Fornire a questi team un meccanismo per la comunicazione con la terminologia in futuro consente di aggiungere punti dati, identificare Gap e creare un attrito integro per le soluzioni proposte. Tale attrito può comportare la levigatura dei bordi approssimativi sulle soluzioni e l'unità di valori a lungo termine. La semplice modifica della conversazione può creare chiarezza su argomenti complessi e generare energia per offrire soluzioni più efficaci.

Le linee guida per la [definizione dei criteri aziendali](../governance/corporate-policy.md) mirano a facilitare le conversazioni basate sul rischio con le parti interessate dell'azienda. Tuttavia, questo stesso modello può essere usato per semplificare le conversazioni con i team che vengono percepiti come resistenti al cloud. Quando la percezione della resistenza è diffusa, potrebbe essere opportuno includere procedure di risoluzione della resistenza nella carta per un team di governance del [cloud](./cloud-governance.md).

## <a name="antipatterns"></a>Antipatterns

La crescita organica e reattiva al suo interno, che consente di creare team IT integri, può anche causare antipattern che bloccano la trasformazione e l'adozione del cloud. I silo e feudi di IT sono diversi dalle microcolture naturali all'interno di team IT integri. In entrambi i modelli, lo stato attivo del team tende a essere indirizzato verso la protezione del "Turf". Quando i membri del team hanno la possibilità di gestire le operazioni di modifica e miglioramento, investono più tempo ed energia per bloccare la modifica rispetto alla ricerca di una soluzione positiva.

Come indicato in precedenza, i team IT integri possono creare resistenza naturale e attrito positivo. Silos e feudi rappresentano un problema diverso. Non è presente alcun indicatore principale documentato per entrambi gli antipattern. Questi antipattern tendono a essere identificati dopo i mesi di [cloud Center of Excellence e del team di](./cloud-center-excellence.md) governance del [cloud](./cloud-governance.md) . Sono state individuate come il risultato della resistenza continua.

Anche nelle impostazioni cultura tossiche, le attività dei CCoE e del team di governance del cloud dovrebbero aiutare a promuovere la crescita culturale e lo stato tecnico. Dopo i mesi di lavoro, è possibile che alcuni team non mostrino alcun segno di comportamenti inclusivi e siano saldi nella loro resistenza al cambiamento. È probabile che questi team funzionino in uno dei modelli antipattern seguenti: silos e feudi. Sebbene questi modelli abbiano sintomi simili, la causa principale e gli approcci per l'indirizzamento della resistenza sono radicalmente diversi tra loro.

## <a name="it-silos"></a>Silo IT

I membri del team in un silo IT possono definire autonomamente il loro allineamento a un numero ridotto di fornitori IT o un'area di specializzazione tecnica. Tuttavia, non confondere i silo con feudi IT. I silo IT tendono a essere basati su comfort e passione e sono in genere più facili da superare rispetto ai motivi basati su paure dietro feudi.

Questo antipattern spesso emerge da una passione comune per una soluzione specifica. Il silo IT viene quindi rinforzato dalle competenze avanzate del team in seguito all'investimento nella soluzione specifica. Questa competenza superiore può essere un acceleratore per le attività di adozione del cloud se la resistenza alla modifica può essere superata. Può anche diventare un blocco principale se i silo sono suddivisi o se i membri del team non possono valutare accuratamente le opzioni. Fortunatamente, i silo IT possono spesso essere superati senza apportare modifiche significative al grafico dell'organizzazione.

### <a name="addressing-resistance-from-it-silos"></a>Indirizzamento della resistenza dai silo IT

I silo IT possono essere risolti tramite gli approcci seguenti. L'approccio migliore dipende dalla causa principale della resistenza.

**Creazione di team virtuali:** La sezione [conformità organizzativa](./index.md) del Framework di adozione del cloud descrive una struttura a più livelli per l'integrazione e la definizione di quattro team virtuali (v-Teams). Un vantaggio di questa struttura è la visibilità e l'inclusione tra organizzazioni. L'introduzione [di un cloud Center of Excellence](./cloud-center-excellence.md) consente di creare un team di aspirazioni di alto profilo a cui vorranno partecipare i tecnici principali. In questo modo è possibile creare nuovi allineamenti tra soluzioni che non sono vincolati da vincoli di organigramma e che consentano di includere i tecnici principali che sono stati protetti da silo IT.

L'introduzione di un [team di strategia cloud](./cloud-strategy.md) creerà visibilità immediata dei contributi it riguardanti le attività di adozione del cloud. Quando i silo si combattono per la separazione, questa visibilità può aiutare a motivare i responsabili IT e aziendali a supportare correttamente questi membri del team resistenti. Questo processo rappresenta un percorso rapido per il coinvolgimento e il supporto degli stakeholder.

**Prendere in considerazione la sperimentazione e l'esposizione:** È probabile che i membri del team in un silo IT siano stati limitati per un certo periodo di tempo. L'indicizzazione di una traccia è il primo passo per affrontare la resistenza.

La sperimentazione e l'esposizione sono strumenti avanzati per suddividere le barriere nei silo. I membri del team potrebbero essere resistenti alle soluzioni concorrenti, quindi non è consigliabile inserirli in un esperimento che compete con la soluzione esistente. Tuttavia, nell'ambito di un primo test del carico di lavoro del cloud, l'organizzazione deve implementare soluzioni in competizione. Il team di silo deve essere invitato a partecipare come origine di input e di revisione, ma non come decisore. Questo dovrebbe essere chiaramente comunicato al team, insieme a un impegno per coinvolgere il team in modo più approfondito come decisore prima di procedere alle soluzioni di produzione.

Durante la revisione della soluzione concorrente, usare le procedure descritte in definire i [criteri aziendali](../governance/corporate-policy.md) per documentare i rischi tangibili dell'esperimento e stabilire i criteri che consentono al team di silo di diventare più agevole con lo stato futuro. Questo consente di esporre il team a nuove soluzioni e rafforzare la soluzione futura.

**Essere "delimitati":** I team che guidano l'adozione del cloud trovano un semplice push dei limiti grazie all'esplorazione di nuove soluzioni native cloud. Si tratta di una metà dell'approccio alla rimozione dei limiti. Tuttavia, il pensiero può rinforzare ulteriormente i silo IT. Il push di modifiche troppo rapidamente e senza rispettare le impostazioni cultura esistenti può creare attriti non integri e causare una resistenza naturale.

Quando i silos iniziano a resistere, è importante avere un limite per le proprie soluzioni. Tenere presente una semplice verità: il cloud nativo non è sempre la soluzione migliore. Prendere in considerazione soluzioni ibride che potrebbero offrire l'opportunità di estendere gli investimenti esistenti del silo IT in futuro.

Prendere in considerazione anche le versioni basate su cloud della soluzione che il team silo IT USA ora. Sperimentare queste soluzioni ed esporsi al punto di vista di coloro che vivono nel silo IT. Come minimo, si otterrà una prospettiva nuova. In molte situazioni, è possibile che si guadagni un numero sufficiente di il silo IT per ridurre la resistenza.

**Investire nella formazione:** Molti utenti che vivono in un silo IT sono diventati appassionati della soluzione corrente in seguito all'espansione della propria formazione. Gli investimenti nella formazione di questi team sono raramente inseriti. Consente di allocare tempo a questi utenti per partecipare a lezioni di apprendimento automatico, classi o persino conferenze per suddividere l'attenzione quotidiana sulla soluzione corrente.

Affinché la formazione sia un investimento, è necessario che alcuni ritornino come risultato della spesa. In Exchange per l'investimento, il team può dimostrare la soluzione proposta al resto dei team che interessano l'adozione del cloud. Potrebbero inoltre fornire la documentazione dei rischi tangibili, degli approcci alla gestione dei rischi e dei criteri desiderati nell'adozione della soluzione proposta. Ognuno di essi attiverà questi team nella soluzione e consentirà di sfruttare le proprie conoscenze di base.

**Trasformare i blocchi stradali in urti di velocità:** Il silo può rallentare o arrestare qualsiasi trasformazione. La sperimentazione e l'iterazione troveranno un modo, ma solo se il progetto continua a essere spostato. Concentrarsi sulla trasformazione dei blocchi stradali in una semplice velocità di urto. Definire i criteri che tutti possono essere temporaneamente a disposizione in Exchange per la progressione continua.

Se, ad esempio, la sicurezza IT costituisce un ostacolo perché la soluzione di sicurezza non è in grado di monitorare i compromessi dei dati protetti nel cloud, definire i criteri di classificazione dei dati. Impedisci la distribuzione di dati classificati nel cloud fino a quando non viene trovata una soluzione consentita. Invita la sicurezza IT nella sperimentazione con soluzioni ibride o native del cloud per monitorare i dati protetti.

Se il team di rete opera come Silo, identificare i carichi di lavoro indipendenti e non hanno dipendenze di rete. In parallelo, sperimenta, espone e istruisce il team di rete lavorando su soluzioni ibride o alternative.

**Essere pazienti ed essere inclusivi:** Si sta tentando di procedere senza supportare un silo IT. Questa decisione, tuttavia, provocherà le rotture e i blocchi stradali. La modifica delle menti nei membri del silo IT può richiedere tempo. Essere paziente della resistenza naturale, ovvero convertirlo in valore. Essere inclusivi e invitare un attrito integro per migliorare la soluzione futura.

**Mai gareggiare:** Il silo IT esiste per un motivo. Viene mantenuto per un motivo. Si è verificato un investimento nella gestione della soluzione di cui i membri del team sono appassionati. La competizione diretta con la soluzione o il silo IT si distrae dall'obiettivo reale di ottenere risultati aziendali. Questo Trap ha bloccato molti progetti di trasformazione.

Rimanere concentrati sull'obiettivo, anziché su un singolo componente dell'obiettivo. Contribuire ad accentuare gli aspetti positivi della soluzione del silo IT e aiutare i membri del team a prendere decisioni sagge sulle soluzioni migliori per il futuro. Non insultare né peggiorare la soluzione corrente, perché sarebbe controproducente.

**Partner con l'azienda:** Se il silo IT non blocca i risultati aziendali, perché si è interessati? Non esiste una soluzione perfetta o un fornitore IT perfetto. La competizione esiste per un motivo; Ognuno presenta vantaggi.

Accetta la diversità e Includi l'azienda grazie al supporto e all'allineamento a un potente [team di strategia cloud](./cloud-strategy.md). Quando un silo IT supporta una soluzione che blocca i risultati aziendali, sarà più semplice comunicare questo ostacolo senza il rumore dei battibecchi tecnici. Il supporto di silo IT non bloccanti mostrerà la possibilità di collaborare ai risultati aziendali desiderati. Questi sforzi otterranno maggiore rispetto e un maggiore supporto da parte dell'azienda quando un silo IT presenta un blocco legittimo.

## <a name="it-fiefdoms"></a>Feudi

I membri del team in un feudo IT possono definire autonomamente il loro allineamento per un processo o un'area di responsabilità specifica. Il team opera in base a un presupposto che l'influenza esterna sulla sua area di responsabilità provocherà problemi. Feudi tende a essere un antipattern basato su paura, che richiede un notevole supporto per la leadership.

Feudi sono particolarmente comuni nelle organizzazioni che hanno sperimentato il ridimensionamento IT, una frequente turbolenza nel personale IT o una scarsa leadership IT. Quando l'azienda lo considera esclusivamente come un centro di costo, è molto più probabile che si verifichino feudi.

In genere, feudi sono il risultato di un gestore delle linee che teme la perdita del team e della base di energia associata. Questi leader hanno spesso un'idea di dovere per il proprio team e devono proteggere le proprie subordinate da conseguenze negative. Le frasi come "proteggere il team dal cambiamento" e "proteggere il team dalle problematiche del processo" possono essere indicatori di un responsabile troppo sorvegliato, che potrebbe richiedere un maggiore supporto da parte della leadership.

### <a name="addressing-resistance-from-it-fiefdoms"></a>Indirizzamento della resistenza dal feudi IT

Feudi è in grado di dimostrare una certa crescita seguendo gli approcci per [risolvere la resistenza del silo it](#addressing-resistance-from-it-silos). Prima di provare a risolvere la resistenza da un feudo IT, è consigliabile considerare prima di tutto il team come un silo IT. Se questi tipi di approcci non riescono a produrre modifiche significative, il team resistente potrebbe essere in sofferenza da un antipattern feudale IT. La causa principale di questo feudi è un po' più complessa da affrontare, perché tale resistenza tende a derivare da Direct Line Manager (o da un leader superiore al grafico dell'organizzazione). I problemi che sono basati su silo sono in genere più semplici da superare.

Quando la resistenza continua da feudi blocca il lavoro di adozione del cloud, potrebbe essere opportuno eseguire un tentativo combinato di valutare la situazione con i responsabili IT esistenti. I responsabili IT devono considerare attentamente le informazioni dettagliate del [team di strategia cloud](./cloud-strategy.md), il [centro cloud di eccellenza](./cloud-center-excellence.md)e il team di governance del [cloud](./cloud-governance.md) prima di prendere decisioni.

> [!NOTE]
> I responsabili IT non dovrebbero mai apportare modifiche al grafico dell'organizzazione. Devono inoltre convalidare e analizzare il feedback da ognuno dei team di supporto. Tuttavia, le attività Transformative come l'adozione del cloud tendono a ingrandire i problemi sottostanti che sono diventati inosservati o non indirizzati molto prima di questa operazione. Quando feudi impedisce la riuscita della società, le modifiche alla leadership sono probabilmente una necessità.
>
> Fortunatamente, la rimozione del leader di un feudo non termina spesso con la terminazione. Questi forti leader appassionati possono spesso passare a un ruolo di gestione dopo un breve periodo di riflessione. Con il supporto corretto, questo cambiamento può essere integro per il leader del feudo e per il team corrente.

> [!CAUTION]
> Per i responsabili del feudi IT, la protezione del team dal rischio è un valore di leadership chiaro. Tuttavia, esiste una linea sottile tra protezione e isolamento. Quando il team non ha partecipato alla Guida alle modifiche, può avere conseguenze psicologiche e professionali sul team. Il desiderio di resistere alle modifiche potrebbe essere forte, soprattutto durante i periodi di modifica visibile.
>
> Il responsabile di qualsiasi team isolato può dimostrare meglio un mindset di crescita sperimentando le linee guida associate ai team IT integri nelle sezioni precedenti. La partecipazione attiva e ottimistica alle attività di governance e CCoE può condurre alla crescita personale. I responsabili dei feudi IT sono ideali per modificare le mentalità soffocanti e aiutare il team a sviluppare nuove idee.

Feudi può essere un segno di problemi di leadership sistemici. Per superare un feudo IT, i responsabili IT hanno la possibilità di apportare modifiche a operazioni, responsabilità e occasionalmente anche alle persone che forniscono la gestione delle linee di team specifici. Quando tali modifiche sono necessarie, è consigliabile affrontare tali modifiche con punti dati chiari e difendibili.

L'allineamento con le parti interessate aziendali, le motivazioni aziendali e i risultati aziendali potrebbe essere necessario per gestire le modifiche necessarie. La collaborazione con il team di [strategia cloud](./cloud-strategy.md), il [centro cloud di eccellenza](./cloud-center-excellence.md)e il [team di governance cloud](./cloud-governance.md) possono fornire i punti dati necessari per una posizione difendibile. Quando necessario, questi team devono essere impegnati in un'escalation dei gruppi per risolvere i problemi che non possono essere risolti solo con la leadership IT.

## <a name="next-steps"></a>Passaggi successivi

L'abpromettere gli antipattern aziendali è un impegno del team. Per agire su queste linee guida, esaminare l'introduzione alla conformità organizzativa per identificare le strutture e i partecipanti appropriati del team:

> [!div class="nextstepaction"]
> [Identificare le strutture e i partecipanti appropriati del team](./index.md)
