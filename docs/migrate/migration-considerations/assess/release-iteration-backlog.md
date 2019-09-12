---
title: Backlog di rilascio e iterazione
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Creazione di un backlog di rilascio e iterazione
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: dc567c80b6193d651c8bf3884476728a8d3daa7f
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70833479"
---
# <a name="manage-change-in-an-incremental-migration-effort"></a>Gestire le modifiche in un lavoro richiesto di migrazione incrementale

Questo articolo presuppone che i processi di migrazione siano di natura incrementale e che vengano eseguiti parallelamente al [processo di governance](../../../governance/index.md). Tuttavia, le stesse informazioni aggiuntive possono essere usate per popolare le attività iniziali in una struttura di suddivisione del lavoro per gli approcci tradizionali alla gestione delle modifiche a cascata.

## <a name="release-backlog"></a>Backlog di rilascio

Un *backlog di rilascio* è costituito da una serie di asset (VM, database, file e applicazioni, tra gli altri) di cui è necessario eseguire la migrazione prima che un carico di lavoro possa essere rilasciato per l'utilizzo in ambiente di produzione nel cloud. Durante ogni iterazione, il team di adozione del cloud documenta e stima il lavoro richiesto per spostare ogni asset nel cloud. Vedere la sezione "Backlog di iterazione" riportata di seguito.

## <a name="iteration-backlog"></a>Backlog di iterazione

Un *backlog di iterazione* è un elenco di operazioni dettagliate necessarie per eseguire la migrazione di un numero specifico di asset dal patrimonio digitale esistente al cloud. Le voci di questo elenco vengono spesso archiviate in uno strumento di gestione agile, ad esempio Azure DevOps, come elementi di lavoro.

Prima di avviare la prima iterazione, il team di adozione del cloud specifica una durata dell'iterazione, in genere da due a quattro settimane. Questa casella temporale è importante per creare un periodo di tempo di inizio e di fine per ogni set di attività di cui è stato eseguito il commit. La gestione di finestre di esecuzione coerenti semplifica la misurazione della velocità (velocità di migrazione) e l'allineamento alle esigenze aziendali in continua evoluzione.

Prima di ogni iterazione, il team esamina il backlog di rilascio, stimando il lavoro richiesto e le priorità degli asset da migrare. Viene quindi eseguito il commit per fornire un numero specifico di migrazioni concordate. Dopo che è stato accettato dal team di adozione del cloud, l'elenco delle attività diventa il *backlog di iterazione corrente*.

Durante ogni iterazione, i membri del team lavorano come un team di organizzazione automatica per soddisfare gli impegni nel backlog di iterazione attuale.

## <a name="next-steps"></a>Passaggi successivi

Dopo che un backlog di iterazione è stato definito e accettato dal team di adozione del cloud, è possibile finalizzare le [approvazioni della gestione del cambiamento](./approve.md).

> [!div class="nextstepaction"]
> [Approvare le modifiche all'architettura prima della migrazione](./approve.md)
