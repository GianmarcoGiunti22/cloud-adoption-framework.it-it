---
title: 'Guida alla gestione di Azure: Prima di iniziare'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Istruzioni dettagliate per la gestione delle operazioni di Azure.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.custom: fasttrack-edit, AQC
ms.localizationpriority: high
ms.openlocfilehash: 58a01e02abad2de68fac9a94d2a2aa3ad22d32a1
ms.sourcegitcommit: 910efd3e686bd6b9bf93951d84253b43d4cc82b5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72769157"
---
::: zone target="docs"

# <a name="azure-management-guide-before-you-start"></a>Guida alla gestione di Azure: Prima di iniziare

> [!NOTE]
> Questa guida rappresenta un punto di partenza per le linee guida per l'innovazione presenti in Cloud Adoption Framework. È anche disponibile nel Centro di avvio rapido di Azure. Per un collegamento al Centro di avvio rapido di Azure, vedere il suggerimento più avanti.

::: zone-end

::: zone target="chromeless"

# <a name="before-you-start"></a>Prima di iniziare

::: zone-end

La Guida alla gestione di Azure è stata pensata per assistere i clienti attivi di Azure nella creazione di una baseline di gestione per stabilire la coerenza delle risorse all'interno di Azure. La guida descrive gli strumenti di base necessari per qualsiasi ambiente di Azure, in particolare quelli che ospitano dati sensibili. Per altre informazioni, procedure consigliate e considerazioni correlate alla preparazione dell'ambiente cloud, vedere la [sezione sull'idoneità di Cloud Adoption Framework](../index.md).

## <a name="scope-of-this-guide"></a>Ambito della guida

Questa guida illustra come definire gli strumenti per la baseline di gestione. Descrive anche come estendere la baseline o sviluppare ulteriore resilienza.

> [!div class="checklist"]
>
> - **Inventario e visibilità:** creare un inventario di asset tra più cloud. Sviluppare visibilità sullo stato di ogni asset.
> - **Conformità operativa:** stabilire controlli e processi per assicurare che ogni stato venga configurato correttamente e sia eseguito in un ambiente ben regolamentato.
> - **Protezione e ripristino:** assicurare che tutti gli asset gestiti siano protetti e possano essere ripristinati con gli strumenti di gestione della baseline.
> - **Opzioni ottimizzate della baseline:** valutare le comuni aggiunte alla baseline che possano soddisfare le esigenze aziendali.
> - **Operazioni della piattaforma:** estendere la baseline di gestione con un catalogo di servizi ben definito e piattaforme gestite centralmente.
> - **Operazioni per i carichi di lavoro:** estendere la baseline di gestione per includere negli obiettivi i carichi di lavoro cruciali.

## <a name="management-baseline"></a>Baseline di gestione

La baseline di gestione è costituita dal set minimo di strumenti e processi da applicare a ogni asset dell'ambiente. È possibile aggiungervi diverse altre opzioni. Gli articoli successivi descrivono come accelerare le funzionalità di gestione del cloud concentrandosi sulle opzioni minime necessarie invece che su tutte quelle disponibili.

::: zone target="docs"

> [!TIP]
> Per un'esperienza interattiva, visualizzare questa guida nel portale di Azure. Passare al [Centro di avvio rapido di Azure](https://portal.azure.com/?feature.quickstart=true#blade/Microsoft_Azure_Resources/QuickstartCenterBlade) nel portale di Azure e selezionare la **Guida alla gestione di Azure**. Seguire quindi le istruzioni dettagliate.

Passaggi successivi: [Inventario e visibilità](./inventory.md)

::: zone-end

::: zone target="chromeless"

Questa guida offre i passaggi interattivi che permettono di provare le funzionalità man mano che vengono introdotte. Per tornare al punto in cui ci si è fermati, usare il percorso di navigazione.

::: zone-end