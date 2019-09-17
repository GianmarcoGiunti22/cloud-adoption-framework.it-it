---
title: Processi di conformità ai criteri della Baseline di sicurezza
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Processi di conformità ai criteri della Baseline di sicurezza
author: BrianBlanchard
ms.author: brblanch
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: 6494f64b91a0a59f235efbc21030c65fa5e7ded8
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71030116"
---
# <a name="security-baseline-policy-compliance-processes"></a>Processi di conformità ai criteri della Baseline di sicurezza

Questo articolo illustra un approccio ai processi di conformità ai criteri che regolano la [Baseline di sicurezza](./index.md). Una governance efficace della sicurezza del cloud inizia con processi manuali ricorrenti progettati per rilevare le vulnerabilità e imporre criteri per correggere i rischi per la sicurezza. Questo richiede il coinvolgimento regolare del team di governance del cloud e delle aziende interessate e degli stakeholder IT per rivedere e aggiornare i criteri e garantire la conformità ai criteri. Inoltre, molti processi di applicazione e di monitoraggio continuo possono essere automatizzati o eseguiti con strumenti per ridurre il sovraccarico di governance e consentire una risposta più rapida alla deviazione dai criteri.

## <a name="planning-review-and-reporting-processes"></a>Pianificazione, revisione e creazione di report per i processi

I migliori strumenti per la Baseline di sicurezza nel cloud, sono validi quanto i processi e i criteri che supportano. Il set seguente contiene processi di esempio comunemente coinvolti nella disciplina Baseline di sicurezza. Usare questi esempi come punto di partenza per la pianificazione di processi che consentono di continuare ad aggiornare i criteri di sicurezza in base alle modifiche dell'azienda e ai feedback da parte del team IT incaricato di concretizzare le indicazioni sulla governance.

**Valutazione e pianificazione iniziali del rischio:** Come parte dell'adozione iniziale della disciplina Baseline di sicurezza, identificare i principali rischi aziendali e le tolleranze correlate alla sicurezza nel cloud. Usare queste informazioni per discutere di rischi tecnici specifici con i membri del reparto IT e del team per la sicurezza, in modo da poter sviluppare un set di base relativo ai criteri di sicurezza per attenuare tali rischi e per stabilire la strategia di governance iniziale.

**Pianificazione della distribuzione:** Prima di distribuire un carico di lavoro o un asset, eseguire una verifica della sicurezza per identificare eventuali nuovi rischi e verificare che siano soddisfatti tutti i requisiti di accesso e criteri di sicurezza dei dati.

**Test di distribuzione:** Come parte del processo di distribuzione per qualsiasi carico di lavoro o asset, il team di governance del cloud, in collaborazione con i team di sicurezza aziendali, sarà responsabile della revisione della distribuzione per convalidare la conformità dei criteri di sicurezza.

**Pianificazione annuale:** Su base annuale, eseguire una verifica generale della Baseline di sicurezza. Esplorare le priorità aziendali future e le strategie di adozione cloud aggiornate per identificare potenziali aumenti dei rischi e altre esigenze di sicurezza emergenti. È consigliabile usare questo momento anche per esaminare le più recenti procedure consigliate riguardo la Baseline di sicurezza per integrarle all'interno dei propri criteri e processi di revisione.

**Revisione trimestrale e pianificazione:** Eseguire con cadenza trimestrale una revisione del controllo di sicurezza dei dati e dei report degli incidenti per identificare eventuali modifiche da apportare ai criteri di sicurezza. Come parte di questo processo, esaminare l'attuale panorama di sicurezza informatica per prevedere in modo proattivo le minacce emergenti e aggiornare i criteri in maniera appropriata. Dopo aver completato la revisione, allineare le indicazioni per la progettazione con i criteri aggiornati.

Questo processo di pianificazione è anche un buon momento per valutare l'appartenenza corrente del team di governance del cloud ai gap della conoscenza correlati a criteri nuovi o mutevoli e a rischi correlati alla sicurezza. Invitare il personale IT pertinente a partecipare alle attività di verifica e pianificazione come consulenti tecnici temporanei o come membri permanenti del team.

**Formazione e formazione:** Con cadenza semestrale, è possibile offrire sessioni di formazione per verificare che il personale IT e gli sviluppatori siano aggiornati sui requisiti più recenti dei criteri di sicurezza. Come parte di questo processo, rivedere e aggiornare qualsiasi documentazione, le linee guida o altre risorse di training per assicurarsi che siano in linea con le definizioni dei criteri aziendali più recenti.

