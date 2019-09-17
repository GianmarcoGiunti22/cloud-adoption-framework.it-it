---
title: 'Baseline di identità: metriche, indicatori e tolleranza ai rischi'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: 'Baseline di identità: metriche, indicatori e tolleranza ai rischi'
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: ad0b06cad7aefc70eea6366eb9ef2b5844c871a6
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71029811"
---
# <a name="identity-baseline-metrics-indicators-and-risk-tolerance"></a>Baseline di identità: metriche, indicatori e tolleranza ai rischi

Questo articolo è concepito per aiutare l'utente a quantificare la tolleranza ai rischi aziendale in relazione alla baseline di identità. La definizione di metriche e indicatori consente di creare un business case per effettuare un investimento riguardo alla disciplina Baseline di identità.

## <a name="metrics"></a>metrics

La disciplina Baseline di identità è incentrata sull'identificazione, autenticazione e autorizzazione di individui, gruppi di utenti o processi automatizzati e sul fornire a queste entità l'accesso appropriato alle risorse nelle distribuzioni cloud. Nell'ambito dell'analisi dei rischi è necessario raccogliere dati relativi ai servizi gestione delle identità per determinare l'entità dei rischi e l'importanza degli investimenti nella governance della baseline di identità per le distribuzioni cloud pianificate.

Di seguito sono riportati esempi di metriche utili che è necessario raccogliere per valutare la tolleranza ai rischi all'interno della disciplina Baseline di identità:

- **Dimensioni dei sistemi di identità.** Numero totale di utenti, gruppi o altri oggetti gestiti tramite i sistemi di gestione delle identità.
- **Dimensioni complessive dell'infrastruttura dei servizi di directory.** Numero di foreste di directory, domini e tenant usati dall'organizzazione.
- **Dipendenza da meccanismi di autenticazione legacy o locali.** Numero di carichi di lavoro che dipendono da meccanismi di autenticazione legacy o da servizi di autenticazione a più fattori di terze parti.
- **Extent dei servizi directory distribuiti nel cloud.** Numero di foreste di directory, domini e tenant distribuiti nel cloud.
- **Server Active Directory distribuiti nel cloud.** Numero di server Active Directory distribuiti nel cloud.
- **Unità organizzative distribuite nel cloud.** Numero di unità organizzative Active Directory distribuite nel cloud.
- **Extent della Federazione.** Numero di sistemi per la baseline di identità federati con i sistemi dell'organizzazione.
- **Utenti con privilegi elevati.** Numero di account utente che dispongono di accesso con privilegi elevati a risorse o strumenti di gestione.
- **Uso del controllo degli accessi in base al ruolo.** Numero di sottoscrizioni, gruppi di risorse o singole risorse non gestite tramite il controllo degli accessi in base al ruolo.
- **Attestazioni di autenticazione.** Numero di tentativi di autenticazione utente riusciti e non riusciti.
- **Attestazioni di autorizzazione.** Numero di tentativi riusciti e falliti di accedere alle risorse da parte degli utenti.
- **Account compromessi.** Numero di account utente che sono stati compromessi.

## <a name="risk-tolerance-indicators"></a>Indicatori sulla tolleranza ai rischi

I rischi correlati alla baseline di identità sono in gran parte legati alla complessità dell'infrastruttura di gestione delle identità dell'organizzazione. Se tutti gli utenti e i gruppi vengono gestiti usando una singola directory o un provider di identità nativo del cloud usando l'integrazione minima con altri servizi, il livello di rischio sarà probabilmente ridotto. Tuttavia, man mano che l'azienda cresce, i sistemi per la baseline di identità potrebbero dover supportare scenari più complessi, ad esempio molteplici directory per supportare l'organizzazione interna o federazione con provider di identità esterni. Man mano che i sistemi diventano più complessi, il rischio aumenta.

Nelle prime fasi di adozione del cloud è necessario lavorare con il team addetto alla sicurezza IT e con gli stakeholder aziendali per identificare i [rischi aziendali](./business-risks.md) correlati alle identità, quindi definire una baseline accettabile per la tolleranza ai rischi per le identità. Questa sezione del Framework di adozione del cloud fornisce esempi, ma i rischi e le basi di riferimento dettagliati per la società o le distribuzioni potrebbero essere diversi.

