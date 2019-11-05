---
title: Processi di conformità ai criteri per la coerenza delle risorse
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Processi di conformità ai criteri per la coerenza delle risorse
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: ebff4e0bbeb7f74a61b81527e0dbc62874ffbe6c
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73566051"
---
# <a name="resource-consistency-policy-compliance-processes"></a>Processi di conformità ai criteri per la coerenza delle risorse

Questo articolo illustra un approccio ai processi di conformità ai criteri che regolano la [coerenza delle risorse](./index.md). Una governance efficace della coerenza delle risorse del cloud inizia con processi manuali ricorrenti progettati per identificare inefficienze operative, migliorare la gestione delle risorse distribuite e garantire interruzioni minime per i carichi di lavoro cruciali. Questi processi manuali sono supportati da attività di monitoraggio, automazione e strumenti per ridurre il carico della governance e consentire risposte più rapide in caso di deviazioni dai criteri.

## <a name="planning-review-and-reporting-processes"></a>Pianificazione, revisione e creazione di report per i processi

Le piattaforme cloud offrono un'ampia gamma di strumenti e funzionalità di gestione che è possibile usare per organizzazione, provisioning, scalabilità e contenimento dei tempi di inattività. L'uso di questi strumenti per strutturare e gestire in modo efficace le distribuzioni cloud in modo da correggere i rischi potenziali richiede processi e criteri ben congegnati, oltre a una stretta collaborazione con i team operativi IT e gli stakeholder aziendali.

Il set seguente contiene processi di esempio comunemente coinvolti nella disciplina Coerenza delle risorse. Usare questi esempi come punto di partenza per la pianificazione di processi che consentono di continuare ad aggiornare i criteri di coerenza delle risorse in base ai cambiamenti aziendali e al feedback da parte dei team di sviluppo e IT incaricati di trasformare le linee guida in azioni.

**Valutazione e pianificazione iniziali del rischio:** Nell'ambito dell'adozione iniziale della disciplina di coerenza delle risorse, identificare i rischi e le tolleranze aziendali principali correlati alle operazioni e alla gestione IT. Usare queste informazioni per discutere di rischi tecnici specifici con i membri dei team IT e dei proprietari del carico di lavoro per sviluppare un set di base di criteri di coerenza delle risorse progettati per correggere questi rischi, definendo la strategia di governance iniziale.

**Pianificazione della distribuzione:** Prima di distribuire qualsiasi asset, eseguire una revisione per identificare eventuali nuovi rischi operativi. Stabilire i requisiti a livello di risorse e i modelli di richiesta previsti, oltre a identificare le esigenze di scalabilità e le potenziali opportunità di ottimizzazione dell'utilizzo. Assicurarsi inoltre che siano presenti piani di backup e ripristino.

**Test di distribuzione:** Come parte della distribuzione, il team di governance del cloud, in collaborazione con i team operativi cloud, sarà responsabile della revisione della distribuzione per convalidare la conformità dei criteri di coerenza delle risorse.

**Pianificazione annuale:** Su base annuale, eseguire una revisione di alto livello della strategia di coerenza delle risorse. Esplorare i piani per l'espansione aziendale futura o le priorità dell'azienda e aggiornare le strategie di adozione del cloud per identificare potenziali aumenti dei rischi e altre esigenze emergenti per la coerenza delle risorse. In questa fase, esaminare anche le procedure consigliate più aggiornate per la coerenza delle risorse del cloud e integrarle nei criteri e nei processi di verifica dell'azienda.

**Revisione trimestrale e pianificazione:** Ogni trimestre esegue una revisione dei dati operativi e dei report sugli eventi imprevisti per identificare le modifiche necessarie per i criteri di coerenza delle risorse. Come parte di questo processo, esaminare le modifiche nell'utilizzo delle risorse e delle prestazioni per identificare gli asset che richiedono aumenti o diminuzioni nell'allocazione delle risorse e identificare eventuali carichi di lavoro o asset candidati per il ritiro.

Questo processo di pianificazione è anche un buon momento per valutare l'appartenenza corrente del team di governance del cloud per i gap delle informazioni correlate ai criteri nuovi o modificati e ai rischi correlati alla coerenza delle risorse come disciplina. Invitare il personale IT pertinente a partecipare alle attività di verifica e pianificazione come consulenti tecnici temporanei o come membri permanenti del team.

Formazione **e formazione:** Su base semestrale, offrire sessioni di formazione per assicurarsi che il personale IT e gli sviluppatori siano aggiornati sui requisiti e le linee guida più recenti per la coerenza delle risorse. Come parte di questo processo, rivedere e aggiornare qualsiasi documentazione o altre risorse di training per assicurarsi che siano in linea con le definizioni dei criteri aziendali più recenti.

