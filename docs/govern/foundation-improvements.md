---
title: Migliora la tua fondazione cloud governance iniziale
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Scopri come migliorare in modo incrementale la tua fondazione cloud governance iniziale.
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/13/2019
ms.topic: landing-page
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
layout: LandingPage
ms.openlocfilehash: d7e4c0516e1c52f1fc6ddd8b42485902cb24d58e
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71223648"
---
# <a name="improve-your-initial-cloud-governance-foundation"></a>Migliora la tua fondazione cloud governance iniziale

Questo articolo presuppone che sia stata stabilita una [Fondazione cloud governance iniziale](./initial-foundation.md). Quando si implementa il piano di adozione del cloud, emergono rischi tangibili dagli approcci proposti per i quali i team vogliono adottare il cloud. Dato che questi rischi emergono nelle conversazioni di pianificazione della versione, usare la griglia seguente per identificare rapidamente alcune procedure consigliate per ottenere il piano di adozione per evitare che i rischi diventino minacce reali.

## <a name="maturity-vectors"></a>Vettori di maturità

In qualsiasi momento, è possibile applicare le seguenti linee guida per la governance iniziale per risolvere il rischio o la necessità indicata nella tabella riportata di seguito.

> [!IMPORTANT]
> L'organizzazione delle risorse può influire sul modo in cui viene applicata questa guida prescrittiva. È importante iniziare con le raccomandazioni che meglio si allineano con la base di governance cloud iniziale implementata nel passaggio precedente.

|Rischio/necessità | Azienda standard | Azienda complessa |
|---|---|---|
|Dati sensibili nel cloud|[Linee guida per la scrittura](./guides/standard/security-baseline-improvement.md)|[Linee guida per la scrittura](./guides/complex/security-baseline-improvement.md)|
|App mission-critical nel cloud|[Linee guida per la scrittura](./guides/standard/resource-consistency-improvement.md)|[Linee guida per la scrittura](./guides/complex/resource-consistency-improvement.md)|
|Gestione dei costi del cloud|[Linee guida per la scrittura](./guides/standard/cost-management-improvement.md)|[Linee guida per la scrittura](./guides/complex/cost-management-improvement.md)|
|Multi-cloud|[Linee guida per la scrittura](./guides/standard/multicloud-improvement.md)|[Linee guida per la scrittura](./guides/complex/multicloud-improvement.md)|
|Gestione delle identità complessa/legacy|N/D|[Linee guida per la scrittura](./guides/complex/identity-baseline-improvement.md)|
|Più livelli di governance|N/D|[Linee guida per la scrittura](./guides/complex/multiple-layers-of-governance.md)|

## <a name="next-steps"></a>Passaggi successivi

Oltre all'applicazione di istruzioni specifiche, la metodologia di governance nel Framework di adozione del cloud può essere personalizzata per adattarsi a vincoli aziendali univoci. Dopo aver seguito le raccomandazioni applicabili, [valutare i criteri aziendali per comprendere ulteriori requisiti di personalizzazione](./corporate-policy.md).

> [!div class="nextstepaction"]
> [Valutare i criteri aziendali](./corporate-policy.md)
