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
ms.openlocfilehash: 2e055cb6105b9424259d2b8e86bdde7d64798479
ms.sourcegitcommit: f3371811a36e12533ecbc3aa936e2a68e0cee25f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/21/2019
ms.locfileid: "72682461"
---
# <a name="protect-and-recover-in-cloud-management"></a>Proteggi e ripristina in gestione cloud

Quando sono stati soddisfatti i requisiti per l' [inventario e la visibilità](./inventory.md) e la [conformità operativa](./operational-compliance.md) , i team di gestione cloud possono essere in grado di esaminare e preparare il potenziale di un'interruzione di carico di lavoro. Quando si pianifica la gestione del cloud, il team deve iniziare con un presupposto che si verifichi un errore.

Nessuna soluzione tecnica può offrire in modo coerente un contratto di tempo di esecuzione del 100%. Le soluzioni con le architetture con la maggiore ridondanza attestano il recapito in "sei 9" o il tempo di esecuzione del 99,9999%. Ma anche una soluzione "sei 9" diventa inattiva per 31,6 secondi in un determinato anno. Sfortunatamente, raramente le soluzioni garantiscono la grande quantità di investimenti operativi in continuazione necessari per raggiungere "sei 9" di tempo di attività.

La preparazione di un'interruzione consentirà al team di rilevare più rapidamente gli errori e di eseguire il ripristino più rapidamente. L'obiettivo di questa disciplina riguarda i passaggi successivi che si verificano in seguito a un errore di sistema. Come proteggere i carichi di lavoro, in modo che possano essere recuperati rapidamente quando si verifica un'interruzione.

## <a name="translating-protection-and-recovery-conversations"></a>Traduzione di conversazioni di protezione e ripristino

I carichi di lavoro che interessano le operazioni aziendali sono costituite da applicazioni, dati, macchine virtuali e altre risorse. Ognuno di questi asset potrebbe richiedere un approccio diverso alla protezione e al ripristino. L'aspetto importante di questa disciplina consiste nel definire un impegno coerente all'interno della linea di base di gestione, per fornire un punto di partenza durante le discussioni aziendali.

Come minimo, ogni asset che supporta un determinato carico di lavoro deve avere un approccio di base con un impegno preciso per la velocità di recupero (obiettivi del tempo di ripristino o RTO) e il rischio di perdita di dati (obiettivi del punto di ripristino o RPO).

### <a name="recovery-time-objectives-rto"></a>Obiettivi del tempo di ripristino (RTO)

Quando si verifica un evento di emergenza, RTO è la quantità di tempo che deve eseguire per il ripristino di un determinato sistema allo stato di pre-emergenza. Per ogni carico di lavoro, che include il tempo necessario per ripristinare le funzionalità minime necessarie per le macchine virtuali e le app. Include inoltre la quantità di tempo necessaria per ripristinare i dati necessari per le applicazioni.

In termini di business, RTO rappresenta la quantità di tempo per cui il processo di business sarà fuori servizio. Per i carichi di lavoro mission-critical, questa variabile dovrebbe essere relativamente bassa, consentendo ai processi aziendali di riprendersi velocemente. Per i carichi di lavoro con priorità più bassa, un livello standard di RTO potrebbe non avere un notevole effetto sulle prestazioni aziendali.

La linea di base di gestione deve stabilire un obiettivo del tempo di ripristino standard per i carichi di lavoro non cruciali. L'azienda può quindi utilizzare tale Baseline come metodo per giustificare ulteriori investimenti nei tempi di ripristino.

### <a name="recovery-point-objectives-rpo"></a>Obiettivi del punto di ripristino (RPO)

Nella maggior parte dei sistemi di gestione cloud, i dati vengono acquisiti e archiviati periodicamente attraverso una forma di protezione dei dati. L'ultima volta che i dati sono stati acquisiti viene definito punto di ripristino. Quando un sistema ha esito negativo, può essere ripristinato solo nel punto di ripristino più recente.

Se un sistema dispone di un obiettivo del punto di ripristino misurato in ore o giorni, un errore di sistema comporterà la perdita di dati per le ore o i giorni compresi tra l'ultimo punto di ripristino e l'interruzione. Un RPO di 1 giorno dovrebbe teoricamente comportare la perdita di tutte le transazioni nel giorno in cui si è verificato l'errore.

