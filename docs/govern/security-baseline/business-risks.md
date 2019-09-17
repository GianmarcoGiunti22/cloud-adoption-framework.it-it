---
title: Motivazioni e rischi aziendali della Baseline di sicurezza
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Motivazioni e rischi aziendali della Baseline di sicurezza
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: a77df6b190db7f9fd5f44e233e175670ff7f4855
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71027774"
---
# <a name="security-baseline-motivations-and-business-risks"></a>Motivazioni e rischi aziendali della Baseline di sicurezza

Questo articolo illustra i motivi per cui i clienti in genere adottano la disciplina Baseline di sicurezza all'interno di una strategia di governance del cloud. Offre inoltre alcuni esempi di rischi aziendali potenziali che possono determinare le istruzioni dei criteri.

<!-- markdownlint-disable MD026 -->

## <a name="is-a-security-baseline-relevant"></a>È rilevante per la Baseline di sicurezza?

La sicurezza è un aspetto chiave per qualsiasi organizzazione IT. Le distribuzioni cloud affrontano molti degli stessi rischi per la sicurezza dei carichi di lavoro ospitati nei data center locali tradizionali. Tuttavia, la natura delle piattaforme cloud pubbliche che non sono direttamente proprietarie dell'hardware fisico che archivia ed esegue i carichi di lavoro, fa sì che che la sicurezza del cloud necessiti di criteri e processi propri.

Uno degli elementi principali che consente di impostare la governance della sicurezza nel cloud oltre ai criteri di sicurezza tradizionali è la facilità con cui è possibile creare risorse, aggiungendo potenzialmente vulnerabilità se la sicurezza non viene considerata prima della distribuzione. La flessibilità offerta da tecnologie come le [software defined networking (SDN)](../../decision-guides/software-defined-network/index.md) (soluzioni di rete basate sul software), che permette di cambiare rapidamente la topologia di rete basata su cloud, può tuttavia anche modificare facilmente e in modi imprevisti la superficie complessiva dell'attacco di rete. Le piattaforme cloud offrono inoltre strumenti e funzionalità che consentono di migliorare le funzionalità di sicurezza in modi che non sono sempre disponibili in ambienti locali.

Quanto viene investito nei criteri di sicurezza e nei processi dipende molto dalla natura della distribuzione del cloud. Le distribuzioni dei test iniziali potrebbero richiedere solo i criteri di sicurezza di base, mentre un carico di lavoro cruciale comporterà la necessità di soddisfare esigenze di sicurezza complesse ed estese. Tutte le distribuzioni dovranno coinvolgere la disciplina, a un certo livello.

La disciplina Baseline di sicurezza illustra i criteri aziendali e i processi manuali che è possibile mettere in atto per proteggere la distribuzione del cloud contro i rischi per la sicurezza.

> [!NOTE]
>Sebbene sia importante capire la [Baseline di identità](../identity-baseline/index.md) nel contesto della Baseline di sicurezza e come ciò si lega al Servizio di controllo di accesso, è bene sottolineare che le [cinque discipline della governance del cloud](../index.md) considerano la [Baseline di identità](../identity-baseline/index.md) come una disciplina a sé, che non fa parte della Baseline di sicurezza.

## <a name="business-risk"></a>Rischio aziendale

La disciplina Baseline di sicurezza tenta di affrontare ai principali rischi per la sicurezza aziendale. Collaborare con l'azienda per identificare questi rischi e monitorarne la rilevanza durante la pianificazione e l'implementazione delle distribuzioni cloud.

I rischi si differenziano per l'organizzazione, ma gli elementi seguenti rappresentano i rischi comuni relativi alla sicurezza che è possibile utilizzare come punto di partenza per le discussioni all'interno del team di governance del cloud:

- **Violazione dei dati:** L'esposizione o la perdita accidentale di dati sensibili ospitati nel cloud può comportare la perdita di clienti, problemi contrattuali o ripercussioni legali.
- **Interrompi servizio:** Le interruzioni e altri problemi di prestazione dovuti a un'infrastruttura non protetta, interrompono le normali operazioni e possono comportare la perdita di produttività o di fatturato.

## <a name="next-steps"></a>Passaggi successivi

Usando il [modello di gestione cloud](./template.md), documentare i rischi aziendali che probabilmente verranno introdotti dal piano di adozione del Cloud corrente.

Dopo aver stabilito in modo realistico i rischi aziendali, il passaggio successivo consiste nel documentare le metriche e gli indicatori principali della tolleranza ai rischi dell'azienda allo scopo di monitorare tale tolleranza.

> [!div class="nextstepaction"]
> [Indicatori, metriche e tolleranza ai rischi](./metrics-tolerance.md)
