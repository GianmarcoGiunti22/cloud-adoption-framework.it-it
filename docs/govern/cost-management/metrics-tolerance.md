---
title: Metriche della Gestione costi, indicatori e tolleranza ai rischi
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Spiegazione sulla Gestione costi in relazione alla governance cloud
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: be1d4456ac8924c87241089c637fa3aacc38fb47
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71029820"
---
# <a name="cost-management-metrics-indicators-and-risk-tolerance"></a>Metriche della Gestione costi, indicatori e tolleranza ai rischi

Questo articolo è concepito per aiutare l'utente a quantificare la tolleranza ai rischi aziendali, in relazione alla Gestione costi. La definizione di metriche e indicatori consente di creare un business case per effettuare un investimento riguardo alla disciplina Gestione costi.

## <a name="metrics"></a>metrics

Il servizio Gestione costi generalmente è incentrato sulle metriche relative ai costi. Come parte dell'analisi dei rischi, è necessario raccogliere dati relativi alle proprie spese correnti e pianificate sui carichi di lavoro basati sul cloud per determinare il livello di rischio da affrontare e quanto sia importante investire nella governance dei costi come strategia di adozione del cloud.

Di seguito sono riportati alcuni esempi di metriche utili da raccogliere per valutare la tolleranza ai rischi all'interno della disciplina di gestione dei costi:

- **Spesa annuale:** Costo annuo totale per i servizi forniti da un provider di servizi cloud.
- **Spesa mensile:** Costo mensile totale per i servizi forniti da un provider di servizi cloud.
- **Rapporto tra previsione e effettivo:** Rapporto che confronta la spesa prevista ed effettiva (mensile o annuale).
- **Rapporto ritmo di adozione (MOM):** Percentuale del Delta nei costi del cloud, dal mese al mese.
- **Costo accumulato:** Totale delle spese giornaliere maturate, a partire dall'inizio del mese.
- **Tendenze di spesa:** Tendenza di spesa rispetto al budget.

## <a name="risk-tolerance-indicators"></a>Indicatori sulla tolleranza ai rischi

Durante le prime distribuzioni di piccole dimensioni, ad esempio i carichi di lavoro di sviluppo/test o primitivi sperimentali, la gestione dei costi può avere un rischio relativamente basso. Dato che vengono distribuite più risorse, il rischio aumenta e la tolleranza delle aziende ai rischi probabilmente diminuisce. Inoltre, visto che altri team che adottano il cloud hanno la possibilità di configurare o distribuire le risorse nel cloud, il rischio aumenta e la tolleranza diminuisce. Al contrario, l'aumento della disciplina della Gestione costi porterà gli utenti dalla fase di adozione del cloud alla distribuzione di nuove tecnologie più innovative.

Nelle prime fasi di adozione del cloud, si dovrà stabilire una baseline di tolleranza ai rischi insieme alla propria azienda. Dopo aver creato una baseline, è necessario determinare i criteri che attiverebbero un investimento nella disciplina della Gestione costi. Questi criteri saranno probabilmente diversi per ogni organizzazione.

Dopo aver identificato [i rischi aziendali](./business-risks.md), si useranno con la propria azienda per identificare i benchmark che è possibile usare per identificare i trigger che potrebbero potenzialmente incrementare tali rischi. Sono indicati alcuni esempi del modo in cui le metriche, ad esempio quelle precedentemente indicate, possono essere confrontate con la tolleranza ai rischi della baseline per indicare la necessità dell'azienda di investire ancora di più in Gestione costi.

- **Basata sull'impegno (più comune):** Un'azienda che quest'anno s'impegna a spendere $ X.000.000 per un fornitore di cloud. È necessaria una disciplina di Gestione costi per assicurarsi che l'azienda non superi i relativi obiettivi di spesa di più del 20% e che venga usato almeno il 90% di tale impegno.
- **Trigger percentuale:** Un'azienda con una spesa per il cloud che è stabile per i sistemi di produzione. Se questa modifica è più che _x%_ , una disciplina di gestione dei costi sarà un investimento sapiente.
- **Trigger con provisioning eccessivo:** Una società che ritiene che le soluzioni distribuite abbiano un provisioning eccessivo. Gestione costi è un investimento prioritario fino a quando non è possibile illustrare l'allineamento corretto dell'uso di provisioning e risorse.
- **Trigger di spesa mensile:** Un'azienda che spende più di $ X.000 al mese, in cui tale importo viene considerato un costo considerevole. Se la spesa supera tale valore in un determinato mese, sarà necessario investire in Gestione costi.
- **Trigger di spesa annuale:** Un'azienda con un budget IT destinato a ricerca e sviluppo che consente una spesa annuale di $ X.000 nella sperimentazione di cloud. Possono eseguire carichi di lavoro di produzione nel cloud, ma vengono comunque considerati soluzioni sperimentali se il budget non supera tale importo. In caso di superamento, è necessario trattare il budget come un investimento di produzione e gestire la spesa minuziosamente.
- **Costo operativo-negativo (insolito):** Come società, sono contrarie alle spese operative e necessitano di controlli di gestione dei costi prima di distribuire un carico di lavoro di sviluppo/test.

## <a name="next-steps"></a>Passaggi successivi

Usare il [modello di gestione del cloud](./template.md) per documentare le metriche e gli indicatori di tolleranza in linea con il piano di adozione del cloud attuale.

Esaminare i criteri di gestione dei costi di esempio come punto di partenza per sviluppare criteri che risolvono i rischi aziendali specifici che si allineano ai piani di adozione del cloud.

> [!div class="nextstepaction"]
> [Esaminare i criteri di esempio](./policy-statements.md)
