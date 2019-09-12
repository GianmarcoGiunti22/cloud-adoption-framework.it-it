---
title: Gestire il mantenimento delle priorità aziendali durante un processo di trasformazione a lungo termine
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Gestire il mantenimento delle priorità aziendali durante un processo di trasformazione a lungo termine.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 05d9441eb8867ff47ad23ccc44a9b58d8e010499
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70833505"
---
# <a name="business-priorities---maintaining-alignment"></a>Priorità aziendali - Gestione dell'allineamento

La *trasformazione* è spesso definita come una modifica drammatica o spontanea. A livello di direzione, la modifica può essere simile a una trasformazione drammatica. Tuttavia, per coloro che usano il processo di modifica in un'organizzazione, la trasformazione è un po' fuorviante. Sotto la superficie, la trasformazione è meglio descritta come una serie di transizioni eseguite correttamente da uno stato a un altro.

La quantità di tempo necessaria per razionalizzare o eseguire la transizione di un carico di lavoro varia a seconda della complessità tecnica coinvolta. Tuttavia, anche quando questo processo può essere applicato rapidamente a un singolo carico di lavoro o a un gruppo di applicazioni, è necessario tempo per produrre modifiche sostanziali all'interno di una base utente. Per la propagazione delle modifiche attraverso diversi livelli di processi aziendali esistenti, è necessario più tempo. Se si prevede che la trasformazione formi modelli di comportamento nei clienti, produrre risultati significativi richiede più tempo.

Sfortunatamente, il mercato non attende la transizione delle aziende. I modelli di comportamento dei clienti cambiano autonomamente, spesso in modo imprevisto. La percezione del mercato di un'azienda e dei suoi prodotti può essere influenzata dai social media o dal posizionamento di un concorrente. Le modifiche di mercato rapide e impreviste richiedono che le aziende siano agili e reattive.

La possibilità di eseguire processi e transizioni tecniche richiede un lavoro coerente e stabile. Le decisioni rapide e le azioni agili sono necessarie per rispondere alle condizioni di mercato. Queste due sono in conflitto, semplificando l'allineamento delle priorità. Questo articolo descrive gli approcci alla gestione dell'allineamento di transizione durante le operazioni di migrazione.

<!-- markdownlint-disable MD026 -->

## <a name="how-can-business-and-technical-priorities-stay-aligned-during-a-migration"></a>In che modo le priorità aziendali e tecniche possono rimanere allineate durante una migrazione?

Il team di adozione del cloud e il team di governance del cloud si concentrano sull'esecuzione dell'iterazione e del rilascio correnti. Le iterazioni forniscono incrementi stabili di lavoro tecnico, evitando così costosi disagi che altrimenti rallenteranno lo stato di avanzamento delle attività di migrazione. I diversi rilasci assicurano che lo sforzo tecnico e l'energia siano concentrati sugli obiettivi aziendali della migrazione del carico di lavoro. Un progetto di migrazione potrebbe richiedere molti rilasci diversi in un periodo prolungato. Nel momento in cui è stata completata, le condizioni di mercato sono state probabilmente modificate in modo significativo.

In parallelo, il team di strategia del cloud si concentra sull'esecuzione del piano di modifica aziendale e sulla preparazione per il rilascio successivo. Il team di strategia del cloud in genere analizza almeno un rilascio in anticipo e monitora la variazione delle condizioni di mercato e gestisce di conseguenza il backlog di migrazione. Questa attività di gestione della trasformazione e della regolazione del piano crea pivot naturali attorno al lavoro tecnico. Quando si modificano le priorità aziendali, l'adozione è solo a un rilascio di distanza, creando flessibilità tecnica e aziendale.

## <a name="business-alignment-questions"></a>Domande di allineamento del business

Le domande seguenti possono essere utili al team di strategia del cloud per formare e definire la priorità del backlog di migrazione, in modo da assicurare che il lavoro di trasformazione sia più adatto alle esigenze aziendali correnti.

- Il team di adozione del cloud ha identificato un elenco di carichi di lavoro pronti per la migrazione?
- Il team di adozione del cloud ha selezionato un singolo candidato per una migrazione iniziale da tale elenco di carichi di lavoro?
- Il team di adozione del cloud e il team di governance del cloud hanno tutti i dati necessari relativi al carico di lavoro e all'ambiente cloud per avere un esito positivo?
- Il carico di lavoro candidato genera l'impatto più rilevante per l'azienda nel prossimo rilascio?
- Sono presenti altri carichi di lavoro più idonei per la migrazione?

## <a name="tangible-actions"></a>Azioni tangibili

Durante l'esecuzione del piano di modifica aziendale, il team di strategia del cloud monitora i risultati positivi e negativi. Quando tali osservazioni richiedono modifiche tecniche, le rettifiche vengono aggiunte come elementi di lavoro al backlog di rilascio per essere classificate in ordine di priorità nell'iterazione successiva.

Quando il mercato cambia, il team di strategia del cloud collabora con l'azienda per comprendere come rispondere alle modifiche in modo ottimale. Quando tale risposta richiede una modifica alle priorità di migrazione, il backlog di migrazione viene modificato. Questa operazione consente di spostare i carichi di lavoro precedentemente inferiori in priorità.

## <a name="next-steps"></a>Passaggi successivi

Con le priorità aziendali allineate correttamente, il team di adozione del cloud può iniziare a [valutare i carichi di lavoro](./evaluate.md) per sviluppare piani di architettura e migrazione.

> [!div class="nextstepaction"]
> [Valutare i carichi di lavoro](./evaluate.md)
