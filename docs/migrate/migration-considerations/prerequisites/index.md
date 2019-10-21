---
title: Prerequisiti per la migrazione
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Prerequisiti per la migrazione
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: ce4cf827f391c5fb15f6b9e78997dd0f02e1751b
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/21/2019
ms.locfileid: "72683785"
---
# <a name="prerequisites-for-migration"></a>Prerequisiti per la migrazione

Prima di avviare qualsiasi migrazione, l'_ambiente_ di destinazione della migrazione deve essere preparato per le modifiche future. In questo caso, con ambiente si intendono le fondamenta tecniche nel cloud. Ambiente significa anche l'ambiente aziendale e la mentalità che promuove la migrazione. Analogamente, l'ambiente include la cultura dei team che eseguono le modifiche e di quelli che ricevono l'output. La mancanza di preparazione per queste modifiche è il motivo più comune di insuccesso delle migrazioni. Questa serie di articoli illustra i prerequisiti consigliati per preparare l'ambiente.

## <a name="objective"></a>Obiettivo

Verificare la preparazione e l'idoneità a livello aziendale, culturale e tecnico prima di avviare un piano di migrazione iterativo.

## <a name="review-business-drivers"></a>Esaminare le motivazioni aziendali

Prima di avviare qualsiasi progetto di migrazione al cloud, vedere le linee guida per la [pianificazione](../../../strategy/index.md) e i [preparativi](../../../ready/index.md) in Cloud Adoption Framework per assicurarsi che l'organizzazione sia pronta per i processi di adozione del cloud e migrazione. In particolare, esaminare i requisiti aziendali e i risultati previsti alla base della scelta di procedere alla migrazione:

- [Introduzione: migrazione](../../../getting-started/migrate.md)
- [Why are we moving to the cloud?](../../../strategy/motivations.md) (Motivi per passare al cloud)

## <a name="definition-of-done"></a>Definizione di *completato*

I prerequisiti si considerano completati in presenza delle condizioni seguenti:

- **Idoneità aziendale.** Il team di strategia del cloud ha definito un backlog di migrazione di alto livello, classificandone anche le priorità, che rappresenta la parte del digital estate di cui eseguire la migrazione entro i due o tre rilasci successivi. Il team di strategia del cloud e il team di adozione del cloud hanno concordato una strategia iniziale per la gestione delle modifiche.
- **Idoneità culturale.** I ruoli, le responsabilità e le aspettative del team di adozione del cloud, del team di strategia del cloud e degli utenti interessati sono stati concordati in relazione ai carichi di lavoro di cui eseguire la migrazione entro i due o tre rilasci successivi.
- **Idoneità tecnica.** L'area di destinazione (ovvero lo spazio di hosting allocato nel cloud) che riceverà gli asset migrati soddisfa i requisiti minimi per ospitare il primo carico di lavoro migrato.

> [!CAUTION]
> La preparazione è fondamentale per il successo di una migrazione. Un eccesso di preparativi, tuttavia, può causare la *paralisi da analisi*, in cui il troppo tempo dedicato alla pianificazione può ritardare significativamente un progetto di migrazione. I processi e i prerequisiti definiti in questa sezione sono concepiti per facilitare il processo decisionale, ma è importante evitare che impediscano di fare progressi significativi.
>
> Scegliere un carico di lavoro relativamente semplice per la migrazione iniziale. Usare i processi illustrati in questa sezione durante la pianificazione e l'implementazione di questa prima migrazione. Questo primo progetto di migrazione offrirà velocemente al team una dimostrazione dei principi del cloud e obbligherà il team a scoprire di più sul funzionamento del cloud. Man mano che il team acquisisce esperienza, le lezioni apprese possono essere integrate per intraprendere migrazioni più estese e più complesse.

## <a name="accountability-during-prerequisites"></a>Team responsabili nella fase dei prerequisiti

Due team sono responsabili dell'idoneità durante la fase dei prerequisiti:

- **Team di strategia del cloud** Questo team è responsabile dell'identificazione e dell'assegnazione delle priorità per primi due o tre carichi di lavoro da usare come candidati per la migrazione.
- **Team di adozione del cloud** Questo team è responsabile della convalida dell'idoneità dell'ambiente tecnico e della fattibilità della migrazione dei carichi di lavoro proposti.

Un singolo membro di ogni team deve essere identificato come responsabile per ognuna delle tre definizioni di completato nella sezione precedente.

## <a name="responsibilities-during-prerequisites"></a>Responsabilità durante la fase dei prerequisiti

Oltre alle responsabilità di alto livello, esistono azioni per cui un singolo utente o un gruppo deve essere direttamente responsabile. Di seguito vengono descritte alcune di tali responsabilità con effetti su queste attività:

- **Assegnazione delle priorità aziendali.** Prendere decisioni aziendali relative ai carichi di lavoro di cui eseguire la migrazione e ai vincoli di tempo generali. Per altre informazioni, vedere [Motivazioni aziendali della migrazione al cloud](../../../strategy/motivations.md).
- **Idoneità per la gestione delle modifiche.** Definire e comunicare il piano per tenere traccia delle modifiche tecniche durante la migrazione.
- **Allineamento degli utenti aziendali.** Elaborare un piano per preparare la comunità degli utenti aziendali per l'esecuzione della migrazione.
- **Inventario e analisi del digital estate.** Esecuzione degli strumenti necessari per creare un inventario e analizzare il digital estate. Per altre informazioni, vedere gli articoli di Cloud Adoption Framework dedicati al [digital estate](../../../digital-estate/index.md).
- **Idoneità del cloud.** Valutare l'ambiente di distribuzione di destinazione per assicurarsi che sia conforme ai requisiti dei primi carichi di lavoro candidati. Vedere la [Guida alla configurazione di Azure](../../../ready/azure-setup-guide/index.md) per altre informazioni.

Gli articoli rimanenti di questa serie sono utili per l'esecuzione di ognuna di queste attività.

## <a name="next-steps"></a>Passaggi successivi

Con una conoscenza generale dei prerequisiti si è pronti per procedere con il primo requisito, ovvero le [decisioni preliminari per la migrazione](./decisions.md).

> [!div class="nextstepaction"]
> [Decisioni preliminari per la migrazione](./decisions.md)
