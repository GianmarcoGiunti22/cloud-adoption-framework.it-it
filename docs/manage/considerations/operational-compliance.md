---
title: Conformità operativa-gestione cloud e operazioni
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Conformità operativa-gestione cloud e operazioni
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/07/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 524f5f63dd6bf5fa99d8677fde06346d2a0c1902
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72557531"
---
# <a name="operational-compliance-in-cloud-management"></a>Conformità operativa in gestione cloud

La conformità operativa si basa sulla disciplina dell' [inventario e della visibilità](./inventory.md), come primo passaggio praticabile della gestione del cloud. Questa disciplina è incentrata sulle normali verifiche di telemetria e sulle attività correttive, sia proattive che correttive. Questa disciplina rappresenta l'elemento fondamentale per mantenere il giusto equilibrio tra sicurezza, governance, prestazioni e costi.

## <a name="components-of-operations-compliance"></a>Componenti della conformità delle operazioni

Il mantenimento della conformità agli impegni operativi richiede l'analisi, l'automazione e la correzione umana. Una conformità operativa efficace richiede la coerenza in alcuni processi critici:

1. Coerenza delle risorse
2. Coerenza dell'ambiente
3. Coerenza di configurazione delle risorse
4. Coerenza aggiornamenti
5. Automazione della correzione

### <a name="resource-consistency"></a>Coerenza delle risorse

Il passaggio più efficace che un team di gestione cloud può adottare per la conformità operativa consiste nel definire la coerenza nell'organizzazione e nell'assegnazione di tag. Quando le risorse vengono organizzate e contrassegnate in modo coerente, tutte le altre attività operative diventano più semplici. Per informazioni più dettagliate sulla coerenza delle risorse, vedere la [fase di governance](../../govern/index.md) del ciclo di vita dell'adozione del cloud. In particolare, gli [articoli iniziali di governance Foundation](../../govern/initial-foundation.md) illustrano esempi di modi per iniziare a sviluppare la coerenza delle risorse.

### <a name="environment-consistency"></a>Coerenza dell'ambiente

Gli ambienti coerenti o le zone di destinazione sono il passaggio più importante successivo alla conformità operativa. Quando le zone di destinazione sono coerenti e applicate tramite strumenti automatici, è molto meno complessa diagnosticare e risolvere i problemi operativi. Per informazioni più dettagliate sulla coerenza dell'ambiente, vedere la [fase di preparazione](../../ready/index.md) del ciclo di vita dell'adozione del cloud. Gli esercizi in questa fase stabiliscono un processo ripetibile per la definizione e la maturazione di un approccio coerente e Code-First allo sviluppo di ambienti basati su cloud.

### <a name="resource-configuration-consistency"></a>Coerenza di configurazione delle risorse

Basandosi sugli approcci di governance e conformità, la gestione del cloud deve includere processi per il monitoraggio e la valutazione continui dell'aderenza ai requisiti di coerenza delle risorse. Quando i carichi di lavoro cambiano o vengono apportate nuove versioni, è fondamentale che i processi di gestione cloud valutino eventuali modifiche di configurazione, che non sono facilmente regolate tramite mezzi automatici.

Quando vengono individuate incoerenze, alcune vengono risolte in base alla coerenza degli aggiornamenti e altre possono essere corrette automaticamente.

### <a name="update-consistency"></a>Coerenza aggiornamenti

La stabilità può condurre a operazioni stabili. Tuttavia, alcune modifiche sono necessarie nei processi di gestione del cloud. In particolare, le normali modifiche alle patch e alle prestazioni sono essenziali per ridurre le interruzioni e controllare i costi.

Uno dei molti valori di una metodologia di gestione cloud matura è la stabilizzazione e il controllo delle modifiche necessarie.

Qualsiasi linea di base di gestione del cloud deve includere un mezzo per pianificare, controllare ed eventualmente automatizzare gli aggiornamenti necessari. Questi aggiornamenti devono includere almeno le patch, ma possono includere anche le prestazioni, il ridimensionamento e altri aspetti dell'aggiornamento degli asset.

### <a name="remediation-automation"></a>Automazione della correzione

Come base avanzata per la gestione del cloud, alcuni carichi di lavoro possono trarre vantaggio dalla correzione automatica. Quando un carico di lavoro rileva in genere problemi che non possono essere risolti tramite modifiche del codice o dell'architettura, l'automazione della correzione può ridurre il carico di gestione del cloud e migliorare la soddisfazione degli utenti.

Molti sostengono che qualsiasi problema, che è abbastanza comune da automatizzare, deve essere risolto tramite la risoluzione del debito tecnico. Quando la risoluzione a lungo termine è prudente, dovrebbe essere l'opzione predefinita. Esistono tuttavia diversi scenari aziendali che rendono difficile giustificare investimenti di grandi dimensioni nella risoluzione del debito tecnico. Quando la risoluzione del debito tecnico non può essere giustificata, ma la correzione è un onere comune e costoso, la correzione automatica è la soluzione migliore.

## <a name="next-steps"></a>Passaggi successivi

La [protezione e il ripristino](./protect.md) sono le aree successive da considerare in una linea di base di gestione del cloud.

> [!div class="nextstepaction"]
> [Proteggi e ripristina](./protect.md)