**Verifiche mensili per il controllo e la creazione di report:** Su base mensile, eseguire un controllo su tutte le distribuzioni cloud per assicurare l'allineamento continuo con i criteri di coerenza delle risorse. Esaminare le attività correlate con il personale IT e identificare eventuali problemi di conformità non ancora gestiti come parte del processo continuo di monitoraggio e imposizione. Il risultato di questa revisione è costituito da un report per il team strategico Cloud e da ogni team di adozione del cloud per comunicare le prestazioni complessive e la conformità ai criteri. Il report viene inoltre archiviato a scopo legale e di controllo.

## <a name="ongoing-monitoring-processes"></a>Processi di monitoraggio continuo

La determinazione del buon esito della strategia di governance della coerenza delle risorse dipende dalla visibilità dello stato corrente e passato dell'infrastruttura cloud. Senza la possibilità di analizzare le metriche e i dati pertinenti sull'integrità e sulle attività dell'ambiente cloud, non è possibile identificare cambiamenti nei rischi o rilevare violazioni delle tolleranze ai rischi. I processi di governance regolari illustrati in precedenza richiedono dati di qualità per assicurarsi che i criteri possano essere modificati per ottimizzare l'utilizzo delle risorse cloud e migliorare le prestazioni complessive dei carichi di lavoro ospitati nel cloud.

Verificare che i team IT abbiano implementato sistemi di monitoraggio automatizzati per l'infrastruttura cloud, che consentono di acquisire i dati di log rilevanti di cui si ha bisogno per valutare i rischi. Essere proattivi nel monitoraggio di questi sistemi garantisce la rapida individuazione e mitigazione di potenziali violazioni dei criteri e assicura che la strategia di monitoraggio sia in linea con le esigenze operative.

## <a name="violation-triggers-and-enforcement-actions"></a>Trigger per le violazioni e azioni di imposizione

Poiché la conformità dei criteri di coerenza delle risorse può comportare un'interferenza critica del servizio o rischi significativi per i costi, il team di governance del cloud deve avere visibilità sugli incidenti di non conformità. Assicurarsi che il personale IT disponga dei percorsi di escalation chiari per segnalare questi problemi ai membri del team di governance più adatti per identificare e verificare che i problemi relativi ai criteri vengano attenuati quando vengono rilevati.

Quando vengono rilevate violazioni, si devono intraprendere azioni per riallinearsi il prima possibile ai criteri. Il team IT può automatizzare la maggior parte dei trigger per le violazioni usando gli strumenti descritti nella [toolchain di coerenza delle risorse per Azure](./toolchain.md).

I trigger seguenti e le azioni di applicazione forniscono esempi a cui è possibile fare riferimento quando si pianifica l'uso dei dati di monitoraggio per risolvere le violazioni dei criteri:

- **Rilevata risorsa con provisioning eccessivo.** le risorse rilevate che risultano usare meno del 60% della capacità della CPU o di memoria devono essere ridotte automaticamente o è necessario effettuare il deprovisioning delle risorse per ridurre i costi.
- **Rilevata risorsa sottoposta a provisioning.** le risorse rilevate che risultano usare più dell'80% della capacità della CPU o di memoria devono essere aumentate automaticamente o è necessario effettuare il provisioning di risorse aggiuntive per ottenere capacità aggiuntiva.
- **Creazione di risorse senza tag.** qualsiasi richiesta di creare una risorsa senza i tag META richiesti verrà rifiutata automaticamente.
- **È stata rilevata un'interruzione critica delle risorse.** il personale IT riceve notifica per tutte le interruzioni rilevate per le risorse cruciali. Se l'interruzione non è immediatamente risolvibile, lo staff escalace il problema e invia una notifica ai proprietari del carico di lavoro e al team di governance del cloud. Il team di governance del cloud tiene traccia del problema fino a quando la revisione del criterio è necessaria per impedire interventi futuri.
- **Drift della configurazione.** Le risorse rilevate che non sono conformi alle linee di base stabilite devono attivare avvisi ed essere corretti automaticamente usando strumenti di gestione della configurazione come automazione di Azure, chef, Puppet, Ansible e così via.

## <a name="next-steps"></a>Passaggi successivi

Usare il [modello di gestione del cloud](./template.md) per documentare i processi e i trigger in linea con il piano di adozione del cloud attuale.

Per istruzioni sull'esecuzione di criteri di gestione cloud in allineamento con i piani di adozione, consultare l'articolo sul miglioramento della disciplina.

> [!div class="nextstepaction"]
> [Miglioramento della disciplina Coerenza delle risorse](./discipline-improvement.md)
