---
title: Protezione e ripristino-gestione e operazioni di cloud
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Protezione e ripristino-gestione e operazioni di cloud
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 356d6c463e97553cb56d132c4f94e812a5b1c656
ms.sourcegitcommit: 6f287276650e731163047f543d23581d8fb6e204
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73752804"
---
# <a name="protect-and-recover-in-cloud-management"></a>Proteggi e ripristina in gestione cloud

Una volta soddisfatti i requisiti per l' [inventario e la visibilità](./inventory.md) e la [conformità operativa](./operational-compliance.md), i team di gestione cloud possono prevedere e preparare una potenziale interruzione del carico di lavoro. Quando si pianifica la gestione del cloud, è necessario che i team inizino con un presupposto che si verifichi un errore.

Nessuna soluzione tecnica può offrire un contratto di contratto con un tempo di incirca pari al 100%. Le soluzioni con le architetture con la maggiore ridondanza attestano il recapito in "sei 9" o il tempo di esecuzione del 99,9999%. Ma anche una soluzione "sei 9" diventa inattiva per 31,6 secondi in un determinato anno. Sfortunatamente, è raro che una soluzione giustifichi un investimento operativo di grandi dimensioni, necessario per raggiungere "sei 9" di tempo di attività.

La preparazione per un'interruzione del servizio consente al team di rilevare prima gli errori e di eseguire il ripristino più rapidamente. L'obiettivo di questa disciplina è la procedura che si verifica immediatamente dopo che un sistema ha avuto esito negativo. Come si proteggono i carichi di lavoro in modo che possano essere recuperati rapidamente quando si verifica un'interruzione?

## <a name="translate-protection-and-recovery-conversations"></a>Tradurre le conversazioni di protezione e ripristino

I carichi di lavoro che interessano le operazioni aziendali sono costituiti da applicazioni, dati, macchine virtuali (VM) e altre risorse. Ognuno di questi asset potrebbe richiedere un approccio diverso alla protezione e al ripristino. L'aspetto importante di questa disciplina consiste nel definire un impegno coerente all'interno della linea di base di gestione, che può fornire un punto di partenza durante le discussioni aziendali.

Come minimo, ogni asset che supporta un determinato carico di lavoro deve avere un approccio di base con un impegno preciso per la velocità di recupero (obiettivi del tempo di ripristino o RTO) e il rischio di perdita di dati (obiettivi del punto di ripristino o RPO).

### <a name="recovery-time-objectives-rto"></a>Obiettivi del tempo di ripristino (RTO)

In caso di emergenza, un obiettivo del tempo di ripristino è la quantità di tempo necessaria per il ripristino di qualsiasi sistema allo stato di pre-emergenza. Per ogni carico di lavoro, che include il tempo necessario per ripristinare le funzionalità minime necessarie per le macchine virtuali e le app. Include inoltre la quantità di tempo necessaria per ripristinare i dati richiesti dalle applicazioni.

In termini di business, RTO rappresenta la quantità di tempo per cui il processo di business sarà fuori servizio. Per i carichi di lavoro cruciali, questa variabile dovrebbe essere relativamente bassa, consentendo ai processi aziendali di riprendersi velocemente. Per i carichi di lavoro con priorità più bassa, un livello standard di RTO potrebbe non avere un notevole effetto sulle prestazioni aziendali.

La linea di base di gestione deve stabilire un RTO standard per i carichi di lavoro non cruciali. L'azienda può quindi utilizzare tale Baseline come metodo per giustificare ulteriori investimenti nei tempi di ripristino.

### <a name="recovery-point-objectives-rpo"></a>Obiettivi del punto di ripristino (RPO)

Nella maggior parte dei sistemi di gestione cloud, i dati vengono acquisiti e archiviati periodicamente attraverso una forma di protezione dei dati. L'ultima volta che i dati sono stati acquisiti viene definito punto di ripristino. Quando un sistema ha esito negativo, può essere ripristinato solo nel punto di ripristino più recente.

Se un sistema dispone di un obiettivo del punto di ripristino misurato in ore o giorni, un errore di sistema comporterà la perdita di dati per le ore o i giorni compresi tra l'ultimo punto di ripristino e l'interruzione. Un RPO di un giorno dovrebbe teoricamente comportare la perdita di tutte le transazioni nel giorno in cui si è verificato l'errore.

