---
title: Allineamento delle risorse ai carichi di lavoro con priorità
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Allineamento delle risorse ai carichi di lavoro con priorità
author: BrianBlanchard
ms.author: brblanch
ms.date: 07/01/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: plan
ms.openlocfilehash: 9d98a9e368f71310a05ae6242ef75a57771824d5
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70828708"
---
# <a name="align-assets-to-prioritized-workloads"></a>Allineare le risorse ai carichi di lavoro con priorità

Il carico di lavoro è una descrizione concettuale di una raccolta di asset: Macchine virtuali, applicazioni e origini dati. L'articolo precedente, [assegnare priorità e definire i carichi di lavoro](./workloads.md), ha fornito indicazioni per la raccolta dei dati che definiranno il carico di lavoro. Prima della migrazione, alcuni degli input tecnici nell'elenco richiedono una convalida aggiuntiva. Questo articolo è utile per la convalida degli input seguenti:

- **Applicazioni**: Elencare tutte le applicazioni incluse in questo carico di lavoro.
- **VM/Server**: Elencare le macchine virtuali o i server inclusi nel carico di lavoro.
- **Origini dati**: Elencare tutte le origini dati incluse nel carico di lavoro.
- **Dipendenze**: Elencare tutte le dipendenze di asset non incluse nel carico di lavoro.

Sono disponibili diverse opzioni per assemblare questi dati. Di seguito sono riportati alcuni degli approcci più comuni.

## <a name="alternative-inputs-migrate-modernize-innovate"></a>Input alternativi: Migrazione, modernizzazione, innovazione

L'obiettivo dei punti dati precedenti è acquisire le dipendenze e il lavoro tecnico relativo come supporto per la definizione delle priorità. A seconda della transizione desiderata, potrebbe essere necessario raccogliere punti dati alternativi per supportare la priorità corretta.

**Migrazione:** Per le attività di migrazione pure, le dipendenze dell'inventario e degli asset esistenti servono come misura equa della complessità relativa.

**Modernizzare** Quando l'obiettivo di un carico di lavoro è quello di modernizzare le applicazioni o altre risorse, questi punti dati sono ancora solide misure di complessità. Tuttavia, potrebbe essere opportuno aggiungere un input per le opportunità di modernizzazione alla documentazione del carico di lavoro.

**Innovazione:** Quando la logica di business o i dati sono in fase di modifica del materiale durante un'operazione di adozione del cloud, viene considerato un tipo *innovativo* di trasformazione. Lo stesso accade quando si creano nuovi dati o una nuova logica di business. Per tutti gli scenari di innovazione, la migrazione delle risorse rappresenterà probabilmente la minima quantità di lavoro richiesta. Per questi scenari, il team deve definire un set di input di dati tecnici per misurare la complessità relativa.

## <a name="azure-migrate"></a>Azure Migrate

Azure Migrate fornisce un set di funzioni di raggruppamento che consentono di velocizzare l'aggregazione di applicazioni, macchine virtuali, origini dati e dipendenze. Dopo che i carichi di lavoro sono stati definiti concettualmente, possono essere usati come base per raggruppare gli asset in base al mapping delle dipendenze.

La documentazione di Azure Migrate fornisce indicazioni su [come raggruppare i computer in base alle dipendenze](https://docs.microsoft.com/azure/migrate/how-to-create-group-machine-dependencies).

## <a name="configuration-management-database"></a>Configuration-database di gestione

Alcune organizzazioni dispongono di un database di gestione della configurazione ben gestito (CMDB) all'interno degli strumenti di gestione delle operazioni esistenti. Potrebbero usare CMDB in alternativa per fornire i punti dati di input descritti in precedenza.

## <a name="next-steps"></a>Passaggi successivi

[Esaminare le decisioni](./review-rationalization.md) di razionalizzazione basate sull'allineamento degli asset e sulle definizioni del carico di lavoro.

> [!div class="nextstepaction"]
> [Esaminare le decisioni di razionalizzazione](./review-rationalization.md)
