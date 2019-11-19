---
title: 'Criticità aziendale: gestione e operazioni del cloud'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Criticità aziendale: gestione e operazioni del cloud'
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 219c5b402c9cdc4b6214e8a5ed38b85ba7a2e203
ms.sourcegitcommit: 50788e12bb744dd44da14184b3e884f9bddab828
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2019
ms.locfileid: "74160365"
---
# <a name="business-criticality-in-cloud-management"></a>Criticità aziendale nella gestione cloud

In ogni azienda esiste un numero ridotto di carichi di lavoro troppo importanti per avere esito negativo. Questi carichi di lavoro sono considerati mission-critical. Quando tali carichi di lavoro riscontrano interruzioni o riduzione delle prestazioni, l'impatto negativo sui ricavi e sulla redditività può essere percepito nell'intera azienda.

All'altra estremità dello spettro, alcuni carichi di lavoro possono passare mesi alla volta senza essere usati. Una riduzione delle prestazioni o delle interruzioni per questi carichi di lavoro non è auspicabile, ma l'effetto è isolato e limitato.

Comprendere la criticità di ogni carico di lavoro nel portfolio IT è il primo passo verso la definizione di impegni reciproci per la gestione del cloud.
Il diagramma seguente illustra un allineamento comune tra la scala della criticità da seguire e gli impegni standard effettuati dall'azienda.

![Allineamento del livello di criticità e gestione](../../_images/manage/cloud-criticality-alignment.png)

## <a name="criticality-scale"></a>Scalabilità della criticità

Il primo passaggio in qualsiasi sforzo di allineamento della criticità aziendale consiste nel creare una scala di criticità. La tabella seguente presenta una scala di esempio da usare come riferimento, o modello, per la creazione di una scala personalizzata.

| Criticità | Visualizzazione aziendale |
| --------- | --------- |
| Cruciale |  Influisce sulla missione dell'azienda e potrebbe influire negativamente sulle istruzioni aziendali di profitto e perdita. |
| Unità-critico | Influiscono sulla missione di una business unit specifica e sulle relative istruzioni di profitto e perdita. |
| Alte | Potrebbe non ostacolare la missione, ma influisce sui processi di importanza elevata. È possibile quantificare le perdite misurabili in caso di interruzioni. |
| Media | L'effetto sui processi è probabilmente. Le perdite sono minime o incommensurabili, ma è probabile che siano presenti danni al marchio o alle perdite upstream. |
| Basse | Un effetto sui processi aziendali non è misurabile. È probabile che non siano presenti danni al marchio e perdite a Monte. È probabile che l'effetto localizzato su un singolo team. |
| Non supportato | Nessun proprietario aziendale, team o processo associato a questo carico di lavoro può giustificare eventuali investimenti nella gestione continuativa del carico di lavoro. |

Spesso le aziende possono includere classificazioni di criticità aggiuntive specifiche per i processi aziendali, verticali o specifici del settore. Esempi di classificazioni aggiuntive includono:

- **Conformità-critico:** Nei settori fortemente regolamentati, alcuni carichi di lavoro potrebbero essere fondamentali come parte del lavoro richiesto per mantenere i requisiti di conformità.
- **Critico per la sicurezza:** Alcuni carichi di lavoro potrebbero non essere cruciali, ma le interruzioni potrebbero comportare la perdita di dati o l'accesso non intenzionale alle informazioni protette.
- **Critico per la sicurezza:** Quando la vita o la sicurezza fisica di dipendenti e clienti è a rischio durante un'interruzione, può essere opportuno classificare i carichi di lavoro come critici per la sicurezza.

## <a name="importance-of-accurate-criticality"></a>Importanza della criticità accurata

Più avanti nel processo di adozione del cloud, il team di gestione cloud utilizzerà questa classificazione per determinare la quantità di lavoro richiesto per soddisfare i livelli di criticità allineati. Negli ambienti locali, la gestione delle operazioni viene spesso acquistata in modo centralizzato e considerata come un onere aziendale necessario, con costi operativi minimi o nulli. Nel cloud, la gestione delle operazioni (come tutto il cloud) viene acquistata in base alle singole risorse come costi operativi mensili.

Poiché esiste un costo chiaro e diretto per la gestione delle operazioni nel cloud, è importante allineare adeguatamente i costi e le scale di criticità desiderate.

## <a name="select-a-default-criticality"></a>Selezionare una criticità predefinita

Una revisione iniziale di ogni carico di lavoro nel portfolio può richiedere molto tempo. Per assicurarsi che questa operazione non blocchi la strategia cloud più ampia, è consigliabile che i team accettino una criticità predefinita da applicare a tutti i carichi di lavoro.

In base alla tabella con scalabilità critica precedente, si consiglia di adottare la criticità *media* come impostazione predefinita. Questa operazione consentirà al team della strategia cloud di identificare rapidamente i carichi di lavoro che richiedono un livello di criticità superiore.

## <a name="use-the-template"></a>Usa il modello

I passaggi seguenti si applicano se si usa la [cartella di lavoro di gestione Ops](https://raw.githubusercontent.com/microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx) per pianificare la gestione del cloud.

1. Registrare la scala della criticità nella scheda **scala** della cartella di lavoro.
2. Aggiornare ogni carico di lavoro nell' *esempio* o *pulire il modello* in modo da riflettere la criticità predefinita nella colonna *criticità* .
3. L'azienda deve immettere i valori corretti per riflettere eventuali deviazioni rispetto alla criticità predefinita.

## <a name="next-steps"></a>Passaggi successivi

Dopo che il team ha definito la criticità aziendale, è possibile [calcolare e registrare l'effetto aziendale](./impact.md).

> [!div class="nextstepaction"]
> [Calcolare e registrare l'effetto aziendale](./impact.md)