Per i sistemi cruciali, un RPO misurato in minuti o secondi potrebbe essere più appropriato da usare per evitare una perdita dei ricavi. Tuttavia, un RPO più breve comporta in genere un aumento dei costi di gestione complessivi.

Per ridurre al minimo i costi, una linea di base di gestione deve concentrarsi sul RPO più lungo accettabile. Il team di gestione cloud può quindi aumentare il numero di RPO di piattaforme o carichi di lavoro specifici, che richiedono un maggior investimento.

## <a name="protect-and-recover-workloads"></a>Proteggi e ripristina i carichi di lavoro

La maggior parte dei carichi di lavoro in un ambiente IT supporta un processo tecnico o aziendale specifico. I sistemi che non hanno un effetto sistematico sulle operazioni aziendali spesso non garantiscono gli investimenti maggiori necessari per recuperare rapidamente o ridurre al minimo la perdita di dati. Con la definizione di una linea di base, l'azienda può comprendere chiaramente il livello di supporto per il ripristino che può essere offerto in un punto di prezzo coerente e gestibile. Questa comprensione consente agli stakeholder aziendali di valutare il valore di un maggiore investimento nel ripristino.

Per la maggior parte dei team di gestione cloud, una linea di base avanzata con impegni RPO/RTO specifici per le varie risorse genera il percorso più favorevole per gli impegni aziendali reciproci. Le sezioni seguenti descrivono alcune linee di base avanzate comuni che consentono all'azienda di aggiungere facilmente funzionalità di protezione e ripristino tramite un processo ripetibile.

### <a name="protect-and-recover-data"></a>Proteggere e ripristinare i dati

I dati sono probabilmente la risorsa più preziosa nell'economia digitale. La possibilità di proteggere e ripristinare i dati in modo più efficace è la base di riferimento avanzata più comune. Per i dati che alimentano un carico di lavoro di produzione, la perdita di dati può essere direttamente equivalente alla perdita di ricavi o alla perdita di redditività. Si consiglia in genere ai team di gestione cloud di offrire un livello di linea di base di gestione migliorata che supporta piattaforme di dati comuni.

Prima di implementare le operazioni della piattaforma, i team di gestione cloud sono comuni per supportare operazioni migliorate per una piattaforma di dati PaaS (Platform as a Service). Ad esempio, è facile per un team di gestione cloud applicare una frequenza più elevata di backup o replica multiarea per il database SQL di Azure o soluzioni Azure Cosmos DB. In questo modo, il team di sviluppo può migliorare facilmente RPO grazie alla modernizzazione delle piattaforme di dati.

Per altre informazioni su questo processo di pensiero, vedere [disciplina delle operazioni della piattaforma](./platform.md).

### <a name="protect-and-recover-vms"></a>Proteggere e ripristinare le macchine virtuali

La maggior parte dei carichi di lavoro dipende dalle macchine virtuali che ospitano vari aspetti della soluzione. Affinché il carico di lavoro supporti un processo di business dopo un errore di sistema, è necessario ripristinare rapidamente un numero di macchine virtuali.

Ogni minuto di tempo di inattività in tali macchine virtuali potrebbe causare perdite di profitti o riduzione della redditività. Quando il tempo di inattività delle VM ha un effetto diretto sulle prestazioni fiscali dell'azienda, RTO è molto importante. Le macchine virtuali possono essere ripristinate più rapidamente tramite la replica in un sito secondario e il recupero automatico, un modello denominato modello di recupero a caldo caldo. Al massimo stato di ripristino, le macchine virtuali possono essere replicate in un sito secondario completamente funzionante. Questo approccio più costoso viene definito modello di recupero a disponibilità elevata o a caldo.

Ognuno dei modelli precedenti riduce il RTO, ottenendo un ripristino più rapido delle funzionalità del processo di business. Tuttavia, ogni modello comporta anche un aumento significativo dei costi di gestione del cloud.

Per altre informazioni su questo processo di pensiero, vedere [disciplina delle operazioni del carico di lavoro](./workload.md).

## <a name="next-steps"></a>Passaggi successivi

Dopo che questo componente della linea di base di gestione è stato soddisfatto, il team può cercare di evitare interruzioni delle operazioni di [piattaforma](./platform.md) e del [carico di lavoro](./workload.md).

> [!div class="nextstepaction"]
> Operazioni della [piattaforma](./platform.md)
> [operazioni del carico di lavoro](./workload.md)
