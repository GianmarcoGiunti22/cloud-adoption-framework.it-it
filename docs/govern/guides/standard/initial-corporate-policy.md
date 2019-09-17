---
title: 'Guida aziendale standard: Criteri aziendali iniziali per la strategia di governance'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Guida aziendale standard: Criteri aziendali iniziali per la strategia di governance'
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/05/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 4da4899038ca86bec2f1d003f9eaaee293119a09
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71027963"
---
# <a name="standard-enterprise-guide-initial-corporate-policy-behind-the-governance-strategy"></a>Guida aziendale standard: Criteri aziendali iniziali per la strategia di governance

I criteri aziendali seguenti definiscono una posizione di governance iniziale, che rappresenta il punto di partenza per questa guida. L'articolo definisce i rischi in fase iniziale, le istruzioni iniziali sui criteri e i processi anticipati per applicare le istruzioni dei criteri.

> [!NOTE]
>I criteri aziendali non costituiscono un documento tecnico, ma guidano molte decisioni tecniche. La governance MVP descritta nella [panoramica](./index.md) deriva in definitiva da questo criterio. Prima di implementare una governance MVP, l'organizzazione dovrebbe sviluppare un criterio aziendale in base ai propri obiettivi e rischi aziendali.

## <a name="cloud-governance-team"></a>Team di governance del cloud

In questo racconto, il team di governance del cloud è costituito da due amministratori di sistema che hanno riconosciuto la necessità di governance. Nei prossimi mesi verranno ereditati i processi di pulizia della governance della presenza nel cloud dell'azienda, ottenendo loro il titolo dei _depositari del cloud_. Nelle iterazioni successive questo titolo cambierà probabilmente.

[!INCLUDE [business-risk](../../../../includes/business-risks.md)]

## <a name="tolerance-indicators"></a>Indicatori sulla tolleranza

L'attuale tolleranza ai rischi è elevata e il desiderio di investire nella governance cloud è basso. Di conseguenza, gli indicatori di tolleranza agiscono come un sistema di avviso preventivo per attivare più investimenti di tempo ed energia. Se e quando vengono osservati gli indicatori seguenti, è necessario migliorare in modo iterativo la strategia di governance.

- **Gestione dei costi:** La scala di distribuzione supera le 100 risorse nel cloud oppure la spesa mensile supera i 1.000 USD al mese.
- **Baseline di sicurezza:** inclusione dei dati protetti nei piani di adozione definiti per il cloud.
- **Coerenza delle risorse:** inclusione di tutte le applicazioni di importanza cruciale nei piani di adozione definiti per il cloud.

[!INCLUDE [policy-statements](../../../../includes/policy-statements.md)]

## <a name="next-steps"></a>Passaggi successivi

Questo criterio aziendale prepara il team di governance del cloud per implementare il MVP di governance, che sarà la base per l'adozione. Il passaggio successivo consiste nell'implementazione di tale MVP.

> [!div class="nextstepaction"]
> [Informazioni aggiuntive sulla descrizione](./prescriptive-guidance.md)
