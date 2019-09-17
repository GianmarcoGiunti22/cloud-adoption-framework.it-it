---
title: 'Guida alla governance per le aziende complesse: Criteri aziendali iniziali per la strategia di governance'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Guida alla governance per le aziende complesse: Criteri aziendali iniziali per la strategia di governance'
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 2d8c2923820883561f75902830425b1bd81eb846
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71028992"
---
# <a name="governance-guide-for-complex-enterprises-initial-corporate-policy-behind-the-governance-strategy"></a>Guida alla governance per le aziende complesse: Criteri aziendali iniziali per la strategia di governance

I criteri aziendali seguenti definiscono la posizione di governance iniziale, che rappresenta il punto di partenza per questa guida. L'articolo definisce i rischi in fase iniziale, le istruzioni iniziali sui criteri e i processi anticipati per applicare le istruzioni dei criteri.

> [!NOTE]
>I criteri aziendali non costituiscono un documento tecnico, ma guidano molte decisioni tecniche. La governance MVP descritta nella [panoramica](./index.md) deriva in definitiva da questo criterio. Prima di implementare una governance MVP, l'organizzazione dovrebbe sviluppare un criterio aziendale in base ai propri obiettivi e rischi aziendali.

## <a name="cloud-governance-team"></a>Team di governance del cloud

Il CIO ha recentemente tenuto una riunione con il team di governance IT per comprendere la cronologia dei dati personali e i criteri cruciali ed esaminare l'effetto della modifica di tali criteri. Il CIO ha anche illustrato il potenziale globale del cloud per l'IT e la società.

Dopo la riunione, due membri del team IT di governance hanno richiesto l'autorizzazione per ricercare e supportare gli sforzi di pianificazione del cloud. Il direttore di governance IT ha supportato questo concetto, riconoscendo l'esigenza di governance e la possibilità per limitare lo shadow IT. A questo proposito, è Nato il team di governance del cloud. Nei mesi successivi, si erediterà la pulizia di molti errori commessi durante l'esplorazione nel cloud da una prospettiva di governance. Questo consentirà di ottenere loro il moniker dei _depositari del cloud_. Nelle iterazioni successive questa guida mostrerà come cambiano i loro ruoli nel tempo.

[!INCLUDE [business-risk](../../../../includes/business-risks.md)]

## <a name="tolerance-indicators"></a>Indicatori sulla tolleranza

L'attuale tolleranza ai rischi è elevata e il desiderio di investire nella governance cloud è basso. Di conseguenza, gli indicatori di tolleranza agiscono come un sistema di avviso preventivo per attivare l'investimento di tempo ed energia. Se vengono osservati gli indicatori seguenti, sarebbe opportuno avanzare la strategia di governance.

- **Gestione dei costi:** la scala di distribuzione supera le 1.000 risorse nel cloud oppure la spesa mensile supera i USD 10.000 al mese.
- **Linea di base identità:** Inclusione di applicazioni con requisiti di autenticazione a più fattori legacy o di terze parti.
- **Baseline di sicurezza:** inclusione dei dati protetti nei piani di adozione definiti per il cloud.
- **Coerenza delle risorse:** inclusione di tutte le applicazioni di importanza cruciale nei piani di adozione definiti per il cloud.

[!INCLUDE [policy-statements](../../../../includes/policy-statements.md)]

## <a name="next-steps"></a>Passaggi successivi

Questo criterio aziendale prepara il team di governance del cloud per implementare il MVP di governance, che sarà la base per l'adozione. Il passaggio successivo consiste nell'implementazione di tale MVP.

> [!div class="nextstepaction"]
> [Informazioni aggiuntive sulla descrizione](./prescriptive-guidance.md)
