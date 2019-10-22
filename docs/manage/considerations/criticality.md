---
title: Criticità aziendale-gestione cloud e operazioni
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Criticità aziendale-gestione cloud e operazioni
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 290fcf7093f128c1415bbf960d65074d12490ae1
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/21/2019
ms.locfileid: "72683639"
---
# <a name="business-criticality-in-cloud-management"></a>Criticità aziendale nella gestione cloud

In ogni azienda esiste un numero ridotto di carichi di lavoro troppo importanti per avere esito negativo. Quando tali carichi di lavoro riscontrano interruzioni o riduzione delle prestazioni, un impatto negativo sui ricavi e sulla redditività può essere percepito nell'intera azienda. Questi carichi di lavoro sono considerati cruciali.

All'altra estremità dello spettro, alcuni carichi di lavoro possono passare mesi alla volta senza essere usati. Una riduzione delle prestazioni o delle interruzioni per questi carichi di lavoro non è auspicabile, ma l'effetto è isolato e limitato.

Comprendere la criticità di ogni carico di lavoro nel portfolio IT è il primo passo avanti verso gli impegni reciproci alla gestione del cloud.
Nell'immagine seguente viene illustrato un allineamento comune tra la scala della criticità da seguire e gli impegni standard effettuati dall'azienda.

![Allineamento del livello di criticità e gestione](../../_images/manage/cloud-criticality-alignment.png)

## <a name="criticality-scale"></a>Scalabilità della criticità

Il primo passaggio in qualsiasi sforzo di allineamento della criticità aziendale è la creazione di una scala di criticità. Di seguito è riportata una scala di esempio che può essere usata come riferimento o come modello per creare una scala personalizzata.

|Criticità  |Visualizzazione aziendale  |
|---------|---------|
|Mission-critical|Influisca sulla missione dell'azienda e può influito negativamente sulle istruzioni per i profitti e le perdite aziendali.|
|Unità critica|Influisca sulla missione di una business unit specifica e sulle istruzioni di profitto e perdita delle business unit.|
|Alte|Potrebbe non ostacolare la missione, ma influire sui processi con priorità alta. È possibile quantificare le perdite misurabili in caso di interruzioni.|
|Media|È probabile che l'effetto sui processi sia. Le perdite sono minime o incommensurabili, ma è probabile che siano presenti danni al marchio o perdite upstream.|
|Basse|L'effetto sui processi aziendali è incommensurabile. È probabile che non siano presenti danni al marchio o perdite a Monte. È probabile che l'effetto localizzato su un singolo team.|
|Non supportato|Nessun proprietario, team o processo aziendale associato a questo carico di lavoro può giustificare gli investimenti per la gestione continuativa del carico di lavoro|

Spesso le aziende possono includere classificazioni di criticità aggiuntive specifiche per i processi aziendali, verticali o specifici. Esempi di classificazioni aggiuntive includono:

- **Conformità-critico:** Nei settori fortemente regolamentati, alcuni carichi di lavoro possono essere fondamentali come parte del lavoro richiesto per mantenere i requisiti di conformità.
- **Critico per la sicurezza:** Alcuni carichi di lavoro potrebbero non essere cruciali, ma le interruzioni potrebbero comportare la perdita di dati o l'accesso non intenzionale alle informazioni protette.
- **Critico per la sicurezza:** Quando le vite o la sicurezza fisica dei dipendenti e dei clienti sono a rischio durante un'interruzione, può essere opportuno classificare i carichi di lavoro come critici per la sicurezza.

## <a name="importance-of-accurate-criticality"></a>Importanza della criticità accurata

Più avanti in questo processo, il team di gestione cloud utilizzerà questa classificazione per determinare la quantità di lavoro richiesto per soddisfare i livelli di criticità allineati. Negli ambienti locali, la gestione delle operazioni viene spesso acquistata centralmente e considerata come un onere aziendale necessario, senza costi operativi aggiuntivi. Nel cloud, la gestione delle operazioni (come tutto il cloud) viene acquistata in base alle singole risorse come costi operativi mensili.

Poiché esiste un costo chiaro e diretto per la gestione delle operazioni nel cloud, è importante allineare adeguatamente i costi e le scale di criticità desiderate.

## <a name="select-a-default-criticality"></a>Selezionare una criticità predefinita

Una revisione iniziale di ogni carico di lavoro nel portfolio potrebbe richiedere molto tempo. Per garantire che questa operazione non blocchi la strategia cloud più ampia, è consigliabile che l'IT e l'azienda accettino una criticità predefinita da applicare a tutti i carichi di lavoro.

In base alla scala di criticità descritta in precedenza, è consigliabile usare come impostazione predefinita "media". Questa operazione consentirà al team di strategia cloud di identificare rapidamente i carichi di lavoro che richiedono un livello di criticità superiore.

## <a name="using-the-template"></a>Uso del modello

I passaggi seguenti si applicano ai lettori che usano la [cartella di lavoro di gestione Ops](https://raw.githubusercontent.com/microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx) per pianificare la gestione del cloud.

1. La scalabilità della criticità può essere registrata nella scheda scala della cartella di lavoro.
2. Ogni carico di lavoro in "example" o "Clean template" deve essere aggiornato per riflettere la criticità predefinita nella colonna "criticità".
3. I valori corretti devono essere inseriti dall'azienda in modo da riflettere qualsiasi deviazione rispetto alla criticità predefinita.

## <a name="next-steps"></a>Passaggi successivi

Una volta definita la criticità, [calcolare e registrare l'effetto aziendale](./impact.md).

> [!div class="nextstepaction"]
> [Calcolare e registrare l'effetto aziendale](./impact.md)
