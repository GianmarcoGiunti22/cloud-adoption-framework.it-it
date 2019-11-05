---
title: 'Innovazione nel cloud: prevedere e influenzare'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Introduzione all'innovazione cloud-stima e influenza
author: BrianBlanchard
ms.author: brblanch
ms.date: 10/17/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: 8aa0e1d86bb679241bc8e769bb8a09fc436c6906
ms.sourcegitcommit: bf9be7f2fe4851d83cdf3e083c7c25bd7e144c20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2019
ms.locfileid: "73565577"
---
# <a name="predict-and-influence"></a>Stimare e influenzare

Nell'economia digitale sono disponibili due classi di applicazioni: *cronologiche* e *predittive*. Molte esigenze dei clienti possono essere soddisfatte esclusivamente usando i dati cronologici, inclusi i dati quasi in tempo reale. La maggior parte delle soluzioni si concentra principalmente sull'aggregazione dei dati nel momento. Quindi elaborano e condividono i dati al cliente sotto forma di esperienza digitale o ambientale.

Poiché la modellazione predittiva diventa più economica e prontamente disponibile, i clienti richiedono esperienze avanzate che portano a decisioni e azioni migliori. Tuttavia, tale richiesta non sempre suggerisce una soluzione predittiva. Nella maggior parte dei casi, una visualizzazione cronologica può fornire dati sufficienti per consentire al cliente di prendere una decisione autonomamente.

Sfortunatamente, i clienti spesso hanno una vista miope che consente di prendere decisioni in base alle loro immediate vicinanze e alla sfera di influenza. Poiché le opzioni e le decisioni crescono in numero e conseguenze, la vista miope potrebbe non soddisfare le esigenze del cliente. Allo stesso tempo, poiché un'ipotesi viene collaudata su larga scala, la società che fornisce la soluzione può vedere in migliaia o milioni di decisioni dei clienti. Questo approccio di grandi dimensioni consente di visualizzare i modelli più ampi e gli effetti di tali modelli. La funzionalità predittiva è un buon investimento quando una conoscenza di questi modelli è necessaria per prendere decisioni più adatte ai clienti.

## <a name="examples-of-predictions-and-influence"></a>Esempi di stime e influenza

Un'ampia gamma di applicazioni e di esperienze di ambiente USA i dati per eseguire stime:

- **E-commerce:** In base agli altri consumer acquistati, un sito Web di e-commerce suggerisce prodotti che potrebbero valere l'aggiunta al carrello.
- **Realtà regolata:** L'offerta offre istanze più avanzate della funzionalità predittiva. Ad esempio, un dispositivo in una riga di assembly rileva un incremento della temperatura di un computer. Un modello predittivo basato sul cloud determina la modalità di risposta. In base a tale stima, un altro dispositivo rallenta la linea di assembly fino a quando non è possibile raffreddare il computer.
- **Prodotti consumer:** Telefoni cellulari, case intelligenti, persino la tua auto, usano tutte le funzionalità predittive che sfruttano per suggerire il comportamento degli utenti in base a fattori come la posizione o l'ora del giorno. Quando una stima e l'ipotesi iniziale sono allineate, la stima comporta un'azione. In una fase molto avanzata, questo allineamento può rendere realtà i prodotti come un'auto auto-guida.

## <a name="develop-predictive-capabilities"></a>Sviluppare funzionalità predittive