**Verifiche mensili per il controllo e la creazione di report:** Su base mensile, eseguire un controllo su tutte le distribuzioni cloud per garantire il costante allineamento con i criteri di sicurezza. Esaminare le attività correlate alla sicurezza con il personale IT e identificare eventuali problemi di conformità non ancora gestiti come parte del processo continuo di monitoraggio e applicazione. Il risultato di questa revisione è costituito da un report per il team strategico Cloud e da ogni team di adozione del cloud per comunicare la conformità complessiva ai criteri. Il report viene inoltre archiviato a scopo legale e di controllo.

## <a name="ongoing-monitoring-processes"></a>Processi di monitoraggio continuo

La determinazione del buon esito della strategia di governance di sicurezza dipende dalla visibilità dello stato corrente e passato dell'infrastruttura cloud. Senza la possibilità di analizzare le metriche e i dati pertinenti sull'integrità della sicurezza e sulle attività delle risorse del cloud, non è possibile identificare cambiamenti nei rischi o rilevare violazioni delle tolleranze di rischio. I processi continui di governance illustrati in precedenza richiedono dati di qualità per garantire che i criteri possano essere modificati per proteggere meglio l'infrastruttura da mutevoli minacce e requisiti di sicurezza.

Verificare che i team IT e di sicurezza abbiano implementato sistemi di monitoraggio automatizzati per l'infrastruttura cloud che consentono di acquisire i dati di log rilevanti di cui si ha bisogno per valutare i rischi. Essere proattivi nel monitoraggio di questi sistemi garantisce la rapida individuazione e mitigazione di potenziali violazioni di criteri e assicura che la strategia di monitoraggio sia in linea con le esigenze di sicurezza.

## <a name="violation-triggers-and-enforcement-actions"></a>Trigger per le violazioni e azioni di imposizione

Poiché la mancata conformità alla sicurezza può causare rischi critici e di rischio per l'esposizione dei dati e l'interferenza dei servizi, il team di governance del cloud deve avere visibilità sulle gravi violazioni dei criteri. Verificare che il personale IT disponga di percorsi di escalation per segnalare eventuali problemi di sicurezza ai membri del team governance più adatti a identificare e verificare che i problemi relativi ai criteri vengano attenuati.

Quando vengono rilevate violazioni, si devono intraprendere azioni per un riallineamento con i criteri il prima possibile. Il team IT può automatizzare la maggior parte delle violazioni di trigger usando gli strumenti descritti in [Security Baseline toolchain for Azure](./toolchain.md) (Toolchain di Baseline di sicurezza per Azure).

I trigger seguenti e le azioni di applicazione forniscono esempi a cui è possibile fare riferimento quando si pianifica l'uso dei dati di monitoraggio per risolvere le violazioni dei criteri:

- **Aumento degli attacchi rilevati.** Se nelle risorse si verifica un aumento del 25% di attacchi DDoS o attacchi di forza bruta, discutere con il personale di sicurezza IT e con il proprietario del carico di lavoro per stabilire i rimedi. Tenere traccia del problema e aggiornare le indicazioni in caso fosse necessaria una revisione dei criteri per prevenire futuri incidenti.
- **Sono stati rilevati dati non classificati.** Qualsiasi origine dati senza una classificazione appropriata su privacy, sicurezza o impatto aziendale non avrà accesso finché non vengono applicati dal proprietario dei dati classificazione e livello appropriato di protezione dati.
- **Rilevato problema di integrità della sicurezza.** Disattivare l'accesso a tutte le macchine virtuali (VM) che hanno un accesso noto o vulnerabilità malware identificate, fino a quando non vengono installate patch appropriate o software di sicurezza. Aggiornare le indicazioni sui criteri per tenere conto di eventuali nuove minacce rilevate.
- **Vulnerabilità di rete rilevata.** L'accesso a qualsiasi risorsa non esplicitamente autorizzata dai criteri di accesso alla rete dovrebbe attivare un avviso per il personale di sicurezza IT e per il relativo proprietario del carico di lavoro. Tenere traccia del problema e aggiornare le indicazioni in caso sia necessaria una revisione dei criteri per attenuare futuri incidenti.

## <a name="next-steps"></a>Passaggi successivi

Usare il [modello di gestione del cloud](./template.md) per documentare i processi e i trigger in linea con il piano di adozione del cloud attuale.

Per istruzioni sull'esecuzione di criteri di gestione cloud in allineamento con i piani di adozione, consultare l'articolo sul miglioramento della disciplina.

> [!div class="nextstepaction"]
> [Security Baseline discipline improvement](./discipline-improvement.md) (Miglioramento della disciplina Baseline di sicurezza)
