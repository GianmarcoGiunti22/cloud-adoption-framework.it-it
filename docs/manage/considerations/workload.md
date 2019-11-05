---
title: Operazioni del carico di lavoro-gestione cloud e operazioni
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Operazioni del carico di lavoro-gestione cloud e operazioni
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: article
ms.service: cloud-adoption-framework
ms.subservice: operate
ms.openlocfilehash: 7eca93ba324a0e41f2a04e81a6bfe8994c232fcd
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565037"
---
# <a name="workload-operations-in-cloud-management"></a>Operazioni del carico di lavoro nella gestione cloud

Alcuni carichi di lavoro sono fondamentali per il successo dell'azienda. Per questi carichi di lavoro, una linea di base di gestione non è sufficiente per soddisfare gli impegni aziendali richiesti per la gestione del cloud. Le operazioni della piattaforma potrebbero non essere sufficienti per soddisfare gli impegni aziendali. Questo subset di carichi di lavoro estremamente importante richiede un'attenzione specializzata sul modo in cui il carico di lavoro funziona e su come è supportato.

In cambio, l'investimento nelle operazioni del carico di lavoro può comportare un miglioramento delle prestazioni, ridurre il rischio di interruzione aziendale e un ripristino più rapido quando si verificano errori di sistema. Questo articolo illustra un approccio per investire nelle operazioni continuative di questi carichi di lavoro con priorità alta per favorire un miglioramento degli impegni aziendali.

## <a name="when-to-invest-in-workload-operations"></a>Quando investire nelle operazioni del carico di lavoro

Il _principio di Pareto_ (anche noto come _regola 80/20_) indica che il 80% degli effetti proviene dal 20% delle cause. Quando i portfolio IT sono autorizzati a crescere in modo organico nel tempo, questa regola è spesso illustrata in una revisione del portfolio IT. A seconda dell'effetto che richiede investimenti, la ragione può variare, ma il principio generale è valido:

- il 80% degli errori di sistema tende a essere il risultato del 20% degli errori comuni o dei bug.
- il 80% del valore aziendale tende a provenire dal 20% dei carichi di lavoro in un portfolio.
- il 80% del lavoro richiesto per la migrazione al cloud deriva dal 20% dei carichi di lavoro spostati.
- il 80% delle attività di gestione del cloud supporterà il 20% degli eventi imprevisti del servizio o dei ticket di problema.
- il 80% dell'impatto aziendale da un'interruzione produrrà dal 20% dei sistemi interessati dall'interruzione del servizio.

Le operazioni del carico di lavoro devono essere applicate solo quando la strategia di adozione del cloud, i risultati aziendali e le metriche operative sono tutti ben noti. Si tratta di un cambiamento di paradigma rispetto alla visualizzazione classica. Tradizionalmente, si presumeva che tutti i carichi di lavoro hanno avuto lo stesso livello di supporto e che richiedevano livelli di priorità simili.

Prima di investire in operazioni di carico di lavoro approfondite, sia l'IT che l'azienda devono comprendere le motivazioni aziendali e le aspettative di un maggior investimento nella gestione del cloud.

## <a name="start-with-the-data"></a>Partire dai dati

Le operazioni sui carichi di lavoro iniziano con una conoscenza approfondita dei requisiti di prestazioni e supporto del carico di lavoro Prima di investire nel carico di lavoro, il team deve avere dati avanzati sulle dipendenze del carico di lavoro, le prestazioni delle applicazioni, la diagnostica del database, la telemetria delle macchine virtuali e la cronologia degli eventi

Questi dati si basano sulle informazioni approfondite che determinano le operazioni di gestione del carico di lavoro.

## <a name="continued-observation"></a>Osservazione continua

I dati iniziali e i dati di telemetria in corso possono contribuire a formulare e testare teorie sulle prestazioni di un carico di lavoro. Tuttavia, le operazioni in corso sui carichi di lavoro sono radicate in un'osservazione continua ed espansa delle prestazioni del carico di lavoro, con un notevole interesse per le prestazioni dell'applicazione e dei dati.

### <a name="test-the-automation"></a>Testare l'automazione

A livello di applicazione, i primi requisiti delle operazioni del carico di lavoro sono un investimento nel testing approfondito. Per qualsiasi applicazione supportata tramite le operazioni del carico di lavoro, è necessario stabilire un piano di test ed eseguirlo regolarmente per offrire test funzionali e di scalabilità tra le applicazioni.

I dati di telemetria di test regolari possono fornire la convalida immediata di varie ipotesi relative al funzionamento del carico di lavoro. Il miglioramento degli schemi operativi e dell'architettura può essere eseguito e testato. I Delta risultanti forniscono un'analisi di effetto chiara per guidare gli investimenti continui.

### <a name="understand-releases"></a>Informazioni sulle versioni

Una comprensione chiara dei cicli di rilascio e delle pipeline di versione è un elemento importante delle operazioni del carico di lavoro.