Le soluzioni che forniscono in modo coerente funzionalità predittive accurate includono generalmente cinque caratteristiche principali: *dati, informazioni* *dettagliate*, *modelli*, *stime*e *interazioni*. Ogni aspetto è necessario per sviluppare funzionalità predittive. Come tutte le innovazioni eccezionali, lo sviluppo di funzionalità predittive richiede un [impegno per l'iterazione](./index.md#commitment-to-iteration). In ogni iterazione viene maturata una o più delle seguenti caratteristiche per convalidare le ipotesi dei clienti sempre più complesse.

![Passaggi per le funzionalità predittive](../../_images/innovate/predict-and-influence.png)

> [!CAUTION]
> Se l'ipotesi del cliente sviluppata in [Build con Customer empatiy](./build.md) include funzionalità predittive, i principi descritti potrebbero essere validi. Tuttavia, le funzionalità predittive richiedono investimenti significativi di tempo e energia. Quando le funzionalità predittive sono [picchi tecnici](./build.md#reduce-complexity-and-delay-technical-spikes), anziché un'origine di un valore reale del cliente, è consigliabile ritardare le stime fino a quando le ipotesi dei clienti non sono state convalidate su larga scala.

## <a name="data"></a>Dati

I dati sono la maggior parte degli elementi delle caratteristiche descritte in precedenza. Ognuna delle discipline per lo sviluppo di invenzioni digitali genera dati. Tali dati, ovviamente, contribuiscono allo sviluppo di stime. Per altre indicazioni sui modi per ottenere i dati in una soluzione predittiva, vedere [democratizzazione dei dati](./data.md) e [interazione con i dispositivi](./devices.md).

È possibile utilizzare un'ampia gamma di origini dati per fornire funzionalità predittive:

## <a name="insights"></a>Informazioni dettagliate

Gli esperti in materia sfruttano i dati relativi alle esigenze e ai comportamenti dei clienti per sviluppare informazioni aziendali di base da uno studio di dati non elaborati. Tali informazioni possono individuare le occorrenze dei comportamenti desiderati del cliente (o, in alternativa, risultati indesiderati). Durante le iterazioni nelle stime, queste informazioni possono aiutare a identificare le possibili correlazioni che potrebbero generare risultati positivi. Per informazioni sull'abilitazione di esperti in materia per sviluppare informazioni dettagliate, vedere [democratizzazione dei dati](./data.md).

## <a name="patterns"></a>Modelli

Le persone hanno sempre tentato di rilevare i modelli in grandi volumi di dati. I computer sono stati progettati a tale scopo. Machine Learning accelera tale ricerca individuando con precisione tali modelli, un'abilità che comprende il modello di machine learning. Questi modelli vengono quindi applicati tramite gli algoritmi di machine learning per stimare i risultati quando viene immesso un nuovo set di dati negli algoritmi.

Usando informazioni dettagliate come punto di partenza, Machine Learning sviluppa e applica modelli predittivi per sfruttare i modelli nei dati. Grazie a più iterazioni di training, test e adozione, i modelli e gli algoritmi possono prevedere in modo accurato i risultati futuri.

[Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning/service/overview-what-is-azure-ml) è il servizio nativo del cloud in Azure per la compilazione e il training di modelli basati sui dati. Questo strumento include anche un [flusso di lavoro per accelerare lo sviluppo di algoritmi di Machine Learning](https://docs.microsoft.com/azure/machine-learning/service/concept-azure-machine-learning-architecture). Questo flusso di lavoro può essere usato per sviluppare algoritmi tramite un'interfaccia visiva o Python.

Per i modelli di apprendimento automatico più affidabili, [ml Services in Azure HDInsight](https://docs.microsoft.com/azure/hdinsight/r-server/r-server-overview) fornisce una piattaforma di Machine Learning basata su cluster Apache Hadoop. Questo approccio consente di controllare in modo più granulare i cluster, le risorse di archiviazione e i nodi di calcolo sottostanti. Azure HDInsight offre anche un'integrazione più avanzata tramite strumenti come Scaler e Sparkr per creare stime basate su dati integrati e inseriti, anche per lavorare con i dati di un flusso. La [soluzione di stima dei ritardi dei voli](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-r-scaler-sparkr) illustra ognuna di queste funzionalità avanzate quando viene usata per stimare i ritardi dei voli in base alle condizioni meteorologiche. La soluzione HDInsight consente anche controlli aziendali, ad esempio la sicurezza dei dati, l'accesso alla rete e il monitoraggio delle prestazioni ai modelli rendere operativo.

## <a name="predictions"></a>Previsioni

Dopo aver compilato e sottoposto a Training un modello, è possibile applicarlo tramite le API, che possono eseguire stime durante la consegna di un'esperienza digitale. La maggior parte di queste API è costituita da un modello adeguatamente sottoposto a training basato su un modello nei dati. Poiché più clienti distribuiscono carichi di lavoro giornalieri nel cloud, le API di stima usate dai provider di servizi cloud comportano un'adozione sempre più rapida.

[Servizi cognitivi di Azure](https://docs.microsoft.com/azure/cognitive-services) è un esempio di un'API predittiva creata da un fornitore di cloud. Questo servizio include API predittive per la moderazione del contenuto, il rilevamento delle anomalie e suggerimenti per personalizzare il contenuto. Queste API sono pronte per l'uso e si basano su modelli di contenuto noti, usati da Microsoft per il training dei modelli. Ognuna di queste API esegue stime basate sui dati da inserire nell'API.

[Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning) consente di distribuire algoritmi personalizzati, che è possibile creare ed eseguire il training esclusivamente in base ai propri dati. Ulteriori informazioni sulla distribuzione delle stime con [Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning/service/how-to-deploy-and-where).

[Configurare cluster HDInsight](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-provision-linux-clusters) illustra i processi per esporre le stime sviluppate per i servizi ml in Azure HDInsight.

## <a name="interactions"></a>Interazioni

Quando una stima viene resa disponibile tramite un'API, è possibile utilizzarla per influenzare il comportamento dei clienti. Tale influenza assume la forma di interazioni. Un'interazione con un algoritmo di apprendimento automatico si verifica all'interno di altre esperienze digitali o di ambiente. Poiché i dati vengono raccolti tramite l'applicazione o l'esperienza, vengono eseguiti attraverso gli algoritmi di machine learning. Quando l'algoritmo esegue la stima di un risultato, la stima può essere condivisa con il cliente attraverso l'esperienza esistente.

Altre informazioni su come creare un'esperienza di ambiente tramite una [soluzione di realtà adattata](./devices.md#adjusted-reality).

## <a name="next-steps"></a>Passaggi successivi

Conoscendo le [discipline di invenzione](./invention.md) e la [metodologia di innovazione](./index.md), è ora possibile apprendere come [creare con l'empatia dei clienti](./build.md).

> [!div class="nextstepaction"]
> [Compilazione con empatia](./build.md)
