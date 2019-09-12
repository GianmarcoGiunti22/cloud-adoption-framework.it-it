---
title: Informazioni aggiuntive per il test aziendale (test di accettazione utente) durante la migrazione
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Processo nell'ambito della migrazione nel cloud che è incentrato sulle attività di migrazione dei carichi di lavoro nel cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 0f1ba39ae283b1ab2fdb276310a9490af6bf87b7
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70825510"
---
# <a name="guidance-for-business-testing-uat-during-migration"></a>Informazioni aggiuntive per il test aziendale (test di accettazione utente) durante la migrazione

Tradizionalmente considerata come funzione IT, il test di accettazione utenti durante una trasformazione aziendale può essere orchestrato esclusivamente dal team IT. Questa funzione, tuttavia, viene spesso eseguita in modo più efficace come funzione aziendale. Il team IT supporta quindi questa attività aziendale facilitando il test, sviluppando piani di test e automatizzando i test quando possibile. Sebbene l'IT possa spesso fungere da surrogato per il test, non vi è alcun sostituto per l'osservazione diretta degli utenti reali che tentano di sfruttare una nuova soluzione nel contesto di un processo aziendale reale o replicato.

> [!NOTE]
> Se disponibile, il test automatizzato è un mezzo più efficace ed efficiente per testare qualsiasi sistema. Tuttavia, le migrazioni cloud spesso si concentrano principalmente sui sistemi legacy o sui sistemi di produzione almeno stabili. Spesso questi sistemi non sono gestiti da test automatizzati accurati e ben gestiti. Questo articolo presuppone che tali test non siano disponibili al momento della migrazione.

In secondo luogo, i test automatizzati sono test delle modifiche apportate alla tecnologia e ai processi da parte degli utenti. Gli utenti esperti sono persone che in genere eseguono un processo reale che richiede interazioni con uno strumento tecnologico o un set di strumenti. Potrebbero essere rappresentati da un cliente esterno che usa un sito di e-commerce per acquisire beni o servizi. Gli utenti esperti possono anche essere rappresentati da un gruppo di dipendenti che esegue un processo aziendale, ad esempio un call center che assiste i clienti e registra le proprie esperienze.

L'obiettivo del test aziendale è sollecitare la convalida da parte degli utenti esperti per certificare che la nuova soluzione è in linea con le aspettative e non ostacola i processi aziendali. Se tale obiettivo non viene soddisfatto, il test aziendale funge da ciclo di feedback che consente di definire il motivo e il modo in cui il carico di lavoro non soddisfa le aspettative.

## <a name="business-activities-during-business-testing"></a>Attività aziendali durante i test aziendali

Durante i test aziendali, la prima iterazione viene gestita manualmente, direttamente con i clienti. Questa è la forma più semplice, ma più dispendiosa in termini di tempo del ciclo di feedback.

- **Identificare gli utenti avanzati.** L'azienda ha in genere un migliore riconoscimento degli utenti esperti più interessati da una modifica tecnica.
- **Allineare e preparare gli utenti avanzati.** Assicurarsi che gli utenti esperti conoscano gli obiettivi aziendali, i risultati desiderati e le modifiche previste ai processi aziendali. Preparare loro e la loro struttura di gestione per il processo di test.
- **Partecipare nell'interpretazione del ciclo di feedback.** Aiutare il personale IT a comprendere l'effetto dei diversi punti di feedback degli utenti esperti.
- **Chiarire la modifica al processo.** Quando la trasformazione può attivare una modifica ai processi aziendali, comunicare la modifica e qualsiasi impatto downstream.
- **Assegnare priorità ai feedback.** Consentire al team IT di assegnare priorità ai feedback in base all'impatto aziendale.

In alcuni casi, il team IT può utilizzare analisti o proprietari del prodotto che possono fungere da proxy per le attività di test aziendale dettagliate. Tuttavia, la partecipazione aziendale è caldamente consigliata ed è probabile che produca risultati aziendali favorevoli.

## <a name="it-activities-during-business-testing"></a>Attività IT durante i test aziendali

Il team IT è uno dei destinatari dell'output dei test aziendali. I cicli di feedback esposti durante i test aziendali diventano elementi di lavoro che definiscono modifiche tecniche o modifiche ai processi. In qualità di destinatario, si prevede che il team IT contribuisca alla facilitazione, alla raccolta di feedback e alla gestione delle azioni tecniche conseguenti. Le attività tipiche che esegue il team IT durante i test aziendali includono:

- Fornire la struttura e la logistica per i test aziendali.
- Agevolare i test.
- Fornire un mezzo e un processo per la registrazione del feedback.
- Consentire all'azienda di definire le priorità e convalidare il feedback.
- Sviluppare piani per agire su modifiche tecniche.
- Identificare i test automatizzati esistenti che possono semplificare il test da parte di utenti esperti.
- Per le modifiche che potrebbero richiedere una distribuzione o un test ripetuti, studiare i processi di test, definire i benchmark e creare l'automazione per semplificare ulteriormente i test dell'utente.

## <a name="next-steps"></a>Passaggi successivi

Insieme ai test aziendali, [l'ottimizzazione degli asset migrati](./optimize.md) può migliorare le prestazioni dei costi e del carico di lavoro.

> [!div class="nextstepaction"]
> [Valutare e ridimensionare gli asset cloud](./optimize.md)
