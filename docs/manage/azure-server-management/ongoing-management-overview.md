---
title: Sicurezza e gestione continuativa
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Sicurezza e gestione continuativa
author: BrianBlanchard
ms.author: brblanch
ms.date: 05/10/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 7b77181dd8ef6efe655b56489e5d4e6b210382b6
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71028201"
---
# <a name="phase-3-ongoing-management-and-security"></a>Fase 3: Sicurezza e gestione continuativa

Dopo aver caricato i servizi di gestione di Azure, sarà necessario concentrarsi sulle operazioni e sulle configurazioni di sicurezza che supporteranno le operazioni in corso. Si inizierà a proteggere l'ambiente esaminando il Centro sicurezza di Azure. Verranno quindi configurati i criteri per assicurare la conformità dei server e l'automazione delle attività comuni. Questa sezione contiene gli argomenti seguenti:

- **[Risolvere le raccomandazioni sulla sicurezza.](#address-security-recommendations)** Il Centro sicurezza di Azure offre suggerimenti per migliorare la sicurezza dell'ambiente. Quando si implementano queste indicazioni, è possibile vedere l'effetto riflesso in un punteggio di sicurezza.
- **[Abilitare i criteri di configurazione Guest.](./guest-configuration-policy.md)** Abilitare la funzionalità di configurazione Guest di criteri di Azure per controllare le impostazioni in una macchina virtuale. Ad esempio, è possibile verificare se i certificati stanno per scadere.
- **[Rilevare e segnalare le modifiche critiche.](./enable-tracking-alerting.md)** Quando si esegue la risoluzione dei problemi, la prima domanda da considerare è "cosa è cambiato?" In questo articolo si apprenderà come tenere traccia delle modifiche e creare avvisi per monitorare in modo proattivo i componenti critici.
- **[Creare pianificazioni degli aggiornamenti.](./update-schedules.md)** Pianificare l'installazione degli aggiornamenti per assicurarsi che tutti i server dispongano di quelli più recenti.
- **[Esempi comuni di criteri di Azure.](./common-policies.md)** Fornisce esempi di criteri di gestione comuni.

## <a name="address-security-recommendations"></a>Suggerimenti sulla sicurezza degli indirizzi

Il Centro sicurezza di Azure è la posizione centrale per gestire la sicurezza per l'ambiente. Verranno visualizzate una valutazione complessiva e consigli mirati.

Si consiglia di esaminare e implementare le raccomandazioni fornite da questo servizio. Per informazioni sui vantaggi aggiuntivi del Centro sicurezza di Azure, vedere [attenersi alle raccomandazioni del Centro sicurezza di Azure](https://docs.microsoft.com/azure/migrate/migrate-best-practices-security-management#best-practice-follow-azure-security-center-recommendations).

## <a name="next-steps"></a>Passaggi successivi

Informazioni su come [abilitare la funzionalità di configurazione Guest di criteri di Azure](./guest-configuration-policy.md) .

> [!div class="nextstepaction"]
> [Criteri di configurazione Guest](./guest-configuration-policy.md)
