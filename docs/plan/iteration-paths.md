---
title: Stabilire le iterazioni e i piani di rilascio
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Stabilire le iterazioni e i piani di rilascio
author: BrianBlanchard
ms.author: brblanch
ms.date: 07/01/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: plan
ms.openlocfilehash: 0dbef36d3909f11c1616d2e44c63227959c4ff56
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70833778"
---
# <a name="establish-iterations-and-release-plans"></a>Stabilire le iterazioni e i piani di rilascio

Agile e altre metodologie iterative sono basate sui concetti di iterazioni e versioni. Questo articolo descrive l'assegnazione di iterazioni e versioni durante la pianificazione. Tali assegnazioni guidano la visibilità della sequenza temporale per semplificare le conversazioni tra i membri del team di strategia cloud. Le assegnazioni allineano anche le attività tecniche in modo che il team di adozione del cloud possa gestire durante l'implementazione.

## <a name="establish-iterations"></a>Stabilire le iterazioni

In un approccio iterativo all'implementazione tecnica, si pianificano le attività tecniche relative ai blocchi temporali ricorrenti. Le iterazioni tendono a essere bloccate da una settimana a sei settimane. Il consenso suggerisce che due settimane è la durata media delle iterazioni per la maggior parte dei team di adozione del cloud. Tuttavia, la scelta della durata dell'iterazione dipende dal tipo di lavoro tecnico, dal sovraccarico amministrativo e dalle preferenze del team.

Per iniziare a allineare le attività a una sequenza temporale, è consigliabile definire un set di iterazioni che dura da 6 a 12 mesi.

## <a name="understand-velocity"></a>Informazioni sulla velocità

L'allineamento degli sforzi a iterazioni e versioni richiede una conoscenza della velocità. Velocità è la quantità di lavoro che può essere completata in una determinata iterazione. Durante le fasi iniziali della pianificazione, la velocità è una stima. Dopo diverse iterazioni, la velocità diventa un indicatore estremamente prezioso degli impegni che il team può ottenere in modo sicuro.

È possibile misurare la velocità in termini astratti, come i punti della storia. È anche possibile misurarlo in termini più tangibili come le ore. Per la maggior parte dei Framework iterativi, è consigliabile usare misure astratte per evitare problemi di precisione e percezione. Gli esempi in questo articolo rappresentano la velocità in ore per Sprint. Questa rappresentazione rende più universale la comprensione dell'argomento.

**Esempio:** Un team di adozione del cloud di cinque persone si è impegnato a Sprint di due settimane. Considerati gli obblighi correnti, ad esempio le riunioni e il supporto di altri processi, ogni membro del team può contribuire in modo coerente a 20 ore alla settimana per il lavoro di adozione. Per questo team, la stima della velocità iniziale è di 100 ore per Sprint.

## <a name="iteration-planning"></a>Pianificazione iterazione

Inizialmente si pianificano le iterazioni valutando le attività tecniche in base al backlog con priorità. I team di adozione del cloud stimano il lavoro richiesto per completare varie attività. Queste attività vengono quindi assegnate alla prima iterazione disponibile.

Durante la pianificazione delle iterazioni, i team di adozione del cloud convalidano e perfezionano le stime. A tale scopo, fino a quando non hanno allineato tutta la velocità disponibile a specifiche attività. Questo processo continua per ogni carico di lavoro con priorità fino a quando tutti gli sforzi non vengono allineati a un'iterazione prevista.

In questo processo, il team convalida le attività assegnate allo sprint successivo. Il team aggiorna le stime in base alla conversazione del team su ogni attività. Il team aggiunge quindi ogni attività stimata allo sprint successivo fino a quando non viene soddisfatta la velocità disponibile. Infine, il team stima le attività aggiuntive e le aggiunge all'iterazione successiva. Il team esegue questi passaggi fino a quando non viene esaurita anche la velocità di tale iterazione.

Il processo precedente continua fino a quando tutte le attività vengono assegnate a un'iterazione.

**Esempio:** Si creerà l'esempio precedente. Si supponga che ogni migrazione del carico di lavoro richieda 40 attività. Si supponga inoltre di stimare ogni attività in modo da richiedere una media di un'ora. La stima combinata è di circa 40 ore per la migrazione del carico di lavoro. Se queste stime rimangono coerenti per tutti i 10 carichi di lavoro con priorità, i carichi di lavoro saranno di 400 ore.

La velocità definita nell'esempio precedente suggerisce che la migrazione dei primi 10 carichi di lavoro effettuerà quattro iterazioni, ovvero due mesi di tempo di calendario. La prima iterazione è costituita da 100 attività che comportano la migrazione di due carichi di lavoro. Nell'iterazione successiva, una raccolta simile di 100 attività comporterà la migrazione di tre carichi di lavoro.

> [!WARNING]
> Il numero di attività e stime precedenti viene usato esclusivamente come esempio. Le attività tecniche sono raramente coerenti. Questo esempio non dovrebbe essere visualizzato come riflesso della quantità di tempo necessaria per la migrazione di un carico di lavoro.

## <a name="release-planning"></a>Pianificazione del rilascio

All'interno dell'adozione del cloud, una versione è definita come una raccolta di risultati finali che producono un valore aziendale sufficiente per giustificare il rischio di rotture ai processi aziendali.

Il rilascio di eventuali modifiche relative al carico di lavoro in un ambiente di produzione crea alcune modifiche ai processi aziendali. Idealmente, queste modifiche sono semplici e l'azienda considera il valore delle modifiche senza interruzioni significative per il servizio. Il rischio di rotture aziendali è tuttavia presente con qualsiasi modifica e non deve essere preso in considerazione.

Per garantire che una modifica sia giustificata dal potenziale ritorno, il team di strategia cloud deve partecipare alla pianificazione del rilascio. Quando le attività sono allineate agli sprint, il team può determinare una sequenza temporale approssimativa quando ogni carico di lavoro sarà pronto per la versione di produzione. Il team di strategia cloud verificherebbe la tempistica di ogni rilascio. Il team identificherà quindi il punto di flessione tra il rischio e il valore aziendale.

**Esempio:** Continuando con l'esempio precedente, il team di strategia cloud ha esaminato il piano di iterazione. La revisione ha identificato due punti di rilascio. Durante la seconda iterazione, un totale di cinque carichi di lavoro sarà pronto per la migrazione. Questi cinque carichi di lavoro offriranno un valore aziendale significativo e attiveranno il primo rilascio. La versione successiva rientrerà in due iterazioni in un secondo momento, quando i cinque carichi di lavoro successivi saranno pronti per la versione.

## <a name="assign-iteration-paths-and-tags"></a>Assegnare i percorsi di iterazione e i tag

Per i clienti che gestiscono i piani di adozione del cloud in Azure DevOps, i processi precedenti vengono riflessi assegnando un percorso di iterazione a ogni attività e storia utente. È inoltre consigliabile contrassegnare ogni carico di lavoro con una versione specifica. L'assegnazione di tag e l'assegnazione inviano il popolamento automatico dei report della sequenza temporale.

## <a name="next-steps"></a>Passaggi successivi

[Stimare le sequenze temporali](./timelines.md) per comunicare correttamente le aspettative.

> [!div class="nextstepaction"]
> [Stime temporali](./timelines.md)
