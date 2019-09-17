---
title: Processi di conformità ai criteri per l'accelerazione della distribuzione
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Processi di conformità ai criteri per l'accelerazione della distribuzione
author: alexbuckgit
ms.author: abuck
ms.date: 02/11/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: govern
ms.custom: governance
ms.openlocfilehash: c127a1c8bc8bce7608f0e146b36785fcee82dc0b
ms.sourcegitcommit: 443c28f3afeedfbfe8b9980875a54afdbebd83a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71028577"
---
# <a name="deployment-acceleration-policy-compliance-processes"></a>Processi di conformità ai criteri per l'accelerazione della distribuzione

Questo articolo illustra un approccio ai processi di conformità ai criteri che regolano l'[accelerazione della distribuzione](./index.md). Una governance efficace della configurazione cloud inizia con processi manuali ricorrenti progettati per rilevare i problemi e imporre criteri per correggere tali rischi. È tuttavia possibile automatizzare questi processi e integrarli con strumenti per ridurre il carico della governance e ottenere risposte più rapide in caso di deviazioni.

## <a name="planning-review-and-reporting-processes"></a>Processi di pianificazione, verifica e creazione di report

L'efficacia degli strumenti per l'accelerazione della distribuzione nel cloud dipende dai processi e dai criteri che supportano. Di seguito è riportato un set di processi di esempio comunemente utilizzati come parte di una disciplina di accelerazione della distribuzione. Usare questi esempi come punto di partenza per la pianificazione dei processi che consentiranno di continuare ad aggiornare i criteri di distribuzione e configurazione in base alle modifiche aziendali e ai commenti e suggerimenti degli sviluppatori e dei team IT responsabili della trasformazione delle linee guida per la governance in azione.

**Valutazione e pianificazione iniziali del rischio:** come parte dell'adozione iniziale della disciplina Accelerazione della distribuzione, identificare i principali rischi aziendali e le tolleranze correlate alla distribuzione delle applicazioni aziendali. Usare queste informazioni per discutere di rischi tecnici specifici con i membri del team operativo IT e sviluppare un set di base di criteri di distribuzione e configurazione per correggere questi rischi per stabilire la strategia di governance iniziale.

**Pianificazione della distribuzione:** Prima di distribuire qualsiasi asset, eseguire una verifica della sicurezza e delle operazioni per identificare eventuali nuovi rischi e verificare che siano soddisfatti tutti i requisiti relativi ai criteri relativi alla distribuzione.

**Test di distribuzione:** Come parte del processo di distribuzione di qualsiasi asset, il team di governance del cloud, in collaborazione con i team operativi IT, è responsabile della revisione della conformità dei criteri di distribuzione.

**Pianificazione annuale:** su base annuale, eseguire una verifica generale della strategia di accelerazione della distribuzione. Esplorare le priorità future dell'azienda e le strategie di adozione del cloud aggiornate per identificare un potenziale aumento dei rischi e altre esigenze e opportunità emergenti per la configurazione. Usare questo tempo anche per esaminare le procedure consigliate di DevOps più recenti e integrarle nei criteri e nei processi di revisione.

**Revisione trimestrale e pianificazione:** Eseguire una revisione trimestrale dei dati di controllo operativi e dei report sugli eventi imprevisti per identificare le modifiche necessarie nei criteri di accelerazione della distribuzione. Come parte di questo processo, esaminare le procedure consigliate per DevOps e DevTechOps e aggiornare i criteri nel modo appropriato. Al termine della revisione, allineare ai criteri aggiornati le linee guida per la progettazione di applicazioni e sistemi.

Questo processo di pianificazione è anche un buon momento per valutare l'appartenenza corrente del team di governance del cloud ai gap della conoscenza correlati a criteri nuovi o mutevoli e a rischi correlati a DevOps e all'accelerazione della distribuzione. Invitare il personale IT pertinente a partecipare alle attività di verifica e pianificazione come consulenti tecnici temporanei o come membri permanenti del team.

**Formazione e formazione:** Su base mensile, è possibile offrire sessioni di formazione per assicurarsi che il personale IT e gli sviluppatori siano aggiornati sulla strategia e sui requisiti più recenti di accelerazione della distribuzione. Come parte di questo processo, rivedere e aggiornare qualsiasi documentazione, le linee guida o altre risorse di training per assicurarsi che siano in linea con le definizioni dei criteri aziendali più recenti.

