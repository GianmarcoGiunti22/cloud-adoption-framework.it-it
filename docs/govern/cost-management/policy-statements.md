---
title: Definizioni dei criteri di esempio per la gestione dei costi
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Definizioni dei criteri di esempio per la gestione dei costi
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 086740f6677896220824096a5afe66618779a2d0
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73566408"
---
# <a name="cost-management-sample-policy-statements"></a>Definizioni dei criteri di esempio per la gestione dei costi

Le singole definizioni dei criteri del cloud sono linee guida per affrontare i rischi specifici identificati durante il processo di valutazione dei rischi. Queste definizioni devono fornire un riassunto conciso dei rischi e dei piani per gestirli. Ogni definizione di istruzione deve includere i tipi di informazioni seguenti:

- **Rischio aziendale:** Riepilogo del rischio che verrà indirizzato da questo criterio.
- **Istruzione per i criteri:** Una chiara spiegazione di riepilogo dei requisiti dei criteri.
- **Opzioni di progettazione:** Raccomandazioni di utilità pratica, specifiche o altre istruzioni che i team IT e gli sviluppatori possono usare per l'implementazione dei criteri.

Le istruzioni dei criteri di esempio seguenti affrontano i rischi aziendali comuni correlati ai costi. Queste istruzioni sono esempi a cui è possibile fare riferimento durante la stesura di istruzioni dei criteri per soddisfare le esigenze dell'organizzazione. Questi esempi non sono destinati a essere proscrittivi e sono potenzialmente disponibili diverse opzioni relative ai criteri per la gestione di ogni rischio identificato. Collaborare a stretto contatto con i team IT e aziendali per identificare i criteri migliori per un set di rischi esclusivo.

## <a name="future-proofing"></a>Investimento solido per il futuro

**Rischio aziendale:** Criteri correnti che non garantiscono un investimento in una disciplina di gestione dei costi del team di governance. Tuttavia, si prevede un investimento di questo tipo in futuro.

**Istruzione per i criteri:** È necessario associare tutti gli asset distribuiti al cloud con un'unità di fatturazione e un carico di lavoro o un'applicazione. In questo modo si ha la sicurezza di ottenere risultati efficaci dall'impegno che si dedicherà in futuro alla gestione dei costi.

**Opzioni di progettazione:** Per informazioni sulla definizione di una base di prova futura, vedere le discussioni correlate alla creazione di un MVP di governance nelle [guide di progettazione](../guides/index.md) di utilità pratica incluse come parte delle linee guida per il Framework di adozione del cloud.

## <a name="budget-overruns"></a>Superamento del budget

**Rischio aziendale:** La distribuzione self-service crea il rischio di sovraspesa.

**Istruzione per i criteri:** Qualsiasi distribuzione cloud deve essere allocata a un'unità di fatturazione con un budget approvato e un meccanismo per i limiti di budget.

