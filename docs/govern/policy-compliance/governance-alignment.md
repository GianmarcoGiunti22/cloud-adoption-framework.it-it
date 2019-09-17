---
title: Allinea la guida alla progettazione della governance del cloud con i criteri aziendali
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Allinea la guida alla progettazione della governance del cloud con i criteri aziendali
author: BrianBlanchard
ms.author: brblanch
ms.date: 01/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.openlocfilehash: c7be14efe6723a32808ba9bd2ba01f48292305df
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71029192"
---
<!---
I've established policies. How to help developers adopt these policies?
Draft an architecture design guide.

[Aspirational statement] If you're using Azure, you can use one of ours as a starting point. The choose one of the following 6 as a starting point and mold it to fit your policies.
--->

# <a name="align-your-cloud-governance-design-guide-with-corporate-policy"></a>Allinea la guida alla progettazione della governance del cloud con i criteri aziendali

Dopo aver [definito i criteri del cloud](./policy-definition.md) in base ai [rischi identificati](./business-risk.md), è necessario generare una guida operativa che si allinei con questi criteri a cui il personale IT e gli sviluppatori devono fare riferimento. La stesura di una guida alla progettazione della governance del cloud consente di specificare scelte strutturali, tecnologiche ed elaborate specifiche in base alle istruzioni dei criteri generate per ognuna delle [cinque discipline di governance](../governance-disciplines.md).

Una guida alla progettazione della governance del cloud deve stabilire le scelte di architettura e gli schemi progettuali per ognuna delle componenti fondamentali dell'infrastruttura delle distribuzioni del cloud che meglio soddisfano i requisiti dei criteri. Assieme a questi è necessario fornire una spiegazione di alto livello della tecnologia, degli strumenti e dei processi che supportano ognuna di queste decisioni di progettazione.

Sebbene l'analisi dei rischi e le istruzioni dei criteri possano, a un certo livello, essere indipendenti dalla piattaforma cloud, la guida alla progettazione dovrebbe fornire dettagli di implementazione specifici della piattaforma che i team IT e dev possono usare per la creazione e la distribuzione di carichi di lavoro basati sul cloud. Concentrarsi sull'architettura, le funzioni e le caratteristiche della piattaforma scelta quando si prendono decisioni di progettazione e si fornisce materiale sussidiario.

Anche se le guide alla progettazione del cloud dovrebbero tenere conto di alcuni dettagli tecnici associati a ogni componente dell'infrastruttura, non sono intese come documenti tecnici o specifiche estese. Assicurati che le tue guide affrontino le istruzioni dei criteri e indichino chiaramente le decisioni di progettazione in un formato semplice da comprendere e fare riferimento al personale.

<!-- markdownlint-enable MD033 -->

## <a name="using-the-actionable-governance-guides"></a>Uso delle guide di governance di utilità pratica

Se si prevede di usare la piattaforma Azure per l'adozione del cloud, il Framework di adozione del cloud fornisce [guide di governance](../guides/index.md) di utilità pratica che illustrano l'approccio incrementale del modello di governance del Framework di adozione del cloud. Queste guide illustrano un'ampia gamma di scenari di adozione comuni, inclusi i rischi aziendali, i requisiti di tolleranza e le istruzioni per i criteri che sono stati creati per la creazione di un prodotto di governance minimo valido (MVP). Queste guide rappresentano una sintesi dell'esperienza del cliente nel mondo reale del processo di adozione del cloud in Azure.

Sebbene ogni adozione del cloud abbia obiettivi, priorità e sfide uniche, questi esempi dovrebbero fornire un modello ottimale per la conversione dei criteri in materiale sussidiario. Selezionare lo scenario più vicino alla propria situazione come punto iniziale in modo da soddisfare le proprie esigenze specifiche in ambito di criteri.

## <a name="next-steps"></a>Passaggi successivi

Servirsi della guida alla progettazione stabilire i processi di adesione ai criteri per garantirne la conformità.

> [!div class="nextstepaction"]
> [Stabilire processi di conformità ai criteri](./processes.md)
