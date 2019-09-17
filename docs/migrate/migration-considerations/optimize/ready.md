---
title: Preparare un'applicazione migrata per promuoverla alla produzione
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Processo nell'ambito della migrazione al cloud che è incentrato sulle attività di migrazione dei carichi di lavoro nel cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: b7f526cbf2b7efba981058d5614b4378adc8c6f6
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71022636"
---
# <a name="prepare-a-migrated-application-for-production-promotion"></a>Preparare un'applicazione migrata per promuoverla alla produzione

Dopo la promozione di un carico di lavoro, il traffico utente di produzione viene indirizzato agli asset di cui è stata eseguita la migrazione. Le attività di idoneità offrono l'opportunità di preparare il carico di lavoro per quel traffico. Di seguito sono riportate alcune considerazioni sull'azienda e sulla tecnologia che possono facilitare le attività di idoneità.

## <a name="validate-the-business-change-plan"></a>Convalidare il piano per le modifiche aziendali

La trasformazione si verifica quando gli utenti aziendali o i clienti sfruttano una soluzione tecnica per eseguire processi che favoriscono lo sviluppo aziendale. La verifica dell'idoneità è una buona opportunità per convalidare il [piano per le modifiche aziendali](./business-change-plan.md) e garantire una formazione adeguata per i team aziendali e tecnici interessati. In particolare, assicurarsi che i seguenti aspetti tecnici del piano per le modifiche vengano comunicati correttamente:

- La formazione degli utenti finali è stata completata (o almeno pianificata).
- I tempi di interruzione sono stati comunicati e approvati.
- I dati di produzione sono stati sincronizzati e convalidati dagli utenti finali.
- Convalidare i tempi dei processi di adozione e promozione e verificare che la tempistica e le modifiche siano state comunicate agli utenti finali.

## <a name="final-technical-readiness-tests"></a>Test finali di idoneità tecnica

La fase *Ready* è l'ultima fase da eseguire prima del rilascio alla produzione. Ciò significa che è anche l'ultima possibilità di testare il carico di lavoro. Di seguito sono riportati alcuni test consigliati durante questa fase:

- **Test di isolamento rete.** Testare e monitorare il traffico di rete per assicurare un isolamento appropriato ed evitare vulnerabilità di rete impreviste. Verificare inoltre che nel routing di rete da interrompere durante il cutover non venga riscontrato traffico imprevisto.
- **Test delle dipendenze.** Verificare che tutte le dipendenze delle applicazioni del carico di lavoro siano state migrate e siano accessibili agli asset di cui è stata eseguita la migrazione.
- **Test della continuità aziendale e del ripristino di emergenza.** Verificare che siano stati stipulati i contratti di servizio per il backup e il ripristino. Se possibile, eseguire un ripristino completo degli asset dalla soluzione per la continuità aziendale e il ripristino di emergenza.
- **Test delle route degli utenti finali.** Convalidare i modelli di traffico e il routing per il traffico degli utenti finali. Assicurarsi che le prestazioni di rete siano conformi alle aspettative.
- **Verifica finale delle prestazioni.** Assicurarsi che i test delle prestazioni siano stati completati e approvati dagli utenti finali. Eseguire test automatizzati delle prestazioni.

## <a name="final-business-validation"></a>Convalida aziendale finale

Dopo aver convalidato il piano per le modifiche aziendali e l'idoneità tecnica, è possibile completare la convalida aziendale eseguendo i passaggi finali seguenti:

- **Convalida dei costi (piano rispetto ai valori effettivi).** È probabile che i test abbiano l'effetto di introdurre modifiche alle dimensioni e all'architettura. Assicurarsi che i prezzi di distribuzione effettivi siano ancora allineati al piano originale.
- **Comunicazione ed esecuzione del piano di cutover.** Prima di procedere al cutover, fornire le adeguate comunicazioni ed eseguire il cutover di conseguenza.

## <a name="next-steps"></a>Passaggi successivi

Al termine delle attività di idoneità, è possibile [promuovere il carico di lavoro](./promote.md).

> [!div class="nextstepaction"]
> [Requisiti per promuovere alla produzione una risorsa migrata](./promote.md)
