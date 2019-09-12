---
title: Che cos'è il cloud accounting?
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Spiegazione del concetto di accounting cloud
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: strategy
ms.openlocfilehash: 62eea92ae85faa396cc36e062735ab2ed182b012
ms.sourcegitcommit: 5846ed4d0bf1b6440f5e87bc34ef31ec8b40b338
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2019
ms.locfileid: "70905754"
---
<!-- markdownlint-disable MD026 -->

# <a name="what-is-cloud-accounting"></a>Che cos'è il cloud accounting?

Il cloud modifica la modalità di gestione dei costi, come descritto in [creazione di un modello finanziario per la trasformazione cloud](financial-models.md). Diversi modelli di contabilità IT sono molto più facili da supportare grazie al modo in cui il cloud alloca i costi. È quindi importante comprendere come tenere conto dei costi del cloud prima di iniziare un percorso di trasformazione cloud. Questo articolo descrive i modelli di contabilità cloud più comuni per l'IT.

## <a name="traditional-it-accounting-cost-center-model"></a>Contabilità IT tradizionale (modello di centro di costo)

Spesso è opportuno considerarlo un centro di costo. Nel modello di contabilità IT tradizionale, consolida la potenza di acquisto per tutte le risorse IT. Come indicato nell'articolo sui [modelli finanziari](financial-models.md) , il consolidamento dell'energia di acquisto può includere le licenze software, gli addebiti ricorrenti per le licenze CRM, l'acquisto di desktop dei dipendenti e altri costi elevati.

Quando funge da centro di costo, il valore percepito viene visualizzato in gran parte tramite una lente di gestione dell'approvvigionamento. Questa percezione rende difficile per la lavagna o altri dirigenti comprendere il vero valore che fornisce. I costi di approvvigionamento tendono a distorcere la visualizzazione della soluzione, superando qualsiasi altro valore aggiunto dall'organizzazione. Questa vista spiega perché è spesso incentrata sulle responsabilità del responsabile finanziario o del COO. Questa percezione è limitata e può essere miope.

## <a name="central-it-accounting-profit-center-model"></a>Contabilità IT centrale (modello centro di profitto)

Per ovviare alla vista del centro di costo, alcuni CIOs hanno optato per un modello IT centrale di contabilità. In questo tipo di modello, viene trattato come una business unit concorrente e un peer per le business unit che producono i ricavi. In alcuni casi, questo modello può essere interamente logico. Ad esempio, alcune organizzazioni hanno una divisione Professional IT Services che genera un flusso di ricavi. Spesso i modelli IT centrali non generano ricavi significativi, rendendo difficile giustificare il modello.

Indipendentemente dal modello di ricavi, i modelli di contabilità IT centrale sono univoci a causa del modo in cui l'unità IT conta i costi. In un modello IT tradizionale, il team IT registra i costi e paga i costi da fondi condivisi, ad esempio operazioni e manutenzione (O & M) o un account dedicato di profitto e perdita (P & L).

In un modello di contabilità IT centrale, il team IT contrassegna i servizi forniti per tenere conto dell'overhead, della gestione e di altre spese stimate. Vengono quindi fatturate le unità aziendali in competizione per i servizi contrassegnati. In questo modello, il CIO deve gestire il P & L associato alla vendita di tali servizi. In questo modo è possibile creare costi e contesa IT tra l'IT centrale e le business unit, soprattutto quando è necessario ridurre i costi o non rispettare i contratti di contratto. Durante i periodi di variazione della tecnologia o del mercato, qualsiasi nuova tecnologia provocherebbe un'interferenza alla P & L centrale, rendendo difficoltosa la trasformazione.

## <a name="chargeback"></a>Chargeback

Uno dei primi passaggi comuni per la modifica della reputazione come centro di costo consiste nell'implementazione di un modello di chargeback di contabilità. Questo modello è particolarmente comune nelle aziende più piccole o nelle organizzazioni IT altamente efficienti. Nel modello di chargeback, qualsiasi costo IT associato a una specifica business unit viene considerato come una spesa operativa nel budget di tale business unit. Questa pratica riduce gli effetti di costi cumulativi su di essa, consentendo la visualizzazione dei valori aziendali in modo più chiaro.

In un modello locale legacy, è difficile realizzare il chargeback perché un utente deve ancora svolgere le spese di capitale e l'ammortamento di grandi dimensioni. La conversione continua da spese di capitale a spese operative associate all'utilizzo è un esercizio di contabilità difficile. Questa difficoltà rappresenta un motivo importante per la creazione del modello di contabilità IT tradizionale e del modello di contabilità IT centrale. Il modello di spese operative per la contabilità dei costi del cloud è quasi obbligatorio se si vuole fornire in modo efficiente un modello di chargeback.

Tuttavia, non è necessario implementare questo modello senza considerare le implicazioni. Di seguito sono riportate alcune conseguenze univoche per un modello di chargeback:

- Il chargeback comporta una riduzione massiccia del budget IT complessivo. Per le organizzazioni IT che risultano inefficienti o che richiedono complesse competenze tecniche per operazioni o manutenzione, questo modello può esporre tali spese in modo non integro.
- La perdita del controllo è una conseguenza comune. Negli ambienti altamente politici il chargeback può comportare la perdita del controllo e del personale riallocato al business. Questo potrebbe creare inefficienze significative e ridurre la capacità di soddisfare costantemente i contratti di contratto o i requisiti di progetto.
- La difficoltà di contabilità per i servizi condivisi è un'altra conseguenza comune. Se l'organizzazione è cresciuta attraverso l'acquisizione e comporta un debito tecnico, è probabile che venga mantenuta una percentuale elevata di servizi condivisi per mantenere tutti i sistemi in funzione.

Le trasformazioni Cloud includono soluzioni per queste e altre conseguenze associate a un modello di chargeback. Tuttavia, ognuna di queste soluzioni include l'implementazione e le spese operative. Il CIO e il CFO devono valutare attentamente i vantaggi e gli svantaggi di un modello di chargeback prima di prenderne in considerazione uno.

## <a name="showback-or-awareness-back"></a>Showback o Awareness-back

Per le aziende di grandi dimensioni, un modello di showback o di consapevolezza è un primo passaggio più sicuro nella transizione dal centro di costo al centro value. Questo modello non influisce sulla contabilità finanziaria. In realtà, la P & LS di ogni organizzazione non cambia. Il cambiamento più importante è la mentalità e la consapevolezza. In un modello di showback o di consapevolezza, gestisce la potenza di acquisto centralizzata e consolidata come agente per l'azienda. Nei report aziendali, attribuisce i costi diretti alla business unit pertinente, riducendo il budget percepito usato direttamente dall'IT. Inoltre, i budget vengono pianificati in base alle esigenze delle business unit associate, che consente di tenere in considerazione in modo più accurato i costi associati alle iniziative IT.

Questo modello offre un equilibrio tra un modello di chargeback reale e modelli di contabilità IT più tradizionali.

## <a name="impact-of-cloud-accounting-models"></a>Conseguenze dei modelli di accounting cloud

La scelta dei modelli di contabilità è fondamentale nella progettazione del sistema. La scelta del modello di contabilità può influire sulle strategie di sottoscrizione, gli standard di denominazione, gli standard di tag e i criteri e le progettazioni dei progetti.

Dopo aver collaborato con l'azienda per prendere decisioni su un modello di contabilità cloud e [sui mercati globali](global-markets.md), sono disponibili informazioni sufficienti per [sviluppare una base di Azure](../ready/index.md).

> [!div class="nextstepaction"]
> [Sviluppare una base di Azure](../ready/index.md)
