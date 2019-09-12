---
title: Creare una motivazione aziendale per la migrazione al cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Considerazioni per la creazione di una motivazione aziendale per la migrazione al cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 12/10/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: strategy
ms.custom: governance
ms.openlocfilehash: 1b91af129210e1eb4cfe108b6f73e88ec25cf829
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70825120"
---
# <a name="build-a-business-justification-for-cloud-migration"></a>Creare una motivazione aziendale per la migrazione al cloud

Le migrazioni cloud possono generare un ritorno sugli investimenti (ROI) anticipato proveniente da attività di trasformazione cloud. Tuttavia, lo sviluppo di una chiara motivazione aziendale con i costi tangibili e i relativi ritorni può essere un processo complesso. Questo articolo consente di valutare i dati necessari per creare un modello finanziario che si allinea ai risultati della migrazione cloud. Innanzitutto, sfatiamo alcuni miti sulla migrazione cloud, in modo che l'organizzazione possa evitare alcuni errori comuni.

## <a name="dispelling-cloud-migration-myths"></a>Miti sulla migrazione cloud

**Mito: il cloud è sempre più economico.** Si ritiene comunemente che la gestione di un Data Center nel cloud sia sempre più economica rispetto alla gestione di un Data Center locale. Sebbene questo presupposto possa essere in genere vero, non è sempre il caso. A volte i costi operativi del cloud sono maggiori. Questi costi più elevati sono spesso causati da una governance dei costi scadente, da architetture di sistema non allineate, dalla duplicazione dei processi, da configurazioni di sistema atipiche o da costi di personale maggiori. Fortunatamente, è possibile mitigare molti di questi problemi per creare il ROI iniziale. Seguendo le istruzioni riportate in [creazione della motivazione aziendale](#building-the-business-justification) , è possibile rilevare ed evitare questi problemi di allineamento. La digitazione degli altri miti descritti qui può essere utile.

**Mito: bisogna passare completamente al cloud.** Infatti, alcuni driver aziendali potrebbero consentire di scegliere una soluzione ibrida. Prima di finalizzare un modello aziendale, è possibile completare un'analisi quantitativa per la prima volta, come descritto negli articoli relativi alle [Proprietà digitali](../digital-estate/5-rs-of-rationalization.md). Per ulteriori informazioni sui singoli driver quantitativi associati alla razionalizzazione, vedere la pagina relativa [alla razionalizzazione di 5](../digital-estate/5-rs-of-rationalization.md). Entrambi gli approcci usano i dati di inventario facilmente ottenuti e una breve analisi quantitativa per identificare i carichi di lavoro o applicazioni che potrebbero causare un aumento dei costi nel cloud. Questi approcci possono anche identificare le dipendenze o i modelli di traffico che richiedono una soluzione ibrida.

**Mito: il mirroring dell’ambiente locale permette di ridurre i costi del cloud.** Durante la pianificazione delle proprietà digitali, per le aziende è necessario rilevare una capacità inutilizzata superiore al 50% dell'ambiente di cui è stato effettuato il provisioning. Se le risorse vengono sottoposte a provisioning nel cloud per soddisfare il provisioning corrente, è difficile realizzare risparmi sui costi. Valutare la possibilità di ridurre le dimensioni degli asset distribuiti per allinearli con i modelli di utilizzo anziché con i modelli di provisioning.

**Mito: I costi del server spingono i casi aziendali per la migrazione nel cloud.** A volte questa ipotesi è vera. Per alcune aziende, è importante ridurre le spese in conto capitale costanti relative ai server. Ma dipende da diversi fattori. Le aziende con un ciclo di aggiornamento hardware da cinque anni a otto anni sono improbabile che rivedano i ritorni rapidi sulla migrazione cloud. Le aziende con cicli di aggiornamento standardizzati o imposti possano raggiungere rapidamente un punto di pareggio. In entrambi i casi, altre spese potrebbero essere i trigger finanziari che giustificano la migrazione. Di seguito sono riportati alcuni esempi di costi comunemente trascurati quando le aziende accettano una visualizzazione dei costi solo per server o solo VM:

- I costi del software per la virtualizzazione, i server e il middleware possono essere estesi. I provider di servizi cloud eliminano alcuni di questi costi. Due esempi di un provider di servizi cloud che riducono i costi di virtualizzazione sono i programmi [vantaggio Azure Hybrid](https://azure.microsoft.com/pricing/hybrid-benefit/#services) e [prenotazioni di Azure](https://azure.microsoft.com/reservations) .
- Le perdite aziendali dovute a interruzioni possono superare rapidamente i costi hardware o software. Se il Data Center corrente è instabile, collaborare con l'azienda per quantificare l'effetto delle interruzioni in termini di costi di opportunità o costi aziendali effettivi.
- Anche i costi ambientali possono essere significativi. Per la famiglia americana media, una casa rappresenta l'investimento più grande e il costo più elevato del budget. Lo stesso accade spesso per i Data Center. I costi dei beni immobili, delle strutture e i costi di utilità rappresentano una parte equa dei costi locali. Quando i Data Center vengono ritirati, è possibile reimpiegare tali funzionalità oppure è possibile che l'azienda sia potenzialmente rilasciata da questi costi.

**Mito: Un modello di spese operative è migliore rispetto a un modello di spese di capitale.** Come illustrato nell'articolo relativo ai [risultati fiscali](business-outcomes/fiscal-outcomes.md) , un modello di spesa operativa può essere un aspetto positivo. Tuttavia, alcune industrie visualizzano le spese operative in senso negativo. Di seguito sono riportati alcuni esempi che innescano una maggiore integrazione con la contabilità e le business unit sulla conversazione delle spese operative:

- Quando un'azienda considera le risorse di capitale come un driver per la valutazione aziendale, le riduzioni delle spese di capitale potrebbero essere un risultato negativo. Sebbene non si tratta di uno standard universale, questo sentimento è più comunemente riscontrato nei settori per la vendita al dettaglio, la produzione e la costruzione.
- Una società di equità privata o una società che sta cercando un afflusso di capitali può prendere in considerazione l'aumento delle spese operative come risultato negativo.
- Se un'azienda si concentra notevolmente sul miglioramento dei margini di vendita o sulla riduzione del costo di merci vendute (PIGNONi), le spese operative potrebbero essere un risultato negativo.

È più probabile che le aziende rivedano le spese operative come più favorevoli delle spese di capitale. Questo approccio, ad esempio, potrebbe essere ricevuto correttamente da aziende che tentano di migliorare il flusso di cassa, ridurre gli investimenti in capitale o ridurre le attività di gestione.

Prima di fornire una giustificazione aziendale incentrata sulla conversione da spese di capitale a spese operative, è necessario comprendere quale sia la soluzione migliore per la propria azienda. L'accounting e l'approvvigionamento possono spesso contribuire a allineare il messaggio agli obiettivi finanziari.

**Mito: la migrazione al cloud è semplice come premere un interruttore.** Le migrazioni sono una trasformazione tecnica manualmente intensa. Quando si sviluppa una motivazione aziendale, in particolare le motivazioni che sono sensibili al tempo, prendere in considerazione i seguenti aspetti che potrebbero aumentare il tempo necessario per eseguire la migrazione delle risorse:

- **Limitazioni della larghezza di banda:** La quantità di larghezza di banda tra il Data Center corrente e il provider di servizi cloud guiderà le sequenze temporali durante la migrazione.
- **Sequenze temporali di test:** Il test delle applicazioni con l'azienda per garantire la conformità e le prestazioni può richiedere molto tempo. L’allineamento agli utenti avanzati e i processi di test sono fondamentali.
- **Sequenze temporali della migrazione:** La quantità di tempo e di lavoro necessaria per implementare la migrazione può aumentare i costi e causare ritardi. Anche l'allocazione di dipendenti o partner contrattuali può ritardare il processo. Il piano deve tenere conto di queste allocazioni.

Gli ostacoli tecnici e culturali possono rallentare l'adozione del cloud. Quando il tempo è un aspetto importante della motivazione aziendale, la soluzione migliore è la corretta pianificazione. Durante la pianificazione, due approcci possono contribuire a ridurre i rischi della sequenza temporale:

- Investire tempo ed energia per comprendere i vincoli di adozione tecnica. Sebbene la pressione per spostarsi rapidamente possa essere elevata, è importante tenere conto di sequenze temporali realistiche.
- Se si verificano ostacoli culturali o persone, avranno effetti più gravi rispetto ai vincoli tecnici. L'adozione del cloud crea un cambiamento, che produce la trasformazione desiderata. Sfortunatamente, le persone a volte temono di cambiare e potrebbe richiedere ulteriore supporto per allinearsi al piano. Identificare le persone principali del team che si oppongono a modifiche e le coinvolgono in anticipo.

Per ottimizzare la conformità e la mitigazione dei rischi per la sequenza temporale, preparare gli stakeholder esecutivi allineando saldamente il valore aziendale e i risultati aziendali. Aiutare le parti interessate a comprendere le modifiche che verranno apportate alla trasformazione. Essere chiari e impostare aspettative realistiche fin dall'inizio. Quando le persone o le tecnologie rallentano il processo, sarà più facile integrare il supporto tecnico Executive.

## <a name="building-the-business-justification"></a>Creazione di una motivazione aziendale

Il processo seguente definisce un approccio allo sviluppo della motivazione aziendale per le migrazioni cloud. Per ulteriori informazioni sui calcoli e sui termini finanziari, vedere l'articolo sui [modelli finanziari](financial-models.md).

Al livello più alto, la formula per una motivazione aziendale è semplice. Tuttavia, i punti dati sottili necessari per popolare la formula possono risultare difficili da allineare. A livello di base, la motivazione aziendale è incentrata sul ritorno sugli investimenti (ROI) associato al cambiamento tecnico proposto. La formula generica per il ROI è:

![ROI Equals (guadagno da investimento meno costo di investimento) diviso per costo di investimento](../_images/formula-roi.png)

È possibile decomprimere questa equazione per ottenere una visualizzazione specifica della migrazione delle formule per le variabili di input sul lato destro dell'equazione. Le altre sezioni di questo articolo offrono alcune considerazioni di cui tenere conto.

## <a name="migration-specific-initial-investment"></a>Investimento iniziale specifico per la migrazione

- I provider di servizi cloud come Azure offrono calcolatrici per stimare gli investimenti nel cloud. Il [calcolatore dei prezzi di Azure](https://azure.microsoft.com/pricing) è un esempio.
- Alcuni provider di servizi cloud forniscono anche calcolatrici a costo Delta. Il [calcolo del costo totale di proprietà (TCO) di Azure](https://azure.com/tco) è un esempio.
- Per strutture di costo più raffinate, prendere in considerazione un esercizio di [pianificazione delle proprietà digitali](../digital-estate/index.md) .
- Stimare il costo della migrazione.
- Stimare il costo di qualsiasi opportunità di training prevista. [Microsoft Learn](/learn) potrebbe essere in grado di mitigare tali costi.
- In alcune aziende, potrebbe essere necessario includere nei costi iniziali il tempo investito dai membri del personale esistente. Per istruzioni, consultare l'ufficio finanziario.
- Discutere eventuali costi aggiuntivi o l’onere dei costi con l'ufficio finanziario per la convalida.

## <a name="migration-specific-revenue-deltas"></a>Delta dei ricavi specifici per la migrazione

Questo aspetto è spesso trascurato dagli strateghi che creano una motivazione aziendale per la migrazione. In alcune aree, il cloud può ridurre i costi. Tuttavia, l'obiettivo finale di qualsiasi trasformazione è ottenere risultati migliori nel tempo. Considerare gli effetti downstream per comprendere i miglioramenti dei ricavi a lungo termine. Quali nuove tecnologie saranno disponibili per l'azienda dopo la migrazione che non è possibile utilizzare oggi? Quali progetti o obiettivi aziendali sono bloccati dalle dipendenze da tecnologie obsolete? Quali programmi sono in attesa di spese di capitale elevata per la tecnologia?

Una volta considerate le opportunità sbloccate dal cloud, collaborare con l'azienda per calcolare gli aumenti dei ricavi che possono provenire da tali opportunità.

## <a name="migration-specific-cost-deltas"></a>Delta dei costi specifici per la migrazione

Calcolare le modifiche ai costi dovute alla migrazione proposta. Vedere l'articolo sui [modelli finanziari](financial-models.md) per informazioni dettagliate sui tipi di delta dei costi. I provider di servizi cloud spesso offrono strumenti per il calcolo dei costi Delta. Il [calcolo del costo totale di proprietà (TCO) di Azure](https://azure.com/tco) è un esempio.

Altri esempi di costi che potrebbero essere ridotti da una migrazione cloud:

- Terminazione o riduzione del Data Center (costi ambientali)
- Riduzione del consumo energetico (costi ambientali)
- Terminazione del rack (ripristino di asset fisico)
- Prevenzione dell'aggiornamento hardware (riduzione dei costi)
- Prevenzione del rinnovo del software (riduzione dei costi operativi o elusione dei costi)
- Consolidamento dei fornitori (riduzione dei costi operativi e riduzione dei costi potenziali)

## <a name="when-roi-results-are-surprising"></a>Quando i risultati ROI sono sorprendenti

Se il ROI per una migrazione cloud non corrisponde alle aspettative, potrebbe essere necessario rivedere i miti comuni elencati all'inizio di questo articolo.

È tuttavia importante comprendere che un risparmio sui costi non è sempre possibile. Alcune applicazioni sono più costose da usare nel cloud rispetto a quelle locali. Queste applicazioni possono alterare significativamente i risultati di un'analisi.

Quando il ROI è inferiore al 20%, si consideri un esercizio di [pianificazione delle proprietà digitali](../digital-estate/index.md) , che presta particolare attenzione alla [razionalizzazione](../digital-estate/rationalize.md). Durante l'analisi quantitativa, esaminare ogni applicazione per individuare i carichi di lavoro che alterano i risultati. Potrebbe essere opportuno rimuovere i carichi di lavoro dal piano. Se sono disponibili i dati di utilizzo, provare a ridurre le dimensioni delle macchine virtuali in modo che corrispondano all’utilizzo.

Se il ritorno sugli investimenti è ancora disallineato, richiedere assistenza al rappresentante Microsoft oppure [coinvolgere un partner esperto](https://azure.microsoft.com/migration/support).

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Creare un modello finanziario per la trasformazione del cloud](./financial-models.md)
