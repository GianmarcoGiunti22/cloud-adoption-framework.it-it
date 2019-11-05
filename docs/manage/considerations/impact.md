---
title: Business Impact-gestione cloud e operazioni
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Business Impact-gestione cloud e operazioni
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 356460b8f2952475060c857e0b7999696be0d215
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565135"
---
# <a name="business-impact-in-cloud-management"></a>Un effetto aziendale sulla gestione cloud

Si supponga che il migliore sia preferibile. Nella gestione IT, è preferibile presupporre che i carichi di lavoro necessari per supportare le operazioni aziendali saranno disponibili e verranno eseguiti entro i vincoli concordati, in base alla criticità selezionata. Tuttavia, per gestire gli investimenti in modo oculato, è importante comprendere l'effetto sull'azienda quando si verifica un'interruzione o una riduzione delle prestazioni. Questa importanza è illustrata nel grafico seguente, che esegue il mapping delle potenziali interruzioni aziendali di carichi di lavoro specifici all'impatto aziendale delle interruzioni in una scala di valori relativi.

![Conseguenze delle interruzioni aziendali](../../_images/manage/time-value-impact.png)

Per creare una base di confronto per l'effetto sui vari carichi di lavoro in un portfolio, viene suggerita una metrica temporale/valore. La metrica tempo/valore acquisisce l'impatto negativo di un'interruzione del carico di lavoro. In genere, questo effetto viene registrato come perdita diretta dei ricavi o dei ricavi operativi durante un periodo di interruzione normale. In particolare, viene calcolata la quantità di ricavi persi per un'unità di tempo. La metrica temporale/valore più comune è l' *effetto per ora*, che misura le perdite dei ricavi operativi per ora di interruzione.

È possibile usare alcuni approcci per calcolare l'effetto. È possibile applicare qualsiasi opzione nelle sezioni seguenti per ottenere risultati simili. Quando si calcolano le perdite protette in un portfolio, è importante usare lo stesso approccio per ogni carico di lavoro.

## <a name="start-with-estimates"></a>Inizia con stime

I modelli operativi correnti possono rendere difficile determinare un effetto accurato. Fortunatamente, pochi sistemi necessitano di un calcolo di perdita molto accurato. Nel passaggio precedente, *classificare la criticità*, è consigliabile avviare tutti i carichi di lavoro con un valore predefinito di *criticità medio*. I carichi di lavoro con criticità media ricevono in genere un livello standard di supporto per la gestione con un impatto relativamente basso sul costo operativo. Solo quando un carico di lavoro richiede risorse aggiuntive per la gestione operativa, potrebbe essere necessario un effetto finanziario accurato.

Per tutti i carichi di lavoro standardizzati, l'effetto aziendale funge da variabile di assegnazione delle priorità quando si esegue il ripristino dei sistemi durante un'interruzione del servizio. Al di fuori di queste situazioni limitate, l'effetto aziendale crea poco a nessuna modifica nell'esperienza di gestione delle operazioni.

## <a name="calculate-time"></a>Calcola ora

A seconda della natura del carico di lavoro, è possibile calcolare le perdite in modo diverso. Per sistemi transazionali ad alta velocità, ad esempio una piattaforma di trading in tempo reale, le perdite per millisecondo potrebbero essere significative. I sistemi utilizzati meno di frequente, ad esempio Payroll, potrebbero non essere utilizzati ogni ora. Se la frequenza di utilizzo è alta o bassa, è importante normalizzare la variabile temporale quando si calcola l'effetto finanziario.

## <a name="calculate-total-impact"></a>Calcola l'effetto totale

Quando si desidera prendere in considerazione altri investimenti di gestione, è più importante che l'effetto aziendale risulti più accurato. I tre approcci seguenti per il calcolo delle perdite sono ordinati dal più accurato al meno accurato:

- **Perdite modificate:** Se l'azienda ha riscontrato un evento di perdita principale in passato, ad esempio un uragano o un'altra calamità naturale, un addetto alle attestazioni potrebbe avere calcolato perdite effettive durante l'interruzione. Questi calcoli sono basati sugli standard del settore assicurativo per il calcolo delle perdite e la gestione dei rischi. L'uso di perdite modificate come quantità totale di perdite in un intervallo di tempo specifico può causare proiezioni altamente accurate.

- **Perdite storiche:** Se l'ambiente locale ha sofferto storicamente dalle interruzioni derivanti dall'instabilità dell'infrastruttura, può essere un po' più difficile calcolare le perdite. Tuttavia, è comunque possibile applicare le formule di regolazione sfruttate internamente. Per calcolare le perdite cronologiche, confrontare i Delta nelle vendite, i ricavi lordi e i costi operativi in tre frame temporali: prima, durante e dopo l'interruzione. Esaminando questi Delta, è possibile identificare le perdite accurate quando non sono disponibili altri dati.

- **Calcolo completo della perdita:** Se non sono disponibili dati cronologici, è possibile derivare un valore di perdita comparativa. In questo modello si determinano i ricavi lordi medi per ora per la business unit. Quando si proiettano investimenti di prevenzione della perdita, non è lecito presumere che un'interruzione completa del sistema equivale a una perdita del 100% dei ricavi. È tuttavia possibile usare questo presupposto come base per confrontare le conseguenze della perdita e la priorità degli investimenti.

Prima di prendere alcune ipotesi sulle potenziali perdite associate a interruzioni del carico di lavoro, è consigliabile collaborare con il reparto finanziario per determinare l'approccio migliore a tali calcoli.

## <a name="calculate-workload-impact"></a>Calcolo dell'effetto del carico di lavoro

Quando si calcolano le perdite applicando i dati cronologici, è possibile che si disponga di informazioni sufficienti per determinare chiaramente il contributo di ogni carico di lavoro a tali perdite. Per eseguire questa valutazione, le relazioni all'interno dell'azienda sono assolutamente critiche. Una volta calcolato l'effetto totale, tale effetto deve essere attribuito a tutti i carichi di lavoro. La distribuzione dell'effetto dovrebbe derivare dalle parti interessate dell'azienda, che devono concordare sull'incidenza relativa e cumulativa di ogni carico di lavoro. A tale scopo, il team deve sollecitare commenti e suggerimenti dei dirigenti aziendali per convalidare l'allineamento. Questo feedback è spesso uguale alle parti emozioni e alle competenze in materia. È importante che questo esercizio rappresenti la logica e le credenze degli stakeholder aziendali che dovrebbero avere un'opinione nell'allocazione del budget.

## <a name="use-the-template"></a>Usa il modello

Se si usa la [cartella di lavoro di Operations Management](https://raw.githubusercontent.com/microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx) per pianificare la gestione del cloud, provare a eseguire le operazioni seguenti:

- Ogni azienda deve aggiornare ogni carico di lavoro nell' *esempio* o *pulire un modello* con l' *effetto tempo/valore* di ogni carico di lavoro. Per impostazione predefinita, l' *effetto tempo/valore* rappresenta le perdite proiettate all'ora associate a un'interruzione del carico di lavoro.

## <a name="next-steps"></a>Passaggi successivi

Dopo che l'azienda ha definito un effetto, è possibile [allineare gli impegni](./commitment.md).

> [!div class="nextstepaction"]
> [Allineare gli impegni di gestione all'azienda](./commitment.md)
