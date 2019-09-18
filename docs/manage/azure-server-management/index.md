---
title: Panoramica dei servizi di gestione del server di Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Introduzione ai servizi di gestione del server di Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 4d1ada9d47e54f4b0d3828ce93b2d55f3eda8a34
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71026265"
---
# <a name="overview-of-azure-server-management-services"></a>Panoramica dei servizi di gestione del server di Azure

I servizi di gestione del server di Azure offrono ai clienti un'esperienza coerente per la gestione i server su larga scala. Questi servizi riguardano i sistemi operativi sia Linux che Windows e possono essere usati in ambienti di produzione, sviluppo e test. Possono inoltre supportare macchine virtuali IaaS di Azure, nonché server fisici e macchine virtuali ospitati in locale o in altri ambienti di hosting. 

Nel gruppo di servizi di gestione dei server di Azure sono inclusi i servizi illustrati nel diagramma seguente. 

![Diagramma del modello delle operazioni di Azure](./media/operations-diagram.png)

Le indicazioni fornite in questa sezione di Microsoft Cloud Adoption Framework costituiscono un piano pratico e attuabile per la distribuzione dei servizi di gestione dei server nell'ambiente. L'obiettivo di questo piano è aiutare a orientarsi rapidamente tra questi servizi grazie a un set incrementale di fasi di gestione per ambienti di qualsiasi dimensione.

Per semplicità, queste indicazioni sono state organizzate in tre fasi:

![Le tre fasi dell'onboarding del gruppo di servizi di gestione del server di Azure](./media/operations-stages.png)

<!-- markdownlint-disable MD026 -->

## <a name="why-use-azure-management-services"></a>Perché usare i servizi di gestione di Azure?

I servizi di gestione di Azure offrono i vantaggi seguenti:

- **Nativi di Azure.** I servizi di gestione sono predefiniti e integrati in modalità nativa con Azure Resource Manager. Questi servizi vengono costantemente migliorati per offrire nuove funzionalità.
- **Windows e Linux.** I computer Windows e Linux offrono la stessa esperienza di gestione coerente.
- **Ibrido.** I servizi di gestione riguardano macchine virtuali IaaS di Azure, nonché server fisici e virtuali ospitati in locale o in altri ambienti di hosting.
- **Sicurezza.** Microsoft dedica ingenti risorse a tutte le forme di sicurezza. Questo investimento non consente solo di proteggere l'infrastruttura cloud di Azure, ma di estendere anche le tecnologie e le competenze risultanti necessarie per proteggere le risorse dei clienti ovunque si trovino.

## <a name="next-steps"></a>Passaggi successivi

Acquisire familiarità con gli [strumenti, servizi e pianificazione](./prerequisites.md) connessi al gruppo di servizi di gestione del server di Azure.

> [!div class="nextstepaction"]
> [Pianificazione e strumenti prerequisiti](./prerequisites.md)
