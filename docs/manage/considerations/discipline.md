---
title: Livellamento della gestione tra le discipline di gestione del cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Questo articolo illustra il livellamento della gestione tra le discipline di gestione del cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 2e3aa2b27c503039d39bf3cc4a90b528f45d513e
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565173"
---
# <a name="management-leveling-across-cloud-management-disciplines"></a>Livellamento della gestione tra le discipline di gestione del cloud

Le chiavi per la corretta gestione in qualsiasi ambiente sono processi coerenti e ripetibili. Sono disponibili innumerevoli opzioni per le operazioni che possono essere eseguite in Azure. Analogamente, esistono innumerevoli approcci alla gestione del cloud. Per garantire coerenza e ripetibilità, è importante limitare tali opzioni a un set coerente di processi e strumenti di gestione che verranno offerti per i carichi di lavoro ospitati nel cloud.

## <a name="suggested-management-levels"></a>Livelli di gestione suggeriti

Poiché i carichi di lavoro nel portfolio IT variano, è improbabile che un singolo livello di gestione sarà sufficiente per ogni carico di lavoro. Per supportare un'ampia gamma di carichi di lavoro e impegni aziendali, è consigliabile che il team operativo cloud o il team operativo della piattaforma stabiliscano alcuni livelli di gestione delle operazioni.

![Gestire i livelli di gestione e la maturità nel Framework di adozione del cloud](../../_images/manage/cloud-management-maturity.png)

Come punto di partenza, prendere in considerazione la possibilità di stabilire i livelli di gestione mostrati nel diagramma precedente e suggeriti nell'elenco seguente:

- **Linea di base di gestione:** Una linea di base di gestione cloud (o una linea di base di gestione) è un set definito di strumenti, processi e prezzi coerenti che funge da base per tutta la gestione del cloud in Azure. Per stabilire una linea di base di gestione del cloud e determinare gli strumenti da includere nell'offerta di base per l'azienda, esaminare l'elenco nella sezione "discipline di gestione del cloud".
- **Baseline avanzata:** Alcuni carichi di lavoro possono richiedere miglioramenti alla baseline che non sono necessariamente specifici di una singola piattaforma o carico di lavoro. Anche se questi miglioramenti non sono convenienti per ogni carico di lavoro, devono essere presenti processi, strumenti e soluzioni comuni per qualsiasi carico di lavoro in grado di giustificare il costo del supporto di gestione aggiuntivo.
- **Specializzazione piattaforma:** In un determinato ambiente, alcune piattaforme comuni vengono usate da un'ampia gamma di carichi di lavoro. Questa comunanza architettonica generale non cambia quando le aziende adottano il cloud. La specializzazione della piattaforma è un livello elevato di gestione che applica i dati e le competenze in materia architettonica per fornire un livello superiore di gestione operativa. Esempi di specializzazione della piattaforma includono funzioni di gestione specifiche per SQL Server, contenitori, Active Directory o altri servizi che possono essere gestiti meglio tramite processi, strumenti e architetture coerenti e ripetibili.
- **Specializzazione del carico di lavoro:** Per i carichi di lavoro realmente cruciali, potrebbe essere necessario giustificare i costi per approfondire la gestione del carico di lavoro. La specializzazione del carico di lavoro applica la telemetria del carico di lavoro per determinare approcci più avanzati alla gestione Gli stessi dati spesso identificano i miglioramenti dell'automazione, della distribuzione e della progettazione che comportano maggiore stabilità, affidabilità e resilienza oltre quanto possibile con la gestione operativa da sola.
- Non **supportato:** È ugualmente importante comunicare processi di gestione comuni che non verranno distribuiti attraverso le discipline di gestione del cloud per i carichi di lavoro classificati come non supportati o non critici.

Le organizzazioni potrebbero anche scegliere di [esternalizzare le funzioni correlate a uno o più di questi livelli di gestione a un provider di servizi](https://www.microsoft.com/cloud-adoption-framework-offers?ot=manage). Questi provider di servizi possono usare [Azure Lighthouse](https://azure.com/lighthouse) per offrire maggiore precisione e trasparenza.

Gli articoli rimanenti di questa serie descrivono una serie di processi comunemente rilevati all'interno di ogni disciplina.
In parallelo, nella [Guida alla gestione di Azure](../azure-management-guide/index.md) vengono illustrati gli strumenti che possono supportare ognuno di questi processi. Per assistenza nella creazione di una linea di base di gestione, iniziare con la guida alla gestione di Azure. Una volta stabilita la linea di base, questa serie di articoli e le procedure consigliate complementari possono contribuire a espandere la baseline per definire altri livelli di supporto per la gestione.

## <a name="cloud-management-disciplines"></a>Discipline di gestione del cloud

Ogni livello di gestione suggerito può chiamare su un'ampia gamma di discipline di gestione del cloud. Tuttavia, il mapping è progettato per semplificare l'individuazione dei processi e degli strumenti suggeriti per fornire il livello appropriato di gestione del cloud.

Nella maggior parte dei casi, il *livello di base di riferimento di gestione* discusso in precedenza è costituito da processi e strumenti delle discipline seguenti. In ogni caso, vengono evidenziati alcuni processi e strumenti per illustrare le *funzioni di base avanzate*.

- **Inventario e visibilità:** Come minimo, una linea di base di gestione deve includere un mezzo per l'inventario delle risorse e la creazione della visibilità nello stato di esecuzione di ogni asset.
- **Conformità operativa:** Una gestione regolare di configurazione, ridimensionamento, costo e prestazioni delle risorse è fondamentale per mantenere le aspettative in termini di prestazioni e una linea di base di gestione.
- **Proteggi e Ripristina:** Ridurre al minimo le interruzioni operative e velocizzare il ripristino consente di evitare perdite di prestazioni e conseguenze dei ricavi. Il rilevamento e il ripristino sono aspetti essenziali di questa disciplina all'interno di qualsiasi linea di base di gestione.

Il livello di specializzazione della piattaforma di gestione esegue il pull dai processi e dagli strumenti allineati alle discipline delle operazioni della piattaforma. Analogamente, il livello di specializzazione del carico di lavoro estrae dai processi e dagli strumenti allineati con le discipline delle operazioni del carico di lavoro.

## <a name="next-steps"></a>Passaggi successivi

Il passaggio successivo verso la definizione di ogni livello di gestione del cloud è la comprensione dell' [inventario e della visibilità](./inventory.md).

> [!div class="nextstepaction"]
> [Opzioni di inventario e visibilità](./inventory.md)