**Verifiche mensili per il controllo e la creazione di report:** eseguire un controllo mensile su tutte le distribuzioni cloud per garantire il costante allineamento con i criteri di configurazione. Esaminare le attività relative alla distribuzione con il personale IT e identificare eventuali problemi di conformità non ancora gestiti come parte del processo di monitoraggio e applicazione continuo. Il risultato di questa revisione è costituito da un report per il team strategico Cloud e da ogni team di adozione del cloud per comunicare la conformità complessiva ai criteri. Il report viene inoltre archiviato a scopo legale e di controllo.

## <a name="ongoing-monitoring-processes"></a>Processi di monitoraggio continuo

La determinazione del buon esito della strategia di governance dell'accelerazione della distribuzione dipende dalla visibilità dello stato corrente e passato dell'infrastruttura cloud. Senza la possibilità di analizzare le metriche e i dati rilevanti delle risorse cloud e le attività operative, non è possibile identificare le modifiche ai rischi o rilevare le violazioni delle tolleranze di rischio. I processi continui di governance illustrati in precedenza richiedono dati di qualità per garantire che i criteri possano essere modificati in modo da proteggere l'infrastruttura da mutevoli minacce e rischi provenienti da risorse non configurate correttamente.

Assicurarsi che i team operativi IT abbiano implementato sistemi di monitoraggio automatici per l'infrastruttura cloud che acquisiscono i dati di log pertinenti necessari per valutare i rischi. Essere proattivi nel monitoraggio di questi sistemi garantisce la rapida individuazione e mitigazione di potenziali violazioni di criteri e assicura che la strategia di monitoraggio sia in linea con le esigenze di distribuzione e configurazione.

## <a name="violation-triggers-and-enforcement-actions"></a>Trigger per le violazioni e azioni di imposizione

Poiché la mancata conformità con i criteri di configurazione può comportare rischi critici per l'interferenza dei servizi, il team di governance del cloud deve avere visibilità sulle gravi violazioni dei criteri. Assicurarsi che il personale IT disponga dei percorsi di escalation chiari per la segnalazione dei problemi di conformità della configurazione ai membri del team di governance più adatti per identificare e verificare che i problemi relativi ai criteri vengano mitigati una volta

Quando vengono rilevate violazioni, si devono intraprendere azioni in modo da riallineare i criteri il prima possibile. Il team IT può automatizzare la maggior parte dei trigger per le violazioni usando gli strumenti descritti nella [toolchain dell'accelerazione della distribuzione per Azure](./toolchain.md).

I trigger e le azioni di imposizione seguenti sono esempi a cui è possibile fare riferimento quando si parla dell'uso dei dati di monitoraggio per risolvere le violazioni dei criteri:

- **Sono state rilevate modifiche impreviste nella configurazione.** Se la configurazione di una risorsa cambia in modo imprevisto, collaborare con il personale IP e con i proprietari del carico di lavoro per identificare la causa principale e sviluppare un piano correttivo.
- **Configurazione di nuove risorse non conforme ai criteri**. Collaborare con i team di DevOps e i proprietari del carico di lavoro per rivedere i criteri di accelerazione della distribuzione durante l'avvio del progetto in modo che le persone coinvolte comprendano i requisiti dei criteri pertinenti.
- **Ritardi nelle pianificazioni di progetto a causa di errori di distribuzione o problemi di configurazione**. Collaborare con i team di sviluppo e i proprietari del carico di lavoro per assicurarsi che comprendano come automatizzare la distribuzione di risorse basate sul cloud per coerenza e ripetibilità. Le distribuzioni completamente automatiche devono essere richieste tempestivamente durante&mdash;il ciclo di sviluppo. il tentativo di eseguire questa operazione in ritardo nel ciclo di sviluppo causa in genere problemi e ritardi imprevisti.

## <a name="next-steps"></a>Passaggi successivi

Usare il [modello di gestione del cloud](./template.md) per documentare i processi e i trigger in linea con il piano di adozione del cloud attuale.

Per istruzioni sull'esecuzione dei criteri di gestione del cloud in linea con i piani di adozione, vedere l'articolo sul miglioramento della disciplina.

> [!div class="nextstepaction"]
> [Miglioramento della disciplina Accelerazione della distribuzione](./discipline-improvement.md)
