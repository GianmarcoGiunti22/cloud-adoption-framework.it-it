---
title: 'Migrazione del mainframe: miti e fact'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni su come eseguire la migrazione di applicazioni da ambienti mainframe ad Azure, un'infrastruttura scalabile, collaudata e a disponibilità elevata per i sistemi attualmente in esecuzione su mainframe.
author: njray
ms.author: v-nanra
ms.date: 12/27/2018
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 4adf229b1ffca1d1360d197ab09a04f0d9584ef8
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72547908"
---
# <a name="mainframe-myths-and-facts"></a>Falsi miti e fatti sui mainframe

I mainframe hanno sempre rivestito una posizione di rilievo nella storia dell'informatica e restano una valida soluzione per carichi di lavoro estremamente specifici. La maggior parte degli utenti considera il mainframe una piattaforma collaudata con procedure operative consolidate che lo rendono un ambiente solido e affidabile. Il software viene eseguito in base all'utilizzo, misurato in milioni di istruzioni al secondo (MIPS) ed è disponibile un ampio report sull'utilizzo per i chargeback.

L'affidabilità, la disponibilità e la potenza di elaborazione dei mainframe hanno tuttavia adottato proporzioni quasi mitiche. Per valutare i carichi di lavoro mainframe più adatti per Azure, è necessario prima distinguere i falsi miti dalla realtà.

## <a name="myth-mainframes-never-go-down-and-have-a-minimum-of-five-9s-of-availability"></a>Mito: i mainframe non passano mai e hanno almeno cinque 9 di disponibilità

L'hardware e i sistemi operativi dei mainframe vengono considerati sempre stabili e affidabili. In realtà, tuttavia, è necessario pianificare periodi di inattività per interventi di manutenzione e operazioni di riavvio (denominate IPL: Initial Program Load). Quando vengono effettuate queste attività, una soluzione mainframe si attesta su una disponibilità di circa il 99-99,9%, pari a quella dei server Intel di fascia alta.

I mainframe, inoltre, rimangono vulnerabili alle situazioni di emergenza come qualsiasi altro server e richiedono un gruppo di continuità (UPS) per gestire questi tipi di eventi.

## <a name="myth-mainframes-have-limitless-scalability"></a>Mito: i mainframe hanno scalabilità illimitata

La scalabilità di un mainframe dipende dalla capacità del suo software di sistema, ad esempio il sistema di controllo delle informazioni del cliente (CICS) e la capacità di nuove istanze di motori e archiviazione del mainframe. Alcune grandi aziende che usano sistemi mainframe hanno personalizzato il software CICS per aumentarne le prestazioni, superando la capacità dei più grandi mainframe attualmente disponibili.

## <a name="myth-intel-based-servers-are-not-as-powerful-as-mainframes"></a>Mito: i server basati su Intel non sono potenti come i mainframe

I nuovi sistemi basati su Intel ad alta densità di core hanno una capacità di elaborazione equivalente a quella dei mainframe.

## <a name="myth-the-cloud-cant-accommodate-mission-critical-applications-for-large-companies-such-as-financial-institutions"></a>Mito: il cloud non può contenere applicazioni cruciali per aziende di grandi dimensioni, ad esempio istituti finanziari

Sebbene sia possibile che esistano alcune istanze isolate in cui le soluzioni cloud rientrino in breve, in genere è possibile che gli algoritmi dell'applicazione non siano distribuiti. Questi rari esempi costituiscono l'eccezione, non la regola.

## <a name="summary"></a>Summary

Per confronto, Azure offre una piattaforma alternativa in grado di offrire funzionalità e funzionalità mainframe equivalenti e a un costo molto più basso. Inoltre, il costo totale di proprietà (TCO) del modello di costo basato sulla sottoscrizione e sull'utilizzo del cloud è molto meno costoso dei computer mainframe.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Eseguire il passaggio dai mainframe ad Azure](./migration-strategies.md)
