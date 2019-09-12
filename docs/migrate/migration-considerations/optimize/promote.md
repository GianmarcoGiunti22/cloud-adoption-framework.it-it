---
title: Requisiti per promuovere alla produzione una risorsa migrata
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Processo nell'ambito della migrazione nel cloud che è incentrato sulle attività di migrazione dei carichi di lavoro nel cloud.
author: BrianBlanchard
ms.author: brblanch
ms.date: 04/04/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: migrate
ms.openlocfilehash: eb025eacb7743f470b15e2714ed65a05c21034a1
ms.sourcegitcommit: a26c27ed72ac89198231ec4b11917a20d03bd222
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70825471"
---
<!-- markdownlint-disable MD026 -->

# <a name="what-is-required-to-promote-a-migrated-resource-to-production"></a>Requisiti per promuovere alla produzione una risorsa migrata

La promozione alla produzione rappresenta il completamento della migrazione di un carico di lavoro nel cloud. Dopo la promozione dell'asset e di tutte le relative dipendenze, il traffico di produzione viene reindirizzato. Il reindirizzamento del traffico rende obsoleti gli asset locali, consentendone la rimozione.

Il processo di promozione varia in base all'architettura del carico di lavoro. Esistono tuttavia diversi prerequisiti coerenti e alcune attività comuni. Questo articolo li descrive tutti e serve come elenco di controllo di pre-promozione.

## <a name="prerequisite-processes"></a>Processi prerequisiti

Ognuno dei processi seguenti deve essere eseguito, documentato e convalidato prima della distribuzione in produzione:

- **[Valutazione](../assess/index.md):** è stata valutata la compatibilità del carico di lavoro con il cloud.
- **[Progettazione](../assess/architect.md):** la struttura del carico di lavoro è stata progettata correttamente per essere allineata al provider di servizi cloud scelto.
- **[Replica](../migrate/replicate.md):** gli asset sono stati replicati nell'ambiente cloud.
- **[Processo di gestione temporanea](../migrate/stage.md):** gli asset replicati sono stati ripristinati in un'istanza dell'ambiente cloud con gestione temporanea.
- **[Test aziendali](./business-test.md):** il carico di lavoro è stato completamente testato e convalidato dagli utenti aziendali.
- **[Piano per le modifiche aziendali](./business-change-plan.md):** l'azienda ha condiviso un piano per le modifiche da apportare in conformità con la promozione alla produzione. Tale piano deve includere un piano di adozione da parte degli utenti, modifiche dei processi aziendali, utenti che richiedono training e sequenze temporali per varie attività.
- **[Preparazione](./ready.md):** in genere, è necessario apportare una serie di modifiche tecniche prima della promozione.

## <a name="best-practices-to-execute-prior-to-promotion"></a>Procedure consigliate da eseguire prima della promozione

Le modifiche tecniche seguenti probabilmente dovranno essere completate e documentate come parte del processo di promozione:

- **Allineamento dei domini.** Alcuni criteri aziendali richiedono domini distinti per la gestione temporanea e la produzione. Assicurarsi che tutti gli asset siano aggiunti al dominio appropriato.
- **Routing degli utenti.** Verificare che gli utenti accedano al carico di lavoro tramite route di rete appropriate. Verificare aspettative di prestazioni coerenti.
- **Allineamento delle identità.** Verificare che gli utenti da reindirizzare all'applicazione dispongano delle autorizzazioni appropriate all'interno del dominio per ospitare l'applicazione.
- **Prestazioni.** Eseguire una convalida finale delle prestazioni del carico di lavoro per ridurre al minimo le sorprese.
- **Convalida di continuità aziendale e ripristino di emergenza.** Verificare che i processi di backup e ripristino appropriati funzionino come previsto.
- **Classificazione dei dati.** Convalidare la classificazione dei dati per assicurarsi che siano stati implementati criteri e protezioni appropriati.
- **Verifica del Chief Information Security Officer (CISO).** Verificare che il responsabile della sicurezza delle informazioni abbia esaminato il carico di lavoro, i rischi aziendali, la tolleranza ai rischi e le strategie di prevenzione.

## <a name="final-step-promote"></a>Passaggio finale: Promozione

I carichi di lavoro richiederanno livelli diversi di processi dettagliati di revisione e promozione. Tuttavia, il riallineamento delle reti rappresenta il passaggio finale comune per tutte le versioni di promozione. Quando tutto il resto è pronto, aggiornare i record DNS o gli indirizzi IP per instradare il traffico al carico di lavoro migrato.

## <a name="next-steps"></a>Passaggi successivi

La promozione di un carico di lavoro segnala il completamento di una versione. Tuttavia, in parallelo con la migrazione, è necessario [rimuovere](./decommission.md) dal servizio gli asset ritirati.

> [!div class="nextstepaction"]
> [Rimuovere gli asset ritirati](./decommission.md)
