---
title: 'Innovazione nel cloud: prevedere e influenzare'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
description: Introduzione all'innovazione cloud-stima e influenza
author: BrianBlanchard
ms.author: brblanch
ms.date: 09/24/2019
ms.topic: guide
ms.service: cloud-adoption-framework
ms.subservice: innovate
ms.openlocfilehash: 2702f1e2807bd2119117283dcb8cfc4fb567c8f5
ms.sourcegitcommit: 35c162d2d09ec1c4a57d3d57a5db1d56ee883806
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2019
ms.locfileid: "72557154"
---
# <a name="predict-and-influence"></a>Stimare e influenzare

Nell'economia digitale sono disponibili due classi di applicazioni: cronologiche e predittive. Molte esigenze dei clienti possono essere soddisfatte esclusivamente usando i dati cronologici, inclusi i dati quasi in tempo reale. La maggior parte delle soluzioni si concentra principalmente sull'aggregazione dei dati, nel momento attuale. Quindi elaborano e condividono i dati al cliente, sotto forma di esperienza digitale o ambientale.

Dato che la modellazione predittiva diventa più economica e prontamente disponibile, i clienti hanno la necessità di esperienze avanzate che consentono di prendere decisioni e azioni migliori. Questa domanda, tuttavia, non deve necessariamente condurre a una soluzione predittiva. Nella maggior parte degli scenari, una visualizzazione cronologica può fornire dati sufficienti per consentire al cliente di prendere una decisione autonomamente.

Sfortunatamente, i clienti hanno una vista miope che consente di prendere decisioni in base alle loro immediate vicinanze e alla sfera di influenza. Man mano che le opzioni e la decisione crescono in numeri e conseguenze, la vista miope potrebbe non comportare la necessità di soddisfare la necessità del cliente. Allo stesso tempo, poiché un'ipotesi viene collaudata su larga scala, la società che fornisce la soluzione può vedere in migliaia o milioni di decisioni dei clienti. È possibile visualizzare i modelli e gli effetti di tali modelli. La funzionalità predittiva è un investimento sapiente, quando è necessario comprendere questi modelli per prendere decisioni che soddisfino le esigenze dei clienti.

## <a name="examples-of-predictions-and-influence"></a>Esempi di stime e influenza

L'utilizzo dei dati per eseguire stime può essere visualizzato in varie applicazioni ed esperienze di ambiente.

- **eCommerce:** Gli elementi suggeriti sono un esempio di stima. In base a ciò che altri utenti hanno acquistato insieme, il sito Web può suggerire prodotti che potrebbero valere l'aggiunta al carrello.
- **Realtà regolata:** Gli esempi più avanzati sono disponibili. Un dispositivo in una riga di assembly rileva un incremento della temperatura dei computer. Un modello predittivo basato sul cloud determina la modalità di risposta. In base a tale stima, a un altro dispositivo viene richiesto di rallentare la riga di assembly fino a quando il computer non può essere raffreddato.
- **Prodotti consumer:** I telefoni cellulari, le case intelligenti, persino la tua auto contengono un certo grado di capacità predittive suggerendo attività basate su fattori come la posizione o l'ora del giorno. Quando la stima e l'ipotesi iniziale sono allineate, tali stime influiscono sui comportamenti. Quando entrambe diventano molto mature, la stima comporta un'azione, ad esempio un'auto auto-guida.

## <a name="developing-predictive-capabilities"></a>Sviluppo di funzionalità predittive

