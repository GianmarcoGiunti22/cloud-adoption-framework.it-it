---
title: 'Guida alla governance per le aziende complesse: criteri aziendali iniziali dietro la strategia di governance'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Guida alla governance per le aziende complesse: criteri aziendali iniziali dietro la strategia di governance'
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 56629e6f313614965ee1baddaa08e4264b4bef53
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72547676"
---
# <a name="governance-guide-for-complex-enterprises-initial-corporate-policy-behind-the-governance-strategy"></a>Guida alla governance per le aziende complesse: criteri aziendali iniziali dietro la strategia di governance

I criteri aziendali seguenti definiscono la posizione di governance iniziale, che rappresenta il punto di partenza per questa guida. L'articolo definisce i rischi in fase iniziale, le istruzioni iniziali sui criteri e i processi anticipati per applicare le istruzioni dei criteri.

> [!NOTE]
>I criteri aziendali non costituiscono un documento tecnico, ma guidano molte decisioni tecniche. La governance MVP descritta nella [panoramica](./index.md) deriva in definitiva da questo criterio. Prima di implementare una governance MVP, l'organizzazione dovrebbe sviluppare un criterio aziendale in base ai propri obiettivi e rischi aziendali.

## <a name="cloud-governance-team"></a>Team di governance del cloud

Il CIO ha recentemente tenuto una riunione con il team di governance IT per comprendere la cronologia dei dati personali e i criteri cruciali ed esaminare l'effetto della modifica di tali criteri. Il CIO ha anche illustrato il potenziale globale del cloud per l'IT e la società.

Dopo la riunione, due membri del team IT di governance hanno richiesto l'autorizzazione per ricercare e supportare gli sforzi di pianificazione del cloud. Il direttore di governance IT ha supportato questo concetto, riconoscendo l'esigenza di governance e la possibilità per limitare lo shadow IT. A questo proposito, è Nato il team di governance del cloud. Nei mesi successivi, si erediterà la pulizia di molti errori commessi durante l'esplorazione nel cloud da una prospettiva di governance. Questo consentirà di ottenere loro il moniker dei _depositari del cloud_. Nelle iterazioni successive questa guida mostrerà come cambiano i loro ruoli nel tempo.

[!INCLUDE [business-risk](../../../../includes/business-risks.md)]

## <a name="tolerance-indicators"></a>Indicatori sulla tolleranza

L'attuale tolleranza ai rischi è elevata e il desiderio di investire nella governance cloud è basso. Di conseguenza, gli indicatori di tolleranza agiscono come un sistema di avviso preventivo per attivare l'investimento di tempo ed energia. Se vengono osservati gli indicatori seguenti, sarebbe opportuno avanzare la strategia di governance.

- **Gestione dei costi:** La scalabilità della distribuzione supera gli asset 1.000 al cloud o la spesa mensile supera $10.000 USD al mese.
- **Linea di base identità:** Inclusione di applicazioni con requisiti di autenticazione a più fattori legacy o di terze parti.
- **Baseline di sicurezza:** Inclusione di dati protetti nei piani di adozione del cloud definiti.
- **Coerenza delle risorse:** Inclusione di applicazioni cruciali nei piani di adozione del cloud definiti.

[!INCLUDE [policy-statements](../../../../includes/policy-statements.md)]

## <a name="next-steps"></a>Passaggi successivi

Questo criterio aziendale prepara il team di governance del cloud per implementare il MVP di governance, che sarà la base per l'adozione. Il passaggio successivo consiste nell'implementazione di tale MVP.

> [!div class="nextstepaction"]
> [Procedure consigliate illustrate](./prescriptive-guidance.md)
