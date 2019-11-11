---
title: Procedure consigliate per la migrazione ad Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Introduzione alle procedure consigliate per la migrazione ad Azure
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 1519adff06d600b9829c9b7ff3ca82a0aa5a0160
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73753370"
---
# <a name="azure-migration-best-practices"></a>Procedure consigliate per la migrazione ad Azure

Azure offre diversi strumenti per facilitare i progetti di migrazione. Questa sezione di Cloud Adoption Framework è progettata per consentire ai lettori di implementare questi strumenti in linea con le procedure consigliate per la migrazione. Queste procedure consigliate sono allineate a uno dei processi all'interno del modello di migrazione di Cloud Adoption Framework illustrato di seguito.

Espandere un processo nel sommario a sinistra per vedere le procedure consigliate previste in genere da tale processo.

![Modello di migrazione di Cloud Adoption Framework](../../_images/operational-transformation-migrate.png)

> [!NOTE]
> La pianificazione del digital estate e la valutazione degli asset rappresentano due diversi livelli delle attività di pianificazione e valutazione per la migrazione:
>
> - **Pianificazione del digital estate:** durante la pianificazione occorre razionalizzare (pianificare) il digital estate per stabilire un backlog di migrazione globale. Questo piano si basa tuttavia su alcuni presupposti e dettagli che devono essere convalidati prima di poter eseguire la migrazione di un carico di lavoro.
> - **Valutazione degli asset:** è necessario valutare i singoli asset di un carico di lavoro prima della migrazione del carico di lavoro, per valutare la compatibilità con il cloud e comprendere i vincoli a livello di architettura e dimensioni. Questo processo convalida i presupposti iniziali e fornisce i dettagli necessari per eseguire la migrazione di un singolo asset.