**Opzioni di progettazione:** In Azure è possibile controllare il budget con [Gestione costi di Azure](https://docs.microsoft.com/azure/cost-management/manage-budgets)

## <a name="underutilization"></a>Sottoutilizzo

**Rischio aziendale:** La società ha prepagato per i servizi cloud o ha compiuto un impegno annuale per spendere un importo specifico. Sussiste il rischio che l'importo concordato non venga utilizzato, causando un investimento perso.

**Istruzione per i criteri:** Ogni unità di fatturazione con un budget allocato per il cloud viene soddisfatta annualmente per impostare i budget, trimestralmente per regolare i budget e mensilmente per allocare tempo per la revisione della spesa pianificata rispetto a quella effettiva. Discutere delle deviazioni superiori al 20% con il responsabile dell'unità di fatturazione una volta al mese. Ai fini della tracciabilità, assegnare tutti gli asset a un'unità di fatturazione.

**Opzioni di progettazione**:

- In Azure il controllo della spesa effettiva rispetto a quella pianificata può essere gestito tramite [Gestione costi di Azure](https://docs.microsoft.com/azure/cost-management/quick-acm-cost-analysis).
- Sono disponibili diverse opzioni per raggruppare le risorse in base all'unità di fatturazione. In Azure è consigliabile scegliere un [modello di coerenza delle risorse](../../decision-guides/resource-consistency/index.md) in collaborazione con il team di governance e applicarlo a tutti gli asset.

## <a name="overprovisioned-assets"></a>Provisioning eccessivo di asset

**Rischio aziendale:** Nei data center locali tradizionali, è prassi comune distribuire gli asset con una pianificazione della capacità aggiuntiva per la crescita in futuro. Le risorse cloud possono essere ridimensionate più rapidamente rispetto alle apparecchiature tradizionali. Inoltre, i prezzi degli asset del cloud variano in base alla capacità tecnica. Esiste il rischio che la prassi tradizionale adottata nei data center locali abbia l'effetto di aumentare artificialmente la spesa relativa al cloud.

**Istruzione per i criteri:** Qualsiasi asset distribuito nel cloud deve essere registrato in un programma in grado di monitorare l'utilizzo e segnalare una capacità superiore al 50% dell'utilizzo. Gli asset distribuiti nel cloud devono essere raggruppati o contrassegnati in base a una logica per consentire ai membri del team di governance di coinvolgere il proprietario del carico di lavoro nell'ottimizzazione degli asset con provisioning eccessivo.

**Opzioni di progettazione**:

- In Azure è possibile ottenere consigli per l'ottimizzazione tramite [Azure Advisor](https://docs.microsoft.com/azure/advisor/advisor-cost-recommendations).
- Sono disponibili diverse opzioni per raggruppare le risorse in base all'unità di fatturazione. In Azure è consigliabile scegliere un [modello di coerenza delle risorse](../../decision-guides/resource-consistency/index.md) in collaborazione con il team di governance e applicarlo a tutti gli asset.

## <a name="overoptimization"></a>Ottimizzazione eccessiva

**Rischio aziendale:** Gestione dei costi effettivi crea nuovi rischi. L'ottimizzazione della spesa è inversamente proporzionale alle prestazioni del sistema. Tagliando i costi si corre il rischio di ridurre eccessivamente la spesa e di conseguenza peggiorare la qualità delle esperienze degli utenti.

**Istruzione per i criteri:** Tutti gli asset che influiscono direttamente sulle esperienze dei clienti devono essere identificati tramite il raggruppamento o l'assegnazione di tag. Prima di ottimizzare qualsiasi asset che influisca sull'esperienza del cliente, il team di governance del cloud deve adattare l'ottimizzazione in base ad almeno 90 giorni di tendenze di utilizzo. Documentare eventuali picchi collegati a eventi o alla variazione stagionale presi in considerazione durante la fase di ottimizzazione degli asset.

**Opzioni di progettazione**:

- In Azure le [funzionalità di Monitoraggio di Azure](https://docs.microsoft.com/azure/azure-monitor/insights/vminsights-performance) consentono di ottenere informazioni dettagliate per l'analisi dell'utilizzo del sistema.
- Sono disponibili diverse opzioni per raggruppare e contrassegnare le risorse in base ai ruoli. In Azure è consigliabile scegliere un [modello di coerenza delle risorse](../../decision-guides/resource-consistency/index.md) in collaborazione con il team di governance e applicarlo a tutti gli asset.

## <a name="next-steps"></a>Passaggi successivi

Usare gli esempi citati in questo articolo come punto di partenza per elaborare criteri applicabili a rischi aziendali specifici, in linea con i piani di adozione del cloud.

Per iniziare a sviluppare definizioni dei criteri personalizzate correlate alla gestione dei costi, scaricare il [modello di gestione dei costi](./template.md).

Per accelerare l'adozione di questa disciplina, scegliere la [Guida alla governance](../guides/index.md) che si allinea maggiormente all'ambiente. Modificare quindi la progettazione per incorporare le decisioni relative a criteri aziendali specifici.

Sulla base dei rischi e della tolleranza, stabilire un processo per controllare e comunicare la conformità ai criteri di Gestione costi.

> [!div class="nextstepaction"]
> [Stabilire i processi di conformità ai criteri](./compliance-processes.md)
