---
title: 'Allineamento aziendale: gestione e operazioni del cloud'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Allineamento aziendale-gestione cloud e operazioni
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: deeb663a344bb3eb4e8ecc9af307da5ec1348b7a
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565208"
---
# <a name="create-business-alignment-in-cloud-management"></a>Crea allineamento aziendale in gestione cloud

Negli ambienti locali, gli asset IT (le applicazioni, le macchine virtuali, gli host VM, i dischi, i server, i dispositivi e le origini dati) vengono gestiti dal IT per supportare le operazioni del carico di lavoro. In termini IT, un carico di lavoro è una raccolta di asset IT che supportano un'operazione aziendale specifica. Per supportare le operazioni aziendali, la gestione IT offre processi progettati per ridurre al minimo le rotture a tali asset. Quando un'organizzazione si sposta nel cloud, la gestione e le operazioni cambiano leggermente, creando un'opportunità per sviluppare un allineamento aziendale più rigoroso.

## <a name="business-vernacular"></a>Business vernacolare

Il primo passaggio nella creazione dell'allineamento aziendale consiste nell'assicurare l'allineamento dei termini. La gestione IT, come la maggior parte delle professioni ingegneristiche, ha raccolto una raccolta di gergo o termini altamente tecnici. Tali condizioni possono comportare confusione per gli stakeholder aziendali e rendere difficile la mappatura dei servizi di gestione al valore aziendale.

Fortunatamente, il processo di sviluppo di una strategia di adozione del cloud e di un piano di adozione del cloud crea un'opportunità ideale per modificare il mapping di questi termini. Il processo crea anche opportunità per ripensare gli impegni alla gestione operativa, in collaborazione con l'azienda. La serie di articoli seguente illustra questo nuovo approccio in tre termini specifici che consentono di migliorare le conversazioni tra gli stakeholder aziendali: 

- **[Criticità](./criticality.md):** Mapping dei carichi di lavoro ai processi aziendali. Criticità della classificazione per concentrare gli investimenti.
- **[Effetto](./impact.md):** Informazioni sull'impatto di potenziali interruzioni per contribuire alla valutazione del ritorno sugli investimenti per la gestione cloud.
- **[Impegno](./commitment.md):** sviluppo di partenariati reali, tramite la creazione e la documentazione di contratti *con l'azienda*.

> [!NOTE]
> I termini sottostanti sono termini IT classici, ad esempio SLA, RTO e RPO. Il mapping di condizioni aziendali e IT specifiche viene trattato in modo più dettagliato nell'articolo relativo all' [impegno](./commitment.md) .

## <a name="ops-management-planning-workbook"></a>Cartella di lavoro Pianificazione gestione Ops

Per acquisire decisioni derivanti da questa conversazione sull'allineamento dei termini, una [cartella di lavoro di gestione Ops](https://raw.githubusercontent.com/microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx) è disponibile nel sito github. Questa cartella di lavoro non esegue calcoli di contratti di contratto o costi. Consente solo di acquisire tali misure e prevedere un ritorno in merito alla perdita di attività di prevenzione.

In alternativa, gli stessi carichi di lavoro e gli asset associati possono essere contrassegnati direttamente in Azure, se le soluzioni sono già state distribuite nel cloud.

## <a name="next-steps"></a>Passaggi successivi

Iniziare a creare l'allineamento aziendale definendo la [criticità del carico](./criticality.md)di lavoro.

> [!div class="nextstepaction"]
> [Definire la criticità del carico di lavoro](./criticality.md)