Per i sistemi mission-critical, un RPO misurato in minuti o secondi potrebbe essere più appropriato per evitare una perdita dei ricavi. Tuttavia, un RPO più breve comporta in genere un aumento dei costi di gestione complessivi.

Una linea di base di gestione deve concentrarsi sul RPO più lungo accettabile per ridurre i costi. Il team di gestione cloud può quindi aumentare il numero di RPO di piattaforme o carichi di lavoro specifici, che richiedono un maggior investimento.

## <a name="protect-and-recover-workloads"></a>Proteggi e ripristina i carichi di lavoro

La maggior parte dei carichi di lavoro in un ambiente IT supporta un processo aziendale o tecnico molto piccolo. I sistemi che non hanno un effetto sistematico sulle operazioni aziendali spesso non garantiscono i maggiori investimenti necessari per il recupero rapido o per ridurre al minimo la perdita di dati. La definizione di una linea di base consente all'azienda di comprendere chiaramente il livello di supporto del ripristino che può essere offerto in un punto di prezzo coerente e gestibile. In questo modo, le parti interessate aziendali valutano il valore di un maggiore investimento nel ripristino.

Per la maggior parte dei team di gestione cloud, una linea di base avanzata con impegni RPO/RTO specifici per varie risorse, produce il percorso più favorevole per gli impegni aziendali reciproci. Le sezioni seguenti descrivono alcune linee di base avanzate comuni che consentono all'azienda di aggiungere facilmente funzionalità di protezione e ripristino tramite un processo ripetibile.

### <a name="protect-and-recover-data"></a>Proteggere e ripristinare i dati

I dati sono probabilmente la risorsa più preziosa nell'economia digitale. La possibilità di proteggere e ripristinare i dati in modo più efficace è la base di riferimento avanzata più comune. Per i dati che alimentano un carico di lavoro di produzione, la perdita di dati può essere direttamente equivalente alla perdita di ricavi o alla perdita di redditività. È in genere consigliabile che i team di gestione cloud offrano un livello di linea di base di gestione migliorata che supporta le piattaforme di dati comuni.

Prima di implementare le operazioni della piattaforma, è comune per i team di gestione cloud supportare operazioni migliorate per la piattaforma dati di piattaforma come servizio. Ad esempio, è facile per un team di gestione cloud applicare una frequenza più elevata di backup o replica in più aree per le soluzioni Azure SQL o Cosmo DB. Questa operazione consente al team di sviluppo di migliorare facilmente RPO semplicemente modernizzando le piattaforme di dati.

Questo processo di pensiero verrà rivisitato più dettagliatamente nella [disciplina delle operazioni della piattaforma](./platform.md).

### <a name="protect-and-recover-vms"></a>Proteggere e ripristinare le macchine virtuali

La maggior parte dei carichi di lavoro dipende dalle macchine virtuali. Tali macchine virtuali ospitano diversi aspetti della soluzione. Affinché il carico di lavoro supporti un processo di business dopo un errore di sistema, è necessario ripristinare rapidamente una serie di macchine virtuali.

Ogni minuto di tempo di inattività in tali macchine virtuali potrebbe equivalere a perdite ricavi o riduzione della redditività. Quando il tempo di inattività delle macchine virtuali ha un effetto diretto sulle prestazioni fiscali dell'azienda, RTO è molto importante. Le macchine virtuali possono essere ripristinate più rapidamente usando la replica in un sito secondario e il ripristino automatico. questo modello viene definito modello di recupero a caldo caldo. Al massimo stato di ripristino, le macchine virtuali possono essere replicate in un sito secondario completamente funzionante. Questo approccio più costoso viene definito modello di recupero ad alta disponibilità o a caldo.

Ognuno dei modelli precedenti riduce l'obiettivo del tempo di ripristino, ottenendo un ripristino più rapido delle funzionalità del processo di business. Tuttavia, ogni modello comporta anche un aumento significativo dei costi di gestione del cloud.

Questo processo di pensiero verrà rivisitato più dettagliatamente nella [disciplina delle operazioni del carico di lavoro](./workload.md).

## <a name="next-steps"></a>Passaggi successivi

Una volta raggiunto il componente della linea di base di gestione, il team può esaminare ulteriormente le interruzioni delle operazioni di [piattaforma](./platform.md) e del [carico di lavoro](./workload.md).

> [!div class="nextstepaction"]
> Operazioni della [piattaforma](./platform.md) 
> [operazioni del carico di lavoro](./workload.md)