Le soluzioni che forniscono in modo coerente funzionalità predittive accurate includono generalmente cinque caratteristiche principali: dati, informazioni dettagliate, modelli, stime e interazioni. Ogni è necessario per sviluppare funzionalità predittive. Come tutte le innovazioni eccezionali, lo sviluppo di funzionalità predittive richiederà un [impegno per l'iterazione](./index.md#commitment-to-iteration). In ogni iterazione, una o più delle seguenti caratteristiche verranno maturate per convalidare le ipotesi dei clienti sempre più complesse.

![Passaggi per le funzionalità predittive](../../_images/innovate/predict-and-influence.png)

> [!CAUTION]
> Se l'ipotesi del cliente sviluppata dall'articolo [Build with customer empatiy](./build.md) include funzionalità predittive, questo articolo potrebbe essere applicabile. Tuttavia, le funzionalità predittive richiedono investimenti significativi di tempo e energia. Quando le funzionalità predittive sono [picchi tecnici](./build.md#reduce-complexity-and-delay-technical-spikes), in contrapposizione a un'origine di valore del cliente realizzabile, è consigliabile ritardare le stime fino a quando l'ipotesi del cliente non è stata convalidata su larga scala.

## <a name="data"></a>Dati

Il più semplice delle caratteristiche precedenti sono i dati. Ognuna delle discipline precedenti per lo sviluppo di invenzioni digitali genererà dati. Tali dati possono contribuire allo sviluppo di stime. Per altre indicazioni sui modi in cui ottenere i dati in una soluzione predittiva, vedere gli articoli sulla [democratizzazione dei dati](./data.md) o sull' [interazione con i dispositivi](./devices.md).

Per fornire funzionalità predittive è possibile usare una serie di origini dati:

## <a name="insights"></a>Informazioni approfondite

Gli esperti in materia sfruttano i dati relativi alle esigenze e ai comportamenti dei clienti per sviluppare informazioni aziendali di base da uno studio dei dati non elaborati. Tali informazioni possono individuare le occorrenze dei comportamenti desiderati del cliente (o risultati alternativi indesiderati). Durante le iterazioni nelle stime, queste informazioni possono aiutare a identificare le possibili correlazioni, che potrebbero avere un effetto causale sui risultati positivi. Per informazioni sull'abilitazione di esperti in materia per lo sviluppo di informazioni dettagliate, vedere l'articolo sulla [democratizzazione dei dati](./data.md).

## <a name="patterns"></a>Modelli

Il personale infaticato a individuare i modelli in volumi di dati di grandi dimensioni. I computer sono stati progettati a tale scopo. Machine Learning accelera tale scopo attraverso il rilevamento dei modelli in una grande quantità di dati, definita modello di machine learning. Questi modelli vengono quindi applicati, tramite gli algoritmi di Machine Learning, per stimare cosa accadrà quando viene immesso un nuovo set di punti dati negli algoritmi.

Usando Insights come punto di partenza, Machine Learning addestra e applica modelli predittivi ai dati per sfruttare i modelli nei dati. Attraverso più iterazioni di training, test e adozione, i modelli e gli algoritmi possono prevedere in modo accurato i risultati futuri.

[Azure Machine Learning servizio](https://docs.microsoft.com/azure/machine-learning/service/overview-what-is-azure-ml) è lo strumento nativo del cloud in Azure per la creazione e il training di modelli basati sui dati. Questo strumento include anche un [flusso di lavoro per accelerare lo sviluppo di algoritmi di Machine Learning](https://docs.microsoft.com/azure/machine-learning/service/concept-azure-machine-learning-architecture). Questo flusso di lavoro può essere usato per sviluppare algoritmi usando l'interfaccia visiva o Python.

Per i modelli di apprendimento automatico più affidabili, [ml Services in Azure HDInsight](https://docs.microsoft.com/azure/hdinsight/r-server/r-server-overview) fornisce una piattaforma di Machine Learning basata su cluster Apache Hadoop. Questo approccio consente un controllo più granulare dei nodi di calcolo, archiviazione e cluster sottostanti. L'uso di Azure HDInsight offre anche un'integrazione più avanzata tramite strumenti come Scaler e Sparkr per creare stime basate su dati integrati e inseriti, anche usando i dati di un flusso. La [soluzione per la stima dei ritardi dei voli](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-r-scaler-sparkr) illustra ognuna di queste funzionalità avanzate per stimare i ritardi dei voli in base alle condizioni meteorologiche. La soluzione HDInsight consente anche controlli aziendali, ad esempio la sicurezza dei dati, l'accesso alla rete e il monitoraggio delle prestazioni ai modelli rendere operativo.

## <a name="predictions"></a>Previsioni

Una volta creato e sottoposto a training, un modello può essere applicato usando le API, che possono eseguire stime durante il recapito di un'esperienza digitale. La maggior parte di queste API è costituita da un modello ben preparato basato su un modello all'interno dei dati. Tuttavia, poiché più clienti distribuiscono carichi di lavoro comuni nel cloud, i provider di servizi cloud sono in grado di fornire API di stima comuni per consentire l'adozione più rapida delle stime.

[Servizi cognitivi di Azure](https://docs.microsoft.com/azure/cognitive-services) è un esempio di compilazione di un'API predittiva da parte di un fornitore di servizi cloud. Questo servizio include API predittive per la moderazione del contenuto, il rilevamento delle anomalie o suggerimenti per personalizzare il contenuto. Queste API sono pronte per l'uso in base ai modelli di contenuto comuni usati da Microsoft per il training dei modelli. Ognuna di queste API esegue stime basate sui dati da inserire nell'API.

[Azure Machine Learning servizio](https://docs.microsoft.com/azure/machine-learning) consente la distribuzione di algoritmi personalizzati, che è possibile creare ed eseguire il training esclusivamente in base ai propri dati. Per altre informazioni sulla distribuzione di stime con Azure Machine Learning, vedere [qui](https://docs.microsoft.com/azure/machine-learning/service/how-to-deploy-and-where).

L'articolo sulla [configurazione di cluster HDInsight](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-provision-linux-clusters) illustra i processi per esporre le stime sviluppate per i servizi ml in Azure HDInsight.

## <a name="interactions"></a>Interazioni

Quando una stima viene resa disponibile tramite un'API, è possibile usare la stima per influenzare i comportamenti dei clienti. Questa influenza si presenta sotto forma di interazioni. Un'interazione con un algoritmo di apprendimento automatico si verifica all'interno di altre esperienze digitali o di ambiente. Poiché i dati vengono raccolti tramite l'applicazione o l'esperienza, i dati vengono eseguiti attraverso gli algoritmi di machine learning. Quando l'algoritmo esegue la stima di un risultato, la stima può essere condivisa con il cliente attraverso l'esperienza esistente.

Per altre informazioni sulla creazione di un'interazione in un'esperienza di ambiente, vedere altre informazioni sulle interazioni in una [soluzione di realtà adattata](./devices.md#adjusted-reality).

## <a name="next-steps"></a>Passaggi successivi

Basandosi sulle conoscenze acquisite in merito alle [discipline di innovazione](./invention.md) all'interno della [metodologia innovativa](./index.md) , si conosceranno gli strumenti tecnici necessari per la [compilazione con Empathy](./build.md).

> [!div class="nextstepaction"]
> [Compilazione con empatia](./build.md)