Una comprensione dei cicli può prepararsi a potenziali interruzioni e consentire al team di gestire in modo proattivo le versioni che potrebbero produrre un effetto negativo sulle operazioni. Questa comprensione consente inoltre al team di gestione del cloud di collaborare con i team di adozione per migliorare costantemente la qualità del prodotto e risolvere eventuali bug che potrebbero influire sulla stabilità.

Ancora più importante, una conoscenza delle pipeline di versione può migliorare significativamente l'obiettivo del punto di ripristino (RPO) di un carico di lavoro. In molti scenari, il percorso più veloce e più preciso del ripristino di un'applicazione è una pipeline di rilascio. Per i livelli dell'applicazione che cambiano solo quando si verifica una nuova versione, potrebbe essere opportuno investire con maggiore attenzione nell'ottimizzazione della pipeline rispetto al ripristino dell'applicazione dai processi tradizionali di backup.

Anche se una pipeline di distribuzione può essere il percorso più veloce per il ripristino, può anche essere il percorso più veloce per la correzione. Quando un'applicazione dispone di una pipeline di rilascio veloce, efficiente e affidabile, il team di gestione cloud ha la possibilità di automatizzare la distribuzione in un nuovo host come una forma di monitoraggio e aggiornamento automatico.

Potrebbero essere presenti molti altri meccanismi più veloci ed efficaci per la correzione e il ripristino. Tuttavia, quando l'uso di una pipeline esistente può soddisfare gli impegni aziendali e capitalizzare gli investimenti DevOps esistenti, la pipeline esistente potrebbe essere un'alternativa valida.

### <a name="clearly-communicate-changes-to-the-workload"></a>Comunicare chiaramente le modifiche al carico di lavoro

La modifica a qualsiasi carico di lavoro è tra i maggiori rischi per le operazioni del carico di lavoro. Per qualsiasi carico di lavoro nel livello delle operazioni del carico di lavoro di gestione cloud, il team di gestione cloud deve allinearsi strettamente ai team di adozione del cloud per comprendere le modifiche provenienti da ogni versione. Questo investimento nella comprensione proattiva avrà un impatto diretto e positivo sulla stabilità operativa.

## <a name="improve-outcomes"></a>Migliorare i risultati

Gli investimenti per la comunicazione e i dati in un carico di lavoro produrranno suggerimenti per migliorare le operazioni in corso in una delle tre aree seguenti:

- Risoluzione del debito tecnico
- Correzione automatica
- Miglioramento della progettazione del sistema

### <a name="technical-debt-resolution"></a>Risoluzione del debito tecnico

I piani operativi migliori per i carichi di lavoro richiedono ancora la correzione. Poiché il team di gestione cloud cerca di rimanere connesso per comprendere le attività e le versioni di adozione, il team deve condividere regolarmente i requisiti di correzione per garantire che il debito tecnico e i bug siano una priorità continua per i team di sviluppo.

### <a name="automated-remediation"></a>Correzione automatica

Applicando il principio di Pareto, si può affermare che il 80% dell'impatto aziendale negativo deriva probabilmente dal 20% degli eventi imprevisti del servizio. Quando questi eventi imprevisti non possono essere risolti nei normali cicli di sviluppo, gli investimenti nell'automazione della correzione possono ridurre significativamente le interruzioni aziendali.

### <a name="improved-system-design"></a>Miglioramento della progettazione del sistema

Nei casi di risoluzione del debito tecnico e correzione automatica, i difetti del sistema sono la ragione comune della maggior parte delle interruzioni del sistema. È possibile avere un maggiore effetto sulle operazioni complessive del carico di lavoro rispettando alcuni principi di progettazione:

- **Scalabilità:** Capacità di un sistema di gestire un aumento del carico.
- **Disponibilità:** Percentuale di tempo in cui un sistema è funzionante e funzionante.
- **Resilienza:** Possibilità che un sistema recuperi gli errori e continui a funzionare.
- **Gestione:** Processi operativi che mantengono un sistema in esecuzione nell'ambiente di produzione.
- **Sicurezza:** Protezione delle applicazioni e dei dati dalle minacce.

Per migliorare le operazioni complessive, il [Framework di architettura di Azure](https://docs.microsoft.com/azure/architecture/guide/pillars) offre un approccio alla valutazione di carichi di lavoro specifici per l'adesione a questi pilastri. È possibile applicare i pilastri che possono essere applicati sia alle operazioni della piattaforma che alle operazioni del carico di lavoro.

## <a name="next-steps"></a>Passaggi successivi

Con una conoscenza completa della metodologia di gestione all'interno del Framework di adozione del cloud, è ora necessario implementare i principi di gestione del cloud. Per istruzioni su come rendere questa metodologia attiva all'interno dell'ambiente operativo, vedere [gestione cloud nel Framework di adozione del cloud](../index.md) del ciclo di vita dell'adozione.

> [!div class="nextstepaction"]
> [Applica questa metodologia](../index.md)
