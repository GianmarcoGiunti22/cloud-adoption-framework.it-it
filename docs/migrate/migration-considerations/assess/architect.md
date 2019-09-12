---
title: Progettare i carichi di lavoro prima della migrazione
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Progettare i carichi di lavoro prima della migrazione
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: d62b2f5957dc5cee19f462e3c7d74c85672eadfe
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70819504"
---
# <a name="architect-workloads-prior-to-migration"></a>Progettare i carichi di lavoro prima della migrazione

Questo articolo illustra il processo di valutazione esaminando le attività associate alla definizione dell'architettura di un carico di lavoro all'interno di una determinata iterazione. Come illustrato nell'articolo sulla [razionalizzazione incrementale](../../../digital-estate/rationalize.md), vengono ideati alcuni presupposti di architettura durante qualsiasi trasformazione aziendale che richiede una migrazione. Questo articolo illustra tali presupposti, condivide informazioni su alcuni ostacoli che possono essere evitati e identifica le opportunità per accelerare il valore aziendale sfidando tali presupposti. Questo modello incrementale per l'architettura consente ai team di spostarsi più rapidamente e di ottenere prima i risultati aziendali necessari.

## <a name="architecture-assumptions-prior-to-migration"></a>Presupposti di architettura prima della migrazione

I presupposti seguenti sono tipici per le operazioni di migrazione:

- **IaaS.** È un presupposto comune che la migrazione dei carichi di lavoro implichi principalmente lo spostamento di macchine virtuali da un data center fisico a un data center nel cloud tramite una migrazione IaaS, richiedendo almeno la riconfigurazione o la riconfigurazione. Questo presupposto viene indicato come migrazione in modalità "lift-and-shift" (eccezioni più in basso).
- **Coerenza dell'architettura.** Le modifiche apportate all'architettura di base durante una migrazione aumentano notevolmente la complessità. Il debug di un sistema modificato in una nuova piattaforma introduce molte variabili che possono risultare difficili da isolare. Per questo motivo, i carichi di lavoro devono essere sottoposti solo a modifiche minime durante la migrazione che è necessario verificare accuratamente.
- **Test di ritiro.** Le migrazioni e l'hosting di asset utilizzano le spese operative e in conto capitale potenziali. Si presuppone che i carichi di lavoro migrati siano stati ricontrollati per convalidarne l'utilizzo attuale. La scelta di ritirare le risorse inutilizzate produce risparmi di costi immediati.
- **Ridimensionare gli asset.** Si presuppone che alcuni asset locali stiano usando per intero le risorse allocate. Prima della migrazione, si presuppone che gli asset vengano ridimensionati in modo da adattarsi ai requisiti di utilizzo effettivi.
- **Requisiti di continuità aziendale e ripristino di emergenza (BCDR).** Si presuppone che un contratto di servizio concordato per il carico di lavoro sia stato negoziato con l'azienda prima della pianificazione del rilascio. Questi requisiti possono produrre modifiche di architettura secondarie.
- **Tempo di inattività della migrazione.** Analogamente, i tempi di inattività per promuovere il carico di lavoro alla produzione possono avere un effetto negativo sull'azienda. In alcuni casi, le soluzioni che devono eseguire la transizione con tempi di inattività minimi richiedono modifiche all'architettura. Si presuppone che sia stata stabilita una conoscenza generale dei requisiti del tempo di inattività prima della pianificazione del rilascio.

## <a name="roadblocks-that-can-be-avoided"></a>Ostacoli che possono essere evitati

I presupposti riportati possono creare ostacoli che potrebbero rallentare lo stato di avanzamento o generare criticità in un secondo momento. Di seguito sono riportati alcuni ostacoli da verificare prima del rilascio:

- **Pagamento del debito tecnico.** Alcuni vecchi carichi di lavoro comportano un debito tecnico elevato. Questo può causare problemi a lungo termine con l'aumento dei costi di hosting con qualsiasi provider di servizi cloud. Quando il debito tecnico porta a un aumento dei costi di hosting non naturale, è necessario valutare le architetture alternative.
- **Modelli di traffico utente.** Le soluzioni esistenti possono dipendere da modelli di routing di rete esistenti. Questi modelli potrebbero rallentare notevolmente le prestazioni. Inoltre, l'introduzione di nuove soluzioni di Wide Area Network ibride (WAN) può richiedere settimane o anche mesi. Prepararsi agli ostacoli dell'inizio del processo di architettura considerando i modelli di traffico e le modifiche apportate ai servizi di infrastruttura di base.

## <a name="accelerating-business-value"></a>Accelerazione del valore di business

Alcuni scenari potrebbero richiedere un'architettura diversa rispetto alla strategia di riallocazione IaaS presunta. Di seguito sono riportati alcuni esempi:

- Alternative PaaS. Le distribuzioni PaaS possono ridurre i costi di hosting così come il tempo necessario per eseguire la migrazione di determinati carichi di lavoro. Per un elenco degli approcci che possono trarre vantaggio da una conversione PaaS, vedere l'articolo sulla [valutazione degli asset](./evaluate.md).
- Distribuzioni con script/DevOps. Se un carico di lavoro dispone di una distribuzione DevOps esistente o di altre forme di distribuzione con script, il costo della modifica degli script potrebbe essere inferiore al costo della migrazione dell'asset.
- Impegno alla correzione. Le attività correttive necessarie per preparare un carico di lavoro per la migrazione possono essere numerose. In alcuni casi, è più opportuno modernizzare la soluzione rispetto a correggere i problemi di compatibilità sottostanti.

In ogni scenario, un'architettura alternativa potrebbe essere la soluzione migliore possibile.

## <a name="next-steps"></a>Passaggi successivi

Una volta definita la nuova architettura, [è possibile calcolare stime dei costi accurate](./estimate.md).

> [!div class="nextstepaction"]
> [Stimare i costi del cloud](./estimate.md)
