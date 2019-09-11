---
title: Ottimizzare i carichi di lavoro migrati
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Ottimizzare i carichi di lavoro migrati
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 7bed1c8383b9c444c9e272c27f71f73fd3325e24
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70818200"
---
# <a name="optimize-migrated-workloads"></a>Ottimizzare i carichi di lavoro migrati

Dopo aver completato la migrazione al cloud di un carico di lavoro e degli asset di supporto corrispondenti, occorre preparare il carico di lavoro prima di poterlo passare in produzione. Questo processo include attività per preparare il carico di lavoro, ridimensionare gli asset dipendenti e preparare l'azienda per l'entrata in produzione del carico di lavoro basato sul cloud migrato.

L'obiettivo dell'ottimizzazione consiste nel preparare un carico di lavoro migrato per la promozione per l'utilizzo in produzione.

## <a name="definition-of-done"></a>Definizione di *completato*

Il processo di ottimizzazione si considera completato quando un carico di lavoro è stato configurato e ridimensionato correttamente e viene usato in produzione.

## <a name="accountability-during-optimization"></a>Team responsabili durante l'ottimizzazione

Il team di adozione del cloud è responsabile per l'intero processo di ottimizzazione. Tuttavia, i membri del team di strategia del cloud, del team operativo del cloud e team di governance del cloud devono anche assumersi responsabilità per le attività incluse in questo processo.

## <a name="responsibilities-during-optimization"></a>Responsabilità durante l'ottimizzazione

Oltre alle responsabilità di alto livello, esistono azioni per cui un singolo utente o un gruppo deve essere direttamente responsabile. L'elenco seguente include alcune delle attività che devono essere assegnate a specifici responsabili:

- **Test aziendali.** Risolvere eventuali problemi di compatibilità che impediscono il completamento della migrazione al cloud per il carico di lavoro.
  - È consigliabile che gli utenti più esperti all'interno dell'azienda partecipino attivamente ai test del carico di lavoro migrato. A seconda del grado di ottimizzazione tentato, potrebbero essere necessari più cicli di test.
- **Piano per le modifiche aziendali.** Sviluppo di un piano per l'adozione da parte degli utenti, per le modifiche dei processi aziendali e per la variazione degli indicatori KPI aziendali o delle metriche di apprendimento come risultato dell'intervento di migrazione.
- **Benchmark e ottimizzazione.** Studio dei test aziendali e dei test automatizzati per il benchmark delle prestazioni. In base all'utilizzo, il team di adozione del cloud perfeziona le dimensioni degli asset distribuiti per bilanciare costi e prestazioni in riferimento ai requisiti di produzione previsti.
- **Pronto per la produzione.** Preparare il carico di lavoro e l'ambiente per il supporto dell'utilizzo in produzione continuativo del carico di lavoro.
- **Promozione.** Reindirizzare il traffico di produzione al carico di lavoro migrato e ottimizzato. Questa attività rappresenta il completamento di un ciclo di rilascio.

Oltre alle attività principali, esistono alcune attività parallele che richiedono assegnazioni e piani di esecuzione specifici:

- **Ritiro.** In genere, si possono ottenere riduzioni dei costi da una migrazione dopo il ritiro e l'adeguato smaltimento degli asset di produzione precedenti.
- **Retrospettiva.** Ogni nuovo rilascio rappresenta un'opportunità per una comprensione più approfondita e per adottare una mentalità orientata alla crescita. Al termine di ogni ciclo di rilascio, il team di adozione del cloud deve valutare i processi usati durante la migrazione per individuare eventuali miglioramenti.

## <a name="next-steps"></a>Passaggi successivi

Con una conoscenza generale del processo di ottimizzazione si è pronti per avviare il processo di [definizione di un piano per le modifiche aziendali per il carico di lavoro candidato](./business-change-plan.md).

> [!div class="nextstepaction"]
> [Piano per le modifiche aziendali](./business-change-plan.md)