Dopo aver creato una baseline, è necessario stabilire i benchmark minimi che rappresentano un aumento inaccettabile dei rischi identificati. Questi benchmark fungono da trigger per quando è necessario intervenire per risolvere questi rischi. Di seguito sono riportati alcuni esempi del modo in cui le metriche correlate alle identità, ad esempio quelle descritte in precedenza, possono giustificare un maggiore investimento nella disciplina Baseline di identità.

- **Trigger numero di account utente.** Una società con più di _x_ utenti, gruppi o altri oggetti gestiti nei sistemi delle identità potrebbe trarre vantaggio dall'investimento nella disciplina della linea di base di identità per garantire una governance efficiente su un numero elevato di account.
- **Trigger di dipendenza di identità locale.** Una società che pianifica la migrazione dei carichi di lavoro nel cloud che richiedono funzionalità di autenticazione legacy o l'autenticazione a più fattori di terze parti deve investire nella disciplina della linea di base di identità per ridurre i rischi correlati al refactoring o al cloud aggiuntivo distribuzione dell'infrastruttura.
- **Trigger di complessità dei servizi directory.** Una società che gestisce più di _x_ numero of_ singole foreste, domini o tenant di directory deve investire nella disciplina della linea di base di identità per ridurre i rischi correlati alla gestione degli account e ai problemi di efficienza correlati a più utenti credenziali distribuite tra più sistemi.
- **Trigger servizi directory ospitati nel cloud.** Una società che ospita _x_ Active Directory macchine virtuali (VM) Server ospitate nel cloud o con unità organizzative _x_ gestite su questi server basati su cloud può trarre vantaggio dall'investimento nella disciplina della linea di base di identità per ottimizzare integrazione con tutti i servizi di identità esterni o locali.
- **Trigger di Federazione.** Una società che implementa la Federazione delle identità con _x_ sistemi di base di identità esterni può trarre vantaggio dall'investimento nella disciplina della linea di base di identità per garantire criteri aziendali coerenti tra i membri della Federazione.
- **Trigger di accesso con privilegi elevati.** Una società con più dell' _x%_ di utenti con autorizzazioni elevate per gli strumenti e le risorse di gestione deve considerare l'investimento nella disciplina della linea di base di identità per ridurre al minimo il rischio di overprovisioning accidentale dell'accesso agli utenti.
- **Trigger RBAC.** Per identificare le modalità ottimizzate per l'assegnazione dell'accesso degli utenti alle risorse, un'azienda con meno di _%_ di risorse che usano metodi di controllo degli accessi in base al ruolo deve considerare l'investimento nella disciplina di base di identità.
- **Trigger di errore di autenticazione.** Un'azienda in cui gli errori di autenticazione rappresentano più dell' _x%_ dei tentativi deve investire nella disciplina della linea di base di identità per assicurarsi che i metodi di autenticazione non siano sotto attacco esterno e che gli utenti siano in grado di usare i metodi di autenticazione correttamente.
- **Trigger di errore di autorizzazione.** Una società in cui i tentativi di accesso vengono rifiutati più dell' _x%_ del tempo deve investire nella disciplina della linea di base di identità per migliorare l'applicazione e l'aggiornamento dei controlli di accesso e identificare i tentativi di accesso potenzialmente dannosi.
- **Trigger account compromesso.** Una società con più di _x_ account compromessi deve investire nella disciplina della linea di base di identità per migliorare la forza e la sicurezza dei meccanismi di autenticazione e migliorare i meccanismi per correggere i rischi correlati agli account compromessi.

Le metriche e i trigger esatti usati per misurare la tolleranza ai rischi e il livello di investimento nella disciplina della linea di base di identità saranno specifici per l'organizzazione, ma gli esempi precedenti dovrebbero fungere da base utile per discutere nel team di governance del cloud.

## <a name="next-steps"></a>Passaggi successivi

Usare il [modello di gestione del cloud](./template.md) per documentare le metriche e gli indicatori di tolleranza in linea con il piano di adozione del cloud attuale.

Esaminare i criteri di base delle identità di esempio come punto di partenza per sviluppare criteri che risolvono i rischi aziendali specifici che si allineano ai piani di adozione del cloud.

> [!div class="nextstepaction"]
> [Esaminare i criteri di esempio](./policy-statements.md)
