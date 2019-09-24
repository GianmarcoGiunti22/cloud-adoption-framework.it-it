---
title: Processi di conformità ai criteri di Gestione costi
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Processi di conformità ai criteri di Gestione costi
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 6345a8cae51a6b26b7fad174113a40e9dc0dae3e
ms.sourcegitcommit: d19e026d119fbe221a78b10225230da8b9666fe1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71220968"
---
# <a name="cost-management-policy-compliance-processes"></a>Processi di conformità ai criteri di Gestione costi

L'articolo illustra un approccio alla creazione di processi che supportano una disciplina di governance di [Gestione costi](./index.md). Una governance efficace dei costi del cloud inizia dai processi manuali ricorrenti, progettati per supportare la conformità ai criteri. Questo richiede il coinvolgimento regolare del team di governance del cloud e degli stakeholder aziendali interessati a esaminare e aggiornare i criteri e garantire la conformità ai criteri. Inoltre, molti processi di applicazione e di monitoraggio continuo possono essere automatizzati o eseguiti con strumenti per ridurre il sovraccarico di governance e consentire una risposta più rapida alla deviazione dai criteri.

## <a name="planning-review-and-reporting-processes"></a>Processi di pianificazione, revisione e creazione di report

I migliori strumenti per Gestione costi nel cloud, sono validi allo stesso modo dei processi e dei criteri che supportano. La serie seguente contiene processi di esempio comunemente coinvolti nella disciplina Gestione costi. Usare questi esempi come punto di partenza per la pianificazione di processi che consentono di continuare ad aggiornare i criteri di costo in base alle modifiche dell'azienda e ai feedback da parte dei team aziendali, a seconda del materiale sussidiario di governance dei costi.

**Valutazione e pianificazione iniziali del rischio:** come parte dell'adozione iniziale della disciplina Gestione costi, identificare i principali rischi aziendali e le tolleranze correlate ai costi del cloud. Usare queste informazioni per discutere il budget e i rischi relativi ai costi con i membri dei team aziendali e sviluppare un set di baseline di criteri per attenuare tali rischi, al fine di stabilire la propria strategia iniziale di governance.

**Pianificazione della distribuzione:** Prima di distribuire un asset, stabilire un budget previsto in base all'allocazione cloud prevista. Assicurarsi che le informazioni su proprietà e gli account siano documentati, al fine della distribuzione.

**Pianificazione annuale:** su base annuale, eseguire un'analisi di rollup in tutte le risorse distribuite e da distribuire. Allinea i budget per unità aziendali, reparti, team e altre divisioni appropriate per consentire l'adozione self-service. Assicurarsi che il responsabile di ogni unità di fatturazione sia a conoscenza del budget e del modo in cui tenere traccia della spesa.

Si tratta del tempo necessario per prestare un pre-impegno o effettuare un pre-acquisto per ottimizzare gli sconti. È consigliabile allineare il budget annuale all'anno fiscale del fornitore di cloud, per sfruttare ancora di più le opzioni sconto di fine anno.

**Pianificazione trimestrale**: con cadenza trimestrale, rivedere i budget con ogni responsabile di unità fatturazione per allineare la spesa prevista e quella effettiva. Se sono state apportate modifiche al piano o ai modelli di spesa imprevisti, allineare e riallocare il budget.

Questo processo di pianificazione trimestrale è anche un buon momento per valutare l'appartenenza corrente del team di governance del cloud ai gap di informazioni correlate ai piani aziendali attuali o futuri. Invitare il personale pertinente a partecipare alle attività di revisione e pianificazione come consulenti tecnici temporanei o come membri permanenti del team.

**Formazione e formazione:** Su base mensile, è possibile offrire sessioni di formazione per assicurarsi che i dipendenti aziendali e IT siano aggiornati sui requisiti più recenti per i criteri di gestione dei costi. Come parte di questo processo, rivedere e aggiornare qualsiasi documentazione, le linee guida o altre risorse di training per assicurarsi che siano in linea con le definizioni dei criteri aziendali più recenti.

**Creazione di report mensili:** su base mensile, elaborare report di spesa effettiva rispetto a quella prevista. Inviare una notifica ai responsabili della fatturazione di eventuali deviazioni impreviste.

Questi processi di base consentono di allineare le spese e stabilire una base per la disciplina Gestione costi.

## <a name="ongoing-monitoring-processes"></a>Processi di monitoraggio continuo

Una corretta strategia di governance di Gestione costi dipende dalla visibilità su passato, presente e spesa pianificata futura relativa al cloud. Senza la possibilità di analizzare le metriche e i dati pertinenti sui costi esistenti, non è possibile identificare cambiamenti nei rischi o rilevare violazioni delle tolleranze ai rischi. I processi continui di governance illustrati in precedenza richiedono dati di qualità per garantire che i criteri possano essere modificati, con l'obiettivo di proteggere meglio l'infrastruttura da mutevoli requisiti aziendali e uso del cloud.

Garantire che i team IT abbiano implementato i sistemi automatizzati per il monitoraggio della spesa per il cloud e l'uso di deviazioni non pianificate da costi previsti. Stabilire sistemi per la creazione di report e avvisi, al fine di garantire il rilevamento di richiesta conferma e la mitigazione di potenziali violazioni dei criteri.

## <a name="compliance-violation-triggers-and-enforcement-actions"></a>Trigger di violazione e azioni di esecuzione conformi

Quando vengono rilevate violazioni, si devono intraprendere azioni di esecuzione per un riallineamento con i criteri. È possibile automatizzare più trigger di violazione mediante gli strumenti descritti in [Cost Management toolchain for Azure (Toolchain di Gestione costi per Azure)](./toolchain.md).

Sono riportati alcuni esempi di trigger:

- **Deviazioni mensili del budget.** trattare tutte le deviazioni di spesa mensile che superano il rapporto tra spesa prevista ed effettiva del 20% insieme al responsabile dell'unità di fatturazione. Registrare le risoluzioni e le modifiche in previsione.
- **Ritmo di adozione.** qualsiasi deviazione a livello di sottoscrizione superiore al 20% attiverà una revisione con il leader dell'unità di fatturazione. Registrare le risoluzioni e le modifiche in previsione.

## <a name="next-steps"></a>Passaggi successivi

Usare il [Modello di gestione del cloud](./template.md) per documentare i processi e i trigger in linea con il piano di adozione del cloud attuale.

Per indicazioni sull'esecuzione dei criteri di gestione del cloud in linea con i piani di adozione, vedere l'articolo sul miglioramento della disciplina Gestione costi.

> [!div class="nextstepaction"]
> [Cost Management discipline improvement (Miglioramento della disciplina Gestione costi)](./discipline-improvement.md)
