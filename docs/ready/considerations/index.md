---
title: Considerazioni sulle aree di destinazione di Azure
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni su come un'area di destinazione costituisca il blocco predefinito di base per qualsiasi ambiente di adozione del cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/20/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: ready
ms.openlocfilehash: f9926fd59133303960338ac4e8b45cc9007dad51
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70816228"
---
# <a name="landing-zone-considerations"></a>Considerazioni sulle aree di destinazione

Un'area di destinazione costituisce il blocco predefinito di base per qualsiasi ambiente di adozione del cloud. Il termine *area di destinazione* fa riferimento a un ambiente di cui è stato effettuato il provisioning e che è stato preparato per ospitare carichi di lavoro in un ambiente cloud come Azure. Un'area di destinazione perfettamente funzionante è il risultato finale di una qualsiasi iterazione della metodologia Ready di Cloud Adoption Framework.

![Considerazioni sulle aree di destinazione](../../_images/ready/landing-zone-considerations.png)

Questa immagine illustra gli aspetti principali da prendere in considerazione per implementare una qualsiasi distribuzione dell'area di destinazione. Le considerazioni possono essere suddivise in tre categorie o tipi: hosting, concetti fondamentali di Azure e governance.

## <a name="hosting-considerations"></a>Considerazioni sull'hosting

Tutte le aree di destinazione forniscono la struttura per le opzioni di hosting. La struttura viene creata in modo esplicito, tramite controlli di governance, o in modo organico, con l'adozione di servizi compresi nell'area di destinazione. Gli articoli seguenti consentono di prendere decisioni che verranno applicate nel progetto o in altri script di automazione per la creazione dell'area di destinazione:

- **[Decisioni relative al calcolo](./compute-decisions.md)** . Per ridurre al minimo la complessità operativa, allineare le opzioni di calcolo in base all'area di destinazione. Questa decisione può essere applicata tramite toolchain di automazione, come le iniziative di Criteri di Azure e i progetti dell'area di destinazione.
- **[Decisioni relative all'archiviazione](./storage-guidance.md)** . Selezionare la soluzione di archiviazione di Azure più adatta per supportare i requisiti del carico di lavoro.
- **[Decisioni relative alla rete](./network-decisions.md)** . Scegliere i servizi di rete, gli strumenti e le architetture per supportare i requisiti di connettività, governance e carico di lavoro dell'organizzazione.
- **[Decisioni relative al database](./data-decisions.md)** . Determinare la tecnologia di database più adatta ai requisiti del carico di lavoro.

## <a name="azure-fundamentals"></a>Concetti fondamentali di Azure

Ogni area di destinazione fa parte di una soluzione più ampia per l'organizzazione delle risorse in un ambiente cloud. I concetti fondamentali di Azure costituiscono i blocchi predefiniti di base per l'organizzazione.

- **[Concetti fondamentali di Azure](./fundamental-concepts.md)** . Informazioni sui termini e i concetti fondamentali usati per organizzare le risorse in Azure e su come questi concetti sono correlati.
- **Guida alle decisioni relative all'organizzazione delle risorse**. Dopo aver appreso le nozioni di base, la guida alle decisioni relative all'organizzazione delle risorse può essere utile per prendere le decisioni per definire l'area di destinazione.

## <a name="governance-considerations"></a>Considerazioni sulla governance

Le metodologie di governance di Cloud Adoption Framework consentono di definire un processo per la regolamentazione dell'intero ambiente. Esistono, però, molti casi d'uso in cui può essere necessario prendere le decisioni relative alla governance in base all'area di destinazione. In molti scenari le baseline della governance vengono applicate in base all'area di destinazione anche se sono stabilite in modo olistico. Questo è vero per le prime zone di destinazione distribuite da un'organizzazione.

Gli articoli seguenti possono essere utili per prendere decisioni correlate alla governance per una specifica area di destinazione. Ogni decisione può quindi essere integrata nelle baseline della governance.

- **Requisiti relativi ai costi**. In base alla motivazione di un'organizzazione per l'adozione del cloud e gli impegni operativi assunti in relazione a questo ambiente, potrebbe essere necessario modificare diverse configurazioni di gestione dei costi per l'area di destinazione.
- **Decisioni relative al monitoraggio**. A seconda dei requisiti operativi di un'area di destinazione, è possibile distribuire diversi strumenti di monitoraggio. L'articolo sulle decisioni relative al monitoraggio può essere utile per determinare gli strumenti più appropriati da distribuire.
- **Uso del controllo degli accessi in base al ruolo**. Il [controllo degli accessi in base al ruolo (RBAC)](../azure-best-practices/roles.md) di Azure consente una gestione degli accessi specifica, basata su gruppi, per risorse organizzate in base ai ruoli utente.
- **Decisioni relative ai criteri**. Gli esempi di progetto di Azure includono progetti di conformità già pronti, ognuno con iniziative di criteri predefinite. Le decisioni relative ai criteri sono utili per orientare la scelta del migliore progetto o della migliore iniziativa di criteri in base ai requisiti e ai vincoli indicati.
- **[Creare coerenza del cloud ibrido](../../infrastructure/misc/hybrid-consistency.md)** . Creare soluzioni cloud ibride che offrono all'organizzazione i vantaggi dell'innovazione cloud, pur mantenendo molte delle caratteristiche della gestione locale.
