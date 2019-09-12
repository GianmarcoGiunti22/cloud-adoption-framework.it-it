---
title: Informazioni sulle attività di gestione temporanea durante una migrazione
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Informazioni sulle attività di gestione temporanea durante una migrazione
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: a23a1e0f42382311a67e39238db8762c27c14480
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70825549"
---
# <a name="understand-staging-activities-during-a-migration"></a>Informazioni sulle attività di gestione temporanea durante una migrazione

Come descritto nell'articolo sui modelli di promozione, la *gestione temporanea* corrisponde alla fase in cui è stata eseguita la migrazione degli asset nel cloud, ma gli asset non sono ancora pronti per passare alla fase di produzione. Questo è spesso l'ultimo passaggio del processo di migrazione. Dopo la gestione temporanea, il carico di lavoro viene gestito da un team dedicato alle operazioni IT e cloud che deve prepararlo per l'uso in produzione.

## <a name="deliverables"></a>Risultati finali

Durante la fase di gestione temporanea, gli asset possono non essere pronti per l'uso in produzione. Prima che questa fase sia considerata completata è necessario finalizzare alcuni controlli di idoneità alla produzione. Di seguito è riportato un elenco dei risultati finali che sono spesso associati al completamento della gestione temporanea degli asset.

- **Test automatizzati.** Prima di concludere il processo di gestione temporanea è necessario eseguire i test automatizzati disponibili per convalidare le prestazioni del carico di lavoro. Quando la fase di gestione temporanea dell'asset è completata, viene terminata la sincronizzazione con il sistema di origine. È quindi più difficile ridistribuire gli asset replicati dopo che sono stati approntati per l'ottimizzazione.
- **Documentazione relativa alla migrazione.** La maggior parte degli strumenti per la migrazione può generare un report automatizzato degli asset di cui viene eseguita la migrazione. Prima di concludere l'attività di gestione temporanea, per maggiore chiarezza è necessario documentare tutti gli asset di cui è stata eseguita la migrazione.
- **Documentazione relativa alla configurazione.** Tutte le modifiche apportate a un asset (durante la correzione, la replica o la gestione temporanea) devono essere documentate in modo da garantire la conformità operativa.
- **Documentazione relativa al backlog.** Il backlog della migrazione deve essere aggiornato in base al carico di lavoro e agli asset della fase di gestione temporanea.

## <a name="next-steps"></a>Passaggi successivi

Dopo aver testato e documentato gli asset della fase di gestione temporanea, è possibile procedere con le [attività di ottimizzazione](../optimize/index.md).

> [!div class="nextstepaction"]
> [Ottimizzare i carichi di lavoro migrati](../optimize/index.md)
