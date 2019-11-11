---
title: Valutare gli asset prima della migrazione
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Valutare gli asset prima della migrazione
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: 6f35ca4e8420100c7455e8fa909fc8b572ee1074
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73753468"
---
# <a name="assess-assets-prior-to-migration"></a>Valutare gli asset prima della migrazione

Molti dei carichi di lavoro esistenti sono candidati ideali per la migrazione al cloud, ma non tutte le risorse sono compatibili con le piattaforme cloud e non tutti i carichi di lavoro possono trarre vantaggio dall'hosting nel cloud. La [pianificazione del digitale estate](../../../digital-estate/index.md) consente di generare un [backlog di migrazione](../prerequisites/technical-complexity.md#migration-backlog-aligning-business-priorities-and-timing) complessivo dei potenziali carichi di lavoro di cui eseguire la migrazione. Tuttavia, questa attività di pianificazione è di alto livello. Si basa sulle ipotesi fatte dal team di strategia del cloud e non approfondisce le considerazioni tecniche.

Di conseguenza, prima della migrazione di un carico di lavoro nel cloud è fondamentale valutare l'idoneità alla migrazione dei singoli asset associati a tale carico di lavoro. Durante questa valutazione, il team di adozione del cloud deve valutare la compatibilità tecnica, l'architettura richiesta, le aspettative a livello di prestazioni/dimensioni e le dipendenze per garantire che il carico di lavoro migrato possa essere distribuito nel cloud in modo efficace.

Il processo di *valutazione* è il primo di quattro attività incrementali eseguite all'interno di un'iterazione. Come descritto nell'articolo dedicato ai prerequisiti in merito alla [gestione delle complessità tecniche e delle modifiche](../prerequisites/technical-complexity.md), occorre decidere anticipatamente come eseguire questa fase. In particolare è necessario stabilire se le valutazioni verranno completate dal team di adozione del cloud in concomitanza con il progetto di migrazione effettivo oppure se verrà usato un modello a onde o factory per completare le valutazioni in un'iterazione separata. Se non tutti i membri del team sono in grado di rispondere a questa domanda di base sul processo, può essere consigliabile rivedere la sezione "[Prerequisiti](../prerequisites/index.md)".

## <a name="objective"></a>Obiettivo

Valutare un candidato alla migrazione, valutare il carico di lavoro, gli asset associati e le dipendenze prima della migrazione.

## <a name="definition-of-done"></a>Definizione di *completato*

Questo processo è completato quando sono note le informazioni seguenti su un singolo candidato alla migrazione:

- È stato definito il percorso da locale a cloud, inclusa la decisione dell'approccio per la promozione in produzione.
- Sono stati completati i processi di approvazione, modifica, stima dei costi o convalida richiesti per consentire al team di adozione del cloud di eseguire la migrazione.

## <a name="accountability-during-assessment"></a>Team responsabili durante la valutazione

Il team di adozione del cloud è responsabile dell'intero processo di valutazione. Tuttavia, i membri del team di strategia del cloud hanno alcune responsabilità, come indicato nella sezione seguente.

## <a name="responsibilities-during-assessment"></a>Responsabilità durante la valutazione

Oltre alle responsabilità di alto livello, esistono azioni per cui un singolo utente o un gruppo deve essere direttamente responsabile. L'elenco seguente include alcune delle attività che devono essere assegnate a specifici responsabili:

- **Priorità aziendale.** Il team comprende gli scopi della migrazione di questo carico di lavoro, incluso l'eventuale impatto previsto per l'azienda.
  - Un membro del team di strategia del cloud dovrebbe assumersi la responsabilità finale per questa attività, sotto la direzione del team di adozione del cloud.
- **Allineamento degli stakeholder.** Il team allinea aspettative e priorità agli stakeholder interni, identificando i criteri per il successo della migrazione. Quali sono gli indicatori del successo post-migrazione?
- **Costo.** È stato stimato il costo dell'architettura di destinazione e il budget complessivo è stato aggiornato corrispondentemente.
- **Supporto della migrazione.** Il team ha deciso come verrà completato il lavoro tecnico della migrazione, incluse le decisioni relative al supporto di partner o Microsoft.
- **Valutazione.** Il carico di lavoro viene valutato per compatibilità e dipendenze.
  - Questa attività deve essere assegnata a un esperto in materia che abbia familiarità con l'architettura e le operazioni del carico di lavoro candidato.
- **Architettura.** Il team ha concordato l'architettura di stato finale per il carico di lavoro migrato.
- **Allineamento del backlog.** Il team di adozione del cloud esamina i requisiti e conferma l'impegno per la migrazione del carico di lavoro candidato. Dopo la conferma, il backlog di rilascio e il backlog delle iterazioni devono essere aggiornati di conseguenza.
- **Struttura di suddivisione del lavoro o pianificazione delle attività.** Il team stabilisce una pianificazione delle attività cardine principali identificando gli obiettivi per il completamento dei processi di pianificazione, implementazione e verifica.
- **Approvazione finale.** Gli eventuali responsabili approvazione necessari hanno verificato il piano e approvato l'approccio per la migrazione dell'asset.
  - Per evitare sorprese in un secondo momento nel processo, almeno un rappresentante dell'azienda deve essere coinvolto nel processo di approvazione.

> [!CAUTION]
> Questo elenco completo di responsabilità e azioni può supportare migrazioni estese e complesse che coinvolgono più ruoli con vari livelli di competenza e richiedono un processo di approvazione dettagliato. Per le iniziative di migrazione più semplici e contenute potrebbero non essere richiesti tutti i ruoli e le azioni qui descritti. Per determinare quali di queste attività offrono valore aggiunto e quali sono invece non necessarie, è consigliabile che il team di adozione del cloud e quello di strategia del cloud seguano questo processo completo durante la prima migrazione dei carichi di lavoro. Dopo aver verificato e testato il carico di lavoro, il team può valutare questo processo e scegliere quali azioni usare in futuro.

## <a name="next-steps"></a>Passaggi successivi

Con una conoscenza generale del processo di valutazione si è pronti per avviare il processo [allineando le priorità aziendali](./business-priorities.md).

> [!div class="nextstepaction"]
> [Allineare le priorità aziendali](./business-priorities.md)
