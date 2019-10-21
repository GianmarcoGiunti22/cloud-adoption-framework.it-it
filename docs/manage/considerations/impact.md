---
title: Criticità aziendale-gestione cloud e operazioni
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Criticità aziendale-gestione cloud e operazioni
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/07/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 2b5901699be735bddac260c9def1a884431d8989
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72557544"
---
# <a name="business-impact-in-cloud-management"></a>Un effetto aziendale sulla gestione cloud

Si supponga che il migliore sia preferibile. Nella gestione IT, è preferibile presupporre che i carichi di lavoro necessari per supportare le operazioni aziendali siano disponibili e che effettuino i vincoli concordati, in base alla criticità selezionata. Tuttavia, per gestire gli investimenti in modo oculato, è importante comprendere l'effetto riscontrato dall'azienda quando si verifica un'interruzione o un calo delle prestazioni. Questa importanza è illustrata nel grafico seguente, che esegue il mapping delle potenziali interruzioni aziendali dei carichi di lavoro specifici all'impatto aziendale delle interruzioni in una scala di valori relativi.

![Conseguenze delle interruzioni aziendali](../../_images/manage/time-value-impact.png)

Per creare una base di confronto per l'effetto sui vari carichi di lavoro in un portfolio, viene suggerita una metrica temporale/valore. La metrica tempo/valore acquisisce l'impatto negativo di un'interruzione del carico di lavoro. In genere, questo effetto viene registrato come perdita diretta dei ricavi o dei ricavi operativi durante un periodo di interruzione normale. In particolare, il calcolo della quantità di ricavi persi per un'unità di tempo. La metrica temporale/valore più comune è "Impact all'ora", che misura le perdite dei ricavi operativi per ora di interruzione.

Esistono alcuni approcci che possono essere usati per calcolare l'effetto. Tutte le opzioni delle sezioni seguenti possono essere utilizzate con risultati simili. Quando si calcolano le perdite protette in un portfolio, è importante usare lo stesso approccio per ogni carico di lavoro.

## <a name="start-with-estimates"></a>Inizia con stime

I modelli operativi correnti possono rendere difficile determinare un effetto preciso. Fortunatamente, pochi sistemi necessitano di un calcolo di perdita molto accurato. Nel passaggio precedente: classificare la criticità, è stato suggerito che tutti i carichi di lavoro iniziano con il valore predefinito "media criticità". I carichi di lavoro con criticità media riceveranno in genere un livello standard di supporto per la gestione con un impatto sui costi operativi relativamente basso. Solo quando un carico di lavoro richiede risorse di gestione operative aggiuntive, potrebbe essere necessario un effetto finanziario accurato.

Per tutti i carichi di lavoro standardizzati, l'effetto aziendale funge da variabile di assegnazione delle priorità durante il ripristino dei sistemi durante un'interruzione del servizio. Al di fuori di queste situazioni limitate, l'effetto aziendale creerà pochissime modifiche nell'esperienza di gestione delle operazioni. 

## <a name="calculating-time"></a>Calcolo del tempo

A seconda della natura del carico di lavoro, le perdite potrebbero essere calcolate in modo diverso. Per sistemi transazionali ad alta velocità come una piattaforma di trading in tempo reale, le perdite per millisecondo potrebbero essere significative. I sistemi usati meno di frequente, ad esempio Payroll, non possono essere usati ogni ora. Se la frequenza di utilizzo è alta o bassa, è importante normalizzare la variabile temporale durante il calcolo dell'effetto finanziario.

## <a name="calculating-total-impact"></a>Calcolo dell'effetto totale

Quando si desidera un investimento di gestione aggiuntivo, è più importante che l'effetto aziendale risulti più accurato. Il contorno dei punti elenco seguenti si avvicina al calcolo delle perdite, in ordine più accurato (dal più accurato al meno accurato):

- **Perdite modificate:** Se l'azienda ha riscontrato un evento di perdita principale in passato, ad esempio un uragano o un'altra calamità naturale, è possibile che una regola di attestazione abbia calcolato perdite effettive durante l'interruzione. Questi calcoli sono basati sugli standard del settore assicurativo per il calcolo delle perdite e la gestione dei rischi. L'uso di perdite modificate come quantità totale di perdite in un intervallo di tempo specifico può causare proiezioni altamente accurate.

- **Perdite storiche:** Se l'ambiente locale ha sofferto da interruzioni storiche a causa dell'instabilità dell'infrastruttura, può essere un po' più difficile calcolare le perdite. Tuttavia, le formule di regolazione possono comunque essere utilizzate internamente. Per calcolare le perdite cronologiche, confrontare i Delta nelle vendite, i ricavi lordi e i costi operativi in tre frame temporali: prima, durante e dopo l'interruzione. L'analisi di questi Delta può determinare perdite accurate quando non sono disponibili altri dati.

- **Calcolo completo della perdita:** Se non sono disponibili dati cronologici, è possibile derivare un valore di perdita comparativa. In questo modello determinare il fatturato lordo medio per ora per la business unit. Presumendo che un'interruzione completa del sistema equivale al 100%, la perdita di ricavi è un presupposto scadente quando si proiettano investimenti per evitare perdite. Ma può essere usato come base per confrontare le conseguenze della perdita e la priorità degli investimenti.

Prima di creare presupposti relativi ai calcoli di perdita, collaborare con il reparto finanziario per determinare l'approccio migliore per calcolare le potenziali perdite associate a un'interruzione del carico di lavoro.

## <a name="calculating-workload-impact"></a>Calcolo dell'effetto del carico di lavoro

Quando si sfruttano i dati cronologici per calcolare le perdite, è possibile che siano disponibili informazioni sufficienti per determinare chiaramente l'effetto di ogni carico di lavoro su tali perdite. Questa valutazione è la posizione in cui la collaborazione con l'azienda è assolutamente critica. Una volta calcolato l'effetto totale, tale effetto deve essere attribuito a ogni carico di lavoro. La distribuzione dell'effetto dovrebbe derivare dalle parti interessate dell'azienda, che devono concordare sull'incidenza relativa e cumulativa di ogni carico di lavoro. Inoltre, il team deve sollecitare commenti e suggerimenti dei dirigenti aziendali per convalidare l'allineamento. Sfortunatamente, il risultato finale è identico alle parti emozioni e alle competenze in materia. L'importanza di questo esercizio è che rappresenta la logica e la credenza degli stakeholder aziendali che dovrebbero avere un'opinione nell'allocazione del budget.

## <a name="using-the-template"></a>Uso del modello

I passaggi seguenti si applicano ai lettori che usano la [cartella di lavoro di gestione Ops](https://raw.githubusercontent.com/microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx) per pianificare la gestione del cloud.

1. Ogni carico di lavoro nell'"esempio" o "modello pulito" deve essere aggiornato dall'azienda con l'"effetto tempo/valore" di ogni carico di lavoro. Per impostazione predefinita, il termine "tempo/valore" indica le perdite proiettate all'ora associate a un'interruzione del carico di lavoro.

## <a name="next-steps"></a>Passaggi successivi

Una volta definito l'effetto, gli [impegni possono essere allineati](./commitment.md).

> [!div class="nextstepaction"]
> [Allineare gli impegni di gestione all'azienda](./commitment.md)
