---
title: Strumenti per la gestione dei costi in Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Strumenti per la gestione dei costi in Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 32c05e04c224f88008ded6e9fe2c69bb6095d346
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70828097"
---
# <a name="cost-management-tools-in-azure"></a>Strumenti per la gestione dei costi in Azure

La [Gestione dei costi](./index.md) è una delle [cinque discipline della governance del cloud](../governance-disciplines.md). Questa disciplina è incentrata sui modi per stabilire piani di spesa per il cloud, allocare, monitorare e applicare i budget per il cloud, rilevare costose anomalie e modificare il piano di governance del cloud quando la spesa effettiva non è allineata.

Di seguito è riportato un elenco di strumenti nativi di Azure che possono aiutare a sviluppare i criteri e i processi che supportano la disciplina di governance.

| Strumento | [Portale di Azure](https://azure.microsoft.com/features/azure-portal)  | [Gestione costi di Azure](/azure/cost-management/overview-cost-mgt)  | [Pacchetto di contenuto per Azure con contratto Enterprise](/power-bi/service-connect-to-azure-enterprise)  | [Criteri di Azure](/azure/governance/policy/overview) |
|---------|---------|---------|---------|---------|
|Enterprise Agreement necessario?     | No         | No         | Sì         | No         |
|Controllo del budget     | No         | Sì         | No         | Sì         |
|Monitoraggio della spesa su singola risorsa    | Yes         | Sì         | Sì         | No         |
|Monitoraggio della spesa su più risorse    | No         | Yes        | Sì         | No         |
|Controllo della spesa su singola risorsa     | Sì, dimensionamento manuale         | Sì         | No         | Sì         |
|Imposizione della spesa su più risorse    | No         | Sì         | No         | Sì         |
|Applicare i metadati di contabilità sulle risorse    | No         | No         | No         | Sì         |
|Monitoraggio e rilevamento delle tendenze     | Sì, limitato         | Yes        | Sì         | No         |
|Rilevamento delle anomalie di spesa     | No         | Yes        | Sì         | No        |
|Socializzazione deviazioni     | No        | Yes        | Sì        | No        |
