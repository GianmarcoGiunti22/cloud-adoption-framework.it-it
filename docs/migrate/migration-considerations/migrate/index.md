---
title: Esecuzione di una migrazione
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Esecuzione di una migrazione
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 21520edecc7ba874713561672cd0bd38aa96c0a2
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70818234"
---
# <a name="execute-a-migration"></a>Eseguire una migrazione

Dopo la valutazione, è possibile eseguire la migrazione di un carico di lavoro nel cloud. Questa serie di articoli illustra le varie attività che possono essere coinvolte nell'esecuzione di una migrazione.

## <a name="objective"></a>Obiettivo

L'obiettivo di una migrazione è eseguire la migrazione di un singolo carico di lavoro nel cloud.

## <a name="definition-of-done"></a>Definizione di *completato*

La fase di migrazione è completa quando il carico di lavoro è disponibile per la gestione temporanea e pronto per i test nel cloud, inclusi tutti gli asset dipendenti necessari per il funzionamento del carico di lavoro. Durante il processo di ottimizzazione, il carico di lavoro viene preparato per l'utilizzo in produzione.

Questa definizione di *completato* può variare, a seconda dei processi di test e rilascio. L'articolo successivo di questa serie riguarda la [scelta di un modello di promozione](./promotion-models.md) e può essere utile per capire il momento migliore per promuovere un carico di lavoro migrato in produzione.

## <a name="accountability-during-migration"></a>Team responsabili durante la migrazione

Il team di adozione del cloud è responsabile per l'intero processo di migrazione. Tuttavia, i membri del team di strategia del cloud hanno alcune responsabilità, come descritto nella sezione seguente.

## <a name="responsibilities-during-migration"></a>Responsabilità durante la migrazione

Oltre alle responsabilità di alto livello, esistono azioni per cui un singolo utente o un gruppo deve essere direttamente responsabile. L'elenco seguente include alcune delle attività che devono essere assegnate a specifici responsabili:

- **Correzione.** Risolvere eventuali problemi di compatibilità che impediscono la migrazione al cloud del carico di lavoro.
  - Come descritto nell'articolo dedicato ai prerequisiti in merito alla [gestione delle complessità tecniche e delle modifiche](../prerequisites/technical-complexity.md), occorre decidere anticipatamente come eseguire questa attività. In particolare è necessario stabilire se la correzione verrà completata dal team di adozione del cloud in concomitanza con il progetto di migrazione effettivo oppure se verrà usato un modello a onde o factory per completare la correzione in un'iterazione separata. Se non tutti i membri del team sono in grado di rispondere a questa domanda di base sul processo, può essere consigliabile rivedere la sezione dedicata ai [prerequisiti](../prerequisites/index.md).
- **Replica.** Creare una copia di ogni asset nel cloud per sincronizzare le macchine virtuali, i dati e le applicazioni con le risorse nel cloud.
  - A seconda del modello di promozione possono essere necessari strumenti diversi per eseguire questa attività.
- **Gestione temporanea.** Dopo la replica e la verifica di tutti gli asset per un carico di lavoro, è possibile procedere attivare il carico di lavoro in un ambiente e procedere con l'attuazione di un piano per le modifiche aziendali.

## <a name="next-steps"></a>Passaggi successivi

Con una conoscenza generale del processo di migrazione si è pronti per [decidere il modello di promozione](./promotion-models.md).

> [!div class="nextstepaction"]
> [Decidere un modello di promozione](./promotion-models.md)
