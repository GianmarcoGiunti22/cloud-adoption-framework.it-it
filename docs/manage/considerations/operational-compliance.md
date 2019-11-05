---
title: Conformità operativa-gestione cloud e operazioni
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Conformità operativa-gestione cloud e operazioni
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 507f0360636e0c56c771a6afa5fd767a42581af3
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565098"
---
# <a name="operational-compliance-in-cloud-management"></a>Conformità operativa in gestione cloud

La conformità operativa si basa sulla disciplina dell' [inventario e della visibilità](./inventory.md). Come primo passaggio praticabile della gestione del cloud, questa disciplina è incentrata sulle normali verifiche di telemetria e sulle attività correttive (sia proattive che correttive). Questa disciplina rappresenta l'elemento fondamentale per mantenere il giusto equilibrio tra sicurezza, governance, prestazioni e costi.

## <a name="components-of-operations-compliance"></a>Componenti della conformità delle operazioni

Mantenere la conformità con gli impegni operativi richiede l'analisi, l'automazione e la correzione umana. Una conformità operativa efficace richiede la coerenza in alcuni processi critici:

- Coerenza delle risorse
- Coerenza dell'ambiente
- Coerenza di configurazione delle risorse
- Coerenza aggiornamenti
- Automazione della correzione

### <a name="resource-consistency"></a>Coerenza delle risorse

Il passaggio più efficace che un team di gestione cloud può intraprendere rispetto alla conformità operativa consiste nel definire la coerenza nell'organizzazione delle risorse e nell'assegnazione di tag. Quando le risorse vengono organizzate e contrassegnate in modo coerente, tutte le altre attività operative diventano più semplici. Per informazioni più dettagliate sulla coerenza delle risorse, vedere la [fase di governance](../../govern/index.md) del ciclo di vita dell'adozione del cloud. In particolare, gli [articoli iniziali di governance Foundation](../../govern/initial-foundation.md) dimostrano come iniziare a sviluppare la coerenza delle risorse.

### <a name="environment-consistency"></a>Coerenza dell'ambiente

La creazione di ambienti coerenti, o zone di destinazione, è il passaggio più importante alla conformità operativa. Quando le zone di destinazione sono coerenti e applicate tramite strumenti automatici, è molto meno complessa diagnosticare e risolvere i problemi operativi. Per informazioni più dettagliate sulla coerenza dell'ambiente, vedere la [fase di preparazione](../../ready/index.md) del ciclo di vita dell'adozione del cloud. Gli esercizi in questa fase consentono di creare un processo ripetibile per la definizione e la maturazione di un approccio coerente e basato sul codice per lo sviluppo di ambienti basati sul cloud.

### <a name="resource-configuration-consistency"></a>Coerenza di configurazione delle risorse

Poiché si basa sugli approcci di governance e conformità, la gestione del cloud deve includere i processi per il monitoraggio e la valutazione continui dell'aderenza ai requisiti di coerenza delle risorse. Quando i carichi di lavoro cambiano o vengono apportate nuove versioni, è fondamentale che i processi di gestione cloud valutino eventuali modifiche di configurazione, che non sono facilmente regolate tramite l'automazione.

Quando vengono individuate incoerenze, alcune vengono risolte in base alla coerenza degli aggiornamenti e altre possono essere corrette automaticamente.

### <a name="update-consistency"></a>Coerenza aggiornamenti

La stabilità nell'approccio può condurre a operazioni più stabili. Tuttavia, alcune modifiche sono necessarie nei processi di gestione del cloud. In particolare, le normali modifiche alle patch e alle prestazioni sono essenziali per ridurre le interruzioni e controllare i costi.

Uno dei molti valori di una metodologia di gestione cloud matura è l'obiettivo di stabilizzare e controllare le modifiche necessarie.

Qualsiasi linea di base di gestione del cloud deve includere un mezzo per pianificare, controllare ed eventualmente automatizzare gli aggiornamenti necessari. Questi aggiornamenti devono includere almeno le patch, ma possono includere anche le prestazioni, il ridimensionamento e altri aspetti dell'aggiornamento degli asset.

### <a name="remediation-automation"></a>Automazione della correzione

Come base avanzata per la gestione del cloud, alcuni carichi di lavoro possono trarre vantaggio dalla correzione automatica. Quando un carico di lavoro rileva in genere problemi che non possono essere risolti tramite modifiche del codice o dell'architettura, l'automazione della correzione può contribuire a ridurre il carico di gestione del cloud e a migliorare la soddisfazione degli utenti.

Molti sostengono che qualsiasi problema comune da automatizzare dovrebbe essere risolto tramite la risoluzione del debito tecnico. Quando una risoluzione a lungo termine è prudente, dovrebbe essere l'opzione predefinita. Tuttavia, una serie di scenari aziendali rende difficile giustificare investimenti di grandi dimensioni nella risoluzione del debito tecnico. Quando una risoluzione di questo tipo non può essere giustificata, ma la correzione è un onere comune e costoso, la correzione automatica è la soluzione migliore.

## <a name="next-steps"></a>Passaggi successivi

La [protezione e il ripristino](./protect.md) sono le aree successive da considerare in una linea di base di gestione del cloud.

> [!div class="nextstepaction"]
> [Proteggi e ripristina](./protect.md)
