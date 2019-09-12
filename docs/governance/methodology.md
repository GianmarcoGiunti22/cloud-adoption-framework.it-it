---
title: Metodologia di governance cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Acquisire le nozioni di base della metodologia alla base della governance del cloud in Cloud Adoption Framework.
author: BrianBlanchard
ms.author: brblanch
ms.date: 07/04/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: organize
ms.custom: organize
ms.openlocfilehash: 43a03112342534a995dae3386b55ac1d98122b50
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70827122"
---
# <a name="cloud-governance-methodology"></a>Metodologia di governance cloud

L'adozione del cloud è un viaggio, non una destinazione. Lungo il percorso, si incontrano fasi cardine chiare e vantaggi aziendali concreti. Lo stato finale di adozione del cloud è tuttavia sconosciuto all'azienda al momento di intraprendere il viaggio. La governance del cloud definisce le misure cautelative, ovvero i guardrail che mantengono l'azienda su un percorso sicuro per l'intero viaggio.

Il Framework di adozione del cloud fornisce guide di governance che descrivono le esperienze di società fittizie, basate sulle esperienze dei clienti reali. Ogni guida segue il cliente attraverso i vari aspetti della governance per l'adozione del cloud.

## <a name="envision-an-end-state"></a>Prevedere uno stato finale

Un viaggio senza una destinazione è semplice vagabondare. È importante stabilire una visione approssimativa dello stato finale prima di partire. L'infografica seguente offre una cornice di riferimento per lo stato finale. Non è il punto di partenza, ma mostra la potenziale destinazione.

![Infografica del modello di governance di Cloud Adoption Framework](../_images/operational-transformation-govern-highres.png)

Il modello di governance di Cloud Adoption Framework identifica le principali aree rilevanti durante il percorso. Ogni area è correlata ai tipi di rischi diversi che la società deve affrontare man mano che adotta ulteriori servizi cloud. All'interno di questo framework, la guida alla governance identifica le azioni necessarie per il team di governance del cloud. Lungo il percorso viene descritto in maggiore dettaglio ogni principio del modello di governance di Cloud Adoption Framework. In generale, sono inclusi i principi seguenti:

**Criteri aziendali**. I criteri aziendali sono alla base della governance del cloud. La guida alla governance è incentrata su specifici aspetti dei criteri aziendali:

- **Rischi aziendali:** identificare e conoscere i rischi aziendali.
- **Criteri e conformità:** convertire i rischi in definizioni dei criteri che supportano eventuali requisiti di conformità.
- **Processi:** garantire la conformità ai criteri definiti.

**Cinque discipline della governance del cloud**. Queste discipline supportano i criteri aziendali. Ogni disciplina consente di proteggere l'azienda da potenziali insidie:

- Gestione dei costi
- Baseline di sicurezza
- Coerenza delle risorse
- Baseline di identità
- Accelerazione della distribuzione

In pratica, i criteri aziendali fungono da sistema di preavviso per rilevare potenziali problemi. Le discipline aiutano l'azienda a gestire i rischi e definire misure cautelative.

## <a name="grow-to-the-end-state"></a>Crescita fino allo stato finale

I requisiti di governance cambiano lungo l'intero percorso di adozione del cloud, quindi è necessario adottare un approccio diverso. Le aziende non possono più aspettare che un piccolo team crei i guardrail e le mappe per ogni autostrada *prima di affrontare la prima tappa*. È previsto che i risultati aziendali arrivino più rapidamente e con maggiore fluidità. La governance IT deve anche prevedere reazioni rapide e restare al passo con le esigenze aziendali per mantenere coerenza durante l'adozione del cloud ed evitare il "shadow IT".

Un approccio di **governance incrementale** supporta questi requisiti. La governance incrementale si basa su un piccolo set di criteri, processi e strumenti aziendali per gettare le fondamenta per l'adozione e la governance. Queste fondamenta sono note come **prodotto minimo funzionante (MVP, Minimum Viable Product)** . Un MVP consente al team di governance di incorporare velocemente la governance nelle implementazioni per l'intero ciclo di vita di adozione. È possibile stabilire un MVP in qualsiasi momento durante il processo di adozione del cloud. Tuttavia, è consigliabile adottare un MVP il prima possibile.

La possibilità di rispondere rapidamente a rischi mutevoli offre al team di governance del cloud l'opportunità di agire in modi nuovi. Il team di governance del cloud può unirsi al team di strategia del cloud per agire come esploratori in avanscoperta rispetto ai team di adozione del cloud, per tracciare la rotta e stabilire velocemente le misure cautelative necessarie per gestire i rischi associati ai piani di adozione. Questi livelli di governance JIT sono noti come **iterazioni della governance**. Con questo approccio, la crescita della strategia di governance è un passo avanti rispetto ai team di adozione del cloud.

Il diagramma seguente mostra un semplice MVP per la governance e tre iterazioni. Durante le iterazioni vengono definiti criteri aziendali aggiuntivi per la gestione di nuovi rischi. La disciplina Accelerazione della distribuzione applica quindi tali variazioni a ogni distribuzione.

![Esempio di miglioramento incrementale della governance](../_images/governance/incremental-governance-example.png)

> [!NOTE]
> La governance non è da intendersi come sostituto di funzioni chiave come sicurezza, rete, identità, finanza, DevOps o operazioni. Lungo il percorso vi saranno interazioni e dipendenze con i membri di ogni funzione. Tali membri dovrebbero essere inclusi nel team di governance del cloud per accelerare decisioni e azioni.

## <a name="next-steps"></a>Passaggi successivi

Usare lo [strumento di benchmark della governance](https://cafbaseline.com) del Framework di adozione cloud per valutare il percorso di trasformazione e semplificare l'identificazione dei gap nell'organizzazione in sei domini chiave, come definito nel Framework.

> [!div class="nextstepaction"]
> [Valutare il percorso di trasformazione](./benchmark.md)
