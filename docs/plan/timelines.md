---
title: Sequenze temporali in un piano di adozione del cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Sequenze temporali in un piano di adozione del cloud
author: BrianBlanchard
ms.author: brblanch
ms.date: 07/01/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: plan
ms.openlocfilehash: c5bafd4504a0df9570bf65846a5a077e54e158ca
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72549021"
---
# <a name="timelines-in-a-cloud-adoption-plan"></a>Sequenze temporali in un piano di adozione del cloud

Nell'articolo precedente di questa serie, i carichi di lavoro e le attività sono stati assegnati alle [versioni e alle iterazioni](./iteration-paths.md). Queste assegnazioni inseriscono le stime della sequenza temporale in questo articolo.

Le strutture di suddivisione dei lavori (WBS) sono comunemente usate negli strumenti sequenziali di gestione dei progetti. Rappresentano il modo in cui le attività dipendenti verranno completate nel tempo. Tali strutture funzionano correttamente quando le attività sono di natura sequenziale. Le interdipendenze nelle attività individuate nell'adozione del cloud rendono difficili la gestione di tali strutture. Per colmare questo gap, è possibile stimare le sequenze temporali in base alle assegnazioni di percorsi di iterazione nascondendo la complessità.

## <a name="estimate-timelines"></a>Stime temporali

Per sviluppare una sequenza temporale, iniziare con le versioni. Questi obiettivi di rilascio creano una data di destinazione per qualsiasi effetto aziendale. Le iterazioni facilitano l'allineamento di tali versioni con durate temporali specifiche.

Se nella sequenza temporale sono necessarie attività cardine più granulari, utilizzare l'assegnazione di iterazione per indicare le attività cardine. Per eseguire questa assegnazione, si supponga che l'ultima istanza di un'attività correlata al carico di lavoro possa fungere da attività cardine finale. I team di solito contrassegnano anche l'attività finale come un'attività cardine.

Per qualsiasi livello di granularità, utilizzare l'ultimo giorno dell'iterazione come data per ogni attività cardine. Questo associa il completamento dell'adozione del carico di lavoro a una data specifica. È possibile tenere traccia della data in un foglio di calcolo o in uno strumento di gestione dei progetti sequenziale come Microsoft Project.

## <a name="delivery-plans-in-azure-devops"></a>Piani di recapito in Azure DevOps

Se si usa Azure DevOps per gestire il piano di adozione del cloud, provare a usare l'estensione dei [piani di distribuzione Microsoft](https://marketplace.visualstudio.com/items?itemName=ms.vss-plans) . Questa estensione può creare rapidamente una rappresentazione visiva della sequenza temporale basata sulle assegnazioni di iterazione e rilascio.
