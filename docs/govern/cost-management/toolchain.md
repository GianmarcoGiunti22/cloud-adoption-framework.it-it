---
title: Strumenti per la gestione dei costi in Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Strumenti per la gestione dei costi in Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 3b301f8dfcc50539f4325901cd32553368a0da55
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71222645"
---
# <a name="cost-management-tools-in-azure"></a>Strumenti per la gestione dei costi in Azure

La [Gestione dei costi](./index.md) è una delle [cinque discipline della governance del cloud](../governance-disciplines.md). Questa disciplina è incentrata sui modi per stabilire piani di spesa per il cloud, allocare, monitorare e applicare i budget per il cloud, rilevare costose anomalie e modificare il piano di governance del cloud quando la spesa effettiva non è allineata.

Di seguito è riportato un elenco di strumenti nativi di Azure che possono aiutare a sviluppare i criteri e i processi che supportano la disciplina di governance.

| Tool | [Portale di Azure](https://azure.microsoft.com/features/azure-portal)  | [Gestione costi di Azure](https://docs.microsoft.com/azure/cost-management/overview-cost-mgt)  | [Pacchetto di contenuto per Azure con contratto Enterprise](https://docs.microsoft.com/power-bi/service-connect-to-azure-enterprise)  | [Criteri di Azure](https://docs.microsoft.com/azure/governance/policy/overview) |
|---------|---------|---------|---------|---------|
|Enterprise Agreement necessario?     | No         | No         | Yes         | No         |
|Controllo del budget     | No         | Yes         | No         | Yes         |
|Monitoraggio della spesa su singola risorsa    | Yes         | Yes         | Sì         | No         |
|Monitoraggio della spesa su più risorse    | No         | Yes        | Sì         | No         |
|Controllo della spesa su singola risorsa     | Sì, dimensionamento manuale         | Yes         | No         | Yes         |
|Imposizione della spesa su più risorse    | No         | Yes         | No         | Yes         |
|Applicare i metadati di contabilità sulle risorse    | No         | No         | No         | Yes         |
|Monitoraggio e rilevamento delle tendenze     | Yes          | Yes        | Sì         | No         |
|Rilevamento delle anomalie di spesa     | No         | Yes        | Sì         | No        |
|Socializzazione deviazioni     | No        | Yes        | Sì        | No        |
