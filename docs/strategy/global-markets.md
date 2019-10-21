---
title: Comprendere l'effetto delle decisioni sul mercato globale
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Spiegazione del concetto di mercati globali
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: strategy
ms.openlocfilehash: 36f0d5ccf826746370054ed213b83968babdee6b
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72548613"
---
<!-- markdownlint-disable MD026 -->

# <a name="how-will-global-market-decisions-affect-the-transformation-journey"></a>In che modo le decisioni sul mercato globale avranno effetto sul percorso di trasformazione?

Il cloud offre nuove opportunità di esecuzione su scala globale. Le barriere alle operazioni globali sono significativamente ridotte, consentendo alle aziende di distribuire le risorse sul mercato, senza dover investire molto nei nuovi Data Center. Sfortunatamente, questo aggiunge anche una grande quantità di complessità dalle prospettive tecniche e legali.

## <a name="data-sovereignty"></a>Sovranità dei dati

Molte aree geopolitiche hanno stabilito normative sulla sovranità dei dati. Queste normative limitano la posizione in cui possono essere archiviati i dati, i dati che possono uscire dal paese di origine e i dati che possono essere raccolti per i cittadini di tale area. Prima di utilizzare qualsiasi soluzione basata sul cloud in una geografia esterna, è necessario comprendere in che modo il provider di cloud gestisce la sovranità dei dati. Altre informazioni sull'approccio di Azure per ogni geografia sono disponibili [qui](https://azure.microsoft.com/global-infrastructure/geographies). Per ulteriori informazioni sulla conformità in Azure, vedere [privacy presso Microsoft](https://www.microsoft.com/trustcenter/privacy) nel centro protezione Microsoft.

Nella parte restante di questo articolo si presuppone che il Consiglio legale abbia esaminato e approvato le operazioni in un paese esterno.

## <a name="business-units"></a>Business Unit

È importante comprendere quali business unit operano in paesi stranieri e quali paesi sono interessati. Queste informazioni verranno usate per progettare soluzioni per l'hosting, la fatturazione e le distribuzioni nel provider di servizi cloud.

## <a name="employee-usage-patterns"></a>Modelli di utilizzo dei dipendenti

È importante comprendere in che modo gli utenti globali accedono alle applicazioni non ospitate nello stesso paese dell'utente. Le reti WAN globali indirizzano gli utenti in base ai contratti di rete esistenti. In un mondo locale tradizionale, alcuni vincoli limitano la progettazione WAN. Questi vincoli possono comportare esperienze utente insoddisfacenti se non sono stati riconosciuti correttamente prima dell'adozione del cloud.

In un modello cloud, Internet per le nuove opzioni offre anche numerose nuove opzioni. La comunicazione tra la diffusione dei dipendenti in più aree geografiche può aiutare il team di adozione del cloud a progettare soluzioni WAN che creano esperienze utente positive **e** potenziali costi di rete.

## <a name="external-user-usage-patterns"></a>Modelli di utilizzo dell'utente esterno

È ugualmente importante comprendere i modelli di utilizzo degli utenti esterni, ad esempio clienti o partner. Analogamente ai modelli di utilizzo dei dipendenti, i modelli di utilizzo degli utenti esterni possono influire negativamente sulle prestazioni delle distribuzioni cloud. Quando una base di utenti di grandi dimensioni o di importanza critica risiede in un paese esterno, potrebbe essere opportuno includere una strategia di distribuzione globale nella progettazione complessiva della soluzione.

## <a name="next-steps"></a>Passaggi successivi

Una volta che le decisioni di mercato globali sono state prese e comunicate, il team è pronto per iniziare a [definire standard tecnici](../digital-estate/index.md) in base a tali metriche.
Il risultato sarà un [backlog di trasformazione o di migrazione](..//migrate/migration-considerations/prerequisites/technical-complexity.md).

> [!div class="nextstepaction"]
> [Valutazione del patrimonio digitale](../digital-estate/index.md)
