---
title: Livellamento della gestione tra le discipline di gestione del cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Livellamento della gestione tra le discipline di gestione del cloud
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/07/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 0517816bd01221da8f5b4d97cc40dd39f4599b5e
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72557570"
---
# <a name="management-leveling-across-cloud-management-disciplines"></a>Livellamento della gestione tra le discipline di gestione del cloud

La chiave per una corretta gestione in qualsiasi ambiente è la coerenza e i processi ripetibili. Sono disponibili innumerevoli opzioni per le operazioni che possono essere eseguite in Azure. Analogamente, esistono innumerevoli approcci alla gestione del cloud. Per garantire coerenza e ripetibilità, è importante limitare tali opzioni a un set coerente di processi e strumenti di gestione che verranno offerti per i carichi di lavoro ospitati nel cloud.

## <a name="suggested-management-levels"></a>Livelli di gestione suggeriti

Poiché i carichi di lavoro nel portfolio IT non sono tutti uguali, è improbabile che un singolo livello di gestione sarà sufficiente per ogni carico di lavoro. Per supportare vari carichi di lavoro e diversi impegni aziendali, è consigliabile che il team operativo cloud o le operazioni della piattaforma stabiliscano alcuni livelli di gestione delle operazioni.

![Gestire i livelli di gestione e la maturità nel Framework di adozione del cloud](../../_images/manage/cloud-management-maturity.png)

I livelli di gestione seguenti (anche illustrati sopra) sono alcuni livelli suggeriti per fungere da punto di partenza:

- **Linea di base di gestione**: una linea di base di gestione cloud (o una linea di base di gestione) è la serie definita di strumenti, processi e prezzi coerenti che fungeranno da base per tutte le operazioni di gestione del cloud in Azure. Per stabilire una linea di base di gestione cloud, vedere la tabella nella sezione seguente e determinare gli strumenti che verranno inclusi nell'offerta di base per l'azienda.
- **Baseline avanzata**: un numero di carichi di lavoro può richiedere miglioramenti alla baseline che non sono necessariamente specifici di una singola piattaforma o carico di lavoro. Anche se questi miglioramenti non sono convenienti per ogni carico di lavoro, è necessario disporre di processi, strumenti e soluzioni comuni per qualsiasi carico di lavoro che possa giustificare il supporto di gestione aggiuntivo.
- **Specializzazione della piattaforma**: in un determinato ambiente sono disponibili piattaforme comuni utilizzate da più carichi di lavoro diversi. Questa comunanza architettonica generale non cambia quando le aziende adottano il cloud. La specializzazione della piattaforma è un livello elevato di gestione che sfrutta i dati e le competenze in materia architettonica per fornire un livello superiore di gestione operativa. Esempi di specializzazione della piattaforma includono funzioni di gestione specifiche per SQL Server, contenitori, Active Directory o altri servizi che possono essere gestiti meglio tramite processi, strumenti e architetture coerenti e ripetibili.
- **Specializzazione del carico**di lavoro: per i carichi di lavoro realmente cruciali, potrebbe essere necessario giustificare i costi per approfondire la gestione del carico di lavoro. La specializzazione dei carichi di lavoro usa la telemetria del carico di lavoro per determinare approcci più avanzati alla gestione giornaliera Gli stessi dati spesso identificano i miglioramenti dell'automazione, della distribuzione e della progettazione che comportano maggiore stabilità, affidabilità e resilienza oltre ciò che è possibile con la gestione operativa da solo.
- Non **supportata**: è ugualmente importante comunicare processi di gestione comuni che non verranno distribuiti attraverso le discipline di gestione del cloud per qualsiasi carico di lavoro classificato come non supportato o non critico.

Gli articoli rimanenti di questa serie delineano una serie di processi comunemente rilevati all'interno di ogni disciplina.
In parallelo, nella [Guida alla gestione di Azure](../azure-management-guide/index.md) vengono illustrati gli strumenti che possono supportare ognuno di questi processi. Per assistenza nella creazione di una linea di base di gestione, iniziare dalla guida alla gestione di Azure. Una volta stabilita la linea di base, questa serie di articoli e le procedure consigliate complementari possono contribuire a espandere la baseline per definire altri livelli di supporto per la gestione.

## <a name="cloud-management-disciplines"></a>Discipline di gestione del cloud

Ognuno dei livelli di gestione suggeriti può chiamare diverse discipline di gestione del cloud. Tuttavia, il mapping è progettato per semplificare l'individuazione dei processi e degli strumenti suggeriti per fornire il livello appropriato di gestione del cloud.

Nella maggior parte dei casi, il "livello di base di gestione" descritto in precedenza è costituito da processi e strumenti delle discipline seguenti. In ogni caso, vengono evidenziati alcuni processi e strumenti per dimostrare "funzioni di base avanzate".

- **Inventario e visibilità**: come minimo, una linea di base di gestione deve includere un mezzo per l'inventario delle risorse e la creazione della visibilità nello stato di esecuzione di ogni asset.
- **Conformità operativa:** Una gestione regolare di configurazione, ridimensionamento, costo e prestazioni delle risorse è fondamentale per mantenere le aspettative in termini di prestazioni e una linea di base di gestione.
- **Proteggi e Ripristina:** Riducendo al minimo le interruzioni operative e velocizzando il ripristino, è possibile evitare perdite di prestazioni e conseguenze dei ricavi. Il rilevamento e il ripristino sono aspetti essenziali di questa disciplina all'interno di qualsiasi linea di base di gestione.

Il livello di specializzazione della piattaforma di gestione esegue il pull dai processi e dagli strumenti allineati alle discipline delle operazioni della piattaforma.
Analogamente, il livello di specializzazione del carico di lavoro estrae dai processi e dagli strumenti allineati alle discipline delle operazioni del carico di lavoro.
  
## <a name="next-steps"></a>Passaggi successivi

Il passaggio successivo verso la definizione di ogni livello di gestione del cloud è la comprensione dell' [inventario e della visibilità](./inventory.md).

> [!div class="nextstepaction"]
> [Opzioni di inventario e visibilità](./inventory.md)
