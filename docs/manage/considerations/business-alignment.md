---
title: Allineamento aziendale-gestione cloud e operazioni
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Allineamento aziendale-gestione cloud e operazioni
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 9c6884d57b9238f58921b14ec3ddbbe3623506af
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72558142"
---
# <a name="create-business-alignment-in-cloud-management"></a>Crea allineamento aziendale in gestione cloud

Negli ambienti locali, gli asset IT (le applicazioni, le macchine virtuali, gli host VM, i dischi, i server, i dispositivi e le origini dati) vengono gestiti dal IT per supportare le operazioni del carico di lavoro. In termini IT, un carico di lavoro è una raccolta di asset IT che supportano un'operazione aziendale specifica. Negli ambienti locali, la gestione IT offre la progettazione dei processi per ridurre al minimo le rotture a tali asset IT, nel tentativo di ridurre al minimo le rotture per le operazioni aziendali di supporto. Quando si passa al cloud, la gestione e le operazioni cambiano leggermente, creando un'opportunità per sviluppare un allineamento aziendale più rigoroso.

## <a name="business-vernacular"></a>Business vernacolare

Il primo passaggio nella creazione dell'allineamento aziendale è l'allineamento dei termini. La gestione IT, come la maggior parte delle professioni ingegneristiche, include un bel po' di gergo o termini altamente tecnici. Tali condizioni possono comportare confusione per gli stakeholder aziendali e rendere difficile il mapping dei servizi di gestione al valore aziendale.

Fortunatamente, i processi per lo sviluppo di una strategia di adozione del cloud e di un piano di adozione del cloud creano una situazione idea per la modifica del mapping dei termini. Viene inoltre creata un'ottima opportunità per ripensare gli impegni alla gestione operativa, in collaborazione con l'azienda. La serie di articoli seguente illustra questo nuovo approccio in tre termini specifici che possono migliorare le conversazioni con gli stakeholder aziendali:

- **[Criticità](./criticality.md)** : mapping dei carichi di lavoro ai processi aziendali. Criticità della classificazione per concentrare gli investimenti.
- **[Impatto](./impact.md)** : comprendere l'impatto di potenziali interruzioni per contribuire alla valutazione del ritorno sugli investimenti per la gestione cloud.
- **[Impegno](./commitment.md)** : sviluppare partenariati reali, creando e documentando contratti **con l'azienda**.

> [!NOTE]
> Sotto ognuno di questi termini sono presenti termini IT classici come SLA, RTO e RPO. Il mapping dei termini aziendali e IT viene trattato in modo più dettagliato nell'articolo sull'impegno.

## <a name="ops-management-planning-workbook"></a>Cartella di lavoro Pianificazione gestione Ops

Per semplificare l'acquisizione delle decisioni in seguito a questa conversazione, nel repository GitHub è disponibile una [cartella di lavoro di gestione delle operazioni](https://raw.githubusercontent.com/microsoft/CloudAdoptionFramework/master/manage/opsmanagementworkbook.xlsx) . Questa cartella di lavoro non esegue calcoli di contratti di contratto o costi. Viene utilizzato solo come guida per acquisire tali misure e prevedere il ritorno in merito alle attività di prevenzione della perdita.

In alternativa, gli stessi carichi di lavoro e gli asset associati possono essere contrassegnati direttamente in Azure, se le soluzioni sono già state distribuite nel cloud.

## <a name="next-steps"></a>Passaggi successivi

Iniziare a creare l'allineamento aziendale definendo la [criticità del carico](./criticality.md)di lavoro.

> [!div class="nextstepaction"]
> [Definire la criticità del carico di lavoro](./criticality.md)
